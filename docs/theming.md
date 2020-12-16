> TODO: An overhaul of this text and write more specific about fonts, colors, backgrounds etc.
# Themes

FictionBoard allows for custom theming of handouts, slide decks, actor sheets and other objects. Themes are written as CSS rules.

Theming is highly encouraged to create an immersive experience relevant to your story. Themes can be generic and preferably genre oriented, game system specific or you can roll your own. The default theme for a system is usually maintained by someone appointed by the game system publisher.
## How styling works in FictionBoard

By default, the look and feel of objects is retrieved from the game system. If the game system does not have any specific styling, genre styling is proposed. On game level you can choose to override genre or game specific styling with another theme. You can also at any time choose a different style for a object. 
## Basic concepts for HTML in FictionBoard

The HTML of objects in FictionBoard is purposly kept quite simple to improve accessibility and make them possible to express in written text.

A more complex object such as an actor sheet is written as a set of headers, list, key value pairs, text and links. To create a rendering of the object, FictionBoard splits texts into chunks. A chunk is represented by a div with class derived from object type and the header from which the chunk is created. The chunks are contained within a div with class according to type and theme.

The chunk rendering can be overridden by defining a plugin to use instead of outputting the default HTML. The plugins adds additional behaviour to the basic HTML such as adding or removing items and more. The default plugins for FictionBoard are:

- list
- listMultivalue
- check

### Plugins
#### List

Takes a regular list or a text with one level of headings an adds these behaviours:

- add
- remove
- use

The `type` property of list will determine the types of use allowed.

Editing the markdown text directly will still have the same effect.

#### ListMultivalue

Takes a list with keyword pairs or text with one level of headings and a set of keyword pairs and adds these behaviours:

- add
- remove
- use

The `type` property of list will determine the types of use allowed.

Editing the markdown text directly will still have the same effect.

**Examples**

- `Name: Two handed sword`, `Damage: +3`, `Range: Melee` , `Bonus: 0`

##### Two handed sword

`Damage: +3`

`Range: Melee`

`Bonus: 0`


#### check

Turns a keyword pair with an upper level and current value into a set of checkboxes with behaviour connected to:

- add
- remove
- use

**Example**
##### Conditions

`Exhausted: 0/1`

`Battered: 0/1`

`Wounded: 0/1`

`Broken: 0/1`

##### Experience

`Experience: 3 (10)`


### Example text

```Markdown

## Diary found in the trash bin

You find an old diary in the trash bin. Seems someone only started writing in it.

### Page 1
 
{Content}

### Page 2

{Content}
```

### Example HTML

```html
<body class="system-{system-shortname} theme-{selected-theme}">

  <div class="handout-{type}">
    <h2>{handout-name}</h2>
    <div class="{type}-{chunk-name-as-slug}">
      <h3>{chunk-name}</h3>
      {Content}
    </div>
    <div class="{type}-{chunk-name-as-slug}">
      <h3>{chunk-name}</h3>
      {Content}
    </div>
  </div>   

```
#### Variables explained

- {system-shortname} - From the system you are playing
- {selected-theme} - From theme setting. Fallback to default game system template if theme not set. 
- {type} - From the top level header or type property. Can be overridden at the time of use (Change a diary note to a letter)
- {chunk-name} - From secondary headers
- {chunk-name-slug} - From secondary headers, lowercase and with space replaced with underscore (\_)
- {content} - All text following a chunk header. May contained formatting.

### Full example from Tales from the loop

A handout of diary pages

> This is a clean HTML version for styling purpose only. Other attributes are purposly left out.

