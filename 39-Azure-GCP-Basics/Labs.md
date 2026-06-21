# Day 39 - Lab: Azure/GCP Free Tier Exploration

## Objective
Create free accounts on Azure and/or GCP and map their core services against what you already know from AWS.

## Task 1: Create Azure Free Account
1. Sign up at azure.microsoft.com/free
2. Explore the Azure Portal - locate Virtual Machines, Blob Storage, Entra ID

## Task 2: Create a Basic Azure VM (Free Tier eligible)
Portal: Create a Resource -> Virtual Machine -> B1s size (free tier eligible)
```bash
az vm list --output table
az vm stop --name <vm-name> --resource-group <rg-name>
```

## Task 3: Create GCP Free Account
1. Sign up at cloud.google.com/free
2. Explore Google Cloud Console - locate Compute Engine, Cloud Storage, IAM

## Task 4: Create a Basic GCP VM (Free Tier eligible)
Console: Compute Engine -> Create Instance -> e2-micro (free tier eligible)
```bash
gcloud compute instances list
gcloud compute instances stop <instance-name>
```

## Task 5: Build a Comparison Table
Fill in based on your hands-on exploration:

| Concept | AWS | Azure | GCP |
|---|---|---|---|
| Compute | EC2 | ? | ? |
| Storage | S3 | ? | ? |
| IAM | IAM | ? | ? |
| Console URL used | console.aws.amazon.com | ? | ? |

## Results
| Item | Value |
|---|---|
| Azure account created (Y/N) | |
| Azure VM created (Y/N) | |
| GCP account created (Y/N) | |
| GCP VM created (Y/N) | |
| Comparison table completed (Y/N) | |

## Cleanup
Stop/delete all VMs created in both Azure and GCP to avoid charges.

## Screenshots
```
![Azure Portal](Screenshots/azure-portal.png)
![GCP Console](Screenshots/gcp-console.png)
```

## Lab Summary
Note which provider's console felt most intuitive coming from AWS, and any naming differences that initially confused you.
