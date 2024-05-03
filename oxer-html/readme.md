Steps to run Docker container locally:
-pull the image from github
-write the docker file.
-build a docker image.
-run the image locally.

How to trigger a cicd pipeline:
we can trigger a cicd pipeline through github webhook and setting up jenkins git poll scm.

Run the deployment script in cloud ecs service:
Step 1: Pull Docker Image from Docker Hub
docker pull bhimkumar/css-project

Step 2: Update ECS Task Definition
aws ecs register-task-definition --cli-input-json file:my-task-definition.json

Step 3: Update ECS Service
aws ecs update-service --cluster my-ecs-cluster --service my-ecs-service --my-definition my-task-family:my-task-revision

step 4: Configure a Load Balancer
step 5: Register ECS Tasks with the Target Group
Step 6: Configure Security Groups
Step 7: Access Your Application
