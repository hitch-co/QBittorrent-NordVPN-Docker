# QBittorrent-NordVPN-Docker Setup

# Source Image Documentation
- [NordLynx](https://github.com/bubuntux/nordlynx)
    see the source image documentation for more information on the NordLynx image and running multiple containers with the same network
- [qBittorrent](https://github.com/linuxserver/docker-qbittorrent)

This repository contains Docker Compose files to set up and run qBittorrent through NordVPN using Docker.

## Overview

The setup includes two main services:
1. **NordVPN**: A container running the NordVPN client, configured to connect to a server in Switzerland using the NordLynx technology.
2. **qBittorrent**: A torrent client container configured to route its traffic through the NordVPN container.

## Prerequisites

- Docker and Docker Compose installed on your system.
- A NordVPN subscription and a generated token for authentication.

## Configuration

Before starting, you need to create an `.env` file in the root of this project with your NordVPN token:

```env
NORDVPN_TOKEN=<Your_NordVPN_Token_Here>
QBIT_CONFIG_FOLDERPATH="C:/your/path/to/config/folder"
QBIT_DOWNLOAD_FOLDERPATH="C:/your/path/to/downloads/folder"
```

**Note**: The `.env` file is excluded from this repository for security reasons.

## Usage

To start the services, run the following command from the directory containing your docker compose file:

```bash
docker-compose up -d
```

```cmd
docker compose -f 'docker-compose-file.yml' up -d
```

This command will start the NordVPN and qBittorrent containers in detached mode.

## Accessing qBittorrent

The qBittorrent web interface will be available at `http://localhost:8080`. The default credentials are `admin` for the username and the terminal will indicate a temporary password for the password. It is highly recommended to change these upon first login.

## Ports

The following ports are exposed:

- `8080` for the qBittorrent web interface.
- `6881` for torrenting (TCP/UDP).

## Stopping the Services

To stop and remove the containers, you can use the following command:

```bash
docker-compose down
```

## Support and Contributions

For issues, suggestions, or contributions, please open an issue or pull request in this repository.

## Disclaimer

This setup is provided as-is without any guarantees. Make sure to comply with the NordVPN Terms of Service and respect copyright laws when using qBittorrent.
