# IBM Cloud Pak MQ module

Module to populate a gitops repository with the MQ operator from IBM Cloud Pak for Integration.

## Software dependencies

The module depends on the following software components:

### Command-line tools

- terraform - v15

### Terraform providers

None

## Module dependencies

This module makes use of the output from other modules:

- GitOps - github.com/cloud-native-toolkit/terraform-tools-gitops.git
- Catalogs - github.com/cloud-native-toolkit/terraform-gitops-cp-catalogs.git
- Plaform Navigator - github.com/cloud-native-toolkit/terraform-gitops-cp-platform-navigator.git

## Example usage

```hcl-terraform
module "mq" {
  source = "github.com/cloud-native-toolkit/terraform-gitops-cp-mq.git"

  gitops_config = module.gitops.gitops_config
  git_credentials = module.gitops.git_credentials
  server_name = module.gitops.server_name
  kubeseal_cert = module.argocd-bootstrap.sealed_secrets_cert
  catalog = module.cp_catalogs.catalog_ibmoperators
  platform_navigator_name = module.cp_platform_navigator.name
}
```







