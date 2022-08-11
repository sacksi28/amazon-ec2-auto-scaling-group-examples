# Auto Scaling Group Predictive Scaling with Mixed Instance Policy Example

This example deploys two Auto Scaling groups within a new VPC. One of the Auto Scaling groups contains instances that host a simple web application behind an Application Load Balancer. The second Auto Scaling group contains instances that generate recurring load against the Application Load Balancer. This stack will launch billable resources, so please keep in mind that you will be charged for any usage. You can adjust the instance types and number of instances deployed via the stack's CloudFormation parameters to reduce costs as needed.

We recommend following [this blog post](https://aws.amazon.com/blogs/compute/creating-predictive-scaling-and-mixed-instance-policy-using-amazon-ec2-auto-scaling/) for an example walk-through using this stack with Predictve Scaling and Mixed Instance Policies.

## Getting Started

We recommend deploying the following [Example AWS Cloud9 Environment](/environment/README.md) to get started quickly with this example. Otherwise, you can attempt to run this example using your own environment with the following prerequisites installed.

### Prerequisites

* [AWS CLI](https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-install.html) installed and configured with Administrator credentials.

## Deployment Steps

Once you've deployed and accessed the [Example AWS Cloud9 Environment](/environment/README.md) execute the following steps from within the Example AWS Cloud9 Environment to deploy this example.

1. Change directories to this example.

```bash
cd ~/environment/amazon-ec2-auto-scaling-group-examples/features/predictive-scaling-mixed-instance-policy
```

2. Deploy the CloudFormation Stack. You will need to replace `REPLACE_THIS_WITH_YOUR_KEY_PAIR_NAME` with the name of an SSH key in the region you are deploying the example to.

```bash
aws cloudformation deploy \
    --template-file template.yaml \
    --stack-name preditive-scaling-with-mixed-instace-policy-example \
    --capabilities CAPABILITY_IAM \
    --parameter-overrides \
        ApplicationInstanceKeyPair=REPLACE_THIS_WITH_YOUR_KEY_PAIR_NAME \
        LoadInstanceKeyPair=REPLACE_THIS_WITH_YOUR_KEY_PAIR_NAME
```

## Clean Up

Delete the CloudFormation Stack

```bash
aws cloudformation delete-stack --stack-name preditive-scaling-with-mixed-instace-policy-example
```