# AWS Infrastructure Subset Plan - IAM Review & New Production Environment

## Overview

This is a focused subset of the full AWS Infrastructure Modernization plan, designed to:
1. **Review and clean up existing IAM**
2. **Create a new production VPC with security best practices**
3. **Deploy Wazuh for security data aggregation**
4. **Setup SigNoz for logs and APM data**

## 🎯 Project Goals

- **IAM Security**: Comprehensive review and cleanup of existing IAM structure
- **Network Isolation**: New production VPC with proper security segmentation
- **Security Monitoring**: Centralized security data aggregation with Wazuh
- **Observability**: Application performance monitoring and logging with SigNoz
- **Best Practices**: Implement AWS security best practices from the start

## 📋 Project Scope

### Phase 1: IAM Review & Cleanup (Weeks 1-2)
- Comprehensive IAM audit and analysis
- Remove unused roles, users, and policies
- Implement least privilege access
- Create new IAM structure for production environment

### Phase 2: New Production VPC (Weeks 3-4)
- Design and create new production VPC
- Implement security best practices
- Configure proper subnet isolation
- Setup network security controls

### Phase 3: Security Monitoring - Wazuh (Weeks 5-6)
- Deploy Wazuh for security data aggregation
- Configure AWS service integrations
- Setup security dashboards and alerting

### Phase 4: Observability - SigNoz (Weeks 7-8)
- Deploy SigNoz for logs and APM
- Configure application monitoring
- Setup dashboards and alerting

## 🏗️ Architecture

### Key Components

#### Network Architecture
- **New Prod VPC**: 10.1.0.0/16 with isolated subnets
- **Public Subnet**: 10.1.1.0/24 (Load Balancers, NAT Gateways)
- **Private Subnet**: 10.1.2.0/24 (Applications, Monitoring)
- **Database Subnet**: 10.1.3.0/24 (RDS, Databases)
- **Security Subnet**: 10.1.4.0/24 (Wazuh, Security Tools)

#### Security & Compliance
- **Wazuh**: Security information and event management
- **AWS Security Hub**: Centralized security findings
- **GuardDuty**: Threat detection
- **AWS Config**: Compliance monitoring
- **VPC Flow Logs**: Network traffic monitoring

#### Observability
- **SigNoz**: Application monitoring and alerting
- **OpenTelemetry**: Distributed tracing and metrics
- **CloudTrail**: API activity logging

## 📚 Implementation Timeline

### Phase 1: IAM Review & Cleanup (Weeks 1-2)

| Week | Task | Description | Deliverable | Hours | Dependencies |
|------|------|-------------|-------------|-------|--------------|
| 1 | 1.1 | Audit existing IAM users, roles, and policies | IAM audit report | 4 | AWS access |
| 1 | 1.2 | Identify unused and overprivileged access | Access analysis report | 3 | IAM audit |
| 1 | 1.3 | Document current IAM structure | IAM documentation | 2 | Access analysis |
| 1 | 1.4 | Design new IAM structure for production | IAM design document | 3 | IAM documentation |
| 2 | 1.5 | Remove unused IAM users and roles | Cleanup completed | 3 | IAM design |
| 2 | 1.6 | Remove inline policies and unused policies | Policy cleanup | 2 | User/role cleanup |
| 2 | 1.7 | Create new IAM roles for production VPC | Production IAM roles | 3 | Policy cleanup |
| 2 | 1.8 | Implement least privilege policies | Least privilege policies | 4 | Production roles |
| 2 | 1.9 | Test new IAM access | IAM validation | 2 | All IAM changes |
| 2 | 1.10 | Document IAM procedures | IAM runbooks | 2 | IAM validation |

### Phase 2: New Production VPC (Weeks 3-4)

| Week | Task | Description | Deliverable | Hours | Dependencies |
|------|------|-------------|-------------|-------|--------------|
| 3 | 2.1 | Design new production VPC architecture | VPC design document | 3 | IAM cleanup |
| 3 | 2.2 | Create new production VPC | Production VPC | 2 | VPC design |
| 3 | 2.3 | Create production subnets | Production subnets | 3 | Production VPC |
| 3 | 2.4 | Configure NAT Gateways | NAT Gateways configured | 2 | Production subnets |
| 3 | 2.5 | Setup route tables | Route tables configured | 2 | NAT Gateways |
| 4 | 2.6 | Configure security groups | Security groups configured | 3 | Route tables |
| 4 | 2.7 | Setup Network ACLs | NACLs configured | 2 | Security groups |
| 4 | 2.8 | Enable VPC Flow Logs | Flow logs enabled | 2 | NACLs |
| 4 | 2.9 | Configure AWS Config | Config enabled | 2 | Flow logs |
| 4 | 2.10 | Test VPC connectivity | VPC validation | 2 | All VPC configs |

### Phase 3: Security Monitoring - Wazuh (Weeks 5-6)

