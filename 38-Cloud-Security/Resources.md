# Day 38 - Resources

## Tools Used
- AWS CloudTrail, GuardDuty, KMS, S3 Block Public Access

## Commands Reference
| Purpose | Command |
|---|---|
| Create CloudTrail | `aws cloudtrail create-trail --name <name> --s3-bucket-name <bucket>` |
| Start logging | `aws cloudtrail start-logging --name <name>` |
| Enable GuardDuty | `aws guardduty create-detector --enable` |
| Apply S3 encryption | `aws s3api put-bucket-encryption --bucket <bucket> --server-side-encryption-configuration '{...}'` |
| Check S3 encryption | `aws s3api get-bucket-encryption --bucket <bucket>` |

## Key Terms Glossary
- **CloudTrail**: AWS API call audit logging service
- **GuardDuty**: AWS managed threat detection service
- **KMS**: Key Management Service, manages encryption keys
- **CSPM**: Cloud Security Posture Management (covered further Topic 40)

## Further Reading
- AWS CloudTrail and GuardDuty official documentation
- "S3 bucket breach" case studies (search recent real-world incidents for context - many public post-mortems exist)

## Skills Gained Today
- CloudTrail audit logging setup
- GuardDuty threat detection enablement
- S3 encryption configuration
- Public access auditing and prevention
