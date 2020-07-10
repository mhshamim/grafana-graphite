# grafana-graphite

StatsD + Graphite + Grafana 6.6.2 + Kamon Dashboards
----------------------------------------------------

This image contains a sensible default configuration of StatsD, Graphite and Grafana, and comes bundled with a example
dashboard that gives you the basic metrics currently collected by Kamon for both Actors and Traces.

### Using the Docker Index ###

This image is published under [mshamim's repository on the Docker Hub](https://hub.docker.com/r/mshamim/grafana-graphite) and all you
need as a prerequisite is having `docker`, `docker-compose`, and `make` installed on your machine. The container exposes the following ports:

- `80`: the Grafana web interface.
- `81`: the Graphite web port
- `2003`: the Graphite data port
- `8125`: the StatsD port.
- `8126`: the StatsD administrative port.

To start a container with this image you just need to run the following command:

```bash
$ make up
```

To stop the container
```bash
$ make down
```

To run container's shell
```bash
$ make shell
```

To view the container log
```bash
$ make tail
```

If you already have services running on your host that are using any
of these ports, you may wish to map the container ports to whatever
you want by changing left side number in the `--publish` parameters,
or the 'ports' parameters in 'docker-compose.yml'.

### Using the Dashboards ###

Once your container is running all you need to do is:

- open your browser pointing to http://localhost:80 (or another port if you changed it)
  - Docker with VirtualBox on macOS: use `docker-machine ip` instead of `localhost`
- login with the default username (admin) and password (admin)
- open existing dashboard (or create a new one) and select 'Local Graphite' datasource
- play with the dashboard at your wish...


### Persisted Data ###

When running `make up`, directories are created on your host and mounted into the Docker container, allowing graphite and grafana to persist data and settings between runs of the container.

### Now go explore! ###

We hope that you have a lot of fun with this image and that it serves it's
purpose of making your life easier. This should give you an idea of how the dashboard looks like when receiving data
from one of our messaging applications:
![Kamon Dashboard](http://kamon.io/assets/img/kamon-statsd-grafana.png)


### Credits ###
[Kamon's repository on the Docker Hub](https://hub.docker.com/u/kamon/)
