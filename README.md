# Android-Tapping-Game
Pop the red balls from the screen 

This is a very basic implementation. There can be cases of spotty touch mechanics. 

GameView class : The GameView class is primarily used to set the stage of the game. The class itself calls the SpriteClass(discussed later) to set the elements on stage, but the touch events(MotionEvent) is fired in this class. This class extends the SurfaceView class, which also holds the SurfaceHolder. These elements are the two distinguished features of this class. An array list is used to add the 2 type of balls that are used, as well as the onTouchEvent() which is used to detect if a ball(sprite) is being touched. 
GameLoop class : The GameLoop is the backbone of the classes which determines what elements will be drawn on the canvas at what time. It is necessary to use a synchronized block for the GameHolder object since simultaneous access can be messy on the canvas. The finally block makes sure to unlock the canvas for other threads. The FPS decides in how many ms will the canvas be needed to refresh. 
SpriteClass class : the SpriteClass just updates the movement of the sprites on the canvas, as well as reverses the direction if they collide on the end screen. A random position and speed is set at every new instance the game is launched. The isColliding() method is called from the GameView class which basically checks if the user has tapped at the correct position and if there is indeed a collision. 
The MainActivity : This is only used to initiate the GameView class.

Common methods in all classes : 
onDraw() : This method is not found in the GameLoop class since it has nothing to contribute to the sprites being on stage, but just control the FPS and the sleep state. This method is bascially called again and again to draw on stage.
onDraw() in GameView : This method is only used to display the .png used in the arrayList.
onDraw() in SpriteClass : This method is used to update the positions of each sprite(with position and movementSpeed) with the help of the Update() function.

The rest of the methods are self explanatory.
Future Scope : Plans to make a decent framework, which could be integrated in any game with a few basic options in a game intro menu.
				Create another intro menu which could help navigate to a few other games which we intend to create as part of the project.
				Plan to integrate SQLite to keep track of high scores.
				
Fixes : Need to fix the scoring feature and the game shut feature (when all red balls have been dissolved, pop a menu for restart)
