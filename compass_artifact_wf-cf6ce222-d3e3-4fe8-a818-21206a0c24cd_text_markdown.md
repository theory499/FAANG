# Career Transition Roadmap: From Platform Engineer at reva.ai to AI Platform / AI Agent Engineer at FAANG & Top AI Companies (Bangalore, April 2026)

## TL;DR
- **Best fit, fastest path:** Target **AI Platform / Agentic AI Engineer** roles at the Bangalore offices of Anthropic, Google Cloud (Vertex AI / Agent Builder), Microsoft (Azure AI / Copilot / CoreAI), AWS India (Bedrock Agents) and NVIDIA — your existing LangGraph + Bedrock + Kubernetes + cybersecurity-for-agents profile is unusually well-aligned with what these teams need; the gaps are mostly in production MLOps depth (vLLM/Ray/KServe), one canonical ML framework (PyTorch), and FAANG-style system design fluency, not in domain knowledge.
- **Realistic compensation in Bangalore (15 YOE, senior IC, 2026):** ₹70 LPA–₹1.2 Cr+ total comp at FAANG GCCs (base ₹45–70 LPA + RSUs + bonus), ₹60–120 LPA at NVIDIA / Databricks / Anthropic / well-funded AI startups, ₹35–80 LPA at Sarvam/Krutrim/Flipkart/Razorpay/CRED. Senior LLM/agent specialists routinely cross ₹70 LPA per Scaler/NASSCOM/Levels.fyi 2026 data.
- **3–6 month plan (high level):** (1) Reposition as "AI Platform Engineer" not "Platform Engineer doing AI"; (2) close the MLOps/serving gap (vLLM, Ray, KServe, Kubeflow, GPU scheduling) and add PyTorch fluency; (3) ship 2–3 portfolio-grade agentic projects and one open-source contribution; (4) drill 100–150 LeetCode mediums + 30 ML/Generative-AI system design reps using the Aminian/Sheng books; (5) run a deliberate referral campaign across 40–60 target ICs at FAANG/Anthropic/NVIDIA; expect first interviews within 6–8 weeks of launching outreach.

---

## Executive Summary — Recommended Path

You are in a structurally **strong** position for this transition, despite your current title underselling the role. Three facts dominate the strategy:

1. **The market is loud about agents.** LinkedIn India job postings requiring LangChain/CrewAI/"AI agent" skills grew >300% between Jan 2025 and Mar 2026 (NASSCOM/Cambridge Infotech tracking). Anthropic opened its Bengaluru office in early 2026 and is actively hiring Applied AI Architects/Engineers there. Google Cloud is hiring Forward Deployed Engineers (GenAI) and Software Engineers for "BigQuery GenAI Query Engine, AI Operators" in Bangalore that explicitly list **LangGraph, CrewAI, Google ADK, ReAct, RAG** as preferred. Microsoft Research India and Microsoft's CoreAI/Experimentation Platform teams are hiring in Bangalore. NVIDIA Bangalore had ~73 open roles on Glassdoor as of April 2026.
2. **Your current work is unusually defensible.** Cybersecurity for AI agents (IBAC/PBAC for multi-agent systems) is a *niche* that maps directly to Anthropic's safety mission, AWS Bedrock Guardrails work, Microsoft's CoreAI safety/governance teams, and is becoming a regulated requirement (NIST AI RMF, EU AI Act). Frame it as your differentiator, not a footnote.
3. **The "Platform Engineer" label is hurting you.** ATS systems and recruiter scans index on titles. You need to rebrand the same work as **"AI Platform Engineer / Agent Platform Engineer"** in your LinkedIn/resume — which is *truthful* given you build agentic systems on Bedrock with LangGraph today.

**Recommended ordered targets (priority):**

| Tier | Companies (Bangalore) | Why |
|---|---|---|
| **A — apply immediately** | Anthropic Bengaluru (Applied AI Architect, Applied AI Engineer – Beneficial Deployments), Google Cloud (Applied AI / Vertex AI / Forward Deployed GenAI), Microsoft (CoreAI, Microsoft Research India AI/Systems, Copilot agent teams), NVIDIA (NeMo / Inference / DGX Cloud teams), AWS India (Bedrock / Agents for Bedrock) | Direct fit, hiring NOW, your stack maps 1:1, highest comp band |
| **B — strong fit, parallel** | Databricks India (Mosaic AI / Agent Bricks / Vector Search), Snowflake India (Cortex), Meta India (GenAI Infra), Apple India (on-device ML platform) | Excellent platform-engineering depth; Databricks especially values your Kubernetes + serving experience |
| **C — Indian AI leaders, optionality** | Sarvam AI (Forward Deployed Engineer / SRE / ML Eng – Speech), Krutrim (Ola), Flipkart (ML Platform), Razorpay (AI/Risk), CRED, Swiggy Hermes (agents), Uniphore, Yellow.ai, Gnani.ai | Faster offer cycles, lower bar than FAANG, often better mission fit if you want to ship fast; can be a leverage offer for FAANG negotiation |
| **D — strategic fallback** | JPMC / Goldman Sachs / Walmart Global Tech / Target India / ServiceNow / Salesforce India (Agentforce) GCCs | GCC stability premium; Storyboard18 reports GCCs pay 12–30% above IT services and have 3–5 percentage points lower attrition than IT services |

You are explicitly **not** targeting research scientist roles (PhD-gated) or engineering management — both are correct calls given your goals (technical IC, stability).

---

## 1. Active Job Openings to Pursue Right Now (April–May 2026)

These are roles confirmed open at time of writing — apply within the next 2 weeks while you simultaneously prep:

**Anthropic — Bengaluru (anthropic.com/careers):**
- Applied AI Architect, Bangalore, India
- Applied AI Engineer, Beneficial Deployments, Bangalore, India
- (Solutions Architect, Applied AI — Bangalore; previously listed)

**Google — Bengaluru (google.com/about/careers/applications):**
- Software Engineer II, Applied AI Engineer (Cloud Applied AI / Gemini Enterprise / Agent Studio)
- Software Engineer, BigQuery GenAI Query Engine, AI Operators
- Forward Deployed Engineer, Generative AI, Google Cloud (lists LangGraph/CrewAI/ADK + ReAct as desired)
- Systems Development Engineer, AI Infrastructure
- Conversational AI Engineer

