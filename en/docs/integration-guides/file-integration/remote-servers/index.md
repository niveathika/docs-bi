# Remote server integration

Learn how to create file integrations that monitor and process files from remote FTP, SFTP, and FTPS servers using WSO2 Integrator: BI.

Remote server integration allows you to monitor directories on remote servers for file events and trigger automated workflows when files are created, modified, or deleted. This is ideal for:

- Automated file processing pipelines that involve external systems.
- Event-driven file synchronization with partner FTP/SFTP sites.
- Securely transferring and processing files from remote locations.

## Develop a remote server integration

This example demonstrates how to create an integration that listens for new JSON files on an FTP server, reads them, and logs the content.

### 1. Create the remote server listener

1.  In WSO2 Integrator: BI design view, click the **+ Add Artifact** button.
2.  Select **FTP / SFTP Integration** under the **File Integration** category.
3.  Select **FTP** as the protocol and provide the connection details for your FTP server.

    | Property      | Description                                            | Example           |
    |---------------|--------------------------------------------------------|-------------------|
    | Host          | Hostname or IP address of the remote server            | `localhost`       |
    | Port Number   | Port to connect on                                     | `21`              |
    | Folder Path   | The folder on the remote server to monitor for files   | `/sales/new`      |

4.  Select **Basic Authentication** and enter the username and password for the FTP server.

    ???+ tip "Use configurable variables"
        Use configurable variables for connection properties (e.g., `ftpHost`, `ftpUsername`, `ftpPassword`) so they can be changed at deployment time without code changes. See [Managing Configurations](../../../deploy/managing-configurations.md) for more details.

5.  Click **Create**. This creates the basic FTP listener service.

### 2. Add a file handler to process files

1. Click **+ Add File Handler** and select **onCreate** handler.
2. Select **JSON** as the **File Format**.
3. Click **Save**.
4. This shows the implementation designer by default.
5. Add a **Log Info** action. In the **Msg** field, type `Processing file from server`.