| Week | Task | Description | Deliverable | Hours | Dependencies |
|------|------|-------------|-------------|-------|--------------|
| 5 | 3.1 | Deploy Wazuh manager | Wazuh manager deployed | 4 | Production VPC |
| 5 | 3.2 | Configure AWS CloudTrail integration | CloudTrail to Wazuh | 2 | Wazuh manager |
| 5 | 3.3 | Configure AWS GuardDuty integration | GuardDuty to Wazuh | 2 | Wazuh manager |
| 5 | 3.4 | Configure AWS Config integration | Config to Wazuh | 2 | Wazuh manager |
| 5 | 3.5 | Configure VPC Flow Logs to Wazuh | Flow logs to Wazuh | 2 | Wazuh manager |
| 6 | 3.6 | Create Wazuh security dashboards | Security dashboards | 4 | All integrations |
| 6 | 3.7 | Configure Wazuh alerting rules | Security alerting | 3 | Dashboards |
| 6 | 3.8 | Test security monitoring | Security monitoring validation | 3 | Alerting rules |
| 6 | 3.9 | Document security procedures | Security runbooks | 2 | Security monitoring |
| 6 | 3.10 | Train team on Wazuh usage | Team training completed | 2 | Documentation |

### Phase 4: Observability - SigNoz (Weeks 7-8)

| Week | Task | Description | Deliverable | Hours | Dependencies |
|------|------|-------------|-------------|-------|--------------|
| 7 | 4.1 | Deploy SigNoz to production VPC | SigNoz deployed | 4 | Production VPC |
| 7 | 4.2 | Configure OpenTelemetry collectors | OTEL collectors configured | 3 | SigNoz deployment |
| 7 | 4.3 | Setup log aggregation | Log aggregation configured | 3 | OTEL collectors |
| 7 | 4.4 | Configure application monitoring | APM configured | 4 | Log aggregation |
| 7 | 4.5 | Create SigNoz dashboards | Application dashboards | 3 | APM configured |
| 8 | 4.6 | Configure SigNoz alerts | Alerting configured | 2 | Dashboards |
| 8 | 4.7 | Test observability stack | Observability validation | 3 | Alerting |
| 8 | 4.8 | Document observability procedures | Observability runbooks | 2 | Validation |
| 8 | 4.9 | Train team on SigNoz usage | Team training completed | 2 | Documentation |
| 8 | 4.10 | Final validation and handoff | Project completion | 3 | All deliverables |

## 🛠️ Technology Stack

### Infrastructure
- **AWS VPC**: New production network
- **AWS IAM**: Reviewed and cleaned up access controls
- **AWS Config**: Compliance monitoring
- **VPC Flow Logs**: Network monitoring

### Security
- **Wazuh**: Security monitoring and aggregation
- **AWS Security Hub**: Centralized security findings
- **GuardDuty**: Threat detection
- **CloudTrail**: API activity logging

### Observability
- **SigNoz**: Application monitoring and logging
- **OpenTelemetry**: Distributed tracing and metrics

## 📊 Cost Optimization

- **Single VPC**: Focus on production environment only
- **Right-sized resources**: Appropriate sizing for monitoring tools
- **Reserved instances**: For predictable workloads
- **S3 lifecycle**: Automated data tiering for logs

## 🔒 Security Features

### Network Security
- **VPC Isolation**: Separate production environment
- **NACLs & Security Groups**: Network-level security
- **VPC Flow Logs**: Complete network visibility

### Access Control
- **Least Privilege IAM**: Minimal required permissions
- **Role-based Access**: No long-term credentials
- **Regular Audits**: Ongoing access reviews

### Monitoring & Compliance
- **Security Monitoring**: Wazuh SIEM
- **Compliance**: AWS Config and Security Hub
- **Audit Logging**: Comprehensive activity tracking

## 🚨 Success Metrics

### Technical Metrics
- **IAM Cleanup**: 100% of unused access removed
- **Security Posture**: Improved security scores
- **Observability**: 100% application and infrastructure monitoring
- **Compliance**: Meeting all security requirements

### Business Metrics
- **Cost Optimization**: Reduced infrastructure costs
- **Operational Efficiency**: Improved monitoring and security
- **Security Compliance**: Meeting all security requirements
- **Knowledge Transfer**: Complete documentation and training

## 📈 Risk Mitigation

- **Staged Approach**: IAM review before infrastructure changes
- **Testing**: Validation at each phase
- **Documentation**: Complete procedures and runbooks
- **Rollback Plans**: Defined rollback procedures

## 📞 Deliverables

### Phase 1 Deliverables
- IAM audit report
- IAM cleanup documentation
- New IAM structure design
- IAM runbooks

### Phase 2 Deliverables
- Production VPC architecture
- Network security configuration
- VPC validation results
- Network runbooks

### Phase 3 Deliverables
- Wazuh deployment
- Security dashboards
- Security alerting configuration
- Security runbooks

### Phase 4 Deliverables
- SigNoz deployment
- Application monitoring dashboards
- Observability alerting
- Observability runbooks

## 📄 Summary

- **Total Duration**: 8 weeks (2 months)
- **Total Hours**: ~120-140 hours
- **Weekly Commitment**: ~15-17 hours (nights/weekends)
- **Key Deliverables**: Clean IAM, secure production VPC, security monitoring, and observability

---

**Last Updated**: [Current Date]
**Version**: 1.0
**Status**: Planning Phase
