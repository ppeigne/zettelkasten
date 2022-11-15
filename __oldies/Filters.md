# Filters

**Filters are algorithms made to estimate values from noisy data.**

The main idea behind filtering is to **combine a prediction** of the next value (based on the previous estimate) **with a new measurement** to get a new estimate of the new value. 

$$\text{Estimate} =\alpha \text{ Prediction} + \beta \text{ Measurement}$$


# Quotes
"Data is better tha guess, even if it's noisy"

"Mutiple data points are more accurate than one data point, so throw nothing away no matter how inaccurate it is"

"Always choose a number part way between two data points to create a more accurate estimate"

"Predic the next measurement and rate of change based on the current estimateand how much we think it will change"

"The new estimate is then chosen as part way between the prediction and next measurement scaled by how accuate each is"

# Terminology

system : the object that we want to estimate
state : current configuration of or values of that system that is of interest to us
measurement : measure value of the system
(state) estimate : our filter's estimate of the state

The system value is usually hidden while the measurement are observable

*(These definitions are close to the concepts of phenomenon (observable thing) VS noumenon (true hidden thing))*

