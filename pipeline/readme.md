## 1

* custom-pipeline-wildfly-02
* 
```
[
  {
    "dissect": {
      "field": "message",
      "pattern": "%{+timestamp} %{+timestamp} %{level} %{?data4} %{formatter} %{message}",
      "append_separator": " "
    }
  },
  {
    "date": {
      "field": "timestamp",
      "formats": [
        "yyyy-MM-dd HH:mm:ss,SSS"
      ],
      "timezone": "UTC"
    }
  }
]
```
