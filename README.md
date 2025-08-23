# Prometheus exporter template (Python)

This is a template to make a Prometheus exporter project (like [Daydream Watcher](https://github.com/MMK21Hub/daydream-watcher)) using Python and the `prometheus_client` library.

## Using this template

1. On GitHub, click the green "use this template" button in the top-right
2. Pick a repository name and description. For consistency, you should name it `*-watcher` (e.g. `core-watcher`, `daydream-watcher`)
3. Clone and open the repository in your preferred IDE
4. Use your IDE's global find-and-replace feature to replace all occurrences of `anything-watcher` with your chosen project slug
5. Also find-and-replace (match whole word) the port number `9000`, changing it to something custom like `9030`
6. Delete this section and everything above it from the README, and replace it with your own project title and description
7. Search for "TODO" across all files and address them by writing your own code

## Online demo

[![Screenshot of Grafana dashboard stats from the program](screenshot.png)][demo]

**[🌍 View dashboard on grafana.slevel.xyz][demo]** <!-- TODO Replace the below with demo link (Grafana dashboard) -->

[demo]: https://example.com

## Local development

This project uses Python (3.9+) and [uv](https://docs.astral.sh/uv/) for development.

1. Clone the repo
2. `uv run main.py`
3. Head to <http://localhost:9000/metrics> to see the metrics

## Production deployment with Docker Compose

1. Download the example Compose file from [deployment/docker-compose.yml](deployment/docker-compose.yml). Feel free to adjust it to your needs.
2. Start it with `docker-compose up -d`
3. Metrics should now be available at <http://localhost:9000/metrics>

### Example `prometheus.yml` config

Start tracking the metrics by adding Daydream Watcher as a scrape config to a Prometheus-compatible database (e.g. Prometheus, VictoriaMetrics).

```yaml
scrape_configs:
  - job_name: anything-watcher
    scrape_interval: "10s"
    static_configs:
      - targets: ["anything-watcher:9000"]
```

<!-- ### Example Grafana dashboard

Start visualising the metrics by importing the example Grafana dashboard at [deployment/grafana-dashboard.json](deployment/grafana-dashboard.json) into your Grafana instance. -->

## Maintainers: Releasing a new version

Use the `release-new-version.sh` shell script, e.g.

```bash
./release-new-version.sh 0.2.1
```

It will

1. Bump the version in `pyproject.toml`
2. Create and push a Git tag for the new version
3. Build and publish the Docker image to Docker Hub

Then, manually check that the version bump commit is as expected, and `git push` it.
