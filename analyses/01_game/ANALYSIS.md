CompSci 308: Game Analysis
===================

> This is the link to the Analysis Description: [Analysis - Game](http://www.cs.duke.edu/courses/compsci308/fall15/assign/01_game/part3.php)

Project Journal
=======

###Time Review
I spent about 50 hours working on this project. I started on 08/25/2015, and finished on 09/03/2015. I spend about an hour planning my project. In the plan phase, I made a list of entities that became classes later. I also had rough sketches of how I want the final design to look. I had description of how entities in the game can interact with each other, but one thing I want to improve in my plan phase is to have methods definition and return values specified at this stage similar to the RPS exercise we did in recitation. I also spend time watching tutorials online and reading the course materials.

After the plan phase, I started coding. I divided the project in three main parts depending on functionality into: Main, level one, and level two. I coded these three main components sequentially starting with Main class. I also spent about four hours debugging issues in my design. I went to office hours for about two hours while I was debugging, and the UTAs were extremely helpful. Not only they helped me fix my errors, but they also suggested ways for me to improve my design and make it easy to follow. 
I also spend about three hours refactoring after 09/01/2015 lecture in accordance with Professor Duvall's instructions

The hardest tasks I had to do were trying to figure out how to change between scenes, how to make the background move continuously, and understanding lambda and keyhandle methods. These tasks required me to spend several hours researching, and trying different code implementation. This is also why I went to office hours.



###Commits

You can put links to commits like this: [My favorite commit](https://github.com/duke-compsci308-fall2015/game_sma45/commit/2da16c355ad002caf998aeaf7b8768240e2a6684)

  I divided my project into three main sections based on functionality or logic in each section. I committed my code every time I finished one of these sections, discovered and fixed a measure bug in current or previous section, or re-factored my code dramatically. Usually the size of a commit included one new class and all of its functions or all the classes on which it depended.  I committed 7 times including a commit for to update Design.txt in the plan phase. I believe that most of my commits messages were meaningful except for one where I write "level one, most functionalities work". Now that I reflect upon it, I do not think that this message is a helpful reference for the future. 


 Other commit messages are more descriptive of what I actually did, for example there is a commit where I describe it as "code re-factored". I submitted this commit after the class lecture. I went through the entire project, and made changes reflect what we talked about in the class that day. I changed all magic numbers into constants, and made all of my variables privates and created more getters and setters for these variables. Furthermore, I extracted a number of methods from class "level two" into their own class because they are similar in nature.
 
 Another commit example is the one labeled " level one completed, menu ready, scene changes correctly". This was an important commit because as I mentioned before I had trouble figuring out how to change scenes. I also had created an infinite loop because I did not create my constructors correctly. I pushed this commit after I went to office hours. I believe that the commit message is very descriptive. The size of the commit was not big in terms of number of lines of code, but it was important because it fixed a null pointer exception that prevented me from going further in my project.

  

###Conclusions
Even though I spend a lot of time on this project, I do not think that I over estimated it because I am not an experienced Java programmer. I think that I will spend less time in the future learning about java syntax, because I have learned a great deal during the past 10 days. I need to continue doing that still. Most of my time was spent on coding as I followed the guidance from the plan phase. 

Debugging took a lot of my time too, but I think that as I do more reading from the lecture, I will spend less time of the kind of mistakes I made in this project. I need to continue make my the results of the planning phase as clear, and as comprehensive as possible, because this helped avoid project creep. I had a very clear idea of where I am on the project, and what outcome I should expect from each phase.


My project contains many Booleans that indicate when a function should be used and in which scene of how many times. If I could work on my project now, I would like to change these switches, and use them less often in my design. Instead, I would like to make my design more readable and less realiable on these switches by using a different mechanics to "activate" a method.

Design Review
=======

###Status
	
I tried to follow naming conventions. I prefixed variables in constructors with "my", I avoided abbreviation in most cases, and I named my methods after what they do. I tried to make my functions short in terms of number of lines of codes. In the beginning I had functions that call other functions in a chain, but after I read tutorials online, and as the UTAs advised me, I removed this dependency by calling all functions pertaining to one class in one function called step. However, that created a problem because not all of these functions are called at the same time. This is why I have a number of if statements that calls these functions. 

I think I have three or four commits in my project. I try to keep my code commit free because to me they are very distracting. I added those commits because they were necessary after I fixed a major bug.

However, my code contains many global variables. One reason I have they variables is that I did not know if it is better to have a global constant even though it is going to be used in one function, or create that constant inside the function directly. I have some local constants, but the majority of them are global to their class. I made sure that they are all private static final after the lecture. 

I am also not sure if it is better for a function to have many parameters or have getters and setters. More specifically, I have functions that get parameters from different classes, and not always do they need all of these parameters.


Describe two pieces of code in detail:

Describe the purpose of this code in the overall project.

What makes this code easy (or hard) to read and understand?

1. Method provideProtection() in levelTwo class:
This method is called from step(). In provideProtectio(), the for loop compares the boundaries of the two floating islands in the scene to the boundaries of any falling rock. If they intersect, the rock's visibility is set to false to show the effect, and from that moment on the rock becomes harmless. The rocks are stored in a a list of type ImageView. The islands are stored in an array of ImageView type of size 2. It was a design choice to put the rocks in a list and the islands in an array because the number of rocks is not a constant unlike that of the islands. 

The first line of the method protects the code from nullPointerException by making sure that the two lists are called only when they are not empty because the function is called every 16 seconds throughout the game. The two nested for loops compare every rock to both of the islands. I used for loops to avoid redundancy. Finally only when the boundary of a rock and an island intersect, and the rock is visible, the condition is set true, and the rock is made invisible.

There are no magic numbers in this function to make it easy to follow. Furthermore, this method is short and has a very specific functionality. This method does not call any other method to avoid dependency.


```java
   private void provideProtection() {
		if(rocksList.size()>0 && islands.returnIslandArray().length>0){
			for(ImageView rok: rocksList){
				for(int i =0; i<TWO; i++){
					Boolean condition= rok.getBoundsInParent().intersects(islands.returnIslandArray()[i].getBoundsInParent())&&(rok.isVisible()==true);
					if(condition){
						rok.setVisible(false);
					}
				}
			}
		}
```

2. ButtonClicked() decides which scene to show based on the button clicked. A new scene with a new level or instruction is shown in three out of the four cases. The logic for these cases is similar; the difference is which class is called when the frame is created and which TimeLine. Each branch of the if  statement does the following: If this is the first time the button is clicked, it creates a new frame and a new timeline.T hen it initiates the corresponding scene. If the button has been clicked before(i.e. a scene has been created before) the it only initiates the corresponding scene. playLevel1 and playLevel2 are Boolean variables that indicate the level to initiate. If these variables are not included, NullPointerException error occurs.
This is the function:

```java
 private void ButtonClicked(ActionEvent actionevent) {
		if (actionevent.getSource()==btn1){
			if(playLevel1){
			final KeyFrame frame = new KeyFrame(Duration.millis(MILLISECOND_DELAY),
                    e -> myGame.step());
			Timeline animation = new Timeline();
			animation.setCycleCount(Timeline.INDEFINITE);
			animation.getKeyFrames().add(frame);
			an = animation;
			animation.play();
			playLevel1=false;
			}
			scene2 = myGame.init(width, height, stage, scene);
			stage.setScene(scene2);
			stage.show();
		}
		else if (actionevent.getSource()==btn2){
			if(playLevel2==true){
			final  KeyFrame frame2 = new KeyFrame(Duration.millis(MILLISECOND_DELAY),
	                e -> myGame2.step());
	        Timeline animation2 = new Timeline();
	        animation2.setCycleCount(Timeline.INDEFINITE);
	        animation2.getKeyFrames().add(frame2);
	        an2= animation2;
	        animation2.play();
	        playLevel2=false;
	        }
			scene3 = myGame2.init(width, height, stage, scene);
			stage.setScene(scene3);
			stage.show();
			}
		else if (actionevent.getSource()==btn3){
			System.exit(0);
		}
		else if (actionevent.getSource()==btn4){
			scene4 = myGame3.init(width, height, stage, scene);
			stage.setScene(scene4);
			stage.show();

		}
	}

```

From this, I re-factored this function into three functions in my masterpiece. The first function is called createTimeLine() that takes a frame and creates a timeline and plays its animation. The second method is callInitScene() that takes a scene and an integer. Both are used to identify and initialize the correct scene. 

Bellow is the re-factored version of the function:



```jave

 private void ButtonClicked(ActionEvent actionevent) {
		if (actionevent.getSource()==listOFButtons[0]){
			if(playLevel1){
				final  KeyFrame frame =  new KeyFrame(Duration.millis(MILLISECOND_DELAY),
				        e -> myGame.step());
				createTimeLine(frame);
				playLevel1=false;
				}
			callInitScene(scene2, ONE);
			}
		else if (actionevent.getSource()==listOFButtons[ONE]){
			if(playLevel2==true){
				final  KeyFrame frame2 =  new KeyFrame(Duration.millis(MILLISECOND_DELAY),
				        e -> myGame2.step());
				createTimeLine(frame2);
				playLevel2=false;
				}
			callInitScene(scene3,TWO);
			}
		else if (actionevent.getSource()==listOFButtons[THREE]){
			System.exit(0);
			}
		else if (actionevent.getSource()==listOFButtons[TWO]){
			callInitScene(scene4,THREE);
			}
	}
	
	private void callInitScene(Scene tempScene, int i) {
		if(i==ONE){
			tempScene = myGame.init(width, height, stage, thisScene);
			}
		if(i==TWO){
			tempScene = myGame2.init(width, height, stage, thisScene);
			}
		else if(i==THREE){tempScene = myGame3.init(width, height, stage, thisScene);}
		stage.setScene(tempScene);
		stage.show();
	}
	
	private void createTimeLine(KeyFrame tempFrame) {
		Timeline animation = new Timeline();
		animation.setCycleCount(Timeline.INDEFINITE);
		animation.getKeyFrames().add(tempFrame);
		if(playLevel1){
		an = animation;
		}
		if(playLevel2){
			an2=animation;
			}
		animation.play();
	}


```


###Design

Overall design:

I tried to separate the project components into classes based on functionality. There are three main classes that represent the main scene, level one, and level two. A player transitions from one scene to the other by clicking on buttons, or by winning, or losing at a level. The game's loop is initiated in main. The two levels contain implementation to methods used only within that class. Any method that is shared between these two classes or any shared object is created in its own class. All the variables and the methods in the other classes are private and are called by getters and setters.


To add a new level to the game, you need to create a new frame and a new timeline for it in Main class, and a button. Then from Main class when the button is clicked, it calls the initScene method for that class. initScene takes the stage, scene, scene width, and scene height as parameters, and returns scene. initScene() is used to create all the objects that will be used throughout the game, as well as anything that does not change. For example, the background function is called from within initScene. This will add a new level to the game. Typically a level has a balloon object, background, kits, or birds objects. Since these objects are common to these levels, each one of them is created in its own class and called by a getter function. Each level also has a step function that is called every 16 seconds. This function is similar to an update method. It contains method calls, and has void return type.

Describe two features from the assignment specification in detail:

1. Characters that interact with the player: Medicine Kits

Medicine kits are objects that appear on both levels of the game. The player has to collect enough of them to win a level. Class Kits contain all the variables and methods needed to create, make kits interactive. I put method implementation in this class to ensure flexibility because it is common to more than one other class. At first I had methods that are implemented in level one, but later I decided to put all of them in one class. 

Functions of this feature create the kits, remove them after a certain time has passed, and there is function that detects when the player collects a kit. I made it a requirement in the design to keep kits class unattached to any other class to make it as flexible as possible. Kits are created into a list, and this list is used through a getter method. 

2. Winning and losing: 

A player wins in level two when he or she collect 15 kits, and reach the hospital. To implement this feature I used a function that returns the number of kits collected at any point and compares it to 15. If this number is reached a Boolean variable is set to true. When the variable is true, the hospital appears from the right side of the stage. The when the player reaches the hospital the game ends, and the player wins. I made the assumption that 15 is the number needed to win a game. This limits the design flexibility in the future if I decide to expand upon the game and let the user specify the number of kits needed to win a game. The function that returns the counter is implemented in Kits class to avoid redundancy. The functions showHospital() and reachedHospital() are implemented in Destination class also to avoid redundancy. 

On the other hand, if a player is hit by the rocks twice, the game ends and the player loses. There is also a counter that keeps track of how many times the player has been hit. When the counter is equal to zero the game ends. This function is implemented in levelTwo class. This assumes that there are only two levels in the game. In the future if more levels are added, it is better to create a class called rocks that include these functions. At this point, since there are only two functions that I need to implement this feature, I have decided to keep them in levelTwo class.  




###Alternate Designs

1. I designed the  background in a way that makes it appear to be moving as the balloon moves. The image that I chose has width of 1920 pixels. My frame rate is 16 frame per second. This means that after less than one minute the background scrolls out of the stage. From watching tutorials online I had the idea to find out where the image ends and reset it. This caused a problem because the transition is not smooth. In the current design I use two instances of the image and substitute them once one of them reaches the end of the stage. This works very well for the first two transitions, afterwards there is a one second delay where the images do not coincide. I do not know why exactly. An alternate design is to try what I found out on an online tutorial where they use a mod function to return the precise pixel where the image ends. 

2.The second design decision I made was to make the stage un-resizable. I decided to do this to ensure that I can use stage width and height as parameters in my methods. Off course this means that the user cannot make the stage larger or smaller, but at the same time this decision helped use precise dimensions. Prior to that I could make the stage limit and the balloon used to go of stage. 

•	What are the three most important bugs that remain in the project's design or implementation?

1. The background image does not always make a smooth transition.
2. 
2. The image boundaries are larger than the image that appears to the user this is why it seems as if the user reaches the hospital early sometimes.




Code Masterpiece
================

