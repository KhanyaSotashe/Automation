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
```

## What I Learned

1. **PowerShell Cmdlets** — Learned how to use PowerShell commands such as `Get-Service` to retrieve information from Windows services.

2. **Variables** — Learned how to store information in variables and access the data later in the script.

3. **Object Properties** — Learned how to access properties of PowerShell objects, such as using `$Service.Status` to retrieve a service's current status.

4. **Conditional Logic** — Learned how to use `if/else` statements to make the script perform different actions based on the service status.

5. **Automated Recovery & Verification** — Learned how to automatically start a stopped service and then verify that the service successfully started.

   ## IF YOU ARE INTERESTED TO CHECK IT OUT, FIND THE SCRIPT BELOW
```powershell
   $ServiceName = "W32Time"
$Service = Get-Service -Name $ServiceName

if ($Service.Status -eq 'Running') {
    Write-Host "The $ServiceName service is already running."
}
else {
    Write-Host "The $ServiceName service is currently stopped. Attempting to start it..."
    
    Start-Service -Name $ServiceName
    Start-Sleep -Seconds 2
    $Service.Refresh()
    
    if ($Service.Status -eq 'Running') {
        Write-Host "Success! The $ServiceName service has been started."
    }
    else {
        Write-Host "Failure. The $ServiceName service could not be started."
    }
}
```


