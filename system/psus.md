# system/psus

### Location
https://{***host-address***}/api/v2/system/psus

### Supported methods
GET, POST, PATCH, DELETE


### Property types:
 ```text
"connectivity_state" : {
    "ref" : string
},
"contained_in" : {
    "ref" : string
},
"id" : int
"is_expansion_in_progress" : boolean
"is_fru" : boolean
"is_phased_out" : boolean
"name" : string
"ndu_state" : string
 ```

## GET

Example 1:

GET https://{***host-address***}/api/v2/system/psus
```json
{
  "hits": [
    {
      "connectivity_state": {
        "ref": "/system/hardware_states/366"
      },
      "contained_in": {
        "ref": "/system/jbods/37"
      },
      "id": 68,
      "is_expansion_in_progress": false,
      "is_fru": true,
      "is_phased_out": false,
      "name": "kblock01-shelf01-psu01",
      "ndu_state": "component upgrade idle"
    },
],
  "limit": 100,
  "offset": 0,
  "total": 6
}
```

## PATCH

### Properties:
```text
Optional:
remove_module
```

Example 1:

PATCH https://{***host-address***}/api/v2/system/psus/{id}

Body:
```json
{
    "remove_module": "true"
}
```

## DELETE

Example 1:

DELETE https://{***host-address***}/api/v2/system/psus/{id}


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
