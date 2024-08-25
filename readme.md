# DiagnosticLogger Module for ProcessWire

## Overview

**DiagnosticLogger** is a ProcessWire module designed to process diagnostic logs and create notifications in the admin GUI. It can also send automated email notifications summarizing warnings and errors found in the logs. This module is highly configurable and integrates seamlessly with the **ProcessDiagnostics** module, which it requires.

## Features

- **Admin Notifications:** Automatically generates admin notifications based on log entries.
- **Email Notifications:** Sends emails containing warnings and errors found in the logs.
- **Configurable Settings:** Easily customize the sender/receiver email addresses, notification schedules, and more via the module's configuration page.
- **LazyCron Integration:** Uses LazyCron to schedule the email notifications, which can be customized as per your needs.

## Requirements

- **ProcessWire 3.x**
- **ProcessDiagnostics** module

## Installation

1. **Download and Install the Module:**

   - Clone or download the repository and place the module folder into the `site/modules/` directory of your ProcessWire installation.
   - In the ProcessWire admin, navigate to **Modules > Refresh**, then find and install the **DiagnosticLogger** module.

2. **Configure the Module:**

   - After installation, go to the module's settings page to configure the email settings, including sender/receiver email addresses, email schedule, and more.

3. **Integrate with ProcessDiagnostics:**

   - To ensure the **DiagnosticLogger** module can capture the relevant log entries, add the following lines to the `ProcessDiagnostics.module` file in the appropriate location where logs are being handled:
     ```php
     wire('log')->delete('diagnostics'); // Clears previous logs
     wire('log')->save('diagnostics', '|' . $row['title'] . '|' . $row['value'] . '|' . $row['status'] . '|' . $row['action']); // Saves new log entries
     ```
   - These lines will log the diagnostic data in the correct format so that the **DiagnosticLogger** can process and notify based on these logs.

## Usage

### Admin Notifications

Once installed, the module will automatically start generating admin notifications based on the entries in the diagnostic logs. These notifications will appear in the ProcessWire admin interface, providing quick insights into any issues or warnings.

### Email Notifications

The module can also send out email notifications that summarize any warnings or failures found in the diagnostic logs. The email configuration, including sender and receiver details, can be set up in the module's configuration page.

### Log Format

The module expects the log entries to follow a specific format:

timestamp | title | value | status | action

Where:
- **timestamp**: Date and time of the log entry.
- **title**: A brief title describing the log entry.
- **value**: The core information or value associated with the log entry.
- **status**: The status, which can be `error`, `warning`, `ok`, etc.
- **action**: Any action taken or recommended based on the log entry.

### LazyCron Scheduling

By default, the module uses LazyCron to send out email notifications based on the schedule defined in the module's settings. You can change the schedule by modifying the `email_schedule` setting.

## Configuration Options

The module provides several configuration options accessible via the ProcessWire admin interface:
- **Sender Name:** The name that will appear as the sender of the email.
- **Sender Email:** The email address that will appear as the sender.
- **Receiver Name:** The name of the person or entity receiving the email.
- **Receiver Email:** The email address where notifications will be sent.
- **Reply-To Email:** The email address where replies will be directed.
- **BCC Email:** An optional email address for sending blind carbon copies.
- **Email Subject:** The subject line for the email notifications.
- **Website Name:** The name of the website, used in the email body.
- **Email Schedule:** The LazyCron schedule for sending emails (e.g., `every2Weeks`, `daily`, `weekly`).

## Example Usage

After installing and configuring the module, the **DiagnosticLogger** will begin to log and notify you based on your configuration. No additional steps are necessary unless you want to adjust the module's settings.

## Contributing

Contributions are welcome! Please fork the repository and submit a pull request with your improvements or fixes. Ensure your code adheres to the coding standards used in this project.

## License

This module is open-source software licensed under the MIT License.

## Contact

If you have any questions, issues, or suggestions, feel free to open an issue on GitHub or reach out directly.
