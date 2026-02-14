# Azure Resource Locks - Infrastructure Governance

## Overview

This project demonstrates the implementation of Azure Resource Manager (ARM) locks to protect infrastructure resources from accidental modification or deletion.

The lab focuses on governance enforcement within Microsoft Azure and highlights the difference between management plane and data plane operations.

---

## Architecture Components

- Resource Group: IntroAzureRG
- Azure Storage Account (Standard LRS)
- Blob Container
- Resource Locks:
  - Read-only
  - Delete

---

## Objectives

- Implement resource-level governance controls
- Understand how Azure enforces management-plane locks
- Observe the behavioral differences between Read-only and Delete locks
- Practice safe infrastructure teardown

---

## Key Engineering Insights

- Resource locks override RBAC permissions.
- Read-only locks block all write operations at the management layer.
- Delete locks allow modification but prevent resource deletion.
- Locks are evaluated by Azure Resource Manager before destructive operations execute.

---

## Documentation

See `steps.md` for full technical breakdown.

Screenshots are available in the `screenshots/` directory.

