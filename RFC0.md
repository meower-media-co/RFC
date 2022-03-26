# RFC 0 - Meower Development Process
Authored by: William Horning <william@meower.org>, Meower Team, on Saturday, March 26, 2022
---
The Meower Development process is made of multiple teams and processes and this document is meant to describe each team, their function, and the Meower Development workflow.
## Teams
### RFC Team
The RFC team is meant to discuss standards, and the making of RFCs, which consist of standards in a standardized form. The structure of an RFC is as follows:
1. A title in the form of `RFC X - D`
   where X is a number assigned by the RFC team to the RFC
   where D is a description of the document
2. An attribution in the form of `Authored by: X, A, on D`
   where X is the authors name and email in the form `Name <email>`
   where A is the affiliation of the author
   where D is the date the RFC was published on
3. Content relating to the description of the document
### Backend Team
The Backend team is to work with the RFC team, giving feedback on drafts of RFCs and implementing them into an API that is consistant with the standards laid out in the RFCs. The Backend Team is to also work with the Frontend Team telling them how the API functions.
### Frontend Team
The Frontend Team is to work on clients which implements the API made by the Backend Team. The Frontend Team is to also work with the Music and Art team to get designs and sound effects to use in the frontend. In addition, the Frontend team is to work with the Wiki Team to document the clients.
### Music and Art Team
The Music and Art Team is to work with the Frontend Team on designs and sound effects. In addition, the Music and Art Team is to work with the Managers Team on branding and other projects as needed. On top of that, the Music and Art Team is to also work with the Wiki Team to make screenshots and mockups for the Meower Wiki.
### Wiki Team
The Wiki Team is to work with the Frontend team to document the clients. In addition, the Wiki Team is to work with the Music and Art team to get screenshots and mockups to use on the Meower Wiki.
### Moderators Team
The Moderators Team is to work on moderating the `meower.org` homeserver.
### Managers Team
The Managers Team is to work on managing the other teams and making sure they are working according to this specification.
## Meower Development workflow
1. RFC Makes an idea
2. RFC Team makes a draft RFC for the respective teams to review and give feedback on until the spec is finalized
3. Relevant teams implement neccessary changes in a staging deployment and test until stable enough to be deployed to the beta channel
4. Beta channel users test the changes and give feedback until it is stable enough to be implemented into the stable channel
5. Gets reviewed by RFC team for spec compliance and is implemented
