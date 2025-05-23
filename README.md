# Azure CLI Cheat Sheet

This repository contains a concise, developer-friendly reference for Azure CLI commands and shortcut flags. It's designed to help streamline your daily workflows when provisioning, managing, and troubleshooting Azure resources via the command line.

---

# 🚩 Common Shortcut Flags
- `-g` = `--resource-group`
- `-n` = `--name`
- `-l` = `--location`
- `-o` = `--output`
- `-y` = `--yes` (auto-confirm prompts)
- `-d` = `--debug` (prints debug logs)
- `--ids` = Use full resource ID instead of name + group

# 🌍 Resource Creation Command Hiearchy Example

## Resource Group
```
az group create -n MyRG -l eastus
```

## Virtual Network
```
az network vnet create -g MyRG -n MyVNet --address-prefixes 10.0.0.0/16
```

## Subnet
```
az network vnet subnet create -g MyRG --vnet-name MyVNet -n MySubnet --address-prefix 10.0.0.0/24
```

## Network Interface
```
az network nic create -g MyRG -n MyNIC --vnet-name MyVNet --subnet MySubnet
```

## Virtual Machine
```
az vm create -g MyRG -n MyVM --image Ubuntu2204 --nics MyNIC --admin-username azureuser --generate-ssh-keys
```

## Storage Account
```
az storage account create -n mystorageacct -g MyRG -l eastus --sku Standard_LRS --kind StorageV2
```

## Role Assignment
```
az role assignment create --assignee user@example.com --role Contributor --scope /subscriptions/xxxx/resourceGroups/MyRG
```
## Delete Resource
```
az resource delete --ids /subscriptions/.../resourceGroups/MyRG/providers/Microsoft.Compute/virtualMachines/MyVM
```

# 🖥️ VM Management Options
- `--image` — Defines OS image (e.g., `Ubuntu2204`, `Win2019Datacenter`)
- `--size` — VM size (e.g., `Standard_DS1_v2`)
- `--admin-username` — Username for login
- `--generate-ssh-keys` — Auto-creates SSH key if missing
- `--authentication-type` — Use `'password'` or `'ssh'`

# 📡 Network / VNet
- `--subnet` — Subnet name  
- `--vnet-name` — Virtual network name  
- `--address-prefixes` — IP range for the VNet or subnet  
- `--subnet-prefix` — IP range for the subnet only  

# 📦 Storage
- `--sku` — Storage account SKU (e.g., `Standard_LRS`)
- `--kind` — Storage type (e.g., `StorageV2`)
- `--access-tier` — Blob storage tier: `Hot` or `Cool`
- `--https-only` — Enforce HTTPS access only

# 👤 Role Assignment / Identity
- `--assignee` — Target user or service principal
- `--role` — Role name (e.g., `Reader`, `Contributor`, `Owner`)
- `--scope` — Scope of access (resource, resource group, or subscription)

# 📝 Output Formatting
- `-o table` — Human-readable table output
- `-o json` — Default structured JSON output
- `-o yaml` — YAML format output
- `--query` — Filter output using JMESPath syntax
### Example:
```
az vm list -g MyRG -o table --query "[].{Name:name, Location:location}"
```

# 🌐 Global Flags

- `--only-show-errors` — Suppress warnings; only show errors
- `--no-wait` — Run command asynchronously without waiting for completion
- `--debug` — Display full debug output
- `--verbose` — Show more detailed output for troubleshooting




