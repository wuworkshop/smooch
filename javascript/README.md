# Contents

  * [JavaScript front-end](#javascript-front-end)
    * [doll.js](#dolljs)
    * [setdata.js](#setdatajs)
  * [reader.html and reader.js](#readerhtml-and-readerjs)

# JavaScript front-end

The "front-end" of Smooch is just a few files. There's some HTML, a
CSS file, and two JavaScript files.

## doll.js

This is the JavaScript for the viewer. It's all vanilla JavaScript,
no libraries or anything.

### the ghost canvas

I'm using a game coding technique called a "ghost buffer" to detect
what images are being clicked on.

If you load a doll and right click and inspect the DOM, you'll see there's a
undisplayed second canvas besides the one that you can see and interact with.
That's the ghost canvas. If you remove the `display: none` from the CSS, you'll
be able to see it -- it's right below the actual canvas and has a bright blue
background. Each item in the real canvas is also drawn on the ghost canvas, but
in shades of black to red. Each item is a subtly different color.

When a player clicks on the real canvas, the JavaScript looks up the
corresponding pixel on the ghost canvas. Each color on the ghost canvas maps to
one object in the set, so the script knows which object you clicked!

## setdata.js

This is mostly JSON representing the KiSS doll set's configuration,
generated by Haskell side of the app. This script is just two variable
declarations.

### kissJson

Here's JSON for a set with one object:

```(json)
{
  // the size of the play area
  "window_size": [
    700,
    430
  ],
  "objs": [
  // an object has an id number, a list of cels, and a
  // list of positions
    {
      "id": 0,
      "cells": [
      // a cell has a palette for the cel, the sets the cel
      // is visible in, a "fix" value indicating how many
      // time you need to click the cel before you can
      // drag it (usually 0 for clothes, a large number for
      // the body), a name, and how transparent it should be.
        {
          "palette": 0,
          "sets": [
            1,
            2,
            3,
            4,
            5,
            6,
            7,
            8,
            9
          ],
          "fix": 4000,
          "name": "aurora",
          "alpha": 0
        }
      ],
      "positions": [
        {
          "y": 0,
          "x": 0
        },
        {
          "y": 67,
          "x": 283
        },
        {
          "y": 67,
          "x": 283
        },
        {
          "y": 67,
          "x": 283
        },
        {
          "y": 67,
          "x": 283
        },
        {
          "y": 67,
          "x": 283
        },
        {
          "y": 67,
          "x": 283
        },
        {
          "y": 67,
          "x": 283
        },
        {
          "y": 67,
          "x": 283
        },
        {
          "y": 67,
          "x": 283
        }
      ]
    }
  ]
}
```

### celJson

This is only the cel parts of the JSON.

```(json)
 {
 "palette": 0,
 "sets": [
        1,
        2,
        3,
        4,
        5,
        6,
        7,
        8,
        9
      ],
  "fix": 0,
  "name": "fuzzskir",
  "alpha": 0
  "offset": {
    "x": 0,
    "y": 0
    }
 }

```

# reader.html and reader.js

These two files are an experiment with reading cels directly in JavaScript. They
aren't currently used by the app at all.
