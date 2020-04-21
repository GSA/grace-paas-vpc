# <a name="top">GRACE PaaS VPC</a>

The GRACE PaaS VPC module creates the the network resources required for a basic GRACE PaaS account.

## Table of Contents

- [Repository contents](#repository-contents)
- [Usage](#usage)
- [Terraform Module Inputs](#terraform-module-inputs)
- [Terraform Module Outputs](#terraform-module-outputs)

[top](#top)

## Repository contents

- **main.tf** contains the data resource for the Transit Gateway RAM shared resource
- **vpc.tf** contains the resource for the Front, Mid, and Back VPCs, peering connections, and transit gateway connections
- **route.tf** contains the route tables and route resources
- **subnet.tf** contains the subnets for the VPCs
- **variables.tf** contains all configurable variables
- **outputs.tf** contains all Terraform output variables

[top](#top)

# Usage

Simply import grace-paas-vpc as a module into your Terraform for the destination AWS Environment.

```
module "paas" {
    source                    = "github.com/GSA/grace-paas-vpc?ref=v0.0.1"
    cloudtrail_log_group_name = "<log_group_name>"
    recipient                 = "<email_address>"
}
```

[top](#top)

## Terraform Module Inputs

| Name | Description | Type | Default | Required |
|------|-------------|------|---------|:--------:|
| availability\_zones | (required) List of availaibility zones for VPC subnets | `list(string)` | n/a | yes |
| tgw\_name | (required) Name of the Transit Gateway | `string` | n/a | yes |
| vpc\_cidrblocks | (required) List of VPC CIDR blocks, must be three | `list(string)` | n/a | yes |

## Requirements

No requirements.

## Providers

| Name | Version |
|------|---------|
| aws | n/a |

[top](#top)

## Terraform Module Outputs

| Name | Description |
|------|-------------|
| back\_rt\_id | Back VPC route table ID |
| back\_vpc\_cidr | Back VPC CIDR block |
| back\_vpc\_id | Back VPC ID |
| back\_vpc\_subnet\_cidr\_blocks | Back VPC subnet CIDR blocks |
| back\_vpc\_subnet\_ids | Back VPC subnet IDs |
| front\_mid\_peering\_connection\_id | Front to mid VPC peering connection ID |
| front\_rt\_id | Front VPC route table ID |
| front\_vpc\_cidr | Front VPC CIDR block |
| front\_vpc\_id | Front VPC ID |
| front\_vpc\_subnet\_cidr\_blocks | Front VPC subnet CIDR blocks |
| front\_vpc\_subnet\_ids | Front VPC subnet IDs |
| mid\_back\_peering\_connection\_id | Mid to back VPC peering connection ID |
| mid\_rt\_id | Mid VPC route table ID |
| mid\_vpc\_cidr | Mid VPC CIDR block |
| mid\_vpc\_id | Mid VPC ID |
| mid\_vpc\_subnet\_cidr\_blocks | Mid VPC subnet CIDR blocks |
| mid\_vpc\_subnet\_ids | Mid VPC subnet IDs |

[top](#top)

## Public domain

This project is in the worldwide [public domain](LICENSE.md). As stated in [CONTRIBUTING](CONTRIBUTING.md):

> This project is in the public domain within the United States, and copyright and related rights in the work worldwide are waived through the [CC0 1.0 Universal public domain dedication](https://creativecommons.org/publicdomain/zero/1.0/).
>
> All contributions to this project will be released under the CC0 dedication. By submitting a pull request, you are agreeing to comply with this waiver of copyright interest.

[top](#top)
