# AWS Infrastructure Improvement Plan
## Contract Engagement: Nights/Weekends (12-16 weeks)

### Phase 1: Foundation & Pulumi Setup (Weeks 1-2)
| Week | Task | Description | Deliverable | Hours | Dependencies |
|------|------|-------------|-------------|-------|--------------|
| 1 | 1.1 | Install Pulumi CLI locally | Pulumi CLI installed and configured | 2 | None |
| 1 | 1.2 | Set up AWS credentials and configuration | AWS access configured for Pulumi | 1 | AWS account access |
| 1 | 1.3 | Create S3 bucket for Pulumi state backend | S3 bucket for state management | 1 | AWS credentials |
| 1 | 1.4 | Set up DynamoDB table for state locking | DynamoDB table for concurrent access control | 1 | S3 bucket |
| 1 | 1.5 | Initialize Pulumi project structure | Project scaffold with Python setup | 2 | Pulumi CLI |
| 1 | 1.6 | Configure Pulumi backend to use S3 | State backend configured and tested | 1 | S3 bucket, DynamoDB |
| 2 | 1.7 | Create Pulumi stacks (dev, prod, shared) | Three separate stacks configured | 2 | Project structure |
| 2 | 1.8 | Set up version control (Git repository) | Git repo with proper branching strategy | 1 | None |
| 2 | 1.9 | Configure AWS provider in Pulumi | AWS provider configured for all stacks | 1 | AWS credentials |
| 2 | 1.10 | Test basic Pulumi connectivity and AWS access | Validation that Pulumi can access AWS | 1 | All above tasks |

### Phase 2: VPC Architecture (Weeks 3-4)
| Week | Task | Description | Deliverable | Hours | Dependencies |
|------|------|-------------|-------------|-------|--------------|
| 3 | 2.1 | Design VPC architecture for Dev environment | VPC design document with subnet layout | 3 | None |
| 3 | 2.2 | Create Dev VPC using Pulumi | Dev VPC with proper CIDR blocks | 2 | Pulumi setup |
| 3 | 2.3 | Create Dev subnets (public, private, database) | Subnets configured with route tables | 3 | Dev VPC |
| 3 | 2.4 | Configure NAT Gateways for Dev VPC | NAT Gateways for private subnet internet access | 2 | Dev subnets |
| 3 | 2.5 | Set up route tables for Dev VPC | Route tables configured for all subnets | 2 | NAT Gateways |
| 4 | 2.6 | Design VPC architecture for Prod environment | Prod VPC design document | 2 | Dev VPC experience |
| 4 | 2.7 | Create Prod VPC using Pulumi | Prod VPC with proper CIDR blocks | 2 | Pulumi setup |
| 4 | 2.8 | Create Prod subnets (public, private, database) | Prod subnets configured | 3 | Prod VPC |
| 4 | 2.9 | Configure NAT Gateways for Prod VPC | Prod NAT Gateways | 2 | Prod subnets |
| 4 | 2.10 | Set up route tables for Prod VPC | Prod route tables | 2 | Prod NAT Gateways |

### Phase 3: IAM Overhaul (Weeks 5-6)
| Week | Task | Description | Deliverable | Hours | Dependencies |
|------|------|-------------|-------------|-------|--------------|
| 5 | 3.1 | Audit existing IAM users, roles, and policies | IAM audit report | 4 | AWS access |
| 5 | 3.2 | Design new IAM structure with role-based access | IAM design document | 3 | IAM audit |
| 5 | 3.3 | Create IAM groups for different access levels | IAM groups configured | 2 | IAM design |
| 5 | 3.4 | Create IAM roles for EKS service accounts | EKS IAM roles | 2 | IAM groups |
| 5 | 3.5 | Create IAM roles for EC2 instances | EC2 IAM roles | 2 | IAM groups |
| 6 | 3.6 | Create IAM policies for least privilege access | IAM policies configured | 4 | IAM roles |
| 6 | 3.7 | Enable IAM Access Analyzer | Access Analyzer configured | 1 | IAM policies |
| 6 | 3.8 | Configure password policies and MFA requirements | Password and MFA policies | 2 | IAM setup |
| 6 | 3.9 | Remove root access keys and inline policies | Root keys removed, inline policies cleaned | 3 | IAM policies |
| 6 | 3.10 | Test IAM access for all user types | IAM access validation | 2 | All IAM changes |

