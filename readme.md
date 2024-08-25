# DiagnosticLogger

**DiagnosticLogger** is a ProcessWire module designed to handle diagnostic logs and create notifications in the admin GUI. It can also send automated email summaries for warnings and errors found in these logs.

## Features

- **Log Handling**: Captures and processes diagnostic logs.
- **Admin Notifications**: Displays notifications within the admin GUI for detected issues.
- **Email Summaries**: Sends automated emails summarizing warnings and errors.

## Integration

The module integrates with **ProcessDiagnostics**, which is required for its functionality. It is designed to work seamlessly with ProcessDiagnostics but is not highly configurable.

## Workaround for Background Diagnostics

The logging feature acts as a workaround due to difficulties with running diagnostics in the background. The hooked method from ProcessDiagnostics will need to be made hookable for better integration.

## LazyCron Scheduling

For scheduling tasks using LazyCron, use the following time schedules:

- `every2Weeks`: Runs tasks every two weeks.
- `everyDay`: Runs tasks every day.
- `everyWeek`: Runs tasks every week.

## Installation

1. Download the module and place it in the `site/modules` directory.
2. Log in to the ProcessWire admin interface.
3. Go to Modules > Refresh.
4. Locate **DiagnosticLogger** and click **Install**.

## Configuration

1. Access the configuration settings in the ProcessWire admin interface.
2. Adjust the settings according to your needs.

## Usage

Once installed, **DiagnosticLogger** will automatically start processing diagnostic logs. You can view notifications in the admin GUI and receive email summaries based on your configuration.

## Requirements

- ProcessWire 3.x or later
- ProcessDiagnostics module

## Troubleshooting

If you encounter issues:

- Ensure **ProcessDiagnostics** is correctly installed and configured.
- Check the module logs for any error messages.
- Review the configuration settings to ensure they are set up properly.

## Contributing

Feel free to contribute to the development of **DiagnosticLogger** by submitting issues or pull requests on the [GitHub repository](https://github.com/your-repository-link).

## License

This module is licensed under the [MIT License](LICENSE).

## Contact

For any questions or support, please contact [your-email@example.com](mailto:your-email@example.com).
