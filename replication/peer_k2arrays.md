# replication/peer_k2arrays

### Location
https://{***host-address***}/api/v2/replication/peer_k2arrays

### Supported methods
GET, POST, PATCH, DELETE


### Property types:
 ```text
"bandwidth_limit" : int
"capacity_allocated" : int
"capacity_allocated_snapshots_and_views" : int
"capacity_allocated_volumes" : int
"capacity_free" : int
"capacity_physical" : int
"capacity_provisioned" : int
"capacity_provisioned_snapshots" : int
"capacity_provisioned_views" : int
"capacity_provisioned_volumes" : int
"capacity_reserved" : int
"capacity_total" : int
"id" : int
"mgmt_connectivity_state" : string
"mgmt_host" : string
"name" : string
"system_id" : string
"username" : string
 ```

## GET

Example 1:

GET https://{***host-address***}/api/v2/replication/peer_k2arrays
```json
{
  "hits": [
    {
      "bandwidth_limit": 40000,
      "capacity_allocated": 0,
      "capacity_allocated_snapshots_and_views": 0,
      "capacity_allocated_volumes": 0,
      "capacity_free": 3233943552,
      "capacity_physical": 0,
      "capacity_provisioned": 94371840,
      "capacity_provisioned_snapshots": 10485760,
      "capacity_provisioned_views": 0,
      "capacity_provisioned_volumes": 83886080,
      "capacity_reserved": 0,
      "capacity_total": 3233943552,
      "id": 1,
      "mgmt_connectivity_state": "ok",
      "mgmt_host": "172.16.50.3",
      "name": "kcs503",
      "system_id": "d503",
      "username": "replication"
    }
  ],
  "limit": 100,
  "offset": 0,
  "total": 1
}
```

## POST

### Properties:
 ```text
Mandatory: 
name
mgmt_host
username
password
local_username
local_password

Optional: 
bandwidth_limit
logical_bandwidth_limit
 ```

Example 1:

POST https://{***host-address***}/api/v2/replication/peer_k2arrays

Body:
```json
{
    "name": "kcs503", 
    "bandwidth_limit": "40000", 
    "mgmt_host": "172.16.50.3",
    "username": "replication", 
    "password": "replication", 
    "local_username": "replication", 
    "local_password": "replication"
}
```

## PATCH

### Properties:
```text
Optional:
name
mgmt_host
username
password
bandwidth_limit
logical_bandwidth_limit
```

Example 1:

PATCH https://{***host-address***}/api/v2/replication/peer_k2arrays/{id}

Body:
```json
{
    "bandwidth_limit": "30000"
}
```

## DELETE

Example 1:

DELETE https://{***host-address***}/api/v2/replication/peer_k2arrays/{id}


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
