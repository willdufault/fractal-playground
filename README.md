# Fractal Playground

I created a tool that allows users to visualize what different fractals look like following the 
equation for the Mandelbrot/Julia set, `z = z^2 + c`. 

One big challenge that I faced when creating this application was performance: I first created 
JavaScript files, which can still be found in the `/static/js` folder, which did all of the 
calculations to determine whether or not each individual pixel on the screen converged or diverged. 
This was very slow, and trying to generate fractals with high numbers of iterations took a very long 
time. To solve this, I first looked into using GLSL shaders, but I have never coded anything in GLSL 
before, and I felt that if I were to use this, I would just have to copy the code. Even though this 
would have most likely resulted in significantly better performance than the final version here, I 
wanted to do it on my own and not just follow a tutorial step-by-step.

So, I instead used web assembly to speed up my application. I wrote a simple C program that did the 
bulk of the calculations and compiled it to web assembly, leading to a 14% reduction in average 
generation time for fractals with 5000 iterations.

In my instructions on the website, I briefly explain what each option does, but a more detailed 
explanation of how the belong and draw algorithms work can be found here [here](https://en.wikipedia.org/wiki/Plotting_algorithms_for_the_Mandelbrot_set).
