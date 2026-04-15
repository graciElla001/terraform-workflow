# terraform-workflow

## What is the Terraform state file used for?
The Terraform state file (terraform.tfstate) is used to store information about the infrastructure Terraform manages. It keeps a mapping between your configuration files and the real resources created in the cloud (e.g., servers, storage).
This allows Terraform to know what resources already exist, track changes over time and plan updates without recreating everything 

## Why is storing state locally risky in a team environment?
Storing state locally is risky because of the following:
a.	Teammates don’t share the same state 
b.	Multiple people may overwrite each other’s changes 
c.	If a machine crashes, the state file is lost 
d.	State files may contain sensitive data (e.g., passwords, keys) 
And this can lead to infrastructure errors or duplication.

## What is a remote backend?
A remote backend is a shared storage location for Terraform state, instead of storing it locally on one machine. It allows Team collaboration, State locking (prevents conflicts) and Secure and centralized storage. A common example is storing state in an S3 bucket on Amazon Web Services.

## Example Backend block
``` 
terraform {
  backend "s3" {
    bucket         = "my-terraform-state-bucket"
    key            = "dev/terraform.tfstate"
    region         = "us-east-1"
    user_lockfile = true
    encrypt        = true    
  }
} 

```
