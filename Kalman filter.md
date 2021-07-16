# Kalman filter 
A Kalman filter is an iterative process used to quickly calculate the true value from consecutive noisy data points (i.e. containing random error, uncertainty or variation).

## Process 
1. Calculate the Kalman gain
2. Calulate current estimate
3. Calculate new error estimate

#### Kalman Gain 
$$
KG_t = \frac{E_{EST_{t-1}}}{E_{EST_{t-1}} + E_{MEA_{t}}}
$$

The Kalman Gain will be **close to zero** if $E_{MEA_t}$, **the *error in measurement* is big**: in such case, we do not give much confidence to the measurements and **put more importance on the estimates**.

The Kalman Gain will be **close to one** if $E_{MEA_t}$, **the *error in measurement* is small**: in such case, we **put more importance on the measurement** than on the estimate.

#### Current estimate 
$$
EST_t = EST_{t-1} + KG * (MEA_t - EST_{t-1})
$$

The current estimate at $t$ is calculated based on the previous estimate. The previous estimate is updated using the [[Kalman gain]] multiplied by the difference between the previous estimate and the measurement at $t$.
- **If the Kalman Gain is high** (close to one), we are in a situation where the measurement are accurate. Therefore **we will use more the informations from the measurement to update the current estimate**: the difference between the previous estimate and the measurement will have a higher importance in the update. 
- **If the Kalman Gain is low** (close to zero), we are in situation where the measurement are inaccurate. Therefore **we will put more importance on the previous estimate** than the current measurement to update the current estimate:  the difference between the previous estimate and the measurement will have a lower importance in the update.

#### New error in estimate
$$
E_{EST_t} = \frac{MEA_t * E_{EST_{t-1}}}{E_{EST_{t-1}} + MEA_t} = (1 - KG_t) E_{EST_{t-1}}
$$

The new error in estimate will rely deeply on the current Kalman Gain. 
- If the Kalman Gain is high (close to one) the measurement are accurate. Therefore we can reduce quickly the error because we rely deeply on the measurement to zero in close to the true value.
- If the Kalman Gain is low (close to zero) the measurement are inaccurate. Therefore we will reduce slowly the error because we cannot rely on the new measurement to zero in to the true value (there is a risk to deviate from the true value due to the bad measurement values).


# DRAFT
# Kalman filter
A Kalman filter is an iterative process used to quickly calculate the true value from consecutive noisy data points (i.e. containing random error, uncertainty or variation).

## Process 
1. Calculate the Kalman gain
2. Calulate current estimate
3. Calculate new error estimate


#### 1. Calculate [[Kalman gain]]
Inputs: 
- Error in estimate (calculated in step 3. at *t-1*)
- Error in data (measurement)

The Kalman gain puts a relative importance in the error of the estimate vs the error of the data. **If an error is small, we put more importance on it**


#### 2. Calculate current estimate
Inputs:
- Previous estimate (current estimate at *t-1*)
- Measured value (data input)
- Kalman gain

The Kalman gain is used tu put a relative importance over the two others parameters and decide which to use more to come up with the new estimate.

#### 3. Calculate new error in estimate
Inputs:
- Kalman gain
- Current estimate



Output:
- Updates estimates
