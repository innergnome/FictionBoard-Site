# API specification (Draft)

This is the draft specification for the API

## Actor

`:id` the id of an entity

`:section_id` the id of a section. Sections within a chunk has a section_id that contains its parents.

`/api/actor/:id` returns the full actor object with template settings and markdown

`/api/actor/:id/_data` returns the data object with all chunks stored in `_children`

`/api/actor/:id/_template` returns the template settings

`/api/actor/:id/_md` returns the raw Markdown

`/api/actor/:id/_md/chunks` returns the Markdown as a multi level array with all headers as chunk objects. The attribute `_children` contains the array of child chunks.

`/api/actor/:id/:section_id` will retrieve a specific part of the data. Use it to refference skills, attributes or similar "chunks" of data

`/api/actor/:id/:section_id/md` will retrieve md for the specific section. 
