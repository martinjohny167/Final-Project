# Terraform AWS Infrastructure Project - Summary

## Project Overview

This project implements a scalable AWS infrastructure using Terraform with a focus on Infrastructure as Code (IaC) best practices. The implementation includes:

1. **S3 Bucket for State Storage**
   - Created with versioning enabled 
   - Used as a backend for Terraform state files

2. **DynamoDB Table for State Locking**
   - Prevents concurrent state updates
   - Uses a LockID as the hash key

3. **VPC Infrastructure**
   - Custom VPC with public subnet
   - Internet Gateway for internet access
   - Route tables and associations
   - Security group allowing SSH, HTTP, and HTTPS traffic

4. **EC2 Instance**
   - Launched in the public subnet with public IP
   - Uses configurable AMI ID and instance type
   - Security group allows required ports

## Project Structure

The project follows a modular structure:

```
.
├── main.tf                 # Main configuration with resource definitions
├── backend.tf              # Backend configuration for state storage
├── variables.tf            # Variable declarations with descriptions
├── terraform.tfvars        # Variable values for configuration
├── outputs.tf              # Output values after deployment
├── modules/                # Modular components
│   ├── ec2/                # EC2 instance module
│   │   ├── main.tf
│   │   ├── variables.tf
│   │   └── outputs.tf
│   └── vpc/                # VPC module
│       ├── main.tf
│       ├── variables.tf
│       └── outputs.tf
├── README.md               # Project documentation
├── usage-instructions.md   # Detailed usage guide
└── project-summary.md      # This summary document
```

## Implementation Details

### Infrastructure as Code Principles Applied

1. **Modularity**
   - Separated VPC and EC2 configurations into modules
   - Each module has its own variables, main logic, and outputs

2. **Configuration as Code**
   - All infrastructure defined in code
   - No manual steps required for deployment
   - Version-controlled infrastructure

3. **Infrastructure State Management**
   - Remote state storage in S3
   - State locking with DynamoDB
   - State versioning through S3 bucket versioning

4. **Variable Parameterization**
   - Variables defined in variables.tf
   - Values provided in terraform.tfvars
   - Separation of configuration from implementation

### Security Considerations

1. **Network Security**
   - VPC with proper routing
   - Security groups with principle of least privilege
   - Public subnet only for resources that need internet access

2. **Access Control**
   - Optional SSH key pair for EC2 access
   - Security group rules limit access to necessary ports


## Sceenshots 
![Image](https://github.com/user-attachments/assets/8b1554cd-b10a-4103-832f-ecbc91259d0b)
![Image](https://github.com/user-attachments/assets/ea44bf60-c37c-4e3a-b706-8369c109531e)
![Image](https://github.com/user-attachments/assets/c8592bb2-2fdc-45ad-b724-8a1be75f1ae0)
![Image](https://github.com/user-attachments/assets/0b3229fb-1e3e-424b-b86c-dcf6175a52af)
![Image](https://github.com/user-attachments/assets/3905aba1-7133-4e3b-9828-c48f053ce567)
![Image](https://github.com/user-attachments/assets/0bd84992-3521-4b74-bfa9-ad0342570761)
![Image](https://github.com/user-attachments/assets/d615e490-31a7-4e02-b3f7-1cd6e41cb8cf)
![Image](https://github.com/user-attachments/assets/e0a4719c-2af3-43c5-b399-42b70fc5c096)
![Image](https://github.com/user-attachments/assets/40ed8b03-81e6-47f4-9446-89c552160783)
## Future Enhancements

Potential improvements for this project:
1. Add private subnets for better security
2. Implement auto-scaling for EC2 instances
3. Add encrypted EBS volumes
4. Implement IAM roles and policies
5. Add load balancing for high availability
6. Integrate with other AWS services like RDS or Lambda 
