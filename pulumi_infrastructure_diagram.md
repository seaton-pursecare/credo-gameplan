# Pulumi Infrastructure Architecture Diagram

## Dev Account Infrastructure with Pulumi TypeScript

```mermaid
graph TB
    %% External Components
    Internet[🌐 Internet]
    VPN[🔒 AWS VPN Gateway]
    Teleport[🔒 Teleport Access]
    
    %% AWS Dev Account
    subgraph "AWS Dev Account (New)"
        subgraph "Dev VPC (10.0.0.0/16)"
            subgraph "Dev Public Subnet (10.0.1.0/24)"
                DevIGW[Internet Gateway]
                DevNAT[NAT Gateway]
                DevALB[Application Load Balancer]
            end
            
            subgraph "Dev Private Subnet (10.0.2.0/24)"
                DevApps[ElasticBeanstalk Applications]
                DevLambda[Lambda Functions]
                DevOTEL[OpenTelemetry Collectors]
            end
            
            subgraph "Dev Database Subnet (10.0.3.0/24)"
                DevRDS[RDS Databases]
            end
            
            subgraph "Dev Security Subnet (10.0.4.0/24)"
                DevVPN[VPN Endpoint]
                DevTeleport[Teleport Server]
                DevMonitoring[Monitoring Tools]
            end
        end
        
        %% Pulumi Infrastructure
        subgraph "Pulumi Infrastructure as Code"
            PulumiState[Pulumi State - S3]
            PulumiLock[DynamoDB Locking]
            PulumiCode[TypeScript Code]
            PulumiStacks[Pulumi Stacks]
        end
        
        %% AWS Services
        subgraph "AWS Global Services"
            IAM[IAM Roles & Policies]
            S3[S3 Buckets]
            CloudTrail[CloudTrail]
            GuardDuty[GuardDuty]
            Config[AWS Config]
            Route53[Route53 DNS]
            Cognito[Cognito User Pools]
        end
    end
    
    %% External Access
    Internet --> VPN
    Internet --> Teleport
    
    %% Network Connections
    VPN --> DevIGW
    Teleport --> DevIGW
    DevIGW --> DevALB
    
    %% Application Flow
    DevALB --> DevApps
    DevApps --> DevLambda
    DevApps --> DevRDS
    
    %% Monitoring Flow
    DevApps --> DevOTEL
    DevOTEL --> DevMonitoring
    
    %% Pulumi Management
    PulumiCode --> PulumiState
    PulumiState --> PulumiLock
    PulumiStacks --> DevVPC
    PulumiStacks --> DevRDS
    PulumiStacks --> DevApps
    PulumiStacks --> DevLambda
    PulumiStacks --> Route53
    PulumiStacks --> Cognito
    
    %% AWS Service Connections
    DevApps --> IAM
    DevApps --> S3
    DevApps --> Route53
    DevApps --> Cognito
    
    %% Security Connections
    DevMonitoring --> CloudTrail
    DevMonitoring --> GuardDuty
    DevMonitoring --> Config
    
    %% Styling
    classDef vpc fill:#e1f5fe
    classDef pulumi fill:#e8eaf6
    classDef security fill:#ffebee
    classDef monitoring fill:#e8f5e8
    classDef aws fill:#fff3e0
    classDef external fill:#fce4ec
    
    class DevVPC vpc
    class PulumiState,PulumiLock,PulumiCode,PulumiStacks pulumi
    class DevVPN,DevTeleport,DevMonitoring security
    class DevOTEL monitoring
    class IAM,S3,CloudTrail,GuardDuty,Config,Route53,Cognito aws
    class Internet,VPN,Teleport external
```

## Pulumi TypeScript Project Structure

```mermaid
graph TB
    subgraph "Pulumi Project Structure"
        subgraph "Source Code"
            MainTS[main.ts]
            VPC[VPC Configuration]
            RDS[RDS Configuration]
            EB[ElasticBeanstalk Configuration]
            Lambda[Lambda Configuration]
            Route53[Route53 Configuration]
            Cognito[Cognito Configuration]
        end
        
        subgraph "State Management"
            S3Backend[S3 Backend]
            DynamoDBLock[DynamoDB Locking]
            StateFiles[State Files]
        end
        
        subgraph "Stacks"
            DevStack[Dev Stack]
            ProdStack[Prod Stack]
            SharedStack[Shared Stack]
        end
        
        subgraph "Resources"
            ImportedRDS[Imported RDS]
            ImportedEB[Imported EB]
            ImportedLambda[Imported Lambda]
            ImportedRoute53[Imported Route53]
            ImportedCognito[Imported Cognito]
        end
    end
    
    %% Code Dependencies
    MainTS --> VPC
    MainTS --> RDS
    MainTS --> EB
    MainTS --> Lambda
    MainTS --> Route53
    MainTS --> Cognito
    
    %% State Management
    VPC --> S3Backend
    RDS --> S3Backend
    EB --> S3Backend
    Lambda --> S3Backend
    Route53 --> S3Backend
    Cognito --> S3Backend
    
    S3Backend --> DynamoDBLock
    S3Backend --> StateFiles
    
    %% Stack Management
    S3Backend --> DevStack
    S3Backend --> ProdStack
    S3Backend --> SharedStack
    
    %% Resource Import
    DevStack --> ImportedRDS
    DevStack --> ImportedEB
    DevStack --> ImportedLambda
    DevStack --> ImportedRoute53
    DevStack --> ImportedCognito
    
    %% Styling
    classDef code fill:#e3f2fd
    classDef state fill:#e8f5e8
    classDef stack fill:#fff3e0
    classDef resource fill:#ffebee
    
    class MainTS,VPC,RDS,EB,Lambda,Route53,Cognito code
    class S3Backend,DynamoDBLock,StateFiles state
    class DevStack,ProdStack,SharedStack stack
    class ImportedRDS,ImportedEB,ImportedLambda,ImportedRoute53,ImportedCognito resource
```

