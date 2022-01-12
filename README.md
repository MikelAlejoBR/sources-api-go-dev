# Sources API Go Development tools

[Main repository — Sources API Go](https://github.com/RedHatInsights/sources-api-go)

In order to run the services this application will connect to, a `docker-compose.yml` file is provided. This will
launch the Redis cache, the database, a Red Hat Marketplace fake server and a Vault server in development mode. The
steps to have a working development environment are:

1. `docker-compose up`
2. Go to the `sources-api` repository and migrate the database.
   1. `bundle exec rake db:migrate`
   2. `bundle exec rake db:seed`
3. Export the minimum required environment variables. You can modify some of them by modifying the `.env` file:

```bash
#!/usr/bin/bash

export BYPASS_RBAC=true
export DATABASE_HOST=localhost
export DATABASE_NAME=sources_api_development
export DATABASE_PASSWORD=toor
export DATABASE_PORT=5432
export DATABASE_USER=root
export MARKETPLACE_HOST=http://localhost:3000
export REDIS_CACHE_HOST=localhost
export REDIS_CACHE_PORT=6379
export VAULT_ADDR=http://0.0.0.0:8200
export VAULT_TOKEN=root
```
