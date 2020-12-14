# API specification (Draft)

This is the draft specification for the API

## Actor

`:id` the id of a document representing an entity

`:chunk_id` the id of a chunk

`/api/actor/:id` returns the full actor object with template settings and markdown

`/api/actor/:id/_data` returns the data object with all chunks stored in `_children`

`/api/actor/:id/_render` returns the template settings

`/api/actor/:id/_md` returns the raw Markdown text

`/api/actor/:id/_chunks` returns the Markdown as a multi level array with all headers as chunk objects. The attribute `_children` contains the array of child chunks.

`/api/actor/:id/:chunk_id` returns a full chunk objects with data and markdown

`/api/actor/:id/:chunk_id/_data` will retrieve data for the specific chunk

`/api/actor/:id/:chunk_id/_render` will retrieve render data and template settings for the specific chunk, including the original template settings for the full document.

`/api/actor/:id/:chunk_id/_md` will retrieve md for the specific chunk
