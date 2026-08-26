# Lab Walkthrough

## Objective
Create a basic segmented cloud network and add audit logging so the environment demonstrates both network control and security visibility.

## Build sequence
1. Create the VPC with 10.0.0.0/16.
2. Create a public subnet with 10.0.1.0/24.
3. Create a private subnet with 10.0.2.0/24.
4. Attach an Internet Gateway.
5. Build a public route table and send 0.0.0.0/0 to the Internet Gateway.
6. Create a NAT Gateway in the public path.
7. Build a private route table and send 0.0.0.0/0 to the NAT Gateway.
8. Confirm the VPC resource map reflects the intended topology.
9. Enable CloudTrail and deliver logs to S3.
10. Verify CloudTrail log objects arrive in the S3 log path.
11. Redact account-specific identifiers before publishing evidence.

## Why this matters
Cloud security requires both prevention and visibility. Segmentation helps limit exposure, while logging gives defenders evidence of activity that can support troubleshooting, auditing, and incident response.
