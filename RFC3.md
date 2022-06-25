# RFC 3 - Meower Foundation Authentication
Authored by: Tnix <tnix@meower.org>, Meower Team, on Friday, June 24, 2022
---
This document is meant to describe the authentication process of handling multiple authentication methods in foundation authentication for Meower API v0.

## Authentication Methods

### All authentication types
`password`: A generic user password. Will require multi-factor authentication if multi-factor authentication is enabled on the user's account.

`email`: A code sent to the user's verified email addresses.

`webauthn`: A WebAuthn method such as a security key or secret stored on the user's device.

`totp`: A timed one time password using an authentication app. This can only be used for mutli-factor authentication.

`device`: A code that is generated then can be used on a device that is already authenticated.

### Authentication method limits
`password`: An account can only have 1 password at a time.

`email`: An account can have 5 or less email addresses at a time.

`webauthn`: An account can have 5 or less WebAuthn devices at a time.

`totp`: An account can only have 1 TOTP device at a time.

`device`: Any currently authenticated device can authenticate another device.

### Authentication methods endpoint
The `/oauth/auth-methods` endpoint is meant to return a content type of `application/json` with a status of `200` upon success.

### Getting authentication methods
The request should be structured like this:
```json
{
    "method": "GET",
    "body": {
        "username": ":username"
    }
}
```
Example of a response of an account's authentication methods with a password and a verified email address while not authenticated:
```json
{
  "methods": ["password", "email"],
  "default": 0
}
```
While authenticated you will not need to give a request body, but you will not be able to get the authentication methods for other accounts other than the currently authenticated account. Example of a response of an account's authentication methods with a password and a verified email address while authenticated:
```json
{
  "methods": [{"_id": "uuid4", "type": "password"}, {"_id": "uuid4", "type": "email", "email_address": "example@meower.org"}],
  "default": 0
}
```
The default authentication type in the examples shown above is their password, the `default` property is the array index of where their preferred authentication method is.

### Adding a new authentication method
The request should be structured like this:
```json
{
    "method": "PUT",
    "body": {
        "type": "password/email/webauthn/totp",
        "data": ":required_data"
    }
}
```

### Deleting an authentication method
The request should be structured like this:
```json
{
    "method": "DELETE",
    "body": {
        "id": ":uuid4"
    }
}
```

## Authentication
The `/oauth/login` endpoint is meant to return a content type of `application/json` with a status of `200` upon success.

### Password
The request should be structured like this:
```json
{
    "method": "POST",
    "body": {
        "username": ":username",
        "auth_method": "password",
        "data": ":password"
    }
}
```

Example of a response of successful authentication with multi-factor required:
```json
{
    "session": sessionObject (limited),
    "user": userObject (limited),
    "requires_mfa": true,
    "mfa_options": ["email", "totp", "webauthn"],
    "requires_authentication_reset": false
}
```
### Email
The request should be structured like this:
```json
{
    "method": "POST",
    "body": {
        "username": ":username",
        "auth_method": "email"
    }
}
```
After the user inputs their unique code from the email they got, their client should send a request to `/oauth/login/email` with the following structure:
```json
{
    "method": "POST",
    "body": {
        "username": ":username",
        "code": ":code"
    }
}
```
### WebAuthn
The request should be structured like this:
```json
{
    "method": "POST",
    "body": {
        "username": ":username",
        "auth_method": "webauthn",
        "data": ":webauthn_data"
    }
}
```
### Device
The request should be structured like this:
```json
{
    "method": "POST",
    "body": {
        "username": ":username",
        "auth_method": "device"
    }
}
```
Example of a response (the code will be the session token):
```json
{
    "session": sessionObject (limited),
    "user": userObject (limited),
    "requires_mfa": false,
    "mfa_options": null,
    "requires_authentication_reset": false
}
```
After the client gets the session data, it'll need to poll `/oauth/login/device` every 5 seconds with the `Authorization` header set to the session token/code. After it has been approved this endpoint will return a successful authentication payload.

## Multi-factor Authentication (only for password authentication)
The only authentication type that requires multi-factor authentication if it's enabled is `password`. Multi-factor authentication acts exactly the same as first-stage authentication except it requires a token to prove first-stage authentication was already completed. Every authentication method is available for completing multi-factor authentication apart from `password`.

The `/oauth/login/mfa` endpoint is meant to return a content type of `application/json` with a status of `200` upon success.

The request should be structured like this and include the multi-factor authentication token in the `Authorization` request header:
```json
{
    "auth_method": ":auth_method",
    "data": ":required_data"
}
```
The `data` property in the example shown above is where the data required to authenticate goes, so this may be in form of a TOTP code or information from a WebAuthn authentication device.
## Successful Authentication Response
Example of a response of successful authentication:
```json
{
    "session": sessionObject (full),
    "user": userObject (full),
    "requires_mfa": false,
    "mfa_options": null,
    "requires_authentication_reset": false
}
```
## Locked Accounts
When an account is found to be doing suspicious activity or has been inactive for an extended period of time, it may be locked to help prevent malicious attempts of accessing it.

When an account is locked the only authentication type that'll be available to use is `email`. If an account does not have a verified email, the user will have to reach out to support to get their account reinstated.

Once the user authenticates with email the `requires_authentication_reset` property in the successful authentication response will be changed to `true`. Their client may ask them to setup their authentication methods again, otherwise their only authentication method will be `email`.