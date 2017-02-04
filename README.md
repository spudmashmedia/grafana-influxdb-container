# grafana-influxdb-container
Docker-compose script to launch docker grafana + influxdb instances

use this setup to collect instrumentation from JMeter Backend Listener

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

### Clone the repository

Using Kitematic (Docker toolbox), click Docker CLI to open a console which is remoted into your Virtual Box VM with Docker.

In the console, run:
```
  /> docker-compose -f docker-compose.yaml up -d
```

### For Grafana setup

For the datasource
|parameter name|value|
|--|--|
|Name| InfluxJmeter|
|Type|InfluxDB|
|Url|http://192.168.99.100:8086|
|Access|direct|
|Database (this is the name from JMeter BackendListener|jmeter|
|credentials| *non*|
create a new one called "InfluxDBJmeter"



Download and Import the JMeter Load Test dashboard by NovaTec-APM

https://grafana.net/dashboards/1152

During importing of dashboard, use the datasource "InfluxJmeter"


### For JMeter
Download the JMeter Influx writer from:

https://github.com/NovaTecConsulting/JMeter-InfluxDB-Writer/releases

And copy the JMeter-InfluxDB-Writer-plugin.jar file into the lib/ext folder

In the Test Plan:
1) add a Backend Listener

2) In Backend Listener Implementation select "rocks.nt.apm.jmeter.JMeterInfluxDBBackendListenerClient"

3) set the parameters to:

|parameter name|value|
|--|--|
|testName|Test|
|influxDBHost|192.168.99.100|
|influxDBPort|8086|
|influxDBUser|jmeter|
|influxDBPassword||
|influxDBDatabase|jmeter|
|retentionPolicy|autogen|
|samplersList|.*|
|useRegexForSamplerList|true|

4) start the Jmeter test, you should see data in the Grafana dashboard

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