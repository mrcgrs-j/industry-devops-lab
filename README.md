# Industry DevOps Lab

**Industrial Automation · OT/IT Integration · DevOps · Cloud · Data Engineering**

A hands-on engineering lab integrating industrial automation with modern IT infrastructure, software engineering, and cloud technologies.

The project combines a physical Siemens PLC and HMI with a virtualized Linux environment. It is being developed incrementally, with an emphasis on practical implementation, reliable data acquisition, automation, observability, security, and technical documentation.

The repository serves as both an engineering project and a technical portfolio demonstrating practical skills across industrial automation, IT infrastructure, and DevOps.

---

## Project at a Glance

| Area | Scope |
|---|---|
| **OT / Industrial Automation** | Industrial electrical systems, PLC programming, PID control, HMI design, process simulation |
| **IT Infrastructure** | Linux administration, networking, VMware ESXi on Arm (Fling), Docker, infrastructure automation with Ansible |
| **OT/IT Integration** | Industrial communication protocols, direct S7 communication, OPC UA, MQTT, Node-RED, Python |
| **DevOps** | Git, CI/CD, automated testing, containerization, deployment automation |
| **GitLab** | Source control, GitLab CI/CD, runners, pipelines, artifact management |
| **Cloud / AWS** | AWS IoT Core, MQTT-based telemetry ingestion, Amazon S3, IAM, secure cloud integration; optional AWS IoT SiteWise and Lambda |
| **Data Engineering / Analytics** | Industrial telemetry, Python data processing, CSV and database storage, Power BI dashboards, historical analysis |
| **Machine Learning** | Data preprocessing, feature engineering, model evaluation, anomaly detection |
| **Observability / Security** | Prometheus, Grafana, Loki, alerting, network security, access control |

**Current focus:** temperature process simulation and PID control using a Siemens SIMATIC S7-1200 PLC and a KTP600 Basic HMI panel.

Other capabilities will be introduced progressively and documented as implemented only after verification.

---

## 1. OT — Industrial Automation

**Focus:** PLC-based process control, industrial hardware, and operator interfaces.

### Current scope

- Siemens SIMATIC S7-1200 CPU 1212C DC/DC/DC
- Siemens KTP600 Basic mono PN HMI
- Temperature process simulation
- PID-based temperature regulation
- Temperature setpoint configuration
- Process monitoring and HMI trend visualization
- Process data acquisition for further analysis

### Engineering objectives

- Document the control logic and process variables.
- Validate controller behavior under changing setpoints and disturbances.
- Evaluate process response and control performance.
- Maintain a clear separation between process control and external data processing.

### Documentation

- [PLC and HMI](docs/04-plc-and-hmi.md)
- [Electrical System and Hardware](docs/03-electrical-system.md)

---

## 2. IT — Infrastructure and Networking

**Focus:** building and maintaining the infrastructure that supports the laboratory.

### Infrastructure

- Raspberry Pi 5
- VMware ESXi on Arm (Fling)
- Linux virtual machines
- Windows 11 engineering workstation in VirtualBox
- Siemens TIA Portal V18
- Ethernet-based communication between laboratory components
- Docker-based application services
- Ansible for configuration management and infrastructure automation (planned)

### Engineering objectives

- Document the physical and logical network topology.
- Define IP addressing and communication paths.
- Configure and maintain Linux services.
- Evaluate resource allocation and ARM64 compatibility.
- Apply network access restrictions and security controls.
- Introduce repeatable infrastructure configuration using Ansible.

### Documentation

- [Network Architecture](docs/02-network.md)
- [Virtualization](docs/05-virtualization.md)
- [Container Infrastructure](docs/06-containers.md)

---

## 3. OT/IT Integration and Data Engineering

**Focus:** connecting industrial processes with software services and data platforms.

### Integration approaches

The project will evaluate different methods of acquiring data from the PLC:

- Direct Siemens S7 communication
- OPC UA, subject to PLC and firmware capabilities
- MQTT messaging using Mosquitto
- Node-RED for integration flows
- Python for custom data acquisition and processing

