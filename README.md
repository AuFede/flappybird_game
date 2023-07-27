# FLAPPY BIRD PSEUDOCLONE:

---
## STARTING

1. Create HTML boilerplate.
2. Link Google Fonts : [Teko Google Fonts](https://fonts.googleapis.com/css?family=Teko:700 "Teko:700"), below the title.
3. Inside the body, we introduce the canvas element with: ID, width and height.
4. Above the final body element, we introduce the JS script.
5. In the body, we add style, inside we work with the canvas (border, display, margin).
6. Take an image and make a favicon with: [FAVICON Generator](https://www.favicon-generator.org/ "Web for favicon generator").

---
## DRAW TO CANVAS

1. Select the canvas element, define the const.
2. Then get the Context, define the const.
3. We create a function called draw, this function will handle all the drawing we'll do to the canvas.
4. We create a loop function, that will call the draw function. We need a loop function because we need to update our game every second.
5. Inside the loop function we will use the request animation frame, wich take in a callback function that is the loop function.
6. Finally we need to call the loop again after the loop function.
7. If we move down the bird to the bottom there will be a repetition of the bird image, so we must clear the first bird and then the second,etc.
8. To clear the canvas i will need to draw a rectangle wich has the same dimensions as our canvas. i will use ctx.fillStyle and set the color to fill the rectangle.
9. Then i will use the method fillRect wich takes the "x" and "y" position of the rectangle. The x is equal to 0 and the y is equal to 0, so is the top-left corner of the rectangle. The width and the height will be the same as the canvas. (0, 0, cvs.width, cvs.height).
10. We need to complete the other images. To make the game a real one, all we need is to update the position of these images. Wich means that i will need and update function(inside our loop function).
11. We also need to create a variable called frames, wich i will set to 0 and then each time i call the loop function i will increment that variable by 1. Inside the loop function: frame ++.

---
## DRAW IMAGE TO CANVAS

1. To draw an image to the canvas we will use our source image, we must take the sprite and drop to the destination canvas.
2. First we need to load our image, so i will create a constant sprite equals to new Image(). This will allow us to use an image object using the image constructor.
3. Then i will set the source property of our image: sprite.src.
Inside the source image, for example, the "Game Over" has an "s" before X and an "s" before the Y (source exposition), then a source height and a source width. When we need to draw the Game Over in our canvas, we should give these parameters: destination X position, destination Y position, destination width and destination height.
4. To draw an image to the canvas i will use drawImage() method. So it will be: context(ctx) dot drawImage(), and the last will taken these parameters (the image itself(image-sprite), the sX, the sY,  the s.Width and the s.Height, the dX, the dY, the d.Width, the d.Height).
5. We have a lot of images in the sprite, so we need to create an object with a name (const = name {}). The name would be background, foreground, pipes, bird. Inside the object we have the properties like sX:276, sY:112, the width and the height will still the same 'cause the destination canvas and the source is the same size, etc.
6. Then for every object we will need a draw method. Inside will use context (ctx.drawImage()).
7. Besides, to draw this image, we need to go inside the draw function then use the name of the object dot the draw method(name.draw())

---
## FIT AN IMAGE

1. If we try to draw our background image to canvas, we will get an image that doesn't fit. So we need to draw another background image to the side. The question is wich POSITION we need to use in every case. The background image have the same "this.y" position, so we must add another line of code.

---
## DRAW THE BIRD 

1. For our bird, inside the object we have an animation array 'cause we have different images of the bird. With those different images we will create an animation. Inside the animation, we use sX and sY position, the bird image is flapping in the game.
2. In the last line inside animation we will put the second line with the sX and sY position, because we need the flappy effect.
3. To create the animation we will need a property called frame, set to 0.
4. Inside the draw method, we need to create a variable called bird. The let bird is equal to this.animation (our array). With an index this.frame [].
5. For the wing animation "this.frame" update the frame, increment the frame every period.
6. And we use the drawImage method for the ctx, wich takes in the bird search exposition and the bird source position. Here we need to center the bird. For that we SUSTRACT the half of the width from the "x" position (this.w/2) and the half of the hight of the "y" position.

---
## GAME STATE

1. Some images are on the top of the others, to fix that we need to implement the Game State. In our game we have three game States: the get ready state : 0, the game state : 1 and the game over state : 2. So, i will need and object called state, inside we put the properties wich are the game states and a current : 0 property, that will keep track the state that we are in. If the current property change the game state change, so the only property that changes is the current state.
2. If the user clicks on the canvas, we must go from the get ready state to the game state (0 --- 1). Then, if the user clicks on the canvas we won't get any of the states, instead we need to make the bird flap. So, our bird has a method called flap() that we must create.
3. Then the player loses the game and is in the game over state (1 --- 2), if he clicks on the start button then we need to go from the gameover state to the getready state (2 --- 0). In terms of code we need to add an event listener to our canvas wich is a click event, this will fire up a function on the canvas, that will take in the event variable wich is the click event. An other important thing is change the ""document.addEventListener" to "cvs.addEventListener".
4. Inside the event function we will use a switch statement to change the current state.
5. An update for the getReady object is that we only need to draw the "get ready" message if "state.current == state.getReady".
6. Also, we only need to show the gameOver message if "state.current == state.over".

---
## ANIMATE THE BIRD

1. Inside the bird object we must add an update method, wich will just update the bird frame to make the bird flapping.


2. Inside the update function we have a loop function and inside the loop function we have a requestAnimationFrame(loop) to create the loop and we have an incrementator: frames++;

* When the game start the frames variable is set to 0: "frames = 0", also the this.frame property of our bird object is set to 0: "this.frame = 0". Now, we need to check every frame of the loop, for this we must use module of 5, so: "frames % 5 == 0".

* If "frames % 5 == 0" we need to increment this.frame by 1: "this.frame += 1". Incremented this by 1 means change the variable bird that we're drawing, wich means CREATING AN ANIMATION. In 0, 5, 10 and 15 frames the condition is regular.

* Inside the update function we put the condition. There is a problem when we are in frames = 20, because the condition is equal to "0". In our animation array we just have four elements. So we must create another condition for the animation array. Inside the update function: this.frame += frames %   5  == 0 ? 1:0;

* The new condition is, if the this.animation.length => 4, if "this.frame = 0" for : "0 % 4", then we increment, But, if we say that: "this.frame = 4" then ""4 % 4 = 0". So, this is it. Below the other condition, inside the update function: this.frame = this.frame % this.animation.length;

* We must now that, when the game start (get ready state), the bird must flap slowly. But instead, if the bird is in the game state, the bird must flap faster. The speed of flappinf of the bird is based on period, higher the period = slowly is the flapping. The period is the "5" that we put in the condition.

* So, we need to say if "state.current == state.getReady ? 10 : 5;", then the bird flap slowly if not the bird flap faster. The new line code is: "this.period = state.current == state.getReady ? 10 : 5;"

* Now, we can change the 5 of the other line of code, so we can put: "this.frame += frames % this.period == 0 ? 1 : 0;"

---
## GRAVITY AND FLAP

1. Our bird must go to the top or to the bottom by speed, go to the top when the user clicks on the canvas and go to the bottom by the gravity. So, inside our bird object we'll set the speed to 0 when the game start, the gravity is set to 0.25 and the jump or the flap is set to 4.6 (we can use different values for the gravity and the jump if we want).

2. Inside our update function: update: function(){if(state.current == state.getReady) {this.y = 150;}} else {this.speed += this.gravity; this.y += this.speed;}. Then the speed will go like this:"speed = 0, speed = 0.25, speed = 0.5, speed = 0.75".

3. In the flap function: flap : function(){this.speed = - this.jump;}.

4. Now, we need a collision detection, so we have a cvs.height (the bottom of the canvas), the foreground.height wich is the light-brown part and finally in the top(the floor), we have the cvs.height - foreground.height.

5. So, we determine that is a game over when the bird touches the floor (cvs.height - fg.h). The bird has this construction: It's center is 'this.y' and the entire bird is 'this.h', then the bottom of the bird is 'this.y + this.h/2'.

6. The final code line result for the collision detection is inside the else, we put another if-statement. The line code is: if(this.y + this.h/2 >= cvs.height-fg.h) {this.y = cvs.height - fg.h - this.h/2; if(state.current == state.game) {state.current = state.over;}}.

7. After gameover we must stop the flap of the bird. So, we reset position with: "this.y=150;".

---
## BIRD ROTATION

1. When the bird is in the getReady state, it's angle of rotation is 0 degrees. But if it's flapping to the top the angle changes to -25 degrees, otherwise if the bird is falling down, the rotation angle is 90 degrees. The real problem is that we don't have any way to rotate the image, so we must rotate de canvas.

2. The top left corner of the canvas is (0,0),  the x axis and the y axis. To rotate the canvas, we use: ctx.rotate(angle).

3. The "angle" must given in a radian, so we must calculate it. For example if we want to rotate the canvas 45 degrees, we must use something like this: ctx.rotate(45 * Math.PI/180). Inside the parenthesis we use a conversion, we convert from degrees to radians.

* The canvas wall will rotate 45 degrees from the x axis and of course the center of the rotation(0,0) as the origin of our canvas.

* So, we need to rotate the bird (this.x, this.y), so means that the center of the rotation will be the center of the bird. Then we must take the center of the rotation of the origin (0,0) to the (this.x, this.y) of the bird. For this, we will use translate method (REMEMBER: we are translating the origin position to the x and y position of the bird), so we will use this: ctx.translate(this.x, this.y); ctx.rotate(angle). It's a sort of displace the canvas.

* Another important thing is this lines of code we must put it above our bird code lines.

* We know that all the other elements will rotate too, like the background, the pipes, the foreground,etc. To just rotate the image of the bird, we must save the old state of the canvas with this line of code: "ctx.save();"

* After we change the state of the canvas, we must restore the state to get back the old state. So, we use: "restore();".

4. Now, let's talk about the conversion. We know that `180° it's equal to PI` in radian. For example, if we want to convert `45° into radiant`, we must say something like this: `x = 45° * PI / 180°` ---> `45 * DEGREE`. In terms of code we will use:   

``` javascript
const DEGREE = Math.PI/180;
```

* Then, to rotate our bird, inside our draw method we will use:

``` javascript
ctx.rotate(this.rotation);
```
* Inside our const bird, we use:

``` javascript
// 2
const bird = {
    rotation : 0,
// 3
    draw : function(){
        let bird = this.animation[this.frame];
// 5.We must save the state before any action.
    ctx.save();
// 4. We must translate, before the rotation.
    ctx.translate(this.x, this.y);
// 1
    ctx.rotate(this.rotation);
// 3
    ctx.drawImage(sprite, bird.sX, bird.sY, this.w, this.h, -this.w/2, -this.h/2, this.w, this.h);
// 6. Finally restore the old state.
    ctx.restore();
    },
}
```
> Something we really need to consider after we translated the origin (0,0) of the canvas to the bird center-origin, is that in our ctx.drawImage() WE ARE NOT SAYING ANYMORE this.x - this.w/2 or this.y - this.h/2 BECAUSE THE "X" AND "Y" POSITION ARE INSIDE OUR ctx.translate().

---

## BIRD UPDATE()

1. Other important thing is that inside our bird object is when the bird is in `(state.current === state.getReady)`, then we need to set the rotation of the bird to zero `this.rotation = 0 * DEGREE;`. Then the code will be something like this:

``` javascript
update: function(){
        this.period = state.current == state.getReady ? 10 : 5;

        this.frame += frames%this.period == 0 ? 1 : 0;

        this.frame = this.frame%this.animation.length;
        
        if(state.current == state.getReady){
            this.y = 150;
            this.rotation = 0 * DEGREE; // 1. WE ADD THIS LINE OF CODE.
        }else {
            this.speed += this.gravity;
            this.y += this.speed;

            if(this.y + this.h/2 >= cvs.height - fg.h){

                this.y = cvs.height - fg.h - this.h/2;

                if(state.current == state.game){
                    state.current = state.over;
                }
            }
        }
    }
```

2. We said that we are incrementing the speed by the gravity `this.speed += this.gravity;`. Let's say now that the player clicked on the canvas, this means that the bird will flap. In other words the `this.y` will be `-4.6` because when the bird flaps we change the speed too.

* Now let's say that we don't click on the canvas, the bird will keep falling down until it reaches `4.6`. This means that when the bird goes from `-4.6` to `0` to `4.6` it's falling down, without any reaction from the player. 
So at `4.6` we need to change the rotation of the bird to `90°`, then we must check with `this.speed >= this.jump`, if thats true then `this.rotation = 90 * DEGREE;`, else if the `bird.flap();` we need to change that to `this.rotation = - 25 * DEGREE;`

* Another thing is when the bird is falling down obvioulsy the bird isn't flapping anymore. We must change the frame inside our if statement, so `this.frame = 1;`. With this we stop the bird.

``` javascript
update: function(){
        this.period = state.current == state.getReady ? 10 : 5;
        this.frame += frames%this.period == 0 ? 1 : 0;
        this.frame = this.frame%this.animation.length;
        
        if(state.current == state.getReady){
            this.y = 150;
            this.rotation = 0 * DEGREE; // 1. WE ADD THIS.
        }else {
            this.speed += this.gravity;
            this.y += this.speed;

            if(this.y + this.h/2 >= cvs.height - fg.h){
                this.y = cvs.height - fg.h - this.h/2;
                if(state.current == state.game){
                    state.current = state.over;
                }
            }
        //2. WE ADD A NEW IF-ELSE
        if(this.speed >= this.jump) {
            this.rotation = 90 * DEGREE;
            this.frame = 1;// 4. WE STOP THE BIRD FLAPPING

        }else{
            this.rotation = - 25 * DEGREE;//3. THE BIRD FLAPS
        }

        }
    }
```
---
## MOVE FOREGROUND

1. The bird must be looking like it's going forward, to make that happen we will create an illusion. So, we are moving to the left and the illusion is that the bird is going to the right. We need to move the ground to the left by `dx : 2,`, this means that we're changing the `x position` by `dx`. There will be an update function that will just to do that, only if `state.current == state.game`. Inside the if-statement we decrement the `x` position by the `d` position.

``` javascript
const fg = {
    sX: 276,
    sY: 0,
    w: 224,
    h: 112,
    x: 0,
    dx: 2, // 1

    update : function(){ //2
        if(state.current == state.game) {
                (this.x - this.dx) % (this.w/2); //3 y 4
        }

    }
}
```

* There is an issue if we keep the decrement, the wall foreground will leave our canvas. So to fix that we must to keep moving the foreground to the left until some point, and then take it back to zero, we do this with ` % (this.w/2); `.

* The explanation: `(this.x - this.dx) % (this.w / 2)`. In terms of numbers:
`(0 - 2) % ( 224 / 2)`

`(0 - 2) % 112` ---> `-2 % 112` ---> `-2` 

`(-2 -2) % 112` ---> `-4 % 112` ---> `-4`

`(-4 -2) % 112` ---> `-6 % 112` ---> `-6`

`(-6 -2) % 112` ---> `-8 % 112` ---> `-8`

                    .

                    .

                    .

`(-100 -2) % 112` ---> `-110 % 112` ---> `-110`

`(-110 -2) % 112` ---> `-112 % 112` ---> `0`. HERE THE X POSITION IN 0 BACKS TO 0.

---
## CREATE THE PIPES




  
              





versión TRYHARD:

gravity : 0.25,
jump : 4.6,

gap : 85,

// MOVE THE PIPES TO THE LEFT
p.x -= this.dx;
