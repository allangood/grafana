# Grafana dashboard for Graylog
Download dashboard from here:
[https://grafana.com/dashboards/2549](https://grafana.com/dashboards/2549)

This dashboard uses Graylog plugin from Telegraf.

First, create a token to interact with the Graylog API: [http://docs.graylog.org/en/2.2/pages/configuration/rest_api.html](http://docs.graylog.org/en/2.2/pages/configuration/rest_api.html)

Then, create a file "/etc/telegraf/telegraf.d/graylog.conf" with this content:
```
[[inputs.graylog]]
  servers = [
    "https://<YOUR_GRAYLOG_IP_OR_NAME>:9000/api/system/metrics/multiple",
  ]
  metrics = [
    "jvm.threads.count",
    "jvm.memory.total.init",
    "jvm.memory.total.used",
    "org.graylog2.journal.size",
    "org.graylog2.journal.size-limit",
    "org.graylog2.buffers.input.size",
    "org.graylog2.buffers.input.usage",
    "org.graylog2.buffers.output.size",
    "org.graylog2.buffers.output.usage",
    "org.graylog2.buffers.process.size",
    "org.graylog2.buffers.process.usage",
    "org.graylog2.journal.append.1-sec-rate",
    "org.graylog2.journal.utilization-ratio",
    "org.graylog2.throughput.input.1-sec-rate",
    "org.graylog2.throughput.output.1-sec-rate"
  ]
  username = "Your token here"
  password = "token"
  insecure_skip_verify = true
```

Screenshot:
![Graylog Dashboard](https://raw.githubusercontent.com/allangood/grafana/master/assets/Graylog_Dashboard.jpg "Graylog Dashboard")
