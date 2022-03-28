# RFC 1 - Meower API Status Endpoint
Authored by: William Horning <william@meower.org>, Meower Team, on Saturday, March 26, 2022
---
This document is meant to describe the `/status` unversioned API endpoint to retain backwards compatibility with Scratch Meower Clients and to provide an endpoint that can be used to describe the status of certain API versions.
## Structure
The `/status` endpoint is meant to return a content type of `application/json` with a status of `200`.
The data is structured like this:
```json
{
  "isRepairMode": false,
  "scratchDeprecated": true,
  "supported":{
    "0": false,
    "1": true
  }
}
```
## Properties
### isRepairMode
This property is a boolean. This property is kept to retain backwards compatibility with Scratch Meower Clients.
### scratchDeprecated
This property is a boolean. This property is to tell Scratch Meower Clients to show a screen regarding the end of life for the Scratch Clients.
### supported
This property is an object with keys for each API version with a boolean as a value. This property shows the API client whether a specific API version is supported or not.
