# OpenRLHF (2024)

### What is the problem being solved?

Ability to train reinforcement learning with human feedback (RLHF) models with sizes greater than that of a device.

4 component models (actor, critic, reward, reference) must be allocated across multiple GPUs due to memory limit of GPU (< 80 GB).

### How was this problem solved previously?

Previously, 4 component models (actor, critic, reward, reference) colocated within a single device.

Merge actor-critic (at the application level). However, this requires changes to the model. Limited.

### What is the main idea?

Redesigns model scheduling using Ray, vLLM and DeepSpeed, enabling training of models beyond 70 billion parameters. Integrates with Hugging Face Transformers, mixture of experts.

4 component models (actor, critic, reward, reference) must be allocated across multiple GPUs due to memory limit of GPU (< 80 GB). Use Ray for model placement and fine-grained orchestration. Scheduler design allows flexible model merging and offloading strategies. 

### What are the key results?

Can do RLHF training of models with over 70B parameeters, by distributing models across GPUs via Ray and optimising efficiency leveraging vLLM. Implements multiple alignment algorithms. Seamless integration with HuggingFace provides out-of-the-box usability.

Lower latency than DSChat (Table 2), 
Analysis is that vLLM allows faster generation than predecessor Hybrid Engine. Ray avoids excessive model splitting and model weights offloading -> saves GPU memory and reduces communication overhead.

### What are the main limitations of this paper?
The main innovation seems to be using vLLM and Ray.

### Why did this paper have an impact?

Easy to use.
