# RFC-1 - Client feature spec
Authored by: ShowierData9978 <contact@showierdata.xyz>, Bloctans <bloctans2@protonmail.com>, derpygamer2142 <derpygamer2142@gmail.com>, Meower Team, on 4/18/24 (CT).

**Note: This is currently a draft**

Please remember to **READ THIS RFC VERY CAREFULLY**.

This RFC applies to all **clients** that **want to get** featured. If you **make a client** just **for the fun** of it, you **DO NOT** need to follow this RFC, however it's recommended that you at least follow [Vulnerabilities](#vulnerabilities) and not make clients that break the Meower TOS or Privacy Policy (unless stated otherwise, eg. custom privacy policy)

This also applies to client plugins in relevant areas (ie: [Design Practices](#design-practices))

You can remove your client from the featured clients at any time for any reason. You are in absolute control of your project.

## Terms/Definitions

- Us/We - The Meower team
- FOSS/OSS - Free and open source software
- M.js - Meower's open source client and bot library made with JavaScript.
- JS - JavaScript
- WS - WebSockets(s)
- APTE - As per (the) example client
- PFP - Profile picture

## Prefacing

This document may be hard to understand for some readers, as it assumes that you have background in developing with JavaScript ("JS"), WebSockets ("WS"), REST APIs, and also that you have read some of the [Meower Documentation](https://docs.meower.org/)

If you do not have any background in this, then it will be harder to understand the references this RFC makes. Therefore, it will be harder to make a featured client.


In other words, this RFC doesn't go easy on you.

## Rules
- You **MAY NOT** create a client for **"malicous intent"**, we will carefully review your client to make sure that you aren't breaking any guidelines.
- This should be obvious, however clients must not break the Meower TOS or Privacy Policy (unless stated otherwise, eg. custom privacy policy)
- Custom privacy policies are allowed, but they are **HIGHLY DISCOURAGED**
  - Custom privacy policies **DO NOT** provide a good user experience
- Plugins are allowed, and are encouraged. They must still follow this RFC.
- Clients must have their own page so users can use it after it has been cycled out of being the featured client.
- Clients cannot have ads, tracking, or data collection. However, you can take donations from users of your client on any donation platform.
- We reserve the right to hold you back from being a featured client if we have suspicion that you are using any kind of loophole in the RFC.
- We reserve the right to add a client to the featured list even if it does not follow guidelines.

## Guidelines

### Code Optimizations

You can either use M.js, a similar library, or follow [Design Practices](#design-practices). 

We suggest that you use M.js, as it provides a nicer way to interact with the Meower API, and also provides features that help with server performance (eg. caching user data)

### Design Practices

If you are using M.js or a similar library, you do not need to follow this part of the RFC. The library should have implemented it for you.

- Do not fetch the chat list every time the user goes onto the page. 
   We provide updates to chats on the WebSocket, so you can cache them.
- Store the posts & don't spam the API to get new posts.   
    The WebSocket provides this to you as well.
- You must use Websocket V1 (Merged [here](https://github.com/meower-media-co/Meower-Server/pull/242))

### Vulnerabilities

If your client is discovered to have a vulnerability, it will be ineligible to be featured until the vulnerability is fixed.
If a vulnerability is reported, you must attempt to fix it as soon as possible and alert users if applicable. You must also alert (to be determined) so your client can be temporarily removed from the featured list to prevent harm to users. 

The easiest fix to most of these issues is to just do it APTE.

Some of the common vulnerabilities include:
- XSS (Cross site scripting attacks)
    - Read more about XSS [here](https://en.wikipedia.org/wiki/Cross-site_scripting) 
    - If you aren't using a web framework, avoid using innerHTML directly for user generated content.
    - For Markdown, make sure that your parser works properly. We can't give a lot of details on how to do this well, as parser implementations vary. It's best to just do Markdown APTE.
- Storing user data insecurely. You should do it APTE
- Having users run scripts in console
    - This isnt something you can really handle, however its important to warn users about the possibility.
    - We have prepared an example script for this case (JS)
        ```js 
            console.log('%cStop!', 'color: #F00; font-size: 30px; -webkit-text-stroke: 1px black; font-weight:bold');
            console.log(
                'This is a part of your browser intended for developers. ' +
                'If someone told you to copy-and-paste something here, ' +
                'don\'t do it! It could allow them to take over your ' +
                'Meower account, and do many other harmful things, causing a ban or account deletion. ' +
                'However, dont let this deter you from being here, as it can be a nice learning resource ' +
                'For people who want to make their own Meower client! ' +
                'If you accidentally do end up running a harmful script,' +
                ' Go to Settings > Security and then hit "Logout Everywhere"'
            );
        ```

### Feature Parity

(These are the **FEATURES** you need to have in your client)

To be featured, your client must have at least these features. 

We also have listed features that can be optionally excluded
- Sending, editing, and deleting posts.
- Updating chats when added to/removed from one.
- User profiles (APTE).
- Custom PFPs.
- Default PFPs, extra can be added by uploading as a custom PFP.
- Post/user reporting.
- Chats:
    - Chat Member management (APTE).
    - Creating chats.
- Logging in/signing up.
- Home page.
    - You can exclude the ulist.
- ALL settings* (APTE).
	- Setting categories have to be APTE.
    - You can exclude Layout and BGM.
    - You can exclude Sound Effects too, however we recommend you keep them so they can be used for notifications. 
- Searching (APTE).
- Blocking/reporting users.
- Bridge support.
    Meower has various bridges that are offical, or are community made. They need to be supported so the syntax is not shown, leading to worse UX. 


    The current list of supported bridges are:

    - Discord
    - gc *internal only*

- Sending typing indication. You do not need to show who is typing.
- Markdown (APTE if you want, markdown itself is not optional). 
- Image host whitelist (until we get a image reflector), can be disabled by the user (with a warning before disabling!).
    
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

    The client does not need to support servers with breaking changes. The only exception to this is when the offical server makes a breaking change.       

# Updates to this RFC

Clients will have 60 days to add features that are added to this RFC after the update is published. There will be a 1 week grace period before being removed from the list of featured clients.
