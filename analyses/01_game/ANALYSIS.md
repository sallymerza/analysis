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
    
    Another commit example is the one labled " level one completed, menue ready, scene changes correctly". This was an important commit becuase as I mentioned before I had trouble figuring out how to change scenes. I also had created an infinite loop becuase I did not create my constructores correclty. I pushed this commit after I went to office hours. I believe that the commit message is very descriptive. The size of the commit was not big interms of nummber of lines of code, but it was important because it fixed a null pointer exception that prevented me from going further in my project.



###Conclusions


Design Review
=======

###Status

* Bullets are made with asterisks

1. You can order things with numbers.

###Design

You can put blocks of code in here like this:
```java
    /**
     * Returns sum of all values in given list.
     */
    public int getTotal (Collection<Integer> data) {
        int total = 0;
        for (int d : data) {
            total += d;
        }
        return total;
    }
```

###Alternate Designs

Code Masterpiece
================