**Microsoft — Bengaluru (careers.microsoft.com & microsoft.com/en-us/research/careers):**
- Research Engineer, Microsoft Research India (AI/ML, scalable ML architectures, systems support)
- Multiple Software Engineer / Senior SWE roles on CoreAI Experimentation Platform and Teams Proactive Agents (some require Hyderabad/Bangalore split)
- Copilot Studio enterprise agent development team (Bangalore)

**NVIDIA — Bangalore (nvidia.wd5.myworkdayjobs.com):**
- Senior Software Engineer roles on NeMo, Triton Inference Server, DGX Cloud, AI Enterprise — search "Bangalore" + "AI" / "inference" / "agent". 73 open roles in Bangalore on Glassdoor.

**AWS India — Bangalore:**
- Software Engineer / Sr SDE, Amazon Bedrock Agents, AgentCore (your current Bedrock experience is the perfect setup story)

**Databricks India — Bangalore:**
- Software Engineer, Mosaic AI / Agent Bricks / Vector Search (databricks.com/company/careers/open-positions)

**Sarvam AI — Bangalore (careers.kula.ai/sarvam-ai):**
- Forward Deployed Engineer (RAG and ML specialist)
- Site Reliability Engineer, Application Specialisation
- ML Engineer – Speech AI

**Other actively hiring (April 2026):** Salesforce India (Agentforce), ServiceNow India (Now Assist), Adobe Bangalore (Firefly platform), Atlassian Bangalore (Rovo agents), Walmart Global Tech (agent platform), Target India.

> Note: hyperlinks are not included per output formatting requirements; navigate the company careers portals listed and filter Location = Bangalore/Bengaluru. Check weekly — FAANG postings rotate fast and many close within 2–3 weeks of opening.

---

## 2. Salary Expectations (Bangalore, ~15 YOE, Senior IC, 2026)

Triangulated from Levels.fyi (April 2026), Glassdoor India (Feb–Apr 2026), Scaler/NASSCOM 2026 reports, Taggd, ShifttoTech, and product-based.in:

| Tier | Base | RSU/yr (vested) | Bonus | **Total Comp (CTC equivalent)** |
|---|---|---|---|---|
| Google L5 / Microsoft 64 / Amazon SDE III (AI Platform) | ₹45–65 LPA | ₹20–40 LPA | ₹8–15 LPA | **₹70 LPA – ₹1.2 Cr** |
| Google L6 / Microsoft 65 / Amazon Principal (rare at 15 YOE entry) | ₹60–85 LPA | ₹35–70 LPA | ₹10–20 LPA | **₹1.0–2.0 Cr** |
| Anthropic Bengaluru (Applied AI Architect/Eng) | ~₹50–75 LPA | Heavy equity (private, $183B valuation) | — | **₹90 LPA – ₹1.8 Cr+ effective** |
| NVIDIA Senior / Principal | ₹50–70 LPA | ₹25–50 LPA (RSUs have appreciated heavily) | ₹8–15 LPA | **₹85 LPA – ₹1.5 Cr** |
| Databricks / Snowflake India Senior | ₹50–70 LPA | Pre-IPO/post-IPO equity | ₹8–12 LPA | **₹80 LPA – ₹1.4 Cr** |
| Sarvam / Krutrim / Flipkart / Razorpay / CRED Principal/Architect | ₹40–70 LPA | ESOPs (variable) | ₹5–12 LPA | **₹50 LPA – ₹1.0 Cr** |
| GCCs (JPMC / GS / Walmart Tech / Target / ServiceNow) | ₹35–55 LPA | Modest RSUs | ₹6–12 LPA | **₹45 LPA – ₹85 LPA** |

**Key 2026 data points to anchor negotiations:**
- Levels.fyi (Mar 2026): Senior SWE in Bengaluru averages ₹37–79 LPA total; "Crack FAANG" India SWE median ₹55.7 LPA, top ₹80.9 LPA.
- Scaler/NASSCOM: GenAI specialists carry a 25–40% premium over generalist ML engineers; senior LLM engineers at product companies clear ₹35–60 LPA, top specialists exceed ₹70 LPA.
- Taggd 2026: Senior LLM/agent engineers at top product companies hit ₹70+ LPA; remote roles for US firms from Bengaluru reach ₹60–80 LPA equivalent.
- Glassdoor (April 2026): "Senior Platform Engineer" Bangalore base median ₹15.75 LPA, 90th pct ₹34.35 LPA — but this label *underprices* you; rebranding to AI/ML platform pulls you into the ₹40–60 LPA base band.

**Negotiation lever:** GCC layoff data (Storyboard18, BW People — ~6,000 GCC roles trimmed in 2025 even as 100K+ added) means recruiters know talent is mobile. Always get **two competing offers** before signing.

---

## 3. Skill Gap Analysis & Prioritized Learning Order

Your **current strengths** (assets to lead with): cloud architecture, K8s, application framework decisions, LangGraph agent building, Amazon Bedrock LLM integration, agent-security/IBAC/PBAC for multi-agent systems, data collection for ML.

**Gap analysis vs FAANG-level AI Platform Engineer (2026 JDs):**

