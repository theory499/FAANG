# 30-Day AI Engineering Skill Upgrade Roadmap
**For: Karthik Ramesh — Associate Principal Engineer → AI Platform / Agent Engineer (FAANG, Bangalore)**
**Start: May 7, 2026 | End: June 5, 2026**

---

## How to Use This Plan

You have 15 years of experience and a full-time job at reva.ai. This plan is designed for **20 hours/week** = ~3 hours per weekday + ~5 hours per weekend day. Total: **~85 hours over 30 days.**

**Daily template (weekdays):**
- **Morning (60 min, 6:30–7:30 AM):** Theory/reading — one paper, chapter, or concept.
- **Lunch break (20 min):** DSA — one LeetCode problem.
- **Evening (90–120 min, 8:30–10:30 PM):** Hands-on coding / labs / projects.

**Weekend template:**
- **Saturday (5 hrs):** Deep project work + system design practice.
- **Sunday (3 hrs):** DSA batch (3–4 problems) + mock interview + week review.

**Five things I want you to do differently from a typical "study plan":**
1. **Build, don't just read.** 70% of your time is hands-on. Reading without a keyboard is wasted.
2. **Lean on your moat.** Your IBAC/PBAC for multi-agent systems is rare. Every project should weave it in — that's how you stand out, not by being the 1000th person who built a RAG pipeline.
3. **Write as you learn.** Each week ends with a 500-word blog draft. By Day 30 you'll have 4 posts ready to publish — interview lubricant.
4. **Apply during prep, not after.** Start submitting applications by Day 14. Interview pipelines take 6–8 weeks; you want phone screens hitting in Week 4 onward.
5. **Pin the basics first.** PyTorch and DSA are non-negotiable; do them daily, never skip.

---

## Day 0 (Today): Setup & Pre-Flight Checklist

Spend 2 hours TODAY to remove all friction for the next 30 days:

**Tools to install (Mac/Linux):**
- Python 3.11+, pyenv, uv (or poetry)
- Docker Desktop + kind (local Kubernetes)
- VS Code + Cursor (free tier) + GitHub Copilot
- `gh` CLI, signed in to your GitHub
- Cloud CLIs: `aws`, `gcloud`, `kubectl`, `helm`
- Optional but recommended: a $300 Lambda Labs / RunPod credit pack OR Google Colab Pro+ ($50/mo) for GPU access in Weeks 3–4

**Accounts to create:**
- LeetCode Premium (₹2,500/yr — *worth it*; gives company-tagged questions)
- Pramp (free, peer mocks)
- Levels.fyi (free, offer benchmark)
- Hugging Face (free; pull a 7B model token)
- LangSmith (free tier)
- Arize Phoenix (free, self-host)
- W&B (free)
- One paid course: **DeepLearning.AI's "AI Agentic Design Patterns with AutoGen + Crew" + "LangGraph"** (free) OR **Sebastian Raschka's "Build an LLM from Scratch" companion** (~$45)

