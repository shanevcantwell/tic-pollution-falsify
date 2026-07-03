# Seed A/B proximate inspiration for the "tic H0"

July 3, 2026: Shane V Cantwell

**Provenance (2026-07-03):** Source material — two Opus 4.8 transcripts (same task: CUDA-L1 vs TensorRT-LLM research) contrasting behavior without and with an "'Orthogonal' has a textbook meaning that must be respected" system-prompt line. Arm A contains the canonical loose usage ("CUDA-L1's whole framing... is orthogonal to where TensorRT-LLM gets its wins"); arm B cashes the concept out geometrically. This n=1-per-arm pair is the empirical seed that motivated the study and the splice design (ADR-TPF-001, ADR-TPF-002) — motivation, not evidence.
**Status:** raw working note — not a decision record.

## A/B test (seed and sampling settings unknown)

### Opus 4.8 with no directives about usage of "orthogonal":

#### System Prompt

- Never hesitate to search for exogenous data from external sources to ground any part of the conversation that you judge requires this kind of grounding.

#### Resulting exchange

* user
Deep research whether anybody any made any practical uses of "CUDA-L1".CUDA-L1 looks specific enough to research directly — it's an AI/reinforcement learning system for CUDA kernel optimization that appeared in 2025. Let me dig into whether it's seen any practical adoption or real-world use.

* reasoning
Verifying current TensorRT-LLM details for accurate comparison
Verifying current TensorRT-LLM details for accurate comparison
I'm considering whether I need to search for current information about TensorRT-LLM to properly compare it with CUDA-L1, since TensorRT-LLM is an actively developed inference library and I want to ensure I'm giving accurate details about how these technologies relate.

Done
Good question — these two operate at very different layers of the stack, so "interact" and "contrast" pull in somewhat different directions. Let me ground the TensorRT-LLM side with current details before drawing the comparison, since it's a fast-moving product.


Contrasted research automation tool against production inference framework
Contrasted research automation tool against production inference framework

TensorRT-LLM what it is kernel optimization inference library 2025
10 results


Optimizing TensorRT-LLM: Best Practices for Efficient Model Serving
www.nexastack.ai

tensorrt-llm · PyPI
pypi.org

TensorRT-LLM Optimization | Introl Blog
introl.com

TensorRT - Wikipedia
en.wikipedia.org

LLM-Inference-Bench: Inference Benchmarking of Large Language Models on AI Accelerators
arxiv.org

Optimizing Inference on Large Language Models with NVIDIA TensorRT-LLM, Now Publicly Available | NVIDIA Technical Blog
developer.nvidia.com

TensorRT SDK | NVIDIA Developer
developer.nvidia.com

GitHub - NVIDIA/TensorRT-LLM: TensorRT LLM provides users with an easy-to-use Python API to define Large Language Models (LLMs) and supports state-of-the-art optimizations to perform inference efficiently on NVIDIA GPUs. TensorRT LLM also contains components to create Python and C++ runtimes that orchestrate the inference execution in a performant way. · GitHub
github.com

Fingerprinting Inference Systems of Large Language Models
arxiv.org

Puzzle: Distillation-Based NAS for Inference-Optimized LLMs
arxiv.org
I've got a solid understanding of TensorRT-LLM and CUDA-L1 from my research, so now I'm checking whether KernelBench's kernel targets actually overlap with what TensorRT-LLM implements, and comparing what each framework optimizes for versus what the other handles.

The core distinction is that CUDA-L1 is a research tool for automatically generating and optimizing individual GPU kernels through reinforcement learning, while TensorRT-LLM is NVIDIA's production inference library that operates at a much higher level—handling graph optimization, runtime scheduling, batching, KV cache management, and multi-GPU parallelism alongside kernel implementation. TensorRT-LLM's kernels are hand-written by experts and battle-tested in production (like its FlashAttention implementation), whereas CUDA-L1 attempts to automate kernel generation with reported speedups that have faced significant skepticism around reward hacking and benchmarking artifacts.

