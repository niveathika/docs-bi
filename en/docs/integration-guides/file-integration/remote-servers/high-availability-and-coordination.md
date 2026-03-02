# High availability and coordination for remote server listeners

When you run multiple instances of your integration, you need a coordination mechanism to ensure that only one instance processes a given file. This prevents data duplication and ensures high availability.

WSO2 Integrator: BI uses a database-backed leasing system to manage this coordination between multiple nodes (server instances).

## How it works

<a href="{{base_path}}/assets/img/integration-guides/file-integration/remote-servers/ha-and-coordination/coordination.png">
<img src="{{base_path}}/assets/img/integration-guides/file-integration/remote-servers/ha-and-coordination/coordination.png" alt="High Availability and Coordination"></a>

The core idea is to have one active node that handles file processing, while other instances act as standby nodes.

1.  Database Coordination: A shared database is used as a central point for all nodes to coordinate their status.

2.  Active Node Leasing: One node acquires a "token" or "lease" from the database, designating it as the active processor. This active node is responsible for polling the remote server and processing files.

3.  Heartbeat Mechanism: The active node continuously sends a "heartbeat" signal to the database, indicating that it is alive and functioning correctly.

4.  Failover: The standby nodes monitor these heartbeats. If the active node fails to send a heartbeat within a configured time (e.g., due to a crash or network issue), one of the standby nodes will acquire the token from the database and take over as the new active node.

This model guarantees that even with multiple server instances running for high availability, only one is actively processing files from the target directory at any time. All database operations are performed transactionally to ensure consistency and prevent a "split-brain" scenario where multiple nodes might think they are the active one.

## Enable coordination in remote servers integration

1. In the design view, click the **⋮** button near the **FTP Listener**.
2. Click **Configure**
3. Add **Coordination** configuration.
