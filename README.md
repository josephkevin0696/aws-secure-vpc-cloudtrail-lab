# AWS Secure VPC + CloudTrail Logging Lab

Hands-on AWS networking and security lab that builds a segmented VPC, separates public and private subnets, routes Internet-bound traffic appropriately, and stores AWS CloudTrail logs in Amazon S3.

> **Portfolio note:** This is a training/lab environment. AWS account identifiers and directly identifying console details were redacted from the screenshots before publication.

## Architecture

Internet
→ Internet Gateway
→ Public Route Table (0.0.0.0/0 → IGW)
→ Public Subnet: 10.0.1.0/24
→ NAT Gateway
→ Private Route Table (0.0.0.0/0 → NAT Gateway)
→ Private Subnet: 10.0.2.0/24

VPC CIDR: 10.0.0.0/16

AWS API activity
→ CloudTrail
→ S3 log storage

## What I built

- AWS VPC using 10.0.0.0/16.
- Public subnet using 10.0.1.0/24.
- Private subnet using 10.0.2.0/24.
- Internet Gateway attached to the VPC.
- Public route table with an Internet default route through the Internet Gateway.
- NAT Gateway for outbound Internet access from the private subnet path.
- Private route table with 0.0.0.0/0 directed to the NAT Gateway.
- CloudTrail log delivery to an S3 bucket for audit visibility and incident-readiness practice.

## Evidence

### Public subnet
![Public subnet](evidence/01-public-subnet.jpg)

### Internet Gateway
![Internet Gateway attached to VPC](evidence/02-internet-gateway-attached.jpg)

### Public route
![Public route table default route to Internet Gateway](evidence/03-public-route-to-igw.jpg)

### NAT Gateway
![NAT Gateway](evidence/04-nat-gateway.jpg)

### Private route
![Private route table default route to NAT Gateway](evidence/05-private-route-to-nat.jpg)

### VPC resource map
![VPC resource map](evidence/06-vpc-resource-map.jpg)

### CloudTrail log delivery
![CloudTrail log objects in S3](evidence/07-cloudtrail-logs-in-s3.jpg)

## Security concepts demonstrated

- **Network segmentation:** separate public and private subnets.
- **Controlled Internet routing:** public subnet uses an Internet Gateway; private subnet uses NAT for outbound access.
- **Reduced direct exposure:** the private subnet does not need a direct Internet Gateway route.
- **Audit logging:** CloudTrail records AWS API activity.
- **Centralized log storage:** S3 provides durable storage for CloudTrail log objects.
- **Evidence hygiene:** public portfolio images are sanitized before publication.

## Validation checklist

- [x] VPC uses 10.0.0.0/16.
- [x] Public subnet uses 10.0.1.0/24.
- [x] Private subnet uses 10.0.2.0/24.
- [x] Internet Gateway is attached to the VPC.
- [x] Public route table has 0.0.0.0/0 to the Internet Gateway.
- [x] Private route table has 0.0.0.0/0 to the NAT Gateway.
- [x] VPC resource map shows separate public/private paths.
- [x] CloudTrail log objects are present in S3.

## Skills demonstrated

AWS VPC · Subnets · Route Tables · Internet Gateway · NAT Gateway · CloudTrail · Amazon S3 · Cloud Security · Network Segmentation · Audit Logging

## Scope and limitations

This repository documents a lab build and does not claim production cloud administration. It focuses on core VPC segmentation, route design, and logging. It does not represent a complete production landing zone, multi-account architecture, high-availability NAT design, or enterprise SIEM integration.
