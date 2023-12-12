### Steps to Create Resource Group (RG1) and Two Virtual Machines (VM1 and VM2) in Azure and How to Edit the Network and Sharing Settings to Allow for Filesharing Between the Virtual Machines

1. **Create Resource Group (RG1):**
   - Navigate to the Azure Portal.
   - In the left sidebar, click on "Resource groups" and then "Add."
   - Provide the name as RG1, select a region, and complete the creation process.
<img src="https://i.imgur.com/gT3hdwS.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

2. **Create Virtual Machine (VM1) in RG1:**
   - In the RG1, click on "Add" and search for "Virtual machine."
   - Fill in details for VM1 (e.g., Windows 10, 2 vCPUs, 16 GiB Memory), create a username and password.
   - Note the Network Name as VM1-vnet.
   - Complete the creation and wait for deployment.
<img src="https://i.imgur.com/VBoa0lN.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

3. **Access VM1 Using RDP:**
   - Obtain the public IP of VM1 from the Azure Portal.
   - Open Remote Desktop, paste VM1's IP, and log in with the provided credentials.
   - Complete the setup to access the desktop.
<img src="https://i.imgur.com/vKLNO17.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>


4. **Create Test Folder and Document on VM1:**
   - Open File Explorer and go to documents.
   - Create a new folder named "TEST FOLDER."
   - Inside "TEST FOLDER," create a new text document called "TEST DOC."
   - Type something in the document and save.
<img src="https://i.imgur.com/1jatCSz.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/uOrFAO2.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/Gu3gQ49.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

5. **Adjust Sharing Settings on VM1:**
   - Right-click on "TEST FOLDER" in documents, click properties.
   - Click Advanced Sharing, check the share box, and click apply.
   - Note the file pathway (e.g., "\\VM1\TEST FOLDER").
<img src="https://i.imgur.com/BeeA9lO.png" height="30%" width="30%" alt="Disk Sanitization Steps"/>


6. **Change Firewall Settings and Create Inbound Rules on VM1:**
   - Open Windows Firewall, allow file and printer sharing over the network.
   - In "Allow an app or feature through Windows Defender Firewall," ensure "File and Printer Sharing" is enabled for both "Private" and "Public."
   - In advanced settings, create new inbound rules.
   - Rule 1: Port, TCP, Type 445. Name: Allow NetBIOs Inbound
   - Rule 2: Port, UDP, Type 137-138. Name: Allow SMB Inbound
<img src="https://i.imgur.com/upenZp9.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/USHUBjb.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/SrTdYnN.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/30fQt7c.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>


7. **Create VM2 Using Same Settings:**
   - Repeat the VM creation process for VM2 in RG1, using the same settings.
   - Ensure VM2 is part of the VM1-vnet network.
<img src="https://i.imgur.com/v6Bp021.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

   
8. **Access VM2 Using RDP:**
   - Obtain the public IP of VM2.
   - Use RDP to access VM2 using the public IP.

9. **Change Firewall Settings on VM2:**
   - Mirror the firewall settings on VM2 as done for VM1.


10. **Access Shared File:**
   - Open File Explorer, paste the shared file pathway ("\\VM1\TEST FOLDER").
   - Open "TEST DOC" and confirm it matches what was created in VM1.
   - Attempt to change the contents of the shared text file and save the file. Note that there are not the correct permissions to perform this action.
<img src="https://i.imgur.com/dFFQWhJ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/ORuV8ov.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>


11. **Change Permissions on TEST DOC:**
   - Go back to the documents folder in VM1, right-click "TEST FOLDER," click sharing, advanced options, and then permissions.
   - Check Full Control and click apply.
<img src="https://i.imgur.com/Z1og1nj.png" height="30%" width="30%" alt="Disk Sanitization Steps"/>


12. **Test Permissions Change:**
   - Go back to VM2, open "TEST DOC," type something, and save.
   - Confirm the ability to edit and save the file.
   - Open VM1, open "TEST DOC," and confirm the changes were made.
<img src="https://i.imgur.com/2uD2SU2.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>


13. **Delete Resource Group:**
   - In the Azure Portal, navigate to "Resource groups," select RG1, and delete it.
<img src="https://i.imgur.com/VBoa0lN.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>


These steps should guide you through the process of creating virtual machines in Azure, enabling file sharing, adjusting file permissions, and noting limitations in direct content changes between VM1 and VM2.
