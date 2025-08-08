# aws-redteam-lab
 Hands-on AWS Cloud Red Teaming Lab – 48-day journey simulating real-world attacks like IAM misconfigurations, S3 exploitation, Lambda privilege escalation, and more. Built with CLI, Pacu, and custom tools.


This lab simulates an AWS attack chain in an isolated test environment for educational and defensive research purposes only. It follows the flow: IAM credential compromise → enumeration → privilege escalation → new credentials → S3 data exfiltration. No production systems or third-party resources were accessed.

Environment Setup: AWS Account ID: 1233-9911-****. Profiles Configured:

admin-user (compromised IAM user)

escalated-user (privileged IAM user created during simulation)

AWS Region(s): us-east-1.

CLI version: aws-cli/2.15.x.

Tools used: AWS CLI, Pacu.

Safety & Ethics

All activities were executed in an AWS account of own.
No production data or live customer environments were accessed.
All access keys and IAM users created in this lab were deleted immediately after testing.
CloudTrail logging was enabled for the entire duration of the lab.
Steps for running the attack chain:

Configured all the details into the CLI.
Enabled AWS CloudTrail in all regions, logging to dedicated S3 bucket (log-bucket-).
Enabled S3 server access logging for target bucket (target-bucket-).
Created a low-privilege IAM user ("admin-user") with simulated compromised keys.
Installed and configured Pacu.
Confirmed AWS CLI profiles in ~/.aws/config and ~/.aws/credentials.
