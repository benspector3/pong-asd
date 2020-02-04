# Setup

To install this project, first clone the [template](https://github.com/benspector3/asd-template/) repository by entering these commands into your bash terminal:

```bash
git clone https://github.com/benspector3/asd-template.git
rm -rf asd-template/.git
```

Then, rename the folder to `pong`

# Learning Objectives
- Build your first project using the template repository
- Practice modeling data with Objects
- Learn a method for handling key events
- Discover the algorithm for detecting collisions between objects

# Planning

Always start any programming task by clarifying what you want to do and then breaking it down into small steps. Small steps can get you just about anywhere if you’ve got enough time. If you get stuck, break it down smaller!

To help, there are a few ca

## User Story / Gameplay
- Describe the gameplay
- What are the conditions when the game begins? 
- Does the game have an end? If so, what are the conditions for when it ends?
- What `if`s will there be?

## Visual Game Components:
- Which will be static?
- Which will be animated?
- What data will you need to model each game component?
  - Common data values needed for moving components: `x`, `y`, `velocityX`, `velocityY`

## Events / Logic 
- What events will occur in this game? (timer events, keyboard events, clicking events?)
- For each "event", write out the high-level logic of what will happen. It is better (and tricky) to be as specific as you can while remaining high-level!

**Bouncing Box Example:**

1. When the user clicks on the box --> the score increases and is displayed on the box, the speed increases, the box is reset to the starting position. 
2. When the timer ticks --> the box will move forward in some direction, if it hits the edge of the screen, reverse the direction 

# Helpful Functions

Below are some funcitons we've written in the past that may be helpful to you in this project:

### Repositioning DOM Elements

This function can be used to reposition DOM elements at absolute positions on the screen by manipulating the CSS properties `left` and `top`. 

This function assumes that we have the following _global_ data values:
- `$gameItem`: the jQuery Object for a `<div id="gameItem">` element
- `x`: the x-coordinate / `left` value of the `$gameItem`
- `y`: the y-coordinate / `top` value of the `$gameItem`
- `velocityX`: the velocity (pixels/frame) along the x-axis of the `$gameItem`
- `velocityY`: the velocity (pixels/frame) along the y-axis of the `$gameItem`

```js
function moveGameItem() {
  x += velocityX;
  y += velocityY;
  $gameItem.css("left", positionX);
  $gameItem.css("top", positionY);
}
```

Assuming that we will be managing the data of multiple DOM elements, we will need to refactor this function such that it can handle _any_ `$gameItem` with its own `x`, `y`, `velocityX`, and `velocityY` values. 

### Keybord Inputs

This function assumes that the event `"keydown"` is being listened for. You can change what events are being listend for in the function `turnOnEvents`. 

```js
var KEYCODE = {
  ENTER: 13,
}

function handleKeyDown() {
  var keycode = event.which;
  console.log(keycode);
  
  if (keycode === 13) {
    console.log("enter pressed");
  }
}
```

# TODOs

The plan for building Pong will be as follows:
1. Create the DOM elements needed for the game with HTML and CSS
2. Model the DOM elements with data objects
3. Reposition the DOM elements on the screen using jQuery
4. Move the paddles in response to keyboard events
5. Move the ball in response to timed events
6. Bounce the ball when it collides with anything
7. Identify when a point ends and what to do to start a new point
8. End the game when 11 points are reached

## TODO 0: Run the template program and understand the basic structure

Before we begin coding, open the `index.html` file and press **Preview** to see what we're starting with. It looks like the beginning of bouncing box, right?

Take 10 minutes to look at the code in each of the three files to get a sense of how this template is laid out. 

## TODO 1: Add HTML for paddles and the ball

Open the `index.html` file. You should see this in the body:

```html
<body>
  <div id='board'>
    <div id='gameItem'></div>
  </div>
</body>
```

Each project in this class will be build on some kind of `board` with various `gameItems` that are on the board. For this project, there are only 3 game items:
- the left paddle
- the ball
- the right paddle

Each one of these game items needs to be represented in HTML. 

**CODE: Add `<div>` elements for the ball and the two paddle (left and right) as children of the `<div id="board">` element. Each element should have a unique id.**

HINT: To create a div with a particular `id` attribute, place the `id=""` attribute inside the opening tag:

```html
<div id="uniqueElement"> </div>
```

Save your code and refresh your game. The box is now gone but where are the ball and paddles? If you inspect the body, you'll see them in the DOM but in order for these elements to look like anything, we need to add CSS! 

## TODO 2: ADD CSS for the paddles and the ball

Open the `index.css` file.

Now that we have HTML elements for our 3 game items, let's add some style to them so we can see them. For most projects, we'll be using simple 2D shapes since they are relatively easy to render with basic HTML and CSS skills.

**CODE: Add 3 new style rules, one for each gameItem's unique id following the template below**

```css
#id {
  /* size and shape */
  width: 20px;
  height: 20px;
  background-color: white;
}
``` 

**Code: Now, make the following changes**
- Paddles should have `width: 20px;` and `height: 80px;`
- Each paddle should have a unique `background-color`
- The ball should have `width:20px;`, `height:20px` and `border-radius: 20px;`

If your elements only have these CSS properties, they should look something like this:

<img src="img/todo2-no-positioning.png" width=250>

Let's get the ball and paddle out of the top corner. 

**CODE: Add the following CSS comment and properties to each of your CSS blocks. Then, specify each game item's `top` and `left` properties so that they are in good starting positions:**

```css
/* positioning */
position: absolute;
top: 100px;
left: 100px;
```

The `position: absolute` property allows us to use the `top` and `left` properties to position HTML elements anywhere we want on the screen. `top` is equivalent to setting the y-coordinate and `left` is equivalent to the x-coordinate.

**Did you struggle finding the right position for the right paddle? Using JavaScript + jQuery will make this much easier! To the next TODO!**

## TODO 3: Set the starting positions for the ball and paddles with JavaScript and jQuery

One of the most common tasks in video game programming is positioning and re-positioning elements on the screen. On each frame, the ball will have to move and, if the players are pressing down any keys, the paddles will likely have to move as well.

First, we'll need to select each of our DOM elements and save a reference to them in JavaScript - we'll be referencing them a lot!

Then, we can write a helper function that can reposition _any_ DOM element using jQuery by modifying the `top` and `left` CSS properties. Rememember, `top` is equivalent to the y-coordinate and `left` is equivalent to the x-coordinate. By writing a helper function, we can reduce repetition and practice our skills of **Abstraction**!

#### Step 1: Select DOM Elements 

In the INITIALIZATION section

#### Step 2: Create the repositionElement helper function

In the HELPER FUNCTIONS section

#### Step 3: Set the starting positions 

At the bottom of the INITIALIZATION section


