# terraform-aws-vpc

## Overview

This Terraform module creates an AWS VPC with a given CIDR block. It also creates multiple subnets (public and private), and for public subnets, it sets up an Internet Gateway (IGW) and appropriate route tables.

## Features

- Creates a VPC with a specified CIDR block
- Creates public and private subnets
- Creates an Internet Gateway (IGW) for public subnets
- Sets up route tables for public subnets

## Usage
```
module "vpc" {
  source = "./module/vpc"

  vpc_config = {
    cidr_block = "10.0.0.0/16"
    name       = "your_vpc_name"
  }
  subnet_config = {
    public_subnet = {
      cidr_block = "10.0.0.0/24"
      az         = "ap-south-1a"
      #To set the subnet as public, default is private
      public     = true
    }

    private_subnet = {
      cidr_block = "10.0.1.0/24"
      az         = "ap-south-1b"
    }
  }
}
```

==================================================================================

Requirements:

*Accept cidr_block from user to create VPC 

*User can create multiple subnets
-Get CIDR block for subnet from user
-Get AZs (availability zone)
-User can mark a subnet as public (default is private)
If public, create IGW
Associte public subnet with Routing table

-------------------------------------------------------------------
Prepare Module for Publish(So others also can used it)
-README.md file
-LICENSE
-Examples
-Push code in GitHub
-Terraform Registry(Publish on)