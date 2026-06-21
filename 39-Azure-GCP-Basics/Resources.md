# Day 39 - Resources

## Tools Used
- Azure Portal, Azure CLI (`az`)
- Google Cloud Console, gcloud CLI

## Commands Reference
| Purpose | Azure CLI | gcloud CLI |
|---|---|---|
| List VMs | `az vm list --output table` | `gcloud compute instances list` |
| Stop VM | `az vm stop --name <vm> --resource-group <rg>` | `gcloud compute instances stop <name>` |
| List storage | `az storage account list` | `gcloud storage buckets list` |

## Service Mapping Quick Reference
| Function | AWS | Azure | GCP |
|---|---|---|---|
| Compute | EC2 | Virtual Machines | Compute Engine |
| Object Storage | S3 | Blob Storage | Cloud Storage |
| IAM | IAM | Entra ID | Cloud IAM |
| Networking | VPC | VNet | VPC |
| Serverless | Lambda | Azure Functions | Cloud Functions |
| Managed DB | RDS | Azure SQL Database | Cloud SQL |

## Further Reading
- Microsoft Learn: Azure Fundamentals (free, AZ-900 aligned)
- Google Cloud Skills Boost: free introductory labs

## Skills Gained Today
- Multi-cloud service mapping (AWS to Azure to GCP)
- Hands-on exposure to Azure Portal and GCP Console
- Cross-cloud CLI tool familiarity
