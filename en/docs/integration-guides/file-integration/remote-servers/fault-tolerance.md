# Fault tolerance for remote server integrations

When processing large files, especially CSVs, a single malformed row can cause the entire integration to fail. To prevent this, WSO2 Integrator: BI provides a fail-safe mechanism that isolates problematic rows and allows the rest of the file to be processed successfully.

This feature improves the robustness of your file integrations by ensuring that minor data errors do not halt your entire workflow.

## How it works

The fail-safe mechanism is enabled by configuring the `csvFailSafe` property in the remote server listener.

1.  **Enable Fail-Safe**: When you enable this option, the listener activates a special error handling mode for CSV file processing.

2.  **Isolate Bad Rows**: If the integration encounters a row that it cannot parse (e.g., due to incorrect formatting or data type mismatch), it doesn't stop. Instead, it isolates the offending row.

3.  **Log Errors**: The problematic row is written to a separate error log file, typically named `<original-filename>_error.log`. This allows you to review and correct the data issues later without losing the original error context.

4.  **Continue Processing**: The integration then seamlessly continues to process the remaining valid rows in the file.

This ensures that your integration is resilient to common data quality issues and can process large volumes of data without interruption.


## Enable fail safe processing

1. In the design view, click the **⋮** button near the **FTP Listener**.
2. Click **Configure**
3. Add **CSV Fail Safe** configuration.
