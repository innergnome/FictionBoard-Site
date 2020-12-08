# Development

> This is very much a work in progress.

## Packages and frameworks

FictionBoard is built on an arhitecture utilizing [Sveltes](https://github.com/sveltejs/svelte) serverless capabilities together with [PouchDbs](https://github.com/pouchdb/pouchdb) offline capabilities.

### Parsing and transformation

FictionBoard use [Marked](https://github.com/markedjs/marked) with home built extensions to support our Markdown extension [RPG Markdown](https://github.com/innergnome/rpg-markdown).

A production ready version of FictionBoard will probably use [ReMark](https://github.com/remarkjs/remark)/[ReHype](https://github.com/rehypejs/rehype) and other packages from the [Unified collective](https://github.com/unifiedjs/collective)

### Database

For the kind of content used in RPGs going with a document databases is a no brainer. 

Some goals when considering database:
- Store large Markdown documents.
- Handle files as blobs or similar
- Sync and replication to allow offline use of FictionBoard (support physical gaming)
- Model only settings and metadata needed for interactions and renderering.
- Allow Markdown and frontmatter as a middle layer
- A user should be able to keep all her content to herself
- Groups should be able to share content between themselves
- A merchant should be able to control the access to their content
- Large parts of the data should be open for all
- Fast load and queries
- Handle queries where we only want a subset of document values returned (Views solves this in Couch/Pouch)
- ... and many more

CouchDb/PouchDb combination which has a proven record for this use case and is built on ideas from Notes/Domino where I have tons of experience.

So - On the client we use [PouchDb](https://github.com/pouchdb/pouchdb).
FictionBoard use [CouchDb](https://github.com/apache/couchdb) as backend storage.
On the server we run [PouchDb Server](https://github.com/pouchdb/pouchdb-server) for fast data access. Not sure yet which database to use for PouchDb Server.

### Server and APIs

The current version of FictionBoard uses Express with [PouchDb Server](https://github.com/pouchdb/pouchdb-server). I've experimented with Firebase, Feathers.js and Sails.js for backends and APIs but do not want to build to many dependecies at this point.

### Messaging

The work on messaging has not started but we'll probably go with a combination of WebRTC and Websocket. Previous experiments have mostly used websocket.

### Styling

Plain old CSS with some sneaky use of CSS variables and Svelte magic. For now. I'm working on moving this setup to a SASS a follow [BEM syntax](http://getbem.com/naming/)

### Graphics

Svelte is really awesome att SVG transformation so a lot of the graphical part of FictionBoard will utilise this. Maps and tokens will probably be a combination of different techniques and frameworks. If we go into 3D territories I've experimented with Three.js, Babylon.js and Greensock.

### Security

The security features in CouchDb are sufficient for many of the FictionBoard use cases and handles most authorization cases. We'll come back authentication in a later relase.



