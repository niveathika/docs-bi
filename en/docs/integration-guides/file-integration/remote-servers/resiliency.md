# Resiliency for remote server integrations

When integrating with remote FTP or SFTP servers, transient network issues can cause operations to fail. To build a truly resilient integration, you need a way to automatically handle these temporary disruptions without manual intervention.

WSO2 Integrator: BI introduces automatic retry support with exponential backoff, making your file integrations more robust and reliable.

## How it works

The automatic retry mechanism helps your integration gracefully handle temporary network failures when communicating with a remote server.

1.  **Enable Retries**: You can enable and configure this feature by adding a `RetryConfig` to your remote server listener or client configuration. This allows you to specify the number of retry attempts, the initial wait time, and the maximum wait time.

2.  **Automatic Retry on Failure**: If a file operation (like reading a file) fails due to a transient network error, the integration doesn't immediately stop. Instead, it automatically waits for a configured interval and then retries the operation.

3.  **Exponential Backoff**: The system uses an exponential backoff strategy. If the first retry fails, it will wait for a longer period before attempting the next one. This prevents overwhelming a remote server that might be temporarily struggling.

By handling these transient errors automatically, this feature simplifies your integration logic and significantly improves its reliability.
