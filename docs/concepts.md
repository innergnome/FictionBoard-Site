# FictionBoard concepts

FictionBoard is split into seperate modules. Some work independent of each other and could be distributed free to use. This is an overview of the concepts and modules I believe FictionBoard will cover. 

## Basic modules

### Board

A container for threads, documents, folders and other high level modules.

### Threads

Is a container for conversations and actions

### Document

A long or short text. If it's following the guidlines for RPG markup game- and plot entities may be parsed from the text. Posts and comments are created and treated as documents.

### Chunk

A short text derrived from a document or created on the fly. Plot- and game entities may be parsed from the text. Messages are treated and created as chunks.

### Media

Movie, image or sound.

## VTT modules

### Game system

### Game

### Session

### Scene

### Action

### Macro

### Bot

### Editor

### Message

### Template

### Rule

### Macro

## VTT dependent modules

### Entity helper

This is really a set of renderers and helpers. Depending on the entity type this renderer will create a visualizion of the entity and provide helpers specific to the entity type. Spells, abilities, tokens and similar are typical entity modules.

## Independent modules

These modules are used by the VTT but work with limited functionalit independent of the VTT enginge. 
      
### Slide deck

Renders a chunk or a document into a slide deck.

### Handout

Renders a chunk or a document into one or more handouts

### Tome

Renders on or more documents into a searchable tome

### Character sheet

Renders a chunk or a document into a character sheet

### Relations

Renders the relations between a specific type of game entities from a chunk, document or collection of documents.

### Avatars

Used in the above objects in various sizes.

## Render modules

These modules will render and add functionality to VTT modules. They should be specified as plugins in the definition for how a VTT module shall render within a specific game system.
### list-multivalue

Allows the user to add or remove an item

### list

### check

Will create a list of checkboxes from a number in a key-value pair such as 3/10 or 3(10).
Will add one or more checkbox to a key-value pair that contains a (0/3).
May include the helper "use" or similar.

## Helper modules

These modules add functionality

### roll

Allows the user to make a roll using one of the values

### use

Allows the user to use an weapon, ability or similar to gain a modiification


### image
## Game entities

### Actor

A character, monster, non player character, creature or being that is playable or part of a plot.

### Object

Any static or abstract object an actor can interact with. 

### Container

### Vehicle/

### Universe

### World

### Location

### Setting


## Plugins

Can be added to an object definition to add renderers (which may include built in actions)
## Actions

Can be added to an object definition to allow triggering of actions and macros

