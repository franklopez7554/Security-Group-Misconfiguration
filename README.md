# Security-Group-Misconfiguration

 https://www.loom.com/share/d5481ae3c6bd448cbc06a26f35a44496?sid=3cb068c7-29fc-4000-bc2a-3468c8e5a260

### Objective

This SOP outlines the steps to simulate and resolve remote desktop connection issues on an AWS EC2 Windows instance using Security Group settings and PowerShell.

### Key Steps

 

**1. Initial Connection Test** [0:00](https://loom.com/share/d5481ae3c6bd448cbc06a26f35a44496?t=0)

![image](https://github.com/franklopez7554/Security-Group-Misconfiguration/blob/main/Screenshot%202025-07-23%20143212.png)
- Begin by attempting to connect to your AWS EC2 Windows instance.
- Retrieve the password for the instance to ensure you can log in.

 

**2. Access Security Group Settings** [0:46](https://loom.com/share/d5481ae3c6bd448cbc06a26f35a44496?t=46)

![image](https://github.com/franklopez7554/Security-Group-Misconfiguration/blob/main/Screenshot%202025-07-23%20143233.png)

- Navigate to the AWS Management Console.
- Go to the 'Security Groups' section.
- Select the relevant security group associated with your EC2 instance.

 

**3. Edit Inbound Rules** [1:00](https://loom.com/share/d5481ae3c6bd448cbc06a26f35a44496?t=60)

![image](https://github.com/franklopez7554/Security-Group-Misconfiguration/blob/main/Screenshot%202025-07-23%20143252.png)

- Click on 'Edit inbound rules'.
- Identify the RDP (Remote Desktop Protocol) rule in the list.

 

**4. Remove RDP Rule** [1:13](https://loom.com/share/d5481ae3c6bd448cbc06a26f35a44496?t=73)

![image](https://github.com/franklopez7554/Security-Group-Misconfiguration/blob/main/Screenshot%202025-07-23%20143320.png)

- Delete the existing RDP rule.
- Save the changes to the inbound rules.

 

**5. Attempt Connection Again** [1:44](https://loom.com/share/d5481ae3c6bd448cbc06a26f35a44496?t=104)

![image](https://github.com/franklopez7554/Security-Group-Misconfiguration/blob/main/Screenshot%202025-07-23%20143320.png)

- Go back to your EC2 instance and try to connect again.
- Note the error message indicating that the remote desktop cannot connect.

 

**6. Test Connection with PowerShell** [2:00](https://loom.com/share/d5481ae3c6bd448cbc06a26f35a44496?t=120)

![image](https://github.com/franklopez7554/Security-Group-Misconfiguration/blob/main/Screenshot%202025-07-23%20143446.png)

- Open Windows PowerShell.
- Use the command `Test-NetConnection` followed by the instance's IP address and port 3389 to check connectivity.

 

**7. Analyze Connection Status** [2:56](https://loom.com/share/d5481ae3c6bd448cbc06a26f35a44496?t=176)

![image](https://github.com/franklopez7554/Security-Group-Misconfiguration/blob/main/Screenshot%202025-07-23%20144159.png)

- Review the output from PowerShell.
- If the status shows 'Timed Out', it confirms that RDP is not accessible.

 

**8. Re-add RDP Rule** [3:07](https://loom.com/share/d5481ae3c6bd448cbc06a26f35a44496?t=187)

![image](https://github.com/franklopez7554/Security-Group-Misconfiguration/blob/main/Screenshot%202025-07-23%20144230.png)
- Return to the security group settings.
- Click on 'Edit inbound rules' again.
- Add a new rule for RDP using your IP address.

 

**9. Save Changes and Connect** [3:24](https://loom.com/share/d5481ae3c6bd448cbc06a26f35a44496?t=204)

![image](https://github.com/franklopez7554/Security-Group-Misconfiguration/blob/main/Screenshot%202025-07-23%20144239.png)

- Save the updated inbound rules.
- Go back to your EC2 instance and attempt to connect once more.

 

**10. Retrieve Password and Access Desktop** [3:37](https://loom.com/share/d5481ae3c6bd448cbc06a26f35a44496?t=217)

![image](https://github.com/franklopez7554/Security-Group-Misconfiguration/blob/main/Screenshot%202025-07-23%20144301.png)

- Download the RDP profile if prompted.
- Enter the password to access your remote desktop.

### Cautionary Notes

- Ensure that your IP address is correctly configured in the inbound rules to avoid connection issues.
- Be cautious when modifying security group settings, as incorrect configurations can lead to security vulnerabilities.

### Tips for Efficiency

- Always keep a backup of your security group settings before making changes.
- Use a script to automate the testing of connectivity if you frequently encounter this issue.