### Phase 4: Application Containerization (Weeks 7-10)
| Week | Task | Description | Deliverable | Hours | Dependencies |
|------|------|-------------|-------------|-------|--------------|
| 7 | 4.1 | Inventory existing applications (Beanstalk, EC2) | Application inventory document | 3 | Access to current infra |
| 7 | 4.2 | Analyze application dependencies and requirements | Dependency analysis report | 4 | Application inventory |
| 7 | 4.3 | Create Dockerfiles for first application | Dockerfile for app #1 | 4 | Dependency analysis |
| 7 | 4.4 | Test containerized application locally | Local container testing | 3 | Dockerfile |
| 8 | 4.5 | Create Dockerfiles for second application | Dockerfile for app #2 | 4 | App #1 containerized |
| 8 | 4.6 | Test containerized application locally | Local container testing | 3 | Dockerfile |
| 8 | 4.7 | Create Dockerfiles for third application | Dockerfile for app #3 | 4 | App #2 containerized |
| 8 | 4.8 | Test containerized application locally | Local container testing | 3 | Dockerfile |
| 9 | 4.9 | Set up container registry (ECR) | ECR repositories configured | 2 | Containerized apps |
| 9 | 4.10 | Push container images to ECR | Images available in ECR | 2 | ECR setup |
| 9 | 4.11 | Create Helm charts for first application | Helm chart for app #1 | 4 | Container images |
| 9 | 4.12 | Test Helm deployment locally | Local Helm testing | 2 | Helm chart |
| 10 | 4.13 | Create Helm charts for second application | Helm chart for app #2 | 4 | App #1 Helm chart |
| 10 | 4.14 | Test Helm deployment locally | Local Helm testing | 2 | Helm chart |
| 10 | 4.15 | Create Helm charts for third application | Helm chart for app #3 | 4 | App #2 Helm chart |
| 10 | 4.16 | Test Helm deployment locally | Local Helm testing | 2 | Helm chart |

### Phase 5: EKS Cluster Setup (Weeks 11-12)
| Week | Task | Description | Deliverable | Hours | Dependencies |
|------|------|-------------|-------------|-------|--------------|
| 11 | 5.1 | Create Dev EKS cluster using Pulumi | Dev EKS cluster | 4 | VPC, IAM roles |
| 11 | 5.2 | Configure EKS node groups for Dev | Dev node groups | 3 | Dev EKS cluster |
| 11 | 5.3 | Enable IAM roles for service accounts (IRSA) | IRSA configured for Dev | 2 | Dev EKS cluster |
| 11 | 5.4 | Install Istio on Dev cluster | Istio installed on Dev | 3 | Dev EKS cluster |
| 11 | 5.5 | Configure Istio ingress gateway for Dev | Dev ingress gateway | 2 | Istio installation |
| 12 | 5.6 | Create Prod EKS cluster using Pulumi | Prod EKS cluster | 4 | VPC, IAM roles |
| 12 | 5.7 | Configure EKS node groups for Prod | Prod node groups | 3 | Prod EKS cluster |
| 12 | 5.8 | Enable IAM roles for service accounts (IRSA) | IRSA configured for Prod | 2 | Prod EKS cluster |
| 12 | 5.9 | Install Istio on Prod cluster | Istio installed on Prod | 3 | Prod EKS cluster |
| 12 | 5.10 | Configure Istio ingress gateway for Prod | Prod ingress gateway | 2 | Istio installation |

### Phase 6: Application Deployment (Weeks 13-14)
| Week | Task | Description | Deliverable | Hours | Dependencies |
|------|------|-------------|-------------|-------|--------------|
| 13 | 6.1 | Deploy first application to Dev EKS | App #1 running on Dev | 3 | Dev EKS, Helm charts |
| 13 | 6.2 | Configure Istio routing for first app | Istio routing for app #1 | 2 | App #1 deployed |
| 13 | 6.3 | Deploy second application to Dev EKS | App #2 running on Dev | 3 | Dev EKS, Helm charts |
| 13 | 6.4 | Configure Istio routing for second app | Istio routing for app #2 | 2 | App #2 deployed |
| 13 | 6.5 | Deploy third application to Dev EKS | App #3 running on Dev | 3 | Dev EKS, Helm charts |
| 13 | 6.6 | Configure Istio routing for third app | Istio routing for app #3 | 2 | App #3 deployed |
| 14 | 6.7 | Test application connectivity and functionality | Dev environment validation | 4 | All apps deployed |
| 14 | 6.8 | Deploy first application to Prod EKS | App #1 running on Prod | 3 | Prod EKS, Dev testing |
| 14 | 6.9 | Configure Istio routing for first app (Prod) | Prod Istio routing for app #1 | 2 | App #1 deployed to Prod |
| 14 | 6.10 | Deploy second application to Prod EKS | App #2 running on Prod | 3 | Prod EKS, Dev testing |
| 14 | 6.11 | Configure Istio routing for second app (Prod) | Prod Istio routing for app #2 | 2 | App #2 deployed to Prod |
| 14 | 6.12 | Deploy third application to Prod EKS | App #3 running on Prod | 3 | Prod EKS, Dev testing |
| 14 | 6.13 | Configure Istio routing for third app (Prod) | Prod Istio routing for app #3 | 2 | App #3 deployed to Prod |