These methods are alternatives or complementary components, not necessarily mutually exclusive solutions.

### Target data flow

1. Acquire process variables from the PLC.
2. Validate and normalize incoming data.
3. Add timestamps and handle communication errors.
4. Publish telemetry through MQTT where appropriate.
5. Store measurements in CSV files and/or a database.
6. Expose selected data to monitoring and analytics services.

Previously prepared MQTT and CSV logging components will be revalidated before being considered operational in the current version.

### Documentation

- [System Architecture](docs/01-architecture.md)
- [Container Infrastructure](docs/06-containers.md)

---

## 4. DevOps — Automation and Delivery

**Focus:** reproducible builds, automated quality checks, testing, and controlled deployment.

### Planned capabilities

- Git-based version control
- Automated code validation and linting
- Python unit and integration tests
- Docker image builds
- ARM64 compatibility checks
- Dependency and container security scanning
- CI/CD pipelines
- Deployment and smoke testing
- Versioned configuration and documentation

### Engineering objectives

- Automate repetitive development and deployment tasks.
- Detect defects before deployment.
- Make changes traceable and reproducible.
- Separate development, testing, and deployment stages.
- Document failures, test results, and recovery procedures.

### Documentation

- [GitLab CI/CD](docs/07-gitlab-ci-cd.md)

---

## 5. GitLab — Source Control and CI/CD

**Focus:** managing source code and automating the software lifecycle.

The intended GitLab workflow will support:

- Repository and branch management
- Merge requests and code review
- GitLab CI/CD pipelines
- GitLab Runner configuration
- Automated testing
- Container image building
- Artifact and version management
- Controlled deployment to the laboratory environment

GitLab deployment and runner placement will be determined after evaluating the available Raspberry Pi 5 resources and the requirements of the selected components.

**Status:** planned; implementation and resource requirements to be validated.

### Documentation

- [GitLab CI/CD](docs/07-gitlab-ci-cd.md)
- [Virtualization](docs/05-virtualization.md)

---

## 6. AWS — Cloud Integration

**Focus:** secure integration between local industrial infrastructure and cloud services.

### Planned capabilities

- Secure telemetry transfer from the local environment
- AWS IoT Core for MQTT-based ingestion
- Amazon S3 for historical data and experiment archives
- Identity and access management
- TLS-protected communication
- Optional AWS IoT SiteWise for industrial data modeling
- Optional AWS Lambda for event-driven processing
- Cloud cost monitoring and resource limits

The cloud architecture will be selected according to actual requirements, service availability, security constraints, and operating costs.

Local process control is intended to remain independent of cloud connectivity.

**Status:** planned; service selection and implementation to be validated.

### Documentation

- [AWS Cloud Integration](docs/09-aws-cloud.md)
- [Monitoring and Security](docs/10-monitoring-and-security.md)

---

## 7. Data Engineering and Analytics

**Focus:** transforming industrial telemetry into useful information.

### Planned capabilities

- Data validation and preprocessing
- Timestamp normalization
- Historical data storage
- CSV and database integration
- Python-based data analysis
- Power BI dashboards and reports
- Process performance analysis
- Comparison of experiments and controller settings

Potential performance indicators include settling time, overshoot, control error, and response to process disturbances.

Power BI will be evaluated as an analytics and reporting tool, while Grafana will primarily support technical monitoring and operational dashboards.

**Status:** planned; initial work will use validated process data from the PID simulation.

---

## 8. Machine Learning

**Focus:** using process telemetry for experiments in predictive analytics and anomaly detection.

### Planned capabilities

- Feature engineering
- Dataset preparation
- Model training and evaluation
- Model versioning
- Anomaly detection
- Inference on selected process data

Future experiments may evaluate process efficiency and operating costs if the laboratory is extended with motor-drive integration and electrical energy measurements.

Machine learning is an additional analytics layer, not a replacement for the PLC's real-time control functions.

