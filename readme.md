# DiagnosticLogger

Do you struggle like me with keeping track of updates across multiple website projects? Do you also feel like your clients are unaware of what web development maintenance involves? Do you sometimes feel unappreciated for your hard work? If so, here's a solution for you. It's not perfect, but it's a start.

**DiagnosticLogger** is a ProcessWire module designed to handle diagnostic logs and create notifications in the admin GUI. It can also send automated email summaries for warnings and errors found in these logs.

## Features

- **Log Handling**: Captures and processes diagnostic logs.
- **Admin Notifications**: Displays notifications within the admin GUI for detected issues.
- **Email Summaries**: Sends automated emails summarizing warnings and errors.

## Integration

The module integrates with **ProcessDiagnostics**, which is required for its functionality. It is designed to work seamlessly with ProcessDiagnostics but is not highly configurable.

## Important!!

I wasn't able to accomplish this in the hook from inside the DiagnosticLogger class so you need to add these lines in the ProcessDiagnostics.module file to make this work.

 ```php
    public function ___execute() {
    wire('log')->delete('diagnostics'); // to not be redundant
    // …
    foreach ($results as $caption => $section_results) {
        // …
        foreach ($section_results as $k => $row) {
            // …
            wire('log')->save('diagnostics', '|' . $row['title'] . '|' . $row['value'] . '|' . $row['status'] . '|' . $row['action']);
        }
    }
}
```

This will log the diagnostics everytime the ProcessDiagnostics runs. I still haven't figured out how to run diagnostics automatically or schedule them.

## Workaround for Background Diagnostics

The logging feature acts as a workaround due to difficulties with running diagnostics in the background. The hooked method from ProcessDiagnostics will need to be made hookable for better integration.

## Configuration

1. Access the configuration settings in the ProcessWire admin interface.
2. Adjust the settings according to your needs.

## email LazyCron Scheduling

For scheduling tasks using LazyCron, for example:

- `every2Weeks`: Runs tasks every two weeks.
- `everyDay`: Runs tasks every day.
- `everyWeek`: Runs tasks every week.

## Installation

1. Download the module and place it in the `site/modules` directory.
2. Log in to the ProcessWire admin interface.
3. Go to Modules > Refresh.
4. Locate **DiagnosticLogger** and click **Install**.

## Usage

Once installed, **DiagnosticLogger** will automatically start processing diagnostic logs. You can view notifications in the admin GUI and receive email summaries based on your configuration.

## Requirements

- ProcessWire 3.x or later
- ProcessDiagnostics module