### Phase 7: Observability - SigNoz (Weeks 15-16)
| Week | Task | Description | Deliverable | Hours | Dependencies |
|------|------|-------------|-------------|-------|--------------|
| 15 | 7.1 | Deploy SigNoz to Dev EKS cluster | SigNoz running on Dev | 4 | Dev EKS cluster |
| 15 | 7.2 | Configure OpenTelemetry collectors | OTEL collectors configured | 3 | SigNoz deployment |
| 15 | 7.3 | Instrument applications for SigNoz | Apps sending metrics/logs | 4 | OTEL collectors |
| 15 | 7.4 | Create SigNoz dashboards for applications | Application dashboards | 3 | Instrumented apps |
| 15 | 7.5 | Configure SigNoz alerts | Alerting configured | 2 | Dashboards |
| 16 | 7.6 | Deploy SigNoz to Prod EKS cluster | SigNoz running on Prod | 4 | Prod EKS cluster |
| 16 | 7.7 | Configure OpenTelemetry collectors (Prod) | Prod OTEL collectors | 3 | Prod SigNoz |
| 16 | 7.8 | Instrument applications for SigNoz (Prod) | Prod apps sending metrics/logs | 4 | Prod OTEL collectors |
| 16 | 7.9 | Create SigNoz dashboards for Prod | Prod application dashboards | 3 | Prod instrumented apps |
| 16 | 7.10 | Configure SigNoz alerts for Prod | Prod alerting configured | 2 | Prod dashboards |

### Phase 8: Security - Wazuh (Weeks 17-18)
| Week | Task | Description | Deliverable | Hours | Dependencies |
|------|------|-------------|-------------|-------|--------------|
| 17 | 8.1 | Deploy Wazuh manager | Wazuh manager deployed | 4 | EKS clusters |
| 17 | 8.2 | Install Wazuh agents on EKS nodes | Agents installed on nodes | 3 | Wazuh manager |
| 17 | 8.3 | Configure AWS CloudTrail integration | CloudTrail logs to Wazuh | 2 | Wazuh manager |
| 17 | 8.4 | Configure AWS GuardDuty integration | GuardDuty alerts to Wazuh | 2 | Wazuh manager |
| 17 | 8.5 | Configure AWS Config integration | Config findings to Wazuh | 2 | Wazuh manager |
| 18 | 8.6 | Create Wazuh security dashboards | Security dashboards | 4 | All integrations |
| 18 | 8.7 | Configure Wazuh alerting rules | Security alerting | 3 | Dashboards |
| 18 | 8.8 | Test security monitoring | Security monitoring validation | 3 | Alerting rules |
| 18 | 8.9 | Document security procedures | Security runbooks | 2 | Security monitoring |
| 18 | 8.10 | Train team on Wazuh usage | Team training completed | 2 | Documentation |

### Phase 9: Security Hardening (Weeks 19-20)
| Week | Task | Description | Deliverable | Hours | Dependencies |
|------|------|-------------|-------------|-------|--------------|
| 19 | 9.1 | Enable AWS Security Hub | Security Hub enabled | 2 | AWS access |
| 19 | 9.2 | Enable AWS Inspector | Inspector enabled | 2 | Security Hub |
| 19 | 9.3 | Enable AWS Macie | Macie enabled | 2 | Security Hub |
| 19 | 9.4 | Configure VPC Flow Logs | Flow logs enabled | 3 | VPCs |
| 19 | 9.5 | Review and update security groups | Security groups hardened | 4 | Flow logs |
| 19 | 9.6 | Review and update NACLs | NACLs hardened | 3 | Security groups |
| 20 | 9.7 | Enable AWS Config | Config enabled | 2 | AWS access |
| 20 | 9.8 | Configure Config rules | Config rules configured | 3 | Config enabled |
| 20 | 9.9 | Set up automated backups for RDS | RDS backups configured | 2 | RDS instances |
| 20 | 9.10 | Configure S3 bucket policies | S3 security hardened | 3 | S3 buckets |
| 20 | 9.11 | Enable encryption at rest and in transit | Encryption enabled | 3 | All resources |
| 20 | 9.12 | Test security configurations | Security testing | 4 | All security configs |