**Books to order/download (today):**
1. *Generative AI System Design Interview* — Aminian & Sheng (ByteByteGo) — **highest priority**
2. *AI Engineering* — Chip Huyen (O'Reilly 2025)
3. *Build a Large Language Model from Scratch* — Sebastian Raschka
4. *System Design Interview Vol 1 & 2* — Alex Xu (you likely have v1 from your past)
5. *Designing Machine Learning Systems* — Chip Huyen (companion code: chiphuyen/dmls-book)

**Repos to clone today:**
```
~/learn/
  ├─ neetcode-150/       # DSA tracker
  ├─ pytorch-from-scratch/  # Raschka's LLM book code
  ├─ vllm/               # for code-reading
  ├─ ray/                # for code-reading
  ├─ langgraph/          # for code-reading
  ├─ projects/
  │   ├─ agent-iam/      # Project 1 — your moat
  │   ├─ prod-agent-stack/  # Project 2
  │   └─ agentic-rag-bench/  # Project 3
```

**Block your calendar:** put 6:30–7:30 AM and 8:30–10:30 PM on every weekday for the next 30 days as recurring "Career — DO NOT SCHEDULE." Tell your spouse/family.

---

# WEEK 1 (May 7–13) — Foundations Reset

**Theme:** Refresh the ML/DL fundamentals you don't use daily, get hands-on with PyTorch, start DSA cadence, refresh system design fundamentals through an ML lens.

**Why this week matters:** Every interview will probe transformer internals, attention math, and basic ML reasoning. You can't fake this. Three days of focused refresh now prevents embarrassing moments in week 4 onsites.

**End-of-week deliverables:**
- ✅ Mini-transformer from scratch (200 lines of PyTorch, runs locally)
- ✅ 12 LeetCode mediums solved (arrays, hashing, two-pointer, sliding window)
- ✅ Resume v1 rewritten with new title/keywords
- ✅ LinkedIn headline + about section updated
- ✅ Blog post draft #1: *"Understanding Transformer Attention from Scratch"*

### Day 1 (Wed, May 7) — Linear Algebra & Probability Refresh + DSA kickoff
- **Morning:** 3Blue1Brown "Essence of Linear Algebra" episodes 1–7 (vectors, matrices, eigenvectors). Watch at 1.5×.
- **Lunch DSA:** LeetCode #1 *Two Sum* + #49 *Group Anagrams* (hashmap warm-up).
- **Evening:**
  - Skim Stanford CS229 Lecture Notes ch 1–2 (probability, MLE).
  - Start `pytorch-from-scratch` repo: install PyTorch, run `torch.tensor`, autograd hello-world.
- **Output:** Notebook `01_pytorch_basics.ipynb` with autograd example.

### Day 2 (Thu) — Classical ML Refresh
- **Morning:** Read Chip Huyen *Designing ML Systems* ch 1–3 (intro, data, feature engineering).
- **Lunch DSA:** LeetCode #167 *Two Sum II*, #15 *3Sum* (two-pointer pattern).
- **Evening:**
  - Build a logistic regression in pure NumPy on a sklearn dataset.
  - Then rebuild it in PyTorch using `nn.Linear` and `BCELoss`.
- **Output:** `02_logreg_numpy_vs_torch.ipynb` showing both implementations.

### Day 3 (Fri) — Neural Networks & Backprop
- **Morning:** Andrej Karpathy's "Neural Networks: Zero to Hero" video 1 (micrograd).
- **Lunch DSA:** LeetCode #128 *Longest Consecutive Sequence*, #238 *Product of Array Except Self*.
- **Evening:** Implement a 2-layer MLP in PyTorch on MNIST. Hit 97%+ accuracy.
- **Output:** `03_mlp_mnist.py` script (not notebook — practice script form).

### Day 4 (Sat — DEEP DAY, 5 hrs) — Transformers from Scratch (Part 1)
- **Block 1 (2 hrs):** Read *Build an LLM from Scratch* ch 1–3 (tokenization, attention).
- **Block 2 (90 min):** Implement BPE tokenizer (use `tiktoken` to verify).
- **Block 3 (90 min):** Implement single-head self-attention from scratch in PyTorch — the famous `Attention(Q,K,V) = softmax(QK^T/√d)V` line. No copying — write it from memory at the end.
- **Output:** `04_attention_from_scratch.ipynb` with shape annotations and a sanity-check run.

### Day 5 (Sun — DEEP DAY, 3 hrs) — Transformers from Scratch (Part 2) + Mock + Resume
- **Block 1 (90 min):** Multi-head attention + positional encoding (sinusoidal first, then RoPE). Read Su et al. RoPE paper section 3.
- **Block 2 (60 min):** Resume rewrite v1 — apply the title surgery from the career roadmap. Inject keywords: PyTorch, vLLM, Ray Serve, agentic AI.
- **Block 3 (30 min):** LinkedIn headline + about section. Set headline to: *"AI Platform Engineer | Agentic AI on Bedrock & LangGraph | Multi-Agent Security (IBAC/PBAC) | 15 yrs scaling cloud platforms | Bangalore"*
- **Output:** `resume_v1.pdf` ready for review.

### Day 6 (Mon, May 12) — Mini-Transformer Decoder
- **Morning:** Karpathy's "Let's build GPT: from scratch" video (first 60 min).
- **Lunch DSA:** LeetCode #76 *Minimum Window Substring* (hard but worth it — sliding window).
- **Evening:** Implement a 4-layer decoder-only transformer (~6M params). Train on Shakespeare text. Generate 200 tokens of fake-Shakespeare.
- **Output:** `05_nano_gpt.py` — your own nano-GPT.

### Day 7 (Tue) — System Design Refresh + Week 1 wrap
- **Morning:** Alex Xu *System Design Vol 1* — re-skim ch 1 (back-of-envelope), ch 5 (consistent hashing), ch 6 (KV store), ch 9 (URL shortener).
- **Lunch DSA:** LeetCode #424 *Longest Repeating Character Replacement*.
- **Evening:**
  - 30 min: do a self-led system design — *"Design a URL shortener"* — speak it out loud, time yourself to 35 min.
  - 60 min: write Blog Post #1 draft: *"Building Transformer Attention from Scratch in 200 Lines of PyTorch"*. Don't publish yet.
  - 30 min: review Week 1, update tracker.
- **Output:** Blog draft #1 in your `blog/` folder.

**Week 1 self-check:**
- [ ] Can you derive the attention formula on a whiteboard from memory?
- [ ] Can you explain why we divide by √d_k? (numerical stability for softmax)
- [ ] 12 LeetCode mediums solved, all in <35 min?
- [ ] Resume sent to 2 friends for review?

---

# WEEK 2 (May 14–20) — Production AI Stack + ML System Design

**Theme:** Close your biggest gap — production LLM serving infrastructure (vLLM, Ray Serve, KServe). This is exactly what FAANG AI Platform JDs require and what most candidates don't have.

**Why this week matters:** Your K8s management experience + this week's serving stack = the AI Platform Engineer profile. Without this, you're an "AI agent dev"; with this, you're an "AI Platform Engineer." Title-and-comp shift of ₹15–25 LPA.

**End-of-week deliverables:**
- ✅ Llama 3.1 8B deployed on local kind cluster with vLLM + KServe
- ✅ Ray Serve autoscaling demo working on GKE
- ✅ 14 LeetCode mediums (graphs, trees, BFS/DFS)
- ✅ 3 ML system designs practiced (RAG, vector search, model serving)
- ✅ Blog draft #2: *"Serving LLMs on Kubernetes: vLLM + Ray Serve + KServe Reference Architecture"*
- ✅ **First 5 job applications submitted** (Tier-A targets from career roadmap)

### Day 8 (Wed, May 14) — LLM Inference Optimization Theory
- **Morning:** Read these in order (90 min):
  1. PagedAttention paper (vLLM): arXiv:2309.06180 — sections 1–4.
  2. FlashAttention v2 paper section 2 (forward pass).
  3. The "Talks at Google: vLLM" YouTube talk (skim chapters).
- **Lunch DSA:** LeetCode #200 *Number of Islands* (graph BFS/DFS).
- **Evening:** Install vLLM locally. Pull a small model (`microsoft/Phi-3-mini-4k-instruct` or `Qwen2.5-1.5B`). Run `vllm serve` and hit it with `curl`.
- **Output:** Notebook with latency measurements (p50, p95) for different `max_tokens`.

### Day 9 (Thu) — KV Cache, Quantization, Speculative Decoding
- **Morning:**
  - Skim Lilian Weng's blog post *"Large Transformer Model Inference Optimization."*
  - Read about quantization: GPTQ, AWQ, FP8 (skim original papers' abstracts + intro).
- **Lunch DSA:** LeetCode #133 *Clone Graph*, #207 *Course Schedule* (topological sort).
- **Evening:** Run the same model with INT8 quantization (`vllm` supports it). Compare latency and output quality. Document the tradeoff in a table.
- **Output:** Update notebook with quantization comparison.

### Day 10 (Fri) — KServe + Kubeflow Basics
- **Morning:** KServe docs — read "InferenceService" concept, autoscaler, transformer/predictor architecture (60 min).
- **Lunch DSA:** LeetCode #235 *LCA of BST*, #102 *Binary Tree Level Order Traversal*.
- **Evening:**
  - Install KServe on your local kind cluster (helm chart).
  - Deploy a simple HuggingFace text classifier as an `InferenceService`.
- **Output:** `kserve-demo/` repo with manifests + README.

### Day 11 (Sat — DEEP DAY, 5 hrs) — Ray Serve + Multi-Replica LLM
- **Block 1 (90 min):** Ray docs — *Serve Quickstart*, *Deployment Graphs*, *Autoscaling*.
- **Block 2 (2 hrs):** Build a Ray Serve deployment that wraps vLLM with autoscaling (1–4 replicas). Test scale-up under load using `wrk` or `vegeta`.
- **Block 3 (90 min):** Move it to GKE (free tier is fine for the demo) using KubeRay operator. Document the GPU node pool config.
- **Output:** `prod-agent-stack/` repo started — README architecture diagram.

### Day 12 (Sun — DEEP DAY, 3 hrs) — ML System Design Practice
- **Block 1 (90 min):** Read Aminian/Sheng *Generative AI System Design Interview* ch 1 (the 7-step framework) + ch 2 (Smart Reply / RAG over personal data).
- **Block 2 (60 min):** Self-led design out loud, recorded on your phone — *"Design a vector search service for 10B vectors with sub-50ms p99."* Cover: clarifying Qs → high-level → embedding pipeline → ANN index choice (HNSW vs IVF-PQ) → sharding → caching → eval → cost.
- **Block 3 (30 min):** Listen back, note 3 things you missed.
- **Output:** Voice memo + 1-page written summary.

### Day 13 (Mon, May 19) — Vector Databases In Depth
- **Morning:** Pinecone "Faiss" + Qdrant docs on HNSW. Read original HNSW paper (Malkov & Yashunin) abstract + intro.
- **Lunch DSA:** LeetCode #994 *Rotting Oranges*, #417 *Pacific Atlantic Water Flow*.
- **Evening:** Install Qdrant locally. Index 1M vectors from a public dataset (Cohere Wikipedia embeddings). Benchmark recall@10 vs `ef_search` parameter.
- **Output:** `vector-bench/` notebook with HNSW recall curves.

### Day 14 (Tue) — RAG Fundamentals + APPLY DAY
- **Morning:** Read Lewis et al. RAG paper + LangChain docs on hybrid retrieval (BM25 + dense + reranker).
- **Lunch DSA:** LeetCode #210 *Course Schedule II*.
- **Evening (CRITICAL):**
  - 60 min: Submit 5 job applications. Tier-A only. Use the list from the career roadmap. Customize each resume bullet to match the JD.
  - 30 min: Send 5 LinkedIn connection requests to ICs at the companies you applied to.
  - 60 min: Write Blog Post #2 draft: *"Serving LLMs on Kubernetes — A Reference Architecture."*
- **Output:** 5 applications submitted (track in a Google Sheet); blog draft #2 ready.

**Week 2 self-check:**
- [ ] Can you explain PagedAttention vs naive KV cache in 60 seconds?
- [ ] Can you draw the Ray Serve autoscaler control loop on a whiteboard?
- [ ] 14 LeetCode mediums done, all <30 min?
- [ ] First 5 applications out the door?
- [ ] Blog post #2 drafted?

---

# WEEK 3 (May 21–27) — Agentic AI Depth + GenAI System Design

**Theme:** Go from "I use LangGraph" to "I can architect agent platforms at scale." Add CrewAI, Google ADK, MCP/A2A protocols, agentic RAG patterns, and eval/observability — and start running ML system design mocks.

**Why this week matters:** This is where your existing reva.ai work compounds. You already understand multi-agent security; this week stitches that into the broader agentic AI platform conversation that every senior interview will go deep on.

**End-of-week deliverables:**
- ✅ Project 1 (`agent-iam`) MVP working — IBAC/PBAC enforcement on a 3-agent LangGraph workflow
- ✅ Comparison demo: same task in LangGraph vs CrewAI vs Google ADK
- ✅ MCP server + client implemented (your own; not just consuming someone else's)
- ✅ 16 LeetCode mediums (DP, heap, intervals)
- ✅ 4 GenAI system designs practiced (ChatGPT, agent platform, agentic RAG, fine-tuning pipeline)
- ✅ 1 mock interview completed
- ✅ Blog draft #3: *"Implementing IBAC for Multi-Agent LangGraph Systems"* — your differentiator post
- ✅ 10 more applications submitted

### Day 15 (Wed, May 21) — Agent Frameworks Deep Compare
- **Morning:** Read in order:
  1. LangGraph docs — re-read State, Checkpointing, Human-in-the-loop.
  2. CrewAI docs — Agents, Tasks, Crews, Process types.
  3. Google ADK docs — Agent abstractions, tools, A2A.
  4. Skim Microsoft Agent Framework intro.
- **Lunch DSA:** LeetCode #198 *House Robber*, #322 *Coin Change* (DP entry).
- **Evening:** Build the same task ("research a topic, write a summary, fact-check it") in LangGraph and CrewAI side-by-side. 80 lines each. Note design tradeoffs.
- **Output:** `agent-framework-compare/` repo with both implementations + comparison table in README.

### Day 16 (Thu) — MCP Protocol Deep Dive (your strategic bet)
- **Morning:** Anthropic MCP spec — read end-to-end (2025-11-25 version you already know). Focus on: Resources, Tools, Prompts, Sampling, Roots primitives.
- **Lunch DSA:** LeetCode #300 *Longest Increasing Subsequence*.
- **Evening:** Build your own MCP server in Python that exposes 3 tools (e.g., a SQL query tool with **IBAC enforcement** — perfect overlap with your reva.ai work). Connect it from Claude Desktop or a Python MCP client.
- **Output:** `mcp-iam-server/` — first half of `agent-iam` Project 1.

### Day 17 (Fri) — Agentic RAG + Evaluation
- **Morning:** Read arXiv:2501.09136 (Agentic RAG survey) sections 1–4. Skim arXiv:2506.10408 (Reasoning RAG).
- **Lunch DSA:** LeetCode #53 *Maximum Subarray*, #152 *Maximum Product Subarray*.
- **Evening:**
  - Install Arize Phoenix locally.
  - Wire it into Day 15's LangGraph implementation. Capture traces.
  - Run a 20-example golden-dataset eval with LLM-as-judge (use Claude/Gemini as judge).
- **Output:** Phoenix dashboard screenshot + eval results in README.

### Day 18 (Sat — DEEP DAY, 5 hrs) — Project 1 Build: `agent-iam`
- **Block 1 (90 min):** Architecture design. Write a 1-page design doc. Cover: IBAC vs PBAC tradeoff, token format (HMAC-sealed contextvars — pull from your reva.ai patterns but anonymized), chain receipts.
- **Block 2 (3 hrs):** Build the core enforcement layer. A LangGraph multi-agent workflow (3 agents — researcher, writer, fact-checker) where each tool call is gated by an IBAC policy decision point. Use your existing `@reva_ai_authorize` patterns conceptually but write fresh code (don't copy company IP).
- **Block 3 (30 min):** Write README with architecture diagram (use Mermaid or excalidraw).
- **Output:** Project 1 MVP — runnable demo + architecture doc.

### Day 19 (Sun — DEEP DAY, 3 hrs) — GenAI System Design + Mock Interview
- **Block 1 (90 min):** Aminian/Sheng *Generative AI System Design Interview* ch 3 (Personal Assistant / ChatGPT) + ch 5 (Image generation — skim). Take notes on the 7-step framework as applied.
- **Block 2 (60 min):** **MOCK INTERVIEW.** Pramp or Interviewing.io — book a session. ML system design topic. Aim for "Design ChatGPT with persistent memory."
- **Block 3 (30 min):** Post-mock review: what 2 things did you fumble?
- **Output:** Mock feedback notes; if Pramp, save the recording.

### Day 20 (Mon, May 26) — LoRA / QLoRA Fine-Tuning Hands-On
- **Morning:** Read LoRA paper (Hu et al. 2021) sections 1–4. Read QLoRA paper section 3 (4-bit NF4).
- **Lunch DSA:** LeetCode #1143 *Longest Common Subsequence*.
- **Evening:** Spin up a Lambda Labs or RunPod A100 for 2 hours (~$2). Fine-tune a 7B model with QLoRA on a tiny instruction dataset (use HF `trl`). Save adapter weights. Don't worry about quality — focus on the pipeline.
- **Output:** `lora-finetune/` repo with reproducible script.

### Day 21 (Tue) — Apply Day + Blog Push
- **Morning:** Skim Anthropic's blog posts on Constitutional AI, Sparse Autoencoders. (For Anthropic interview prep.)
- **Lunch DSA:** LeetCode #647 *Palindromic Substrings*.
- **Evening (CRITICAL):**
  - 60 min: Submit 10 more applications (Tier A + B). Send 10 LinkedIn connection requests with personalized notes referencing recent posts by those ICs.
  - 60 min: Polish and publish Blog Post #3: *"Implementing IBAC for Multi-Agent LangGraph Systems."* Cross-post to LinkedIn, r/LocalLLaMA, Hacker News.
  - 30 min: Track applications in spreadsheet. Note any responses.
- **Output:** Blog #3 LIVE. 10 apps submitted.

**Week 3 self-check:**
- [ ] Can you explain when to use LangGraph vs CrewAI vs Google ADK in 2 minutes?
- [ ] Did your blog post on IBAC get any engagement? (Comments, DMs from recruiters?)
- [ ] Have you had at least one phone screen scheduled?
- [ ] Project 1 demo runs end-to-end?
- [ ] 16 LeetCode mediums done?

---

# WEEK 4 (May 28 – June 5) — Polish, Project Capstone, Mock Interview Sprint

**Theme:** Convert prep into pipeline. By Day 30 you should be in active interview loops. This week is heavy on **mock interviews + portfolio polish + behavioral story crafting + advanced topics**.

**Why this week matters:** Most candidates fail in the final 2 weeks before interviews because they keep "studying" instead of practicing. The flip from passive learning to active simulation happens here.

**End-of-week deliverables:**
- ✅ Project 1 (`agent-iam`) **published with case study**
- ✅ Project 2 (`prod-agent-stack`) MVP working
- ✅ 15 STAR behavioral stories written
- ✅ 6 mock interviews completed (3 coding, 3 system design)
- ✅ 18 LeetCode mediums + 5 hards
- ✅ Blog draft #4 ready
- ✅ **20 total applications submitted (cumulative)**
- ✅ At least 2 phone screens scheduled

### Day 22 (Wed, May 28) — DSPy + Advanced Prompt Patterns
- **Morning:** Read DSPy paper (Khattab et al.) abstract + intro. Skim Constitutional AI (Anthropic) for context.
- **Lunch DSA:** LeetCode #146 *LRU Cache* (must-know for senior — uses LinkedHashMap pattern).
- **Evening:** Implement a DSPy program for a 3-step agent task. Compare prompt-based LangGraph version vs DSPy compiled version on the same eval set.
- **Output:** Add DSPy comparison to `agent-framework-compare/`.

### Day 23 (Thu) — Behavioral Story Catalog
- **Morning:** Re-read Austen McDonald's "How to Nail Big Tech Behavioral Interviews" newsletter. Re-read Amazon's 16 Leadership Principles.
- **Lunch DSA:** LeetCode #295 *Find Median from Data Stream* (heap).
- **Evening (90 min):** Write **15 STAR stories** from your 15 years. Map them to:
  - Ambiguity (×2)
  - Conflict resolution (peer / manager) (×2)
  - Driving alignment cross-functionally (×2)
  - Technical leadership without authority (×2)
  - Hard tradeoffs (×2)
  - Mentoring / scaling others (×1)
  - Project failure & recovery (×2)
  - Ownership / scope expansion (×2)
- **Output:** `stories.md` — 15 STAR stories, ~150 words each.

### Day 24 (Fri) — Mock Interview Day 1 + Project 2 kickoff
- **Lunch DSA:** LeetCode #239 *Sliding Window Maximum*.
- **Evening:**
  - 60 min: Mock interview #1 — DSA on Pramp.
  - 60 min: Start Project 2 (`prod-agent-stack`): combine vLLM + Ray Serve + KServe + LangGraph orchestrator + Phoenix from Weeks 2–3 into ONE reference architecture. README + Helm chart.
- **Output:** Mock #1 done; Project 2 scaffold up.

### Day 25 (Sat — DEEP DAY, 5 hrs) — Project 2 Build + System Design Mock
- **Block 1 (3 hrs):** Project 2 build — get the full stack running on a kind cluster. End-to-end: HTTP request → Ray Serve → vLLM → KServe → response, with a LangGraph agent orchestrator on top using your `agent-iam` IBAC layer.
- **Block 2 (90 min):** Mock interview #2 — system design on Interviewing.io. Topic: "Design an AI agent platform."
- **Block 3 (30 min):** Post-mock review.
- **Output:** Project 2 demoable + Mock #2 feedback.

### Day 26 (Sun — DEEP DAY, 3 hrs) — Project 1 Case Study + Apply Push
- **Block 1 (60 min):** Write a polished case study for Project 1 — frame as a Medium/Hashnode post. 1500 words. Architecture, threat model, IBAC enforcement flow, eval results, what's next.
- **Block 2 (90 min):** **Apply blitz** — 10 more applications (cumulative 25). Refresh LinkedIn outreach: pick 15 new ICs across remaining target companies; personalized notes.
- **Block 3 (30 min):** Behavioral practice — record yourself answering 3 random STAR questions. Listen back. Tighten.
- **Output:** Case study published; 25 applications cumulative.

### Day 27 (Mon, June 1) — DSA Hard Day + Mock #3
- **Morning:** Skim NeetCode patterns video on hard graph problems (Dijkstra, Union-Find).
- **Lunch DSA:** LeetCode #207 + #210 review (already done) → Try #269 *Alien Dictionary* (hard, topo sort).
- **Evening:**
  - 60 min: 2 hard problems — #84 *Largest Rectangle in Histogram*, #42 *Trapping Rain Water*.
  - 60 min: Mock interview #3 — DSA, harder difficulty (Interviewing.io paid).
- **Output:** Mock #3 feedback.

### Day 28 (Tue) — Distributed Training Speedrun + System Design Mock
- **Morning:** Read DeepSpeed ZeRO paper sections 1–3 (memory partitioning). FSDP docs (PyTorch).
- **Lunch DSA:** LeetCode #287 *Find the Duplicate Number* (Floyd's cycle).
- **Evening:**
  - 90 min: Run a tiny distributed training job on 2 GPUs with FSDP (rent for 1 hr). Note the wall-clock vs single-GPU.
  - 60 min: Mock interview #4 — System design, "Design an LLM fine-tuning pipeline."
- **Output:** Distributed training script + Mock #4 feedback.

### Day 29 (Wed) — Anthropic-Specific Prep + Final Behavioral Polish
- **Morning:** Read Anthropic's "Constitutional AI" paper section 1–2. Read 2–3 Anthropic engineering blog posts published in 2026.
- **Lunch DSA:** LeetCode #560 *Subarray Sum Equals K*.
- **Evening:**
  - 60 min: Anthropic-specific behavioral prep — write 3 stories explicitly about safety/judgment/ambiguity (your reva.ai work is GOLD here — frame it as "I built guardrails before the industry had them").
  - 60 min: Mock interview #5 — behavioral with a friend or paid coach.
- **Output:** Anthropic story bank.

### Day 30 (Thu, June 5) — Final Polish + Launch
- **Morning:** Review week. Update `stories.md`, resume, LinkedIn based on all mock feedback received.
- **Lunch DSA:** LeetCode #75 *Sort Colors* (Dutch National Flag).
- **Evening:**
  - 60 min: Mock interview #6 — full loop simulation if possible (Interviewing.io "FAANG mock loop").
  - 60 min: Submit final 10 applications (cumulative 35). Send DMs to recruiters who've engaged with your blog posts.
  - 30 min: Plan Week 5+: continue project polish, add Project 3 (`agentic-rag-bench`), keep DSA at 30 min/day.
- **Output:** 35 cumulative applications. At least 2 onsite loops scheduled. You are now in **execute mode**, not prep mode.

---

# Subject-by-Subject Curriculum (Reference)

This section is the *what* organized by topic. Use it to look up "what should I learn in X" — but the **week-by-week plan above is the prioritized sequence**. If you only have time for 60% of this, do the week plan and skip the optional items below.

## A. Machine Learning (Classical + Deep Learning)

**Must-know (Week 1 covers this):**
- Linear algebra: vectors, matrices, eigenvalues, SVD intuition
- Probability: Bayes' rule, MLE/MAP, common distributions (Gaussian, Bernoulli, Categorical)
- Optimization: gradient descent, SGD, Adam, learning rate scheduling
- Classical ML: linear/logistic regression, decision trees, random forest, gradient boosting (XGBoost), k-means, PCA
- Evaluation: precision/recall/F1, ROC/AUC, train/val/test split, cross-validation, bias-variance
- Neural network basics: forward/backward pass, backprop, activations, regularization (dropout, weight decay, batch norm/layer norm), loss functions
- PyTorch fluency: `nn.Module`, `DataLoader`, `optimizer.step()`, `.to(device)`, mixed precision
- **Transformer architecture (memorize cold):** scaled dot-product attention, multi-head, FFN, residual + LayerNorm, positional encoding (sinusoidal vs RoPE vs ALiBi), causal mask
- Tokenization: BPE, WordPiece, SentencePiece — tradeoffs, vocab size, OOV handling

**Should-know (Week 3–4 dips into):**
- Mixture-of-Experts: routing, load balancing loss (DeepSeek-V3, Mixtral)
- Long-context strategies: sliding window, NTK-aware RoPE scaling, ring attention
- Reasoning models: o1-style RL post-training intuition, R1-style cold-start
- Speculative decoding, Medusa-style heads
- KV cache mechanics, paged attention, FlashAttention 1/2/3
- Quantization: INT8, INT4, FP8, AWQ, GPTQ, GGUF — when to use each
- LoRA / QLoRA / DoRA — what's frozen, where adapters insert, rank tradeoffs
- RLHF pipeline: SFT → reward model → PPO; DPO as a simpler alternative
- Evaluation for LLMs: perplexity, MMLU/HellaSwag/HumanEval, faithfulness, hallucination, toxicity, LLM-as-judge

**Optional (only if time / target deep ML role):**
- JAX basics (only if Google DeepMind track)
- Diffusion models / Stable Diffusion (only if multimodal target)
- Multimodal: CLIP, LLaVA, vision encoders

**Resources:**
- Stanford CS229 (classical ML), CS231n (vision), CS224n (NLP), CS336 (LLMs from scratch)
- Andrej Karpathy "Neural Networks: Zero to Hero" (free YouTube)
- Sebastian Raschka *Build an LLM from Scratch* (book)
- Lilian Weng's blog (`lilianweng.github.io`) — best long-form ML writing on the internet
- Hugging Face NLP Course, Agents Course (free)

## B. AI / Agentic AI

**Must-know:**
- RAG architecture: chunking strategies (fixed, semantic, hierarchical, agentic), embedding models, ANN indexes (HNSW, IVF-PQ), hybrid retrieval (BM25 + dense + reranker, e.g., Cohere/BGE), context construction
- Vector databases — production tradeoffs:
  - Pinecone (managed, simple), Weaviate (open, hybrid built-in), Milvus/Zilliz (scale), Qdrant (Rust, fast, payloads), Chroma (dev), pgvector (when you already have Postgres)
- Agent design patterns: ReAct, Plan-and-Execute, Reflexion, Tree-of-Thoughts, multi-agent collaboration (hierarchical / conversational / graph-based)
- Agent frameworks (you should be able to choose between):
  - **LangGraph** — graph-based, stateful, best for complex flows (your home base)
  - **CrewAI** — role-based, simpler, fast prototyping
  - **Google ADK / Agent Builder** — production agents on Vertex AI; A2A native
  - **OpenAI Agents SDK** — recently launched, simpler than LangGraph
  - **Microsoft Agent Framework** — successor to AutoGen (which is now in maintenance mode)
  - **Pydantic-AI** — type-safe, lightweight
- Memory: short-term (within-context), long-term (vector store), episodic, semantic
- Tool use: function calling, MCP (Anthropic), A2A (Google), Toolhouse, OpenAPI
- Evaluation:
  - Component-level (retrieval recall, reranker precision)
  - End-to-end (golden datasets, LLM-as-judge, human review)
  - Production (Phoenix, LangSmith traces, A/B tests)
- Safety: prompt injection, jailbreaks, tool sandboxing, data exfiltration defenses, **IBAC/PBAC for multi-agent (your moat)**

**Should-know:**
- Agentic RAG taxonomy (Singh et al. survey arXiv:2501.09136): single-agent, multi-agent, hierarchical, corrective, adaptive
- DSPy (programming, not prompting)
- Constitutional AI (Anthropic) — RLAIF
- Agent observability stack: Phoenix, LangSmith, Helicone, Langfuse, OpenInference standard
- Cost-control patterns: prompt caching (Anthropic), semantic caching (GPTCache), model routing/fallback

**Resources:**
- LangChain Academy (free) — *especially* the LangGraph course
- DeepLearning.AI short courses (free): LangGraph, AutoGen, MCP, Multi-AI Agent
- Hugging Face Agents Course + MCP Course (free)
- Anthropic MCP docs (`modelcontextprotocol.io`)
- arXiv survey papers: 2501.09136 (Agentic RAG), 2505.10468 (AI Agents vs Agentic AI)

## C. System Design (Generic + ML/GenAI)

**Generic system design (must-know — Alex Xu Vol 1):**
- Scaling: vertical vs horizontal, stateful vs stateless
- Caching: Redis/Memcached, cache invalidation, TTL, write-through/write-back
- Load balancing: L4 vs L7, round-robin/least-conn/consistent-hashing
- Databases: SQL vs NoSQL choices, replication, sharding, CAP theorem, isolation levels
- Message queues: Kafka, SQS, NATS — when to use which
- Pub/sub vs point-to-point
- Microservices vs monolith tradeoffs
- API design: REST vs gRPC, idempotency, rate limiting, pagination
- Observability: metrics (Prometheus), logs (ELK/Loki), traces (OpenTelemetry, Jaeger)
- Reliability: retries (with backoff/jitter), circuit breakers, bulkheads, timeouts

**ML system design (Aminian/Sheng Vol 1):**
- 6-step framework: clarify → metrics → architecture → data → model → eval/iteration
- Recommender systems (YouTube/Spotify pattern): candidate generation → ranking → re-ranking
- Search ranking, ad ranking
- Feature stores (Feast, Tecton)
- Online vs offline training, training-serving skew
- A/B testing infrastructure
- Model monitoring: data drift, prediction drift, ground truth latency

**GenAI system design (Aminian/Sheng Vol 2 — your priority book):**
- 7-step framework: requirements → high-level → data prep → model selection → training/fine-tuning → eval → deployment
- Designs to memorize:
  - **ChatGPT / personal LLM assistant with memory**
  - **RAG over enterprise documents** (10K to 1B docs)
  - **Vector search at scale**
  - **AI agent platform** (multi-tenant, with eval/observability)
  - **Smart Reply / Gmail Compose**
  - **Image generation pipeline**
  - **Code completion** (Copilot pattern)
  - **LLM fine-tuning pipeline** (data → train → register → deploy)
  - **Multi-LoRA serving** (50 adapters on 1 GPU with vLLM)
  - **Real-time content moderation with LLMs**
- Capacity / cost back-of-envelope: tokens/sec/GPU, $/M tokens, KV cache memory math, LoRA adapter sizing

**Resources:**
- **Aminian/Sheng — *Generative AI System Design Interview*** (your priority)
- Aminian/Sheng — *ML System Design Interview*
- Alex Xu — *System Design Interview Vol 1 & 2*
- Eugene Yan's blog (`eugeneyan.com`) — case studies from real systems
- ByteByteGo newsletter
- Backprop / IGotAnOffer ML system design guides
- TheSystemDesignHandbook.com generative AI guide

## D. DSA / Coding

**Must-know patterns (and one canonical problem per pattern):**
- Two pointers — *3Sum* (#15)
- Sliding window — *Longest Substring Without Repeating Characters* (#3), *Minimum Window Substring* (#76)
- Hashmap / set — *Two Sum* (#1), *Group Anagrams* (#49)
- Stack — *Valid Parentheses* (#20), *Largest Rectangle in Histogram* (#84)
- Heap / priority queue — *Top K Frequent Elements* (#347), *Find Median from Data Stream* (#295)
- Linked list — *Reverse Linked List* (#206), *LRU Cache* (#146)
- Tree DFS/BFS — *Binary Tree Level Order Traversal* (#102), *LCA* (#236)
- Binary search — *Search Rotated Sorted Array* (#33), *Median of Two Sorted Arrays* (#4)
- Backtracking — *Word Search* (#79), *N-Queens* (#51)
- Graph BFS/DFS — *Number of Islands* (#200), *Course Schedule* (#207)
- Topological sort — *Course Schedule II* (#210), *Alien Dictionary* (#269)
- Union-find — *Number of Connected Components* (#323)
- DP (1D) — *House Robber* (#198), *Climbing Stairs* (#70)
- DP (2D) — *Longest Common Subsequence* (#1143), *Edit Distance* (#72)
- DP (intervals/knapsack) — *Coin Change* (#322), *Partition Equal Subset Sum* (#416)
- Trie — *Implement Trie* (#208), *Word Search II* (#212)
- Greedy — *Jump Game* (#55), *Gas Station* (#134)

**Volume target for 30 days:** 70 mediums + 10 hards. This roadmap schedules ~75. Prioritize **patterns over count** — solving the same pattern 5 ways beats solving 5 unrelated problems.

**Resources:**
- NeetCode 150 (free) — best curated list
- Blind 75 (subset of NeetCode 150)
- LeetCode Premium — company-tagged questions (filter by Google/Amazon/Meta past-6-months)
- AlgoMonster — pattern-based explanations
- *Cracking the Coding Interview* / *Elements of Programming Interviews*

## E. Behavioral / Interview Soft Skills

**Must-prep:**
- 15 STAR stories covering: ambiguity, conflict, alignment, technical leadership without authority, hard tradeoffs, mentoring, failure, ownership
- Amazon's 16 Leadership Principles (memorize names + 1-line summary)
- Anthropic values (safety, beneficial AI, mission-driven) — your reva.ai work is gold; tell that story
- Google's "Googleyness" — comfort with ambiguity, collaboration, learning mindset
- Microsoft's growth mindset
- Meta's "move fast" — but at senior levels, frame it as *"move thoughtfully fast"*

**Story structure (modified STAR for senior roles):**
- **S**ituation (1 sentence — context)
- **T**ask (1 sentence — what you owned)
- **A**ction (3–4 sentences — *what you did and why*; emphasize judgment calls and tradeoffs)
- **R**esult (1–2 sentences — quantified outcome)
- **L**earning (1 sentence — what would you do differently / what playbook did you build) — *this is where senior candidates shine*

**Resources:**
- Austen McDonald (Eng Leadership newsletter) — *"How to Nail Big Tech Behavioral Interviews"*
- *Cracking the PM Interview* behavioral chapter (overlaps with senior eng)
- IGotAnOffer behavioral guides (company-specific)

---

## Daily Habits (non-negotiable)

| Habit | Time | Purpose |
|---|---|---|
| 1 LeetCode problem | 25 min | Pattern fluency |
| Read 1 ML paper section OR 1 book chapter | 30 min | Theory depth |
| Hands-on coding | 90–120 min | Skill internalization |
| Track applications + recruiter responses | 5 min | Pipeline visibility |
| Update `stories.md` if anything happens at work | 5 min | Behavioral inventory builds passively |

---

## Weekly Self-Assessment Template

End each Sunday, ask:
1. What did I ship this week (project, blog, applications)?
2. What 3 concepts can I explain on a whiteboard from memory now that I couldn't last Sunday?
3. Did I do at least 1 mock interview? What was my biggest gap?
4. How many applications, and how many real responses?
5. What's the one thing I'm avoiding? (Answer: do that first next week.)

---

## What to Do Beyond Day 30

By Day 30 you should be in **active interview pipelines**, not still prepping. From Day 31:
- Maintain DSA at 30 min/day (one problem)
- Maintain 1 system design rep per week (Sunday)
- Continue blog cadence (1 post/2 weeks)
- Add Project 3 (`agentic-rag-bench`) to portfolio
- Start a 10-page deep-dive on one open-source project — submit a non-trivial PR (highest leverage activity for FAANG callbacks)
- Reach out to 3 new ICs/week
- Bunch all final-round loops into a 2–3 week window for offer negotiation

---

## Honest Caveats

- **20 hrs/week is aggressive** alongside a senior IC role at reva.ai. If your work pushes 50+ hrs in a given week, *protect the daily LeetCode + 30-min reading habit* and let the project work slip — patterns and theory compound; project days can be made up on weekends.
- **You will not master everything in this list.** That's fine. The goal is to be *interviewable*, not encyclopedic. A strong candidate with 70% coverage and great storytelling beats a 100% candidate with weak narrative every time.
- **Mock interview ROI > self-study ROI in Week 4.** Don't skip mocks to "study more." The fastest way to improve is to fail in a low-stakes setting and iterate.
- **Comp ranges, hiring patterns, and the specific companies' hiring posture can shift in 30 days** — check Levels.fyi, Blind, and Anthropic/Google careers pages weekly.
- **Your moat is the cybersecurity-for-agents work**, not generic AI knowledge. When in doubt about what to emphasize in interviews and content, return to that thread. Most candidates can rebuild a RAG pipeline; very few can speak fluently about IBAC/PBAC for multi-agent systems.

You've got this. The plan is realistic, the gap is closeable, and the timing — with FAANG India hiring expanding and Anthropic Bengaluru just opening — is genuinely favorable. See you on the other side.
