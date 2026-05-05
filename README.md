# monitoring

## Setup

1. Create environment file for Grafana credentials:
	- `cp .env.template .env`
2. Edit `.env` and set a strong `GRAFANA_ADMIN_PASSWORD`.
3. Start the stack:
	- `docker compose up -d`

`connections` > `data sources` > `add data source`  
select `prometheus`  
url `http://prometheus:9090`  

## Nextcloud endpoint monitoring

This stack now includes Blackbox Exporter to probe HTTP availability.

1. Edit `blackbox-targets.yml`.
2. Set your real Nextcloud status endpoint URL:
	- `https://<your-nextcloud-domain>/status.php`
3. Restart monitoring stack:
	- `docker compose up -d`

Prometheus job name: `nextcloud-blackbox`

`dashboards` > `import dashboard`  
node exporter dashboard id `1860`  
docker containers dashboard id `10619`  
