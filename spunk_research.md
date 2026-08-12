## What is a SOC?

 A Security Operations Centre (SOC) is a team + technology setup that monitors, detects, investigates, and responds to cyber threats in an organisation. 
 
```
Think of it as the “security control room” for a company.
```

## Key Functions of a SOC

- **Monitoring** – Watch logs(various), alerts, events and systems 24/7

- **Detection** – Spot suspicious or malicious activity- I.E if someone is trying to log in 10 times in a minute, might be a brute force attack

- **Investigation** – Analyse alerts to understand what happened

- **Response** – Contain and fix security incidents

- **Threat Hunting** – Actively search for hidden threats

- **Reporting** – Document incidents and improvements

- **Improvement** – Tune rules, update playbooks, reduce false positives (CI/CD continuous improvement)

## Common SOC Technologies

**SIEM** means (Security Information & Event Management)  
e.g., Splunk, Microsoft Sentinel, QRadar
- Purpose: Collects logs + correlates events + parses unreadable or hard to read event data so its readable

**EDR/XDR** (Endpoint Detection & Response)  
e.g., Defender for Endpoint, CrowdStrike
Detects suspicious behaviour on devices

**SOAR** (Security Orchestration, Automation & Response)  
e.g., Sentinel SOAR, Cortex XSOAR
- Automates responses by executing predefined response playbooks

**Firewalls / IDS / IPS** 
Network protection + intrusion detection

**Threat Intelligence Platforms**  
e.g., MISP, Recorded Future
Provides attacker info, IOCs

**Cloud Security Tools**  
e.g., Defender for Cloud, AWS GuardDuty

## SOC Processes

**Log Collection** – Gather logs from servers, apps, cloud, endpoints

**Alerting** – SIEM detects patterns and triggers alerts

**Triage** – Analysts check severity + urgency

**Investigation** – Deep dive into logs, endpoints, network

**Containment** – Block IPs, isolate machines, reset credentials

**Eradication** – Remove malware, patch vulnerabilities

**Recovery** – Restore systems, verify safety

**Post‑Incident Review** – Lessons learned + improvements

## Common SOC Challenges

**Too many alerts** (alert fatigue) - Security tools generate enormous volumes of alerts daily, many of which turn out to be false positives. Sorting through thousands of notifications can easily become overwhelming for analysts, increasing the risk that critical warnings get overlooked.

**False positives** - a false postive is an alert triggered by a security tool that flags safe, normal activity as a cyber or malicious attack.

**Lack of skilled analysts** - The cyber industry faces a significant skill gap. Experienced and qualified cyber workers are expensive to hire because the demand is high, making retention and recruitment difficult.

**Poor log quality or missing logs**

**Slow response times**

**Complex cloud environments**

**Keeping up with new threats**

## SoC Best practices

Effective security operations centre best practices focus on balancing people, processes, and technology to reduce adversary dwell time. They do this by using:

- Tiered Structure: Clearly seperate responsibilities into seperate tiers, I.E Tier 1 (Triage and monitoring), Tier 2(deep investigation and analysis) and Tier 3(advanved forensic and detection engineering)

- Combat burnout : Rotate shifts fairly, automate repetitive tasks

## SoC roles

| **SoC Tier** | **What the Tier entails** |
| ---      | ---                   |
| Tier 1   | acts as frontline triage unit watching alerts |
| Tier 2   | investigates real threats and manages containment |
| Tier 3   | handles complex incidents while building long term defensive rules |

## What is threat hunting

**Threat hunting** is a proactive approach to identify previously unknown or currently ongoing cyber threats in a organisation.

## Common Event types to look out for

- **Security breaches** - The SOC may send an alert if it detects a security breach, such as unauthorized access to a network or system, or if it receives notification of a breach from an external source. A few examples of security breaches would include unauthorized access attempts, malware infections, Denial of Service (DOS) attacks, and data exfiltration attempts.

- **Vunerabilities** - You might be alerted if the SoC detects vunerabilities in your organisation or application that could be exploited by an attacker. Examples of this are Weak data encryption, weak authorisation credentials and unpatched software. 

- **Suspicious activity**
- **Compliance violations**
- **System failures**
- **Threat intelligence**

## What is SIEM?

SIEM Stands for **Security information & Events management**. 

Its a system/software that monitors your organisation for security by collectings logs and event data. Log/Event data is a digital record of events occuring within a system, application or a network device or endpoint. Its mostly machine generated. For example, what ever a user does on their computer on a website a company own, they can see what has been done from the computer because of the log/event data it produces.

SIEM acts as a central source for collecting, storing and analysing all of that log and alert data together. It also parses that data so its more human readable. 

## SIEM analogy

![CCTV image](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQ32lPMrH6HdnTQ_GQtdTZ-_OH-U53cQ7glG5XTwnqrRw&s=10)

A **SIEM** (Security Information and Event Management) is like an airport security control room or a master CCTV center for a giant building. It gathers thousands of different video feeds and data logs from every door, window, and hallway, puts them on one massive screen, and flags strange behavior for human guards to check out.