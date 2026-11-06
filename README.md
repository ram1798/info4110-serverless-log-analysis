# Automated Serverless Log Analysis & Security Alerting

**INFO 4110 – Cloud Computing**

## Project Overview

This project aims to develop an automated, serverless security log analysis system using Amazon Web Services (AWS). The system is designed to process uploaded security logs, identify suspicious activities using predefined detection rules, and notify administrators of potential security threats.

By using a serverless architecture, the system can process incoming logs without requiring the maintenance of dedicated physical servers.

## Project Objectives

- Automate the collection and processing of security logs.
- Detect suspicious activity through configurable rules.
- Generate security notifications for administrators.
- Explore event-driven cloud computing.
- Apply cloud security and access management principles.

## AWS Services

- **Amazon S3:** Stores uploaded security log files.
- **AWS Lambda:** Processes log files and applies detection rules.
- **Amazon SNS:** Publishes alerts when suspicious activity is detected.
- **Amazon CloudWatch:** Supports monitoring and troubleshooting of Lambda execution.

## Proposed Workflow

1. Security logs are uploaded to an Amazon S3 bucket.
2. An S3 object-created event invokes AWS Lambda.
3. Lambda retrieves and analyzes the uploaded logs.
4. The system evaluates events against predefined detection rules.
5. When suspicious activity is identified, Amazon SNS publishes a notification to subscribed administrators.

## Project Status

In development.

## Documentation

Architecture, setup instructions, testing procedures, and security considerations will be maintained in the `docs/` directory.
