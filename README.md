## Gitea Deployment with Docker Compose

This guide will help you deploy Gitea using Docker Compose.

### Prerequisites

- [Docker](https://docs.docker.com/get-docker/) installed
- [Docker Compose](https://docs.docker.com/compose/install/) installed

### Before `docker compose up`

Create the necessary directories and set permissions:

```sh
mkdir config data
chown 1000:1000 config/ data/
```

### Copy `env.sample` to `.env` and configure

Copy the sample environment file and edit it as needed. If you are using a custom domain or reverse proxy, adjust the relevant URL settings accordingly.

```sh
cp env.sample .env
# Edit .env to match your environment and proxy/domain settings
```

### Start Gitea

```sh
docker compose up -d
```

### Create an Admin User in the Gitea Container

To create an admin user, first log in to the running Gitea container:

```sh
docker compose exec gitea bash
```

Then run the following command inside the container (replace the values as needed):

```sh
gitea admin user create --username admin --password yourpassword --email admin@example.com --admin
```

After setting up the NGINX proxy, your Gitea instance will be available at [https://example.com/ui/gitea/](https://example.com/ui/gitea/).

See how to set up the proxy: [https://github.com/nginx-proxy/nginx-proxy](https://github.com/nginx-proxy/nginx-proxy)

### Stopping Gitea

```sh
docker compose down
```

### Resource Limits

Gitea can be configured with memory and CPU limits for efficient local development (customize in `docker-compose.yml` as needed).

### Data Persistence

- `./data` stores repositories and application data.
- `./config` stores configuration files.

For more details, see the [Gitea Docker documentation](https://docs.gitea.com/installation/docker).

---

**License:** MIT  
**Author:** [furiatona](https://github.com/furiatona)
