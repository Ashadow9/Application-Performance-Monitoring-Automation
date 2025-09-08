# Application-Performance-Monitoring-Automation


## Architecture Diagram

```mermaid
graph TB
    subgraph "Application Layer"
        APP[Application Services]
        EKS[EKS/EC2/Lambda Apps]
    end
    
    subgraph "Monitoring Layer"
        CAS[CloudWatch Application Signals]
        CWM[CloudWatch Metrics]
        CWA[CloudWatch Alarms]
    end
    
    subgraph "Event Processing"
        EB[EventBridge]
        EBR[EventBridge Rules]
    end
    
    subgraph "Response Layer"
        LF[Lambda Functions]
        AS[Auto Scaling]
        SNS[SNS Topics]
    end
    
    subgraph "Notification Layer"
        EMAIL[Email Notifications]
        SLACK[Slack Integration]
        DASH[CloudWatch Dashboard]
    end
    
    APP --> CAS
    EKS --> CAS
    CAS --> CWM
    CWM --> CWA
    CWA --> EB
    EB --> EBR
    EBR --> LF
    LF --> AS
    LF --> SNS
    SNS --> EMAIL
    SNS --> SLACK
    CAS --> DASH
    
    style CAS fill:#FF9900
    style EB fill:#FF4444
    style LF fill:#FF9900
    style SNS fill:#FF9900
```

## Prerequisites

1. AWS account with appropriate permissions for CloudWatch, EventBridge, Lambda, SNS, and IAM services
2. AWS CLI v2 installed and configured (minimum version 2.0) or AWS CloudShell access
3. Basic knowledge of AWS monitoring services and event-driven architectures
4. An existing application running on AWS (EKS, EC2, or Lambda functions)
5. Estimated cost: $20-50/month for moderate monitoring workload (varies based on metrics volume and notification frequency)
