# Starting React App
```sh
source ~/.bash_profile
npx create-react-app kio-sl-auction-places
```

# Amplify

## configure

- Just when is a new aws account
```sh
amplify configure
```


## init

```sh
amplify init
# Scanning for plugins...
# Plugin scan successful
# Note: It is recommended to run this command from the root of your app directory
# ? Enter a name for the project kioslauctionplaces
# ? Enter a name for the environment klaucplenv
# ? Choose your default editor: Visual Studio Code
# ? Choose the type of app that you're building javascript
# Please tell us about your project
# ? What javascript framework are you using react
# ? Source Directory Path:  src
# ? Distribution Directory Path: build
# ? Build Command:  npm run-script build
# ? Start Command: npm run-script start
# Using default provider  awscloudformation

# For more information on AWS Profiles, see:
# https://docs.aws.amazon.com/cli/latest/userguide/cli-multiple-profiles.html

# ? Do you want to use an AWS profile? Yes
# ? Please choose the profile you want to use kio-makersi-sl-lms
# Adding backend environment klaucplenv to AWS Amplify Console app: d2xjykbou5rjnv
# ⠸ Initializing project in the cloud...

# CREATE_IN_PROGRESS DeploymentBucket                             AWS::S3::Bucket            Wed Jul 21 2021 12:15:16 GMT-0500 (Colombia Standard Time) Resource creation Initiated
# CREATE_IN_PROGRESS UnauthRole                                   AWS::IAM::Role             Wed Jul 21 2021 12:15:16 GMT-0500 (Colombia Standard Time) Resource creation Initiated
# CREATE_IN_PROGRESS AuthRole                                     AWS::IAM::Role             Wed Jul 21 2021 12:15:16 GMT-0500 (Colombia Standard Time) Resource creation Initiated
# CREATE_IN_PROGRESS UnauthRole                                   AWS::IAM::Role             Wed Jul 21 2021 12:15:16 GMT-0500 (Colombia Standard Time)                            
# CREATE_IN_PROGRESS AuthRole                                     AWS::IAM::Role             Wed Jul 21 2021 12:15:15 GMT-0500 (Colombia Standard Time)                            
# CREATE_IN_PROGRESS DeploymentBucket                             AWS::S3::Bucket            Wed Jul 21 2021 12:15:15 GMT-0500 (Colombia Standard Time)                            
# CREATE_IN_PROGRESS amplify-kioslauctionplaces-klaucplenv-121507 AWS::CloudFormation::Stack Wed Jul 21 2021 12:15:11 GMT-0500 (Colombia Standard Time) User Initiated             
# ⠼ Initializing project in the cloud...

# CREATE_COMPLETE UnauthRole AWS::IAM::Role Wed Jul 21 2021 12:15:30 GMT-0500 (Colombia Standard Time) 
# CREATE_COMPLETE AuthRole   AWS::IAM::Role Wed Jul 21 2021 12:15:30 GMT-0500 (Colombia Standard Time) 
# ⠹ Initializing project in the cloud...

# CREATE_COMPLETE amplify-kioslauctionplaces-klaucplenv-121507 AWS::CloudFormation::Stack Wed Jul 21 2021 12:15:39 GMT-0500 (Colombia Standard Time) 
# CREATE_COMPLETE DeploymentBucket                             AWS::S3::Bucket            Wed Jul 21 2021 12:15:37 GMT-0500 (Colombia Standard Time) 
# ✔ Successfully created initial AWS cloud resources for deployments.
# ✔ Initialized provider successfully.
# Initialized your environment successfully.

# Your project has been successfully initialized and connected to the cloud!

# Some next steps:
# "amplify status" will show you what you've added already and if it's locally configured or deployed
# "amplify add <category>" will allow you to add features like user login or a backend API
# "amplify push" will build all your local backend resources and provision it in the cloud
# “amplify console” to open the Amplify Console and view your project status
# "amplify publish" will build all your local backend and frontend resources (if you have hosting category added) and provision it in the cloud

# Pro tip:
# Try "amplify add api" to create a backend API and then "amplify publish" to deploy everything

```

# Codecommit

[Create repo](https://docs.aws.amazon.com/cli/latest/reference/codecommit/create-repository.html)

```sh
nano ~/.aws/credentials
export PATH=~/Library/Python/3.8/bin:$PATH
# source ~/.bash_profile
# test
aws s3 ls --profile kio-makersi-sl-lms
export AWS_PROFILE=kio-makersi-sl-lms

# aws codecommit create-repository --repository-name MyDemoRepo --repository-description "My demonstration repository" --tags Team=Saanvi
aws codecommit create-repository --repository-name kio-sl-auction-places --repository-description "Kamay Serverless Auction Places" --tags Team=kio --region us-east-1 

```
## Result
```json
{
    "repositoryMetadata": {
        "accountId": "436023604714",
        "repositoryId": "945b7a78-fde9-4389-a557-0036f27326dc",
        "repositoryName": "kio-sl-auction-places",
        "repositoryDescription": "Kamay Serverless Auction Places",
        "lastModifiedDate": 1626887954.71,
        "creationDate": 1626887954.71,
        "cloneUrlHttp": "https://git-codecommit.us-east-1.amazonaws.com/v1/repos/kio-sl-auction-places",
        "cloneUrlSsh": "ssh://git-codecommit.us-east-1.amazonaws.com/v1/repos/kio-sl-auction-places",
        "Arn": "arn:aws:codecommit:us-east-1:436023604714:kio-sl-auction-places"
    }
}
```

# git

```sh
ssh-keygen
/Users/robin8a/.ssh/kio_sl_lms_rsa

cat ~/.ssh/kio_sl_lms_rsa.pub

```

## Configure AWS IAM user

![AWS Config](_images/aws_iam_ssh_config.png)

```sh
cd ~/.ssh
ls
nano config

# Add

# CodeCommit hosts
Host kio_sl_lms_rsa
   HostName git-codecommit.us-east-1.amazonaws.com
   User APKAWLBIIGXVPJ7NHOZ5
   IdentityFile ~/.ssh/kio_sl_lms_rsa

```

https://xiaolishen.medium.com/use-multiple-ssh-keys-for-different-github-accounts-on-the-same-computer-7d7103ca8693

```sh
git remote -v
git remote rm origin
git remote add origin ssh://kio_sl_lms_rsa/v1/repos/kio-sl-lms
git push
```