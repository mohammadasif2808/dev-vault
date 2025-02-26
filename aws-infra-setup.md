![aws-infra-1](/images/infra1.jpg)
1. install aws cli
2. create aws access key
3. use "aws configure" command to set access key on local
4. to create s3 bucket "s3 mb s3://springboot-jar-bucket-02-25 --profile default"
5. to upload jar in s3 bucket "aws s3 cp project-one-springboot-app-0.0.1-SNAPSHOT.jar s3://springboot-jar-bucket-02-25 --profile default"
6. "aws cloudformation create-stack --stack-name my-spring-app --template-body file://spring-boot-stack.yml --capabilities CAPABILITY_NAMED_IAM --profile default"
7. "aws ec2 create-key-pair --key-name my-key-pair --query 'KeyMaterial' --output text > my-key-pair.pem --profile default"
8. "aws cloudformation update-stack --stack-name my-spring-app --template-body file://spring-boot-stack.yml --capabilities CAPABILITY_NAMED_IAM  --profile default"
9. "aws ec2 describe-instances --query 'Reservations[*].Instances[*].[InstanceId, PublicIpAddress]' --output table" to get the public ip of running ec2 instance for doing ssh.
