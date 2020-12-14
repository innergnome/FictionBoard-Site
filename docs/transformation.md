# Transformation and templating

Transformations are used a lot in FictionBoard to achieve various renderings.


## Replace variables

{key} or {object.key} will let you replace values from the YAML frontmatter. The values are expected to live within the ´data´ object.
## Key-value pairs

If a key-value pair is to be rendered, for instance in a character sheet, it is transformed into **key:** value. 

Key-value pairs often appear within a context so applying logic that applies to the text following the key is quite easy.

## Transformation of values

This to achieve various visualisations, values in a key-value pair is transformed and handled by small rendering modules.

### 3/10 

[Temporary current=3, max=10]

### 3 (10) 

[Temporary current=3, max=10]

### 1-3 

[Range low=1 high=3]

