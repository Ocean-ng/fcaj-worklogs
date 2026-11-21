---
title: "Blog 3"
date: 2024-01-01
weight: 3
chapter: false
pre: " <b> 3.3. </b> "
---

# Automating Threat Detection and Security Incident Response on AWS with GuardDuty, Security Hub, and EventBridge

In Cloud Security Operations (Cloud SecOps), the elapsed time between an initial compromise and when defenders detect (**MTTD** - Mean Time to Detect) and contain (**MTTR** - Mean Time to Respond) the threat determines the blast radius of an incident. Relying solely on manual log reviews across CloudTrail or VPC Flow Logs leaves organizations vulnerable to fast-moving automated attacks.

This article outlines an event-driven threat detection, compliance scoring, and automated incident response architecture on AWS practiced during my internship.

---

### 1. Three-Tier Automated Cloud SecOps Architecture

An active cloud defense pipeline on AWS integrates three core functional tiers:

1. **Detection & Posture Assessment Tier:**
   * **Amazon GuardDuty:** Continuously analyzes **AWS CloudTrail Events**, **VPC Flow Logs**, and **Route 53 DNS Query Logs** using Machine Learning anomaly detection and integrated threat intelligence feeds (e.g., detecting IAM credentials used from Tor exit nodes, EC2 instances communicating with crypto-mining pools, or internal port sweeps).
   * **AWS Security Hub:** Aggregates findings in the standardized **AWS Security Finding Format (ASFF)** from GuardDuty, Inspector, and IAM Access Analyzer while continuously evaluating account configurations against the **CIS AWS Foundations Benchmark**.

2. **Event Orchestration Tier:**
   * **Amazon EventBridge:** Acts as the real-time event router, filtering high-severity findings (`HIGH` / `CRITICAL`) emitted by GuardDuty and Security Hub.

3. **Automated Response & Notification Tier:**
   * **Amazon SNS:** Delivers instant alerts to the security engineering team via Email, Slack, or Microsoft Teams.
   * **AWS Lambda:** Executes automated containment playbooks within seconds of detection.

---

### 2. EventBridge Rule Pattern for High-Severity GuardDuty Findings

To trigger automated containment and alerting only for high-severity threats (`severity >= 7.0`), configure the following Event Pattern in Amazon EventBridge:

```json
{
  "source": ["aws.guardduty"],
  "detail-type": ["GuardDuty Finding"],
  "detail": {
    "severity": [
      { "numeric": [">=", 7.0] }
    ]
  }
}
```

---

### 3. Automated EC2 Quarantine Playbook with AWS Lambda

When GuardDuty detects an EC2 instance communicating with a known Command-and-Control server (`Backdoor:EC2/C&CActivity.B!DNS`), EventBridge invokes an AWS Lambda remediation function that performs three automated steps:
1. **Network Isolation:** Replaces the instance's active Security Groups with a dedicated `Quarantine-Security-Group` (containing zero Inbound and zero Outbound rules) to sever attacker communication while keeping the instance running to preserve volatile memory for forensic investigation.
2. **Forensic Snapshot Capture:** Triggers **EBS Snapshots** of all attached volumes and tags them with `ForensicEvidence=True`.
3. **Structured Alerting:** Publishes the Instance ID, Finding Type, Region, and remediation status to **Amazon SNS** for immediate analyst review.

---

### 4. Key Takeaways from Hands-On Practice

* **Agentless, Tamper-Resistant Visibility:** Because Amazon GuardDuty operates directly on AWS control-plane telemetry streams (CloudTrail, VPC Flow Logs, DNS logs), an attacker who gains `root` access inside an EC2 guest OS cannot disable GuardDuty telemetry collection.
* **Isolate Rather Than Terminate:** During incident response, isolating an instance via Security Group swap and capturing EBS Snapshots preserves crucial forensic evidence needed for Root Cause Analysis, whereas terminating the instance destroys evidence.
* **Cost Management in Lab Environments:** GuardDuty provides a 30-day Free Trial; students practicing SecOps labs should monitor the Usage tab in the GuardDuty console and disable the detector after completing their evaluation.
