# Why is RL a good setting for continual learning?  
Because agent must care about present and future: <objective function>  
- A portion of future will be similar to past  
- Stability-plasticity dilemma: how should the agent prioritize current experience vs past experience?  
- Supervised CL: no time dependence  
- Continual RL: observed data is explicitly time dependence  

# Explicit knowledge retention  
## Shared parameters:  

Problems:  
- requires a methodology of detecting current task  
- requires significant storage, limit ability to leverage relevant knowledge learned accross tasks  
    
Solutions:  
- leverage knowledge via shared latent components https://openreview.net/forum?id=rkgpv2VFvr  
- store a prior about the extent of past usage of each parameter during learning in order to preserve important old knowledge https://arxiv.org/abs/1612.00796  
- context information is stored for each task so that the weights can be explicitly decomposed into orthogonal sub-networks (Cheung https://arxiv.org/abs/1902.05522

## Distillation based  
- using one neural network as a target or soft target (policy, value function) for another  https://arxiv.org/abs/1805.06370  

## Rehearsal based  
Reinforcing the importance of experiences from the past distribution during continual RL is leveraging experience replay  

Problems:  
- storage requirements as we scale to progressively more complex continual learning settings    

Solutions:  
- pseudo-rehearsals  (generative experience replay)
- learn to compress experiences during learning

# Leverage shared structures  
## Modularity and Composition
- Train NN modules which can be composed for tasks  
## State abtractions  
- Map the default state into a different state representation  
## Skill focused  
- Lean macro-actions which control lower level actions  
## Goal focused:  
## Auxiliary tasks:  

# Meta learning  