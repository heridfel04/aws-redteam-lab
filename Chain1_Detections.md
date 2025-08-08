# Chain 1: Detection Queries for AWS Attack Steps

**1. IAM Credentials**

   *Action:* Attacker uses compromised IAM credentials via aws configure --profile attacker.

   *Detection:*

   SELECT eventTime, eventName, userIdentity, sourceIPAddress

   FROM cloudtrail_logs

   WHERE eventSource = 'iam.amazonaws.com' 

   AND eventName IN ('AssumeRole', 'GetSessionToken', 'GetCallerIdentity') 

   AND userIdentity.type = 'IAMUser';

**2. Recon & Enumeration**

   *Action:* Attacker lists IAM users and S3 buckets using commands like aws iam list-users and aws s3 ls.

   *Detection:*

   SELECT eventTime, eventName, userIdentity, sourceIPAddress

   FROM cloudtrail_logs

   WHERE eventSource = 'iam.amazonaws.com' AND eventName = 'ListUsers';

   SELECT eventTime, eventName, userIdentity, sourceIPAddress

   FROM cloudtrail_logs

   WHERE eventSource = 's3.amazonaws.com' AND eventName = 'ListBucket';

**3. Privilege Escalation**

   *Action:* Attacker escalates privileges using iam:CreateUser and iam:AttachUserPolicy.

   *Detection:*

   SELECT eventTime, eventName, userIdentity, requestParameters

   FROM cloudtrail_logs

   WHERE eventSource = 'iam.amazonaws.com' AND eventName IN ('CreateUser', 'AttachUserPolicy');

**4. New Access & Role Assumption**

  *Action:* Attacker creates new access keys and assumes roles.

  *Detection:* 

  SELECT eventTime, eventName, userIdentity, requestParameters

  FROM cloudtrail_logs

  WHERE eventSource = 'iam.amazonaws.com' AND eventName = 'CreateAccessKey';

**5. S3 Data Exfiltration**

   *Action:* Attacker exfiltrates data using aws s3 ls.

   *Detection:*

   SELECT eventTime, eventName, userIdentity, requestParameters

   FROM cloudtrail_logs

   WHERE eventSource = 's3.amazonaws.com' AND eventName = 'CopyObject';


#Notes:
- Monitor CloudTrail, GuardDuty, and S3 logs to detect and respond to these attacks quickly.
- Regular audits and alerts for suspicious activities like privilege escalation and data exfiltration will improve security.



