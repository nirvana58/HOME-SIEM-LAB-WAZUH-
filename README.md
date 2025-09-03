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

1. **Clone the Repository**
   ```bash
   git clone https://github.com/yourusername/wazuh-siem-homelab.git
   cd wazuh-siem-homelab
   ```

2. **Set up Virtual Machine**
   ```bash
   # Follow the VM setup guide
   ./scripts/setup-vm.sh
   ```

3. **Install Wazuh Manager**
   ```bash
   # Run on Ubuntu VM
   sudo ./scripts/install-wazuh-manager.sh
   ```

4. **Install Wazuh Agent**
   ```powershell
   # Run on Windows host
   .\scripts\install-wazuh-agent.ps1
   ```

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
- [x] Privilege escalation detection



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

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- Wazuh team for the excellent open-source SIEM platform
- Security community for sharing knowledge and best practices
- Oracle VirtualBox team for reliable virtualization

## 📞 Contact

- **Project Maintainer**: [Your Name]
- **Email**: your.email@example.com
- **LinkedIn**: [Your LinkedIn Profile]

---

**⭐ If this project helped you learn about SIEM implementation, please give it a star!**
