# Azure IaC Landing Zone

## Business Problem
Most infrastructure mistakes don't happen because someone wrote bad code. They happen because someone clicked the wrong thing in the portal and nobody can reproduce what they did. Manual configuration is invisible, unrepeatable, and one human error away from taking down a production environment. I built this to show how you eliminate that risk entirely.

## What I Built
I provisioned a secure Azure network foundation using Terraform. Everything is defined as code and deployed through the Azure CLI. No clicking around the portal, no manual configuration.

## Architecture
![Azure Portal showing deployed resources](screenshot.png)

## Resources I Deployed
Resource Group
Virtual Network (10.0.0.0/16)
Application Subnet (10.0.1.0/24)
Network Security Group

## Key Decisions

**Why Terraform over the portal?**
Manual portal configuration is not repeatable. If something breaks or I need to spin up a second environment, I'd have to remember every click. With Terraform the infrastructure lives in code, it's version controlled, and I can rebuild the entire environment in under two minutes.

**Why separate variables from the main config?**
Hardcoding values like subscription ID and region directly into main.tf makes the code environment-specific and impossible to reuse. Pulling them into variables means the same config works across dev, staging, and production without touching the core files.

**Why gitignore the tfvars and state files?**
The tfvars file holds my subscription ID and the state file contains a full map of live infrastructure. Pushing either to a public repo is a security risk. Sensitive values stay local and never touch version control.

## Tools I Used
Terraform v1.15
Azure CLI
Azure Resource Manager (azurerm provider v4)

## How to Deploy
1. Clone this repo
2. Run az login
3. Add your subscription ID to terraform.tfvars
4. Run terraform init && terraform plan && terraform apply

## How to Destroy
terraform destroy