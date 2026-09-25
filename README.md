☁️ AWS Fundamentals — Day 2

Cornell Notes | Learning & Revision
Topic: AWS Fundamentals
Day: 2
Date: 26 September 2026
Learner: Rehmat Ullah

This repository contains my Day 2 AWS Fundamentals notes, covering AWS pricing models, cloud service models, AWS access methods, and Identity & Access Management (IAM).

The notes are organized for quick revision, practical understanding, and interview preparation.

📚 Topics Covered

OPEX vs CAPEX in AWS

IaaS, PaaS, and SaaS

AWS Console, CLI, and SDK

IAM Overview

IAM Policies

IAM Roles

IAM Identity Providers

1. 💰 OPEX vs CAPEX in AWS

OPEX — Operational Expense

OPEX refers to ongoing expenses required to operate services.

Key Characteristics

Pay-as-you-go pricing

Little or no upfront infrastructure cost

Pay only for what you use

Resources can scale up or down

Costs change according to usage

AWS Examples

Amazon EC2 On-Demand

Amazon S3

Amazon DynamoDB

AWS Lambda

Simple Example

Instead of purchasing a physical server, you can launch an EC2 instance and pay for the compute resources while you use them.

CAPEX — Capital Expense

CAPEX refers to spending money upfront to purchase long-term assets.

Key Characteristics

Large upfront investment

Infrastructure is purchased for long-term use

Potentially lower cost over a long period when utilization is predictable

Less flexible than pay-as-you-go resources

Capacity is planned in advance

AWS-Related Examples

Savings Plans

Reserved Instances for committed usage

Quick Comparison

OPEX

CAPEX

Pay for usage

Commit/invest upfront

Flexible

Less flexible

Low upfront cost

Higher upfront commitment

Good for changing workloads

Useful for predictable long-term workloads

Key Idea: OPEX focuses on flexibility and variable cost, while CAPEX focuses on long-term commitment and potential savings.

2. 🏗️ IaaS, PaaS, and SaaS

Cloud service models describe how much of the infrastructure AWS manages and how much the customer manages.

IaaS — Infrastructure as a Service

With IaaS, the customer gets infrastructure and manages a larger portion of the software stack.

Customer Typically Manages

Applications

Data

Runtime

Middleware

Operating system

AWS Manages

Physical infrastructure

Networking

Storage

Servers

Virtualization

AWS Examples

Amazon EC2

Amazon EBS

Amazon VPC

Control: High
Flexibility: High

PaaS — Platform as a Service

PaaS provides a managed platform so developers can focus more on their applications.

Customer Manages

Applications

Data

AWS Manages

Runtime

Middleware

Operating system

Servers

Storage

Networking

Infrastructure

AWS Examples

AWS Elastic Beanstalk

Amazon RDS

AWS App Runner

Control: Medium
Development: Faster

SaaS — Software as a Service

SaaS provides ready-to-use software where the provider manages almost everything.

Customer

Uses the software

Manages their own data and configuration where applicable

Provider

Manages infrastructure

Application

Runtime

Middleware

Operating system

Servers

Storage

Networking

Examples

Gmail

Salesforce

Microsoft 365

Remember:
IaaS → More control
PaaS → Balanced management
SaaS → Mostly managed for you

3. 🖥️ AWS Console, CLI, and SDK

AWS provides different ways to interact with its services.

AWS Management Console

A web-based graphical interface for managing AWS resources.

Best For

Beginners

Learning AWS

Exploring services

Manual operations

Visual configuration

AWS CLI — Command Line Interface

AWS CLI allows you to control AWS services using commands from a terminal.

Best For

Automation

DevOps

Scripting

Repeatable tasks

CI/CD workflows

Example

aws s3 ls

aws ec2 describe-instances

AWS SDK — Software Development Kit

AWS SDKs provide programming libraries that allow applications to interact with AWS services.

Supported Languages Include

Python

Java

JavaScript / TypeScript

.NET

Go

PHP

Ruby

Example — Python

import boto3

s3 = boto3.client("s3")
response = s3.list_buckets()

print(response)

Which One Should You Use?

Tool

Best Use

AWS Console

Learning & manual management

AWS CLI

Automation, DevOps & scripting

AWS SDK

Building applications that use AWS

4. 🔐 IAM — Identity and Access Management

AWS IAM is used to securely control who can access AWS resources and what actions they can perform.

Principle of Least Privilege

Give users, applications, and services only the permissions they actually need.

IAM is a Global AWS Service

IAM resources are not tied to a specific AWS Region.

Key IAM Components

Users — Individual identities

Groups — Collections of users

Roles — Identities that can be assumed temporarily

Policies — Permission documents

MFA — Multi-factor authentication

Identity Providers — External authentication systems

5. 📜 IAM Policies

An IAM policy is a JSON document that defines permissions.

Policies determine which actions are allowed or denied on AWS resources.

Policy Types

1. Managed Policies

Policies managed by AWS or created and managed by customers.

2. Inline Policies

Policies embedded directly into a specific user, group, or role.

3. Permissions Boundaries

Define the maximum permissions an identity-based policy can grant to a user or role.

4. Session Policies

Temporary permissions that can limit permissions during a session.

Basic Policy Structure

{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": "s3:ListBucket",
      "Resource": "arn:aws:s3:::my-bucket"
    }
  ]
}

Important Elements

Element

Purpose

Version

Policy language version

Statement

Contains permission statements

Effect

Allow or Deny

Action

AWS API action

Resource

Resource the action applies to

Permission Logic

Allow → Grants the specified permission

Explicit Deny → Overrides an Allow

Default → Access is denied unless permission is granted