**Status:** planned; development will follow validation of the data acquisition pipeline.

### Documentation

- [Machine Learning and Data Processing](docs/08-machine-learning.md)

---

## 9. Observability and Security

**Focus:** understanding system behavior and protecting the laboratory infrastructure.

### Planned capabilities

- Prometheus metrics collection
- Grafana dashboards
- Centralized logging with Loki
- Alerting and service health checks
- Authentication and least-privilege access
- Network access restrictions
- Secure handling of credentials and secrets
- Backup and recovery procedures

Monitoring coverage will distinguish between infrastructure health, application health, and industrial process measurements.

**Status:** planned; components will be marked operational after implementation and testing.

### Documentation

- [Monitoring and Security](docs/10-monitoring-and-security.md)

---

## 10. Physical Infrastructure

| Component | Model / specification |
|---|---|
| Computing platform | Raspberry Pi 5 |
| Virtualization | VMware ESXi on Arm (Fling) |
| PLC | Siemens SIMATIC S7-1200 CPU 1212C DC/DC/DC |
| HMI | Siemens KTP600 Basic mono PN |
| Industrial Ethernet switch | Moxa EDS-205 |
| Power supply | Mean Well MDR-60-24, 24 V DC |
| Circuit protection | Schneider Electric K60N B6 |
| Isolating switch | Schneider Electric A9S65240 iSW |
| Engineering workstation | Windows 11 in VirtualBox |
| Engineering software | Siemens TIA Portal V18 |

Hardware details and electrical documentation will be verified against the actual devices and manufacturer documentation.

---

## 11. Development Roadmap

The project will be implemented incrementally.

1. **Documentation and baseline verification** — document the existing hardware, software, and network configuration.
2. **Industrial process** — validate temperature simulation, PID regulation, and HMI trends.
3. **Data acquisition** — restore and test PLC data acquisition, MQTT messaging, and CSV logging.
4. **Linux infrastructure** — document and configure virtual machines and container services.
5. **Python services** — implement data validation, processing, logging, and automated tests.
6. **DevOps automation** — introduce GitLab CI/CD, image builds, and controlled deployment.
7. **Observability and security** — add monitoring, alerting, and security controls.
8. **Cloud integration** — evaluate and implement a secure, cost-controlled AWS data path.
9. **Analytics and reporting** — build Power BI reports from validated process data.
10. **Machine learning** — develop and evaluate data analysis and anomaly detection.

Each stage should have documented acceptance criteria and test results before it is considered complete.

---

## 12. Repository Structure

```text
industry-devops-lab/
├── README.md
├── docs/
│   ├── 01-architecture.md
│   ├── 02-network.md
│   ├── 03-electrical-system.md
│   ├── 04-plc-and-hmi.md
│   ├── 05-virtualization.md
│   ├── 06-containers.md
│   ├── 07-gitlab-ci-cd.md
│   ├── 08-machine-learning.md
│   ├── 09-aws-cloud.md
│   └── 10-monitoring-and-security.md
├── diagrams/
└── assets/
```

The documentation is organized by technical domain so readers can navigate directly to the areas relevant to their interests.

---

## 13. Documentation and Security Principles

- Clearly distinguish implemented, tested, planned, and experimental components.
- Document significant architectural decisions and their rationale.
- Include test procedures and observed results where relevant.
- Keep diagrams and configuration examples synchronized with the actual system.
- Never commit passwords, API keys, access tokens, private keys, or other secrets.
- Sanitize sensitive network and infrastructure details before publishing.
- Verify electrical designs and manufacturer requirements before performing physical wiring changes.

---

## Project Status

**Status: In development**

The physical laboratory provides the foundation for the project. The initial engineering focus is temperature process simulation and PID control with Siemens PLC and HMI hardware.

The broader DevOps, integration, observability, data processing, analytics, and cloud capabilities will be implemented and validated in stages.

The objective is to demonstrate not only knowledge of individual technologies, but also the ability to integrate them into a documented, testable, maintainable engineering system.
