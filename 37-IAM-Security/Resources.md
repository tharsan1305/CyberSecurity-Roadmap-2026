# Day 37 - Resources

## Tools Used
- AWS IAM Console, IAM Access Analyzer
- Virtual MFA app (Google Authenticator, Authy, etc.)

## Commands Reference
| Purpose | Command |
|---|---|
| Generate credential report | `aws iam generate-credential-report` |
| Retrieve credential report | `aws iam get-credential-report` |
| Enable MFA device | `aws iam enable-mfa-device --user-name <user> ...` |
| Simulate a policy | `aws iam simulate-principal-policy ...` |

## Key Terms Glossary
- **Least Privilege**: minimum necessary permissions principle
- **MFA**: Multi-Factor Authentication
- **Access Analyzer**: AWS tool identifying externally shared resources and generating least-privilege suggestions
- **Trust Policy**: defines who can assume an IAM Role (used in cross-account access)

## Further Reading
- AWS IAM Security Best Practices (official documentation)
- AWS re:Inforce conference talks on IAM (free on YouTube, real-world breach case studies)

## Skills Gained Today
- MFA enforcement (account-level and policy-level)
- Credential auditing practices
- Least-privilege policy refinement
- Cross-account access pattern understanding
