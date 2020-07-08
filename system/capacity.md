# system/capacity

### Location
https://{***host-address***}/api/v2/system/capacity

### Supported methods
GET


### Property types:
 ```text
"allocated" : int
"allocated_snapshots_and_views" : int
"allocated_volumes" : int
"curr_dt_chunk" : int
"free" : int
"id" : int
"is_reclamation_in_progress" : false,
"logical" : int
"physical" : int
"provisioned" : int
"provisioned_snapshots" : int
"provisioned_views" : int
"provisioned_volumes" : int
"reserved" : int
"state" : string
"total" : int
 ```

## GET

Example 1:

GET https://{***host-address***}/api/v2/system/capacity
```json
{
  "hits": [
    {
      "allocated": 0,
      "allocated_snapshots_and_views": 0,
      "allocated_volumes": 0,
      "curr_dt_chunk": 0,
      "free": 3233943552,
      "id": 1,
      "is_reclamation_in_progress": false,
      "logical": 0,
      "physical": 0,
      "provisioned": 94371840,
      "provisioned_snapshots": 10485760,
      "provisioned_views": 0,
      "provisioned_volumes": 83886080,
      "reserved": 0,
      "state": "ok",
      "total": 3233943552
    }
  ],
  "limit": 100,
  "offset": 0,
  "total": 1
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
