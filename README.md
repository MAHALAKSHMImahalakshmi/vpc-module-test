
# 🚀 vpc-module-test: Real-World Terraform VPC Module Testing

Welcome! This repository demonstrates how to **test and validate a reusable AWS VPC Terraform module** in practical scenarios. It’s built to showcase my skills in DevOps, cloud automation, and real troubleshooting. Whether you’re a recruiter, a beginner, or a fellow cloud engineer, you’ll find depth, clarity, and plenty of learning gems here.

## 🗂️ What This Repo Does

- **Deploys a real AWS VPC** using my custom public Terraform module
- Provisions public, private, and database subnets, IGW/NAT, route tables, and more
- Teaches you robust, reusable Infrastructure as Code practices
- Documents every step, mistake, fix, and “aha!” moment along my learning journey


## 👩💻 Author & Intent

**I’m Mahalakshmi R**—I started this journey with **zero AWS/Terraform knowledge**. This repo is my story of becoming cloud-fluent, showing real growth, not just final results.

> “Sharing lessons—including my mistakes—turns experience into community knowledge.”

## 📚 What’s Inside?

```
.
├── main.tf           # Declares module usage & variables to deploy VPC
├── variables.tf      # Input values (CIDRs, subnets, project tags)
├── output.tf         # Outputs for deployed resource IDs/attributes
├── provider.tf       # AWS provider block and region setup
├── README.md         # This file: usage, learning, debugging advice
└── .terraform.lock.hcl # Dependency lock
```

## 🔍 Key Features Tested

- **Module input/output interface:** Can you swap VPC/subnet configs easily?
- **Idempotency:** `terraform plan` always predicts, `apply` changes once
- **State changes:** Practice updating, rolling back, or deleting infra safely
- **Debugging:** Every error is logged—with the fix and a “lesson learned”
- **Clean-up:** Responsible teardown (`terraform destroy`) to avoid AWS bills

## 🚦 Step-by-Step Workflow

### 1. **Clone the Repo**

```bash
git clone https://github.com/MAHALAKSHMImahalakshmi/vpc-module-test.git
cd vpc-module-test
```

### 2. **Customize Variables**

Edit `variables.tf` or override in CLI to choose your VPC CIDR, subnet ranges, tags, etc.

### 3. **Initialize Terraform**

```bash
terraform init
```

This pulls required providers and the VPC module from GitHub.

### 4. **Plan and Review**

```bash
terraform plan
```

See what AWS resources will be created—read the diff before you run!

### 5. **Deploy!**

```bash
terraform apply
```

- Watch the creation steps.
- Check the AWS Console for visual confirmation!

### 6. **Inspect Outputs**

After deployment, see IDs, subnet ARNs, and route tables instantly in your terminal.

### 7. **Destroy to Clean Up**

```bash
terraform destroy
```

Always keep your free tier safe—easy clean-up by design.

## 🔎 Example Main.tf Snippet

```hcl
module "vpc" {
  source = "git::https://github.com/MAHALAKSHMImahalakshmi/terraform-aws-vpc.git"
  project     = "roboshop"
  environment = "dev"
  cidr_block  = "10.0.0.0/16"
  public_subnet_cidrs  = ["10.0.1.0/24", "10.0.2.0/24"]
  private_subnet_cidrs = ["10.0.3.0/24", "10.0.4.0/24"]
  database_subnet_cidrs = ["10.0.5.0/24", "10.0.6.0/24"]
}
```

## 🚫 Mistakes, Debugging & Lessons Learned

- *Mixed up subnet CIDRs?*  
  → Caught at `terraform plan`—now always double-check test VPC network ranges.

- *Route tables didn’t attach as expected?*  
  → Fixed by reading Terraform documentation and adding clear outputs in the module!

- *Forgot to `terraform destroy`?*  
  → Pay careful attention to AWS usage. Responsible automation is as important as building infra!

- *Learning to read and interpret errors is just as important as writing code.*

## 🔧 Tools & Skills Demonstrated

- **Terraform CLI**: modules, remote sources, state management, drift detection
- **AWS Free Tier**: VPC, subnets, gateways, all with cost-awareness!
- **VS Code**: Infrastructure-as-Code syntax linting, formatting, and error highlighting
- **Git & GitHub**: Open versioned, modular, and documented codebase

## 🎓 Key Learnings For Everyone

- Understand the “why” behind VPC, subnets, NAT, route tables (see the companion [VPC Module README](https://github.com/MAHALAKSHMImahalakshmi/terraform-aws-vpc#readme))
- **map_public_ip_on_launch** is *only* for public subnets—know where your EC2s will be internet-reachable!
- Always `plan` before `apply` to avoid surprises.
- Commit your changes early—version control saves you from breaking things.
- Practice iterative improvement: add, test, debug, refactor, repeat!

## 💬 Why I Made This Public

- To document **real learning**—mistakes, fixes, best practices—so others grow faster, too
- To **attract recruiters** and potential mentors by showcasing genuine project work
- To invite contributions, questions, and feedback from the DevOps community



- ⭐ Star and share if you learned something!
- Clone, copy, and use these patterns in your own projects—in or outside AWS
- Help others by reporting issues or suggesting improvements

This project is a living portfolio—**designed for clarity, learning, and professional readiness.**

**Thanks for visiting—happy Terraforming!**  
*—Mahalakshmi R*

