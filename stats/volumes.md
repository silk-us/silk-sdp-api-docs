# stats/volumes

### Location
https://{***host-address***}/api/v2/stats/volumes

### Supported methods
GET

## Stats-specific modifiers
| Supported Modifiers	| Description | Supported values |
|-----------------------|------------|----------------|
|__rw_breakdown	|Provides read/write statistics.|`True`|
|__bs_breakdown	|Provides blocksize statistics.|`True`|

### Property types:
 ```text
"iops_avg" : int
"iops_max" : int
"latency_inner" : int
"latency_outer" : int
"peer_k2_name" : string
"resolution" : int
"rw" : string
"throughput_avg" : int
"throughput_max" : int
"timestamp" : int
"volume": "{
    ref : string
}"
"volume_name" : string
 ```

## GET

Example 1:  
* This example gathers global volume stats.
```
GET https://{host-address}/api/v2/stats/volumes
```
```json
{
  "hits": [
    {
      "iops_avg": 20370,
      "iops_max": 20483,
      "latency_inner": 0.43,
      "latency_outer": 0.03,
      "peer_k2_name": "K2-6310",
      "resolution": 5,
      "throughput_avg": 333742080,
      "throughput_max": 335593472,
      "timestamp": 1639503680,
      "volume": {
        "ref": "/volumes/5"
      },
      "volume_name": "centos-vol1"
    }
  ],
  "total": 1
}

```

Example 2:
* This example gathers global volume stats with read and write stats seperated.
```
GET https://{host-address}/api/v2/stats/volumes?__rw_breakdown=True
```
```json
{
  "hits": [
    {
      "iops_avg": 18024,
      "latency_inner": 0.46,
      "latency_outer": 0.02,
      "peer_k2_name": "K2-6310",
      "resolution": 5,
      "rw": "r",
      "throughput_avg": 295311770,
      "timestamp": 1639503525,
      "volume": {
        "ref": "/volumes/5"
      },
      "volume_name": "centos-vol1"
    },
    {
      "iops_avg": 2016,
      "latency_inner": 0.22,
      "latency_outer": 0.11,
      "peer_k2_name": "K2-6310",
      "resolution": 5,
      "rw": "w",
      "throughput_avg": 33030144,
      "timestamp": 1639503525,
      "volume": {
        "ref": "/volumes/5"
      },
      "volume_name": "centos-vol1"
    }
  ],
  "total": 2
}

```

Example 3:
* This example gathers a specific volume's stats with block size stats seperated.
```
GET https://{host-address}/api/v2/stats/volumes/5?__bs_breakdown=True
```
```json
{
  "hits": [
    {
      "bs": "lt8k",
      "iops_avg": 0,
      "latency_inner": 0.0,
      "latency_outer": 0.0,
      "peer_k2_name": "K2-6310",
      "resolution": 5,
      "throughput_avg": 0,
      "timestamp": 1639503605,
      "volume": {
        "ref": "/volumes/5"
      },
      "volume_name": "centos-vol1"
    },
    {
      "bs": "8k_64k",
      "iops_avg": 20190,
      "latency_inner": 0.44,
      "latency_outer": 0.03,
      "peer_k2_name": "K2-6310",
      "resolution": 5,
      "throughput_avg": 330792960,
      "timestamp": 1639503605,
      "volume": {
        "ref": "/volumes/5"
      },
      "volume_name": "centos-vol1"
    },
    {
      "bs": "64k_256k",
      "iops_avg": 0,
      "latency_inner": 0.0,
      "latency_outer": 0.0,
      "peer_k2_name": "K2-6310",
      "resolution": 5,
      "throughput_avg": 0,
      "timestamp": 1639503605,
      "volume": {
        "ref": "/volumes/5"
      },
      "volume_name": "centos-vol1"
    },
    {
      "bs": "gt256k",
      "iops_avg": 0,
      "latency_inner": 0.0,
      "latency_outer": 0.0,
      "peer_k2_name": "K2-6310",
      "resolution": 5,
      "throughput_avg": 0,
      "timestamp": 1639503605,
      "volume": {
        "ref": "/volumes/5"
      },
      "volume_name": "centos-vol1"
    }
  ],
  "total": 4
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
