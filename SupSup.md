# Supermasks in Superposition 
Instead of learning the weights, or jointly learning the weights and connectivity, good performance can be achieved by choosing whether each edge in the the network is on or off. For each new task i SupSup finds a supermask (subnetwork) which achieves good performance on task i. The underlying weights are not modified and so forgetting does not occur. The underlying weights are not modified and so forgetting does not occur. Moreover, the underlying weights have minimal storage cost as you only need to save the random seed.

## Continual Learning Scenarios
The key differences between scenarios are whether 1) the model has access to which task it is performing inference or training on and 2) whether tasks reuse labels. Consider, for example, the task of learning 50 permuations of MNIST. Is the model evaluated on correctly identifying the digit or is the model required to identify the digit and permutation? The table below provides our taxonomy, which builds upon van de Ven & Tolias and Zeno et al..

| Scenario	| Description |
|---|---|
| GG	| Task Given during train and Given during inference | 
| GNs	| Task Given during train, Not inference; shared labels |
| GNu	| Task Given during train, Not inference; unshared labels |
| NNs	| Task Not given during train Nor inference; shared labels |