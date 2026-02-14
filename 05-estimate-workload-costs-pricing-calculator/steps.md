# Step-by-Step Implementation

## 1. Define Workload Requirements

The workload includes:

- Internal ASP.NET web application
- 2 Windows Virtual Machines
- Azure Application Gateway for load balancing
- Azure SQL Database
- 730 hours/month uptime
- 1 TB monthly data processing
- 32 GB database storage
- Moderate compute requirements

---

## 2. Open Azure Pricing Calculator

1. Navigated to the Azure Pricing Calculator.
2. Cleared any existing estimates.

---

## 3. Add Required Services

Selected the following services:

- Compute → Virtual Machines
- Databases → Azure SQL Database
- Networking → Application Gateway

---

## 4. Configure Virtual Machines

Configured:

- Region: West US
- OS: Windows
- Instance: D2 v3
- Quantity: 2
- Usage: 730 hours/month

This represents two always-on production VMs.

---

## 5. Configure Azure SQL Database

Configured:

- Region: West US
- Type: Single Database
- Purchase Model: vCore
- Service Tier: General Purpose
- Compute Tier: Provisioned
- Instance: 8 vCore
- Backup Storage: RA-GRS

This configuration supports moderate production workloads.

---

## 6. Configure Application Gateway

Configured:

- Region: West US
- Tier: Web Application Firewall
- Size: Medium
- Gateway Hours: 2 x 730
- Data Processed: 1 TB
- Outbound Data: 5 GB

This provides secure load balancing and traffic management.

---

## Step 7: Review Estimated Costs

Reviewed:

- Monthly cost breakdown
- Cost contribution per service
- Currency adjustments
- Export and share options

---

## Lessons Learned

- Always-on workloads significantly impact monthly pricing.
- Regional selection influences pricing.
- Database and Compute tier/series selection affects cost-performance balance.
- Cloud cost estimation is critical before production deployment.

