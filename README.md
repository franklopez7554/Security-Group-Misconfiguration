# Security-Group-Misconfiguration

 https://www.loom.com/share/d5481ae3c6bd448cbc06a26f35a44496?sid=3cb068c7-29fc-4000-bc2a-3468c8e5a260

### Objective

This SOP outlines the steps to simulate and resolve remote desktop connection issues on an AWS EC2 Windows instance using Security Group settings and PowerShell.

### Key Steps

 

**1. Initial Connection Test** [0:00](https://loom.com/share/d5481ae3c6bd448cbc06a26f35a44496?t=0)

![generated-image-at-00:00:00](https://loom.com/i/1781be269b8c4409bac1c30f54524f89?workflows_screenshot=true)

- Begin by attempting to connect to your AWS EC2 Windows instance.
- Retrieve the password for the instance to ensure you can log in.

 

**2. Access Security Group Settings** [0:46](https://loom.com/share/d5481ae3c6bd448cbc06a26f35a44496?t=46)

![generated-image-at-00:00:46](https://loom.com/i/ca27dbbfcf4347d9bf9100b084c9ecfa?workflows_screenshot=true)

- Navigate to the AWS Management Console.
- Go to the 'Security Groups' section.
- Select the relevant security group associated with your EC2 instance.

 

**3. Edit Inbound Rules** [1:00](https://loom.com/share/d5481ae3c6bd448cbc06a26f35a44496?t=60)

![generated-image-at-00:01:00](https://loom.com/i/ece2df8c6c3f46abb8fea4d1c2fd7006?workflows_screenshot=true)

- Click on 'Edit inbound rules'.
- Identify the RDP (Remote Desktop Protocol) rule in the list.

 

**4. Remove RDP Rule** [1:13](https://loom.com/share/d5481ae3c6bd448cbc06a26f35a44496?t=73)

![generated-image-at-00:01:13](https://loom.com/i/af01605e4a3344b2937155f1deaa67a1?workflows_screenshot=true)

- Delete the existing RDP rule.
- Save the changes to the inbound rules.

 

**5. Attempt Connection Again** [1:44](https://loom.com/share/d5481ae3c6bd448cbc06a26f35a44496?t=104)

![generated-image-at-00:01:44](https://loom.com/i/8fd508b2a06b4d07b15e00395b7eb605?workflows_screenshot=true)

- Go back to your EC2 instance and try to connect again.
- Note the error message indicating that the remote desktop cannot connect.

 

**6. Test Connection with PowerShell** [2:00](https://loom.com/share/d5481ae3c6bd448cbc06a26f35a44496?t=120)

![generated-image-at-00:02:00](https://loom.com/i/63fc893d15b0439ba809f76421fd5304?workflows_screenshot=true)

- Open Windows PowerShell.
- Use the command `Test-NetConnection` followed by the instance's IP address and port 3389 to check connectivity.

 

**7. Analyze Connection Status** [2:56](https://loom.com/share/d5481ae3c6bd448cbc06a26f35a44496?t=176)

![generated-image-at-00:02:56](https://loom.com/i/1e284d33eadd4a079ac12d738c12eff8?workflows_screenshot=true)

- Review the output from PowerShell.
- If the status shows 'Timed Out', it confirms that RDP is not accessible.

 

**8. Re-add RDP Rule** [3:07](https://loom.com/share/d5481ae3c6bd448cbc06a26f35a44496?t=187)

![generated-image-at-00:03:07](https://loom.com/i/754780d786d64c59bd8c3f63e4504257?workflows_screenshot=true)

- Return to the security group settings.
- Click on 'Edit inbound rules' again.
- Add a new rule for RDP using your IP address.

 

**9. Save Changes and Connect** [3:24](https://loom.com/share/d5481ae3c6bd448cbc06a26f35a44496?t=204)

![generated-image-at-00:03:24](https://loom.com/i/0340b62805f047cb87b93f1c77fa2454?workflows_screenshot=true)

- Save the updated inbound rules.
- Go back to your EC2 instance and attempt to connect once more.

 

**10. Retrieve Password and Access Desktop** [3:37](https://loom.com/share/d5481ae3c6bd448cbc06a26f35a44496?t=217)

![generated-image-at-00:03:37](https://loom.com/i/5223fe93acc243a1a00b7d5e6e58484d?workflows_screenshot=true)

- Download the RDP profile if prompted.
- Enter the password to access your remote desktop.

### Cautionary Notes

- Ensure that your IP address is correctly configured in the inbound rules to avoid connection issues.
- Be cautious when modifying security group settings, as incorrect configurations can lead to security vulnerabilities.

### Tips for Efficiency

- Always keep a backup of your security group settings before making changes.
- Use a script to automate the testing of connectivity if you frequently encounter this issue.