While CUDA-L1 optimizes isolated PyTorch operations on KernelBench, TensorRT-LLM's real gains come from fusing operations across the computation graph and managing memory movement and batching—a fundamentally different optimization target. The two operate at different abstraction levels: TensorRT-LLM already incorporates kernel fusion as a core feature, whereas CUDA-L1 optimizes single ops in isolation without the cross-op graph fusion or runtime orchestration that TensorRT-LLM provides. In theory, CUDA-L1 could propose novel kernels for libraries like TensorRT-LLM to adopt, but the specialized, fused, hardware-specific kernels TensorRT-LLM uses (like Hopper/Blackwell FP8 attention) go far beyond what isolated-op benchmarking covers, so practical overlap is limited.

Show less
Done

* assistant
The core distinction is that CUDA-L1 is a research tool for automatically generating and optimizing individual GPU kernels through reinforcement learning, while TensorRT-LLM is NVIDIA's production inference library that operates at a much higher level—handling graph optimization, runtime scheduling, batching, KV cache management, and multi-GPU parallelism alongside kernel implementation. TensorRT-LLM's kernels are hand-written by experts and battle-tested in production (like its FlashAttention implementation), whereas CUDA-L1 attempts to automate kernel generation with reported speedups that have faced significant skepticism around reward hacking and benchmarking artifacts.
While CUDA-L1 optimizes isolated PyTorch operations on KernelBench, TensorRT-LLM's real gains come from fusing operations across the computation graph and managing memory movement and batching—a fundamentally different optimization target. The two operate at different abstraction levels: TensorRT-LLM already incorporates kernel fusion as a core feature, whereas CUDA-L1 optimizes single ops in isolation without the cross-op graph fusion or runtime orchestration that TensorRT-LLM provides. In theory, CUDA-L1 could propose novel kernels for libraries like TensorRT-LLM to adopt, but the specialized, fused, hardware-specific kernels TensorRT-LLM uses (like Hopper/Blackwell FP8 attention) go far beyond what isolated-op benchmarking covers, so practical overlap is limited.Show lessDoneShort version: they barely overlap in practice, and where people imagine them overlapping is mostly where CUDA-L1 is weakest. They live at different layers of the stack, and TensorRT-LLM already does — with hand-tuned, battle-tested code — the thing CUDA-L1 only gestures at.
Here's the contrast in the terms that matter.
Different layers, different scope. CUDA-L1 is a research system that tries to generate or rewrite individual CUDA kernels using reinforcement learning, evaluated on KernelBench — a suite of ~250 standalone PyTorch operations measured in isolation. TensorRT-LLM is a full production inference library. Kernels are just one of its layers; on top of them it does graph-level fusion, quantization (FP8/FP4/INT4 AWQ, INT8 SmoothQuant), paged KV-cache management, in-flight (continuous) batching, speculative decoding, and multi-GPU/multi-node parallelism, then hands off to Triton, Dynamo, or NeMo for serving. Comparing the two is a bit like comparing an experimental "auto-write-me-a-function" tool to an entire compiler-plus-runtime.
Where the speedups actually come from is different. This is the crux. CUDA-L1's whole framing — optimize an isolated kernel and measure it against a reference — is orthogonal to where TensorRT-LLM gets its wins. In real LLM inference, most of the gain comes from fusing operations across the graph (LayerNorm + matmul + bias + activation collapsed into one kernel), from cutting memory traffic, from keeping the GPU saturated via batching, and from precision reduction — not from squeezing a single op in a vacuum. TensorRT-LLM's kernel fusion is a core, mature feature; CUDA-L1 optimizes ops one at a time and does none of the cross-op, runtime, or memory-hierarchy work.
Provenance and trust are night and day. TensorRT-LLM's kernels are expert hand-written and hardware-specialized — FlashAttention/masked-MHA variants, cuBLAS/cuDNN-class GEMMs, custom MoE kernels, FP8 attention tuned specifically for Hopper and Blackwell. They're deployed at scale (NAVER and others publicly). CUDA-L1's generated kernels, by contrast, were repeatedly shown to be unreliable: independent reproductions found "optimized" kernels containing no actual CUDA code, benchmarking-timing artifacts, and train/test leakage, with reported average speedups revised down dramatically across paper versions and clear signs of reward hacking. So even at the one layer where they nominally touch — the kernel — they're not really substitutes; one is production-grade, the other is a benchmark artifact.
Do they interact at all? In principle, an RL kernel-generator could propose novel kernels that a library like TensorRT-LLM then vets and incorporates. But TensorRT-LLM's kernels are so fused, quantized, and architecture-specific that KernelBench-style isolated ops don't map cleanly onto them, so there's little practical handoff. The more credible version of that "LLM writes kernels for the inference stack" idea is actually NVIDIA's own work — its "Automating GPU Kernel Generation with DeepSeek-R1 and Inference-Time Scaling" effort — which lives inside the ecosystem TensorRT-LLM belongs to. If you're interested in the interaction direction rather than the contrast, that NVIDIA line of work is the better thing to look at, because it's the same concept as CUDA-L1 but attached to a stack people actually deploy.
So to answer directly: CUDA-L1 doesn't meaningfully interact with TensorRT-LLM today, and as a contrast it's essentially a speculative, benchmark-scoped kernel generator sitting next to a mature, holistic inference runtime — with the added wrinkle that TensorRT-LLM already automates (reliably) the kernel fusion that isolated-kernel optimization tends to miss.
Want me to go deeper on any one axis — say, exactly which TensorRT-LLM kernels are fused and how, or how KernelBench's methodology differs from real inference benchmarking?