## Resource Import Strategy

```mermaid
graph TB
    subgraph "Source Account Resources"
        SourceRDS[Source RDS Instances]
        SourceEB[Source EB Applications]
        SourceLambda[Source Lambda Functions]
        SourceRoute53[Source Route53 Records]
        SourceCognito[Source Cognito Pools]
    end
    
    subgraph "Import Process"
        Analyze[Analyze Resources]
        Export[Export Configurations]
        Import[Import to Pulumi]
        Validate[Validate Import]
    end
    
    subgraph "Pulumi Management"
        PulumiRDS[Pulumi RDS]
        PulumiEB[Pulumi EB]
        PulumiLambda[Pulumi Lambda]
        PulumiRoute53[Pulumi Route53]
        PulumiCognito[Pulumi Cognito]
    end
    
    subgraph "Dev Account Resources"
        DevRDS[Dev RDS Instances]
        DevEB[Dev EB Applications]
        DevLambda[Dev Lambda Functions]
        DevRoute53[Dev Route53 Records]
        DevCognito[Dev Cognito Pools]
    end
    
    %% Import Flow
    SourceRDS --> Analyze
    SourceEB --> Analyze
    SourceLambda --> Analyze
    SourceRoute53 --> Analyze
    SourceCognito --> Analyze
    
    Analyze --> Export
    Export --> Import
    Import --> Validate
    
    %% Pulumi Management
    Validate --> PulumiRDS
    Validate --> PulumiEB
    Validate --> PulumiLambda
    Validate --> PulumiRoute53
    Validate --> PulumiCognito
    
    %% Dev Account Deployment
    PulumiRDS --> DevRDS
    PulumiEB --> DevEB
    PulumiLambda --> DevLambda
    PulumiRoute53 --> DevRoute53
    PulumiCognito --> DevCognito
    
    %% Styling
    classDef source fill:#ffebee
    classDef process fill:#e3f2fd
    classDef pulumi fill:#e8eaf6
    classDef dev fill:#e8f5e8
    
    class SourceRDS,SourceEB,SourceLambda,SourceRoute53,SourceCognito source
    class Analyze,Export,Import,Validate process
    class PulumiRDS,PulumiEB,PulumiLambda,PulumiRoute53,PulumiCognito pulumi
    class DevRDS,DevEB,DevLambda,DevRoute53,DevCognito dev
```

## VPN/Teleport Access Architecture

```mermaid
graph TB
    subgraph "External Access"
        Internet[Internet]
        VPNClient[VPN Client]
        TeleportClient[Teleport Client]
    end
    
    subgraph "AWS Dev Account"
        subgraph "VPN Gateway"
            VPNGateway[VPN Gateway]
            VPNConnection[VPN Connection]
            VPNEndpoint[VPN Endpoint]
        end
        
        subgraph "Teleport Infrastructure"
            TeleportServer[Teleport Server]
            TeleportAuth[Teleport Auth Server]
            TeleportProxy[Teleport Proxy]
        end
        
        subgraph "Dev VPC"
            DevResources[Dev Resources]
            DevApps[Dev Applications]
            DevDatabases[Dev Databases]
        end
    end
    
    %% Access Flow
    Internet --> VPNClient
    Internet --> TeleportClient
    
    VPNClient --> VPNGateway
    TeleportClient --> TeleportServer
    
    VPNGateway --> VPNConnection
    VPNConnection --> VPNEndpoint
    VPNEndpoint --> DevResources
    
    TeleportServer --> TeleportAuth
    TeleportAuth --> TeleportProxy
    TeleportProxy --> DevResources
    
    %% Resource Access
    DevResources --> DevApps
    DevResources --> DevDatabases
    
    %% Styling
    classDef external fill:#fce4ec
    classDef vpn fill:#e3f2fd
    classDef teleport fill:#e8f5e8
    classDef dev fill:#fff3e0
    
    class Internet,VPNClient,TeleportClient external
    class VPNGateway,VPNConnection,VPNEndpoint vpn
    class TeleportServer,TeleportAuth,TeleportProxy teleport
    class DevResources,DevApps,DevDatabases dev
```

