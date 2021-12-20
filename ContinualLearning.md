# TODO:

# Definition: 
Thrun - Lifelong Machine Learning: The system has performed N tasks. When faced with the (N+1)th task, it uses the knowledge gained from the N tasks to help the (N+1)th task. Note that the data of the first N tasks is generally assumed to be no longer available at the time of learning about the N + 1th task

Chen and Liu- Lifelong Machine Learning [3]: Lifelong Machine Learning is a continuous learning process. At any time point, the learner performed a sequence of N learning tasks, T1,T2, . . . ,TN. These tasks can be of the same type or different types and from the same domain or different domains. When faced with the (N+1)th task TN+1 (which is called the new or current task) with its data D(N+1), the learner can leverage past knowledge in the knowledge base (KB) to help learn TN+1. The objective of LML is usually to optimize the performance on the new task TN+1, but it can optimize any task by treating the rest of the tasks as previous tasks. KB maintains the knowledge learned and accumulated from learning the previous task. After the completion of learning TN+1, KB is updated with the knowledge (e.g. intermediate as well as the final results) gained from learning TN+1. The updating can involve inconsistency checking, reasoning, and meta-mining of additional higher-level knowledge.

There are three chatacteristics should be noticed in above definition including continuous learning; knowledge accumulation and maintenance in the knowledge base (KB)

# Subset of continual learning
- Transfer learning  
- Multi-task learning
- Few-shot learning
- Online learning
- Curriculum learning
- Open world learning
- Active learning
