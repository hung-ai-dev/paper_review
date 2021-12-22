# DisCoRL: Continual Reinforcement Learning via Policy Distillation

- policy distillation method  
- at test time, the agent does not have access to a task label to determine which policy to run, and thus, it needs to figure it out by itself from its observations

## Related works  
- Rehearsal: keeps samples from previous tasks, or generative replay    
- Regularization: keeping an old model in memory and distilling knowledge, or constrain- ing weight updates in order to maintain knowledge from previous tasks  
- Dynamic network architectures: maintains past knowledge thanks to architectural modifications while learning  

## Scenarions  
- Task indicator is provided at test time  
- Task indicator is NOT provided at test time  

## Questions  
- Efficiency sampling  
    - Simulation  
    - First learn a state representation to compress the observation into a low dimensional embedding and secondly learn the policy on top of this representation 

## Methods  
### One tasks  
- Each task i is solved by first learning a state representation encoder Ei in order to compress input images into a representation of the important underlying factor of variation
- To train this encoder, we sample data from the environment Env_i with a random policy. We call this dataset DR,i. DR,i is then used to train the SRL model composed of an inverse model and an auto-encoder.  
-  The inverse model is trained to predict the action at that led to transition from state st to st+1
- The auto-encoder is additionally trained to reconstruct the observations from the encoded states  
- Once the SRL model is trained, we use its encoder Ei to provide features as input of a policy πi trained using RL
- Once trained, πi is used to create a distillation dataset Dπi that acts as a memory of the learned behaviour. All policies are finally compressed into a single policy πd:1,..,i by merging the current dataset Dπi with datasets from previous tasks Dπ1 ∪ ... ∪Dπi−1 and using distillation (3)

### Continual tasks 
- Distillation strategies: Distillation is done with a loss function that minimizes the difference between the student model’s output and the teacher model’s output for the same input.
- Data sampling:
    - On-policy generation
    - Off-policy generation from a grid walker