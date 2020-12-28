# vZID Web Infrastructure
This repository contains files necessary to deploy ZID networking and server infrastructure via AWS CloudFormation.

## AWS CloudFormation
These infrastructure files are written using AWS CloudFormation template formats (written in YAML). Information about the CloudFormation syntax and its features can be found [here](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/Welcome.html).

## Things to Note
- Ensure you have the [AWS CLI](https://aws.amazon.com/cli/) installed on your local machine. Before using the AWS CLI for the first time, you must add your credentials and configuration settings by running `aws configure`.
- Before running the script for the first time, ensure you have the required Python packages by running `python3 -m pip install -r requirements.txt`.
- The `infra` script found in the root directory will take care of provisioning, updating, and destroying CloudFormation stacks for you. 
    - Networking stacks should rarely need updated or re-provisioned; a new networking stack will include a new (blank) database and could cause any current data to be irreversibly lost. 
- The `config.yml` file should be updated with values found in the networking CloudFormation stack prior to deploying any web stack. These values are used to deploy stacks in the proper accounts and locations.

## Tooling Usage Guide
To use the script in this repository, run the following command in the terminal:
```bash
./infra {provision,update,destroy} <stack name> [--config-file FILE_PATH]
```
The first argument should be one of `provision`, `update`, or `destroy`. If updating an existing web stack, ensure the AWS networking settings in `config.yml` do not change from the existing stack.

`<stack-name>` must match the name of a top-level entry in the `config.yml` file. If you have changed the name of the configuration file or it is located in a different directory than the root, you must specify the relative or absolute path by using the `--config-file` flag.
