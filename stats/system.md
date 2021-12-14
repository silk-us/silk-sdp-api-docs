# stats/system

### Location
https://{***host-address***}/api/v2/stats/system

### Supported methods
GET

## Stats-specific modifiers
| Supported Modifiers	| Description | Supported values | Default value |
|-----------------------|------------|----------------|--------------|
|__rw_breakdown	|Provides read/write statistics. |`True`, `False` | `False` |
|__bs_breakdown	|Provides blocksize statistics.| `True`, `False` | `False` |
|__from_time	|Display performance statistics for the specified timestamp in UTC.| Timestamp as a Unix/Epoch time integer | `now` |
|__datapoints	|Show previous performance statistics for number of points specified.| `int` integer less than 1000 | `1` |
|__resolution |Defined time between each iterative performmance statistic. | `5s`, `5m`, `1h`| `5s` |


### Property types:
 ```text
"iops_avg" : int
"iops_max" : int
"latency_inner" : int
"latency_outer" : int
"resolution" : int
"rw" : string
"throughput_avg" : int
"throughput_max" : int
"timestamp" : int
 ```

## GET

Example 1:

GET https://{***host-address***}/api/v2/stats/system
```json
{
  "hits": [
    {
      "iops_avg": 0,
      "iops_max": 0,
      "latency_inner": 0.0,
      "latency_outer": 0.0,
      "resolution": 5,
      "throughput_avg": 0,
      "throughput_max": 0,
      "timestamp": 1635196465
    }
  ],
  "total": 1
}
```

Example 2:

GET https://{***host-address***}/api/v2/stats/system?__bs_breakdown=True
```json
{
  "hits": [
    {
      "bs": "lt8k",
      "iops_avg": 0,
      "latency_inner": 0.0,
      "latency_outer": 0.0,
      "resolution": 5,
      "throughput_avg": 0,
      "timestamp": 1639503010
    },
    {
      "bs": "8k_64k",
      "iops_avg": 81086,
      "latency_inner": 0.44,
      "latency_outer": 0.03,
      "resolution": 5,
      "throughput_avg": 1328506470,
      "timestamp": 1639503010
    },
    {
      "bs": "64k_256k",
      "iops_avg": 0,
      "latency_inner": 0.0,
      "latency_outer": 0.0,
      "resolution": 5,
      "throughput_avg": 0,
      "timestamp": 1639503010
    },
    {
      "bs": "gt256k",
      "iops_avg": 0,
      "latency_inner": 0.0,
      "latency_outer": 0.0,
      "resolution": 5,
      "throughput_avg": 0,
      "timestamp": 1639503010
    }
  ],
  "total": 4
}

```

Example 3:

GET https://{***host-address***}/api/v2/stats/system?__bs_breakdown=True
```json
{
  "hits": [
    {
      "iops_avg": 72650,
      "latency_inner": 0.46,
      "latency_outer": 0.02,
      "resolution": 5,
      "rw": "r",
      "throughput_avg": 1190300877,
      "timestamp": 1639503085
    },
    {
      "iops_avg": 8079,
      "latency_inner": 0.23,
      "latency_outer": 0.12,
      "resolution": 5,
      "rw": "w",
      "throughput_avg": 132366336,
      "timestamp": 1639503085
    }
  ],
  "total": 2
}
```

---

## Global modifiers
| Supported Modifiers	| Description|
|-----------------------|------------|
|__contains	|Field contains the exact string given.|
|__contains_some	|Field contains any substring of a given string.|
|__gt	|Greater than; for numeric fields only.|
|__lt	|Less than; for numeric fields only.|
|__gte	|Greater than-equal; for numeric fields only|
|__lte	|Less than-equal; for numeric fields only|
|__neq	|Field value is not equal to the given string.|
|__in	|Accepts a list of comma-separated values (val1,val2,val3);Matches objects having a related field matching any of these values.|
|__m_eq	|Deprecated. Use __in instead.|
|__prefix	|Field value starts with given string.|
|__regexp	|Field value matches given regular expression.|

## Error responses

| Error Responses	| Description |
|-------------------|-------------|
|400 Bad request	|Client tried to do something that cannot be done.
|401 Unauthorized	|Client tried to access a resource without providing authentication information.
|403 Forbidden	|Client does not have permission to execute the requested action.
|404 Not found	|Client requested resource that does not exist.
|405 Method not allowed	|Client tried to execute an action that is not supported by the resource. For example, DELETE on system capacity policy.
|500 Internal server error	|General error returned by server when it fails to complete the operation for some reason.
|502 Bad Gateway	|K2 REST service became unavailable while performing the request. Client should recheck the state of the object.
|503 Service unavailable	|K2 REST service is busy and cannot execute the requested operation. The client should try again later.
