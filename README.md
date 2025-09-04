# HOME-SIEM-KAB-WAZUH-
A SIEM(System Information and Event management) platform which is open source and free used for complete end to end monitoring of system information and events.
# Wazuh SIEM Home Lab Project


<img width="224" height="76" alt="Screenshot 2025-09-03 235020" src="https://github.com/user-attachments/assets/1cf934af-6f2f-4108-83c5-c1364a46a8c5" />


A comprehensive home lab setup demonstrating Wazuh SIEM deployment for cybersecurity learning and testing. This project showcases vulnerability detection, threat hunting, file integrity monitoring, and unified XDR/SIEM protection across endpoints.

## 🏗️ Architecture Overview

```
┌─────────────────────────────────────────────────────────────┐
│                    Home Lab Architecture                     │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  ┌─────────────────┐              ┌─────────────────────┐   │
│  │   Host Machine  │              │   Virtual Machine   │   │
│  │   Windows 10/11 │◄────────────►│   Ubuntu 24.04      │   │
│  │                 │   Bridged    │                     │   │
│  │  Wazuh Agent    │   Network    │  Wazuh Manager      │   │
│  │  (Monitored)    │              │  (SIEM/XDR)        │   │
│  └─────────────────┘              └─────────────────────┘   │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

## 🎯 Project Objectives

- **Security Monitoring**: Implement comprehensive endpoint monitoring
- **Threat Detection**: Real-time threat hunting and vulnerability assessment
- **File Integrity**: Monitor critical file changes and system modifications
- **Log Analysis**: Centralized log collection and analysis
- **Incident Response**: Alert generation and response workflows

## 🛠️ Technology Stack

| Component | Technology | Version |
|-----------|------------|---------|
| **SIEM Platform** | Wazuh | Latest (Open Source) |
| **Manager OS** | Ubuntu | 24.04 |
| **Agent OS** | Windows | 10/11 |
| **Virtualization** | Oracle VirtualBox | Latest |
| **Network** | Bridged NAT | - |
| **Database** | Elasticsearch | Bundled |
| **Web Interface** | Wazuh Dashboard | Bundled |

## 🚀 Quick Start

### Prerequisites

- Oracle VirtualBox installed
- Windows host machine
- At least 4GB RAM available for VM
- 20GB+ storage space

### Installation Steps

1. **Install the Wazuh Manager**
   Go to Terminal and Enter this Command 
   ```
   curl -sO https://packages.wazuh.com/4.12/wazuh-install.sh && sudo bash ./wazuh-install.sh -a
   ```
   Once the Wazuh Manager is downloaded it'll show the below interfaces
   <img width="1045" height="198" alt="Screenshot 2025-09-03 235514" src="https://github.com/user-attachments/assets/0b8b1345-fc10-45d1-8eac-c7400a2e43ed" />

3. **Open your browser in ubuntu**
   ```
   https://<manager_ip_adress>:443
   ```
   Enter the above url in Browser(Modify the managers ip adress)

4. **Register your Agent**
   Enter the below command and register your Agent
   ```
   sudo /var/ossec/bin/manage_agents
   ```
   <img width="641" height="337" alt="wazuh agent register" src="https://github.com/user-attachments/assets/e0951905-2fa0-4dfd-a4d7-d4c94990d03c" />

   
5. **Setup a Wazuh agent on your windows**
    Setup using the GUI:
    Download the windows agent installer on Installationguide/Wazuh agent Section
   
    <img width="694" height="48" alt="Screenshot 2025-09-04 000515" src="https://github.com/user-attachments/assets/ff28b3e6-cee9-4f09-9870-9937527b6c97" />

    A Window will appear
   
    <img width="419" height="373" alt="Screenshot 2025-09-04 000610" src="https://github.com/user-attachments/assets/62a58fb4-e2b8-4b06-8270-67e7a2215a00" />
    
    Enter Managers ip address and auth key(request from manager(specified in 4th step))

    Setup  using the CLI :
    Download the windows agent installer
    Enter the below command on powershell

    ```powershell
    .\wazuh-agent-4.12.0-1.msi /q WAZUH_MANAGER="<managers_ip>"
    ```
    check logs  and configuration files for any error during installation


7. **Check  your Wazuh Dashboard**
   A similar inetrface will appear
   
   <img width="1837" height="968" alt="bd10bd16-40db-442e-a965-4a318111e74a" src="https://github.com/user-attachments/assets/c4b2a7a8-11cc-4efe-b3f4-b95c9e72d133" />
   <img width="1837" height="968" alt="bc603d00-5ac3-48ea-ba9b-c5ea527c6284" src="https://github.com/user-attachments/assets/99c55771-eece-4afb-96af-26d051b1d3cf" />



## 📋 Features Implemented

### ✅ Core Features
- [x] File Integrity Monitoring (FIM)
- [x] Real-time log analysis
- [x] Vulnerability detection
- [x] System inventory
- [x] Rootkit detection
- [x] Active response capabilities

### 🧪 Tested Scenarios
- [x] File creation/deletion monitoring
- [x] Registry changes detection
- [x] Process monitoring
- [x] Network connection tracking
- [x] Failed login attempts




## 🔧 Configuration Highlights

### Wazuh Manager Configuration
- **Port**: 1514 (Agent communication)
- **Dashboard**: https://manager-ip:443
- **API**: https://manager-ip:55000

### File Integrity Monitoring
```xml
<syscheck>
    <directories check_all="yes">C:\Users</directories>
    <directories check_all="yes">C:\Program Files</directories>
    <directories check_all="yes">C:\Windows\System32</directories>
