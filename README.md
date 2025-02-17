java cMGTS7523 Assessment #3 2024, Semester 2 
Part 1: Building a predator-prey (seabirds – cats) stock and flow model 
The aim of this part of the assignment is to test your ability to construct a system dynamics model using the Stella Architect software. You will be required to use this model to help understand the dynamic consequences of introducing a cat population to an existing seabird population. Furthermore, you will use this same model to incorporate a simple management strategy that examines the effect of a cat removal program. Finally, you will update an initial causal loop diagram (Figure 1) to create a more accurate representation of the system.
Background 
The stock and flow model (SFM) that you will build using Stella Architect is a predator-prey model that has similarities to the Macquarie Island case study that was first introduced in week 1 for MGTS7523. Figure 1 shows a simplified causal loop diagram (CLD) for the system that you will be modelling. The basic story is there is a population of seabirds (the prey) on an island. Initially, there are no cats, however their introduction is the catalyst for a predator-prey system between the birds and the cats.
Figure 1. Simple CLD for the predator-prey model 
Stock and flow model development  
In this section you are tasked with building a stock and flow model (SFM) using Stella Architect.
Model settings 
Open Stella Architect and create a new (model) file.
Open the model settings panel and ensure the following model settings are used:· Start Time = 1, Stop Time = 3650· Time Units = Days· DT = ½ (0.5)· Integration method = Euler
Copy and paste the model settings panel showing these settings below (Mac: use shift+command+4, PC: Use screen print) – make sure that the Start Time, Stop Time, DT, Time Units, and Integration Method are clearly visible [2 marks] 
The seabird population model 
The first task is to build a SFM for a seabird population. Your model will have the following stocks:· ‘SEABIRD EGGS’ [birds] – the number of eggs· ‘SEABIRDS’ [birds] – the number of seabirds
For simplicity, assume that the units for SEABIRD EGGS and SEABIRDS are the same (birds). The basic structure of the SFM that you need to build is shown in Figure 2.
Figure 2. The basic structure for the seabird model 
Initial conditions 
The two stocks need initial conditions. Rather than insert these directly into the stocks, we will use converters to store these – this approach allows easy access to these variables if we develop a user-interface. It also addresses the modelling principle that “there should be no hidden variables”.
Add two new converters to be used to store the initial conditions for the two stocks of the seabird model, naming them as follows:· ‘Initial seabird eggs’ = 50000 [birds]· ‘Initial seabirds’ = 4700 [birds]
Make sure that the units of the stocks are the same as these ‘initial value’ converters.
In this model, you are required to colour-code some of your converters. This provides a visual aide for their rapid identifying different types of converters in a SFM.
For converters that store initial conditions, we will set the fill colour of these as green.· Set the fill colour for these two new converters (‘Initial seabird eggs’, ‘Initial seabirds’) to green.
Controlling the flows 
The following rate constants help determine how quickly (or slowly) the number of seabirds are created (births) and die (eggs lost, bird deaths). Introduce the following three converters to your model, naming them as follows:· ‘Birth rate eggs’ = 0.027 [1/day] (i.e. for every 1000 birds, 27 eggs are laid each day)· ‘Loss rate of eggs’ = 0.01 [1/day] (the proportional rate that eggs fail to hatch)· ‘Seabird death rate’ = 0.01 [1/day]
Now connect these three new converters into the appropriate flows in your model.
To account for eggs hatching ('birds hatch’), use the following data to introduce one new converter (‘Egg incubation period’) and connect this to the basic model structure.· ‘Egg incubation period’ = 35 [days] (the time it takes for an egg to hatch)
Set the units for each of these four new converters. Set the fill colour for each of these four converters to grey.
Note that each of these four converters, which are used to control the flows in the current model, is used in combination with one of the stocks to determine the amount of flow. Based on this, add connections between the appropriate stock and flow so that the flows are correctly set up.
Finally, to complete this part of the SFM, you need to set the equations for the four flows to accommodate these additions to the model (use Stella Architect’s built-in unit checker to ensure that all variables have been properly specified).
Copy and paste your model structure into the box below [2 marks] 
If you run the model now you will get exponential growth – explain in the box below why this occurs? [2 marks] 
Using a graph ( ), show the behaviour over time for SEABIRDS that confirms that exponential growth is occurring. Copy and paste your graph into the space below (make sure that the x and y axes are visible) [3 marks] 
Adding a carrying capacity effect 
An issue of the seabird model is that it currently does not allow a shift in feedback dominance as the population increases (or declines). This effect can be introduced by bringing in a carrying capacity effect and adding an additional feedback loop.· Introduce a new converter and name it ‘Carrying capacity’ and set its value = 50000. Set the fill colour for this converter to grey.· Introduce an additional new converter and name it ‘Seabirds:CC’
‘Seabirds:CC’ is a variable that will compare the current seabird population with the carrying 代 写MGTS7523 Assessment #3 2024, Semester 2SPSS
代做程序编程语言capacity (the maximum number of seabirds that the system can support). It does this by taking the ratio of seabirds to carry capacity (Seabirds divided by the carrying capacity).
Connect the SEABIRD stock and the ‘Carrying capacity’ converter to ‘Seabirds:CC’. Add the equation needed for this.
Set the units for these two new converters (note that the units for ‘Carrying capacity’ are the same as for SEABIRD).

A dimensionless multiplier  · Introduce another new converter and name it ‘Effect of seabird population on seabird death rate’.
Set the fill colour for this new converter to yellow. Connect ‘Seabirds:CC’ to ‘Effect of seabird population on seabird death rate’. The units for this converter will be the same as ‘Seabirds:CC’.
The ‘Effect of seabird population on seabird death rate’ will be a graphical function. Therefore, specify this converter as a graphical function by checking ‘Graphical’ in Stella Architect:

The input to the graphical function is the ratio of seabirds to the carrying capacity (Seabirds:CC) à we are only concerned over the range that this ratio is 0 – 1. Therefore set the limits on the x-axis of the graphical function to be 0 – 1.
We are interested in converting this input into an effect on the death rate of the seabirds. At a low ratio value (i.e. the input), there should be no effect on the seabird death rate, whilst at a low ratio value, there should be an increasing effect on the seabird death rate (i.e. the death rate will start to increase as the input ratio approaches 1). To accommodate this, set the limits of the y axis to 1-2. Select ‘Points’ and then set the number of data points = 11:

Use the following information to populated the table for your graphical function:
When Seabirds:CC 
When Seabirds:CC  = 0.700, the utput = 1.069
When Seabirds:CC  = 0.800, the utput = 1.186
When Seabirds:CC  = 0.900, the utput = 1.452
When Seabirds:CC  = 1.000, the utput = 2.000
Copy and paste your graphical function (as a graph - click on ‘Graph’) below, ensuring that you include the x and y axes [2 marks] · Add another new converter and name it ‘Seabird death rate adjusted for CC’.
Delete the connection between ‘Seabird death rate’ and ‘bird deaths’ and add a new connection from ‘Seabird death rate’ to ‘Seabird death rate adjusted for CC’. Now also connect ‘Effect of seabird population on seabird death rate’ to ‘Seabird death rate adjusted for CC’.  Set the equation for ‘Seabird death rate adjusted for CC’ so that its units are the same as for ‘Seabird death rate’
Finally add a new connector from ‘Seabird death rate adjusted for CC’ to ‘bird deaths’ (update your equation for ‘bird deaths’ to reflect this change).
Copy and paste your entire SFM below [3 marks] 
Run the model and paste the chart below showing SEABIRDS over the entire simulation run (make sure that the x and y axes are visible) [2 marks] 
We now have a seabird population model that will grow until it reaches the carrying capacity of the system.
Adding a cat population model 
To investigate the impact on the seabird population of introducing cats, we need to build a cat population model. The basic structure of the cat model that you need to use is Figure 3.
Figure 3. The basic structure for the cat model 
What type of flows are shown in Figure 3? Why are these types of flows used? [2 marks] 
Build this basic structure in Stella Architect in the same file as you built your Seabird population model (you will be connecting the two models).

Initial conditions 
The stock needs an initial condition – add a new converter to set the following initial condition for CATS:· ‘Initial cats’ = 0 [cats]. Set the fill colour for this new converter to green.
Add the following two converters – these will be the population rate constants for your cat model (set fill to grey):· ‘Cat birth rate’ = 0.00857 [1/day]· ‘Cat death rate’ = 0.006 [1/day]
Note that these two new rate constants are used in a linear first-order combination with CATS to control the inflow (cat births) and outflow (cat deaths). Update your SFM to reflect this.
Set the equations for ‘cat births’ and ‘cat deaths’ to accommodate these additions to the model.
Run the model – create a new graph to display ‘CATS’. Copy and paste this graph below and include with your graph an explanation of the why you observe the trend you see for CATS (make sure that the x and y axes of your graph are visible) [3 marks] 
Introducing cats into the system 
We are now going to set up the model so that cats are introduced to the system. The approach that we will use is to create a new flow that represents the introduction of cats.· Add a new inflow (name it ‘Introduction of cats’) and connect it into the CATS stock.
We will use Stella Architect’s built-in ‘PULSE’ function to essentially inject some cats into the CATS stock. To do this add the following three new converters:· ‘cat introduced rate’· ‘cat introduction day’ = 1000 [day]· ‘number of cats introduced’ = 50 [cats]
Connect ‘cat introduced rate’ to the ‘Introduction of cats’ flow
Connect ‘cat introduction day’ and ‘number of cats introduced’ to ‘cat introduced rate’
Set the fill colour for ‘cat introduction day’ and ‘number of cats introduced’ to grey.
Set the equation for ‘cat introduction rate’ = PULSE(number_of_cats_introduced, cat_introduction_day, 100000) [use Stella Architect’s unit checker to recommend units]
Finally, set the equation for the ‘Introduction of cats’ flow.
Run the model and plot the ‘Introduction of cats’ flow on a graph. Copy and paste your graph below (make sure that the x and y axes are visible) [2 marks] 



         
加QQ：99515681  WX：codinghelp  Email: 99515681@qq.com
