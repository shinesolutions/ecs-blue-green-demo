# Blue/Green ECS Deployments

Amazon announced earlier this year that [ECS now supports Blue/Green deployments](https://aws.amazon.com/blogs/aws/accelerate-safe-software-releases-with-new-built-in-blue-green-deployments-in-amazon-ecs/) natively. Why is this a big deal?

## What is Blue/Green Deployment?

An application deployment typically involves stopping the currently running version of an application, updating the software, and then restarting the application. This means downtime, where the application is unavailable for a period of time. It also means that in the event that the new version doesn't work rolling back to the previous version will mean re-deploying the old version. There are ways to minimise this downtime and make rollbacks easier. You won't be surprised to learn that blue-green deployments are one of those ways.

In a blue-green deployment, the currently running application is deemed the "blue" version. The new version to be deployed is the "green" version. The green version is deployed into its own infrastructure, so that blue and green are running simultaneously. This allows the green version to be tested while production traffic is still being handled by the blue version. If testing succeeds, the traffic is pointed to the green version. The blue version is then shut down, and green becomes the new blue. If testing the green version fails, nothing needs to be done - the blue version is still serving traffic and nobody needs to know of the shameful green version debacle. Zero downtime, easy rollbacks. The downside is temporarily needing more resources and capacity while both versions are running.

In ECS, a deployment usually means a new version of a container used by a service or task. With a standard deployment, the old container is stopped and the new one started, with a period of interrupted service in between. In a blue/green deployment, both containers run for a period of time with AWS handling the movement of traffic from the blue to the green.

## Couldn't you already do this with CodeDeploy?
[AWS CodeDeploy](https://docs.aws.amazon.com/codedeploy/latest/userguide/welcome.html) does have the ability to perform blue/green deployments in ECS, and until recently was the only way supported by AWS.

## How to set it up in an existing ECS service

## Deployment hooks and how to do something a bit more complicated




[Cluster architecture and sample CF template](https://containersonaws.com/pattern/public-facing-web-ecs-fargate-cloudformation)
[Simple VPC (public subnets only) CF template](https://containersonaws.com/pattern/low-cost-vpc-amazon-ecs-cluster)

needs [SAM CLI](https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/install-sam-cli.html)

[Target group listener rule info](https://edwardpoot.com/posts/aws-ecs-blue-green-deployments/)

[Sample stack with manual approval step and gradual traffic movement from blue to green](https://github.com/aws-samples/sample-amazon-ecs-blue-green-deployment-patterns/blob/main/ecs-bluegreen-lifecycle-hooks/README.md)