### Phase 10: VPN & Network Security (Weeks 21-22)
| Week | Task | Description | Deliverable | Hours | Dependencies |
|------|------|-------------|-------------|-------|--------------|
| 21 | 10.1 | Design VPN architecture | VPN design document | 3 | VPC architecture |
| 21 | 10.2 | Deploy AWS VPN Gateway | VPN Gateway deployed | 3 | VPCs |
| 21 | 10.3 | Configure VPN connections | VPN connections configured | 4 | VPN Gateway |
| 21 | 10.4 | Set up VPN client configuration | VPN client setup | 3 | VPN connections |
| 21 | 10.5 | Test VPN connectivity | VPN connectivity validated | 2 | VPN client |
| 22 | 10.6 | Configure route tables for VPN traffic | VPN routing configured | 3 | VPN connectivity |
| 22 | 10.7 | Update security groups for VPN access | Security groups updated | 3 | VPN routing |
| 22 | 10.8 | Test secure access to resources | Secure access validation | 4 | Security groups |
| 22 | 10.9 | Document VPN procedures | VPN runbooks | 2 | VPN testing |
| 22 | 10.10 | Train team on VPN usage | VPN training completed | 2 | Documentation |

### Phase 11: HashiCorp Vault Integration (Weeks 23-24)
| Week | Task | Description | Deliverable | Hours | Dependencies |
|------|------|-------------|-------------|-------|--------------|
| 23 | 11.1 | Deploy HashiCorp Vault to EKS | Vault deployed to EKS | 4 | EKS clusters |
| 23 | 11.2 | Configure Vault authentication | Vault auth configured | 3 | Vault deployment |
| 23 | 11.3 | Set up Vault secrets engines | Secrets engines configured | 3 | Vault auth |
| 23 | 11.4 | Configure database credentials management | DB creds management | 4 | Secrets engines |
| 23 | 11.5 | Integrate applications with Vault | Apps using Vault for secrets | 4 | DB creds management |
| 24 | 11.6 | Configure Vault policies | Vault policies configured | 3 | Vault integration |
| 24 | 11.7 | Set up Vault audit logging | Audit logging configured | 2 | Vault policies |
| 24 | 11.8 | Test Vault functionality | Vault testing completed | 3 | Audit logging |
| 24 | 11.9 | Document Vault procedures | Vault runbooks | 2 | Vault testing |
| 24 | 11.10 | Train team on Vault usage | Vault training completed | 2 | Documentation |

### Phase 12: Cleanup & Finalization (Weeks 25-26)
| Week | Task | Description | Deliverable | Hours | Dependencies |
|------|------|-------------|-------------|-------|--------------|
| 25 | 12.1 | Remove unused resources in us-east-1 | N.Virginia cleanup | 3 | All migrations complete |
| 25 | 12.2 | Clean up legacy security groups | Security groups cleanup | 2 | Security review |
| 25 | 12.3 | Remove unused IAM roles and users | IAM cleanup | 3 | IAM audit |
| 25 | 12.4 | Validate WAF rules are functional | WAF validation | 2 | Security review |
| 25 | 12.5 | Remove Elastic Beanstalk environments | Beanstalk cleanup | 3 | App migrations |
| 26 | 12.6 | Create CI/CD pipelines for Pulumi | CI/CD for infrastructure | 4 | All infrastructure |
| 26 | 12.7 | Create final architecture documentation | Architecture docs | 4 | All components |
| 26 | 12.8 | Create operational runbooks | Operational documentation | 4 | All systems |
| 26 | 12.9 | Conduct knowledge transfer sessions | Knowledge transfer | 3 | Documentation |
| 26 | 12.10 | Final validation and handoff | Project completion | 4 | All deliverables |

## Summary
- **Total Duration**: 26 weeks (6+ months)
- **Total Hours**: ~400-450 hours
- **Weekly Commitment**: ~15-17 hours (nights/weekends)
- **Key Deliverables**: Modernized AWS infrastructure with containerization, security, and observability

## Risk Mitigation
- Each phase includes testing and validation steps
- Rollback procedures documented for each major change
- Staged deployment (Dev → Prod) reduces risk
- Comprehensive documentation ensures knowledge retention 