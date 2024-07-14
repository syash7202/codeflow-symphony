# Codeflow Symphony

This repository demonstrates a CI/CD pipeline using AWS services to automate the deployment of applications, specifically developed for automatic static website development and deployment. The pipeline ensures that code changes are continuously integrated, tested, and deployed to a production environment, providing a robust and scalable solution for application development and deployment.

![Architecture](./CICD.png)

## Key Components:

- **Code Repository:**

  - `GitHub`: Central repository for managing the application's codebase. Developers commit and push code changes to this repository, triggering the CI/CD pipeline.

- **CI/CD Pipeline:**

  - `AWS CodePipeline`: Orchestrates the CI/CD workflow, integrating various AWS services to automate the deployment process. -` AWS CodeCommi`t: Stores the fetched code from GitHub as part of the pipeline's workflow.
  - `AWS CodeDeploy`: Deploys the application to Amazon EC2 instances in the production environment.

- **Infrastructure:**

  - `Virtual Private Cloud (VPC)`: Ensures secure communication within the deployment environment.
  - `Application Load Balancer (ALB)`: Distributes incoming user requests across multiple Availability Zones for high availability and fault tolerance.
  - `Amazon EC2 with Auto Scaling`: EC2 instances in multiple Availability Zones managed by Auto Scaling groups to handle varying traffic loads.

  - `EC2 User data:` the instance template attached to ASG can be configuired according to the application requirements. Static hosting can be done but it will be benification to use S3 for hosting core static websites.

## Workflow

- **Code Commit:**

  Developers commit code changes to the GitHub repository.
  A webhook in GitHub triggers AWS CodePipeline when changes are pushed.

- **Code Fetch:**

  AWS CodePipeline fetches the latest code from the GitHub repository.
  The code is stored in AWS CodeCommit for further processing.

- **Deployment:**

  AWS CodePipeline triggers AWS CodeDeploy to deploy the application.
  The deployment occurs within a secure VPC, ensuring secure and reliable communication.
  The Application Load Balancer routes user requests to the appropriate EC2 instances across multiple Availability Zones.
  Auto Scaling adjusts the number of EC2 instances based on traffic, ensuring optimal performance and cost-efficiency.

## Benefits:

- `Continuous Integration and Deployment`: Automates the entire process from code commit to deployment, reducing manual effort and increasing deployment frequency.

- `Scalability and High Availability`: Utilizes AWS services like AGS & multi AZs to ensure the application scales based on demand and remains highly available.

- `Security`: The use of a VPC provides a secure environment for the deployment.

- `Load Balancing`: The Application Load Balancer ensures efficient distribution of user requests, improving application performance and reliability.v
