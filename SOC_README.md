# SOC NIST CSF Compliance Monitoring & Dashboard

![SOC Dashboard](https://img.shields.io/badge/SOC-Dashboard-blue)
![NIST CSF](https://img.shields.io/badge/NIST-CSF-green)
![Python](https://img.shields.io/badge/Python-3.8%2B-yellow)
![License](https://img.shields.io/badge/License-MIT-lightgrey)

A comprehensive Security Operations Center (SOC) monitoring solution that analyzes security logs, maps them to NIST Cybersecurity Framework (CSF) functions, and provides real-time interactive dashboards with compliance reporting.

## 👨‍💻 Author

**Nelson Mbua Mosisah**  
*CyberSecurity Analyst & Project Developer*  
📧 Email: nelson.mosisah@outlook.com  
🔗 LinkedIn: [Nelson Mbua Mosisah](https://linkedin.com/in/nelsonmbua)  
🐙 GitHub: [@nelsonmbua](https://github.com/nelsonmbua)

> *This project was prepared and carried out by Nelson Mbua Mosisah as part of advanced SOC monitoring and compliance automation initiatives.*

## 🚀 Features

### 📊 Interactive Dashboard
- **Real-time Monitoring Charts**: Live event tracking, system metrics, and threat distribution
- **NIST CSF Compliance Mapping**: Visual representation of security control coverage
- **Severity Analysis**: Critical/High/Medium/Low event classification
- **Gap Detection**: Identify missing Respond/Recover capabilities
- **Priority Alerting**: Automated detection of high-risk security events

### 🔍 Security Analysis
- **Log Analysis**: Parse and analyze security logs from multiple sources
- **Correlation Detection**: Identify related security events (e.g., brute-force → account lockouts)
- **Noise Reduction**: Detect and flag noisy alert sources for tuning
- **Compliance Reporting**: Generate NIST CSF compliance reports

### 🔄 SIEM Integration
- **Multi-SIEM Support**: Splunk HEC, Elasticsearch, Generic Webhook
- **Real-time Alerting**: Automated priority event notifications
- **Report Indexing**: Store analysis results in your SIEM
- **Flexible Configuration**: Easy setup for various SIEM environments

## 📋 Prerequisites

- Python 3.8 or higher
- Required packages: `pandas`, `requests`

## 🛠 Installation

1. **Clone the repository**:
   ```bash
   git clone https://github.com/nelsonmbua/soc-nist-csf-monitoring.git
   cd soc-nist-csf-monitoring
Install dependencies:

bash
pip install pandas requests
Configure your environment:

Edit the CONFIG section in the script

Set up SIEM endpoints and credentials

Configure log sources and alerting rules

⚙️ Configuration
Basic Setup
Modify the CONFIG dictionary in the script:

python
CONFIG = {
    'LOG_PATH': None,  # Set to your log file path or use embedded sample
    'SIEM': {
        'TYPE': 'noop',  # Options: 'splunk', 'elastic', 'webhook', 'noop'
        # ... SIEM-specific configurations
    },
    'ALERT': {
        'PRIORITY_SEVERITIES': ['Critical', 'High'],
        'SEND_ALERTS': True,
        # ... Alerting configurations
    },
    'REPORT_PATH': '/tmp/soc_nist_csf_report.html',
    'RUN_ONCE': True,  # Set to False for continuous monitoring
}
SIEM Configuration Examples
Splunk HEC
python
'SPLUNK_HEC': {
    'HEC_ENDPOINT': 'https://your-splunk-server:8088/services/collector',
    'TOKEN': 'your-splunk-token',
    'VERIFY_TLS': True,
    'INDEX': 'soc_analysis',
    'SOURCETYPE': 'soc:nist_csf_report'
}
Elasticsearch
python
'ELASTIC': {
    'URL': 'http://your-elasticsearch:9200',
    'INDEX': 'soc-nist-csf',
    'USERNAME': 'your-username',
    'PASSWORD': 'your-password'
}
🎯 Usage
Basic Execution
bash
python soc_nist_csf_siem_integration.py
With Custom Log File
bash
python soc_nist_csf_siem_integration.py --log-path /path/to/your/logs.csv
Continuous Monitoring Mode
Set RUN_ONCE: False in configuration for 24/7 monitoring.

Docker Execution
bash
docker build -t soc-monitor .
docker run -v /path/to/logs:/app/logs soc-monitor
📈 Dashboard Features
Real-time Monitoring
Events Per Minute: Live tracking of security event volume

System Metrics: CPU, memory, and network utilization

Threat Distribution: Current threat landscape visualization

Live Alerts: Real-time security alert feed

NIST CSF Compliance
Function Coverage: Identify, Protect, Detect, Respond, Recover

Gap Analysis: Missing security capabilities

Recommendations: Actionable security improvements

Security Analytics
Severity Distribution: Critical/High/Medium/Low event breakdown

Source Analysis: Log type and source distribution

Timeline Analysis: Event patterns over time

🔧 Customization
Adding New Log Sources
Ensure your CSV has these columns:

Timestamp, LogType, Source, Severity, EventDescription, NIST_CSF_Function

Update the EMBEDDED_CSV variable or provide a file path in LOG_PATH

Custom Alert Rules
Modify the ALERT_ON_EVENTS_CONTAINING list:

python
'ALERT_ON_EVENTS_CONTAINING': [
    'Unauthorized USB',
    'PowerShell',
    'Brute-force',
    # Add your custom patterns
]
Extending SIEM Support
Implement new SIEM clients by extending the SIEMClient base class.

🗂 Project Structure
text
soc-nist-csf-monitoring/
├── soc_nist_csf_siem_integration.py  # Main script
├── README.md                         # This file
├── requirements.txt                  # Python dependencies
├── config/                          # Configuration files
│   ├── splunk.json                  # Splunk configuration
│   └── elasticsearch.json           # Elasticsearch configuration
├── samples/                         # Sample data
│   └── sample_logs.csv              # Example log format
└── docs/                           # Documentation
    └── deployment-guide.md         # Deployment instructions
🐳 Docker Support
Build the Image
bash
docker build -t soc-nist-monitor .
Run Container
bash
docker run -d \
  -v /host/logs:/app/logs \
  -v /host/config:/app/config \
  -p 8080:8080 \
  soc-nist-monitor
📊 Sample Output
The script generates:

Interactive HTML Dashboard (/tmp/soc_nist_csf_report.html)

SIEM Indexed Reports (if configured)

Priority Alerts for critical security events

Compliance Recommendations based on NIST CSF gaps

🛡 NIST CSF Mapping
The tool maps security events to these NIST CSF functions:

Function	Description	Example Events
Identify	Asset management, business environment	Asset discovery, vulnerability scans
Protect	Access control, awareness training	Firewall blocks, phishing prevention
Detect	Anomalies and events, continuous monitoring	IDS alerts, EDR detections
Respond	Response planning, communications	Incident response, playbook execution
Recover	Recovery planning, improvements	Backup restoration, system recovery
🔍 Use Cases
Security Compliance
NIST CSF compliance reporting

SOC 2 control mapping

Regulatory requirement validation

Operational Monitoring
Real-time security event tracking

Alert noise reduction

Security control effectiveness

Incident Response
Priority event detection

Response capability assessment

Playbook execution tracking

🏆 Project Highlights by Nelson Mbua Mosisah
This project demonstrates several key cybersecurity competencies:

Advanced Log Analysis: Developed sophisticated parsing and correlation algorithms

Real-time Dashboard: Created interactive visualization with live data updates

SIEM Integration: Built extensible connectors for multiple security platforms

Compliance Automation: Automated NIST CSF mapping and gap analysis

Scalable Architecture: Designed for enterprise-level deployment

🤝 Contributing
Fork the repository

Create a feature branch (git checkout -b feature/amazing-feature)

Commit your changes (git commit -m 'Add amazing feature')

Push to the branch (git push origin feature/amazing-feature)

Open a Pull Request

📝 License
This project is licensed under the MIT License - see the LICENSE file for details.

🙏 Acknowledgments
Nelson Mbua Mosisah - Project development and implementation

NIST Cybersecurity Framework

Pandas for data analysis

Chart.js for interactive visualizations

Security community for best practices and inspiration

📞 Support
For issues and questions:

Check the documentation

Open a GitHub Issue

Contact the maintainer: Nelson Mbua Mosisah

Note: This tool was developed by Nelson Mbua Mosisah for security monitoring and compliance assessment. Always test in non-production environments first and ensure proper authorization before monitoring production systems.

📫 Contact Nelson Mbua Mosisah
Email: nelson.mosisah@outlook.com

LinkedIn: Nelson Mbua Mosisah

GitHub: nelsonmbua

Portfolio: nelsonmbua.dev

"Building secure systems through innovative automation and comprehensive monitoring." - Nelson Mbua Mosisah
Just so you know Thanks goes to BNS CyberLab for giving me the platform to better inprove my skills as a Cybersecurity Professional.
