# Project 1: Windows Service Health Check & Recovery

## Project Overview

This project is my first practical automation project using **PowerShell**.

The objective was to create a script that can check the status of a Windows service, identify whether the service is running or stopped and automatically attempt to start the service if it is stopped.


This project introduced me to the basic automation workflow of:

**Detect → Act → Verify**

---

## Objective

The objective of this project was to learn how PowerShell can be used to automate a basic IT administration task.

The script performs the following:

1. Checks the Windows Time service (`W32Time`).
2. Retrieves the current service status.
3. Determines whether the service is running.
4. If the service is stopped, attempts to start it.
5. Checks the service status again.
6. Confirms whether the service successfully started.

---

## Technology Used

- **PowerShell**
- Windows Services
- PowerShell Cmdlets
- Variables
- Conditional Statements
- Service Management

### Script Language

The automation script is written in **PowerShell** and uses the `.ps1` file extension.

---

## Automation Workflow

```text
             Get W32Time Service
                    ↓
             Check Service Status
                    ↓
             Is Service Running?
              ↙             ↘
            YES              NO
             ↓                ↓
      Report Status      Start Service
                              ↓
                       Check Status Again
                              ↓
                    Did Service Start?
                       ↙          ↘
                     YES          NO
                      ↓            ↓
                Report Success  Report Failure
