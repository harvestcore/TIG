# My custom TIG stack

> _Telegraf_ + _InfluxDB_ + _Grafana_ (not [TIG](https://en.wikipedia.org/wiki/Gas_tungsten_arc_welding)).

## Important note

I'm using a Raspberry Pi 3B to run this stack. There are two inputs in the `telegraf.conf` file used to get the temperature and the frequency of the CPU.

## Before running the stack

1. Rename the `.env.sample` to `.env`, and change the environment variables according to your needs.
2. Take a quick look at the `telegraf.conf` file, as you need to configure some variables according to the ones you just set in step #1.

## Run the stack

```sh
docker-compose up -d
```

## Dashboards

- _InfluxDB_: `<ipaddress>:8086`
- _Grafana_: `<ipaddress>:3000`

## Configure the database in Grafana

1. Access the _Grafana_ dashboard.
2. Go to _Configuration/DataSources_ and add a new one (_InfluxDB_).
3. Make sure the query language is set to _Flux_.
4. Set the _URL_ (`http://influxdb:8086`).
5. Disable _basic auth_.
6. Fill the following fields in the _InfluxDB Details_ section:

- _Organization_: The organization you set in the `.env` file.
- _Token_: The token you set in the `.env` file.
- _Default bucket_: The default bucket you set in the `.env` file.

## Import the dashboard

1. Access the _Grafana_ dashboard.
2. Go to _Dashboards/Import_ and import the `dashboard.json` file.
