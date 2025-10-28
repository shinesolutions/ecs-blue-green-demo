# ecs-blue-green-demo
Demo to illustrate native blue-green deployments in ECS.

[AWS blog post announcement](https://aws.amazon.com/blogs/aws/accelerate-safe-software-releases-with-new-built-in-blue-green-deployments-in-amazon-ecs/)

[Cluster architecture and sample CF template](https://containersonaws.com/pattern/public-facing-web-ecs-fargate-cloudformation)
[Simple VPC (public subnets only) CF template](https://containersonaws.com/pattern/low-cost-vpc-amazon-ecs-cluster)

needs [SAM CLI](https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/install-sam-cli.html)

[Target group listener rule info](https://edwardpoot.com/posts/aws-ecs-blue-green-deployments/)

[Sample stack with manual approval step and gradual traffic movement from blue to green](https://github.com/aws-samples/sample-amazon-ecs-blue-green-deployment-patterns/blob/main/ecs-bluegreen-lifecycle-hooks/README.md)