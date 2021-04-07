# Terminology

| Symbol |	Meaning  |  
| --- | ----------- |
| s∈S | States. |   
| a∈A | Actions. | 
| r∈R |	Rewards.
| St,At,Rt |	State, action, and reward at time step t of one trajectory |
| γ | Discount factor; penalty to uncertainty of future rewards; 0<γ≤1 |
| Gt | Return; or discounted future reward; G<sub>t</sub>=∑<sup>∞</sup><sub>k= 0</sub> *γ*<sup>k</sup>R<sub>t+k+1</sub> |
| P(s',r\|s,a) | Transition probability of getting to the next state s′ from the current state s with action a and reward r |
| π(a\|s) | Stochastic policy (agent behavior strategy); π<sub>θ</sub>(.) is a policy parameterized by θ |
| μ(s) | Deterministic policy |
| V(s) | State-value function measures the expected return of state s; V<sub>w</sub>(.) is a value function parameterized by w. |
| V<sup>π</sup>(s) | The value of state s when we follow a policy π; V<sup>π</sup>(s)=E<sub>a∼π</sub>[Gt\|St=s] |
| Q(s,a) | Action-value function is similar to V(s), but it assesses the expected return of a pair of state and action (s,a); Q<sub>w</sub>(.) is a action value function parameterized by w |
| Q<sup>π</sup>(s,a) | Similar to V<sup>π</sup>(.), the value of (state, action) pair when we follow a policy π; Q<sup>π</sup>(s,a)=E<sub>a∼π</sub>[Gt\|St=s,At=a] |
| A(s,a) | Advantage function, A(s,a)=Q(s,a)−V(s); it can be considered as another version of Q-value with lower variance by taking the state-value off as the baseline. |
| trajectory | is a sequence of states and actions. In RL, the goal is to maximize the expected reward, by finding the right trajectories. <b>max<sub>τ</sub>R(τ)</b> This means maximizing not immediate reward (caused by one action from a state), but cumulative reward (all states and actions: trajectory) |

# Policy Gradient

The goal of reinforcement learning is to find an optimal behavior strategy for the agent to obtain optimal rewards. The policy gradient methods target at modeling and optimizing the policy directly. The policy is usually modeled with a parameterized function respect to θ
, πθ(a|s).

Rollout: batch of data from simulation including observation, actions, rewards, advantage