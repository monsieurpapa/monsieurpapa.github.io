 ---
layout: post
title: Migrating a PostgreSQL Database from Kubernetes to Amazon RDS
comments: true
---

![_config.yml]({{ site.baseurl }}/images/rds.png)
"Ever wondered what happens when a Kubernetes cluster and Amazon RDS walk into a bar? We're about to spill the beans on why your PostgreSQL database might ditch the K8s dance floor for the RDS rock concert! 🚀🎸"

## Introduction

Migrating a PostgreSQL database from a Kubernetes (K8s) cluster to Amazon RDS for PostgreSQL (RDS) offers numerous advantages, driven by specific requirements and business needs. In this technical blog post, we'll explore the motivations behind such a migration and provide a step-by-step guide to help you seamlessly transition your database. Let's dive in!

## Motivation

Before delving into the migration process, let's understand the reasons why you might consider migrating your PostgreSQL database from a Kubernetes cluster to Amazon RDS:

1. **Managed Service Benefits**: Amazon RDS is a fully managed database service, relieving your team from routine tasks like backups, patching, and scaling. This allows your operations team to focus on critical aspects of your application.

2. **Scalability and Performance**: RDS offers automated scaling to handle varying workloads, enhancing scalability and performance without manual Kubernetes adjustments.

3. **High Availability and Reliability**: RDS features like Multi-AZ deployments and automated failover ensure high availability and reliability, simplifying your architecture.

4. **Security and Compliance**: RDS provides robust security features, including encryption, IAM-based authentication, and integration with IAM for enhanced security and compliance.

5. **Backup and Restore**: RDS simplifies backup and recovery with automated options, streamlining your disaster recovery strategy.

6. **Cost Efficiency**: Despite costs, RDS can be cost-effective due to reduced operational overhead. Careful cost analysis is essential.

7. **Database Expertise**: RDS offers access to AWS expertise, beneficial if your team lacks in-depth PostgreSQL management skills.

8. **Simplified Deployment**: Migrating to RDS streamlines deployment, especially for teams less familiar with Kubernetes.

9. **Vendor Lock-in Considerations**: Be cautious of vendor lock-in, as RDS might make switching providers challenging.

10. **Future Growth and Innovation**: RDS frees up resources for innovation, letting your team focus on application development and business growth.

## Migration Procedure

Here's a step-by-step guide to migrate your PostgreSQL database from Kubernetes to Amazon RDS:

1. **Create a Kubernetes Cluster**:
   - Execute: `eksctl create cluster ...` (See [explanation](https://monsieurpapa.github.io/DeployK8sCluster/))

2. **Allow Cluster to Manage RDS Instance**:
   - Run:
   ```bash
   aws ecr-public get-login-password --region us-east-1 | helm registry login --username AWS --password-stdin public.ecr.aws
   ```
   
   ``` helm install --create-namespace -n ack-system oci://public.ecr.aws/aws-controllers-k8s/rds-chart --version=0.0.27 --generate-name --set=aws.region=us-east-1```


   ``` APP_NAMESPACE=myproject-dev```

   
   ```kubectl create ns "${APP_NAMESPACE}"```

4. Generate Cluster Subnets and Create DBSubnetGroup:

- Execute:
  ```bash
  RDS_SUBNET_GROUP_NAME="myproject-SUBNET-GROUP-NAME"
  RDS_SUBNET_GROUP_DESCRIPTION="<myproject subnet group description>"
  ```
  
  
  ```EKS_VPC_ID=$(aws eks describe-cluster --name="${EKS_CLUSTER_NAME}" --query "cluster.resourcesVpcConfig.vpcId" --output text)```


   ```EKS_SUBNET_IDS=$(aws ec2 describe-subnets --filters "Name=vpc-id,Values=${EKS_VPC_ID}" --query 'Subnets[*].SubnetId' --output text) ```

4. Create DB Subnet Group YAML:

- Generate db-subnet-groups.yaml with specified subnets.
- Apply DBSubnetGroup Configuration:

  Run: ```kubectl apply -f db-subnet-groups.yaml```
  
- Create Security Group for RDS:

  ```bash
      RDS_SECURITY_GROUP_NAME="<myproject security group name>"
  ```
  
  ```RDS_SECURITY_GROUP_DESCRIPTION="<myproject rds security group description>" ```
  
  ``` EKS_CIDR_RANGE=$(aws ec2 describe-vpcs --vpc-ids $EKS_VPC_ID --query "Vpcs[].CidrBlock" --output text)```
  
  ``` RDS_SECURITY_GROUP_ID=$(aws ec2 create-security-group --group-name "${RDS_SUBNET_GROUP_NAME}" --description "${RDS_SUBNET_GROUP_DESCRIPTION}" --vpc-id "${EKS_VPC_ID}" --output text) ```
  
  ``` aws ec2 authorize-security-group-ingress --group-id "${RDS_SECURITY_GROUP_ID}" --protocol tcp --port 5432 --cidr "${EKS_CIDR_RANGE}"```

- Provision Amazon RDS Instance:

  -  Create Kubernetes secret with database credentials.
  - Deploy DBInstance using a manifest with high availability, backups, monitoring, and encrypted storage.


# Validation
- To view RDS instance details: 
    ``` kubectl describe dbinstance -n "${APP_NAMESPACE}" "${RDS_DB_INSTANCE_NAME}" ```

- Check RDS instance availability:
    ``` kubectl get dbinstance -n "${APP_NAMESPACE}" "${RDS_DB_INSTANCE_NAME}" -o jsonpath='{.status.dbInstanceStatus}' ```

# Deployment Description

- Store PostgreSQL instance endpoint and port:

    ``` bash
        RDS_DB_INSTANCE_HOST=$(kubectl get dbinstance -n "${APP_NAMESPACE}" "${RDS_DB_INSTANCE_NAME}" -o jsonpath='{.status.endpoint.address}')
    ```
    
  ```bash RDS_DB_INSTANCE_PORT=$(kubectl get dbinstance -n "${APP_NAMESPACE}" "${RDS_DB_INSTANCE_NAME}" -o jsonpath='{.status.endpoint.port}') ```

- Deploy your project to the production cluster.

- Cleanup
  Refer to the AWS blog post for cleanup steps : https://aws.amazon.com/blogs/database/deploy-amazon-rds-databases-for-applications-in-kubernetes/

# Conclusion
Migrating your PostgreSQL database from a Kubernetes cluster to Amazon RDS offers a range of benefits, from managed services to enhanced scalability, security, and more. By following this comprehensive guide, you can efficiently migrate your database, optimize your infrastructure, and focus on innovation. Happy migrating!
