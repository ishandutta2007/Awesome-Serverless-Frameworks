# Awesome-Serverless-Frameworks

# Awesome-Serverless-Frameworks

# Top Serverless Frameworks Ecosystem

**Curated List of SaaS Products & Open-Source GitHub Projects**  
*Focused on Infrastructure as Code, Edge Deployment & Full-Stack Serverless DX*  
**Last updated: March 2026**

This repository tracks notable **SaaS platforms** and **open-source projects** for **Serverless Frameworks**. These tools help developers define, deploy, and manage serverless applications — abstracting away infrastructure details while providing local development, CI/CD integration, and multi-cloud or edge deployment capabilities.

**Examples** include AWS SAM, Serverless Framework, SST, Vercel, Netlify, AWS CDK, Cloudflare Workers, Pulumi, Terraform, and Firebase (the category leaders).

**Open-source emphasis**: This section is heavily expanded with every major active project for self-hosting, multi-cloud IaC, and transparent deployment pipelines — ideal for developers prioritizing portability, avoiding vendor lock-in, and building serverless applications that can run anywhere.

Contributions welcome! Open a PR to add/update entries. Keep descriptions factual and link to official sites.

## Table of Contents
- [SaaS/Hosted Platforms](#saas-hosted-platforms)
- [Open-Source GitHub Projects](#open-source-github-projects)
- [How to Contribute](#how-to-contribute)
- [Disclaimer](#disclaimer)

## SaaS/Hosted Platforms

- **[Vercel](https://vercel.com/)**  
  **The framework-native platform for Next.js and frontend applications.** Fluid Compute pricing bills based on **Active CPU time** — paused during I/O waits — plus provisioned memory and invocations. **Hobby tier (non-commercial)**: 4 hours Active CPU, 360 GB-hrs memory, 1M invocations included. **Pro at $20/seat** with on-demand usage. Regional Active CPU rates vary from **$0.128/hr (Portland/Cleveland) to $0.221/hr (São Paulo)**. Fluid Compute's concurrency model serves multiple requests per warm instance, improving cost efficiency for bursty traffic. **Best for Next.js-first teams** and streaming workloads requiring longer request windows.

- **[Netlify](https://www.netlify.com/)**  
  **Credit-based platform with unlimited team members on Pro.** **Pro at $20/month** for 3,000 credits, scaling to 20,000 credits, with rollover on higher tiers. Functions billed in **GB-Hour units** — 10 credits per GB-Hour. **Default 1 GB memory**, up to 4 GB on Pro/Enterprise. **Compute rate doubled in April 2026** — function-heavy apps may now cost more on Netlify than Vercel. **Standard Functions: 60s limit; modern streaming: 10s; Background Functions: 15 minutes**. **Best for collaboration-heavy teams** valuing unlimited members and free deploy previews.

- **[Firebase](https://firebase.google.com/)**  
  **Google's serverless platform** with Cloud Functions for Firebase (Node.js), Firestore, Authentication, and Hosting. **Best for mobile and web apps** tightly coupled with Firebase's BaaS offerings.

- **[AWS Amplify](https://aws.amazon.com/amplify/)**  
  Full-stack serverless platform for frontend and mobile apps with AWS backend provisioning, CI/CD, and hosting. **Best for frontend teams wanting AWS backend without deep AWS expertise**.

## Open-Source GitHub Projects

- **[Serverless Framework](https://github.com/serverless/serverless)**  
  **The original multi-cloud serverless framework** — MIT licensed core, free for individuals and teams under $2M revenue. **YAML syntax** deploys both code and infrastructure in ~40 lines for a Lambda + API Gateway setup (vs 80 for SAM, 200 for raw CloudFormation). **Plugin ecosystem is the largest**: serverless-offline, python-requirements, webpack/esbuild, warmup, domain-manager, canary-deployments. **v4 changed licensing** for large organizations — pin your version. **Trade-offs**: slow first deploy (60-90s CloudFormation stack creation), CloudFormation drift risk, package size blowout. **Best for teams wanting maximum plugin flexibility** and multi-cloud capability (AWS, Azure, GCP, Cloudflare, Kubernetes).

- **[SST](https://github.com/sst/sst)**  
  **The full-stack serverless framework built on CDK** — **Live Lambda Development** runs functions locally while interacting with real AWS resources, eliminating deploy-then-test cycles. **Deployment speed**: code-only changes in **5-15 seconds**, infrastructure in 30-90 seconds. **Resource linking and type-safe config** provide a generation-ahead DX compared to SAM and Serverless Framework. **Trade-offs**: newer, smaller community, locks you into AWS and SST's abstraction layer. **Best for full-stack applications on AWS** where developer experience is the priority.

- **[AWS CDK](https://github.com/aws/aws-cdk)**  
  **Programmatic infrastructure as code** in TypeScript, Python, Java, C#, or Go. **Constructs** compose reusable infrastructure patterns. **When to switch**: SAM → CDK when you need non-serverless resources. **Best for teams wanting type-safe infrastructure** with full AWS coverage beyond serverless.

- **[Pulumi](https://github.com/pulumi/pulumi)**  
  **Multi-cloud IaC using general-purpose languages** — TypeScript, Python, Go, C#, Java. **More portable than CDK or SAM** — decoupled from any specific serverless model. **Best for multi-cloud or infrastructure-heavy projects** wanting programmatic control.

- **[Terraform](https://github.com/hashicorp/terraform)**  
  **The multi-cloud IaC standard** — HCL declarative configuration with 3,000+ providers. **When to switch**: Serverless → Terraform when going multi-cloud. **Best for organizations wanting cloud-agnostic infrastructure** with a mature ecosystem.

- **[Cloudflare Workers](https://github.com/cloudflare/workers-sdk)**  
  **Edge-native serverless with V8 isolates** — **10-50ms cold starts** and **20-40ms average latency** in Singapore vs 100-700ms cold start for AWS Lambda in the same region. **Flat $5/month** account pricing with no bandwidth meter, beating Vercel's $20/seat + usage meters at scale. **Wrangler CLI** for local development and deployment. **Durable Objects** provide stateful coordination at the edge. **Best for latency-sensitive edge logic** and CDN-adjacent computing.

- **[Apache OpenWhisk](https://github.com/apache/openwhisk)**  
  **Open-source serverless platform** deployable on Kubernetes and OpenShift. **Composer** provides JavaScript-based function composition. **Serverless Framework plugin** available for OpenWhisk. **Best for self-hosted serverless** on Kubernetes.

- **[Self-Hosted Serverless](https://github.com/mstgnz/self-hosted-serverless)**  
  **Lightweight, self-hostable serverless framework in Go** — runs on your own infrastructure without vendor lock-in. **WebAssembly support** for multi-language functions, **HTTP and gRPC** dual protocol, **PostgreSQL/SQLite/Redis** integration, and **built-in metrics** for execution times, error rates, and cold starts. **Docker-ready** with CLI for function management. **Best for teams wanting complete control** over their serverless runtime.

### Additional Strong Open-Source Options

- **OpenFaaS** — Serverless functions on Kubernetes with Docker/OCI image support.
- **Fission** — Kubernetes-native serverless framework with fast cold starts.
- **Kubeless** — Kubernetes-native serverless framework using CRDs (now largely unmaintained).
- **Nuclio** — High-performance serverless framework for data science and real-time workloads.

**Frameworks for building custom systems**: Combine **SST** for full-stack AWS development with Live Lambda, **Serverless Framework** for plugin-rich multi-cloud deployments, **AWS SAM** for first-party AWS-native simplicity with SAM Accelerate, **Cloudflare Workers** for edge-native low-latency logic, and **Terraform** or **Pulumi** for multi-cloud infrastructure control — to build a serverless deployment strategy tailored to your cloud, team skills, and portability requirements.

## How to Contribute

1. Fork the repo.
2. Add/edit entries in `README.md` (follow existing format).
3. Include: name, link, 1–2 sentence description, and whether it's SaaS or open-source.
4. Submit PR with a short explanation.

Star the repo if you find it useful!

## Disclaimer

- This is a **community-curated** list — not exhaustive and not an endorsement.
- Serverless frameworks differ significantly in cloud support, deployment speed, and lock-in risk. **SST offers the best developer experience on AWS** with Live Lambda Development and 5-15 second code deploys. **Serverless Framework v4 changed licensing** for organizations over $2M revenue — pin your version. **Netlify's compute rate doubled in April 2026** — function-heavy apps may cost more there than on Vercel. **Cloudflare Workers offer the fastest cold starts (10-50ms) and lowest edge latency** but are coupled to Cloudflare's environment. **Vercel's Hobby tier is non-commercial only** — commercial apps require Pro. **The biggest lock-in is the runtime, not the framework** — Lambda code uses AWS SDK calls and event source formats regardless of deployment tool.
- Self-hosted open-source solutions require proper Kubernetes infrastructure, container runtime configuration, and monitoring for cold-start latency.

---

**Made for developers, platform engineers, and teams building serverless applications across cloud and edge environments.**  
Let's make serverless deployment more open, portable, and developer-friendly.
