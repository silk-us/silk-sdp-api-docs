# replication/rpo_history

### Location
https://{***host-address***}/api/v2/replication/rpo_history

### Supported methods
GET


### Property types:
 ```text
"bytes_transmitted_logical" : int 
"bytes_transmitted_physical" : int
"generation_number" : int
"role" : string
"round_end" : int
"round_start" : int
"session" : {
    "ref" : string
},
"target_rpo" : int
 ```

## GET

Example 1:

GET https://{***host-address***}/api/v2/replication/rpo_history
```json
{
  "hits": [
    {
      "bytes_transmitted_logical": 0,
      "bytes_transmitted_physical": 0,
      "generation_number": 18,
      "role": "target",
      "round_end": 1470577726,
      "round_start": 1470577500,
      "session": {
        "ref": "/replication/sessions/7"
      },
      "target_rpo": 600
    },
    {
      "bytes_transmitted_logical": 0,
      "bytes_transmitted_physical": 0,
      "generation_number": 76,
      "role": "target",
      "round_end": 1470577766,
      "round_start": 1470577500,
      "session": {
        "ref": "/replication/sessions/3"
      },
      "target_rpo": 600
    },
    {
      "bytes_transmitted_logical": 0,
      "bytes_transmitted_physical": 0,
      "generation_number": 84,
      "role": "target",
      "round_end": 0,
      "round_start": 1470577500,
      "session": {
        "ref": "/replication/sessions/5"
      },
      "target_rpo": 900
    },
    {
      "bytes_transmitted_logical": 0,
      "bytes_transmitted_physical": 0,
      "generation_number": 75,
      "role": "target",
      "round_end": 1470577391,
      "round_start": 1470577200,
      "session": {
        "ref": "/replication/sessions/3"
      },
      "target_rpo": 600
    }
],
  "total": 100
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
