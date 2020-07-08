# replication/peer_volume_groups

### Location
https://{***host-address***}/api/v2/replication/peer_volume_groups

### Supported methods
GET, PATCH, DELETE


### Property types:
 ```text
"capacity_state" : string
"fullname" : string
"id" : int
"local_volume_group" : {
    "ref" : string
},
"logical_capacity" : int
"name" : string
"remote_volume_group_id" : int
"replication_peer_k2array" : {
    "ref" : string
},
"replication_session": {
    "ref" : string
},
"replication_session_id" : int
"snapshots_logical_capacity" : int
"volumes_logical_capacity" : int
 ```

## GET

Example 1:

GET https://{***host-address***}/api/v2/replication/peer_volume_groups
```json
{
  "hits": [
    {
      "capacity_state": "ok",
      "fullname": "d568_Dedup_vg",
      "id": 3,
      "local_volume_group": {
        "ref": "/volume_groups/4501"
      },
      "logical_capacity": 98893080,
      "name": "Dedup_vg",
      "remote_volume_group_id": 4467,
      "replication_peer_k2array": {
        "ref": "/replication/peer_k2arrays/1"
      },
      "replication_session": {
        "ref": "/replication/sessions/3"
      },
      "replication_session_id": 3,
      "snapshots_logical_capacity": 30012444,
      "volumes_logical_capacity": 68880636
    }
],
  "limit": 100,
  "offset": 0,
  "total": 1
}
```

## PATCH

### Properties:
 ```text
Mandatory: 
name
 ```

Example 1:

PATCH https://{***host-address***}/api/v2/replication/peer_volume_groups/{id}

Body:
```json
{
    "name": "peer_vg1"
}
```

## DELETE

Example 1:

DELETE https://{***host-address***}/api/v2/replication/peer_volume_groups/{id}


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
