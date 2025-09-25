# AWS Dev Account Refined Plan - September 2025

## Overview

This refined plan focuses on creating a new AWS Dev account to decrease risk for production Cognito issues, while building out infrastructure using Pulumi TypeScript and importing existing resources for comprehensive testing.

## 🎯 Project Goals

- **Risk Reduction**: Create Dev account first to test Cognito migration safely
- **Infrastructure as Code**: Use Pulumi TypeScript for all infrastructure
- **Resource Import**: Import existing resources into Pulumi management
- **Data Migration**: Plan for migrating data from existing resources
- **VPN/Teleport Access**: Secure access to new Dev environment

## 📋 Project Scope

### Phase 1: New Dev Account Setup (Weeks 1-2)
- Create new AWS Dev account
- Configure IAM roles and policies
- Set up Pulumi TypeScript project
- Configure VPN/Teleport access

### Phase 2: Infrastructure Buildout (Weeks 3-4)
- Create VPC with security best practices
- Deploy VPN/Teleport infrastructure
- Set up monitoring and logging
- Configure security controls

### Phase 3: Resource Import (Weeks 5-6)
- Import RDS instances
- Import ElasticBeanstalk applications
- Import Lambda functions
- Import Route53 records
- Import Cognito user pools

### Phase 4: Data Migration Planning (Weeks 7-8)
- Plan RDS data migration
- Plan ElasticBeanstalk application migration
- Plan Lambda function migration
- Plan Route53 DNS migration
- Plan Cognito user migration

## 🏗️ Architecture

### Key Components

#### Network Architecture
- **New Dev VPC**: 10.0.0.0/16 with isolated subnets
- **Public Subnet**: 10.0.1.0/24 (Load Balancers, NAT Gateways)
- **Private Subnet**: 10.0.2.0/24 (Applications, Databases)
- **Database Subnet**: 10.0.3.0/24 (RDS, Databases)
- **Security Subnet**: 10.0.4.0/24 (VPN, Security Tools)

#### Access Control
- **VPN Gateway**: AWS VPN for secure access
- **Teleport**: Alternative secure access solution
- **IAM Roles**: Least privilege access control
- **Security Groups**: Network-level security

#### Infrastructure as Code
- **Pulumi TypeScript**: All infrastructure management
- **Resource Import**: Existing resources into Pulumi
- **State Management**: S3 backend with DynamoDB locking
- **Version Control**: Git-based infrastructure changes

## 📚 Implementation Timeline

### Phase 1: New Dev Account Setup (Weeks 1-2)

| Week | Task | Description | Deliverable | Hours | Dependencies |
|------|------|-------------|-------------|-------|--------------|
| 1 | 1.1 | Create new AWS Dev account | New AWS Dev account | 2 | None |
| 1 | 1.2 | Configure IAM roles and policies | IAM roles and policies | 4 | New account |
| 1 | 1.3 | Set up billing and cost management | Billing configuration | 1 | New account |
| 1 | 1.4 | Configure CloudTrail and security services | Security services enabled | 2 | IAM setup |
| 2 | 1.5 | Initialize Pulumi TypeScript project | Pulumi project structure | 3 | Security services |
| 2 | 1.6 | Configure Pulumi backend (S3 + DynamoDB) | Pulumi backend configured | 2 | Pulumi project |
| 2 | 1.7 | Set up VPN Gateway | VPN Gateway deployed | 3 | Pulumi backend |
| 2 | 1.8 | Configure Teleport (alternative) | Teleport configured | 4 | VPN Gateway |
| 2 | 1.9 | Test access to new Dev account | Access validation | 2 | All setup |
| 2 | 1.10 | Document Dev account procedures | Dev account runbooks | 2 | Access validation |

### Phase 2: Infrastructure Buildout (Weeks 3-4)

| Week | Task | Description | Deliverable | Hours | Dependencies |
|------|------|-------------|-------------|-------|--------------|
| 3 | 2.1 | Create VPC with Pulumi TypeScript | VPC infrastructure | 4 | Pulumi setup |
| 3 | 2.2 | Create subnets and route tables | Subnet infrastructure | 3 | VPC created |
| 3 | 2.3 | Configure NAT Gateways | NAT Gateways | 2 | Subnets created |
| 3 | 2.4 | Set up security groups | Security groups | 3 | NAT Gateways |
| 3 | 2.5 | Configure Network ACLs | NACLs configured | 2 | Security groups |
| 4 | 2.6 | Deploy VPN/Teleport infrastructure | Access infrastructure | 4 | NACLs |
| 4 | 2.7 | Set up monitoring and logging | Monitoring infrastructure | 3 | Access infrastructure |
| 4 | 2.8 | Configure backup and disaster recovery | Backup infrastructure | 2 | Monitoring |
| 4 | 2.9 | Test infrastructure connectivity | Infrastructure validation | 3 | All infrastructure |
| 4 | 2.10 | Document infrastructure procedures | Infrastructure runbooks | 2 | Validation complete |

