# Build Docker Image and Publish to Amazon ECR with GitHub Actions

![image](https://github.com/user-attachments/assets/845c425a-61d3-4631-9809-cfa365469e77)

1. **Create a Fork of the Application Repo**  
   Fork the repository and give it a relevant name.

2. **Update Your Repo with AWS Credentials**  
   Make sure your repository is configured with the appropriate AWS credentials.

3. **Create a Repository for Your Images in ECR**  

    Create an Amazon ECR repository using the AWS CLI from your AWS Academy or Cloud9 Terminal:

  ```bash
   $ aws ecr create-repository --repository-name github-actions-docker-publish
  ```
5. **Create GitHub Actions Workflow**

6. **Verify that the Docker Image is available in Registry**  
       _Verify in the registry._

7. **Run the container in Cloud9**

   - **Describe Repositories**
     ```bash
     $ aws ecr describe-repositories
     ```

   - **Export environment variable**
     ```bash
     $ export ECR={your repository uri}/github-actions-docker-publish
     ```

   - **Log into Docker registry to get permissions to pull an image**
     ```bash
     $ aws ecr get-login-password --region us-east-1 | docker login -u AWS ${ECR} --password-stdin
     ```

   - **Start the webserver**
     ```bash
     $ docker run -d -p 80:8080 {your repository uri}/github-actions-docker-publish:v0.1
     ```

   - **Verify that the application is running**
     ```bash
     $ curl localhost
     ```
