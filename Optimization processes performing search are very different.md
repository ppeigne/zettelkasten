Gradient descent is a sequential process
Tree search is a parallel process

TS use the objective function to select the best candidate among a set of options
GD use the objective function to iteratively improve the same candidate. 

Human planning is much more like GD than TS:

Humans: iteratively developping the plan and relying on TS only for unsatisfactory step. 

Example: the hollidays in Portugal

1. 


2. You look for a bike to rent. The first option does not fit your criteria (this is too expensive): you go for a second option. You are not that much conviced (you do not like that much the bikes proposed) so you go for a third one. Its a deal! The bikes are great and the price is what you expected to pay. Four other options were available but you did not even look at them: once you got what you want you stop searching. 
  
3. You are now looking for your train ticket. This is more trickier because you have a huge range of prices and all of them seem expensive. Here you have a different objective here: you want it to be as cheap as possible. Here you are litteraly comparing all of the options in a compressed search space (the available trains trips) under a lot of constraint (the departure station, the time of departure) trying to minimize the price and the time of travel. 

4. Now you get your train ticket, you go back to your bike research. You select  