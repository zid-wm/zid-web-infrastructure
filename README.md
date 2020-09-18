# vZID Web Infrastructure
This repository contains descriptor files for AWS backend services configured for the vZID ARTCC website. Also included are bash files to assist in deploying stacks from a local machine.

## AWS CloudFormation
These infrastructure files are written using AWS CloudFormation template formats (written in YAML). Information about the CloudFormation syntax and its features can be found [here](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/Welcome.html).

## Deploying Stacks from Local Machine
_Note: Unless otherwise specified, all commands are run from the root project directory._
1. Ensure you have the [AWS CLI](https://aws.amazon.com/cli/) installed on your local machine. Before using the AWS CLI for the first time, you must add your credentials and configuration settings by running `aws configure`.
2. The automated `create` and `destroy` scripts are written for Bash (and similar) terminals. If you are using Windows, I recommend downloading one of many free versions of Bash available. Otherwise, you will have to find documentation on deploying CloudFormation stacks manually.
3. Ensure the automated scripts are executable by running:
```
chmod +x create destroy
```
4. To deploy a new stack, run `./create`. You will be prompted for a development environment. If the script is successful, a file will be created in the project directory containing the RSA private key for connecting to the created EC2 instance. **Do not commit this file to any version control.**
5. To destroy an old stack, run `./destroy`. You will be prompted for a development environment. Ensure that the development environment you provide is the same as you used for provisioning the new stack. Your file containing the RSA private key for the given environment will be deleted.