## Security Architecture

```mermaid
graph TB
    subgraph "Security Layers"
        subgraph "Network Security"
            VPC[VPC Isolation]
            Subnets[Subnet Segmentation]
            NACLs[Network ACLs]
            SecurityGroups[Security Groups]
        end
        
        subgraph "Access Security"
            IAM[IAM Roles & Policies]
            MFA[Multi-Factor Authentication]
            VPN[VPN Access]
            Teleport[Teleport Access]
        end
        
        subgraph "Data Security"
            Encryption[Data Encryption]
            Backup[Backup & Recovery]
            Audit[Audit Logging]
            Compliance[Compliance Monitoring]
        end
        
        subgraph "Monitoring Security"
            CloudTrail[CloudTrail]
            GuardDuty[GuardDuty]
            Config[AWS Config]
            SecurityHub[Security Hub]
        end
    end
    
    %% Security Flow
    VPC --> Subnets
    Subnets --> NACLs
    NACLs --> SecurityGroups
    
    IAM --> MFA
    MFA --> VPN
    VPN --> Teleport
    
    Encryption --> Backup
    Backup --> Audit
    Audit --> Compliance
    
    CloudTrail --> GuardDuty
    GuardDuty --> Config
    Config --> SecurityHub
    
    %% Styling
    classDef network fill:#e3f2fd
    classDef access fill:#e8f5e8
    classDef data fill:#fff3e0
    classDef monitoring fill:#ffebee
    
    class VPC,Subnets,NACLs,SecurityGroups network
    class IAM,MFA,VPN,Teleport access
    class Encryption,Backup,Audit,Compliance data
    class CloudTrail,GuardDuty,Config,SecurityHub monitoring
```

## Implementation Phases

```mermaid
graph LR
    subgraph "Phase 1: Account Setup"
        A1[Create Dev Account]
        A2[Configure IAM]
        A3[Set up Pulumi]
        A4[Configure Access]
    end
    
    subgraph "Phase 2: Infrastructure"
        B1[Create VPC]
        B2[Deploy VPN/Teleport]
        B3[Set up Monitoring]
        B4[Configure Security]
    end
    
    subgraph "Phase 3: Resource Import"
        C1[Import RDS]
        C2[Import EB]
        C3[Import Lambda]
        C4[Import Route53]
        C5[Import Cognito]
    end
    
    subgraph "Phase 4: Data Migration"
        D1[Plan RDS Migration]
        D2[Plan EB Migration]
        D3[Plan Lambda Migration]
        D4[Plan DNS Migration]
        D5[Plan Cognito Migration]
    end
    
    A1 --> A2
    A2 --> A3
    A3 --> A4
    A4 --> B1
    
    B1 --> B2
    B2 --> B3
    B3 --> B4
    B4 --> C1
    
    C1 --> C2
    C2 --> C3
    C3 --> C4
    C4 --> C5
    C5 --> D1
    
    D1 --> D2
    D2 --> D3
    D3 --> D4
    D4 --> D5
    
    %% Styling
    classDef phase1 fill:#ffebee
    classDef phase2 fill:#e1f5fe
    classDef phase3 fill:#e8eaf6
    classDef phase4 fill:#e8f5e8
    
    class A1,A2,A3,A4 phase1
    class B1,B2,B3,B4 phase2
    class C1,C2,C3,C4,C5 phase3
    class D1,D2,D3,D4,D5 phase4
```

## Key Benefits

### **Infrastructure as Code**
- **Version Control**: All infrastructure in Git
- **Reproducibility**: Consistent deployments
- **Collaboration**: Team-based infrastructure management
- **Audit Trail**: Complete change history

### **Resource Management**
- **Centralized Control**: All resources managed by Pulumi
- **Import Capability**: Existing resources into Pulumi
- **State Management**: Reliable state tracking
- **Rollback Capability**: Quick rollback procedures

### **Security & Compliance**
- **Network Isolation**: Proper VPC segmentation
- **Access Control**: VPN/Teleport secure access
- **Monitoring**: Comprehensive security monitoring
- **Compliance**: Automated compliance checking

### **Operational Efficiency**
- **Automation**: Automated infrastructure deployment
- **Monitoring**: Comprehensive monitoring and alerting
- **Documentation**: Self-documenting infrastructure
- **Training**: Team training on Pulumi management

---

**Last Updated**: September 25, 2025
**Version**: 1.0
**Status**: Planning Phase