Important: An explicit Deny takes precedence over an Allow.

6. 🎭 IAM Roles

An IAM Role is an identity that AWS services, applications, or trusted users can assume to obtain temporary permissions.

Key Characteristics

Designed for temporary access

Does not require long-term access keys for the role itself

Useful for AWS services and applications

Uses AWS STS to provide temporary credentials

Common Use Cases

EC2 → S3

An EC2 instance can assume a role that allows it to access an S3 bucket without storing permanent access keys on the server.

Lambda → CloudWatch

A Lambda function can assume a role that allows it to write logs to CloudWatch.

Cross-Account Access

A role can be used to provide controlled access between AWS accounts.

External Identity Federation

Users authenticated through an external identity provider can assume AWS roles.

How IAM Role Access Works

Trusted Entity
      │
      ▼
Assume IAM Role
      │
      ▼
AWS STS
      │
      ▼
Temporary Credentials
      │
      ▼
AWS Resources

Why Roles Are Important

Roles help reduce dependence on long-term credentials and support secure, temporary access.

7. 🌐 IAM Identity Providers

An Identity Provider (IdP) is an external system that authenticates users and can provide federated access to AWS.

Benefits

Centralized user management

Single Sign-On (SSO)

Easier onboarding and offboarding

Improved security

External identity federation

Common Identity Provider Technologies

AWS IAM Identity Center

AWS service for centralized workforce access and SSO across AWS accounts and applications.

SAML 2.0

Commonly used for enterprise federation.

Examples include:

Active Directory Federation Services (AD FS)

Okta

OpenID Connect (OIDC)

Used by modern identity platforms and applications.

Examples include:

Google

Auth0

Microsoft Entra ID

🧠 Quick Revision

AWS Pricing

OPEX
 └── Pay as you go
     ├── Flexible
     ├── Low upfront cost
     └── Usage-based

CAPEX
 └── Long-term commitment
     ├── Upfront/committed cost
     ├── Predictable usage
     └── Potential long-term savings

Cloud Service Models

IaaS → More customer control
PaaS → Shared responsibility
SaaS → Provider manages most of the stack

AWS Access Methods

Console → Learn & Manual Work
CLI     → Automation & DevOps
SDK     → Application Development

IAM

Users + Groups + Roles + Policies + MFA + Identity Providers
                         │
                         ▼
                 Secure AWS Access

📌 Key Takeaways

✅ Understand the difference between OPEX and CAPEX.

✅ Know the responsibilities in IaaS, PaaS, and SaaS.

✅ Use the AWS Console for visual/manual operations.

✅ Use the AWS CLI for automation and repeatable tasks.

✅ Use AWS SDKs to integrate AWS into applications.

✅ Follow the Principle of Least Privilege.

✅ Understand IAM Users, Groups, Roles, Policies, and Identity Providers.

✅ Prefer IAM Roles and temporary credentials where appropriate instead of embedding long-term credentials.

✅ Remember that an explicit Deny overrides an Allow.

✅ Understand how identity federation enables SSO and external authentication.

🎯 Interview / Viva Questions

1. What is OPEX?

OPEX is an operational spending model where costs are generally incurred as services are used.

2. What is CAPEX?

CAPEX is spending on long-term assets or committed capacity, generally involving upfront or long-term financial commitment.

3. What is the difference between IaaS, PaaS, and SaaS?

They represent different levels of management responsibility. IaaS gives the customer more infrastructure control, PaaS manages more of the platform, and SaaS provides ready-to-use software.

4. What is AWS CLI?

AWS CLI is a command-line tool used to manage AWS services through commands.

5. What is an AWS SDK?

An AWS SDK provides programming libraries that allow applications to interact with AWS services.

6. What is IAM?

IAM is AWS's service for managing identities and permissions.

7. What is the Principle of Least Privilege?

It means granting only the permissions required to perform a specific task.

8. What is an IAM Policy?

An IAM Policy is a JSON document that defines permissions.

9. What is an IAM Role?

An IAM Role is an identity that can be assumed to obtain temporary permissions.

10. Why are IAM Roles useful?

They allow applications, AWS services, and federated users to obtain temporary credentials without embedding long-term access keys.

11. What is an Identity Provider?

An Identity Provider authenticates users and can provide federated access to AWS.

12. What happens when an explicit Deny and Allow both apply?

The explicit Deny takes precedence.

🛠️ Practical AWS Commands

List S3 Buckets

aws s3 ls

Describe EC2 Instances

aws ec2 describe-instances

Configure AWS CLI

aws configure

Security Note: Never commit AWS access keys, secret keys, passwords, or other credentials to GitHub. Use IAM roles, environment variables, AWS credential profiles, or other appropriate credential-management mechanisms.

📈 Day 2 Learning Flow

AWS Pricing
     ↓
OPEX vs CAPEX
     ↓
Cloud Service Models
     ↓
IaaS → PaaS → SaaS
     ↓
AWS Console / CLI / SDK
     ↓
IAM Fundamentals
     ↓
Policies & Permissions
     ↓
IAM Roles
     ↓
Identity Providers & Federation

📂 Suggested Repository Structure

aws-fundamentals/
│
├── Day-01/
│   └── README.md
│
├── Day-02/
│   ├── README.md
│   └── notes/
│       └── cornell-notes.png
│
└── README.md

📝 Learning Goal

The goal of Day 2 is to build a strong foundation in AWS cost models, cloud service models, AWS management interfaces, and identity/security fundamentals before moving into deeper AWS services and hands-on cloud projects.

AWS Fundamentals — Day 2
Learn → Practice → Revise → Build ☁️
