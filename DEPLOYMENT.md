# MW-STORAGE deployment

This repository is based on RustFS. The deployment below runs a **single-node object-storage service** using the upstream RustFS container image. It is a practical starting point, not a claim of multi-node high availability or production certification.

## Requirements

- A Linux host with Docker Engine and the Docker Compose plugin.
- Persistent disk space for object data and logs.
- A TLS reverse proxy (for example, Caddy, Nginx, or Traefik) if the service will be accessed remotely.
- A reviewed RustFS image version. For production, pin `RUSTFS_IMAGE` to a release tag or immutable image digest rather than tracking `latest`.

## Configure

From the repository root:

```sh
cp deploy/mw-storage/.env.example deploy/mw-storage/.env
```

Edit `deploy/mw-storage/.env` and replace both credential placeholders with unique, high-entropy values. Do not commit this file. Set `RUSTFS_IMAGE` to the exact RustFS release you have reviewed, and set `RUSTFS_CONSOLE_CORS_ALLOWED_ORIGINS` to the exact origin from which administrators will open the console.

The Compose file binds the S3 API and console to `127.0.0.1` on the host. They are therefore not directly exposed to the public network. Configure your TLS reverse proxy to reach the local ports. Do not change the bindings to `0.0.0.0` unless you have deliberately designed and secured the network boundary.

## Start and verify

```sh
docker compose --env-file deploy/mw-storage/.env -f deploy/mw-storage/compose.yaml config
docker compose --env-file deploy/mw-storage/.env -f deploy/mw-storage/compose.yaml pull
docker compose --env-file deploy/mw-storage/.env -f deploy/mw-storage/compose.yaml up -d
docker compose --env-file deploy/mw-storage/.env -f deploy/mw-storage/compose.yaml ps
docker compose --env-file deploy/mw-storage/.env -f deploy/mw-storage/compose.yaml logs -f
```

The S3 API is available locally at `http://127.0.0.1:9000`; the administration console is at `http://127.0.0.1:9001`. Use the TLS reverse proxy hostname for remote access. Confirm the container reports healthy before connecting clients.

## Data and backups

The named volumes `mw_storage_data` and `mw_storage_logs` persist across container replacement. Back up the data volume using a storage-consistent procedure and test restores regularly. A Docker volume is persistence, not a backup. Keep backup copies off-host and protect them with separate access controls.

## Before production

- Pin and record the exact image version/digest; do not deploy an unreviewed `latest` image.
- Configure TLS at the reverse proxy and restrict console access to trusted administrators or a VPN.
- Store credentials in a secret manager where available; restrict access to the env file and never commit it.
- Set CORS to the exact console origin; do not use `*` by default.
- Monitor disk capacity, service health, logs, and host security updates.
- Test upload, download, deletion, authentication, restart recovery, backup, and restore with non-critical data first.
- For multi-node availability, erasure coding, replication, or production durability guarantees, design and test the topology against the upstream RustFS documentation. This single-node Compose file does not provide those guarantees.

## Stop

```sh
docker compose --env-file deploy/mw-storage/.env -f deploy/mw-storage/compose.yaml down
```

Do not add `-v` unless you intentionally want to delete the named data and log volumes.
