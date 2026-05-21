# Grafana with Podman

Step-by-Step guide for installing Grafana using Podman on Linux / WSL Ubuntu.

---

## Install Podman

```bash
sudo apt update
sudo apt install -y podman
```

Verify:

```bash
podman --version
```

---

## Pull Grafana Image

```bash
podman pull docker.io/grafana/grafana:latest
```

---

## Create Persistent Folder

```bash
mkdir -p ~/grafana-data
```

---

## Run Grafana Container

```bash
podman run -d \
--name grafana \
-p 3000:3000 \
-v ~/grafana-data:/var/lib/grafana \
docker.io/grafana/grafana:latest
```

---

## Access Grafana

```text
http://localhost:3000
```

Default Login:

| Username | Password |
|---|---|
| admin | admin |

---

## Useful Commands

### Stop Container

```bash
podman stop grafana
```

### Start Container

```bash
podman start grafana
```

### Restart Container

```bash
podman restart grafana
```

### View Logs

```bash
podman logs -f grafana
```

### Remove Container

```bash
podman rm -f grafana
```

---

## Example Architecture

```mermaid
flowchart LR

A[PLC / Sensor] --> B[Node-RED]
B --> C[MQTT Broker]
C --> D[InfluxDB]
D --> E[Grafana Dashboard]
```

---

## Industrial Use Cases

- PLC Dashboard
- SCADA Monitoring
- MQTT Visualization
- Energy Monitoring
- Industrial IoT
