# Terraform Comprehensive Cheat Sheet

## 1. Basics
- **Initialize Terraform**: `terraform init`
- **Format Code**: `terraform fmt`
- **Validate Configuration**: `terraform validate`
- **Show Plan**: `terraform plan`
- **Apply Changes**: `terraform apply`
- **Destroy Infrastructure**: `terraform destroy`
- **Show State**: `terraform show`
- **List Resources in State**: `terraform state list`
- **Remove Resource from State**: `terraform state rm <resource>`

---

## 2. Configuration Blocks
### Provider Configuration
```hcl
provider "aws" {
  region = "us-east-1"
}
```
### Resource Definition
```hcl
resource "aws_instance" "example" {
  ami           = "ami-123456"
  instance_type = "t2.micro"
}
```

---

## 3. Variables & Outputs
### Variables
```hcl
variable "instance_type" {
  description = "Instance type"
  type        = string
  default     = "t2.micro"
}
```
### Outputs
```hcl
output "instance_ip" {
  value = aws_instance.example.public_ip
}
```

---

## 4. State Management
- **View State**: `terraform state list`
- **Remove Resource from State**: `terraform state rm <resource>`
- **Move Resource in State**: `terraform state mv <old> <new>`
- **Refresh State**: `terraform refresh`

---

## 5. Terraform Backend (State Management)
Terraform supports remote state storage for collaboration.

### S3 Backend Example
```hcl
terraform {
  backend "s3" {
    bucket         = "my-terraform-state"
    key            = "terraform/state.tfstate"
    region         = "us-east-1"
    dynamodb_table = "terraform-lock"
    encrypt        = true
  }
}
```
### Backend Commands
- **Initialize Backend**: `terraform init`
- **Migrate State to Backend**: `terraform init -migrate-state`
- **Manually Pull State**: `terraform state pull`
- **Manually Push State**: `terraform state push`

---

## 6. Modules
### Usage
```hcl
module "ec2" {
  source        = "./modules/ec2"
  instance_type = "t2.micro"
}
```
### Module Structure
```
modules/
  ├── ec2/
  │   ├── main.tf
  │   ├── variables.tf
  │   ├── outputs.tf
```

---

## 7. Workspaces
- **List Workspaces**: `terraform workspace list`
- **Create Workspace**: `terraform workspace new <name>`
- **Select Workspace**: `terraform workspace select <name>`
- **Delete Workspace**: `terraform workspace delete <name>`

---

## 8. Provisioners
### Local Exec Example
```hcl
resource "null_resource" "example" {
  provisioner "local-exec" {
    command = "echo Hello, Terraform!"
  }
}
```
### Remote Exec Example
```hcl
resource "null_resource" "example" {
  provisioner "remote-exec" {
    inline = [
      "sudo apt update",
      "sudo apt install -y nginx"
    ]
  }
}
```

---

## 9. Data Sources
### Fetch Data Example
```hcl
data "aws_ami" "latest" {
  most_recent = true
  owners      = ["amazon"]
  filter {
    name   = "name"
    values = ["amzn2-ami-hvm-*-x86_64-gp2"]
  }
}
```

---

## 10. Common Commands
| Command                 | Description |
|-------------------------|-------------|
| `terraform init`        | Initialize Terraform |
| `terraform plan`        | Show execution plan |
| `terraform apply`       | Apply configuration |
| `terraform destroy`     | Destroy infrastructure |
| `terraform validate`    | Validate configuration |
| `terraform fmt`         | Format code |
| `terraform state list`  | List state resources |
| `terraform workspace list` | List workspaces |
| `terraform refresh` | Sync state with real infrastructure |
| `terraform output` | Show output values |
| `terraform import` | Import existing resources |
| `terraform graph` | Generate a visual graph of resources |
