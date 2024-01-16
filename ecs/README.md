# Pre-Requisites 
* Install aws-cli
* Install aws session-manager-plugin

# Create Cluster
> aws ecs create-cluster --cluster-name fargate-cluster

# Create Task Defination File

# Register Task Defination
> aws ecs register-task-definition --cli-input-json file://$PWD/fargate-task.json

# Create a Service (with ecs exec)
> aws ecs create-service --cluster fargate-cluster --service-name fargate-service --task-definition sample-fargate:4 --desired-count 1 --launch-type "FARGATE" --network-configuration "awsvpcConfiguration={subnets=[subnet-0d842e249a77afe0a],securityGroups=[sg-01ed4054c2a19ea6e]}" --enable-execute-command

# Exec into ECS Task
> aws ecs execute-command --cluster fargate-cluster --task e864a193ecf442909051207b5ce28e3f --container fargate-app --interactive --command "/bin/sh"

# Clean up
> aws ecs delete-service --cluster fargate-cluster --service fargate-service --force

> aws ecs delete-cluster --cluster fargate-cluster