| Skill area | Your level | FAANG bar | Priority |
|---|---|---|---|
| **Python (production-grade, async, typing, pydantic)** | Strong (assumed) | Expert | Verify, sharpen |
| **PyTorch fluency** (model loading, fine-tuning, custom training loops) | Likely shallow | Required | **P0** |
| **TensorFlow / JAX** | Optional | Nice-to-have for Google teams (JAX) | P2 |
| **LLM serving stack** — vLLM, TGI, TensorRT-LLM, Triton, BentoML | Gap | Required for AI Platform | **P0** |
| **Distributed training/inference** — Ray, Ray Serve, DeepSpeed, FSDP, Horovod | Gap | Expected | **P1** |
| **MLOps platform** — Kubeflow, KServe, MLflow, Vertex AI Pipelines, SageMaker, W&B | Partial (K8s) | Required | **P0** |
| **GPU/TPU infra** — CUDA basics, MIG, NVLink, GPU operator, topology-aware scheduling | Gap | Required at NVIDIA, Google, Meta | **P1** |
| **Vector DBs** — Pinecone, Weaviate, Milvus/Zilliz, Qdrant, Chroma, pgvector | Likely surface | Production depth (HNSW, hybrid search, filtering) | **P1** |
| **RAG architecture** — chunking, hybrid search (BM25+vector), reranking, agentic RAG | Partial via LangGraph | Required | **P1** |
| **Agent frameworks beyond LangGraph** — CrewAI, AutoGen (maintenance mode 2026), OpenAI Agents SDK, Google ADK, Microsoft Agent Framework, OpenAgents | LangGraph only | Two-framework fluency expected | **P1** |
| **MCP / A2A protocols** | Likely new | Hot topic 2026 (Google ADK A2A native, OpenAgents) | **P1** |
| **LLM fine-tuning** — LoRA/QLoRA/PEFT, RLHF, DPO | Gap | Differentiator (most Applied AI roles want it) | **P2** |
| **Eval/observability** — Arize Phoenix, LangSmith, evals/golden datasets, LLM-as-judge | Gap | Required (Anthropic, Microsoft especially) | **P0** |
| **AI safety/security** — prompt injection, guardrails, IBAC/PBAC | **Strong** (your differentiator) | Bonus — most candidates lack this | Lead with it |
| **System design at scale** — back-of-envelope, capacity planning, multi-region | Solid (15 YOE) | Required | Sharpen with ML-specific framing |
| **DSA / coding** | Rusty (assumed for 15 YOE platform eng) | LeetCode medium fluency required at all FAANG | **P0** |

**Priority learning sequence (P0 → P1 → P2):**

**P0 (weeks 1–6, must close before applying broadly):**
1. **PyTorch** — Stanford CS231n + Sebastian Raschka's "Build an LLM from Scratch" book; build a small transformer from scratch (1 weekend project).
2. **vLLM + Ray Serve + KServe on K8s** — work through the premai.io "Deploying LLMs on Kubernetes 2026" guide and Google Cloud's "Build a ML platform with Kubeflow and Ray on GKE" tutorial. Deploy a Llama 3 8B with vLLM + RayServe + autoscaling on your local kind cluster, then on GKE/EKS.
3. **MLflow + W&B** — instrument one project end-to-end with experiment tracking and model registry.
4. **Eval / observability** — wire Arize Phoenix or LangSmith into your existing LangGraph agents at reva.ai (or a side project); build a golden-dataset eval with LLM-as-judge.
5. **DSA brush-up** — 100 LeetCode mediums (NeetCode 150 list) + 25 hards focused on graphs/DP/heap.

**P1 (weeks 5–10, parallel with P0 tail):**
6. **Vector DB depth** — production deployment with Milvus or Qdrant; hybrid (BM25 + dense) retrieval; HNSW parameter tuning.
7. **Agentic RAG** — read Singh et al. arXiv:2501.09136 ("Agentic RAG survey") and arXiv:2506.10408 (Reasoning Agentic RAG); build one project that demonstrates predefined-vs-agentic reasoning RAG.
8. **CrewAI + Google ADK + OpenAI Agents SDK** — one weekend project per framework; understand A2A and MCP (Anthropic's MCP, Google's A2A).
9. **GPU fundamentals** — NVIDIA DLI's "Fundamentals of Deep Learning" + "Building LLM Applications with Prompt Engineering"; understand MIG, NVLink, FlashAttention, KV cache, quantization (GPTQ, AWQ, FP8).
10. **Distributed training** — DeepSpeed ZeRO + FSDP, Ray Train; fine-tune a 7B model with LoRA on a single A100 (rented).

**P2 (weeks 9–14, polish):**
11. **JAX** — only if targeting Google DeepMind / Google Brain heavy roles.
12. **TensorRT-LLM** — only if targeting NVIDIA inference team.
13. **RLHF / DPO** — read InstructGPT + DPO papers; optional unless targeting Anthropic/OpenAI research-adjacent roles.

---

## 4. Detailed 14-Week Preparation Roadmap (Weekly Milestones)

Calibrated for ~15–20 hrs/week alongside your full-time role at reva.ai.

**Phase 1 — Foundation reset (weeks 1–4)**

| Wk | Learning | Coding | Portfolio | Outreach |
|---|---|---|---|---|
| 1 | PyTorch basics (autograd, nn.Module); LeetCode arrays/strings (15 problems) | NeetCode roadmap start | Audit & rebrand LinkedIn → "AI Platform Engineer" | Identify 50 target ICs at FAANG/Anthropic/NVIDIA Bangalore |
| 2 | Build mini-transformer; trees/graphs DSA (15 problems) | Cont. | Resume rewrite v1 (see §6) | Connect (no pitch) with 20 ICs |
| 3 | vLLM local deploy + KServe basics; DP DSA (10 problems) | Cont. | Start **Project 1: Multi-agent platform with IBAC** (uses LangGraph + your security expertise) | Engage on LinkedIn posts of target ICs |
| 4 | Ray Serve + KubeRay; review LeetCode top 75 | Mock #1 (Pramp/Interviewing.io) | Project 1 MVP | Begin asking warm contacts for FAANG referrals |

**Phase 2 — Depth + System Design (weeks 5–8)**

| Wk | Learning | Coding | Portfolio | Outreach |
|---|---|---|---|---|
| 5 | Read Aminian/Sheng *Generative AI System Design Interview* ch 1–4 | LeetCode mediums (heap/sliding window) | Project 1 polish + README + blog post | Submit 3–5 cold applications (highest-fit roles) |
| 6 | Aminian/Sheng ch 5–7 (RAG, ChatGPT, Image gen) | System design reps: design a vector search service, design an agent platform | **Project 2: Production agent serving stack** — vLLM + Ray Serve + Phoenix + LangGraph agent orchestrator on K8s | Cold-DM 10 ICs/week with specific value prop |
| 7 | Chip Huyen *Designing Machine Learning Systems* (focus ch 7–10 platform/MLOps) + her 2025 *AI Engineering* book | 3 ML system design mocks (try Exponent, IGotAnOffer) | Project 2 progress | Engage Anthropic recruiters specifically |
| 8 | NVIDIA DLI cert (LLM Apps with Prompt Eng) + Vertex AI Agent Builder hands-on | Mock interview FAANG-style coding | **Project 3: Open-source contribution** — pick a LangGraph/Ray Serve/KServe issue, ship PR | Apply Tier-A roles (Anthropic, Google, NVIDIA, Microsoft, AWS) |

