# Help Desk Access Troubleshooting Lab

**Scenario:** A domain user was unable to access a shared folder on the Windows Server. I reproduced the access issue, verified network connectivity and the affected user account, investigated the user's Active Directory group membership, identified the root cause, corrected the issue, and verified that access was restored.

## 1. Reproduce the Shared Folder Access Issue

I attempted to access the `HelpDeskShare` network share from the Windows 11 client while logged in as the affected user. Windows returned an access denied message, confirming the reported issue.


<img width="1168" height="880" alt="01-shared-folder-access-denied png" src="https://github.com/user-attachments/assets/ef8d9a02-e9c2-4ca2-9652-71fa05987551" />


## 2. Verify Connectivity and User Account

I verified that the Windows Server was reachable using `ping` and used `whoami` to confirm that I was troubleshooting the correct domain user session. This helped rule out a basic network connectivity problem before investigating permissions.


<img width="646" height="623" alt="02-connectivity-and-user-verified-annotated" src="https://github.com/user-attachments/assets/1dd5c192-a221-4ca8-82a0-0fef93b9600c" />


## 3. Identify the Root Cause

I reviewed the user's Active Directory group membership and discovered that Sarah was missing from the **Help Desk Users** security group required for access to the shared folder.


<img width="1046" height="1024" alt="03-missing-group-membership png" src="https://github.com/user-attachments/assets/65bb124e-6bb9-4f14-a955-170757d3e2f0" />


## 4. Restore and Verify Access

I restored Sarah's membership in the required security group and refreshed the user session. I then accessed the shared folder and successfully modified a file through the network share, confirming that access had been restored.


<img width="1430" height="1100" alt="04-shared-folder-access-restored png" src="https://github.com/user-attachments/assets/dc5bd9c5-e85b-487d-a28d-54e594310997" />


**Tools used:** Active Directory Users and Computers • File Explorer • Command Prompt • `ping` • `whoami` • Windows Server • Windows 11 • SMB File Sharing

**Result:** Successfully diagnosed a shared folder access issue, ruled out basic network connectivity, identified missing Active Directory group membership as the root cause, restored the user's access, and verified successful access to the network share.

## What I Learned

I learned how Active Directory security group membership can control access to shared resources and how a missing group membership can appear to the user as a permissions problem.

This lab also reinforced the importance of troubleshooting systematically instead of immediately changing permissions. By first verifying connectivity and the affected user account, I was able to narrow the issue down before investigating Active Directory and correcting the root cause.

**Reproduce → Verify Connectivity → Confirm User → Investigate Access → Correct → Verify**
