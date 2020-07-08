# volume_groups

### Location
https://{***host-address***}/api/v2/volume_groups

### Supported methods
GET, POST, PATCH, DELETE


## GET

### Property types:
 ```text
"capacity_policy" : string
"capacity_state" : string
"creation_time" : int
"description" : string
"id" : int
"is_dedup" : boolean
"is_default" : boolean
"iscsi_tgt_converted_name" : string
"last_restored_from" : string
"last_restored_time" : string
"last_snapshot_creation_time" : string
"logical_capacity" : int
"mapped_hosts_count" : int
"name" : string
"quota" : int
"replication_peer_volume_group" : string
"replication_rpo_history" : string
"replication_session" :string
"snapshots_count" : int
"snapshots_logical_capacity" : int
"snapshots_overhead_state" : string
"views_count" : int
"volumes_count" : int
"volumes_logical_capacity" : int
"volumes_provisioned_capacity" : int
 ```
Example 1:

GET https://{***host-address***}/api/v2/volume_groups
```json
{
    "capacity_policy": null,
    "capacity_state": "ok",
    "creation_time": 1470296567.234391,
    "description": null,
    "id": 4,
    "is_dedup": false,
    "is_default": false,
    "iscsi_tgt_converted_name": "test.anmir",
    "last_restored_from": null,
    "last_restored_time": null,
    "last_snapshot_creation_time": 1507446023,
    "logical_capacity": 0.0,
    "mapped_hosts_count": 1,
    "name": "test_anmir",
    "quota": null,
    "replication_peer_volume_group": null,
    "replication_rpo_history": null,
    "replication_session": null,
    "snapshots_count": 3,
    "snapshots_logical_capacity": 0,
    "snapshots_overhead_state": "ok",
    "views_count": 0,
    "volumes_count": 8,
    "volumes_logical_capacity": 0,
    "volumes_provisioned_capacity": 21474836480
}
```

## POST

### Property types:
 ```text
Mandatory: 
"name" : string
"quota" : int

Optional: 
"is_dedup" : boolean
"capacity_policy" : string
"description" : string
 ```

Example 1:

POST https://{***host-address***}/api/v2/volume_groups

Body:
```json
{
    "name": "vg2", 
    "quota": "100000000"
}
```

## PATCH

### Property types:
 ```text
First option:
"name" : string
"quota" : int
"capacity_policy" : string
"description" : string

Second option:
"name" : string
"last_restored_from" : int
 ```

Example 1:

PATCH https://{***host-address***}/api/v2/volume_groups/{id}

Body:
```json
{
    "quota": "2000000000"
}
```
```json
{
    "last_restored_from": {
        "ref": "/snapshots/16"
    }
}
```

## DELETE

Example 1:

DELETE https://{***host-address***}/api/v2/volume_groups

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