**Phase 3 — Specialization + Interview Drills (weeks 9–12)**

| Wk | Learning | Coding | Portfolio | Outreach/Interview |
|---|---|---|---|---|
| 9 | LoRA/QLoRA fine-tuning one 7B model on rented A100; CrewAI + Google ADK comparison project | LeetCode hards (15) | Project 2 published with benchmarks (latency, cost, KV cache util) | Phone screens begin (expected) |
| 10 | Agentic RAG papers; build hybrid retrieval (BM25 + Qdrant + Cohere reranker) | Behavioral STAR stories drafted (15 stories covering Meta's signal areas + Amazon LPs) | Project 1 case study | First onsite loops |
| 11 | Read recent 2025–26 papers: Anthropic Constitutional AI, Sparse Mixture-of-Experts (DeepSeek-V3, Mixtral), DSPy, Reasoning RAG | 5 system design mocks | Tech blog post on agent security IBAC/PBAC (your differentiator) | Continue interviews; negotiate timing to bunch offers |
| 12 | Polish weak areas based on interview feedback | Mock interviews 3×/wk | Project 4 (optional): Research replication of a recent agent paper | Convert offers, negotiate |

**Phase 4 — Buffer + Negotiation (weeks 13–14)**

| Wk | Focus |
|---|---|
| 13 | Final-round prep, leadership/behavioral, comp benchmarking via Levels.fyi + Blind |
| 14 | Negotiate; align start dates; transition planning at reva.ai |

**If your timeline must be 3 months instead of 4**: drop P2 items (JAX, TensorRT-LLM, RLHF), drop Project 4, compress Phase 1 from 4 to 3 weeks.

---

## 5. Interview Preparation Plan

FAANG and top AI companies typically run 4–6 round loops for senior IC AI roles: recruiter screen → coding (1–2) → ML/Generative-AI system design (1–2) → behavioral/values → hiring manager / bar raiser.

### 5a. Coding (DSA)
- **Bar:** LeetCode medium fluency, must solve 1–2 mediums in 35–45 min with optimal complexity articulated. Hards possible at L6/Staff+ levels.
- **Topics with highest yield:** Arrays/two-pointer, hashmap, graphs (BFS/DFS, topological sort), heap/priority queue, sliding window, dynamic programming (knapsack/intervals), tries.
- **Plan:** NeetCode 150 → Blind 75 → Grind 169. Do 100–150 problems total; quality > quantity.
- **Tools:** LeetCode, NeetCode.io, AlgoMonster patterns.
- **Mock platforms:** Interviewing.io (best for senior, pricey but worth it), Pramp (free peer), Exponent (paid, ML-specific coaches), Apex Interviewer (company-specific rubrics — covers all 13 FAANG+).

### 5b. ML / Generative AI System Design (highest weight for you)

This is where you win or lose given your background. Two canonical books:
1. **Aminian & Sheng — *Machine Learning System Design Interview*** (ByteByteGo, traditional ML topics).
2. **Aminian & Sheng — *Generative AI System Design Interview*** (ByteByteGo, 2024) — 7-step framework, 10 questions including Gmail Smart Compose, ChatGPT Personal Assistant, RAG, image/video gen. **This is the must-read for 2026.**

Practice these prompts with the 7-step framework (clarifying questions → high-level architecture → deep-dive on retrieval/serving → cost/latency → safety/governance → observability → failure modes):

- Design ChatGPT / a personal LLM assistant with memory
- Design a vector search service at 10B vectors
- Design an enterprise RAG system over 100M documents
- Design an AI agent platform (multi-tenant, with tool use, memory, eval)
- Design a model serving infrastructure for 50 concurrent fine-tuned LoRA adapters on one GPU (vLLM multi-LoRA)
- Design a recommendation system (Spotify/YouTube — classic)
- Design a real-time content moderation system with LLMs
- Design an LLM fine-tuning pipeline (data → train → eval → deploy)
- Design an agentic coding assistant (Cursor/Claude Code competitor)
- Design an evaluation framework for non-deterministic LLM outputs

Supplement with: Backprop's "FAANG Interview – Machine Learning System Design" guide, Exponent's MLE course, IGotAnOffer ML system design guide, ByteByteGo blog & newsletter, the systemdesignhandbook.com generative AI guide.

### 5c. AI Agent / Agentic AI Specific
Agentic-AI interviews now exist as their own track. Drill the ATUL4U / Medium "Complete Agentic AI System Design Interview Guide 2026" question bank (40 questions across 8 domains: agent definition, design, orchestration, memory, tools, evaluation, safety, deployment). Key topics:
- When to use an agent vs deterministic workflow (you should *underuse* agents — most "agent" problems are actually workflows).
- How to version an agent system (prompts + tools + policies + model version pinned together).
- Multi-agent coordination patterns (hierarchical, conversational, graph-based).
- Eval strategy: golden datasets + LLM-as-judge + human review + production traces.
- Prompt injection defense, tool sandboxing, IBAC/PBAC ← **lead with your reva.ai expertise here**.

### 5d. LLM-Specific Knowledge Interview Questions (2026)
Prep the InterviewBit, Simplilearn, DataCamp, GeeksforGeeks, ProjectPro 2026 LLM/Agentic AI question banks plus Outcome School's GitHub `amitshekhariitbhu/ai-engineering-interview-questions`. Must-know:
- Transformer architecture (Q/K/V, multi-head attention, positional encodings, RoPE, layer norm, residuals)
- Tokenization (BPE, WordPiece, SentencePiece)
- KV cache, paged attention, FlashAttention, speculative decoding
- Sampling (top-k, top-p, temperature, beam, contrastive)
- LoRA/QLoRA/PEFT, RLHF, DPO, instruction tuning
- RAG components, chunking strategies, hybrid retrieval, reranking
- MCP and A2A protocols (very 2026)
- LLM evaluation: faithfulness, groundedness, toxicity, hallucination metrics
- "Lost in the middle" problem, long-context strategies (RAG vs long context vs caching)

### 5e. Behavioral (15 YOE — this is heavily weighted)

At Staff/Principal levels, the behavioral round is *the* leveling round. Per Austen McDonald (ex-Meta hiring committee chair, eng-leadership.com):
- Build a **Story Catalog** of ~15 stories before any interview.
- Choose stories by **scope** (breadth × timescale × autonomy × business impact), not exact match to the question.
- Cover signal areas: ambiguity, conflict resolution (peer / manager / cross-functional), driving alignment, technical leadership without authority, hard tradeoffs, mentoring, project failure & recovery, scope expansion.
- Use STAR but emphasize *learning* and *systems-level thinking* (what would you do differently, what playbook did you build).
- Map to company values: Amazon Leadership Principles (memorize all 16, especially Ownership, Bias for Action, Earn Trust, Are Right A Lot, Deliver Results, Dive Deep), Google's Googleyness, Microsoft's growth mindset, Meta's "move fast", Anthropic's safety-mission alignment.

For Anthropic specifically, prepare strong answers around: why safety/beneficial AI matters to you (your reva.ai cybersecurity-for-agents background is gold here), specific Claude/Anthropic research you find compelling, comfortable with uncertainty/ambiguity.

### 5f. Mock Interview Platforms (ranked for senior IC AI roles)
1. **Interviewing.io** — anonymous mocks with FAANG engineers; AI/ML track exists; ~$225/session but highest signal.
2. **Exponent** — structured ML engineer course + ML system design coaches.
3. **Apex Interviewer** — company-specific rubrics (13 FAANG+ companies), AI-driven mocks.
4. **Pramp** — free peer mocks, good early-stage volume.
5. **IGotAnOffer / Interview Kickstart** — paid coaching with ex-FAANG ML engineers; behavioral focus.
6. **InterviewNode AI Coach / PrampGPT** — emerging AI mock platforms aligned to FAANG rubrics.

---

## 6. Resume & Profile Optimization

### 6a. The Title Surgery (most important single move)

Current self-description: "Associate Principal Engineer, Platform Engineer."
**Replace with:** "Associate Principal Engineer — AI Platform & Agent Infrastructure" OR "Senior Staff AI Platform Engineer (Agentic Systems)."

Recruiters and ATS index on titles. A 2026 *Resume Optimizer Pro* analysis of FAANG/Anthropic/Netflix MLE JDs found that mismatched titles route candidates into the wrong shortlist and "underprice offers by $15K to $30K." The same applies in India.

### 6b. Resume Bullet Rewrite Pattern

For each bullet, follow the FAANG MLE pattern (per IGotAnOffer + Resume Optimizer Pro 2026):
**[Action verb] [system/model] using [stack] resulting in [quantified business or technical metric].**

Examples to model from your actual reva.ai work:

- **Weak (current):** "Manage Kubernetes for the platform team."
- **Strong:** "Architected multi-tenant Kubernetes-based agent serving platform on AWS supporting *N* concurrent LangGraph agents with sub-200ms p95 tool-call latency; cut GPU spend *X%* through LoRA multi-adapter packing on shared inference endpoints."

- **Weak:** "Worked on cybersecurity for AI agents."
- **Strong:** "Designed and shipped Intent-Based and Policy-Based Access Control (IBAC/PBAC) for a multi-agent system on Amazon Bedrock, enforcing fine-grained tool/data permissions across *N* agents and reducing prompt-injection-driven privilege escalation incidents by *X%*; presented framework to *N* enterprise customers."

- **Weak:** "Built AI agents using LangGraph."
- **Strong:** "Built production agentic system on LangGraph + Amazon Bedrock (Claude 3.7 / Llama 3 70B) with persistent state, tool orchestration, and RAG over *N* enterprise documents; integrated Phoenix tracing and golden-dataset evals achieving *X%* task-success rate on *Y* benchmark."

### 6c. Required Keyword Coverage (ATS-driven, 2026 JDs)

**Must appear in your resume body:** Python, Kubernetes, LangGraph, LangChain, Amazon Bedrock, RAG, Vector Database, AI Agents, Multi-Agent Systems, MLOps, MLflow, vLLM, Ray, KServe, Pinecone/Qdrant/Milvus, Prompt Engineering, Guardrails, AWS, Docker, Terraform, Observability, LLM, Agentic AI, MCP/A2A.

**Add as you complete the roadmap:** PyTorch, Triton/TGI, LoRA/QLoRA, DeepSpeed/FSDP, Kubeflow, Vertex AI / SageMaker, CrewAI, Google ADK, Arize Phoenix, LangSmith.

### 6d. LinkedIn Profile

- **Headline (160 chars):** "AI Platform Engineer | Agentic AI on Bedrock & LangGraph | Multi-Agent Security (IBAC/PBAC) | 15 yrs scaling cloud platforms | Bangalore"
- **About:** Lead with the unique angle — "I build the platforms that make AI agents safe and scalable in production." Then 3 bullets of impact, then a "currently exploring" line on 2026 themes (MCP, A2A, agentic RAG).
- **Featured:** pin your blog posts and Project 1/2 GitHub repos.
- **Skills:** Order matters — put AI/Agent skills *first*, infra second.
- **Activity:** Post or comment on LangGraph/Anthropic/NVIDIA technical content 2–3×/week for the next 4 months. Recruiters see active profiles 2–3× more often.

### 6e. GitHub Portfolio — what to build

You need 2–3 substantive projects with clean READMEs, results, and architecture diagrams. Ideal sequence (mapped to roadmap):

1. **`agent-iam`** — open-source IBAC/PBAC framework for multi-agent systems (your differentiator). Could become a real OSS contribution. Frame around MCP-tool-permissions integration.
2. **`prod-agent-stack`** — reference production agent platform: LangGraph + vLLM + RayServe on K8s + Phoenix observability + golden-dataset eval harness, reproducible on a single GKE/EKS cluster.
3. **`agentic-rag-bench`** — benchmark of 4 RAG architectures (naive, hybrid, agentic single-agent, multi-agent reasoning) on a public corpus, with cost/latency/accuracy tradeoff curves. Cite the arXiv:2501.09136 and arXiv:2506.10408 surveys.

**Open-source contributions that move the needle:** LangGraph itself, Ray/KubeRay, vLLM, KServe, OpenAgents (MCP/A2A), Hugging Face TRL/PEFT, Pydantic-AI. Even one merged non-trivial PR signals "production-grade engineer who participates in the ecosystem" — disproportionate weight in hiring committee debates.

### 6f. Technical Blog

Set up a simple Hashnode/Medium/personal site. Write 3 high-quality posts:
1. "Implementing IBAC for Multi-Agent LangGraph Systems on Bedrock" (your unique angle).
2. "Serving 50 LoRA-Tuned Adapters on a Single A100 with vLLM Multi-LoRA" (production engineering).
3. "Agentic RAG vs Naive RAG: Benchmarks from 4 Production Architectures."

Cross-post on LinkedIn and r/LocalLLaMA, r/MachineLearning, Hacker News. Each post that gets traction is interview lubricant — Anthropic and Google recruiters specifically read engineering blogs.

---

## 7. Resources List (Curated, 2026)

### Books (must-read in this order)
1. **Aminian & Sheng — *Generative AI System Design Interview*** (ByteByteGo) — the single most important interview book for your target roles.
2. **Chip Huyen — *Designing Machine Learning Systems*** (O'Reilly, 2022) — still the canonical MLOps book.
3. **Chip Huyen — *AI Engineering*** (O'Reilly, 2025) — currently #1 on O'Reilly platform; covers post-LLM era.
4. **Aminian & Sheng — *Machine Learning System Design Interview*** (vol 1) — for classical ML rounds.
5. **Sebastian Raschka — *Build a Large Language Model from Scratch*** — best PyTorch + transformer hands-on book.
6. **Alex Xu — *System Design Interview vol 1 & 2*** — non-negotiable for the regular system design round.
7. **Cracking the Coding Interview** / **Elements of Programming Interviews** — DSA refresher.

### Courses & Certifications (priority-ranked for ROI in 2026)
1. **Google Cloud Professional ML Engineer (PMLE)** — *highest ROI* for your profile; now includes Vertex AI Agent Builder, GenAI scope. ~₹17,000, 8–10 weeks. Counts heavily for Google Cloud and most GCC roles.
2. **NVIDIA DLI** — "Building LLM Applications with Prompt Engineering," "Generative AI with Diffusion Models," "Rapid Application Development with LLMs." Cheap, hands-on, reputable for NVIDIA-adjacent roles.
3. **Databricks Certified Generative AI Engineer Associate** — direct credibility if targeting Databricks; ~$200.
4. **DeepLearning.AI / LangChain Academy** — free LangGraph + Agent courses (Harrison Chase taught some); MUST-do given your stack.
5. **AWS Certified ML Engineer – Associate** — still active (the older ML Specialty retires March 31, 2026).
6. **Microsoft Azure AI Engineer Associate (AI-102)** — only if targeting Microsoft heavily.
7. **Stanford CS231n / CS224n / CS336** — free YouTube; depth on transformers, attention.
8. **Hugging Face Agents Course + MCP Course** — free, current, taught by HF ML engineers (per FiftyOne meetup speakers, March 2026).
9. **Full Stack Deep Learning** — free, MLOps focus.

### GitHub Repos to Study & Star
- `langchain-ai/langgraph` — read source, contribute issues/PRs.
- `ray-project/ray` and `ray-project/kuberay`.
- `vllm-project/vllm`.
- `kubeflow/kubeflow` and `kserve/kserve`.
- `Arize-ai/phoenix`.
- `huggingface/peft`, `huggingface/trl`.
- `chiphuyen/dmls-book` and `chiphuyen/aie-book` — companion repos for Huyen's books.
- `amitshekhariitbhu/ai-engineering-interview-questions` — Q bank.
- `alexeygrigorev/ai-engineering-field-guide` — Q4 2025 / Q1 2026 hiring data, takehome examples.
- `serodriguez68/designing-ml-systems-summary` — DMLS book summary.

### Papers (read in this order, all 2024–2026)
1. **Singh et al. (Jan 2025, v4 Apr 2026), arXiv:2501.09136** — "Agentic RAG: A Survey." Table-stakes reference.
2. **Sapkota et al. (May 2025, v5 Sep 2025), arXiv:2505.10468** — "AI Agents vs Agentic AI: A Conceptual Taxonomy."
3. **VLDB 2025 Workshop paper** — "Towards the Next Generation of Agent Systems: From RAG to Agentic AI" (vldb.org).
4. **arXiv:2506.10408** — "Reasoning RAG via System 1 or System 2."
5. **Anthropic** — Constitutional AI, Sparse Autoencoders / Mechanistic Interpretability blog posts (esp. for Anthropic interviews).
6. **DeepSeek-V3, V3-R1** technical reports (MoE + reasoning).
7. **Mixtral 8×22B** technical report (MoE architecture in production).
8. **InstructGPT** + **DPO** (Rafailov et al.) — RLHF foundations.
9. **MCP** spec (Anthropic) and **A2A** spec (Google).
10. **DSPy** paper (Khattab et al.) — programming, not prompting.

### Newsletters / Blogs to subscribe
- **Latent Space** (swyx) — best AI engineering newsletter.
- **The Batch** (Andrew Ng).
- **Eugene Yan's blog** — applied ML system design.
- **Lilian Weng's blog** (OpenAI) — research depth.
- **Chip Huyen's blog**.
- **ByteByteGo newsletter** (Alex Xu).
- **Anthropic, Google DeepMind, OpenAI engineering blogs.**

---

## 8. Company-Specific Insights

### Anthropic (Bengaluru)
- **Stack/teams:** Applied AI (architects + engineers, customer-facing technical), Beneficial Deployments (nonprofit/govt deployments). India is Claude's #2 market globally; revenue doubled since Oct 2025 announcement.
- **Process:** typically recruiter screen → coding (1) → applied AI / LLM system design (1–2) → behavioral with values emphasis (safety, mission) → leadership/bar-raiser. Glassdoor and IGotAnOffer have detailed Anthropic-specific guides.
- **Why a fit for you:** Cybersecurity-for-agents at reva.ai aligns with safety mission; LangGraph + Bedrock experience translates directly (Anthropic's MCP is the protocol you'd use); Applied AI Architect role explicitly wants someone who can design scalable LLM solutions.
- **Stability:** privately held, $183B+ valuation as of 2026, hiring aggressively in India. Lower layoff risk than mid-tier AI startups.

### Google (Bangalore)
- **AI platforms to know:** **Vertex AI**, **Vertex AI Agent Builder**, **Google ADK**, Gemini Enterprise. Many open Bangalore SWE roles explicitly list LangGraph/CrewAI/ADK/ReAct/MCP.
- **Process:** Recruiter → 1 phone coding → 5-round onsite (3 coding, 1 system design, 1 Googleyness/leadership). For senior, expect ML system design replacing one coding round.
- **Best teams:** Cloud AI (Applied AI, Gemini Enterprise, Forward Deployed Engineering), DeepMind India (research-heavy), BigQuery GenAI Operators, Search/Assistant ML platforms.
- **Stability:** Strong; India headcount growing per recent India.com reporting (Big Tech added 32K India jobs in 2025).

### Microsoft (Bangalore + Hyderabad)
- **Best teams:** CoreAI (Experimentation Platform), Microsoft Research India (Research Engineer roles open Feb–April 2026 in Bangalore — AI/ML scalable architectures), Copilot Studio + Teams Proactive Agents, Azure AI Foundry.
- **Process:** Recruiter → 4–5 onsite (coding + design + cross-collab + hiring manager). AS/AS2 levels (the senior IC band) target 14+ YOE.
- **Why a fit:** Heavy investment in agentic systems (Copilot agents); your Bedrock work translates to Azure OpenAI / Foundry Models.
- **Stability:** Among the most stable FAANG GCCs in India; major expansion in Bangalore Garage 2025–26.

### Amazon / AWS India (Bangalore)
- **Best teams:** **Bedrock Agents / AgentCore**, SageMaker AI, Q Developer, Alexa AI India.
- **Process:** Notoriously LP-heavy behavioral (16 Leadership Principles). 4 onsite rounds, each weighted 50% LPs / 50% technical. Bar Raiser interview is critical.
- **Why a strong fit:** You already build on Bedrock daily; explicit advantage.
- **Stability:** Mixed — Amazon had India layoffs in late 2025; AWS specifically remains a growth org.

### NVIDIA (Bangalore)
- **Best teams:** NeMo Framework, Triton Inference Server, NIMs (NVIDIA Inference Microservices), DGX Cloud, AI Enterprise, Robotics/Isaac.
- **Process:** Strong on systems/CUDA fundamentals; deep system design round; less DSA-heavy than FAANG.
- **Why a fit:** Your K8s + GPU adjacency. Even without CUDA expertise, an NIMs / Triton platform role is realistic; just lean into the DLI courses.
- **Stability:** Best-in-class — NVIDIA stock and headcount have boomed; 73 Bangalore openings as of April 2026 (Glassdoor).

### Databricks India (Bangalore)
- **Best teams:** Mosaic AI, Agent Bricks, Vector Search, Lakehouse AI.
- **Process:** Heavy system design, often Spark/Lakehouse-flavored. Coding bar = FAANG-level.
- **Why a fit:** Your platform-eng + agent skills are exactly Mosaic's profile.
- **Stability:** Pre-IPO unicorn; high upside but IPO-timing risk.

### Sarvam AI (Bangalore)
- **Roles fit:** Forward Deployed Engineer (RAG/ML specialist), Site Reliability Engineer, ML Engineer Speech AI.
- **Why a fit:** Smaller, India-sovereign-AI mission, your platform skills are at premium.
- **Stability:** Series-A/B startup; lower stability but career upside if they win the Indic-AI niche.

### Krutrim, Flipkart, Razorpay, CRED, Swiggy, Ola
- Solid B-tier options. Use them as comp leverage and faster-cycle interview practice. Most have ML platform / Agent platform initiatives in 2026.

### Compensation comparison summary (Bangalore, senior IC, 2026)
NVIDIA ≈ Databricks ≈ Anthropic ≈ Google > Microsoft ≈ Amazon ≈ Apple > Indian unicorns > GCCs (BFSI) > IT services (TCS/Infosys/Wipro you're correctly avoiding).

### Stability ranking post-2024–26 layoffs
Microsoft = Google = NVIDIA > Apple > Amazon > Meta > Anthropic (private, but well-funded and growing) > Databricks > Indian unicorns > Indian AI startups.

### Remote/hybrid policies (April 2026 status)
Most FAANG India is **3 days/week in office** (RTO mandate). Anthropic Bengaluru is on-site/hybrid. NVIDIA flexible. Databricks hybrid. Sarvam mostly on-site. **No fully remote roles at top FAANG India** as of April 2026 — plan for 3-day in-office.

### Visa / international relocation potential
Strong from all FAANG (typically L1-B after 1 year for Google/Microsoft/Amazon, internal transfer programs at Apple/Meta). Anthropic has UK/US relocation paths. NVIDIA has US relocation. Databricks has US/EU. This is a real long-term lever — but the 2025 H-1B reform tightened the US path; UK and Ireland are now the easier transfers.

---

## 9. Career Longevity & Future-Proofing

### Most resistant roles to AI-driven obsolescence (2026–2030)

1. **AI Platform / ML Infrastructure Engineer** — the platform itself is what makes AI scale. As AI generates more *code*, the *systems* it runs on become *more* important, not less. **This is your bullseye.**
2. **AI Safety / Security Engineer** — regulation (EU AI Act, India's DPDP, NIST AI RMF) is creating durable demand. **Direct overlap with your reva.ai work.**
3. **Forward Deployed / Applied AI Engineer** — deeply customer-facing, requires judgment AI can't replicate.
4. **Distributed Systems / GPU Infrastructure Engineer** — physics doesn't get cheaper.

### Less defensible long-term
- "Prompt Engineer" — already commoditized in 2026.
- Junior implementer roles (Pichai's "75% AI-generated code" data point per Fast Company 2026).
- Pure ML researcher roles (PhD-gated, narrow paths).

### Why your direction is correct for 15+ years of stability
You're combining **infrastructure (durable)** + **AI agents (the layer where economic value pools)** + **safety/security (regulated)**. Triple moat. The only category arguably more defensible is "AI Researcher with PhD," which is closed to you and isn't your stated goal.

### 2026–2030 trends to specialize toward
- **Agentic systems in production** (your current work).
- **MCP / A2A protocols** — interop is the next platform fight; bet on it.
- **Multi-agent orchestration & evaluation** — eval is the unsolved problem of 2026.
- **AI Security/Governance** — your IBAC/PBAC is ahead of the curve.
- **Edge / on-device agents** — Apple's bet; relevant if you eventually want Apple India.

---

## 10. Networking & Application Strategy

### Application channel mix (target ~60 applications over 12 weeks)

| Channel | Share | Conversion rate (typical) |
|---|---|---|
| **Warm referrals via LinkedIn/community** | 50% | 20–35% to phone screen |
| **Cold apply via company portal** | 25% | 3–8% |
| **Recruiter-initiated (after profile activation)** | 15% | 30–50% |
| **Specialist tech recruiters** | 10% | 10–20% |

Per Zippia/Glassdoor 2026 data, referred candidates are **~4× more likely to get an interview** than cold applicants. Don't skip the referral push.

### Top tech recruiters for AI roles in Bangalore (specialist firms)
- **Heidrick & Struggles** (executive AI/exec talent)
- **Hunt Partners** (senior tech IC + leadership)
- **Antal International** (FAANG/GCC volume)
- **Karya Search**, **Avtar Group**, **WizeHire**
- **The Bridge / Vahan** (product-company specialists)
- LinkedIn Recruiter Lite + Naukri RMS (recruiters source heavily here — keyword optimize)

### LinkedIn outreach playbook
- **Week 1:** identify 50 ICs at target companies — preferably "Senior Software Engineer / Staff Engineer / Principal Engineer, AI Platform / Agents / ML Infrastructure" at the *exact teams* you'd join.
- **Connection request** (no message OR ≤300 chars):
  > "Hi [name] — I'm an AI Platform Engineer in Bangalore building agent systems on Bedrock + LangGraph with a focus on multi-agent security (IBAC/PBAC). Followed your work on [specific thing]. Would love to connect."
- **After accept (3–5 days later):** specific engagement on a recent post; 1–2 weeks later send the ask:
  > "Hi [name] — I noticed [team] is hiring for [role link]. Given my work on [1 sentence specific match], would you be open to a 15-min chat? Happy to send my resume first if helpful."
- **Avoid:** mass templates, unsolicited resume dumps in first message.
- Per workforfang.com data: small-batches outreach (5–10/week with personalization) beats mass-outreach 3:1 on response rate.

### Communities to join (Bangalore + remote)
- **AI Tinkerers Bengaluru** (bengaluru.aitinkerers.org) — 100K+ global, screened, demos-only no-slides. **Highest-quality Bangalore community.** Members from Amazon, Microsoft, Google, Stripe, Atlassian.
- **Bangalore AI Developers Group / AICamp** (meetup.com/bangalore-ai-tech-talks) — monthly, ~10K members, weekly Google-Cloud-led DevTalks.
- **Bangalore AI, ML and Computer Vision Meetup** — Voxel51-organized, frequent agentic AI sessions.
- **Cypher 2026** (Oct 7–9, Bengaluru) — India's flagship AI conference, 5,000+ attendees, 150+ speakers.
- **Microsoft Reactor Bengaluru** — frequent AI/dev sessions.
- **Agentic AI Community Bengaluru** (Meetup).
- **ODSC AI Bengaluru** (Meetup).
- **AI Tinkerers Slack / Discord** — global, where the actual builders hang out.
- **MLOps Community Slack** — best global MLOps community.
- **r/LocalLLaMA**, **r/MachineLearning**.
- **Blind** (verified work email) — comp negotiation intel; FAANG India levels and offers shared frequently.
- **AI Engineer Summit / Latent Space Discord** — global AI engineering community; recruiters lurk.

### Timing of applications
- **Best windows:** Jan–Mar and Jul–Sep (FAANG headcount-budget cycles align). April–May (now) is a *good* secondary window because Q1 hires that didn't pan out are getting backfilled.
- **Avoid:** mid-Nov to early-Jan (US Thanksgiving + Christmas freeze most FAANG hiring).
- **Bunch interviews** — once you have one offer, accelerate all other pipelines so all offers land in a 2–3 week window for negotiation leverage.

---

## Caveats

- **Compensation ranges are estimates** triangulated from public sources (Levels.fyi, Glassdoor, Scaler, NASSCOM, Taggd, ShifttoTech, product-based.in, Storyboard18, BW People). Individual offers depend heavily on level fit, interview performance, competing offers, and recruiter alignment. Always validate via Levels.fyi India + Blind for the specific company/level before negotiation.
- **Active job openings cited** are confirmed open as of late April 2026 from the company career portals (Anthropic, Google, Microsoft, NVIDIA, Databricks, Sarvam) but FAANG postings rotate weekly; verify via company portal at time of application.
- **Some 2026 sources cited (cambridgeinfotech.io, dheya.com, shifttotech.co.in, taggd.in, generativeaimasters.in, scaler.com)** are content-marketing sites that aggregate NASSCOM/Glassdoor/Levels.fyi data; treat their *trend* statements as directional rather than precise. The most reliable salary anchors are **Levels.fyi**, **Glassdoor company-specific salaries**, and **Blind**.
- **Anthropic Bangalore listings are evolving rapidly** post-office-opening (Q1 2026); current Bangalore-specific listings are Applied AI Architect and Applied AI Engineer (Beneficial Deployments). Senior Software Engineer (Inference) and other deep-eng roles remain US-based as of April 2026.
- **AutoGen status** — Microsoft has shifted AutoGen to maintenance mode in 2026 in favor of the broader Microsoft Agent Framework (per OpenAgents and PE Collective comparisons). Prioritize LangGraph + CrewAI + Google ADK over AutoGen if time-constrained.
- **"AI Engineer" salary averages reported by Glassdoor (~₹12.67 LPA average, Feb 2026)** mix freshers and seniors and *severely understate* what a 15-YOE Senior AI Platform Engineer at a FAANG GCC would actually earn. Use Levels.fyi senior-band data as your true anchor.
- **The 75% AI-generated-code Pichai quote** (Fast Company 2026) is widely circulated but reflects a workflow/tooling shift, not displacement of senior roles — senior platform/architecture/safety work is *more* valuable in that environment, not less. Don't let that quote panic you out of this transition; it actually argues *for* it.
- **Visa/relocation paths from India** have tightened post-2025 H-1B reforms. UK, Ireland, Singapore, and Australia are now easier secondary moves than the US for FAANG India transferees.
- **This roadmap assumes you can dedicate 15–20 hrs/week** for 14 weeks alongside your day job. If your reva.ai workload exceeds that, extend the plan to 5–6 months by stretching each phase ~30%.