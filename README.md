## 部署
aws s3 mb s3://sam-z
sam build -t template.yaml
sam package --s3-bucket sam-z  --output-template-file package.yaml
sam deploy --template-file /Users/zxuejiao/Downloads/repos/sam-test/sam-app/package.yaml --stack-name sam-test --capabilities CAPABILITY_NAMED_IAM
aws s3 cp --recursive www/ s3://sam-s3-web-z
aws s3 cp --recursive www/ s3://sam-s3-web-z


## Clean Up
aws s3 rb s3://sam-s3-web-z --force 
aws s3 rb s3://sam-audios-z --force 
aws cloudformation delete-stack --stack-name sam-test
