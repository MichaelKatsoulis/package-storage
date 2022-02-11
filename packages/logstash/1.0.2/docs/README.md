# Logstash

The `logstash` package collects metrics and logs of Logstash.

## Compatibility

The `logstash` package works with Logstash 7.3.0 and later

## Logs

Logstash package supports the plain text format and the JSON format. Also, two types of 
logs can be activated with the Logstash package:

* `log` collects and parses the logs that Logstash writes to disk.
* `slowlog` parses the logstash slowlog (make sure to configure the Logstash slowlog option).

#### Known issues

When using the `log` data stream to parse plaintext logs, if a multiline plaintext log contains an embedded JSON object such that
the JSON object starts on a new line, the fileset may not parse the multiline plaintext log event correctly.


## Metrics

Logstash metric related data streams works with Logstash 7.3.0 and later.

### Node Stats

An example event for `node_stats` looks as following:

```json
{
    "agent": {
        "hostname": "docker-fleet-agent",
        "name": "docker-fleet-agent",
        "id": "0c223a58-fac1-457d-84d2-13b4cc188cd8",
        "type": "metricbeat",
        "ephemeral_id": "14484f41-a26f-44c9-adf0-fc0f1495b4f3",
        "version": "7.15.0"
    },
    "elastic_agent": {
        "id": "0c223a58-fac1-457d-84d2-13b4cc188cd8",
        "version": "7.15.0",
        "snapshot": true
    },
    "logstash": {
        "node": {
            "stats": {
                "events": {
                    "filtered": 0,
                    "in": 0,
                    "out": 0
                }
            }
        }
    },
    "@timestamp": "2021-09-02T17:29:14.596Z",
    "ecs": {
        "version": "1.10.0"
    },
    "data_stream": {
        "namespace": "default",
        "type": "metrics",
        "dataset": "logstash.node_stats"
    },
    "service": {
        "hostname": "45943bf17069",
        "address": "http://logstash:9600/_node/stats",
        "name": "logstash",
        "id": "8cfe1a39-ac50-439d-8bf2-93198aa26c0d",
        "type": "logstash",
        "version": "8.0.0"
    },
    "host": {
        "hostname": "docker-fleet-agent",
        "os": {
            "kernel": "5.11.10-arch1-1",
            "codename": "Core",
            "name": "CentOS Linux",
            "type": "linux",
            "family": "redhat",
            "version": "7 (Core)",
            "platform": "centos"
        },
        "containerized": true,
        "ip": [
            "172.25.0.4"
        ],
        "name": "docker-fleet-agent",
        "id": "1292624d19b2cee1a317ad634c9a8358",
        "mac": [
            "02:42:ac:19:00:04"
        ],
        "architecture": "x86_64"
    },
    "metricset": {
        "period": 10000,
        "name": "node_stats"
    },
    "event": {
        "duration": 18621194,
        "agent_id_status": "verified",
        "ingested": "2021-09-02T17:29:15.608149964Z",
        "module": "logstash",
        "dataset": "logstash.node_stats"
    }
}
```

**Exported fields**