```html
<body class="system-tftl theme-eighties">

  <div class="handout-diary">
    <h2>Letter found on pavement</h2>
    <div class="diary-page">
      <h3>December 12</h3>
      <p>What has happened is unbelievable, yet it has happened. 
I was chasd up te pat by a creature tat I could only 
identify as a dinosaur from te Cretaceous Period. The per-
son reading tis must tink I hav lost my mind. I heard te 
rocks slip beneat its fet while I ran as fast as I could 
to te brushes on te far side of te mountain, while te 
creature came closr. Had te brush not ben tick enough to 
kep te creature from finding me, I would be dead.
I hav found tis old Hunting Cabin, and made it my 
bas. I try to make as litle nois as possible. Who knows 
what els is out tere?</p>
    </div>
    <div class="diary-page">
      <h3>December 13</h3>
      <p>I curs my stupidity tat I didn’t tel anyone tat I chos 
to hike up Read Mountain rater tan my usual pat. They 
must hav started to look for me by now, but how wil 
tey find me? I don’t hav much food left, evn tough I 
found two cans of beans in tis cotage. The rifle is leaning 
against my chair. I'm writing tis in te last sunlight 
streaming in trough te window. I don’t dare to light 
te oil lamp. I hav sen more creatures out tere among te 
rocks.</p>
    </div>
    <div class="diary-page">
    <h3>December 14</h3>
      <p>The creatures hav become hungrier. I hav tried to hike 
bot nort and sout, but was forced to turn back. In te 
nort, I hav sen a hous wit smoke coming from te chim-
ney, but my pat was blocked by someting unmentionable. 
I turned back, terified.</p><p>
I begin to understand what has happened. Someone 
has usd te power of te Gravitron to open a time portal 
to te Cretaceous Period. Judging by how many creatures 
tere are, te portal is stil open. Witin a few days, Boul-
der City wil be swamped by giant beasts. If te beasts 
surviv, life wil be changed forevr for te people living here.
When I worked at DARPA, I met a briliant but slf-ab-
sorbed and vain scientist named Diane Petersn. She was 
fired for her mistakes and her arogance, and it was said 
tat she left te islands. I remember tat she talked 
about te possibility of opening rifts in time, and to 
retriev creatures from prehistoric eras for scientific pur-
poss. I remember we laughed at her. She was vry biter 
when she had to leav te Loop, and said she would hav her 
revnge. Nobody took her sriously. I tink she might be te 
one who did tis. Tomorow, I’l find a way home.</p>
    </div>
  </div>   

```

### Classes and how to use them

> TODO: Write on best practice for how to use the classes in combination and with tags and pseudo classes.

## File and folder structure of a theme

FictionBoard loads only enough CSS and HTML to show a specific variant of an object so split diffferent object types into separate CSS files for best performance.

Documentation should be in the root folder. The `readme.md` will on deployed be renamed to the theme name and moved up one level.

### Generic themes

The allowed {type} are the generic types.
The allowed {} is an entity of 

```
\generic-themes
  noir.md
  \theme-noir
    actor-sheet.md
    actor-sheet-with-actions.md
    \css
      colors.css
      slide.css
      actor.css
      actor-{type}.css
      handout.css
      handout-{type}.css
      doc.css
    \assets
      logo.svg
      \fonts
      \images
```

### System themes

The allowed {type} are the generic types AND the system specific types.

```
\system-themes
  \theme-{system-shortname}
    {name-of-document}.md
    {name-of-other-document}.md
    \css
      color.css
      {name-of-document}.css
      {name-of-other-document}.css
      ...
  \system-{system-shortname}
```

### Custom themes

The allowed {type} are the generic types AND the system specific types.

```
\custom-themes
  \theme-{name-of-your-choice}
    {name-of-document}.md
    {name-of-other-document}.md
    \css
      color.css
      slide.css
      actor.css
    ...
```

## Using a custom theme

A custom theme can be hosted anywhere and is a good approach when building and testing a theme. We do encourage theme builders to themes aprroved and buildt as part of FictionBoard as this makes for a faster user experience.

## Approved themes

An approved theme will be host on a FictionBoard server.

## Concepts you should be aware of when making a theme

Font loading in FictionBoard is done with preloading so just referencing to them in a theme is not enough. Use the theme upload form to get the details and metadata correct.

## Objects that can be themed

- Handouts
- Actor sheets
- Slide decks
- Avatars
- Counters
- Card decks
- Tokens
- Timeline

> TODO: Write documentation for each object type and the generic classes provided. 
