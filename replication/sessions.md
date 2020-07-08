# replication/sessions

### Location
https://{***host-address***}/api/v2/replication/sessions

### Supported methods
GET, POST, PATCH, DELETE


### Property types:
 ```text
"common_snapshots_count" : int
"current_role" : string
"current_snapshot" : string
"current_snapshot_progress" : int
"estimated_remaining_time" : int
"external_retention_policy" : {
    "ref" : string
},
"id" : 2,
"latest_replicated_snapshot" : {
    "ref" : string
},
"local_volume_group" : {
    "ref" : string
},
"name" : string
"next_snapshot" : string
"primary" : boolean
"remote_replication_session_id" : int
"remote_replication_session_name" : string
"replication_peer_k2array" : {
    "ref" : string
},
"replication_peer_volume_group" : {
    "ref" : string
},
"replication_rpo_history" : {
    "ref" : string
},
"restored_snapshot" : string
"retention_policy" : {
    "ref" : string
},
"rpo" : int
"state" : string
"stopped" : boolean
"suspend_reason" : string
"suspend_reason_code" : string
"target_exposure" : string
 ```

## GET

Example 1:

GET https://{***host-address***}/api/v2/replication/sessions
```json
{
  "hits": [
    {
      "common_snapshots_count": 4,
      "current_role": "target",
      "current_snapshot": null,
      "current_snapshot_progress": 0,
      "estimated_remaining_time": null,
      "external_retention_policy": {
        "ref": "/retention_policies/6"
      },
      "id": 2,
      "latest_replicated_snapshot": {
        "ref": "/snapshots/428"
      },
      "local_volume_group": {
        "ref": "/volume_groups/8"
      },
      "name": "remote_kcs572_session_ATF-VG-1",
      "next_snapshot": null,
      "primary": false,
      "remote_replication_session_id": 2,
      "remote_replication_session_name": "kcs572_session_ATF-VG-1",
      "replication_peer_k2array": {
        "ref": "/replication/peer_k2arrays/1"
      },
      "replication_peer_volume_group": {
        "ref": "/replication/peer_volume_groups/2"
      },
      "replication_rpo_history": {
        "ref": "/replication/rpo_history/2"
      },
      "restored_snapshot": null,
      "retention_policy": {
        "ref": "/retention_policies/5"
      },
      "rpo": 300,
      "state": "in_sync",
      "stopped": false,
      "suspend_reason": "",
      "suspend_reason_code": "none",
      "target_exposure": "unmapped"
    }
    ],
  "limit": 100,
  "offset": 0,
  "total": 4
}
```

## POST

### Properties:
 ```text
Mandatory: 
replication_peer_k2array
local_volume_group
rpo
retention_policy
external_retention_policy
name

Optional: 
replication_peer_volume_group_name
remote_replication_session_name
auto_configure_peer_volumes
target_exposure
 ```

Example 1:

POST https://{***host-address***}/api/v2/replication/sessions

Body:
```json
{
    "replication_peer_k2array": {
        "ref": "/replication/peer_k2arrays/1"
    }, 
    "local_volume_group": {
        "ref": "/volume_groups/5101"
    }, 
    "rpo": "1200", 
    "name": "test_src", 
    "retention_policy": {
        "ref": "/retention_policies/5"
    }, 
    "external_retention_policy": {
        "ref": "/retention_policies/6"
    }
}

```

## PATCH

### Properties:
 ```text
Option 1:
Mandatory: 
name
state

Optional: 
snapshot_wwn
offline_initial_sync
```
```text
Option 2:
Mandatory: 
name

Optional: 
rpo
retention_policy
external_retention_policy
target_exposure
 ```

Example 1:

PATCH https://{***host-address***}/api/v2/replication/sessions/{id}

Body:
```json
{
    "name": "test_src", 
    "state": "in_sync"
}
```

## DELETE

Example 1:

DELETE https://{***host-address***}/api/v2/replication/sessions/{id}


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
