<h1>Configuring a Network Security Group (NSG) to Control ICMP Traffic in Azure</h1>

<b>Objective:</b> In this section, you will configure an Azure Network Security Group (NSG) to control ICMP (ping) traffic between your Azure Windows 10 VM and Ubuntu VM. <br><br>
You will observe how firewall rules affect network communication in real-time using both Wireshark and PowerShell’s ping command. <br><br>
This exercise demonstrates how Azure NSG rules control traffic flow between virtual machines. By using Wireshark and PowerShell, you will see how security policies affect real-time network communication. <br><br>

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Computer)
- Remote Desktop/Windows App
- Powershell
- Network Security Groups
- Command-Line Tools
- Network Protocol ICMP
- Wireshark (Protocol Analyzer)


<h2>Operating Systems Used </h2>

- Windows 10 Pro (22H2)
- Ubuntu Server 22.04


<h2>Actions and Observations</h2>

Steps:
1.	Start a Continuous Ping: On your Windows 10 VM, initiate a continuous (-t) ICMP ping to your Ubuntu VM using PowerShell.
<img width="1512" alt="Step 4a - Network Security Group" src="https://github.com/user-attachments/assets/7309e364-eacb-4804-b190-485f231b3d91" />
<br><br>
2.  Modify the Network Security Group (NSG): Locate the NSG associated with your Ubuntu VM, then disable inbound ICMP traffic by updating the security rules.
<img width="1628" alt="Step 4b - Network Security Group" src="https://github.com/user-attachments/assets/d6e140f7-4597-4d05-b753-335b33d273ad" />
<img width="1629" alt="Step 4c - Network Security Group" src="https://github.com/user-attachments/assets/acf7074e-c51d-4918-b9c7-a5bfe8a3ae7d" />
<img width="1632" alt="Step 4d - Network Security Group" src="https://github.com/user-attachments/assets/f491c459-b315-4ab7-8ee6-373aed7f7c1f" />
<br><br>
3.	Observe the Impact: Back in your Windows 10 VM, monitor both:
    - The Wireshark capture (to see ICMP request packets being sent but no responses).
    - The PowerShell ping output, which should indicate packet loss or timeouts.
<img width="1512" alt="Step 4e - Network Security Group" src="https://github.com/user-attachments/assets/c1e73e24-a68b-4597-8a38-304c0c8982d1" />
<br><br>
4.	Restore ICMP Access: Re-enable inbound ICMP traffic in the NSG for your Ubuntu VM.
<img width="1633" alt="Step 4f - Network Security Group" src="https://github.com/user-attachments/assets/3fa170b5-da26-4319-af85-aa479559e5d8" />
<br><br>
5.	Verify Connectivity: Return to the Windows 10 VM and observe:
    - Wireshark should now show successful ICMP replies.
    - The ping command should resume normal operation.
<img width="1512" alt="Step 4g - Network Security Group" src="https://github.com/user-attachments/assets/94372d3d-a046-48a0-9775-344f4363ebb1" />
<br><br>
6.	Stop the Ping Test: Once confirmed, stop the continuous ping process in PowerShell by pressing Ctrl + C, or closing Powershell.

<h2>Summary & Significance</h2>

<h3>What You Did</h3>
	•	Started a continuous ping to monitor ICMP traffic. <br>
	•	Used Azure NSG rules to temporarily block and re-enable ICMP traffic. <br>
	•	Observed the effects of firewall changes in Wireshark and PowerShell. <br>

<h3>Why This Matters:</h3>
	•	NSGs are essential for cloud security – they control which traffic is allowed or blocked between Azure resources.<br>
	•	ICMP filtering is commonly used for security to prevent unauthorized network scanning or restrict unnecessary ping traffic.<br>
	•	Using Wireshark for real-time packet analysis provides insight into how network rules affect communication at the packet level.<br>
	•	Understanding NSGs helps troubleshoot connectivity issues – for example, if a service isn’t reachable, checking NSG rules can reveal whether traffic is being blocked.<br>
<br>
By completing this tutorial, you’ve gained hands-on experience with configuring security rules in Azure, monitoring network traffic with Wireshark, and understanding how firewall policies affect ICMP communication.






