# OpenRLHF (2024)

### What is the problem being solved?

The problem is to be able to train reinforcement learning with human feedback (RLHF) models with sizes greater than that of a single GPU device. This is different from other machine learning fields because RLHF typically has four component models (actor, critic, reward, reference) which poses coordination challenges.

### How was this problem solved previously?

Prior efforts, such as Transformer Reinforcement Learning (TRL), ColossalChat, DeepSpeed-Chat, colocate the four component models within a single device. 

TRL also attempted merging the actor and critic models (basically restricting the family of models). However, this requires changes to the model and also limits performance.

### What is the main idea?

The goal is to allocate the four component models across multiple GPUs efficiently. The model scheduling is done using Ray, which does model placement and fine-grained orchestration (3.1). vLLM is used for efficient LLM inference and serving, and achieves faster generation than predecessor HydridEngine. DeepSpeed and Ray also does model merging and offloading strategies. Ray avoids excessive model splitting and model weights offloading, thus saving on GPU memory and reducing communication overhead. 

### What are the key results?

OpenRLHF can do RLHF training for models with over 70B parameters. It achieves lower latency than the state-of-the-art DSChat (Table 2). The project also implements the popular alignment algorithms (RLHF DPO, rejection sampling) and integrates with Hugging Face Transformers, mixture of experts etc. 

### What are the main limitations of this paper?

The project's benefits seem to derive very much from Ray and vLLM and does not seem to have novel optimisations that added significant improvement. It also felt like the idea of the project lies in linking Ray and vLLM together. Perhaps the identification of the problem and the choice of these two major technologies is the difficult part?

### Why did this paper have an impact?
The project is open-sourced and is easy to experiment with/use due to its comprehensive set of initial alignment policies and integration with Hugging Face.