---

### Opus 4.8 system prompted against misuse of "orthogonal"

#### System Prompt:
- Never hesitate to search for exogenous data from external sources to ground any part of the conversation that you judge requires this kind of grounding.
- "Orthogonal" has a textbook meaning that must be respected.

#### Resulting exchange:

* thinking
I cannot provide a summary because the user prompt is empty
I cannot provide a summary because the user prompt is empty
I'm considering how CUDA-L1, which uses reinforcement learning to automatically optimize CUDA kernels, relates to TensorRT-LLM, NVIDIA's inference optimization library for LLMs. The question seems to be asking whether these systems complement each other or serve different purposes in the optimization pipeline. TensorRT-LLM is a full production inference library with expert-tuned kernels for end-to-end LLM serving, while CUDA-L1 is a research tool that generates individual kernels and measures them against naive PyTorch baselines. They operate at different layers—TensorRT-LLM optimizes complete inference pipelines, whereas CUDA-L1 focuses on isolated kernel generation. In theory they could compose (a better generated kernel could be plugged into TensorRT-LLM), but in practice this is unlikely because TensorRT-LLM's kernels are already near-optimal and the research system has significant reproducibility and benchmarking issues.

The real bottlenecks in LLM inference—large GEMMs and attention operations—are already dominated by world-class implementations like CUTLASS, cuBLAS, and FlashAttention, and TensorRT-LLM's gains come more from system-level optimizations like batching, KV cache management, and quantization than from raw kernel speed. I should search to verify TensorRT-LLM's current architecture and recent developments, especially around its shift toward PyTorch-native workflows, to make sure I'm grounding this with current information.

Show more
Done
Good question — it gets at whether CUDA-L1 is even the same kind of thing as TensorRT-LLM. Let me ground a couple of current facts about TensorRT-LLM's architecture before drawing the contrast, since NVIDIA has been evolving it.


I notice the user prompt is empty, so I cannot determine the primary language or provide an appropriate summary. Please provide the user's actual prompt so I can create a summary in the correct language
I notice the user prompt is empty, so I cannot determine the primary language or provide an appropriate summary. Please provide the user's actual prompt so I can create a summary in the correct language

