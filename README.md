# grafana-influxdb-container
Docker-compose script to launch docker grafana + influxdb instances

use this setup to collect instrumentation from JMeter Backend Listener (Graphite)

## Requirements
Please install

1) Docker Toolbox
```
https://www.docker.com/products/docker-toolbox
```
2) Docker-Compose
```
https://docs.docker.com/compose/
```

## Installation

Clone the repository

Using Kitematic (Docker toolbox), click Docker CLI to open a console which is remoted into your Virtual Box VM with Docker.

In the console, run:
```
  /> docker-compose -f docker-compose.yaml up -d
```

For JMeter,
1) add a Backend Listener

2) set the parameters to:

|parameter name|value|
|--|--|
|graphiteHost|192.168.99.100|
|graphitePort|2003|
|rootMetricsPrefix|jmeter.|
|summaryOnly|false|
|samplersList|.*|
|useRegexpForSamplersList|false|
|percentiles|90;95;99|

3) run a quick test to populate influxdb

4) in Influx DB, a new database called "graphite" should be created (this is your Graphite datasource)


## Contributing
1. Fork it!
2. Create your feature branch: `git checkout -b my-new-feature`
3. Commit your changes: `git commit -am 'Add some feature'`
4. Push to the branch: `git push origin my-new-feature`
5. Submit a pull request :D

## History
- V1



## License
MIT