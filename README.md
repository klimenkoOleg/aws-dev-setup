# aws-dev-setup
This is a set of commands to organazi dev environemnt in AWS: create Kubernetes EKS, other resources, deploy to EKS, etc.


$ Prerequisites

1. Install kubectl command line tool: https://docs.aws.amazon.com/eks/latest/userguide/install-kubectl.html
2. Install eksctl tool, instatuctions are here: https://docs.aws.amazon.com/eks/latest/userguide/eksctl.html
3. Create EKS cluster by runnin commands from your local computer:
```
eksctl create cluster \
--name dev-env \
--region us-west-1 \
--node-type t2.small \
--nodes 2
```

