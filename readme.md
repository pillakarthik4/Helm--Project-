how to automate the build and deployment of Springboot Microservices Docker Container into Elastic Kubernetes Cluster(EKS) using Helm and Jenkins pipeline.

Jenkins pipeline will:
- Automate maven build(jar) using Jenkins
- Automate Docker image creation
- Automate Docker image upload into Elastic container registry(ECR)
- Automate Springboot docker container deployments into Elastic Kubernetes Cluster using Helm charts
- Automate the SonarQube for static code analysis

Pre-requisites:
1. EKS cluster needs to be up running. Click here to learn how to create Amazon EKS cluster.
https://www.coachdevops.com/2022/02/c...
2. Jenkins instance is up and running
3. Install AWS CLI on Jenkins instance
4. Helm installed on Jenkins instance
5. Install Kubectl on Jenkins instance
6. Install eksctl on Jenkins instance
7. Install Docker in Jenkins and Jenkins have proper permission to perform Docker builds
8. Make sure to Install Docker, Docker pipeline 
9. Create ECR repo in AWS
10. Dockerfile created along with the application source code for springboot App.
11. Namespace created in EKS cluster
12. Created SonarQube instance for static code analysis and integrated with Jenkins with required plugins.
    
![Screenshot (19)](https://github.com/pillakarthik4/Microservice-Deploy-using-Helm/assets/130967802/19fddbf5-ad4e-45c0-914d-46c98f6839d1)



#Jenkins Pipeline successfully completed


![Screenshot (18)](https://github.com/pillakarthik4/Microservice-Deploy-using-Helm/assets/130967802/a26fead5-07eb-4873-ab71-b6859df90059)


