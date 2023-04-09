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

