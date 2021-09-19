<!-- BEGIN_TF_DOCS -->
[![Tests](https://github.com/netascode/terraform-aci-snmp-trap/actions/workflows/test.yml/badge.svg)](https://github.com/netascode/terraform-aci-snmp-trap/actions/workflows/test.yml)

# Terraform ACI SNMP Trap Module

Manages ACI SNMP Trap

Location in GUI:
`Admin` » `External Data Collectors` » `Monitoring Destinations` » `SNMP`

## Examples

```hcl
module "aci_snmp_trap" {
  source  = "netascode/snmp-trap/aci"
  version = ">= 0.0.1"

  name        = "TRAP1"
  description = "My Description"
  destinations = [{
    hostname_ip   = "1.1.1.1"
    port          = 1162
    community     = "COM1"
    security      = "priv"
    version       = "v3"
    mgmt_epg      = "oob"
    mgmt_epg_name = "OOB1"
  }]
}

```

## Requirements

| Name | Version |
|------|---------|
| <a name="requirement_terraform"></a> [terraform](#requirement\_terraform) | >= 1.0.0 |
| <a name="requirement_aci"></a> [aci](#requirement\_aci) | >= 0.2.0 |

## Providers

| Name | Version |
|------|---------|
| <a name="provider_aci"></a> [aci](#provider\_aci) | >= 0.2.0 |

## Inputs

| Name | Description | Type | Default | Required |
|------|-------------|------|---------|:--------:|
| <a name="input_name"></a> [name](#input\_name) | SNMP trap policy name. | `string` | n/a | yes |
| <a name="input_description"></a> [description](#input\_description) | Description. | `string` | `""` | no |
| <a name="input_destinations"></a> [destinations](#input\_destinations) | List of destinations. Allowed values `port`: 0-65535. Default value `port`: 162. Choices `security`: `noauth`, `auth`, `priv`. Default value `security`: `noauth`. Choices `version`: `v1`, `v2c`, `v3`. Default value `version`: `v2c`. Choices `mgmt_epg`: `inb`, `oob`. | <pre>list(object({<br>    hostname_ip   = string<br>    port          = optional(number)<br>    community     = string<br>    security      = optional(string)<br>    version       = optional(string)<br>    mgmt_epg      = optional(string)<br>    mgmt_epg_name = optional(string)<br>  }))</pre> | `[]` | no |

## Outputs

| Name | Description |
|------|-------------|
| <a name="output_dn"></a> [dn](#output\_dn) | Distinguished name of `snmpGroup` object. |
| <a name="output_name"></a> [name](#output\_name) | SNMP trap policy name. |

## Resources

| Name | Type |
|------|------|
| [aci_rest.fileRsARemoteHostToEpg](https://registry.terraform.io/providers/netascode/aci/latest/docs/resources/rest) | resource |
| [aci_rest.snmpGroup](https://registry.terraform.io/providers/netascode/aci/latest/docs/resources/rest) | resource |
| [aci_rest.snmpTrapDest](https://registry.terraform.io/providers/netascode/aci/latest/docs/resources/rest) | resource |
<!-- END_TF_DOCS -->