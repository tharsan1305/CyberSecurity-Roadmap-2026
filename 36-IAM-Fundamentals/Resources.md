# Day 36 - Resources

## Tools Used
- AWS IAM Console, AWS CLI

## Commands Reference
| Purpose | Command |
|---|---|
| Create user | `aws iam create-user --user-name <name>` |
| Create group | `aws iam create-group --group-name <name>` |
| Attach managed policy to group | `aws iam attach-group-policy --group-name <name> --policy-arn <arn>` |
| Add user to group | `aws iam add-user-to-group --user-name <user> --group-name <group>` |
| Create custom policy | `aws iam create-policy --policy-name <name> --policy-document file://policy.json` |
| Attach policy to user | `aws iam attach-user-policy --user-name <user> --policy-arn <arn>` |

## Key Terms Glossary
- **ARN**: Amazon Resource Name, unique identifier for AWS resources
- **Managed Policy**: reusable, AWS or customer-created policy
- **Inline Policy**: policy embedded directly in a single identity, not reusable
- **Assume Role**: the act of temporarily taking on a Role's permissions

## Further Reading
- AWS IAM official documentation and best practices guide
- AWS IAM Policy Simulator (test policies before applying)

## Skills Gained Today
- IAM Users, Groups, Roles creation and management
- Custom IAM Policy JSON writing
- EC2 instance role configuration
- Permission enforcement verification
