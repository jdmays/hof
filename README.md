# Hounds of Fury
A simple game of racing weiner dogs. 
Completed as part of a code review project. 
Despite my best efforts it would still have a ways to go before it would be worthwhile as anything more than a quick one-off. (More detail below)

## Built With
* Vue V3
* Tailwind CSS
* Greensock Animation

## Project setup
Intallation:
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

## Description and Discussion

I spent the following time on the project.

Time Spent on Coding:
- Friday, 9/17:  Determine game concept and basic layout - 2 hrs.
- Saturday, 9/18:  Game Play including Animation - 4 hrs.
- Monday, 9/20: Revise sequence of Modals, check for edge cases, add validation - 3hrs.

I spent about 4 hours on Thursday the 16th just re-learning / learning Vue.  I didn't want to start throwing code at the wall to 
see what stuck so I intentionally did not work on the actual project.  Instead, I watched some previous Vue tutorials and did the code along with them.
Finally, I drew out on paper the different screens and their relation to each other. 

Originally, I started off writing a Trivia Quiz type of application but after coming across ones extremely similar to what I started doing, I 
decided that I didn't want there to be any question about how much of it was my original code.  

I haven't googled Weiner Dog Race or anything like that so I'm assuming that there isn't such a thing or that if there is, it is not like mine.  
The idea originated from a festival over the summer that we were going to go to up in Wisconsin. (A German Festival similar to Oktoberfest) They 
advertised Dachshund Races so that must've been rattling around in my head.

For what it's worth, although I've been an avid programmer for a very long time, I've never gotten into playing or writing games.  I guess Pac-Man in the dark ages, but that's it. 
This is the first game application I've ever written.

Given my choice I would've written this with Laravel and Livewire.  Livewire has all the benefits of the laravel backend with the benefits of a Javascript library.  (Including Alpine.js)  React is the most mature library of all and that would've been my second choice.  


### Playability

The game is not nearly as playable as I wanted.  For starters, I was pulling the dogs from a json file and the user would be able to pick 
whichever dogs they wanted by clicking on the dogs shown on the side of the screen.  

Additionally, having the dogs win randomly is pretty boring.  Personally I like games that have a mix of skill and luck.  This one is pretty much just luck.

I would've liked to have a two or more person version as well.


- To be able to assign the dogs to a slot on the track the person would click the dog's picture -- this worked great except I could bring everything from the dog info over but 
not the picture on the track.  I researched this like crazy and could not figure out how to dynamically place an image anywhere.  Vue couldn't find the file despite several different 
ways of referring to it.  I'm sure there is some deep dark secret to doing this, but I couldn't figure it out in a reasonable amount of time.  This affected some other areas of the 
game also.  For example, when you select from the dropdown list it would be great to see a little picture of the dog being chosen.  I could've installed a plugin or library to achieve that, but I didn't want to kludge the thing up with various libraries and if I couldn't do it in a reasonable amount of time I just moved on.
- Animating the dogs on the track was a way bigger deal than I thought it should be.  In Jquery or plain old JavaScript I could've done something like this in a very short amount of time, but with Vue, I felt like I was fighting with Vue for control of the screen.  Finally, I installed the greensock library and it was amazingly easy.  I didn't want to use any libraries, but if the dogs can't move the whole Weiner Dog Race thing was dead in the water.
- If you read the code closely you'll come to the realization that the application knows who is going to win before the race is run.  Originally, I planned on tracking to see which dog got to the X coordinate first but with the animation program it was a little trickier. The way the winner is determined is that I put the possible durations in an array then shuffled the array and located the position of the lowest number.  The position corresponds to the dog so that will always be the winner.  
- I did not want the races to be random.  Random Interval Reinforcement is the way to get people addicted to things and that's what I would've liked to do. I had planned on tracking the number of times the race is run (there is still a variable in there for that) and then changing it so that the first and second time out of a series of 8 or even a random number of runs, the player always wins.  Another wrinkle, is that I wanted to introduce a co-efficient based on the previous race record of the dogs.  As in real life, the more a dog wins, the more it seems like it will win.  I saved that until last and I ran out of time.  Of the many bugs I've created over the years, one way it happens is that I do a bunch of testing and then after the testing add something at the last minute.  That's a recipe for trouble.  So, I decided to forgo the addiction making component of the application.
- A multi-person application would've been more fun also. I mean, who doesn't want to beat the other person?  

### Appearance

I tend to like an un-cluttered design that is subtle, consistent, and intuitive.  However, this is a little more bland than I would like.  I was originally going to style all of the elements by hand.  It's not a huge app and there wouldn't be that many elements.  But in the interests of time, I broke down and decided to use Tailwind.  I don't know it as 
well as Bootstrap but it isn't all that difficult either.  I felt like using Bootstrap would be cheating somehow because I can do Bootstrap in my sleep.  The problem is, 
when you use Bootstrap - unless you spend a lot of time tinkering with the elements, it looks like you did it in Bootstrap.

The transitions between the elements are harsh.  Ideally I would've liked to have used Greensock to smooth those out.  

I wanted to be able to have the user hover over each dog and get a little tooltip describing their wins, their hobbies, etc.  Ran out of time.

---!-- LICENSE -->
## License

Distributed under the do whatever you want License. Do whatever you want with it, just don't blame me if it causes a disturbance in the space/time continuum.

<!-- CONTACT -->
## Contact

Jim Mays - jdmays@gmail.com 



<!-- ACKNOWLEDGEMENTS -->
## Acknowledgements

* []()
* []()
* []()