# Greenbone Community Edition (OpenVAS)

This repository contains a Docker Compose configuration for running the **Greenbone Community Edition**, a powerful vulnerability management solution.

## Prerequisites

- [Docker](https://docs.docker.com/get-docker/)
- [Docker Compose](https://docs.docker.com/compose/install/)

## Quick Start

1.  **Start the services:**
    ```bash
    docker compose up -d
    ```

2.  **Wait for the setup to complete:**
    The first start can take several minutes as it downloads the vulnerability feeds and initializes the database. You can monitor the progress with:
    ```bash
    docker compose logs -f
    ```

3.  **Access the Web Interface:**
    Open your browser and navigate to:
    - [https://127.0.0.1:9392](https://127.0.0.1:9392)
    - [https://127.0.0.1:443](https://127.0.0.1:443)

4.  **Login:**
    - **Username:** `admin`
    - **Password:** `admin`

## Configuration

### Changing the Admin Password
It is highly recommended to change the default password after the first login:
```bash
docker compose exec -u gvmd gvmd gvmd --user=admin --new-password=<YOUR_NEW_PASSWORD>
```

### Feed Updates
The containers are configured to automatically sync the community feeds (Vulnerability Tests, Scap Data, Cert Data, etc.). The `FEED_RELEASE` is currently set to `24.10`.

## Architecture Overview

This deployment consists of several interconnected services:

- **gvmd**: The Greenbone Vulnerability Manager daemon.
- **gsa**: The Greenbone Security Assistant (web interface).
- **gsad**: The Greenbone Security Assistant daemon.
- **ospd-openvas**: The OpenVAS Scanner wrapper.
- **openvas**: The core OpenVAS scanner.
- **redis-server**: Used for temporary storage during scans.
- **pg-gvm**: PostgreSQL database for storing scan results and configurations.
- **nginx**: Reverse proxy for secure access.
- **Data Containers**: Multiple services (`vulnerability-tests`, `scap-data`, etc.) dedicated to managing and updating the security feeds.

## Volumes & Persistence

The configuration uses named volumes to ensure data persistence across container restarts and updates:

- `gvmd_data_vol`: Configuration and scan data.
- `psql_data_vol`: PostgreSQL database files.
- `vt_data_vol`: Vulnerability Test (VT) scripts.
- `scap_data_vol`: SCAP data.
- `cert_data_vol`: CERT data.
- `openvas_log_data_vol`: Scanner logs.

## Troubleshooting

- **Logs:** To view logs for all services: `docker compose logs -f`. To view a specific service: `docker compose logs -f <service_name>`.
- **Feed Sync:** If scans are not working as expected, ensure the feed sync services have completed successfully.
- **Permission Issues:** The scanner requires specific capabilities (`NET_ADMIN`, `NET_RAW`) which are granted in the `docker-compose.yml`.

## License

The Greenbone Community Edition is released under various Open Source licenses (mostly GPL). Please see the individual component repositories for details.
