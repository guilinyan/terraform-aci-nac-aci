<!-- BEGIN_TF_DOCS -->
# AAEP Example

To run this example you need to execute:

```bash
$ terraform init
$ terraform plan
$ terraform apply
```

Note that this example will create resources. Resources can be destroyed with `terraform destroy`.

```hcl
module "aci_aaep" {
  source  = "netascode/nac-aci/aci//modules/terraform-aci-aaep"
  version = ">= 0.8.0"

  name               = "AAEP1"
  description        = "AAEP1 Description"
  infra_vlan         = 10
  physical_domains   = ["PD1"]
  routed_domains     = ["RD1"]
  vmware_vmm_domains = ["VMM1"]
  endpoint_groups = [{
    tenant               = "TF"
    application_profile  = "AP1"
    endpoint_group       = "EPG1"
    primary_vlan         = 10
    secondary_vlan       = 20
    mode                 = "untagged"
    deployment_immediacy = "immediate"
  }]
}
```
<!-- END_TF_DOCS -->