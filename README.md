[![GitHub release (latest by date)](https://img.shields.io/github/v/release/native-cube/terraform-aws-eks-fargate-profile)](https://github.com/native-cube/terraform-aws-eks-fargate-profile/releases/latest)

# terraform-aws-eks-fargate-profile
Terraform module to configure an Fargate Profile on AWS EKS

## Usage

```hcl
module "eks-fargate-profile" {
  source  = "native-cube/eks-fargate-profile/aws"
  version = "~> 1.0.1"

  cluster_name = "eks-native-cube"
  subnet_ids   = ["subnet-037c37205ce1cd88c", "subnet-0bb4e7a5c3120bc47", "subnet-07a58a249f38a1f58"]

  namespace = "kube-system"
  labels = {
    infrastructure = "fargate"
  }

  tags = {
    Environment = "test"
  }
}
```

## Examples

* [ESK Fargate Profile](https://github.com/native-cube/terraform-aws-eks-fargate-profile/tree/main/examples/core)


<!-- BEGINNING OF PRE-COMMIT-TERRAFORM DOCS HOOK -->
## Requirements

| Name | Version |
|------|---------|
| <a name="requirement_terraform"></a> [terraform](#requirement\_terraform) | >= 1.0.0 |
| <a name="requirement_aws"></a> [aws](#requirement\_aws) | >= 3.38 |

## Providers

| Name | Version |
|------|---------|
| <a name="provider_aws"></a> [aws](#provider\_aws) | >= 3.38 |

## Modules

No modules.

## Resources

| Name | Type |
|------|------|
| [aws_eks_fargate_profile.main](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/eks_fargate_profile) | resource |
| [aws_iam_role.main](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/iam_role) | resource |
| [aws_iam_role_policy_attachment.main](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/iam_role_policy_attachment) | resource |

## Inputs

| Name | Description | Type | Default | Required |
|------|-------------|------|---------|:--------:|
| <a name="input_cluster_name"></a> [cluster\_name](#input\_cluster\_name) | The name of the EKS cluster | `string` | n/a | yes |
| <a name="input_description"></a> [description](#input\_description) | The description of the IAM Role used by fargate profile. | `string` | `"EKS cluster fargate profile IAM role."` | no |
| <a name="input_fargate_profile_name"></a> [fargate\_profile\_name](#input\_fargate\_profile\_name) | Name of the EKS Fargate Profile. If not provided, profile will be called `fargate-profile-namespace_name`. | `string` | `null` | no |
| <a name="input_labels"></a> [labels](#input\_labels) | Key-value mapping of Kubernetes labels for selection | `map(string)` | `null` | no |
| <a name="input_namespace"></a> [namespace](#input\_namespace) | Kubernetes namespace for which fargate profile will be used. | `string` | n/a | yes |
| <a name="input_subnet_ids"></a> [subnet\_ids](#input\_subnet\_ids) | Identifiers of private EC2 Subnets to associate with the EKS Fargate Profile. These subnets must have the following resource tag: kubernetes.io/cluster/cluster\_name. | `list(string)` | n/a | yes |
| <a name="input_tags"></a> [tags](#input\_tags) | Mapping of additional tags. | `map(string)` | `{}` | no |

## Outputs

| Name | Description |
|------|-------------|
| <a name="output_eks_fargate_profile_arn"></a> [eks\_fargate\_profile\_arn](#output\_eks\_fargate\_profile\_arn) | ARN of the EKS Fargate Profile |
| <a name="output_eks_fargate_profile_id"></a> [eks\_fargate\_profile\_id](#output\_eks\_fargate\_profile\_id) | EKS Cluster name and EKS Fargate Profile name separated by a colon |
| <a name="output_eks_fargate_profile_role_arn"></a> [eks\_fargate\_profile\_role\_arn](#output\_eks\_fargate\_profile\_role\_arn) | ARN of the EKS Fargate Profile IAM role |
| <a name="output_eks_fargate_profile_role_name"></a> [eks\_fargate\_profile\_role\_name](#output\_eks\_fargate\_profile\_role\_name) | Name of the EKS Fargate Profile IAM role |
| <a name="output_eks_fargate_profile_status"></a> [eks\_fargate\_profile\_status](#output\_eks\_fargate\_profile\_status) | Status of the EKS Fargate Profile |
<!-- END OF PRE-COMMIT-TERRAFORM DOCS HOOK -->

## License

See LICENSE for full details.

## Pre-commit hooks

### Install dependencies

* [`pre-commit`](https://pre-commit.com/#install)
* [`terraform-docs`](https://github.com/segmentio/terraform-docs) required for `terraform_docs` hooks.
* [`TFLint`](https://github.com/terraform-linters/tflint) required for `terraform_tflint` hook.

#### MacOS

```bash
brew install pre-commit terraform-docs tflint

brew tap git-chglog/git-chglog
brew install git-chglog
```
