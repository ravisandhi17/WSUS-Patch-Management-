## WSUS Patch Management Lab

## Project Overview

This project demonstrates the deployment and configuration of Windows Server Update Services (WSUS) on Windows Server 2022 in an Active Directory domain environment. The lab was built to centralize Windows update management, automate patch deployment, and manage update compliance for domain-joined Windows 11 client systems.

The objective of this project was to simulate an enterprise patch management environment commonly used by System Administrators, Infrastructure Support Technicians, and IT Operations teams.

## Lab Environment

Server

Dell PowerEdge R720

Windows Server 2022 Standard Evaluation

Active Directory Domain Services (AD DS)

DNS Server

WSUS Server

Client

Windows 11 Domain-Joined VM

Domain: ravikumar.local

## Lab Architecture

Dell PowerEdge R720
│
├── DC1 (Windows Server 2022)
│   ├── Active Directory Domain Services
│   ├── DNS Server
│   ├── WSUS Server
│   └── WSUS Port: 8530
│
└── Windows 11 Client
    ├── Domain Joined
    ├── Receives Group Policy
    └── Uses WSUS for Updates

## Objectives

Install and configure WSUS on Windows Server 2022

Create WSUS computer groups

Configure Group Policy for WSUS clients

Redirect Windows Update traffic to an internal WSUS server

Verify client-side WSUS configuration

Simulate centralized patch management

WSUS Configuration

WSUS Installation

Installed WSUS services and management tools on Windows Server 2022.

WSUS Content Directory: C:\WSUS

WSUS Server: DC1

WSUS Port: 8530

Computer Group Created: Workstations

## Group Policy Configuration

Created and linked a Group Policy Object:

WSUS Client Settings
Policy Location
Computer Configuration
└─ Policies
   └─ Administrative Templates
      └─ Windows Components
         └─ Windows Update
Configure Intranet Microsoft Update Service Location

Enabled:

Specify intranet Microsoft update service location

Configured:

http://DC1:8530

for both:

Update Detection Server
Statistics Server
Client Verification
Group Policy Applied

## Verified using:

gpresult /r

Result:

Applied Group Policy Objects

- Default Domain Policy

- WSUS Client Settings

Registry Verification

Verified WSUS settings using:

Get-ItemProperty "HKLM:\Software\Policies\Microsoft\Windows\WindowsUpdate"

Get-ItemProperty "HKLM:\Software\Policies\Microsoft\Windows\WindowsUpdate\AU"

Results:

WUServer       = http://DC1:8530

WUStatusServer = http://DC1:8530

UseWUServer    = 1

Validation Performed

Verified WSUS installation completed successfully

Confirmed WSUS service status

Verified WSUS console accessibility

Created WSUS computer groups

Configured Group Policy for clients

Verified GPO application on Windows 11 client

Verified registry-based WSUS settings

Tested Windows Update detection against WSUS configuration

Screenshots

WSUS Administration Console




Workstations Computer Group




WSUS Client Settings GPO




WSUS Update Server Configuration




Group Policy Verification




Registry Verification




WSUS Service Status




## Skills Demonstrated

Windows Server 2022

Windows Server Update Services (WSUS)

Patch Management

Group Policy Administration

Active Directory

Windows Update Management

Endpoint Administration

System Administration

Troubleshooting

Enterprise IT Infrastructure

## Outcome

Successfully deployed and configured a centralized WSUS patch management solution in an Active Directory environment. Domain-joined Windows clients were configured through Group Policy to use the internal WSUS server, demonstrating enterprise patch management and update administration practices.
## Author

## RAVI KUMAR