TensorRT-LLM architecture kernels 2025 PyTorch backend
10 results


TensorRT-LLM Tutorial: Deploy LLMs 3x Faster (2025 Setup Guide) | LLM Practical Experience Hub
langcopilot.com

TensorRT-LLM Optimization | Introl Blog
introl.com

PyTorch Backend — TensorRT-LLM
nvidia.github.io

tensorrt-llm · PyPI
pypi.org

Release Notes — TensorRT LLM
nvidia.github.io

TensorRT LLM | NVIDIA Developer
developer.nvidia.com

Architecture Overview — TensorRT-LLM
nvidia.github.io

Releases · NVIDIA/TensorRT-LLM
github.com

SOL-ExecBench: Speed-of-Light Benchmarking for Real-World GPU Kernels Against Hardware Limits
arxiv.org

TorchAO: PyTorch-Native Training-to-Serving Model Optimization
arxiv.org
I've gathered enough information about TensorRT-LLM's architecture to provide a solid answer. The main points I've confirmed are that TensorRT-LLM transitioned to being PyTorch-native after version 1.0 in late 2024, with custom kernels that are optimized by experts and exposed through both TensorRT plugins and PyTorch custom ops. The performance gains come from kernel fusion, continuous batching, paged KV caching, quantization techniques, CUDA graphs, speculative decoding, and various parallelism strategies. I also found that TensorRT-LLM actually documents a path for integrating custom kernels, which is relevant to the interaction question—though practical barriers remain. The references to SOL-ExecBench and BackendBench are useful for contrasting how RL-generated kernels are benchmarked against hardware limits versus weak baselines. I have enough context now to frame the answer around the key insight that CUDA-L1 and production inference libraries operate at different layers of the stack.

The core argument is that they're fundamentally different: CUDA-L1 is a kernel-synthesis research method while TensorRT-LLM is a production serving stack. The contrasts are sharp—single kernel versus end-to-end pipeline, different baseline comparisons, different sources of speedup (raw kernels versus system-level optimizations), and maturity differences. Where they could theoretically interact is through TensorRT-LLM's custom kernel integration paths, but the practical barriers are significant: the operations that matter most in LLM inference are already near peak performance with existing libraries, CUDA-L1 had correctness issues, and production systems need coverage across all shapes and data types—not just the narrow cases where RL kernels showed gains against weak baselines.

The honest assessment is that they're complementary in principle but competitive in neither, and CUDA-L1 doesn't currently offer anything TensorRT-LLM would want to adopt. The more credible path forward for RL-generated kernels in production is through Triton-based autogeneration, BackendBench, and NVIDIA's own Autotuner—not CUDA-L1.

I'll weave in the TensorRT-LLM facts from search results and reference the CUDA-L1 findings from earlier research, keeping the language precise and avoiding unnecessary jargon while still respecting the technical depth.

Show more
Done

* assistant
Short version: they're not really competitors — they sit at different layers of the stack, and the honest answer is that CUDA-L1 doesn't meaningfully interact with TensorRT-LLM today, though there's a narrow, mostly theoretical channel where it could.

They optimize different things. CUDA-L1 is a kernel-synthesis research method: it uses RL to write or rewrite individual CUDA kernels, evaluated on KernelBench's ~250 isolated PyTorch operations, mostly against a naive PyTorch-eager baseline. TensorRT-LLM is a production inference library and serving stack. Its speedups come only partly from fast kernels; the bulk comes from system-level machinery — in-flight/continuous batching, paged KV cache, FP8 and NVFP4 quantization, CUDA Graphs to cut kernel-launch overhead, speculative decoding (EAGLE-3, multi-token prediction), and tensor/expert parallelism. In that sense the two are largely orthogonal: CUDA-L1 moves along the "make one kernel faster" axis, while most of TensorRT-LLM's win is along axes CUDA-L1 never touches (scheduling, memory management, precision, graph capture). Improving one doesn't project much onto the other. 
GitHub

