Splunk SOC Project – SSH, Web and Cloudflare Log Analysis

About This Project
In this project, I built a simple SOC-style monitoring setup using Splunk to understand how real-world security teams detect and analyze threats.

I worked on three different types of logs:

* SSH logs for attack detection
* Apache web logs for traffic monitoring
* Cloudflare-style logs generated using Python

This project helped me gain hands-on experience with log analysis, writing SPL queries, and building dashboards.

---

Tools Used

* Splunk Enterprise
* Python for generating Cloudflare logs
* JSON log files
* SPL (Search Processing Language)

---

Use Case 1: SSH Brute Force Detection

I analyzed SSH logs to detect brute force login attempts.

What I Did:

* Filtered failed login attempts
* Identified IPs with multiple failures
* Grouped activity by IP and username
* Built a dashboard to visualize attacks

Example Query:

```spl
index=main source="ssh_logs_new.json" sourcetype="_json" event_type="Failed SSH Login"
| stats count by src_ip, user
| where count > 5
| sort -count
```

---

GeoIP-Based Attack Visualization

To make the project more realistic, I added GeoIP analysis.

What I Did:

* Extracted attacker IPs
* Used iplocation to find country
* Visualized attacks on a map

This helped identify where attacks are coming from globally.

---

Use Case 2: Web Traffic Monitoring (Apache Logs)

I analyzed Apache logs to understand user activity and detect anomalies.

What I Did:

* Counted total requests
* Analyzed HTTP status codes
* Identified top IPs and URLs
* Created traffic trends

Example Query:

```spl
index=main source="apache_logs.json" host="webserver"
| timechart count
```

---

Use Case 3: Cloudflare Log Analysis (Custom Generated)

I generated Cloudflare-style logs using Python to simulate real-world web security monitoring.

What I Did:

* Created structured JSON logs
* Simulated requests, IPs, and status codes
* Ingested logs into Splunk
* Analyzed traffic and behavior

What I Analyzed:

* Request patterns
* Suspicious IP activity
* Status code distribution
* Traffic spikes

This part shows my ability to not only analyze logs but also generate realistic datasets.

---

Dashboards Created

* SSH attack detection dashboard
* Web traffic monitoring dashboard
* Cloudflare traffic analysis dashboard

---

Project Structure

```
SOC-Splunk-Web-Monitoring/
│
├── logs/
│   └── apache_logs.json
│
├── queries/
│   └── spl_queries.txt
│
├── dashboards/
│   └── dashboard_screenshots.png
│
└── README.md
```

---

Data Used

* SSH and Apache logs from cybersecurity training datasets
* Cloudflare logs generated using Python
* Used for educational and demonstration purposes

---

What I Learned

* Working with Splunk for SIEM use cases
* Writing SPL queries for detection
* Detecting brute force attacks
* Analyzing web traffic
* Creating dashboards
* Using GeoIP for visualization
* Generating custom log datasets

---

Final Thoughts
This project gave me practical exposure to how SOC analysts monitor systems, detect attacks, and analyze logs. It also helped me understand how different log sources can be combined for better visibility.

---

Future Improvements

* Add real-time alerting
* Automate responses
* Integrate threat intelligence
* Expand detection rules

---
