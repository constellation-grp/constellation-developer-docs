# Watson Public API

We offer free access to the public API for the Watson service.

!!! warning
    The free tier of the Watson API allows only 500 requests per month.

## Pricing Tiers

Watson API offers different usage tiers:

- **Free**: 500 requests per month.
- **Subscription**: Monthly plans for higher request limits (pricing varies, contact support for details).

### Prepaid Requests

If you exceed your request limit, you can purchase additional requests:

- **Prepaid**: 100 Robux for every additional 1000 requests.

To register for an account or top up prepaid requests, you must contact support.

## Authentication

To use the API, you need to register and obtain an authentication token. The token must be included in the request headers as a Bearer token.

### Obtaining a Token

1. Contact support to register an account.
2. Log in and navigate to the API settings section.
3. Generate an API token.

### Using the Token

Include the token in the `Authorization` header of your requests:

```http
Authorization: Bearer YOUR_ACCESS_TOKEN
```

## Available Endpoints

### Get User Licences

**Endpoint:**

```http
GET https://api.constellationgroup.site/public/api/getuserlicences/{userid}
```

**Headers:**

```http
Authorization: Bearer YOUR_ACCESS_TOKEN
```

**Response:**

Success:

```json
{   
    "success": true,
    "userId": "12345",
    "licences": [
        {
            "licenceId": "571e924a-fd16-4696-a80a-cf1c84f8a4f2",
            "productId": "SCO",
            "ownsSince": "1741454719",
            "expires": "never"
        }
    ]
}
```

Error:

```json
{
    "success": false,
}
```

## Error Handling

If authentication fails or the request is invalid, the API will return an appropriate HTTP status code:

- `401 Unauthorized` - Missing or invalid authentication token.
- `403 Forbidden` - Access denied.
- `404 Not Found` - User ID not found.
- `423 Locked` - The specified user ID is suspended and cannot be accessed.
- `429 Too Many Requests` - Rate limit exceeded.
- `451 Unavailable For Legal Reasons` - The user has not permitted access to their data.
