# snapshots

### Location
https://{***host-address***}/api/v2/snapshots

### Supported methods
GET, POST, PATCH, DELETE


## GET

### Property types:
 ```text
"creation_time" : int
"data_creation_time" : int
"description" : string
"generation_number" : int
"id" : int
"is_application_consistent" : boolean
"is_auto_deleteable" : boolean
"is_deleted" : boolean
"is_exist_on_peer" : boolean
"is_exposable" : boolean
"is_external" : boolean
"is_originating_from_peer": boolean
"iscsi_tgt_converted_name": string
"last_exposed_time": null,
"name": string
"replication_session": null,
"retention_policy": {
    "ref": string
},
"short_name": string
"source": {
    "ref": string
},
"triggered_by" : string 
"volsnaps_provisioned_capacity" : int
"volume_group": {
    "ref" : string
},
"wwn" : string
 ```
Example 1:

GET https://{***host-address***}/api/v2/snapshots/{id}
```json
{
  "hits": [
    {
      "creation_time": 1470553471.110832,
      "data_creation_time": null,
      "description": null,
      "generation_number": null,
      "id": 41,
      "is_application_consistent": null,
      "is_auto_deleteable": true,
      "is_deleted": false,
      "is_exist_on_peer": false,
      "is_exposable": false,
      "is_external": null,
      "is_originating_from_peer": null,
      "iscsi_tgt_converted_name": "vg1:s1",
      "last_exposed_time": null,
      "name": "vg1:s1",
      "replication_session": null,
      "retention_policy": {
        "ref": "/retention_policies/4"
      },
      "short_name": "s1",
      "source": {
        "ref": "/volume_groups/2"
      },
      "triggered_by": "api",
      "volsnaps_provisioned_capacity": 17179869184,
      "volume_group": {
        "ref": "/volume_groups/2"
      },
      "wwn": null
    }
  ],
  "limit": 100,
  "offset": 0,
  "total": 1
}
```

## POST

### Property types:
 ```text
Mandatory:
"short_name" : string
"source" : string
"retention_policy" : {
    "ref" : string
}

Optional: 
"is_auto_deleteable" : boolean
"is_exposable" : boolean
 ```

Example 1:

POST https://{***host-address***}/api/v2/snapshots

Body:
```json
{
    "short_name": "s1", 
    "source": {
        "ref": "/volume_groups/2"
    }, 
    "retention_policy": {
        "ref": "/retention_policies/1"
    }
}
```

Example 2:

To create a "view", specify the /snapshots/{id} as 'source'

POST https://{***host-address***}/api/v2/snapshots

Body:
```json
{
    "short_name": "v1", 
    "is_auto_deleteable": true,
    "is_exposable": true,
    "source": {
        "ref": "/snapshots/2"
    }, 
    "retention_policy": {
        "ref": "/retention_policies/1"
    }
}
```

## PATCH

### Property types:
 ```text
Optional:
name
short_name
retention_policy
is_auto_deleteable
Examples
 ```

Example 1:

PATCH https://{***host-address***}/api/v2/snapshots/{id}

Body:
```json
{
    "retention_policy": {
        "ref": "/retention_policies/2"
    }
}
```

## DELETE


DELETE https://{***host-address***}/api/v2/snapshots/{id}

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

