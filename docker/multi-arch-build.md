```
export AWS_ACCESS_KEY_ID=
export AWS_SECRET_ACCESS_KEY=

Login to AWS ECR

docker buildx build --no-cache --push --platform linux/amd64,linux/arm64 --tag USERNAME/IMAGE_NAME:TAG .
```
Reference: 
1. [How to Rapidly Build Multi-Architecture Images with Buildx](https://www.docker.com/blog/how-to-rapidly-build-multi-architecture-images-with-buildx/#:~:text=Building%20Multi%2DArchitecture%20Images%20with,manifest%20list%20to%20Docker%20Hub.)
2. [Environment variables to configure the AWS CLI](https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-envvars.html)
