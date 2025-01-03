
# Time Based Local Historian Stack

```plaintext
████████╗ ██╗ ███╗   ███╗ ███████╗    ██████╗   █████╗  ███████╗ ███████╗ ██████╗ 
╚══██╔══╝ ██║ ████╗ ████║ ██╔════╝    ██╔══██╗ ██╔══██╗ ██╔════╝ ██╔════╝ ██╔══██╗
   ██║    ██║ ██╔████╔██║ █████╗      ██████╔╝ ███████║ ███████╗ █████╗   ██║  ██║
   ██║    ██║ ██║╚██╔╝██║ ██╔══╝      ██╔══██╗ ██╔══██║ ╚════██║ ██╔══╝   ██║  ██║
   ██║    ██║ ██║ ╚═╝ ██║ ███████╗    ██████╔╝ ██║  ██║ ███████║ ███████╗ ██████╔
   ╚═╝    ╚═╝ ╚═╝     ╚═╝ ╚══════╝    ╚═════╝  ╚═╝  ╚═╝ ╚══════╝ ╚══════╝ ╚═════╝ 
```

A Docker Compose stack for deploying a local Industrial Historian infrastructure that includes:

- **Timebase Historian**: A time-series data historian.
- **Timebase Collector**: Collects and organizes time-series data.
- **Timebase Explorer**: Provides visualization and exploration tools.
- **Node-RED**: A flow-based development tool for wiring IoT systems.
- **EMQX MQTT Broker**: A scalable MQTT broker for real-time data.

## Environment Variables

The stack uses an `.env` file for configuration. Below are the variables used and some example values:

```plaintext
# Timebase Historian
HISTORIAN_TAG=latest
HISTORIAN_HOSTNAME=historian
HISTORIAN_CONTAINER_NAME=historian
HISTORIAN_PORT=4511
```

```plaintext
# Timebase Collector
COLLECTOR_TAG=latest
COLLECTOR_HOSTNAME=collector
COLLECTOR_CONTAINER_NAME=collector
COLLECTOR_PORT=4521
COLLECTOR_ACTIVE=false
```

```plaintext
# Timebase Explorer
EXPLORER_TAG=latest
EXPLORER_HOSTNAME=explorer
EXPLORER_CONTAINER_NAME=explorer
EXPLORER_PORT=4531
```

```plaintext
# Node-RED
NODERED_TAG=latest
NODERED_HOSTNAME=node-red
NODERED_CONTAINER_NAME=node-red
NODERED_PORT=1880
```

```plaintext
# EMQX MQTT Broker
EMQX_TAG=latest
EMQX_HOSTNAME=broker
EMQX_CONTAINER_NAME=broker
EMQX_MQTT_PORT=1883
EMQX_WS_PORT=8083
EMQX_DASHBOARD_PORT=18083
EMQX_ALLOW_ANONYMOUS=true
```

## Deploying in Portainer

1. **Go to Portainer Stacks**:
   Log in to your Portainer instance and navigate to the **Stacks** section.

2. **Add a new stack**:
   - Click **Add Stack**.
   - Provide a name (e.g., `time-based-historian`).

3. **Deploy from Git**:
   - Select the **Git Repository** option.
   - Enter the Git repository URL (e.g., `https://github.com/DMDuFresne/time-based-historian.git`).
   - Specify the branch (e.g., `main`) and the path to `docker-compose.yml`.

4. **Set environment variables**:
   - Use the **Variables** tab to input the variables from the `example.env` file or customize them in the stack editor.

5. **Deploy the stack**:
   - Click **Deploy the stack** to launch the services.

6. **Monitor and manage the stack**:
   - Use Portainer's dashboard to view logs, restart containers, or troubleshoot any issues.

## Run Locally with Docker Compose

1. **Clone the repository**:

   ```bash
   git clone https://github.com/DMDuFresne/time-based-historian.git
   cd time-based-historian
   ```

2. **Create an `.env` file**:

   ```bash
   cp example.env .env
   ```

   Edit `.env` to customize your configuration as needed.

3. **Start the stack**:

   ```bash
   docker-compose up -d
   ```

4. **Verify the services**:

   ```bash
   docker-compose ps
   ```

5. **Stop the stack**:

   ```bash
   docker-compose down
   ```

## Notes

- Ensure your Docker engine and Portainer instance have adequate resources for the services.
- All services use persistent volumes to store data. These volumes are defined in `docker-compose.yml`.
- Health checks are included for all services to monitor their readiness and availability.

## Help and Configuration

- Timebase: <https://timebase.flow-software.com/en/knowledge-base>
- Node Red: <https://nodered.org/docs/user-guide/editor/>
- EMQX:     <https://docs.emqx.com/en/emqx/latest/>

## License

This project is licensed under the [MIT License](LICENSE).
