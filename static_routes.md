# static_routes

### Location
https://{***host-address***}/api/v2/static_routes

### Supported methods
GET, POST, DELETE


## GET

### Property types:
 ```text
"destination_subnet_ip" : string
"destination_subnet_mask" : string
"gateway_ip" : string
"knode" : string
"id" : int
 ```
Example 1:

GET https://{***host-address***}/api/v2/static_routes
```json
{
  "hits": [
    {
      "destination_subnet_ip": "10.3.0.0",
      "destination_subnet_mask": "255.255.0.0",
      "gateway_ip": "172.16.0.0",
      "knode": "kblock01-knode01",
      "id": 1
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
"destination_subnet_ip" : string
"destination_subnet_mask" : string
"gateway_ip" : string

Optional: 
"knode" : string
 ```

Example 1:

POST https://{***host-address***}/api/v2/static_routes

Body:
```json
{
    "gateway_ip": "172.16.0.0",
    "destination_subnet_ip": "10.3.0.0", 
    "destination_subnet_mask": "255.255.0.0"
}
```

## DELETE

### Property types:
 ```text
 "id" : int
 "labels" : string
 ```

Example 1:

DELETE https://{***host-address***}/api/v2/static_routes/{id}

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
