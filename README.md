# Automated Email Notification Script

## Overview

This Google Apps Script automates the process of sending email notifications based on data entered in a Google Sheet. The script is triggered whenever a value is edited in the "Planned Start Date" column (Column Z). Upon detecting an edit, the script collects data from various columns in the same row and sends an email formatted according to the specified template.

## Features

- **Trigger-Based Execution:** The script automatically triggers when an edit is made in the "Planned Start Date" column (Column Z).
- **Dynamic Email Content:** The email content is dynamically generated based on the data in the same row as the edit.
- **HTML Email Formatting:** The email is sent with HTML formatting, ensuring that the content appears clean and consistent.
- **Customizable Subject Line:** The subject line of the email includes the Request ID, Request Type, and Metrics associated with the objectives.

## Column Mappings

The script uses the following columns from the Google Sheet:

- **Email Address:** Column B
- **Request Type:** Column G
- **Metrics Associated with the Objectives:** Column K
- **Complete Name:** Column C
- **Assigned To:** Column U
- **Complexity:** Column X
- **SLA (computed):** Column Y
- **Planned Start Date:** Column Z (this column triggers the script)
- **Communicated End Date (computed):** Column AA
- **Request ID:** Column W

## How It Works

1. **Trigger Setup:**
   - The script is triggered by edits made in the "Planned Start Date" column (Column Z). When a user updates or enters a date in this column, the script automatically runs.

2. **Data Retrieval:**
   - When the script is triggered, it retrieves the necessary data from the following columns in the same row: Email Address (B), Request ID (W), Request Type (G), Metrics (K), Complete Name (C), Assigned To (U), Complexity (X), SLA (Y), Planned Start Date (Z), and Communicated End Date (AA).

3. **Email Generation:**
   - The script constructs the subject line using the following format:
     ```
     [Request ID] Request for Request Type - Metrics
     ```
   - The body of the email includes details such as the assignee, complexity, SLA, planned start date, and expected completion date. The text is formatted in plain black color with no bold formatting.

4. **Email Sending:**
   - The script sends the email to the address found in Column B. The email is sent in HTML format to ensure proper styling.

## Installation

1. **Copy the Script:**
   - Copy the provided script into the Google Apps Script editor associated with your Google Sheet.

2. **Set Up the Trigger:**
   - Go to the Apps Script editor, click on the clock icon (Triggers), and set up an installable trigger for the `customOnEdit` function. The trigger should be set to run on edits made in the Google Sheet.

## Troubleshooting

- **Emails Not Being Sent:** Ensure that the trigger is correctly set up in the Google Apps Script editor. Also, verify that the email addresses in Column B are correctly formatted.
- **Date Formatting Issues:** If the dates are not displaying correctly, double-check the format used in the `Utilities.formatDate()` function.
- **Script Not Triggering:** Make sure that the script is linked to the correct Google Sheet and that the trigger is set to monitor edits in Column Z.
