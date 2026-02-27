# 🚀 DevOps Journey

A hands-on learning and documentation repository tracking my progression from DevOps fundamentals through real-world cloud deployments. This repo captures practical notes, lab exercises, and project documentation built while working toward a career in DevOps engineering.

## 📋 Table of Contents
- [About](#about)
- [Skills & Technologies](#skills--technologies)
- [Projects](#projects)
- [Learning Notes](#learning-notes)
- [Repository Structure](#repository-structure)

---

## About

This repository documents my self-driven DevOps learning journey — from Linux fundamentals and networking basics through deploying a live 2-tier LAMP application on AWS. Each folder represents a topic area with notes and practical exercises.

---

## Skills & Technologies

| Category | Technologies |
|----------|-------------|
| **Cloud** | AWS (EC2, Security Groups, IAM) |
| **Linux** | Bash, file permissions, process management, SSH |
| **Networking** | TCP/IP, DNS, HTTP/HTTPS, SSL/TLS |
| **Web Servers** | Apache (httpd), Nginx basics |
| **Databases** | MariaDB / MySQL |
| **Languages** | Python, Node.js, Java basics |
| **Version Control** | Git, GitHub |
| **Containers** | Docker (in progress) |
| **CI/CD** | Jenkins, GitHub Actions (in progress) |
| **IaC** | Terraform (in progress) |
| **Architecture** | 12-Factor App methodology, 2-tier architecture |

---

## Projects

### 🌐 2-Tier LAMP Stack on AWS
> Deployed a production-style e-commerce web application on AWS EC2

- **Stack:** Apache + PHP (web tier) + MariaDB (database tier) on Amazon Linux 2023
- **Cloud:** AWS EC2 (t3.micro), Security Groups, SSH key-based access
- **Highlights:** Database hardening (not publicly exposed), service management with `systemctl`, live browser-verified deployment
- 📄 [View Deployment Documentation](devops_prerequisites/2_tier_application/lamp-aws-deployment/README.md)

---

## Learning Notes

| Topic | Description |
|-------|-------------|
| [DevOps Fundamentals](fundamentals_of_devops/fundamentals_of_devops.md) | Core DevOps concepts, culture, and practices |
| [Linux Basics](devops_prerequisites/Linux/Linux.md) | File system, commands, permissions, shell scripting |
| [Linux Advanced](devops_prerequisites/Linux/Linux2.md) | Process management, networking commands, advanced shell |
| [Networking](devops_prerequisites/Networking_basics/Networking.md) | TCP/IP, DNS, OSI model, ports and protocols |
| [Web Servers](devops_prerequisites/Webserver/webserver_baics.md) | Apache, Nginx configuration and management |
| [Databases](devops_prerequisites/Databases/databases_basics.md) | MySQL/MariaDB operations and administration |
| [SSL/TLS](devops_prerequisites/Databases/ssl_tls.md) | Certificate management and HTTPS fundamentals |
| [Git](devops_prerequisites/GIT/git_tool.md) | Version control workflow, branching, collaboration |
| [YAML & JSON](devops_prerequisites/yaml_json/yaml_json.md) | Configuration file formats used across DevOps tooling |
| [Node.js](devops_prerequisites/NODEJS/nodejs.md) | JavaScript runtime fundamentals |
| [Python](devops_prerequisites/NODEJS/Python/python.md) | Python scripting for automation |
| [Java](devops_prerequisites/JAVA/java_basics.md) | Java basics for understanding enterprise applications |
| [DevOps Tools Overview](devops_prerequisites/devopstools/devopstools.md) | Survey of the DevOps toolchain |
| [12-Factor App](12Factorapp/12factorapp.md) | Cloud-native application design methodology |
| [Week 1 - Linux](notes/week1-linux/linux-basics.md) | Hands-on Linux command practice notes |
| [Week 2 - SSH](notes/week2-ssh/ssh-basics.md) | SSH setup and remote access fundamentals |

---

## Repository Structure

```
devops-journey/
├── 12Factorapp/                    # 12-Factor App methodology notes
├── devops_prerequisites/           # Foundation topics
│   ├── 2_tier_application/         # LAMP stack project + AWS deployment docs
│   ├── Databases/                  # MySQL/MariaDB & SSL/TLS
│   ├── GIT/                        # Git version control
│   ├── JAVA/                       # Java fundamentals
│   ├── Linux/                      # Linux commands & administration
│   ├── Networking_basics/          # Networking concepts
│   ├── NODEJS/                     # Node.js & Python
│   ├── Webserver/                  # Apache/Nginx
│   ├── devopstools/                # DevOps tool survey
│   └── yaml_json/                  # YAML and JSON
├── fundamentals_of_devops/         # Core DevOps principles
└── notes/                          # Weekly study notes
    ├── week1-linux/
    └── week2-ssh/
```

---

## License

This repository is licensed under the MIT License.