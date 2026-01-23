# Step-by-Step Implementation

## Attempting to Access the Web Server
This is to show why things didn't work at first
1. Retrieved the public IP address of the virtual machine and stored it in a Bash variable:

```bash
IPADDRESS="$(az vm list-ip-addresses \
  --resource-group "IntroAzureRG" \
  --name my-vm \
  --query "[].virtualMachine.network.publicIpAddresses[*].ipAddress" \
  --output tsv)"
```
2. Attempting to access web server using `curl`

```
curl --connect-timeout 5 http://$IPADDRESS
```

3. The request timed out, confirming that the VM was not accessible over HTTP.


## Reviewing Existing Netwok Security Group Rules
1. Listed the Network Security Groups associated with the VM:
```bash
az network nsg list \
  --resource-group "IntroAzureRG" \
  --query '[].name' \
  --output tsv
```

2. Identified the NSG automatically created by Azure:
```bash
my-vmNSG
```

3. Listed existing NSG rules in a readable format:
```bash
az network nsg rule list \
  --resource-group "IntroAzureRG" \
  --nsg-name my-vmNSG \
  --query '[].{Name:name, Priority:priority, Port:destinationPortRange, Access:access}' \
  --output table
```

4. Observed the only SSH(port 22) was allowed by default

## Creating an Inbound HTTP Rule
1. Created a new NSG rule to allow inbound HTTP traffic on port 80:
```bash
az network nsg rule create \
  --resource-group "IntroAzureRG" \
  --nsg-name my-vmNSG \
  --name allow-http \
  --protocol tcp \
  --priority 100 \
  --destination-port-range 80 \
  --access Allow
```

2. Verified that the rule was added successfully:
```bash
az network nsg rule list \
  --resource-group "IntroAzureRG" \
  --nsg-name my-vmNSG \
  --query '[].{Name:name, Priority:priority, Port:destinationPortRange, Access:access}' \
  --output table
```

## Accessing the Web Server Successfully
1. Retried the `curl` command after NSG rule propagation:
```bash
curl --connect-timeout 5 http://$IPADDRESS
```

2. Retrieved the expected HTML response from the Nginx web server:
```html
<html><body><h2>Welcome to Azure! My name is my-vm.</h2></body></html>
```

3. Verified access through a web browser using the VM's public IP address.



## Cleanup
To avoid unnecessary costs, deleted the resource group and all associated resources.

## Lessons Learned
- NSGs control inbound and outbound network traffic in Azure.
- By default, Linux VMs only allow SSH access.
- Rule priority determines which traffic is evaluated first.
- Network changes may take time to propagate.
