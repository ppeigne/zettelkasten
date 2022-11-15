


# DRAFT
# Kalman gain
The Kalmain gain determines how much of the new estimate to use in order to update the new estimate.

Inputs: 
- Error in estimate (calculated in step 3. at *t-1*)
- Error in data (measurement)

Kalman Gain = $KG \in [0, 1]$
Error in estimate = $E_{EST}$
Error in measurement = $E_{MEA}$

$$
KG = \frac{E_{EST}}{E_{EST} + E_{MEA}}
$$

The Kalman gain puts a relative importance in the error of the estimate vs the error of the data. **If an error is small, we put more importance on it**
