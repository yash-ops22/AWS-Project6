# Amazon RDS
Amazon Relational Database Service is a distributed relational database 
service by Amazon Web Services. It is a web service running "in the cloud"
designed to simplify the setup, operation, and scaling of a relational 
database for use in applications.

# Task 
Deploy the Wordpress application on Kubernetes and AWS using terraform including the following steps;

1.  Write an Infrastructure as code using terraform, which automatically deploy the Wordpress application
2. On AWS, use RDS service for the relational database for Wordpress application.
3. Deploy the Wordpress as a container either on top of Minikube or EKS or Fargate service on AWS
4. The Wordpress application should be accessible from the public world if deployed on AWS or through workstation if deployed on Minikube.

# Requirements:
1. We have to configure our Profile or IAM user
2. We need minikube or EKS for Kubernetes, Here I am using EKS Service.
3. For using EKS through command Line we have to install and configure eksctl.
4 We have to configure kubectl to launch wordpress.

# Steps
Creating AWS RDS instance with security Group...

    provider "aws" {
    region     = "ap-south-1"
    profile    = "Yashu"
    }

    resource "aws_security_group" "sg-rds" {
    name        = "rds-database"
    vpc_id      = "vpc-12a7486f"

     ingress {
     description = "VPC"
     from_port   = 3306
     to_port     = 3306
     protocol    = "tcp"
     cidr_blocks = ["0.0.0.0/0"]
     }
     egress {
     from_port   = 0
     to_port     = 0
     protocol    = "-1"
     cidr_blocks = ["0.0.0.0/0"]
     }

    tags = {
      Name = "rds-database"
     }
   }

    resource "aws_db_instance" "wordpress-rds" {
     allocated_storage    = 10
     storage_type         = "gp2"
     engine               = "mysql"
     engine_version       = "5.7"
     identifier           = "database"
     instance_class       = "db.t2.micro"
     name                 = "mydb"
     username             = "wordpress"
     password             = "10987654321"
     parameter_group_name = "default.mysql5.7"
     publicly_accessible  = "true"
     port                 = "3303"
     final_snapshot_identifier = "false"
     skip_final_snapshot = "true"
    }



      
