Steps to run Docker container locally:
-pull the image from github
-write the docker file.
-build a docker image.
-run the image locally.

How to trigger a cicd pipeline:
we can trigger a cicd pipeline through github webhook and setting up jenkins git poll scm.

Run the deployment script in cloud ecs service:
# Login to Amazon ECR
aws ecr get-login-password --region your-aws-region | docker login --username AWS --password-stdin your-aws-account-id.dkr.ecr.your-aws-region.amazonaws.com

# Tag your Docker image
docker tag your-docker-image:tag your-aws-account-id.dkr.ecr.your-aws-region.amazonaws.com/your-docker-image:tag

# Push your Docker image to Amazon ECR
docker push your-aws-account-id.dkr.ecr.your-aws-region.amazonaws.com/your-docker-image:tag

Update ECS Task Definition with Docker Image
aws ecs register-task-definition --cli-input-json file://your-task-definition.json

Update ECS Service to use the new Task Definition
aws ecs update-service --cluster your-ecs-cluster --service your-ecs-service --task-definition your-task-family:your-task-revision
