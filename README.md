# Azure IaC Landing Zone

## What I Built
I provisioned a secure Azure network foundation using Terraform.
All infrastructure is defined as code and deployed via the Azure CLI —
no manual portal configuration.

## Resources I Deployed
- Resource Group
- Virtual Network (10.0.0.0/16)
- Application Subnet (10.0.1.0/24)
- Network Security Group

## Architecture
![Azure Portal showing deployed resources](screenshot.png)

## Tools I Used
- Terraform v1.15
- Azure CLI
- Azure Resource Manager (azurerm provider v4)

## How to Deploy
1. Clone this repo
2. Run `az login`
3. Add your subscription ID to `terraform.tfvars`
4. Run `terraform init && terraform plan && terraform apply`

## How to Destroy
```bash
terraform destroy
```