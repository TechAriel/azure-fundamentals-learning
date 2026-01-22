# Step-by-Step Implementation

## Creating a Virtual Machine

1. Signed into the Azure Portal.
2. Navigated to:
   - Create a resource → Compute → Virtual Machine
3. Configured the following:
   - Resource Group: IntroAzureRG
   - Virtual Machine Name: my-VM
   - Authentication Type: Password
   - Username: azureuser
   - Public Inbound Ports: None
4. Reviewed configuration and selected **Create**.
5. Waited for deployment to complete.

![Vm Created](01CreateAzureResource/screenshots
/VmCreated.png)

## Verifying Resources Created

1. Navigated to:
   - Home → Resource Groups → IntroAzureRG
2. Observed multiple resources created automatically, including:
   - Virtual Machine
   - Network Interface
   - Virtual Network
   - Network Security Group
   - Disk resources

## Cleanup

1. Deleted the resource group `IntroAzureRG`.
2. Confirmed deletion to avoid unnecessary costs.

## Lessons Learned
- Azure automatically provisions dependent resources.
- Resource Groups simplify management and cleanup.
- Deleting a resource group deletes all contained resources.

