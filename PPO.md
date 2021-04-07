## Problems:
-  natural policy gradient involves a second-order derivative matrix which makes it not scalable for large scale problems.

## Contributions:
- Make the first order derivative solution, like the gradient descent, closer to the second-order derivative solution by adding soft constraints.

### PPO use penalized KL instead of contrained KL as TRPO
![MM algo](./TRPO/PPO_panalty.jpeg)


β controls the weight of the penalty. It penalizes the objective if the new policy is different from the old policy. Borrow a page from the trust region, we can dynamically adjust β. d below is the KL-divergence between the old and the new policy. If it is higher than a target value, we shrink β. Similarly, if it falls below another target value, we expand the trust region.

![MM algo](./TRPO/PPO_KL_Penalty.png)

### PPO with clipped objective
we maintain two policy:
- current policy that we want to refine
- last policy to collect samples  
However, difference between current and old policy getting larger through iteration (outside the range (1 — ε) and (1 + ε)). So for every 4 iteratils, we assign old policy to refined policy  
With clipped objective, we compute a ratio between the new policy and the old policy:   
![MM algo](./TRPO/clipped_objective.png)
if new policy is much different from the old one => clip estimated advantage function
![MM algo](./TRPO/clip_ojbective.png)

Advantage is positive:  
Suppose the advantage for that state-action pair is positive, in which case its contribution to the objective reduces to [formulation]  
Because the advantage is positive, the objective will increase if the action becomes more likely—that is, if \pi_{\theta}(a|s) increases. But the min in this term puts a limit to how much the objective can increase. Once \pi_{\theta}(a|s) > (1+\epsilon) \pi_{\theta_k}(a|s), the min kicks in and this term hits a ceiling of (1+\epsilon) A^{\pi_{\theta_k}}(s,a). Thus: the new policy does not benefit by going far away from the old policy.

Advantage is negative: 
Suppose the advantage for that state-action pair is negative, in which case its contribution to the objective reduces to [formulation] 

Because the advantage is negative, the objective will increase if the action becomes less likely—that is, if \pi_{\theta}(a|s) decreases. But the max in this term puts a limit to how much the objective can increase. Once \pi_{\theta}(a|s) < (1-\epsilon) \pi_{\theta_k}(a|s), the max kicks in and this term hits a ceiling of (1-\epsilon) A^{\pi_{\theta_k}}(s,a). Thus, again: the new policy does not benefit by going far away from the old policy.