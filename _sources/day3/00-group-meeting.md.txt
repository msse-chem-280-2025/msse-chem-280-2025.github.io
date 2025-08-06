# Python Warm Up & Returning to the LJ Equation

To start class today, we will spend about half an hour reviewing Python concepts, and another half hour working with the Lennard Jones equation.


## Python Review

Pick a chapter from the e-book [Think Python](https://allendowney.github.io/ThinkPython/). 
To pick your chapter, read the topics and one you think you'd like to know more about. 
You have a quiz due at 9:35 AM with your observations from the textbook.

For the first part, we will all be in the main area. 

1. Add your name ot the [class Google Slide Presentation](https://docs.google.com/presentation/d/1wvhMZ0gUMV_UjCSfmSjz2GBiXnmtRPAphe8iiYoCDH4/edit?usp=sharing)] on the slide corresponding to your chosen chapter. (You must be logged into your UC Berkeley account to view the presentation.)
2. Spend 20 minutes or so reading independently. As you read, take note of three useful or interesting facts, or things you didn't know before.
2. **Take the quiz on bCourses by 9:35 AM.** You should record the facts you wrote from (1) on this quiz (this is the only question)
3. After 9:35 AM, we will move into breakout rooms. Spend 10 minutes discussing the chapter with your group. Record your group observations on the [class Google Slide Presentation](https://docs.google.com/presentation/d/1wvhMZ0gUMV_UjCSfmSjz2GBiXnmtRPAphe8iiYoCDH4/edit?usp=sharing)].  

## Calculation of Lennard Jones Energy for System of Particles

Take 20 minutes to work alone, then 10 minutes to discuss your answers as a group on the following questions.

When applying the LJ potential to a set of atomic coordinates, the total potential energy of the system is equal to the sum of the LJ energy over all pairwise interactions:

$$
U \left( \textbf{r}^N \right) = \sum_{i=1}^{N} \sum_{j>i}^{N} U \left( r_{ij} \right)
$$

Consider the system of three particles represented by the picture below.  

```{image} ../fig/three-particles.png
:align: center
```

Complete the following tasks:

1. Based on what we discussed yesterday, make an estimate of what you would expect the total system energy to be. For this, think about our expected energy between two particles at the equilibrium distance.
2. Calculate the total system energy **by hand**, using a pen/paper and a calculator (you can use a calculator on a computer). If you finish early, see if you can translate your calculation into a Python code.