### Phase 3: Resource Import (Weeks 5-6)

| Week | Task | Description | Deliverable | Hours | Dependencies |
|------|------|-------------|-------------|-------|--------------|
| 5 | 3.1 | Import RDS instances | RDS imported to Pulumi | 4 | Infrastructure complete |
| 5 | 3.2 | Import ElasticBeanstalk applications | EB imported to Pulumi | 4 | RDS imported |
| 5 | 3.3 | Import Lambda functions | Lambda imported to Pulumi | 3 | EB imported |
| 5 | 3.4 | Import Route53 records | Route53 imported to Pulumi | 2 | Lambda imported |
| 5 | 3.5 | Import Cognito user pools | Cognito imported to Pulumi | 3 | Route53 imported |
| 6 | 3.6 | Validate all imported resources | All resources validated | 4 | All imports |
| 6 | 3.7 | Test resource functionality | Resource testing | 3 | Validation complete |
| 6 | 3.8 | Update Pulumi configurations | Configurations updated | 2 | Testing complete |
| 6 | 3.9 | Document import procedures | Import runbooks | 2 | Configurations updated |
| 6 | 3.10 | Train team on Pulumi management | Team training | 2 | Documentation complete |

### Phase 4: Data Migration Planning (Weeks 7-8)

| Week | Task | Description | Deliverable | Hours | Dependencies |
|------|------|-------------|-------------|-------|--------------|
| 7 | 4.1 | Plan RDS data migration | RDS migration plan | 4 | All resources imported |
| 7 | 4.2 | Plan ElasticBeanstalk application migration | EB migration plan | 4 | RDS plan |
| 7 | 4.3 | Plan Lambda function migration | Lambda migration plan | 3 | EB plan |
| 7 | 4.4 | Plan Route53 DNS migration | Route53 migration plan | 2 | Lambda plan |
| 7 | 4.5 | Plan Cognito user migration | Cognito migration plan | 4 | Route53 plan |
| 8 | 4.6 | Create data migration scripts | Migration scripts | 4 | All plans |
| 8 | 4.7 | Test migration procedures | Migration testing | 4 | Scripts created |
| 8 | 4.8 | Document migration procedures | Migration runbooks | 3 | Testing complete |
| 8 | 4.9 | Create rollback procedures | Rollback procedures | 3 | Documentation |
| 8 | 4.10 | Final validation and handoff | Project completion | 3 | All procedures |

## 🛠️ Technology Stack

### Infrastructure as Code
- **Pulumi**: Infrastructure as Code (TypeScript)
- **S3 Backend**: State management
- **DynamoDB**: State locking
- **Git**: Version control

### Network Infrastructure
- **VPC**: Virtual Private Cloud
- **VPN Gateway**: Secure access
- **Teleport**: Alternative secure access
- **NAT Gateways**: Internet access for private subnets

### Security & Compliance
- **IAM**: Identity and Access Management
- **Security Groups**: Network security
- **NACLs**: Network Access Control Lists
- **CloudTrail**: API activity logging

### Monitoring & Observability
- **CloudWatch**: Monitoring and alerting
- **VPC Flow Logs**: Network monitoring
- **AWS Config**: Compliance monitoring

## 📊 Resource Import Strategy

### RDS Import
```typescript
// Example Pulumi TypeScript for RDS import
import * as aws from "@pulumi/aws";

const existingRDS = aws.rds.getInstance({
    dbInstanceIdentifier: "existing-db-instance"
});

const importedRDS = new aws.rds.Instance("imported-rds", {
    // Import existing RDS configuration
    identifier: existingRDS.identifier,
    engine: existingRDS.engine,
    instanceClass: existingRDS.instanceClass,
    // ... other configurations
});
```

### ElasticBeanstalk Import
```typescript
// Example Pulumi TypeScript for EB import
const existingEB = aws.elasticbeanstalk.getApplication({
    name: "existing-application"
});

const importedEB = new aws.elasticbeanstalk.Application("imported-eb", {
    name: existingEB.name,
    description: existingEB.description,
    // ... other configurations
});
```

### Lambda Import
```typescript
// Example Pulumi TypeScript for Lambda import
const existingLambda = aws.lambda.getFunction({
    functionName: "existing-function"
});

const importedLambda = new aws.lambda.Function("imported-lambda", {
    name: existingLambda.name,
    runtime: existingLambda.runtime,
    handler: existingLambda.handler,
    // ... other configurations
});
```

