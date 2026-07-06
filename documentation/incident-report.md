# Incident Report

## Incident Title
Multiple Failed Login Attempts Detected

## Date and Time
Pending

## Affected Device
Desktop1 / Windows 10 Domain Client

## Event ID
4625 - Failed Logon

## Description
Multiple failed login attempts were generated and detected using Windows Event Viewer. These events may indicate a user typing the wrong password, unauthorized login attempts, or a possible brute-force attempt.

## Findings
- Failed login events were found in Windows Security logs.
- Event ID 4625 was used to identify failed authentication attempts.
- The affected user account and source device were reviewed.

## Impact
The activity did not cause confirmed compromise in this lab. However, repeated failed login attempts can indicate a security risk and should be investigated.

## Recommended Actions
- Verify if the login attempts were made by the legitimate user.
- Check if the account becomes locked out.
- Reset the password if suspicious activity is confirmed.
- Review related successful login events.
- Continue monitoring the affected account.

## Status
Pending final testing.
