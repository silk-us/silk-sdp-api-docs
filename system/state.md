# system/state

### Location
https://{***host-address***}/api/v2/system/state

### Supported methods
GET, POST, PATCH, DELETE


### Property types:
 ```text
"current_user_role" : string
"id" : int
"is_system_functionality_degraded" : boolean
"iscsi_qualified_target_name" : string
"last_online_time" : int
"next_state" : string
"replication_default_target_exposure" : string
"replication_min_protocol_version" : int
"replication_protocol_version" : int
"rest_api_version" : string
"sra_protocol_version" : string
"state" : string
"system_connectivity_type" : string
"system_id" : string
"system_name" : string
"system_time" : int
"system_tz" : string
"system_tz_short" : string
"system_version" : string
 ```

## GET

Example 1:

GET https://{***host-address***}/api/v2/system/state
```json
{
  "hits": [
    {
      "current_user_role": "admin",
      "id": 1,
      "is_system_functionality_degraded": false,
      "iscsi_qualified_target_name": "iqn.2009-01.com.kaminario:storage.k2.54645",
      "last_online_time": 1551766366.8819399,
      "next_state": "None",
      "replication_default_tar
      get_exposure": "unmapped",
      "replication_min_protocol_version": 1,
      "replication_protocol_version": 2,
      "rest_api_version": "2.2.0",
      "sra_protocol_version": "1.2",
      "state": "ONLINE",
      "system_connectivity_type": "FC",
      "system_id": "d575",
      "system_name": "kcs575",
      "system_time": 1551776801.95715,
      "system_tz": "Asia/Jerusalem",
      "system_tz_short": "IST",
      "system_version": "latest-20190304-1128"
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
system_name
send_callhome
send_test_event
replication_default_tar
get_exposure
 ```

Example 1:

PATCH https://{***host-address***}/api/v2/system/state/{id}

Body:
```json
{
    "system_name": "kcs527b"
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