### Route53 Import
```typescript
// Example Pulumi TypeScript for Route53 import
const existingZone = aws.route53.getZone({
    name: "example.com"
});

const importedZone = new aws.route53.Zone("imported-zone", {
    name: existingZone.name,
    // ... other configurations
});
```

### Cognito Import
```typescript
// Example Pulumi TypeScript for Cognito import
const existingUserPool = aws.cognito.getUserPool({
    name: "existing-user-pool"
});

const importedUserPool = new aws.cognito.UserPool("imported-user-pool", {
    name: existingUserPool.name,
    // ... other configurations
});
```

## 🔄 Data Migration Plan

### RDS Data Migration
1. **Snapshot Creation**: Create snapshots of existing RDS instances
2. **Cross-Account Sharing**: Share snapshots with new Dev account
3. **Restore Process**: Restore snapshots in new Dev account
4. **Data Validation**: Validate data integrity and consistency
5. **Connection Testing**: Test application connections to new RDS

### ElasticBeanstalk Application Migration
1. **Application Export**: Export EB application configurations
2. **Environment Recreation**: Recreate EB environments in new account
3. **Code Deployment**: Deploy application code to new environments
4. **Configuration Sync**: Sync all environment configurations
5. **Testing**: Test application functionality in new environment

### Lambda Function Migration
1. **Function Export**: Export Lambda function code and configurations
2. **Dependency Management**: Identify and migrate dependencies
3. **Function Recreation**: Recreate Lambda functions in new account
4. **Trigger Configuration**: Configure all triggers and event sources
5. **Testing**: Test Lambda function execution and integrations

### Route53 DNS Migration
1. **Zone Export**: Export Route53 hosted zones
2. **Record Recreation**: Recreate DNS records in new account
3. **Domain Validation**: Validate domain ownership and configurations
4. **DNS Testing**: Test DNS resolution and record functionality
5. **Cutover Planning**: Plan DNS cutover procedures

### Cognito User Migration
1. **User Pool Export**: Export Cognito user pool configurations
2. **User Data Export**: Export user data (if applicable)
3. **User Pool Recreation**: Recreate user pools in new account
4. **User Data Import**: Import user data to new user pools
5. **Authentication Testing**: Test authentication flows and user management

## 🔒 Security Considerations

### Network Security
- **VPC Isolation**: Separate Dev environment from production
- **Subnet Segmentation**: Proper network boundaries
- **Security Groups**: Least privilege access
- **NACLs**: Additional network security

### Access Control
- **IAM Roles**: Role-based access control
- **VPN/Teleport**: Secure access methods
- **MFA Requirements**: Multi-factor authentication
- **Regular Audits**: Ongoing access reviews

### Data Security
- **Encryption**: Data encryption at rest and in transit
- **Backup Security**: Secure backup procedures
- **Access Logging**: Comprehensive audit trails
- **Compliance**: Regulatory compliance maintenance

## 📈 Success Metrics

### Technical Metrics
- **Resource Import**: 100% successful resource import
- **Data Integrity**: 100% data preservation
- **Functionality**: All services working correctly
- **Performance**: Maintained or improved performance

### Business Metrics
- **Risk Reduction**: Reduced production risk
- **Cost Optimization**: Improved cost structure
- **Operational Efficiency**: Enhanced operations
- **Knowledge Transfer**: Complete documentation and training

## 🚨 Risk Mitigation

### Technical Risks
- **Data Loss**: Comprehensive backup and testing
- **Service Disruption**: Staged migration approach
- **Integration Issues**: Thorough testing of all integrations
- **Performance Impact**: Load testing and monitoring

### Business Risks
- **Production Impact**: Dev account isolation
- **Timeline Delays**: Buffer time in schedule
- **Resource Constraints**: Adequate resource allocation
- **Knowledge Gaps**: Comprehensive training and documentation

## 📄 Deliverables

### Phase 1 Deliverables
- New AWS Dev account
- IAM roles and policies
- Pulumi TypeScript project
- VPN/Teleport access

### Phase 2 Deliverables
- VPC infrastructure
- Security configurations
- Monitoring setup
- Infrastructure documentation

### Phase 3 Deliverables
- All resources imported to Pulumi
- Resource validation
- Import documentation
- Team training

### Phase 4 Deliverables
- Data migration plans
- Migration scripts
- Rollback procedures
- Final documentation

## 🎯 Next Steps

1. **Stakeholder Approval**: Get approval for Dev account approach
2. **Resource Allocation**: Allocate necessary resources
3. **Timeline Confirmation**: Confirm 8-week timeline
4. **Team Preparation**: Prepare migration team
5. **Communication**: Begin stakeholder communication

---

**Last Updated**: September 25, 2025
**Version**: 1.0
**Status**: Planning Phase
