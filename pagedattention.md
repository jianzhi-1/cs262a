# PagedAttention (2023)

### What is the problem being solved?

The problem is to allow larger batch sizes for LLM serving system (i.e. at inference time) by carefully managing the memory space of each request (due to its KV cache's dynamic growing and shrinking nature). This is done by reducing fragmentation and redundant duplication in the KV cache memory of each request, due to the dynamic growing and shrinking of it. This will also result in cheaper cost per request.


### How was this problem solved previously?

Previously, the KV cache of a request is stored in a pre-allocated, contiguous memory space (due to deep learning frameworks' requirements) with size equal to the request's maximum length. Thus, they suffer from internal and external memory fragmentation. Also, they cannot exploit opportunities for memory sharing during decoding algorithms (beam search) and autoregressive generation.

### What is the main idea?

The main idea is to take inspiration from the idea of paging in virtual memory. A request's KV cache is divided into blocks, each of which can contain the attention keys and values of a fixed number of tokens. The blocks of the KV cache are not necessarily stored in contiguous space, hence alleviating internal and external fragmentation (1).

During the attention computation, the PagedAttention kernel identifies and fetches the necessary KV blocks (4.1).

### What are the key results?

PagedAttention achieved near zero waste in KV cache memory and allows for flexible sharing of KV cache from within and across requests (no graphs, but the result followed from the methodology). It improves throughput (using normalised latency as the metric (6.1)) of popular LLMs (ShareGPT, Alpaca) by 2-4x with similar level of latency compared to state-of-the-art systems (FasterTransformer, Orca). Accommodates longer sequences, larger models and more complex decoding algorithms. 

### What are the main limitations of this paper?

I think the main limitation of vLLM is that it incorporates optimisations specifically designed for LLM inference (i.e. fixed on the transformer model). In that sense, it is taking a bet that the model is here to stay.

### Why did this paper have an impact?

vLLM is open sourced. It is a very popular LLM serving system now and has gained industry traction. It also kind of maintained its dominance in the LLM serving system (with exception of RadixAttention).
