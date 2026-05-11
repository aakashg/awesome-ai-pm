# Awesome AI PM

A curated guide to AI product management. Frameworks, tools, skills, and resources for PMs building AI products.

Built and maintained by [Aakash Gupta](https://www.aakashg.com) | [Product Growth Newsletter](https://www.news.aakashg.com)

---

## Table of Contents

- [AI PM Fundamentals](#ai-pm-fundamentals)
- [Core Technical Concepts](#core-technical-concepts)
- [AI Product Discovery](#ai-product-discovery)
- [AI Product Design](#ai-product-design)
- [AI Pricing](#ai-pricing)
- [AI Metrics and Evaluation](#ai-metrics-and-evaluation)
- [AI Agents and Tools](#ai-agents-and-tools)
- [Prototyping with AI](#prototyping-with-ai)
- [PM Workflows with AI](#pm-workflows-with-ai)
- [AI PM Career](#ai-pm-career)
- [AI PM Interview Prep](#ai-pm-interview-prep)
- [Essential Reading](#essential-reading)
- [Tools and Platforms](#tools-and-platforms)

---

## AI PM Fundamentals

What makes AI product management different from traditional PM work.

**The core difference:** Traditional products have deterministic behavior — the same input always produces the same output. AI products are probabilistic — the same input can produce different outputs. This changes how you spec, test, launch, and measure everything.

### Key Concepts

- **Probabilistic vs deterministic products** — AI outputs vary. Your spec needs to define acceptable ranges, not exact outputs.
- **Data as a product input** — The quality of your training data directly determines product quality. PMs own the data strategy.
- **Evaluation-driven development** — You can't manually QA an AI feature. You need automated evals before and after every change.
- **Prompt engineering as product design** — The system prompt IS the product spec for LLM features.
- **Feedback loops** — AI products improve from usage data. Design the loop: collect, label, retrain, deploy, measure.

### Resources

- [How to Build AI Products the Right Way](https://www.news.aakashg.com/p/how-to-build-ai-products) — Complete framework for AI product development
- [Complete Course: AI Product Management](https://www.news.aakashg.com/p/complete-course-ai-product-management) — From basics to expert: prompting, PRDs, fine-tuning, RAG, MCP, and agents
- [Marty Cagan on AI Product Management](https://www.svpg.com/) — How the product operating model adapts to AI
- [AI Product Institute](https://www.aiproductinstitute.com/) — Community and resources for AI PMs
- Google's People + AI Guidebook — Design patterns for human-AI interaction

---

## Core Technical Concepts

You don't need to build models. You need to make informed product decisions about them.

### LLMs and Foundation Models

| Concept | What It Means for PMs |
|---------|----------------------|
| **Tokens** | LLMs process text in chunks (tokens). More tokens = higher cost and latency. Your pricing model depends on this. |
| **Context window** | How much text the model can "see" at once. Determines what features are possible (e.g., summarizing a 100-page doc). |
| **Temperature** | Controls randomness. Low = predictable (good for data extraction). High = creative (good for brainstorming). You set this per feature. |
| **Fine-tuning** | Training a model on your specific data. Expensive but improves quality for domain-specific tasks. |
| **RAG (Retrieval-Augmented Generation)** | Pull relevant docs into the prompt before generating. Cheaper than fine-tuning, good for knowledge bases. |
| **Hallucination** | Model confidently generates false information. Your #1 product risk. Design for it. |
| **Embeddings** | Numeric representations of text. Used for search, recommendations, clustering. |
| **Agents** | AI systems that can take actions (call APIs, browse web, write code), not just generate text. |

### When to Use What

| Use Case | Approach | Why |
|----------|----------|-----|
| Customer support bot | RAG + base model | Needs accurate answers from your docs, not creative generation |
| Content generation | Fine-tuned model or prompted base model | Needs to match your brand voice |
| Data extraction | Low-temperature base model with structured output | Needs deterministic, parseable results |
| Search | Embeddings + vector DB | Semantic search beats keyword matching |
| Workflow automation | Agent framework | Needs to take actions, not just generate text |

### Resources

- [RAG vs. Fine-tuning vs. Prompt Engineering: The Complete Guide](https://www.news.aakashg.com/p/rag-vs-fine-tuning-vs-prompt-engineering) — Decision framework built with OpenAI's Director of PM
- [The Ultimate Guide to Context Engineering for PMs](https://www.news.aakashg.com/p/context-engineering) — How to fill the context window with the right information
- [Prompt Engineering Best Practices](https://www.news.aakashg.com/p/prompt-engineering) — Latest techniques and workflows

---

## AI Product Discovery

How to figure out what AI features to build when users can't tell you what they want.

### The Discovery Problem

Users can't articulate what AI features they want because they don't know what's possible. You can't survey your way to an AI roadmap. You have to:

1. **Prototype first, validate second** — Build a working demo before writing a spec
2. **Observe behavior, not preferences** — Watch what users do with the prototype, don't ask what they'd want
3. **Test with real data** — Synthetic demos lie. Use actual user data in your prototypes.

### Discovery Framework for AI Features

1. **Identify high-frequency manual tasks** — What do users do repeatedly that AI could handle?
2. **Map data availability** — Do you have the data needed to power this feature?
3. **Prototype the interaction** — Build a working demo (even if the AI is faked behind the scenes)
4. **Test with 5-10 real users** — Not a survey. Sit with them. Watch their reaction.
5. **Measure willingness to trust** — AI features fail when users don't trust the output. Measure trust, not just satisfaction.

### Resources

- [Teresa Torres' Step-by-Step Guide to AI Product Discovery](https://www.news.aakashg.com/p/teresa-torres-podcast) — Continuous discovery adapted for AI products
- [OpenAI's Framework for AI Product Sense](https://www.news.aakashg.com/p/ai-product-sense) — How top PMs think about AI product decisions
- [Your Guide to AI Product Strategy](https://www.news.aakashg.com/p/ai-product-strategy) — Why AI reshapes what's possible and how users interact with your product
- [Teresa Torres on Continuous Discovery](https://www.producttalk.org/) — The original discovery framework

---

## AI Product Design

Designing interfaces for probabilistic outputs.

### Design Principles

1. **Show confidence, not certainty** — "This might be..." beats "Here's your answer." Users need to know AI can be wrong.
2. **Make correction easy** — If the AI gets it wrong, fixing it should take one click, not a restart.
3. **Progressive disclosure** — Show the simple answer first. Let users drill into reasoning on demand.
4. **Inline, not separate** — AI features work best embedded in existing workflows, not as standalone tools (Notion AI vs. a separate AI app).
5. **Human-in-the-loop by default** — Let users review before AI takes action. Automate only after trust is established.

### Common AI UI Patterns

| Pattern | When to Use | Example |
|---------|-------------|---------|
| **Autocomplete** | High-confidence, low-stakes suggestions | Gmail Smart Compose |
| **Draft + edit** | Medium-confidence, user wants control | Notion AI writing |
| **Side panel** | AI as assistant, user drives the workflow | GitHub Copilot |
| **Fully automated** | High-confidence, low-stakes, high-frequency | Spam filtering |
| **Chat interface** | Open-ended exploration or Q&A | ChatGPT, customer support |

### Resources

- [The AI Product Design Interview: Your Complete Guide](https://www.news.aakashg.com/p/the-ai-product-design-interview-your) — Frameworks for designing AI product experiences
- Google's People + AI Guidebook — Design patterns and principles
- Apple Human Interface Guidelines for Machine Learning

---

## AI Pricing

Pricing AI products when your best users are your most expensive users.

### The Core Tension

Traditional SaaS has near-zero marginal cost per user. AI products pay for compute on every interaction. A casual user costs pennies. A power user costs thousands per month.

### Pricing Models

| Model | How It Works | Best For | Risk |
|-------|-------------|----------|------|
| **Flat subscription** | Fixed price, unlimited use | Low-variance usage | Power users crush margins |
| **Usage-based** | Pay per token/request/action | Developer tools, APIs | Unpredictable bills scare users |
| **Tiered with credits** | Plans include credit pools | Prosumer tools | Complex to communicate |
| **Per-seat + usage cap** | Per user with limits | Enterprise SaaS | Users game seat allocation |
| **Outcome-based** | Pay per result (e.g., per resolved ticket) | High-value automations | Hard to attribute outcomes |
| **Hybrid** | Base subscription + usage overage | Most AI SaaS | Requires good metering |

### Key Rule

Before you set any price, pull the cost distribution. What does your P10 user cost? P50? P90? If the ratio exceeds 10x, flat pricing will break. In AI products, it almost always exceeds 10x.

### Resources

- [How to Price AI Products: The Complete Guide](https://www.news.aakashg.com/p/how-to-price-ai-products) — 6 models, case studies, and a decision tree for AI pricing

---

## AI Metrics and Evaluation

### Metrics That Matter for AI Features

| Metric | What It Measures | Why It Matters |
|--------|-----------------|---------------|
| **Task completion rate** | % of users who accomplish their goal with the AI | The #1 metric. If users can't complete tasks, nothing else matters. |
| **Acceptance rate** | % of AI suggestions users accept | Proxy for quality. Below 30% = the feature is noise. |
| **Edit distance** | How much users modify AI output before using it | Low edit distance = high quality. Track over time. |
| **Time to value** | How fast users get a useful result | AI should be faster than manual. If not, why use it? |
| **Fallback rate** | % of times users abandon AI and do it manually | High fallback = trust problem or quality problem. |
| **Hallucination rate** | % of outputs containing factual errors | Must track. Must have a threshold. Must automate detection. |
| **Cost per interaction** | $ spent on compute per user action | Your margin depends on this. Track by user segment. |

### AI Evaluation (Evals)

Evals are automated tests for AI output quality. They replace manual QA for probabilistic systems.

**Types:**
- **Deterministic evals** — Does the output contain required fields? Is it valid JSON? Is it under the token limit?
- **LLM-as-judge evals** — Use a separate LLM to grade outputs on criteria (relevance, accuracy, tone)
- **Human evals** — Gold standard but expensive. Use for calibrating automated evals.
- **A/B test evals** — Ship both versions, measure user behavior

### Resources

- [AI Evals: Everything You Need to Know to Start](https://www.news.aakashg.com/p/ai-evals) — Practical walkthrough of building and running evals
- [The AI Product Success Metrics Interview: Your Complete Guide](https://www.news.aakashg.com/p/ai-success-metrics-interview) — Framework for defining AI feature metrics
- [Vibe Experimentation: An AI PM's Guide](https://www.news.aakashg.com/p/vibe-experimentation) — How to run experiments on AI features

---

## AI Agents and Tools

### What PMs Need to Know About Agents

An agent is an AI system that can take actions — not just generate text. It can call APIs, browse the web, execute code, and chain multiple steps together.

**Why PMs care:** Agents shift your product from "tool the user operates" to "assistant that operates tools on behalf of the user." This changes every assumption about UX, trust, pricing, and error handling.

### Agent Architecture for PMs

| Component | PM Decision |
|-----------|-------------|
| **Planner** | How much autonomy does the agent get? (Full auto vs. human approval at each step) |
| **Tools** | What can the agent access? (APIs, databases, file systems) Each tool = a risk surface. |
| **Memory** | Does the agent remember past conversations? How long? Privacy implications. |
| **Guardrails** | What can the agent NOT do? (Spend limits, scope restrictions, content policies) |

### MCP (Model Context Protocol)

MCP is becoming the standard for connecting AI tools to external services. OpenAI, Google, Microsoft, and Cloudflare have all adopted it.

**For PMs:** If your product doesn't have an MCP server, AI agents can't discover or use it. MCP is the new API.

### Resources

- [AI Agents for PMs: Practical Guide](https://www.news.aakashg.com/p/ai-agents-pms) — The practical guide to building and using AI agents
- [The Ultimate Guide to Context Engineering for PMs](https://www.news.aakashg.com/p/context-engineering) — How to give agents the right information
- [RAG vs. Fine-tuning vs. Prompt Engineering](https://www.news.aakashg.com/p/rag-vs-fine-tuning-vs-prompt-engineering) — Choosing the right optimization approach

---

## Prototyping with AI

### The PM Prototyping Stack

You can go from idea to working prototype in under an hour. No designer. No engineer.

| Tool | What It Does | Best For |
|------|-------------|----------|
| **Cursor** | AI-powered code editor | Full prototypes with backend logic |
| **Claude Code** | Terminal-based AI coding | PM workflows, scripts, data tools |
| **Bolt** | Prompt-to-app in browser | Quick UI prototypes |
| **Replit** | Cloud-based AI coding | Shareable demos |
| **v0 by Vercel** | Prompt-to-UI component | Design mockups that work |

### Prototyping Workflow

1. Describe the problem and desired UX in plain English
2. Let the AI generate the first version
3. Iterate through conversation ("make the CTA more prominent", "add error handling")
4. Deploy to a shareable URL
5. Put it in front of real users

### Resources

- [Tutorial of Top 5 AI Prototyping Tools](https://www.news.aakashg.com/p/ai-prototyping-for-pms) — Bolt, Lovable, v0, Replit, and Cursor compared
- [Ultimate Guide to AI Prototyping Tools](https://www.news.aakashg.com/p/ai-prototyping-tutorial) — Step-by-step from idea to working app
- [The Ultimate Guide to Replit](https://www.news.aakashg.com/p/guide-replit) — Complete Replit walkthrough for PMs
- [How to Make a Winning PM Portfolio with Vibe Coding](https://www.news.aakashg.com/p/vibe-code-pm-portfolio) — Turn prototypes into portfolio pieces
- [How to Ace the Vibe Coding Interview](https://www.news.aakashg.com/p/vibe-coding-interview) — Frameworks and examples for the newest PM interview format

---

## PM Workflows with AI

### Claude Code for PMs

Claude Code turns your terminal into a PM workstation. Set up a CLAUDE.md file and skills, and Claude handles PM tasks: PRD writing, competitive analysis, metrics definition, stakeholder updates.

| Workflow | What It Does |
|----------|-------------|
| **PRD generation** | Asks clarifying questions, then generates structured PRDs |
| **Competitive teardown** | Analyzes competitor products with structured frameworks |
| **Status updates** | Turns messy notes into clean stakeholder updates |
| **Metrics definition** | Defines primary, secondary, guardrail, and anti-metrics |
| **Feedback synthesis** | Clusters user feedback by theme across multiple sources |

### Resources

- [The Claude Code Tutorial for AI PMs](https://www.news.aakashg.com/p/carl-vellotti-podcast) — Why you need to use it and how to get started
- [8 Months of Claude Code Lessons in 80 Minutes](https://www.news.aakashg.com/p/carl-vellotti-podcast-2) — Advanced workflows and power user tips
- [How to Vibe PM with Claude Code and Your Analytics Data](https://www.news.aakashg.com/p/frank-lee-podcast) — Five workflows that replace manual dashboard reviews
- [Claude Skills Tutorial](https://www.news.aakashg.com/p/claude-skills-tutorial) — Setting up skills for PM automation
- [How to Use Claude for Work](https://www.news.aakashg.com/p/how-to-use-claude-for-work) — Complete setup guide
- [Claude Cowork Guide](https://www.news.aakashg.com/p/you-should-be-using-claude-cowork) — Using Claude's collaborative features
- [PM Claude Code Setup](https://github.com/aakashg/pm-claude-code-setup) — Ready-to-use CLAUDE.md and PRD writer skill
- [PM Claude Skills](https://github.com/aakashg/pm-claude-skills) — 5 drop-in skills for PM work
- [PM Prompt Library](https://github.com/aakashg/pm-prompt-library) — Battle-tested prompts for PM workflows

---

## AI PM Career

### The AI PM Role

AI PM is the fastest-growing specialization in product management. The role sits at the intersection of traditional PM skills and AI-specific knowledge.

**What's different:**
- You spec probabilistic systems, not deterministic features
- You define evaluation criteria, not just acceptance criteria
- You manage model behavior, not just UI behavior
- You own the data pipeline as a product input
- You price around compute costs, not just value

### How to Break In

1. **Build a GitHub profile** — Show you can build, not just talk
2. **Ship an AI prototype** — One working project beats ten certificates
3. **Learn the vocabulary** — You need to speak to engineers about models, fine-tuning, evals, and inference
4. **Publish your thinking** — Write about AI product decisions. LinkedIn, blog, or GitHub READMEs.
5. **Target the right roles** — Look for "AI PM", "ML PM", or PM roles on AI-native teams

### Resources

- [How to Land a $300K+ AI PM Job](https://www.news.aakashg.com/p/ai-pm-job-search-guide) — Complete roadmap for the AI PM job search
- [How to Become an AI PM with No Experience](https://www.news.aakashg.com/p/become-an-ai-pm-no-experience) — Breaking in from scratch
- [Full Roadmap: Become an AI PM](https://www.news.aakashg.com/p/ankit-shukla-podcast) — Step-by-step with HelloPM founder Ankit Shukla
- [The AI PM's Playbook](https://www.news.aakashg.com/p/ai-pm-playbook) — How top PMs are 10x-ing their impact

---

## AI PM Interview Prep

### Interview Mix (based on 100+ AI PM interviews)

| Category | % of Questions | Focus |
|----------|---------------|-------|
| **Behavioral: Leadership & Drive** | 40% | Handling stakeholders, past experiences |
| **Behavioral: AI Experience** | 25% | Actual AI PM work you've done |
| **Behavioral: Values & Culture** | 10% | Company-specific fit |
| **Case: Product Sense** | 5% | AI-specific product cases |
| **Case: Product Design** | 5% | "Design an AI device to communicate with pets" |
| **Case: Success Metrics** | 5% | AI feature metrics |
| **Technical: Deep Dive** | 5% | Architecture, model selection |
| **Technical: Strategy** | 5% | Cross-functional presence |

### Key Insight

75% of AI PM interviews are behavioral. The technical bar is lower than most candidates expect. The behavioral bar is higher — they want proof you've actually done AI PM work, not just studied it.

### Resources

- [The AI PM Interview: Your Complete Guide](https://www.news.aakashg.com/p/ai-pm-interview) — Full question-type analysis with guides for each category
- [The AI Product Design Interview Guide](https://www.news.aakashg.com/p/the-ai-product-design-interview-your) — Frameworks for the newest interview format
- [The AI Product Success Metrics Interview Guide](https://www.news.aakashg.com/p/ai-success-metrics-interview) — How to nail metrics questions
- [Master the AI Product Sense Interview](https://www.news.aakashg.com/p/ai-product-sense-interview) — 7 frameworks, 86 questions, strategies for $500K+ offers
- [OpenAI's Framework for AI Product Sense](https://www.news.aakashg.com/p/ai-product-sense) — How OpenAI's PM leaders think about product sense

---

## Essential Reading

### Books

| Book | Author | Why It Matters |
|------|--------|---------------|
| *Inspired* / *Empowered* / *Transformed* | Marty Cagan | Foundation of modern product management |
| *Build* | Tony Fadell | How products actually get built at scale |
| *The Lean Product Playbook* | Dan Olsen | Systematic approach to product-market fit |
| *Trustworthy Online Controlled Experiments* | Kohavi, Tang, Xu | The A/B testing bible |
| *Designing Machine Learning Systems* | Chip Huyen | Technical foundation for AI PMs |
| *AI Product Management* | Marily Nika | AI PM-specific frameworks |

### Newsletters

| Newsletter | Focus |
|-----------|-------|
| [Product Growth](https://www.news.aakashg.com) | AI product management, PM career, growth |
| [AI by Aakash](https://www.aibyaakash.com) | AI industry analysis |
| [Lenny's Newsletter](https://www.lennysnewsletter.com) | Product management and growth |
| [The Batch (Andrew Ng)](https://www.deeplearning.ai/the-batch/) | AI industry news |

### Podcasts

| Podcast | Focus |
|---------|-------|
| [The Growth Podcast](https://www.news.aakashg.com) | AI PM interviews and deep dives |
| Lenny's Podcast | Product leadership |
| Latent Space | AI engineering |
| Gradient Dissent (Weights & Biases) | ML in production |

---

## Tools and Platforms

### AI Development

| Tool | Category | PM Relevance |
|------|----------|-------------|
| **OpenAI API** | LLM provider | Most widely used, good for prototyping |
| **Anthropic Claude** | LLM provider | Strong at analysis and long documents |
| **Google Gemini** | LLM provider | Multimodal, integrated with Google ecosystem |
| **Hugging Face** | Model hub | Open source models for custom deployments |
| **LangChain / LlamaIndex** | Agent frameworks | Building AI pipelines and agents |

### PM-Specific AI Tools

| Tool | What It Does |
|------|-------------|
| **Cursor** | AI code editor for prototyping |
| **Claude Code** | Terminal AI for PM workflows |
| **NotebookLM** | Research and synthesis from your sources |
| **Gamma** | AI presentations and documents |
| **Granola** | AI meeting notes |
| **Amplitude / Mixpanel** | Product analytics with AI features |

---

## Contributing

Found a resource that should be here? Open a PR or issue.

---

Built and maintained by [Aakash Gupta](https://www.aakashg.com)

[Product Growth Newsletter](https://www.news.aakashg.com) | [The Growth Podcast](https://www.news.aakashg.com) | [LinkedIn](https://www.linkedin.com/in/aagupta)

## AI Ethics for PMs

### Why PMs Own This

Engineers build the system. PMs decide what the system should do. Every AI ethics issue traces back to a product decision: what data to use, what behavior to allow, what guardrails to set.

### Key Principles

- **Transparency**: Users should know when they're interacting with AI and what data it uses
- **Fairness**: Test for bias across user segments before launch, not after complaints
- **Privacy**: Collect only the data you need. Explain why you need it. Let users opt out.
- **Accountability**: When AI makes a mistake, the PM owns the communication and the fix
- **Human override**: Users should always be able to override or correct AI decisions

### Resources

- Google Responsible AI Practices — Practical guidelines for AI product teams
- Microsoft Responsible AI Standard — Framework used at enterprise scale
- AI Incident Database — Real examples of AI failures to learn from

## Communities

| Community | Platform | Focus |
|-----------|----------|-------|
| Product Growth | Newsletter | AI PM deep dives and career advice |
| Lenny's Community | Slack | General product management |
| AI Product Institute | Community | AI-specific PM resources |
| MLOps Community | Slack | ML engineering and operations |
| Latent Space | Discord | AI engineering and product |
| Product Hunt | Web | New AI product launches |
| r/ProductManagement | Reddit | PM discussions and career advice |

## Glossary

Essential AI terms every PM should know.

| Term | Definition | PM Relevance |
|------|-----------|-------------|
| **Fine-tuning** | Training a base model on domain-specific data | Expensive but improves quality. PM decides if it's worth the investment. |
| **RAG** | Pulling relevant documents into context before generating | Cheaper alternative to fine-tuning for knowledge-based features. |
| **Hallucination** | Model generating plausible but false information | Your #1 product risk. Design detection and mitigation. |
| **Embedding** | Numeric representation of text for similarity comparison | Powers search, recommendations, clustering features. |
| **Token** | Unit of text processing (~4 characters in English) | Directly affects cost and latency. Track usage per feature. |
| **Context window** | Maximum text the model can process at once | Determines what features are possible (e.g., summarizing long docs). |
| **Temperature** | Parameter controlling output randomness | Low = predictable (data extraction). High = creative (brainstorming). |
| **Inference** | Running a trained model to generate output | Your marginal cost per user interaction. |
| **Prompt engineering** | Crafting inputs to get desired outputs | The PM's primary tool for shaping AI behavior. |
| **Eval** | Automated test of AI output quality | Replaces manual QA for probabilistic systems. |
| **RLHF** | Training with human feedback to align behavior | How models learn to be helpful vs harmful. |
| **Multimodal** | Models that handle text, images, audio, video | Expands what AI features can do (image analysis, voice). |
| **Agent** | AI that can take actions (call APIs, execute code) | Shifts product from "tool" to "assistant." |
| **MCP** | Model Context Protocol — standard for connecting AI to tools | The new API standard. If your product doesn't support it, agents can't use it. |
| **Guardrails** | Rules constraining AI behavior | PMs define what the AI can/cannot do. |

## Case Studies

Real examples of AI product decisions and their outcomes.

### Notion AI
- **Decision**: Embed AI inline in the editor instead of a separate tool
- **Why it worked**: Zero context-switching. Users try it where they already write.
- **Lesson**: Inline > standalone for AI features that augment existing workflows.

### Cursor
- **Decision**: Tab-based code completion with multi-line predictions
- **Why it worked**: Matched the developer's existing flow (Tab to accept)
- **Challenge**: Power users burned through flat-rate plans. Had to switch to credit-based pricing.
- **Lesson**: Your best users will be your most expensive users in AI products.

### Canva Magic Studio
- **Decision**: AI features available on free tier with limited usage
- **Why it worked**: Bottom-up adoption. Free users upgrade after hitting limits.
- **Lesson**: Free AI features drive trial. Usage limits drive conversion.

### GitHub Copilot
- **Decision**: Side-panel chat + inline suggestions (two interaction modes)
- **Why it worked**: Different tasks need different interaction patterns
- **Lesson**: One AI interface doesn't fit all use cases. Design for the task, not the technology.

## Conferences

| Conference | Focus | When | Format |
|-----------|-------|------|--------|
| AI Product Summit | AI product management | Annual, Spring | In-person + Virtual |
| Mind the Product | Product management (AI track) | Multiple per year | In-person |
| ProductCon | PM community | Quarterly | Virtual |
| NeurIPS | ML/AI research | December | In-person |
| Google I/O | Google AI products | May | In-person + Virtual |
| AWS re:Invent | Cloud AI/ML services | November | In-person |
| Anthropic Sessions | Claude and AI safety | Periodic | Virtual |

## Courses

| Course | Provider | Focus | Level |
|--------|----------|-------|-------|
| AI Product Management | Pendo / Todd Olson | AI PM skills for working PMs | Intermediate |
| Product Management for AI | Duke (Coursera) | Foundation of AI PM | Beginner |
| Machine Learning for Product Managers | Pragmatic Institute | Technical foundations | Beginner |
| Full Stack Deep Learning | UC Berkeley | Building ML products end-to-end | Advanced |
| Reforge AI & ML for Product | Reforge | AI strategy for growth | Intermediate |
| LLM Bootcamp | The Full Stack | Building with LLMs | Intermediate |

## Weekly Reading List

A rotating selection of the best AI PM content. Updated regularly.

### Foundational
- [How to Build AI Products](https://www.news.aakashg.com) — Complete framework from problem to launch
- [AI Product Management is Different](https://www.news.aakashg.com) — Why traditional PM frameworks break with AI

### Current
- [How to Price AI Products](https://www.news.aakashg.com/p/how-to-price-ai-products) — 6 pricing models for AI
- [Context Engineering Guide](https://www.news.aakashg.com) — How to give AI the right information
- [AI Evals Explained](https://www.news.aakashg.com) — Testing AI outputs systematically

### Timeless
- [Andrej Karpathy: Software 2.0](https://karpathy.medium.com/software-2-0-a64152b37c35) — The original essay on neural net programming
- [Google's Rules of ML](https://developers.google.com/machine-learning/guides/rules-of-ml) — Still the best engineering guide for ML products
