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

