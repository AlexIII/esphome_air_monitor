# ESPHome(esphome.io)-based Air Monitor

## Hardware

- nodemcu-32s
- MH-Z19 (indoor) (UART0)
- BME680 (outdoor) (I2C)
- DHT-11 (indoor) (GPIO23)
- MQ-135 (outdoor) (A0)
  - Replace 1k pull-up sensor resistor with 4.7k resistor
- Ext voltage (5V) sensor (A3)
  - Use 1/2 resistor voltage divider (4.7k + 4.7k) + 0.1uF cap
- Button (GPIO14) to ground - reset MQ-135 to 100ppm

## Grafana

Create Grafana stack with Prometheus, use Telegraf API for metrics submission.

https://grafana.com/docs/grafana-cloud/send-data/metrics/metrics-influxdb/push-from-telegraf/

The url will be something like this
`https://influx-prod-24-prod-eu-west-2.grafana.net/api/v1/push/influx/write`
(even though it says 'influx' we're actually pushing to Prometheus)

## Settings

See `esphome_air_monitor.yaml`

Update:
- substitutions
- wifi: ssid, password, manual_ip

## Build/flash


`esphome run esphome_air_monitor.yaml --device 192.168.0.115`
