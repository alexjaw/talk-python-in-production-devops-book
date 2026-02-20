# Containers

Base images, core app, and web server containers for the example setup.

## Base images and timezone (TZ)

The `linuxbase` image accepts a **TZ** build argument so you can set the container timezone (default: `UTC`). Use it if you want logs and in-container time in your local zone (e.g. `Europe/Helsinki`); omit it to keep the default.

### With Docker Compose

From `base-images/`:

```bash
cd base-images

# Default (UTC)
docker compose build

# Override with environment variable
TZ=Europe/Helsinki docker compose build
```

Or set `TZ` in a `.env` file next to `compose.yaml`, then run `docker compose build` as usual.

### With plain Docker build

From this directory (`containers/`):

```bash
# Default
docker build -t linux-example-base base-images/linuxbase

# Override with --build-arg
docker build --build-arg TZ=Europe/Helsinki -t linux-example-base base-images/linuxbase
```

Use any valid [tz database](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones) name (e.g. `UTC`, `Europe/Helsinki`, `America/New_York`).
