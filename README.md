# Awesome-Serverless-Frameworks

## Top Serverless GPU & AI Compute Tools Ecosystem

**Curated List of SaaS Products & Open-Source GitHub Projects**  
*Focused on Per-Second GPU Billing, Sub-Second Cold Starts & Bring-Your-Own-Container Workloads*  
**Last updated: March 2026**

This repository tracks notable **SaaS platforms** and **open-source projects** for **Serverless GPU & AI Compute**. These tools let developers run GPU inference, training, and sandbox workloads without managing infrastructure — paying per second of compute rather than for idle capacity, and scaling to zero when nothing is running.

**Examples** include Modal, RunPod, Baseten, Together AI, Replicate, Beam Cloud, Cerebrium, and Banana (the category leaders).

**Open-source emphasis**: This section is heavily expanded with every major active project for self-hosting, container-native runtimes, and transparent GPU billing — ideal for AI engineers prioritizing control, avoiding vendor lock-in, and running production inference on their own hardware or cloud accounts.

Contributions welcome! Open a PR to add/update entries. Keep descriptions factual and link to official sites.

## Table of Contents
- [SaaS/Hosted Platforms](#saas-hosted-platforms)
- [Open-Source GitHub Projects](#open-source-github-projects)
- [How to Contribute](#how-to-contribute)
- [Disclaimer](#disclaimer)

## SaaS/Hosted Platforms

- **[Modal](https://modal.com/)**  
  **The category-defining serverless GPU platform** — raised $750M at a **$15.75B valuation** in October 2026 [citation:1][citation:13]. Revenue run rate crossed **$1B annually**, with usage tripling in five months [citation:13]. **Per-second GPU billing**: H100 SXM5 at **$0.001097/sec (~$3.95/hr)**, B200 at **$0.001736/sec**, B300 at **$0.001972/sec** [citation:2]. **Python-native** — decorate functions with `@app.function(gpu="H100")` and Modal handles container builds, scaling, and GPU scheduling. **Sub-second cold starts** via custom container runtime and distributed storage layer. **Best for developers who want Python-native serverless without Kubernetes or YAML.**

- **[RunPod](https://www.runpod.io/)**  
  **The cost-effective serverless GPU option** — per-second billing with **scale-to-zero** for variable workloads, or always-running workers for consistent traffic with discounts via sales [citation:15]. **GPU pricing**: A4000 at **$0.00016/sec**, L4 at **$0.00019/sec**, A100 80GB at **$0.00076/sec**, H100 PRO at **$0.00116/sec**, H200 PRO at **$0.00155/sec**, B200 at **$0.00240/sec** [citation:3]. **Billing starts when the worker begins running** — container pulls and model downloads from cache are free [citation:15]. **Custom pricing for enterprise workloads.** **Best for teams wanting maximum GPU selection at competitive per-second rates.**

- **[Baseten](https://www.baseten.co/)**  
  **Enterprise-grade serverless inference with model performance focus** — in talks for a funding round valuing it at **$26B**, up from $13B in June 2026 [citation:4]. Provides the infrastructure for companies that "don't necessarily have access to the infrastructure teams of the frontier labs" [citation:4]. **Best for production ML teams needing dedicated performance guarantees.**

- **[Together AI](https://www.together.ai/)**  
  **The open-source model inference platform at scale** — raised **$800M at $8.3B valuation** in July 2026 [citation:8]. **Annual bookings crossed $1.15B** as open-source model usage tripled industry-wide [citation:8]. Customers report **6x to 60x cost savings** compared to closed-model pricing [citation:8][citation:20]. **Never built a proprietary foundation model** — focuses entirely on making open-source models cheap and fast to run [citation:20]. **Best for teams wanting frontier-quality inference on open-weight models at a fraction of closed-model cost.**

- **[Replicate](https://replicate.com/)**  
  **The open catalog for arbitrary model deployment** — run any model packaged with **Cog** (open-source container format) [citation:7]. **Per-second GPU billing**: H100 at **$0.001525/sec (~$5.49/hr)**, A100 80GB at **$0.001400/sec (~$5.04/hr)**, L40S at **$0.000975/sec** [citation:7]. **Private models run on dedicated hardware** — billed for setup, idle, and active time unless using fast-booting fine-tunes [citation:7]. **Cold boots can take several minutes for large models** — set minimum warm instances to eliminate latency at the cost of idle billing [citation:19]. **Best for image/video/audio models and custom architectures** that don't fit curated LLM platforms [citation:19].

- **[Beam Cloud](https://www.beam.cloud/)**  
  **The open-source Modal alternative** — 100% open-source and self-hostable via the **Beta9 runtime** (AGPL-3.0, open-sourced May 2024) [citation:5][citation:11]. Used by **Coca-Cola, Magellan AI, Shippabo, and Stratum** [citation:11]. **Python/TypeScript decorators** with **GPU checkpoint restore** for pausing and resuming sandboxes while preserving running processes, **gVisor isolation**, and **multi-node clusters** [citation:11]. **Billed per millisecond** while containers run; image pulls and machine startup are free [citation:17]. **Developer tier caps GPU concurrency at 5** — load testing requires Team plan [citation:5]. **Best for teams wanting Modal-like DX with zero vendor lock-in.**

- **[Cerebrium](https://www.cerebrium.ai/)**  
  **Serverless GPU for real-time AI workloads** — **$9M funding** from Y Combinator, Gradient Ventures, and Authentic Ventures [citation:18]. **Per-second billing with no idle charges** across 12+ GPU types from T4 to H200 in US, EU, and Asia [citation:18]. **H100 80GB at $2.21/hr, T4 at $0.59/hr**. **Cold-start time is not billed** [citation:18]. **Best for teams deploying latency-sensitive AI workloads across multiple regions.**

- **[Banana](https://www.banana.dev/)**  
  **Serverless GPU inference hosting platform** with Python decorators for model deployment and per-second billing. Accessible entry point for simple inference endpoints.

## Open-Source GitHub Projects

- **[Beta9 (Beam Cloud)](https://github.com/beam-cloud/beta9)**  
  **The open-source runtime behind Beam Cloud** — AGPL-3.0 licensed, open-sourced May 2024 [citation:5]. **Custom container runtime and distributed storage layer** designed for **large container images with low cold start** [citation:11]. **gVisor security isolation** for sandboxed execution. **Memory/file system snapshotting** and **GPU checkpoint restore** — stop and resume sandboxes while preserving running processes [citation:11]. **Multi-node clusters** for distributed training and inference. **Deployable on any cloud, on-premises hardware, or hybrid architectures** — the same Python decorator syntax and CLI work whether managed or self-hosted [citation:5]. **Built in Go (72.5%)** for faster container scheduling than Python-native runtimes [citation:5]. **Best for teams wanting Modal-like serverless GPU without vendor lock-in.**

- **[Cog (Replicate)](https://github.com/replicate/cog)**  
  **Open-source tool for packaging machine learning models** into production-ready containers. Define your environment in a `cog.yaml`, and Cog generates a Docker image with an HTTP API server. **The same packaging format works on Replicate or anywhere you can run Docker** — no lock-in [citation:19]. Supports arbitrary model code, custom architectures, and GPU requirements. **Best for teams wanting reproducible model packaging that travels across platforms.**

- **[vLLM](https://github.com/vllm-project/vllm)**  
  **The high-throughput inference engine for open-weight models** — Apache 2.0 licensed. **PagedAttention and continuous batching** deliver state-of-the-art serving throughput. **The default engine for self-hosted GPU inference** when you want to saturate hardware and control costs. Runs on any cloud or on-premises GPU.

- **[SGLang](https://github.com/sgl-project/sglang)**  
  **Fast serving framework with RadixAttention for efficient prefix caching** — Apache 2.0 licensed. **Optimized for structured generation and multi-turn conversations** where prompt prefixes repeat. **Best for high-throughput serving with shared context across requests.**

- **[Text Generation Inference (TGI)](https://github.com/huggingface/text-generation-inference)**  
  **Hugging Face's production inference server** with tensor parallelism, continuous batching, and token streaming. Apache 2.0 licensed. **Best for teams already in the Hugging Face ecosystem.**

- **[OpenLLM](https://github.com/bentoml/OpenLLM)**  
  **BentoML's platform for deploying and operating open-source LLMs** with OpenAI-compatible API, quantization, and multi-GPU support. **Best for teams wanting a higher-level abstraction over vLLM and TGI.**

### Additional Strong Open-Source Options

- **LocalAI** — Free, open-source OpenAI drop-in replacement for local inference. MIT licensed.
- **llama.cpp** — C/C++ inference for quantized models. Runs on CPU and GPU with minimal dependencies.
- **ExLlamaV2** — Fast inference for consumer GPUs with quantized models. MIT licensed.
- **Ray Serve** — Distributed model serving built on Ray with autoscaling and composition.
- **KServe** — Kubernetes-native model serving with standard inference protocol and scale-to-zero.

**Frameworks for building custom systems**: Combine **Beta9** for self-hosted serverless GPU with Modal-like DX and checkpoint restore, **Cog** for portable model packaging that runs anywhere Docker runs, **vLLM** or **SGLang** for high-throughput inference engines, **Ray Serve** for distributed serving with autoscaling, and **KServe** for Kubernetes-native model deployment — to build a complete serverless GPU stack that runs on your own hardware or any cloud account.

## How to Contribute

1. Fork the repo.
2. Add/edit entries in `README.md` (follow existing format).
3. Include: name, link, 1–2 sentence description, and whether it's SaaS or open-source.
4. Submit PR with a short explanation.

Star the repo if you find it useful!

## Disclaimer

- This is a **community-curated** list — not exhaustive and not an endorsement.
- Serverless GPU platforms differ significantly in billing granularity, cold-start performance, and lock-in risk. **Modal and RunPod lead on Python-native DX and GPU selection** [citation:2][citation:3]. **Together AI offers 6x-60x cost savings on open-weight models** compared to closed-model APIs [citation:8]. **Replicate's Cog packaging is portable** but cold boots can take minutes without warm instances [citation:19]. **Beam Cloud's Beta9 is the only fully open-source serverless GPU runtime** with GPU checkpoint restore [citation:11]. **Lepton AI was acquired by NVIDIA in 2025 and its open-source plans were cancelled** — the platform is no longer an independent option [citation:9]. **OctoAI was acquired by NVIDIA in 2024** and no longer operates independently [citation:10]. **Pricing changes frequently** — verify against provider pages before committing.
- Self-hosted open-source solutions require proper GPU infrastructure, container runtime configuration, and monitoring for cold-start latency.

---

**Made for AI engineers, ML platform teams, and developers building serverless GPU inference and training pipelines.**  
Let's make serverless GPU compute more open, portable, and cost-effective.
