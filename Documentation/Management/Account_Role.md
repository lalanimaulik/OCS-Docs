---
uid: AccountRole
---

# Role

A Role is an entity that is used to authorize API requests.

## Properties

For HTTP requests and responses, the Role object has the following properties and JSON-serialized body: 

| Property | Type | Description | 
 | --- | --- | ---  | 
| Id | string | GUID for this Role. Generated by the server upon Creation. | 
| Name | string | Name of this Role. | 
| Description | string | Description of this Role. | 
| RoleScope | RoleScope | Scope of this Role. | 
| TenantId | string | GUID of Tenant for this Role, if this is a Account Role, null otherwise. | 
| CommunityId | string | GUID of Community for this Role, if this is a Community Role, null otherwise. | 
| RoleTypeId | string | GUID of Role Type for this Role, if this is a Account Role and is not a customer defined Role. | 


```json
{
	"Id": "id",
	"Name": "name",
	"Description": "description",
	"RoleScope": 0,
	"TenantId": "tenantid",
	"CommunityId": "communityid",
	"RoleTypeId": "roletypeid"
}
```
***

## `GetAccountRole()`

Retrieves an Account Role based on the specified Account Id and Role Id.

### Http

`GET api/Tenants/{tenantId}/Roles/{roleId}`

### Parameters

```csharp
[Required]
string tenantId
```

The Account identifier for this request
```csharp
[Required]
string roleId
```

The Role identifier for this request


### Security

Authorized for Account Administrator role

### Returns

The `Role` with Id roleId

***
## `GetAccountRoles()`

Retrieves all Account Roles for the specified Account Id.

### Http

`GET api/Tenants/{tenantId}/Roles`

### Parameters

```csharp
[Required]
string tenantId
```

The Account identifier for this request
```csharp
[Required]
string skip
```

Number of `Roles` to ignore
```csharp
[Required]
string count
```

Number of `Roles` to be returned
```csharp
[Optional]
[Default = ""]
string query
```

Unsupported parameter


### Security

Authorized for Account Member role

### Returns

An array of `Role` objects 

***
## `CreateAccountRole()`

Create an Account Role

### Http

`POST api/Tenants/{tenantId}/Roles`

### Parameters

```csharp
[Required]
string tenantId
```

The Account identifier for this request
```csharp
[Required]
[FromBody]
Role role
```

The `Role` for this request


### Security

Authorized for Account Administrator role

### Returns

The `Role`

***
## `UpdateAccountRole()`

Update a Role by its Role Id

### Http

`PUT api/Tenants/{tenantId}/Roles/{roleId}`

### Parameters

```csharp
[Required]
string tenantId
```

The Account identifier for this request.
```csharp
[Required]
string roleId
```

The Role identifier for this request.
```csharp
[Required]
[FromBody]
Role role
```

The `Role` for this request.


### Security

Authorized for Account Administrator role

### Returns

The `Role` with Id roleId

***
## `DeleteAccountRole()`

Delete any Account scoped, non built-in Role by its Role Id

### Http

`DELETE api/Tenants/{tenantId}/Roles/{roleId}`

### Parameters

```csharp
[Required]
string tenantId
```

The Account identifier for this request
```csharp
[Required]
string roleId
```

The Role identifier for this request


### Security

Authorized for Account Administrator role

### Returns

HTTP status code - 200 on success, other HTTP status codes on failure

***
