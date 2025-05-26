# IoT-Plattform

<a id="readme-top"></a>

## About The Project

This IoT platform is an extension of the [IoTCountingApp](https://github.com/OrhanSalman/IoTCountingApp). The platform contains:

- **Traefik + LE** as reverse proxy and Let's encrypt for certificates
- **WireGuard** for IP-based protection on critical routes
- **Keycloak + PostgreSQL** as identity and access management system
- **HiveMQ** as MQTT broker
- **InfluxDB** as time series based database
- **Telegraf** MQTT client plugin in InfluxDB to automatically write payloads to Influx
- **Grafana** for building dashboards

## Imports

- The repository contains a realm including a client. Only a user account needs to be created with credentials.
- InfluxDB is already stored as a data source in Grafana
- Telegraf is preconfigured and is based on the topics and payloads of the IoTCountingApp
- HiveMQ has client access with **admin-user** and **admin-password** as credentials. Additional users can be created in credentials.xml or via the Control Center.

### Installation

1. Create the specific network with

```bash
docker network create traefik-network
docker network create mqtt-telegraf-network
```

2. Run `docker compose up -d`
3. Open your keycloak instance `http://10.13.13.7:8082/admin` and create a new user in your realm. By default, the admin interface can only be accessed via the VPN or your IP in `ALLOWED_IP`.

---

This project is only a demonstration. It can include bugs and mistakes. Do not use it in production environments.
