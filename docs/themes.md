# Themes

FictionBoard allows for custom theming of handouts, slide decks, actor sheets and other objects. 

Theming is highly encouraged to create an immersive experience relevant to your story. Themes should be generic and preferably genre oriented or game system specific. 

## Basic concepts

The HTML of objects in FictionBoard is purposly kept quite simple to improve accessibility and make them possible to express in written text.

A more complex object such as an actor sheet is written as a set of headers, list, key value pairs, text and links. To create a rendering of the object, FictionBoard splits texts into chunks. A chunk is represented by a div with class derived from object type and the header from which the chunk is created. The chunks are contained within a div with class according to type and theme.

### Example HTML

```
<body class="system-{game-system} theme-{selected-theme}">

  <div class="handout-{type}">
    <h2>Name of handout</h2>
    <div class="{type}-{chunk-name}">
      Content
    </div>
    <div class="{type}-{chunk-name}">
      Content
    </div>
    <div class="{type}-{chunk-name}">
      Content
    </div>
  </div>   

```
 {game-system} - Derived from the system you are playing
 {selected-theme} - Derived from theme setting. Fallback to default game system template if theme not set. 
 {type} - Derived from the top level header or type property (Found in frontmatter). Can be overridden at the time of use (Change a diary note to a letter)
 {chunk-name} - Derived from a secondary header

### Example from Tales from the loop

A handout of diary notes

```
<body class="system-tftl theme-eighties">

  <div class="handout-diary">
    <h1>Letter found on pavement</h1>
    <div class="diary-page">
      <h2>December 12</h2>
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
      <h2>December 13</h2>
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
    <h2>December 14</h2>
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

## File and folder structure of a theme

FictionBoard loads only enough CSS and HTML to show a specific variant of an object so split diffferent object types into separate CSS files for best performance.

### Generic themes

The allowed {type} are the generic types. 

\themes
  \theme-noir
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

### System themes

The allowed {type} are the generic types AND the system specific types

\system-themes
  \theme-{system}
    color.css
    ...

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

> TODO: Write documentation for each object type. 
