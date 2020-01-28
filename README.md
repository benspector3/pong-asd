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

# TODOs

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

**CODE: Modify the contents of the `<div id="board">` element such that it contains a `<div>` for the two paddle (left and right) and the ball**

Your HTML should look like this:

```html
<div id = "board"> 
  <div id = "leftPaddle"> </div>
  <div id = "ball"> </div>
  <div id = "rightPaddle"> </div>
</div>
```

Save your code and refresh your game. The box is now gone but where are the ball and paddles? Remember, in order for these elements to look like anything, we need to add CSS! 

**Something to note here**: In my code above, the ball is between the left and right paddle. Later on, we will be positioning these elements within the board using absolute coordinates. Therefore, the order in which they are written in HTML won't matter.

## TODO 2: ADD CSS for the paddles and the ball

Open the `index.css` file.

Now that we have HTML elements for our 3 game items, let's add some style to them so we can see them. For most projects, we'll be using simple 2D shapes since they are relatively easy to render with basic HTML and CSS skills.

**CODE: Add 3 new style rules, one for each gameItem's unique id following the template below **

```css
#id {
  /* size and shape */
  width: 20px;
  height: 20px;
  background-color: white;
}
``` 

**Code: Now, make the following changes
- **Paddles should have width: 20px and height: 80px**
- **The ball should have border-radius: 20px**
- **Each paddle should have a unique background-color**

At this point your game should look like this:


