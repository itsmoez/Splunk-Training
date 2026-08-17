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

A **SIEM** (Security Information and Event Management) is like an airport security control room or a master CCTV center for a giant building. It gathers thousands of different video feeds and data logs from every door, window, and hallway, puts them on one massive screen, and flags strange behavior for human guards to check out, The human guards being the Soc analysts.

## Examples of SIEM software in 2026

|Major SIEM platforms   | Their Focus       |
|:-------:      |---------     |
| Splunk Enterprise Security|Best for massive, complex enterprise data analytics and deep security operations customization|
|Microsoft Sentinel|Best for Azure and Microsoft 365-heavy enterprise environments, leveraging cloud scaling and Kusto Query Language (KQL).|
|Google Security Operations|Best for high-scale, cloud-native threat detection backed by Chronicle's large-scale log ingestion|
|CrowdStrike Falcon Next-Gen SIEM|Best for endpoint-driven ecosystems utilizing native XDR telemetry and AI triage workflows|
|Rapid7 InsightIDR|Best for lean security teams needing fast deployment and asset-based visibility|

## What is Splunk?

Every second, organisations generate massive amounts of machine data but without the right tools, this data remains untapped potential. Splunk Enterprise is a powerful data platform that helps organizations collect, analyze, and act on machine-generated data in real time, powering solutions across observability, security, IT operations, and business analytics.

## What can Splunk be used for? Why use it?

### CyberSecurity use cases

- **Splunk** provides tools for detecting, investigating, and responding to cyber threats.

**Example** : A financial instituition, like dueche bank, can use Splunk to track fraudulant transactions in real-time, saving millions in potential loses.

**Why it matters**: Correlating data across IT systems makes it easier to identify anomalies — which may be threats or attacks in action — before they escalate.

## IT Operations and AIOps use cases
- **Splunk** monitors IT infrastructure, identifies performance bottlenecks, and ensures systems run smoothly.

**Example** : E-commerce platforms use Splunk to prevent downtime during high-traffic events like Black Friday.

**Why It Matters**: Rapid troubleshooting reduces downtime, saving both time and money.

## Observability and monitoring use cases
- **Splunk** provides end-to-end visibility into applications, infrastructure, and user experiences.

**Example**: Healthcare providers monitor critical applications to ensure seamless patient care.

**Why it matters**: Observability helps resolve issues faster, enhancing user satisfaction and building brand trust.

## What is a Splunk/SOC analyst?

A Soc analyst is a frontline CyberSecurity Professional. Their job is to monitor an organization's networks, servers, and data 24/7 for cyber threats, investigate security alerts, and stop digital attacks before they cause harm.#

A Splunk analyst is an IT or security professional who uses Splunk, a powerful data platform, to collect, search, and analyze large amounts of machine-generated data

## What are the versions of Splunk and how are they different?

1. Splunk Enterprise
- Self hosted, on-premises (you manage the servers, storage, upgrades and scaling)
- Most flexible

2. Splunk Cloud Platform
- SaaS hosted by Splunk on cloud enviroments like aws or gcp
- Splunk manages infastructure and handles continuous background updates

3. Splunk SOAR
- SOAR - Security orchestration automation response software
- An independent automation and orchestration product used to execute automated response playbooks alongside security alerts

## What are the components of Splunk Architecture?

![Splunk arch image] (url)

**Universal Forwarders** - The first stage in Splunk is data collection. Splunk can ingest data from a variety of sources. Data collection is typically performed using forwarders, which are lightweight agents that can be installed on any machine that generates data. 

**Indexers** - The data is then stored and indexed. Splunk indexes the data by parsing it into individual events and extracting relevant fields, such as timestamps, source types, and host information. This process enables efficient searching and analysis of the data later on.

**Search Head** - After data is indexed, it can be searched and analyzed using Splunk’s powerful search language, the Search Processing Language (SPL). SPL allows users to perform a wide range of operations on the data, such as filtering, aggregation, correlation, and statistical analysis. Users can create custom reports, dashboards, and alerts based on the results of their searches and analyses.

*In simplier words*
remember these 3 components... 
1) Splunk Universal forwarder collects the logs and send it to Splunk indexer. 

