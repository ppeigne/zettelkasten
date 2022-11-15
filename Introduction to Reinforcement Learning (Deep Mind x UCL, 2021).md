#### Environment
Can be fully observable or partially observable.

#### Interaction agent-environment

![[RL1.drawio(2).png]]

At time $t$ 
- agent performs action $A_t$ in the environment;
- agent then get an observation $O_{t+1}$ of the environment which modifies its internal state $S_t$. 
- this observation $O_{t+1}$ allows to calculate the reward $R_{t+1}$

#### Cumulative reward
Cumulative reward (reward about the future):
$$G_t = R_{t+1} + R_{t+2} + R_{t+3} + \dots$$
$$G_t = R_{t+1} + G_{t+1}$$

#### The value: expected cumulative reward
Value for state $s$ only: 
$$v(s) =  \mathbb{E}[G_t | S_t = s]$$
$$v(s) =  \mathbb{E}[R_{t+1} + v(s_{t+1}) | S_t = s]$$

Value for sate $s$ and action $a$:
$$q(s,a) =  \mathbb{E}[G_t | S_t = s, A_t=a]$$
$$q(s,a) =  \mathbb{E}[R_{t+1} + v(s_{t+1}) | S_t = s, A_t=a]$$

The usual goal is to **maximize the value** (i.e the cumulative reward) by taking actions, **not the immediate reward**. Therefore the behavior can imply sacrificing immediate reward to get more value on the long term.


## Agent components
### Agent state
The state is an encoding of the current state of the world. 
In an MDP the state is enough to take the best actions.

#### Markovian Decision Process (MDP)
A process is markovian if  its probability of reward and subsequent state does not change if we add more information (e.g whole history $H$ or whole set of previous actions $\mathbb{A}$). 
$$
p(r, s | S_t, A_t) = p(r, s | H_t, \mathbb{A}_t)
$$

Fully observable environment are markovian. Partially observable env. are not. 

#### Partially Observable MDP (POMDP)

#### State update function
$$S_{t+1} = u(S_t, A_t, R_{t+1}, O_{t+1})$$

### Policies
- Stochastic: sample actions from policy
- Deterministic: one unique action given the state

Policies are mapping $S_t  \rightarrow A_t$ 

### Value estimate
Given a policy $\pi$ 
$$v_\pi(s) =  \mathbb{E}[G_t | S_t = s, \pi]$$
$$v_\pi(s) =  \mathbb{E}[R_{t+1} + v_\pi(s_{t+1}) | S_t = s, \pi]$$

#### Discount factor $\gamma \in [0,1]$
The return (cumulative reward)
$$
G_t = R_{t+1} + \gamma G_{t+1}
$$


##### Bellman equation
The value (expected cumulative reward)
$$v_\pi(s) =  \mathbb{E}[R_{t+1} + \gamma G_{t+1} | S_t = s, A_t \sim \pi(s)]$$
$$v_\pi(s) =  \mathbb{E}[R_{t+1} + \gamma v_\pi(s_{t+1}) | S_t = s, A_t \sim \pi(s)]$$

$a \sim \pi(s)$ -> $a$ is chosen in the available actions by policy $\pi$ given the state $s$. 

##### Optimal value ($v_*$)
$$v_*(s) = \max_a \mathbb{E}[R_{t+1} + \gamma v_*(s_{t+1}) | S_t = s, A_t = a]$$

Does not depends on policy $\pi$. Why? 
Because the optimal value is the best sequence of action / trajectories (in a way it is the best policy we can reach). Therefore it does not depends on any given policy because it replaces the mapping $S_t \rightarrow A_t$ from any policy by an optimal choice. 

The goal of many RL algorithms is to approximate $v_*$.

##### Approximating the optimal value
If we can approximate $v_*$, we can then use it to select the optimal policy. 

### Model (optional)
Model of the environment. Usually need additional compute to extract a good policy.
Can predict:
- the next states: $p(s, a, s') \approx p(S_{t+1}=s' | S_t=s, A_t=a)$
- the reward: $r(s,a) = \mathbb{E}[R_{t+1} | S_t=s, A_t=a]$


### Agent categories
Value based
Policy based
Actor critic (value + policy)

Model free: policy AND/OR value
Model based: optional policy AND/OR value

### Sub-problems 
- Prediction: evaluate the future of a given policy
- Control: optimize the future -> select the best policy

Best policy: 
$$
\pi_* = \operatorname*{argmax}_\pi v_\pi(s)
$$

- Learning: build the model by interacting with the environment
- Planning: no interaction. Internal computation given the model.