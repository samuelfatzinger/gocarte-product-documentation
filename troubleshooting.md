# Troubleshooting Common GoCarte Issues

## Overview

This guide addresses common issues users may encounter while working in GoCarte. The sections below describe typical problems and provide steps to resolve them.

If the issue persists after completing the recommended steps, contact your Workroom administrator or the GoCarte IT Help Desk.

---

## Unable to Sign In

If you cannot sign in to GoCarte, verify the following:

- Confirm that your username or email address is entered correctly. Usernames and passwords are case-sensitive.  
- Check that your password is correct and has not expired. Accounts restored through the IT Help Desk after a password expiration may take up to 24 hours to become active again.  
- Make sure the **two-factor authentication (2FA)** code is entered correctly before the five-minute expiration.  

If you have forgotten your password, follow the steps in **Resetting Your GoCarte Password**.

If your password has expired and cannot be reset, contact the IT Help Desk for authorization:

Email: helpdesk.it@gocarte.com  
Phone: (555) 123-1234

---

## Tasks Do Not Appear in a Project

If a task you created does not appear in the project task list, check the following:

- Refresh the browser page to ensure the dashboard is updated.  
- Confirm that the task was created within the correct project.  
- Check whether the task is hidden within a collapsed task group or subtask list.  
- Verify that the due date is correct.  
- Verify that the task was not marked complete by searching for the task name in **Completed Tasks** within the **Task Management Container**.

If the task still does not appear, verify that the task was successfully created and saved.

---

## Dashboard Does Not Update

If the dashboard does not reflect recent changes to tasks or projects:

- Refresh the page to update the dashboard.  
- Confirm that task status changes were saved.  
- Verify that you are viewing the correct Workroom and the correct project.  
- Check that your status is not set to **Away** in the notification widget.

The dashboard normally updates automatically when task status changes.

---

## Unable to Access a Workroom

If you cannot access a Workroom:

- Confirm that you are signed in using the correct account.  
- Verify that you have permission to access the Workroom.  
- Check whether the Workroom administrator has sent you an invitation to the workspace.  
- Try signing out of your account and signing back in.

If access problems continue, contact the Workroom administrator.

---

## GoCarte Is Unresponsive

If you cannot navigate or select menus or icons:

- Check whether your browser is functioning in other tabs.  
- Close the GoCarte application tab and reopen it.  
- Make sure the browser has permission to run GoCarte scripts and extensions.  
- Restart the browser if the problem continues.  
- Verify that your browser and operating system are up to date.  
- Confirm that your internet connection is working on another device.

If problems continue, contact the Workroom administrator or submit a ticket to the IT Help Desk.

---

## API Authentication Errors

Developers using the GoCarte API may encounter authentication errors if an API key is invalid or expired.

Verify the following:

- Confirm that the API key is included in the request header.  
- Ensure the key is entered correctly.  
- Check that the API key has not expired or been revoked.  
- Verify that the request header uses the correct authorization format.

Common errors include **401 Unauthorized** or **403 Forbidden** responses.

For additional guidance, refer to the **GoCarte API Reference**.

---

## When to Contact Support

If the issue cannot be resolved using the steps above, contact the **GoCarte IT Help Desk**.

Email: helpdesk.it@gocarte.com  
Phone: (555) 123-1234

Provide the following information when submitting a support request:

- your username  
- the Workroom you are working in  
- a description of the issue  
- screenshots if available