2) Splunk indexer, indexes(ingests) the logs(it reads the logs, word by word, and write it down to flat files for searching)

3) Splunk Search head - its the webserver which provides the Splunk GUI login page, it reads the search requests from the users and send it to indexer. and collects the results from indexer, consolidates, reports it.

## What are some of the options for deploying Splunk (Search Head)?

The primary options for deploying a Splunk search head include a Standalone Search Head for small or test environments, a Distributed Search Head for standard multi-tier architectures, a Search Head Cluster (SHC) for high availability and scale, or Splunk Cloud Platform for a fully managed SaaS solution.

- **Standalone Search Head**
    - Best use: Small testing, proof-of-concept, or single-user environments.
    - Details: One single instance acts as both the search management interface and the data indexer.
    - Limitation: No high availability; resource-constrained for concurrent heavy searches.
    
- **Distributed Search Head (Non-Clustered)**
    - Best use: Mid-sized environments with a dedicated search tier separate from indexers.
    - Details: A dedicated machine handles user searches and coordinates queries across a pool of separate indexer peers.
    - Limitation: Acts as a single point of failure for users if that specific node goes down.
    
- **Search Head Cluster (SHC)**
    - Best use: Medium to large enterprise production environments requiring zero downtime.
    - Details: A group of three or more coordinated search head members sharing search workloads, saved jobs, and KV store data.
    - Management: Uses an external Deployer instance to push apps and configuration bundles safely across cluster members. Often paired with a third-party load balancer.

- **Splunk Cloud Platform**
    - Best use: Organizations preferring a fully managed, cloud-hosted architecture over on-premise infrastructure.
    - Details: Splunk manages the backend infrastructure, search head scaling, and upgrades natively in the cloud.

**What are some of the basic terms in Splunk?**

|Term|	Meaning|
|---|---|
|Event	|A single record. Usually one line of a log file. The basic unit of everything in Splunk.|
|Index|	Where events are stored. Like a folder or database table. You often search a specific index, for example index=wineventlo. Splitting data into indexes also controls who can see what.|
|Sourcetype	|The format of the data, which tells Splunk how to interpret it. Getting sourcetypes right at onboarding is one of the most important things you can do.|
|Source|	Where the data came from specifically, usually a file path or port, such as /var/log/auth.log.|
|Host|	The machine that produced the event.|
|Field|	A name and value pair extracted from an event, such as user=jsmith or status=404. Fields are what you search and calculate on.|
|_time|	The timestamp field. Splunk is built around time, and every event has one.
|_raw|	The original, unmodified text of the event.
|Bucket|	The physical directory an index is stored in. Buckets age through stages: hot (being written to), warm (recent, searchable), cold (older, on cheaper disk), frozen (deleted or archived), thawed (restored from archive).|

## What type of data/files does Splunk usually ingest?

Splunk can index any kind of data. However in particular splunk platform can index any and all:
- IT streaming, machine, and historical data, such as Microsoft Windows event logs, web server logs, live application logs
- network feeds
- metrics 
- change monitoring
- message queues
- archive files and so on

## How can Splunk onboard/ingest data? 

### Main Ingestion Methods

- Splunk Universal Forwarder: A lightweight agent installed on host machines (Windows, Linux) to read and forward log files securely.
    - What it is: A tiny, free software assistant.
    - How it works: You install it directly on your company's computer servers.
    - The simple analogy: It acts like a loyal mail carrier. It sits by your files, watches for new lines of text, and instantly mails them to Splunk.
    - Why use it: It is super lightweight, meaning it will not slow down your computers.

- HTTP Event Collector (HEC): A token-based, high-performance REST API endpoint allowing web apps, scripts, and devices to push JSON or raw text data directly over HTTP/HTTPS.
    - What it is: A secure, digital drop-box on the internet.
    - How it works: It gives your apps a specific web address and a secret password (called a token).
    - The simple analogy: It is like ordering a pizza online. Your app puts the data into a neat digital box (JSON format) and sends it straight to Splunk's address.
    - Why use it: It is incredibly fast for web apps and code to send data directly without saving it to a file first.

