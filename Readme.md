## REQUIREMENTS

1. Terraform v1.3.7
2. Ansible [core 2.10.8]
3. AWS CLI [aws configure]

4. ## MINI PROJECT

- Using Terraform, create 3 EC2 instances and put them behind an Elastic Load Balancer
- Make sure the after applying your plan, Terraform exports the public IP addresses of the 3 instances to a file called host-inventory
- Get a .com.ng or any other domain name for yourself (be creative, this will be a domain you can keep using) and set it up with AWS Route53 within your terraform plan, then add an A record for subdomain terraform-test that points to your ELB IP address.
- Create an Ansible script that uses the host-inventory file Terraform created to install Apache, set timezone to Africa/Lagos and displays a simple HTML page that displays content to clearly identify on all 3 EC2 instances.
- Your project is complete when one visits terraform-test.yourdomain.com and it shows the content from your instances, while rotating between the servers as your refresh to display their unique content.
- Submit both the Ansible and Terraform files created

- # Project: Terraform and Ansible Deployment

## Overview

This project involves the deployment of three EC2 instances behind an Elastic Load Balancer (ELB) using Terraform. After applying the Terraform plan, the public IP addresses of the instances are exported to a file called `host-inventory`. Additionally, a custom domain with the extension `.com.ng` is acquired and set up with AWS Route53 within the Terraform plan. An A record for the subdomain `terraform-test` is created, pointing to the ELB's IP address.

To automate the configuration of the EC2 instances, set the timezone to Africa/Lagos, and install Apache, an Ansible script is used. This script reads the `host-inventory` file created by Terraform and executes the necessary configurations on each instance. The final goal is to have the subdomain `terraform-test.yourdomain.com` display a simple HTML page on the instances, with the ability to rotate between servers upon page refresh.

## Project Structure

### Terraform

- **terraform/**
  - **alb.tf:** Defines the configuration for the Elastic Load Balancer (ELB).
  - **ec2.tf:** Configures the EC2 instances.
  - **igw.tf:** Manages the Internet Gateway.
  - **pub_security.tf:** Configures security groups for public resources.
  - **routes.tf:** Defines routing configurations.
  - **routes53.tf:** Sets up Route53 for domain management.
  - **subnet.tf:** Manages subnets.
  - **variable.tf:** Defines variables used in the Terraform configuration.
  - **vpc.tf:** Configures the Virtual Private Cloud (VPC).
  - **outputs.tf:** Specifies the outputs that Terraform will generate, including the `host-inventory` file.

### Ansible

- **ansible/**
  - **roles/**
    - **ubuntu20.04/**
      - **tasks/**
      -  **ubuntu.sh, ubuntu.yml, main.yml**
      -**amz/**
         -**tasks/**
            -**amz_linux.sh, amz_linux.yml, main.yml**
          - **debain12/**
      - **tasks/**
      -  **debain12.sh, debain12.yml, main.yml**
         
           
  - **host-inventory:** Generated by Terraform, contains the public IP addresses of the EC2 instances.
  - **ansible.cfg:** Configuration file for Ansible, specifying the location of the `host-inventory` file.
  - **main.yml:** Main Ansible playbook that includes roles for Ubuntu configuration.

## Instructions

1. **Terraform Deployment:**
   - Navigate to the `terraform/` directory.
   - Run `terraform init` to initialize the Terraform configuration.
   - Execute `terraform apply` and follow the prompts to apply the configuration.
   - After completion, note the public IP addresses of the instances and the ELB.

2. **Ansible Configuration:**
   - Navigate to the `ansible/` directory.
   - Ensure that the `host-inventory` file is generated by Terraform and contains the correct IP addresses.
   - Run `ansible-playbook main.yml` to configure the instances using Ansible.

3. **Access the Website:**
   - Visit `terraform-test.yourdomain.com` in a web browser.
   - Observe the simple HTML page displaying content from the rotating instances.

## Notes
- Ensure AWS CLI is configured with the necessary credentials for Terraform and Ansible to interact with AWS services.
- Customize the domain name (`yourdomain.com.ng`) and adapt configurations as needed.

Feel free to reach out if you have any questions or encounter issues during the deployment process. Happy coding!

## HOW TO RUN THE CONFIGURATION

Go into the terraform folder 

 ```
  cd terraform
   terraform init 
 ```

then plan the changes
and later apply 

```
 terraform plan
 terraform apply --auto approve
```

When your instances are runnig then proceed to run the ansible files then go into the root folder 

```
   cd ..
```

run the playbook now 


 ```
      ansible-playbook -i host-inventory main.yml
```
 
  ![Random Color Generator](Random%20Color%20Generator.png)

