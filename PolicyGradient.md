Objective: find a policy θ that create a optimal trajectory τ (maximize expected reward)
![MM algo](./TRPO/PG_objective.jpeg)

Policy gradient:
![MM algo](./TRPO/PG_1.png)

=> ![MM algo](./TRPO/PG_2.png)

```
Policy Gradients suffer from high variance and low convergence
```

- Stuck if waiting for termitate state
- Estimated Q, A value => big error