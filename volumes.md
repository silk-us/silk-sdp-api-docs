# volumes

### Location
https://{***host-address***}/api/v2/volumes

### Supported methods
GET, POST, PATCH, DELETE

### Property types:
 ```text
"avg_compressed_ratio" : int
"avg_compressed_ratio_timestamp" : int
"creation_time" : int
"current_replication_stats" : {
    "ref" : string
},
"current_stats" : {
    "ref" :string
},
"dedup_source" : int
"dedup_target" : int
"description" : string
"id" : int
"is_dedup" : boolean
"is_new" : boolean
"iscsi_tgt_converted_name" : string
"last_restored_from" : int
"last_restored_time" : int
"logical_capacity" : int
"marked_for_deletion" : boolean
"name" : string
"no_dedup" : int
"node_id" : int
"read_only" : boolean
"replication_peer_volume" : {
    "ref" : string
},
"scsi_sn" : string
"scsi_suffix" : int
"size" : int
"snapshots_logical_capacity" : int
"stream_avg_compressed_size_in_bytes" : int
"vmware_support" : boolean
"volume_group" : {
"ref" : string
}
 ```

## GET

Example 1:

GET https://{***host-address***}/api/v2/volumes
```json
{
  "hits": [
   {
     "avg_compressed_ratio": null,
     "avg_compressed_ratio_timestamp": 0.0,
     "creation_time": 1695658216,
     "current_replication_stats": null,
     "current_stats": {
       "ref": "/stats/volumes/8"
     },
     "description": null,
     "id": 8,
     "is_dedup": false,
     "is_new": false,
     "iscsi_tgt_converted_name": "test-vm-vol-4",
     "last_restored_from": null,
     "last_restored_time": null,
     "logical_capacity": 0.0,
     "marked_for_deletion": false,
     "name": "test-vm-vol-4",
     "node_id": 5,
     "read_only": false,
     "scsi_sn": "1072470004",
     "scsi_suffix": 4,
     "size": 209715200,
     "snapshots_logical_capacity": 0,
     "stream_avg_compressed_size_in_bytes": 0.0,
     "vmware_support": false,
     "volume_group": {
       "ref": "/volume_groups/4"
     }
   }
  ],
  "limit": 100,
  "offset": 0,
  "total": 9
}
```

## POST

### Properties:
 ```text
Mandatory: 
name, 
size, 
volume_group

Optional: 
vmware_support, 
description, 
read_only
 ```

Example 1:

POST https://{***host-address***}/api/v2/volumes

Body:
```json
{
    "name": "vol1",
    "volume_group": {
        "ref": "/volume_groups/14"
    }, 
    "size": "10000000000"
}
```

## PATCH

### Properties:
 ```text
First option:
name
size
description
volume_group (to move volume between volume groups)
read_only
 ```

Example 1:

PATCH https://{***host-address***}/api/v2/volumes/{id}

Body:
```json
{
    "size": "11000000000"
}
```

Example 2:

PATCH https://{***host-address***}/api/v2/volumes/{id}
Body:
```json
{
    "avg_compressed_ratio_timestamp": 0
}
```

## DELETE

Example 1:

DELETE https://{***host-address***}/api/v2/volumes/{id}


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
