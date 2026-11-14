# AWS-01 — Infrastructure & IAM

**Project:** INFO 4110 Serverless Log Analysis  
**Status:** Permissions configured; runtime evidence and CloudWatch confirmation pending

## Objective
Configure least-privilege AWS Lambda access to read project security logs from S3, publish alerts through SNS, and write execution logs to CloudWatch.

## Resources
| Resource | Value |
|---|---|
| Region | ca-central-1 (Canada Central) |
| IAM role | `info4110-lambda-execution-roles` |
| Base policy | `AWSLambdaBasicExecutionRole` |
| Custom policy | `INFO4110-Lambda-S3-SNS-Policy` |
| S3 bucket | `info4110-security-logs-3478a78dgds` |
| SNS topic | `info4110-security-alerts` (Standard) |
| Test function | `info4110-iam-test` |
| Test object | `testing AWS.txt` |

## IAM design
Trust principal: `lambda.amazonaws.com`. Attached base policy enables CloudWatch Logs writes. Custom policy restricts operations to:
- `s3:GetObject` → `arn:aws:s3:::info4110-security-logs-3478a78dgds/*`
- `sns:Publish` → `arn:aws:sns:ca-central-1:[AWS_ACCOUNT_ID]:info4110-security-alerts`

The custom policy uses the real account ID; it is redacted here for sharing. No broad administrative policies are needed.

## Validation
| Test | Result | Evidence |
|---|---|---|
| Lambda role assignment | Confirmed | Screenshot pending insertion |
| Both IAM policies attached | Confirmed | Screenshot captured |
| S3 test file upload | Succeeded, 78 B | Screenshot captured |
| Manual SNS email | Received | Email confirmation |
| Lambda S3 read and SNS publish | User reported success; retain test output | Pending screenshot |
| CloudWatch execution logs | Not yet confirmed | Pending screenshot |

**Evidence distinction:** A manually published SNS email tests the subscription, not Lambda's `sns:Publish` permission. Retain Lambda output for the latter claim.

## Remaining before closing AWS-01
1. Save Lambda output showing S3 read and SNS publish success.
2. Verify corresponding CloudWatch execution logs.
3. Insert or link evidence in the GitHub issue and final report.
4. Remove only temporary test resources after teammates confirm they are unneeded.

## Final-report paragraph
For the infrastructure and identity-access-management phase, the team configured a dedicated AWS Lambda execution role in the ca-central-1 region. The role combines AWS-managed CloudWatch logging permissions with a custom least-privilege policy that permits `s3:GetObject` on the project security-log bucket and `sns:Publish` on the designated alert topic. A temporary Lambda function was used to validate the intended service integration with a non-sensitive S3 test object. The SNS topic and its email subscription were also tested successfully. Final verification evidence, including the Lambda execution output and corresponding CloudWatch logs, is retained as part of the project test record once captured.

## Implementation Evidence
- TBD