- Network Inputs (TCP/UDP/Syslog): Configure Splunk to listen on a specific network port to accept incoming syslog streams or raw socket data from firewalls and routers.
    - What it is: A digital listening post.
    - How it works: You open a specific network "channel" (a port) on Splunk. Network hardware sends data straight to that channel.
    - The simple analogy: This is like a radio station. Splunk tunes into a specific station frequency, and gadgets like internet routers or firewalls broadcast their data live into it.
    - Why use it: Perfect for network gear that cannot have extra software installed on them.

- Cloud Connectors & Add-ons: Use built-in integrations, Data Manager, or modular inputs to pull metrics and logs straight from cloud services like AWS, GCP, and Azure.
    - What it is: Pre-made digital bridges.
    - How it works: Splunk uses built-in tools to log into major cloud accounts like Amazon Web Services (AWS) or Microsoft Azure.
    - The simple analogy: Imagine giving Splunk permission to log into your cloud Google Drive to automatically grab files whenever they appear.
    - Why use it: Saves you from building complex setups to connect your cloud tools to Splunk.

- OpenTelemetry Collector: Use vendor-neutral OpenTelemetry agents to stream unified logs, metrics, and traces natively into the Splunk platform.

- Splunk Web Upload: Manually upload local static files (like CSV or small log samples) through the user interface for testing or ad-hoc analysis

## What are events?

In the simpliest terms, an event is when something has happened. In IT terms,an event represents a change in data. 
For example : 
    - a sensor signalling a change in temperature
    - a field changing in a database
    - a bank deposit being completed
    - a checkout button being clicked in an e-commerce app. 

Often, the sooner an enterprise knows about an event and can react, the better.

## What is SPL?

Search Processing Language is Splunk’s query language for searching, filtering, and transforming machine data.

SPL allows users to:
    - Search events
    - Filter data
    - Extract information
    - Transform results
    - Calculate statistics
    - Identify patterns
    - Create visualisations
    - SPL is particularly useful for SOC analysts because it allows large amounts of security data to be investigated efficiently.

SPL commands are commonly connected using the pipe (|) character.
```
Search → Filter → Transform → Analyse → Visualise
```

## Basic examples of SPL:

Search an index — returns events from the main index:
```
index=main
```

Search for failed Windows logins:
```
index=windows EventCode=4625
```
Event Code 4625 is commonly associated with failed Windows logon attempts. This type of search could help a SOC analyst investigate potential brute-force or account compromise activity.

Search for a specific host:
```
index=main host=server10
```
This searches for events generated by server10.

Search for a specific IP address:
```
index=firewall src_ip="172.568.1.40"
```
This searches firewall data for events associated with the specified source IP address.

Search using multiple conditions:
```
index=windows EventCode=4625 user="admin"
```
This searches for failed login events associated with the specified user.

## Basic SPL Transformations

SPL can be used to transform raw events into useful statistics and summaries.

Count events:
```
index=main
| stats count
```
This counts the number of events returned by the search.

Count events by user:
```
index=windows
| stats count by user
```
This groups events by user and counts the number of events associated with each user, which is useful for identifying accounts generating unusually high amounts of activity.

Find common source IP addresses:
```
index=firewall
| top src_ip
```
This identifies the source IP addresses appearing most frequently in the search results.

Display specific fields:
```
index=windows
| table user, host, EventCode
```
The table command displays selected fields in a table.

Sort results:
```
index=main
| sort -count
```

The sort command can be used to order search results.

Count events by host:
```
index=main
| stats count by host
```
This can help identify which systems are generating the largest number of events.

## Basic visualisations

Splunk searches can also be used to create visual representations of data.

Events over time:
```
index=main
| timechart count
```
The timechart command can be used to show how event volumes change over time. The results can be displayed as a line or column chart.

Events by action:
```
index=firewall
| stats count by action
```
The results could be displayed as a bar chart to compare different actions.

Events by user:
```
index=windows
| stats count by user
```
This can be displayed as a bar chart to compare activity between users.

## What are some of the things you can produce in Splunk (e.g. dashboards)?

Splunk can turn search results into different forms of analysis, monitoring and reporting.