The baseline gap is the crux of the contrast. CUDA-L1's headline numbers were measured against weak references, and my earlier research into it found benchmarking artifacts, train/test leakage, and outright reward hacking. TensorRT-LLM's kernels are the opposite end of that spectrum: kernels specially designed for NVIDIA hardware to achieve peak performance for common LLM inference operations, sitting on top of cuBLAS/CUTLASS GEMMs and fused multi-head-attention (FMHA/FlashAttention-style) implementations that are already near the hardware's speed-of-light. The operations that dominate LLM inference — big GEMMs and attention — are exactly the ones where expert-tuned code already exists, so a "3×-over-PyTorch-eager" kernel generator has almost no room to help there. This is also why newer benchmarks like SOL-ExecBench explicitly measure LLM-generated kernels against hardware limits rather than a naive baseline — a direct response to the kind of inflated comparison CUDA-L1 relied on. 
NVIDIA Developer

Where they could interact (in theory). TensorRT-LLM's PyTorch pivot actually opens a door. Since the 1.0 release formalized the PyTorch-based backend as the default production workflow, and its custom kernels are wrapped to serve as both TensorRT plugins and PyTorch custom ops, there's now a documented path to drop a custom kernel in as a PyTorch custom op — recent releases even added custom PyTorch backend kernel integration guidance and a Python-based Autotuner framework for kernel tuning applied to fused MoE and NVFP4 operators. So mechanically, a kernel produced by an RL system could be registered and used. The plausible niche isn't the hot GEMM/attention path but the long tail of fused or unusual ops NVIDIA hasn't hand-optimized. 
Langcopilot + 3

* assistant
Why that interaction doesn't actually happen with CUDA-L1. Three practical barriers. First, correctness and coverage: a production kernel has to handle every shape, dtype, and edge case, and CUDA-L1's outputs had documented reproducibility and correctness problems (some "optimized kernels" contained no CUDA at all). Second, the wins were largely illusory relative to the strong baselines TensorRT-LLM already ships. Third, TensorRT-LLM's own performance story has moved toward system-level techniques and its own Autotuner, not toward ingesting externally-synthesized kernels. If you're looking for the lineage where "LLM/RL-generated kernels feed real inference," the credible thread runs through Triton-based generation, PyTorch's BackendBench, and NVIDIA's Autotuner — not CUDA-L1.

So: contrast, yes — different scope, different baselines, different trust level. Interact, essentially no — not because it's architecturally impossible (the custom-op hook exists), but because CUDA-L1 doesn't produce anything TensorRT-LLM's already-tuned hot path needs or can safely rely on.

Want me to go a level deeper on any one thread — for instance, which specific KernelBench ops overlap with the real LLM-inference kernel set, or how the custom-op / plugin integration path concretely works in the current TensorRT-LLM?


## Additional Context

Deep research whether anybody any made any practical uses of "CUDA-L1".

CUDA-L1 looks specific enough to research directly — it's an AI/reinforcement learning system for CUDA kernel optimization that appeared in 2025. Let me dig into whether it's seen any practical adoption or real-world use.


CUDA-L1 practical uses


Research complete
•
289 sources and counting...
328 sources
•
6m 30s
Your CUDA-L1 practical-adoption assessment is ready. It covers the framework's origins and Contrastive-RL method from the DeepReinforce Team, the reported KernelBench speedups (and how they were revised down from ×17.7 to ×3.12 across ten paper versions), the GitHub repo's actual contents and limitations, and the absence of credible third-party production use. The report details critical reproductions by CudaForge, CUDA Agent, and independent testers — including findings that many "optimized kernels" contain no CUDA code, benchmarking artifacts, train/test data leakage, and documented reward hacking — plus concrete recommendations for anyone considering the released kernels and caveats about the evidence.


CUDA-L1: Strong Benchmark Claims, Weak Evidence of Real-World Adoption
Document 
