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

Gitea will be available at [http://localhost:3000](http://localhost:3000).

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
