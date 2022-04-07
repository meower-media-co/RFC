# RFC 2 - Meower Basic Networking Architecture
Authored by: MikeDEV <mike@meower.org>, Meower Team and William Horning <william@meower.org>, Meower Team, on Thursday, April 7, 2022
---
This RFC outlines the functions of clients and servers.

## Client functions

1. Pulling profile data from main server
2. Performing authentication with main server
3. Authorizing 2FA requests for other Meower-authorized apps
4. Download an index of servers the user has joined from the main server
5. Using the main server as a social media platform
6. Accessing a place for global announcements, forums, and other functions not accomplished with existing Yoom builds from the main server
7. Accessing hosting for communities from the main server and user servers

## Server functions

1. Storing content shared within that server
2. Serving as a substitute in the event that the other servers are down
3. Optionally functioning similarly to a CDN to share content causing improved load times for clients around the world
4. Hosting for public/private communities
5. Filtering content in public communities
6. Having moderation of some form (Moderation can be requested from the Meower Moderation team)

## Additional main server functions

1. Hosting profile data
2. Handling authentication
3. Handling federation
4. Hosting an index of servers joined by users
5. Hosting a social media platform
6. Hosting a place for global announcements, forums, and other functions
