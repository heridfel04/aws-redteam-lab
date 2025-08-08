This lab simulates an AWS attack chain in an isolated test environment for educational and defensive research purposes only. 
It follows the flow: IAM credential compromise → enumeration → privilege escalation → new credentials → S3 data exfiltration.
No production systems or third-party resources were accessed.

1) **Environment Setup:**
   *AWS Account ID:* 1233-9911-****.
   *Profiles Configured:*
   - admin-user (compromised IAM user)
   - escalated-user (privileged IAM user created during simulation)

     *AWS Region(s):* us-east-1.
     
     *CLI version:* aws-cli/2.15.x.
     
     *Tools used:* AWS CLI, Pacu.

2) **Safety & Ethics**
   - All activities were executed in an AWS account of own.
   - No production data or live customer environments were accessed.
   - All access keys and IAM users created in this lab were deleted immediately after testing.
   - CloudTrail logging was enabled for the entire duration of the lab.
  

 3) **Steps for running the attack chain:**
    - Configured all the details into the CLI.
    - Enabled AWS CloudTrail in all regions, logging to dedicated S3 bucket (log-bucket-<date>).
    - Enabled S3 server access logging for target bucket (target-bucket-<date>).
    - Created a low-privilege IAM user ("admin-user") with simulated compromised keys.
    - Installed and configured Pacu.
    - Confirmed AWS CLI profiles in `~/.aws/config` and `~/.aws/credentials`.

 4) **Lab Timeline**
   Start: 2025-08-08 14:15 IST  
   End:   2025-08-08 15:35 IST  
   Duration: ~80 minutes     



