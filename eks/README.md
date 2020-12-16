# eks

## Setup

Change directory first.

```bash
cd eks
```

Create a new pulumi stack.

```bash
pulumi stack init k8s-gitops-workshop-eks-dev
# enter passphrase
```

Configure the stack.

```bash
pulumi config set aws:region ap-southeast-1
pulumi config set aws:profile k8s-gitops-workshop

# For example:
#   FULL_NAME=jakpat-mingmongkolmitr
FULL_NAME=<REPLACE YOUR FULL NAME>
pulumi config set postfix $FULL_NAME
```

## Provision

Provision cluster IaC via Pulumi CLI.

```bash
# select the certain stack
pulumi stack select k8s-gitops-workshop-eks-dev

# provision resources from IaC
pulumi up

# get the cluster name
CLUSTER_NAME=$(pulumi stack output clusterName)
# update cluster config to kubectl
aws eks update-kubeconfig --profile k8s-gitops-workshop --name "${CLUSTER_NAME}"
```
