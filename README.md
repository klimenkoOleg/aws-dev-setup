# aws-dev-setup
This is a set of commands to organazi dev environemnt in AWS: create Kubernetes EKS, other resources, deploy to EKS, etc.


$ Prerequisites

1. Install kubectl command line tool: https://docs.aws.amazon.com/eks/latest/userguide/install-kubectl.html
2. Install eksctl tool, instatuctions are here: https://docs.aws.amazon.com/eks/latest/userguide/eksctl.html
3. Install AWS CLI: https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-getting-started.html
4. Login to AWS:
aws configure
└─[$] <> aws configure --profile dev-aws set region us-west-11
└─[$] <> aws configure --profile myprofile set aws_access_key_id <access_key>
└─[$] <> aws configure --profile myprofile set aws_secret_access_key <secret_access_key>
└─[$] <> aws configure list-profiles


aws sts get-caller-identity




6a. EITHER Create EKS cluster by runnin commands from your local computer:
```
eksctl create cluster \
--name dev-env \
--region us-west-1 \
--node-type t2.small \
--nodes 2
```
6b. OR grab existing configuration:
```
aws eks update-kubeconfig --region us-east-1 --name dev-eks
```


7. Check is we can connect to AWS Kubernetese: 
```
kubectl get nodes --kubeconfig ~/.kube/config
```

8. 


Useful AWS commands:
* aws configure get region - get current region
* 

esctl:
*  eksctl delete cluster --name microservices --region eu-central-1 - remove a cluster

Useful kubectl commands:
* 


Push Docker image to AWS ECR repo:
aws ecr create-repository --repository-name microservice-fake-api
docker image ls fake-api
```
REPOSITORY   TAG       IMAGE ID       CREATED          SIZE
fake-api     latest    557cfe2072f6   29 minutes ago   439MB
```
docker tag  557cfe2072f6 839112409020.dkr.ecr.us-west-1.amazonaws.com/microservice-fate-api:1.0.0
aws ecr get-login-password | docker login --username AWS --password-stdin  839112409020.dkr.ecr.us-west-1.amazonaws.com/microservice-fate-api
docker push 839112409020.dkr.ecr.us-west-1.amazonaws.com/microservice-fate-api:1.0.0

kubectl run fake-api-5 --image=839112409020.dkr.ecr.us-west-1.amazonaws.com/microservice-fate-api:1.0.0 --port=8080 

kubectl port-forward pods/fake-api-5  8888:8080

http://localhost:8888/shop/campaigns.json


kubectl exec --stdin --tty krakend-deployment-5755f5dd4d-4kqs2 -- sh





