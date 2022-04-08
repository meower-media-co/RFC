# RFC 2 - Functions of Meower Clients and Servers
Authored by: MikeDEV <mike@meower.org>, Meower Team and William Horning <william@meower.org>, Meower Team, on Thursday, April 7, 2022
---
This RFC outlines the functions of clients and servers.

## Client functions

1. Pulling profile data from the user's homeserver
2. Performing authentication with the user's homeserver
3. Authorizing 2FA requests for other Meower-authorized apps
4. Download an index of servers the user has joined from the user's homeserver
5. Using the the user's homeserver as a social media platform
6. Accessing global community features not accomplished with existing Yoom builds from the user's homeserver
7. Accessing hosting for communities from community servers

## Community server functions

1. Storing content shared within that server
2. Serving as a substitute in the event that other servers are down
3. Optionally functioning similarly to a CDN to share content causing improved load times for clients around the world
4. Hosting for public/private communities

## Homeserver functions

1. Hosting profile data
2. Handling authentication
3. Handling federation
4. Hosting an index of servers joined by users
5. Hosting a social media platform
6. Hosting global community features
7. All functions of community servers
