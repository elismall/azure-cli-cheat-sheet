
# Azure CLI Cheat Sheet

This is a concise reference for Azure CLI shortcut flags and commonly used commands.

---

## 🔹 Azure CLI Common Shortcut Flags

### General Flags
```
-g                # --resource-group
-n                # --name
-l                # --location
-o                # --output
-y                # --yes (auto-confirm prompts)
-d                # --debug (prints debug logs)
--ids             # Use full resource ID instead of name + group
```

---

## 🔹 VM Management
```
--image              # Defines OS image (e.g., Ubuntu2204, Win2019Datacenter)
--size               # Defines VM size (e.g., Standard_DS1_v2)
--admin-username     # Login name for VM
--generate-ssh-keys  # Auto-creates SSH key if not present
--authentication-type # Specify 'password' or 'ssh'
```

---

## 🔹 Network / VNet
```
--subnet             # Specify subnet name
--vnet-name          # Name of virtual network
--address-prefixes   # IP range for the VNet or subnet
--subnet-prefix      # IP range for subnet only
```

---

## 🔹 Storage
```
--sku                # Storage account type (e.g., Standard_LRS)
--kind               # Storage type (e.g., StorageV2, BlobStorage)
--access-tier        # Hot or Cool for blob storage
--https-only         # Forces HTTPS access
```

---

## 🔹 Role Assignment / Identity
```
--assignee           # User or app to assign a role to
--role               # Role name (Reader, Contributor, Owner)
--scope              # The target (subscription, resource group, resource)
```

---

## 🔹 Output Formatting
```
-o table             # Human-readable table view
-o json              # Default (structured)
-o yaml              # YAML output
--query              # Filter output using JMESPath
```

### Example:
```
az vm list -g MyRG -o table --query "[].{Name:name, Location:location}"
```

---

## 🔹 Useful Global Flags
```
--only-show-errors   # Hides warnings and only shows errors
--no-wait            # Launches a job but doesn’t wait for it to finish
--debug              # Full debug log
--verbose            # More detail about what's happening
```
