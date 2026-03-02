# Local Files Integration

Learn how to create file integrations that monitor and process files in local directories using WSO2 Integrator: BI.

Local files integration allows you to monitor directories for file events and trigger automated workflows when files are created, modified, or deleted. This is ideal for:

- Automated file processing pipelines
- Event-driven file synchronization
- Real-time file monitoring and alerting

## Develop a Local Files Integration

### Step 1: Create a Local Files Integration

1. In the design view, click the **Add Artifact** button.
2. Select **Local Files** under the **File Integration** category.
3. Enter the path to the directory you want to monitor. For example, `/user/home/Downloads`.

    ???+ Tip "Use configurable variables"
        Use a configurable variable for the path (e.g., `monitorPath`) so it can be changed at deployment time without code changes. See [Managing Configurations](../deploy/managing-configurations.md) for more details.

4. Click the **Create** button to create the Local Files Integration.

    <a href="{{base_path}}/assets/img/integration-guides/file-integration/local-files-integration/1-add-local-files-integration.gif">
    <img src="{{base_path}}/assets/img/integration-guides/file-integration/local-files-integration/1-add-local-files-integration.gif" alt="Local Files Integration" width="70%"></a>

### Step 2: Configure file event handlers

1. Click the **Add Handler** button and select the **onCreate** handler.

    <a href="{{base_path}}/assets/img/integration-guides/file-integration/local-files-integration/2-add-handler.gif">
    <img src="{{base_path}}/assets/img/integration-guides/file-integration/local-files-integration/2-add-handler.gif" alt="onCreate Function" width="70%"></a>
