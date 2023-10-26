
# Azure RDP Failed Login Map Monitoring

## Project Introduction

Welcome to a comprehensive guide on Azure RDP Failed Login Map Monitoring. In this project, our primary focus is working with Windows Event Logs using PowerShell, with a specific emphasis on monitoring failed RDP (Remote Desktop Protocol) login attempts.

## Creating Your Azure Account

Before diving into the technical details, ensure you have an Azure account. If you don't have one, you can easily sign up for a free account, which comes with a generous $200 credit for exploration.

## Building the Vulnerable Virtual Machine

The first step is to create a virtual machine made intentionally vulnerable by turning off the firewall. Follow these steps:

1. Create an Azure Virtual Machine with a Windows 10 operating system, setting up the administrator account and specifying a resource group for streamlined management.
2. During Network configuration, create a custom firewall rule to intentionally make the VM vulnerable.

## Setting Up Log Analytics

To effectively gather and analyze data from your VM, you'll need a log analytic workspace. Here's how to set it up:

1. Create a log analytic workspace and ensure it's in the same resource group as your VM.
2. Configure data collection within Microsoft Defender for Cloud, selecting your log analytic workspace and enabling "Servers" under Environment settings.

## Configuring the Vulnerable VM

Return to the vulnerable VM and connect to it with the public IP address using RDP. Ensure the firewall is turned off for the Domain Profile, Private Profile, and Public Profile.

## Data Ingestion with PowerShell

Let's delve into data ingestion using PowerShell:

1. Sign up at ipgeolocation.io and obtain an API key.
2. Open PowerShell ISE on your vulnerable VM and execute a provided PowerShell script, replacing the API key with the one you obtained.
3. This script will notify you in the PowerShell command line of any attempted connections to your vulnerable VM.

## Creation of Custom Logs

Creating custom logs in the Log Analytic Workspace is the next step:

1. Within the Log Analytics Workspace, select your workspace.
2. Under virtual machines, connect your VM to the workspace.
3. In the same menu, click "Tables" and then "Create," establishing a new custom log (MMA-based).
4. Configure the log to collect data from your VM by copying the contents of the "failed_rdp.log" file from your VM to your local computer.

## Setting up the Map and Analyzing Data

Now, it's time to set up our SIEM:

1. Access Microsoft Sentinel and create a new workbook.
2. Add a query matching the one used in the custom logs.
3. Visualize the data on a map using specific settings as illustrated.
4. Save your configuration.

That's it! Each time someone attempts to connect to your vulnerable VM via RDP, the event will be plotted on your map.

## Important Note

Don't forget to delete all resources when you're finished to avoid consuming your Azure credits.

## In Conclusion

A special thanks to @JoshMadakor for sharing this fascinating project, which has not only enhanced our understanding of Azure but also our experience with Microsoft Sentinel.
