# Development

> This is very much a work in progress.
## Issue tracker

https://github.com/users/innergnome/projects/2

## Main repos

The FictionBoard site and previews (private)
https://github.com/privatemonkey/fictionboard-site

Documentation
https://github.com/innergnome/FictionBoard

## Packages and frameworks

FictionBoard is built on an arhitecture utilizing [Sveltes](https://github.com/sveltejs/svelte) serverless capabilities together with [PouchDbs](https://github.com/pouchdb/pouchdb) offline capabilities.
### Parsing and transformation

FictionBoard use [Marked](https://github.com/markedjs/marked) with home built extensions to support our Markdown extension [RPG Markdown](https://github.com/innergnome/rpg-markdown). Default values for a markdown document is set as YAML in the Frontmatter.

- ´title´ The name of the page
- ´slug´ The URL friendly version of the title
- ´type´ Should be a game entity, a container for game entities or a generic 'document'
- ´data´ contains values parsed from the markdown
- ´defaults´ Values used in the text that may be overridden by ´data´
- ´template´ Values related to rendering.
- ´template.plugins´ List of plugins and which chunks they apply to. A ´\_plugin: value´ directly in a chunk lets you _override_ the template plugin. Allowed plugins are defined by template properties.
- ´template.effects´ List of default template effects. A ´\_effect: value´ in a chunk _adds_ an effect to the chunk. Allowed effects are defined by template properties.

<!-- TODO: Write about ´template.actions´ -->

#### Template YAML

´´´yaml
template:
   name:
   effects: 
   plugins:
   actions:
   logo:
´´´

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

### Drag and drop

https://github.com/isaacHagoel/svelte-dnd-action

### Styling

Goals: 
- Clean and simple
- Readable
- Accessible for anyone skilled in CSS.

For now I use plain old CSS with some sneaky use of CSS variables and Svelte magic. I'm working on moving this setup to a SASS a follow [BEM syntax](http://getbem.com/naming/). I don't really see the need for frameworks now that grids, flex, css variables and other niceness are at hand but will probably borrow some breakpoint, layout, typography and spacing syntax to make it recognizable and compatible. The HTML of FictionBoard is quite plain. 

### Graphics

Svelte is really awesome att SVG transformation so a lot of the graphical part of FictionBoard will utilise this. Maps and tokens will probably be a combination of different techniques and frameworks. If we go into 3D territories I've experimented with Three.js, Babylon.js and Greensock.

### Security

The security features in CouchDb are sufficient for many of the FictionBoard use cases and handles most authorization cases. We'll come back authentication in a later relase.