| Field | Description | Type |
|---|---|---|
| @timestamp | Date/time when the event originated. This is the date/time extracted from the event, typically representing when the event was generated by the source. If the event source has no original timestamp, this value is typically populated by the first time the event was received by the pipeline. Required field for all events. | date |
| data_stream.dataset | Data stream dataset. | constant_keyword |
| data_stream.namespace | Data stream namespace. | constant_keyword |
| data_stream.type | Data stream type. | constant_keyword |
| host.hostname | Hostname of the host. It normally contains what the `hostname` command returns on the host machine. | keyword |
| logstash.node.jvm.version | Version | keyword |
| logstash.node.state.pipeline.hash |  | keyword |
| logstash.node.state.pipeline.id |  | keyword |
| logstash.node.stats.events.duration_in_millis |  | long |
| logstash.node.stats.events.filtered | Filtered events counter. | long |
| logstash.node.stats.events.in | Incoming events counter. | long |
| logstash.node.stats.events.out | Outgoing events counter. | long |
| logstash.node.stats.jvm.mem.heap_max_in_bytes |  | long |
| logstash.node.stats.jvm.mem.heap_used_in_bytes |  | long |
| logstash.node.stats.jvm.uptime_in_millis |  | long |
| logstash.node.stats.logstash.uuid |  | keyword |
| logstash.node.stats.logstash.version |  | keyword |
| logstash.node.stats.os.cgroup.cpu.stat.number_of_elapsed_periods |  | long |
| logstash.node.stats.os.cgroup.cpu.stat.number_of_times_throttled |  | long |
| logstash.node.stats.os.cgroup.cpu.stat.time_throttled_nanos |  | long |
| logstash.node.stats.os.cgroup.cpuacct.usage_nanos |  | long |
| logstash.node.stats.os.cpu.load_average.15m |  | long |
| logstash.node.stats.os.cpu.load_average.1m |  | long |
| logstash.node.stats.os.cpu.load_average.5m |  | long |
| logstash.node.stats.pipelines.events.duration_in_millis |  | long |
| logstash.node.stats.pipelines.events.out |  | long |
| logstash.node.stats.pipelines.hash |  | keyword |
| logstash.node.stats.pipelines.id |  | keyword |
| logstash.node.stats.pipelines.queue.events_count |  | long |
| logstash.node.stats.pipelines.queue.max_queue_size_in_bytes |  | long |
| logstash.node.stats.pipelines.queue.queue_size_in_bytes |  | long |
| logstash.node.stats.pipelines.queue.type |  | keyword |
| logstash.node.stats.pipelines.vertices.duration_in_millis |  | long |
| logstash.node.stats.pipelines.vertices.events_in |  | long |
| logstash.node.stats.pipelines.vertices.events_out | events_out | long |
| logstash.node.stats.pipelines.vertices.id | id | keyword |
| logstash.node.stats.pipelines.vertices.pipeline_ephemeral_id | pipeline_ephemeral_id | keyword |
| logstash.node.stats.pipelines.vertices.queue_push_duration_in_millis | queue_push_duration_in_millis | float |
| logstash.node.stats.process.cpu.percent |  | double |
| logstash.node.stats.queue.events_count |  | long |
| logstash_stats.pipelines |  | nested |
| process.pid | Process id. | long |
| service.version | Version of the service the data was collected from. This allows to look at a data set only for a specific version of a service. | keyword |

### Node

An example event for `node` looks as following:

```json
{
    "process": {
        "pid": 1
    },
    "agent": {
        "hostname": "docker-fleet-agent",
        "name": "docker-fleet-agent",
        "id": "0c223a58-fac1-457d-84d2-13b4cc188cd8",
        "ephemeral_id": "14484f41-a26f-44c9-adf0-fc0f1495b4f3",
        "type": "metricbeat",
        "version": "7.15.0"
    },
    "elastic_agent": {
        "id": "0c223a58-fac1-457d-84d2-13b4cc188cd8",
        "version": "7.15.0",
        "snapshot": true
    },
    "logstash": {
        "node": {
            "host": "2cb47f6e0eab",
            "version": "8.0.0",
            "jvm": {
                "version": "11.0.5"
            },
            "id": "4cc683ce-3ddc-46e3-bea3-aefbf37bc082",
            "state": {
                "pipeline": {
                    "hash": "3000c3abf87d4dfa4a57aaf6af0a1f5bee2e0fc1c48a8e8636e2a33d7d2e91dd",
                    "ephemeral_id": "afb1a50a-95f0-484a-b7d7-e683ddddc75a",
                    "representation": {
                        "graph": {
                            "edges": [
                                {
                                    "from": "1bf3a9cc73ceb7c3a9cbe885df249b23f3496c52a342a6d513153cc865d78182",
                                    "id": "b3db599ec6ae0b9493158bd7024dcd922c8a3e76295c37fef0da440086bf3f8c",
                                    "to": "__QUEUE__",
                                    "type": "plain"
                                },
                                {
                                    "type": "plain",
                                    "from": "71b91bc85b66ab25c5fb16e63db4dd7111c183f96d1f18e19078051ed5fc74f7",
                                    "id": "9db20a77b3e1eb91229a50bd33388425d59725f9093e076a37e6565f8d5a20ad",
                                    "to": "__QUEUE__"
                                },
                                {
                                    "id": "9b2bc571e978746fb9b55b83521a6603c3c940144cde0e3f4296298cea6585cf",
                                    "to": "a339cb309b29181703c6adf321da3d639f5b60713de5a1e5519ebfea069556d8",
                                    "type": "plain",
                                    "from": "__QUEUE__"
                                }
                            ],
                            "vertices": [
                                {
                                    "config_name": "beats",
                                    "explicit_id": false,
                                    "id": "1bf3a9cc73ceb7c3a9cbe885df249b23f3496c52a342a6d513153cc865d78182",
                                    "meta": {
                                        "source": {
                                            "line": 2,
                                            "protocol": "file",
                                            "column": 3,
                                            "id": "/usr/share/logstash/pipeline/default.conf"
                                        }
                                    },
                                    "plugin_type": "input",
                                    "type": "plugin"
                                },
                                {
                                    "plugin_type": "input",
                                    "type": "plugin",
                                    "config_name": "beats",
                                    "explicit_id": false,
                                    "id": "71b91bc85b66ab25c5fb16e63db4dd7111c183f96d1f18e19078051ed5fc74f7",
                                    "meta": {
                                        "source": {
                                            "protocol": "file",
                                            "column": 3,
                                            "id": "/usr/share/logstash/pipeline/default.conf",
                                            "line": 7
                                        }
                                    }
                                },
                                {
                                    "explicit_id": false,
                                    "id": "__QUEUE__",
                                    "meta": null,
                                    "type": "queue"
                                },
                                {
                                    "config_name": "elasticsearch",
                                    "explicit_id": false,
                                    "id": "a339cb309b29181703c6adf321da3d639f5b60713de5a1e5519ebfea069556d8",
                                    "meta": {
                                        "source": {
                                            "id": "/usr/share/logstash/pipeline/default.conf",
                                            "line": 17,
                                            "protocol": "file",
                                            "column": 3
                                        }
                                    },
                                    "plugin_type": "output",
                                    "type": "plugin"
                                }
                            ]
                        },
                        "type": "lir",
                        "version": "0.0.0",
                        "hash": "3000c3abf87d4dfa4a57aaf6af0a1f5bee2e0fc1c48a8e8636e2a33d7d2e91dd"
                    },
                    "batch_size": 125,
                    "workers": 12,
                    "id": "main"
                }
            }
        }
    },
    "@timestamp": "2021-09-02T17:31:04.592Z",
    "ecs": {
        "version": "1.10.0"
    },
    "data_stream": {
        "namespace": "default",
        "type": "metrics",
        "dataset": "logstash.node"
    },
    "service": {
        "hostname": "45943bf17069",
        "address": "http://logstash:9600/_node",
        "name": "logstash",
        "id": "8cfe1a39-ac50-439d-8bf2-93198aa26c0d",
        "type": "logstash",
        "version": "8.0.0"
    },
    "host": {
        "hostname": "docker-fleet-agent",
        "os": {
            "kernel": "5.11.10-arch1-1",
            "codename": "Core",
            "name": "CentOS Linux",
            "family": "redhat",
            "type": "linux",
            "version": "7 (Core)",
            "platform": "centos"
        },
        "ip": [
            "172.25.0.4"
        ],
        "containerized": true,
        "name": "docker-fleet-agent",
        "id": "1292624d19b2cee1a317ad634c9a8358",
        "mac": [
            "02:42:ac:19:00:04"
        ],
        "architecture": "x86_64"
    },
    "metricset": {
        "period": 10000,
        "name": "node"
    },
    "event": {
        "duration": 13519531,
        "agent_id_status": "verified",
        "ingested": "2021-09-02T17:31:05.607256453Z",
        "module": "logstash",
        "dataset": "logstash.node"
    }
}
```