# replication/stats

### Location
https://{***host-address***}/api/v2/replication/stats

### Supported verbs
GET, POST, PATCH, DELETE

### Property types:
 ```text
  "logical_in" : int
  "logical_out" : int
  "peer_k2_name" : string
  "physical_in" : int
  "physical_out" : int
  "resolution" : int
  "timestamp" : int
  "volume" : array 
    "ref" : string
  "volume_name" : string
 ```

## GET
Example 1:

GET https://{***host-address***}/api/v2/replication/stats
```json
{
  "logical_in": 0,
  "logical_out": 0,
  "peer_k2_name": null,
  "physical_in": 0,
  "physical_out": 0,
  "resolution": 5,
  "timestamp": 1579801960,
  "volume": {
    "ref": "/volumes/158497"
  },
  "volume_name": "Splunk02"
}
```

## POST

Example 1:

POST https://{***host-address***}/api/v2/replication/stats
```json
{

}
```

## PATCH

Example 1:

PATCH https://{***host-address***}/api/v2/replication/stats
```json
{

}
```

## DELETE

Example 1:

DELETE https://{***host-address***}/api/v2/replication/stats
```json
{

}
```


