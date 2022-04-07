# RFC 2 - Meower Basic Networking Architecture
Authored by: MikeDEV <mike@meower.org>, Meower Team, on Thursday, April 7, 2022
---
This RFC outlines the bare minimal design and structure of how Meower's servers/clients interact, and how user servers talk to each other. Also outlines general protections and features.

## Client and main server communication
The main client and server will communicate utilizing REST APIs. Some of the specs for this has been detailed in RFC1. 

Clients will only need to communicate with the main server to do the following:
1. Pull profile data
2. Perform authentication
3. Authorize 2FA requests for other Meower-authorized apps
4. Download an index of other servers the user has joined.
5. Utilize the main server as a basic social media platform, sharing photos and posts (similarly to twitter, as an example).
6. Offer a place for global announcements, forums, and other necessities not yet accomplished with existing Meower builds.

## User server and main server communication
User servers can be created using prebuilt software provided by the backend team, allowing a user to make and host their own private or public server. The servers will talk to each other over REST as well.

Some functionality for user servers are:
1. Store content shared within that server.
2. Serve as a substitute in the event that the main server is down.
3. Function similarly to a CDN. Servers will talk to each other (utilizing the main server as a "phonebook") and share posts, videos, music, etc. to improve load times for clients around the world.
4. Offer voice and video chat functionality (similarly to discord, as an example).

## Client and user server communication
Akin to discord servers, users can utilize user servers to:

1. Have long, private, and secure communications
2. Keep main server load down
3. Pull content quicker (utilizing a bunch of user servers as a CDN)
4. Offer alts

Some minor specifications needed to maintain moderation of all systems as follows:
1. A moderator of the main server will automatically be a moderator of all user servers.
2. Given special permission, a user server moderator can be promoted to a main server mod.
3. All content must be filtered and verified by a minimum amount of user servers running scanners and filters. This will hopefully decrease the chances of malicious and/or obscene content from being shared.
4. Main server and user server moderators have remote access to the server to perform standard antivirus software, ddos protection, and other misc. network administrative measures to keep services running smoothly.
