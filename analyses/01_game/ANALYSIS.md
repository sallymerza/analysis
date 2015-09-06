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


###Design
###Alternate Designs

Code Masterpiece
================

