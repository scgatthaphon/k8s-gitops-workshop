# ecr

## Setup

Change directory first.

```bash
cd ecr
```

Create a new pulumi stack.

```bash
pulumi stack init k8s-gitops-workshop-ecr-dev
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
pulumi stack select k8s-gitops-workshop-ecr-dev

# provision resources from IaC
pulumi up
```