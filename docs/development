# Development

> This is very much a work in progress.

## Packages and frameworks

FictionBoard is built on an arhitecture utilizing [Sveltes](https://github.com/sveltejs/svelte) serverless capabilities together with [PouchDbs](https://github.com/pouchdb/pouchdb) offline capabilities.

### Parsing and transformation

FictionBoard is using [Marked](https://github.com/markedjs/marked) with home built extensions to support our Markdown extension [RPG Markdown](https://github.com/innergnome/rpg-markdown).

A production ready version of FictionBoard will probably use [ReMark](https://github.com/remarkjs/remark)/[ReHype](https://github.com/rehypejs/rehype) and other packages from the [Unified collective](https://github.com/unifiedjs/collective)

### Database

For the kind of content used in RPGs document databases is a no brainer. I also want to keep the data layer as simple, stable and flexible as possibly without having to do a ton of modelling. The setup for now is to use Markdown and frontmatter as a middle layer. The front matter will be modelled but will contain mostly metadata, styling and behaviour. The real data will be stored directly in the markdown.
A goal for FictionBoard is to be able to run most parts of the game and editor experience offline to accomodate physical game experience. Sync and replication are key capabilities needed from our databases so the obvious choice is CouchDb/PouchDb combination which has a proven record for this use case.

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
