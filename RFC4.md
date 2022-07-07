# RFC 3 - Meower OAuth Scopes
Authored by: Tnix <tnix@meower.org>, Meower Team, on Tuesday, June 28, 2022
---
This document is meant to list all the OAuth scopes that can be granted to first party and third party OAuth applications.

## Foundation
### User
`foundation:profile:view_profile`: Gives access to reading their public profile information, such as username, avatar, quote, public flags, and any other information that is publicly accessible about the user.

`foundation:profile:edit_profile`: Allows editing the user's public profile information such as username, avatar, quote, etc.

### Account Settings
`foundation:settings:read_email`: Gives access to reading the user's email addresses they have linked to their account.

`foundation:settings:read_config`: Gives access to reading the user's chosen configuration, such as theme, colors, background music, sound effects, and any other personalization options.

`foundation:settings:edit_config`: Gives access to updating the user's configuration.

`foundation:settings:edit_authentication` (**This can only be granted to first party applications**): Gives access to editing the user's authentication methods.

`foundation:settings:sessions` (**This can only be granted to first party applications**): Allows viewing and revoking foundation sessions.

`foundation:settings:danger` (**This can only be granted to first party applications**): Allows requesting account deletion, data exports, etc.

### OAuth
`foundation:oauth:view_apps`: Allows viewing the user's authorized applications and any used first-party applications.

`foundation:oauth:edit_apps` (**This can only be granted to first party applications**): Allows viewing, editing, and creating OAuth applications for the user.

`foundation:oauth:revoke_apps` (**This can only be granted to first party applications**): Allows revoking access to authorized applications.

### Inbox
`foundation:inbox:read_messages`: Allows reading the user's inbox messages.

`foundation:inbox:mark`: Allows marking the user's inbox messages as read/unread.

## Meower
### Chats
`meower:chats:view_chats`: 

### Posts
`meower:posts:read_posts`: Allows reading all the user's posts in places the OAuth app has been granted to access (home is always granted).

`meower:posts:create_posts`: Allows creating posts as the user in places the OAuth app has been granted to access (home is always granted).

`meower:posts:edit_posts`: Allows editing and deleting posts as the user in places the OAuth app has been granted to access (home is always granted).

`meower:posts:comments`: Allows viewing, creating, and editing posts as the user in places the OAuth app has been granted to access (home is always granted).