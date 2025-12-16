# spacelift-iac-orchestration
End-to-end infrastructure automation on AWS using Terraform and Ansible, orchestrated with Spacelift for dependency management, secure secret handling, and repeatable deployments.


# Spacelift Terraform + Ansible AWS Automation

This project demonstrates a production-style Infrastructure as Code (IaC) workflow using **Terraform** and **Ansible**, orchestrated through **Spacelift**.  
The goal is to provision AWS EC2 infrastructure and automatically configure it using Ansible in a controlled, scalable, and repeatable manner.

---

## Problem Statement

In many organizations:
- Infrastructure provisioning and configuration are handled separately
- Manual handoffs between Terraform and Ansible introduce delays
- Secrets are hardcoded or poorly managed
- Deployments are slow, error-prone, and difficult to reproduce

This project solves these problems using Spacelift as an orchestration and policy layer.

---

## Solution Overview

- **Terraform** provisions EC2 instances on AWS
- **Ansible** installs and configures system packages (htop, nginx)
- **Spacelift** orchestrates execution order, manages secrets, and enforces best practices
- Terraform outputs dynamically generate Ansible inventory

---

## Architecture

1. Spacelift triggers the Terraform stack
2. Terraform provisions multiple EC2 instances
3. Public IPs are exported as Terraform outputs
4. Spacelift passes outputs to the Ansible stack
5. Ansible configures all instances in parallel

---

## Tech Stack

- AWS EC2
- Terraform
- Ansible
- Spacelift
- Linux (Ubuntu)
- SSH

---

## Repository Structure

```text
.
├── terraform/
│   ├── main.tf
│   ├── variables.tf
│   └── outputs.tf
│
├── ansible/
│   ├── inventory.tpl
│   ├── htop.yml
│   └── nginx.yml
│
└── README.md