|Output|	Purpose|
|---|---|
|Dashboards|	Provide an overview of important information|
|Reports|	Save searches for repeated or scheduled analysis|
|Alerts|	Notify analysts when defined conditions are met|
|Tables|	Display detailed event information|
|Charts|	Show patterns and trends|
|Single Values|	Display important metrics|
|Maps| Visualise geographically relevant data|

## Dashboards
Dashboards combine multiple searches and visualisations into a single interface, providing a centralised view of security activity.

For example, a SOC dashboard could display:

Allowed and blocked intrusion attempts
Alerts by severity, including critical, high, medium, low and informational
Intrusion signatures and their associated event counts
Attack sources and geographic locations
Alert trends over time
Visual summaries of intrusion activity
This allows security analysts to quickly monitor the current security posture, identify unusual activity and prioritise alerts for further investigation.

## Example Splunk Dashboard
![exaxmple](https://www.splunk.com/en_us/solutions/security-monitoring.html)
The following image demonstrates how multiple security-related visualisations can be presented together within a Splunk dashboard.


## What are Splunk apps vs Splunk addons?

## Case studies of Splunk being used?

## Security/SOC
Splunk Use Cases and Case Studies
Splunk can be used across cybersecurity, IT operations, business analysis and other areas.

Security / SOC
In a SOC, Splunk can be used to:

Monitor authentication activity
Detect brute-force attacks
Investigate suspicious IP addresses
Monitor endpoint activity
Detect unusual network behaviour
Support threat hunting
Investigate security incidents
Create security dashboards
Generate alerts

## Data/business analysis
Business and Data Analysis
Splunk can analyse machine-generated business data to identify trends and patterns.

Potential uses include:

Transaction monitoring
Customer activity analysis
Operational metrics
Business performance monitoring
Identifying unusual transaction behaviour
Tracking key performance indicators
Other Uses
Additional Splunk use cases include:

Cloud monitoring
Application monitoring
Compliance
Fraud detection
DevOps monitoring
Infrastructure monitoring

## IT Operations
Splunk can also be used by IT and operations teams to monitor infrastructure and applications.

Examples include:

Server errors
Application failures
Network problems
System performance
Service availability
Troubleshooting incidents
Infrastructure monitoring
This can help organisations identify problems before they significantly affect users or services.

## Best practices for securing data on Splunk?

Splunk environments can contain sensitive information such as usernames, IP addresses, authentication records and application data. Protecting the Splunk environment is therefore important.

Key practices include:

Apply least privilege
Use Role-Based Access Control (RBAC)
Enable strong authentication and MFA where available
Restrict administrative access
Encrypt communications between Splunk components
Protect sensitive indexes
Regularly patch Splunk components
Monitor administrative activity
Maintain appropriate data retention policies
Avoid unnecessarily collecting sensitive information
Restrict access to sensitive searches, dashboards and data
Security controls should be appropriate to the organisation's environment, data sensitivity and compliance requirements.

## Splunk certification path? Certifications related to or helpful for SOC?

Splunk provides training and certifications covering different levels of Splunk knowledge and specialist areas.

A learning progression can move from foundational knowledge towards more advanced user, administration, development and security-focused skills.

```
Splunk Fundamentals
        │
        ▼
Core Splunk Knowledge
        │
        ▼
Advanced Searching
        │
        ├───────────────┐
        ▼               ▼
 Administration      Development
        │
        ▼
Advanced / Specialist Skills
        │
        ▼
Security-focused Splunk Skills
```

For someone interested in SOC and cybersecurity, useful areas to develop alongside Splunk knowledge include:

|Certification / Area|	Relevance to SOC|
|---|---|
|Splunk Certifications|	Develops practical knowledge of the Splunk platform|
|CompTIA Security+|	Provides broad cybersecurity fundamentals|
|CompTIA CySA+|	Focuses on security monitoring, detection and incident response|
|Microsoft Security Certifications|	Useful for Microsoft-focused SOC environments|
|Vendor-specific SIEM Training|	Develops knowledge of other security monitoring platforms|

Certifications are most valuable when supported by practical labs, investigation exercises and experience analysing realistic security data.

