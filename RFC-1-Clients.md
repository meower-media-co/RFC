# RFC-1 - Featured Client Requirements
Authored by: ShowierData9978 <contact@showierdata.xyz> on 4/18/24 (CT).
## Terms/Definitions

- Us/We - The Meower team



## Rules
- Clients created for malicious intent will not be featured
- Clients must have their own TOS and Privacy Policy
- If your client implements any kind of plugin/addon interface, those are considered part of your client
- The Meower Team may, at it's sole discretion, choose whether or not a client should be featured
- The Meower Team may feature a client despite not complying with this RFC

## Guidelines

### Design Practices

- Cache chat and post data
- Use Cloudlink to get updates to cached information
- You must use Websocket V1 (Merged [here](https://github.com/meower-media-co/Meower-Server/pull/242))

### Vulnerabilities

If your client is discovered to have a vulnerability, you must fix said vulnerability as soon as possible, alert your client's users (if necessary), and have it removed from the list of featured clients if it won't be fixed in a reasonable amount of time.


### Feature Parity
To be featured, your client must have at least these features. 

- Sending, editing, and deleting posts.
- Updating chats when added to/removed from one.
- User profiles (APTE).
- Profile picture support
- Post/user reporting.
- Chats:
    - Chat Member management (APTE).
    - Creating chats.
- Logging in/signing up.
- Home page.
- ALL settings* (APTE).
	- Setting categories have to be APTE.
    - You can exclude Layout and BGM.
    - You can exclude Sound Effects too, however we recommend you keep them so they can be used for notifications. 
- Searching (APTE).
- Blocking/reporting users.
- Bridge support.
    Meower has various bridges that are offical, or are community made. They need to be supported so the syntax is not shown, leading to worse UX. 


    The current list of supported bridges are:

    - gc *internal only*

- Typing indicator support that users must be able to disable
- Markdown (APTE if you want, markdown itself is not optional). 
- Image host whitelist, can be disabled by the user (with a warning before disabling!).
    
    Current list of allowed image hosts:
    - https://meower.org/
    - https://http.meower.org/
    - https://assets.meower.org/
    - https://forums.meower.org/
    - https://go.meower.org/  
    - https://hedgedoc.meower.org/
    - https://docs.meower.org/
    - https://uploads.meower.org/ 
    - https://u.cubeupload.com/
    - https://cubeupload.com/
    - https://i.ibb.co/
    - https://media.tenor.com/
    - https://tenor.com/
    - https://c.tenor.com/
    - https://assets.scratch.mit.edu/
    - https://cdn2.scratch.mit.edu/
    - https://cdn.scratch.mit.edu/
    - https://uploads.scratch.mit.edu/
    - https://cdn.discordapp.com/
    - https://media.discordapp.net/

- Option to switch to an external sever.
