# DiagnosticLogger Module

A ProcessWire module for collecting and displaying diagnostic messages.

## Overview

This module provides a mechanism for collecting and displaying diagnostic messages in ProcessWire applications. It can be used to log warnings, errors, and other important information that may help in debugging and troubleshooting issues.

## Features

- Collects diagnostic messages from various sources, including the ProcessWire framework, modules, and custom code.
- Stores diagnostic messages in a configurable log file.
- Logs messages with different severities: warning, error, and critical.
- Provides a hook to render diagnostic messages on the page, allowing them to be viewed by users.

## Limitations

- Currently, the module only logs messages to a file. In the future, it could be extended to support logging to other destinations, such as a database or console.
- The rendering of diagnostic messages is currently done using a separate module, which could be integrated into the DiagnosticLogger module for a more streamlined approach.
- The module doesn't provide any advanced filtering or search functionality for the diagnostic messages.

## Installation

1. Download the DiagnosticLogger module and place it in the `site/modules` directory of your ProcessWire installation.
2. Enable the module in the Process admin panel under the Modules tab.

## Usage

To collect diagnostic messages, simply call the `log()` method of the DiagnosticLogger module, passing the message string and severity level (warning, error, critical).

To render the diagnostic messages on the page, you can hook into the `Process::render()` event and use the `formatDiagnosticMessage()` method of the DiagnosticLogger module to format the messages.

### Example usage (PHP)

```php
$messages = wire('modules')->get('DiagnosticLogger')->getDiagnostics();

if (!empty($messages)) {
    foreach ($messages as $message) {
        $severity = $message['severity'];
        $message = $message['message'];

        if ($severity === 'Warning') {
            wire('modules')->get('DiagnosticMessageRenderer')->warning($severity . ': ' . $message);
        } else if ($severity === 'Error') {
            wire('modules')->get('DiagnosticMessageRenderer')->error($severity . ': ' . $message);
        }
    }
}