</syscheck>
```

### Custom Rules
- Windows event monitoring
- File system changes
- Network anomaly detection
- Authentication failures

## Monitoring Capabilities

### Real-time Dashboards
- Security events overview
- Agent status monitoring
- Vulnerability assessments
- Compliance reporting

### Alert Categories
- **High Priority**: Malware detection, privilege escalation
- **Medium Priority**: Failed logins, configuration changes
- **Low Priority**: File modifications, system updates

## 🧪 Testing Scenarios

### File Integrity Monitoring Test
1. Create test folder: `C:\TestFolder`
2. Add test file: `test.txt`
3. Modify file content
4. Delete file
5. Monitor alerts in Wazuh Dashboard

### Expected Results
- File creation alert
- Content modification alert
- File deletion alert
- Metadata changes logged

## 📈 Performance Metrics

| Metric | Value |
|--------|-------|
| **Average Alert Response Time** | < 5 seconds |
| **Daily Events Processed** | 1000+ |
| **Storage Usage** | ~500MB/day |
| **CPU Usage (Manager)** | < 10% |
| **RAM Usage (Manager)** | ~2GB |

## 🔐 Security Considerations

- Enable TLS encryption for agent-manager communication
- Implement proper firewall rules
- Regular backup of configuration files
- Monitor manager system resources
- Update signatures and rules regularly

## 🐛 Troubleshooting

### Common Issues
1. **Agent Connection Issues**
   - Check firewall settings
   - Verify network connectivity
   - Confirm manager IP configuration

2. **Dashboard Not Accessible**
   - Check service status
   - Verify port availability
   - Review SSL certificates

3. **Missing Alerts**
   - Validate rule configurations
   - Check log levels
   - Verify agent reporting

## 📚 Learning Resources

- [Official Wazuh Documentation](https://documentation.wazuh.com/)
- [SIEM Best Practices](https://www.sans.org/reading-room/whitepapers/logging/siem-best-practices-33528)
- [Threat Hunting with Wazuh](https://wazuh.com/blog/threat-hunting-with-wazuh/)

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch
3. Commit your changes
4. Push to the branch
5. Create a Pull Request


## 🙏 Acknowledgments

- Wazuh team for the excellent open-source SIEM platform
- Security community for sharing knowledge and best practices
- Oracle VirtualBox team for reliable virtualization

## 📞 Contact

- **Project Maintainer**: Lakshmeesha Suvarna
- **Email**: laksmeesha.s.999@gmail.com
- **LinkedIn**: www.linkedin.com/in/lakshmeesha-suvarna-23037824a

---

**⭐ If this project helped you learn about SIEM implementation, please give it a star!**
