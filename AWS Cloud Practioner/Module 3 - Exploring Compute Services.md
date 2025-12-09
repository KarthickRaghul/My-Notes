![[/image 3.png|image 3.png]]

AWS Lambda - function as a service - Lambda is a serverless compute service that runs code in response to events without the need to provision or manage servers. It automatically manages the underlying infrastructure, scaling resources based on the volume of requests. You are charged only for the compute time consumed, down to the millisecond. Lambda handles execution, scaling, and resource allocation. You can optimize performance by configuring the appropriate memory size for your function.

---

**Amazon Elastic Container Registry (ECR)**

Amazon ECR is a fully managed container registry service that stores, manages, and versions container images. It integrates with other AWS services and provides secure, scalable storage for Docker and OCI images. ECR supports image lifecycle policies for automatic cleanup and uses image scanning to identify vulnerabilities.

**Amazon ECS and Amazon EKS**

Amazon Elastic Container Service (ECS) and Amazon Elastic Kubernetes Service (EKS) are container orchestration services. ECS is AWS's proprietary orchestration platform that simplifies deploying and managing containers at scale. EKS runs Kubernetes, the popular open-source orchestration system, on AWS infrastructure. Both services handle deployment, scaling, load balancing, and managing containerized applications across clusters.

**AWS Fargate**

AWS Fargate is a serverless compute engine for containers that works with both ECS and EKS. It eliminates the need to provision, configure, or manage servers—you simply define your application requirements, and Fargate handles the underlying infrastructure. This allows you to focus on building applications rather than managing compute resources.

---

**Elastic Beanstalk**

AWS Elastic Beanstalk is a Platform as a Service (PaaS) that simplifies application deployment and management. You upload your code, and Beanstalk automatically handles deployment, capacity provisioning, load balancing, auto-scaling, and health monitoring. It supports multiple programming languages and frameworks, allowing developers to focus on writing code rather than managing infrastructure.

**AWS Batch**

AWS Batch is a fully managed service for running batch computing workloads at scale. It automatically provisions the optimal quantity and type of compute resources based on the volume and requirements of submitted jobs. Batch dynamically schedules, queues, and executes jobs across AWS compute services, making it ideal for processing large volumes of data or running parallel workloads.

**Lightsail**

Amazon Lightsail is a simplified compute service designed for users who need straightforward virtual private servers. It offers an easy-to-use interface with pre-configured plans that include compute, storage, and networking at a predictable low monthly price. Lightsail is ideal for simple web applications, websites, development environments, and small-scale projects where ease of use is prioritized over complex configurations.

**Outposts**

AWS Outposts brings AWS infrastructure, services, and tools to your on-premises data center or co-location facility. It provides a fully managed service that extends AWS's cloud capabilities to your local environment, enabling a hybrid cloud architecture. Outposts is useful for workloads that require low latency, local data processing, or compliance with data residency requirements.