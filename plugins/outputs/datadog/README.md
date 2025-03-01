# Datadog Output Plugin

This plugin writes to the [Datadog Metrics API][metrics] and requires an
`apikey` which can be obtained [here][apikey] for the account.

## Configuration

```toml
# Configuration for DataDog API to send metrics to.
[[outputs.datadog]]
  ## Datadog API key
  apikey = "my-secret-key"

  ## Connection timeout.
  # timeout = "5s"

  ## Write URL override; useful for debugging.
  # url = "https://app.datadoghq.com/api/v1/series"

  ## Set http_proxy (telegraf uses the system wide proxy settings if it isn't set)
  # http_proxy_url = "http://localhost:8888"

  ## Override the default (none) compression used to send data.
  ## Supports: "zlib", "none"
  # compression = "none"
```

## Metrics

Datadog metric names are formed by joining the Telegraf metric name and the field
key with a `.` character.

Field values are converted to floating point numbers.  Strings and floats that
cannot be sent over JSON, namely NaN and Inf, are ignored.

[metrics]: https://docs.datadoghq.com/api/v1/metrics/#submit-metrics
[apikey]: https://app.datadoghq.com/account/settings#api
