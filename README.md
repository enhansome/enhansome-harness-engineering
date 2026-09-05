# Awesome Harness Engineering with stars

> A curated list of articles, playbooks, benchmarks, specifications, and open-source projects for harness engineering: the practice of shaping the environment around AI agents so they can work reliably.

Harness engineering sits at the intersection of context engineering, evaluation, observability, orchestration, safe autonomy, and software architecture. This list focuses on resources that make agents more dependable in real workflows, especially long-running coding and research tasks.

Generic agent tooling is out of scope unless the page directly covers harness design, context management, evaluation, runtime control, or other reliability-critical harness primitives.

## Contents

* [Courses & Learning Resources](#courses--learning-resources)
* [Foundations](#foundations)
* [Context, Memory & Working State](#context-memory--working-state)
  * [Context Design & Delivery](#context-design--delivery)
  * [Memory & Knowledge Systems](#memory--knowledge-systems)
* [Constraints, Guardrails & Safe Autonomy](#constraints-guardrails--safe-autonomy)
  * [Tool Design & Execution Boundaries](#tool-design--execution-boundaries)
  * [Security, Authorization & Policy](#security-authorization--policy)
  * [Operational Autonomy & Reliability](#operational-autonomy--reliability)
* [Specs, Agent Files & Workflow Design](#specs-agent-files--workflow-design)
  * [Instruction Files & Formats](#instruction-files--formats)
  * [Spec-Driven Development](#spec-driven-development)
  * [Operating Principles & Human Oversight](#operating-principles--human-oversight)
* [Evals & Observability](#evals--observability)
  * [Evaluation Design](#evaluation-design)
  * [Verification & Quality Gates](#verification--quality-gates)
  * [Telemetry, Tracing & Performance](#telemetry-tracing--performance)
* [Benchmarks](#benchmarks)
  * [Coding & Terminal Agents](#coding--terminal-agents)
  * [Web, GUI & Computer Use](#web-gui--computer-use)
  * [Tools, APIs & MCP](#tools-apis--mcp)
  * [Multi-Agent, General & Interactive](#multi-agent-general--interactive)
  * [Safety, Robustness & Economic Agency](#safety-robustness--economic-agency)
* [Runtimes, Harnesses & Reference Implementations](#runtimes-harnesses--reference-implementations)
  * [Runtime Foundations & Control Layers](#runtime-foundations--control-layers)
  * [Sandboxes & Execution Infrastructure](#sandboxes--execution-infrastructure)
  * [Coding-Agent Harnesses](#coding-agent-harnesses)
  * [Multi-Agent Orchestration](#multi-agent-orchestration)
  * [Browser, MCP & Tool Integration](#browser-mcp--tool-integration)
  * [Workflow, Profiles & Asset Management](#workflow-profiles--asset-management)
* [Contributing](#contributing)
* [License](#license)

## Courses & Learning Resources

* [walkinglabs/learn-harness-engineering](https://github.com/walkinglabs/learn-harness-engineering) ⭐ 14,838 | 🐛 11 | 🌐 TypeScript | 📅 2026-08-26 - A project-based course repository on making Codex and Claude Code more reliable, centered on an Electron personal knowledge base app with lecture handouts, example artifacts, and practical harness projects.
* [hardness1020/awesome-agent-architecture](https://github.com/hardness1020/awesome-agent-architecture) ⭐ 851 | 🐛 5 | 🌐 Python | 📅 2026-08-28 - Trilingual architecture notes and runnable demos covering agent loops, tool execution, memory, permissions, context delivery, and orchestration.
* [Phelan164/codex-howto](https://github.com/Phelan164/codex-howto) ⭐ 3 | 🐛 4 | 🌐 Python | 📅 2026-09-04 - A Codex-focused engineering curriculum with installable skills, repository instructions, scoped permissions, testing, review, orchestration, and reproducible token measurements for building an inspectable coding-agent harness.

## Foundations

<!-- FIXME: 403 Forbidden — - [Agent Harness for Large Language Model Agents: A Survey](https://www.preprints.org/manuscript/202604.0428) - A survey that formalizes, taxonomizes, and frames harness design for long-running LLM agents as a distinct research area. -->

* [Harness engineering: leveraging Codex in an agent-first world](https://openai.com/index/harness-engineering/) - OpenAI's flagship field report on building a large application with Codex using architectural constraints, repo-local instructions, browser validation, and telemetry.
* [Effective harnesses for long-running agents](https://www.anthropic.com/engineering/effective-harnesses-for-long-running-agents) - Anthropic's core article on initializer agents, feature lists, `init.sh`, self-verification, and handoff artifacts across many context windows.
* [Harness design for long-running application development](https://www.anthropic.com/engineering/harness-design-long-running-apps) - Anthropic follow-up focused on improving long-running app generation with better task state and evaluator design.
* [The Anatomy of an Agent Harness](https://blog.langchain.com/the-anatomy-of-an-agent-harness/) - LangChain's concise framing of an agent as model plus harness, with prompts, tools, middleware, orchestration, and runtime infrastructure.
* [Harness Engineering](https://martinfowler.com/articles/exploring-gen-ai/harness-engineering.html) - Thoughtworks' framing of harness work into context engineering, architectural constraints, and "garbage collection" against entropy.
* [Building effective agents](https://www.anthropic.com/engineering/building-effective-agents) - Anthropic's broader guide to workflows, agents, tools, and when structured systems outperform raw prompting.
* [Skill Issue: Harness Engineering for Coding Agents](https://www.humanlayer.dev/blog/skill-issue-harness-engineering-for-coding-agents) - A practical argument that weak results from coding agents are often harness problems rather than model problems.
* [Your Agent Needs a Harness, Not a Framework](https://www.inngest.com/blog/your-agent-needs-a-harness-not-a-framework) - Inngest's case for treating state, retries, traces, and concurrency as first-class infrastructure.
* [Greenfield AI, Brownfield AI, and the Vibecode You Just Inherited](https://sawinyh.com/blog/greenfield-vs-brownfield-ai-codebases) - A three-way taxonomy of codebases agents encounter — agent-native greenfield, true legacy brownfield, and recently-vibecoded inheritance — with playbooks for installing layered `CLAUDE.md` rules, ratcheted pre-commit hooks, baselined lint violations, and feature-folder refactors so the codebase itself stops being the harness bottleneck.
* [Harness Engineering for Language Agents: The Harness Layer as Control, Agency, and Runtime](https://www.preprints.org/manuscript/202603.1756) - A position paper that treats the harness layer as a first-class research object, proposes the **control–agency–runtime (CAR)** decomposition, and introduces **HarnessCard** for structured reporting of harness design and evaluation.
* [Many Hands Engineering](https://github.com/mseeks/many-hands-engineering/blob/main/many-hands-engineering.pdf) ⭐ 3 | 🐛 0 | 🌐 Typst | 📅 2026-06-13 - A handbook framing the layer above the per-agent harness: how multiple harnessed agents share a commons, where decisions belong on a planned / emergent spectrum, and how human stewardship operates at a different cadence than agent execution. Treats harness engineering as a critical layer of "terrain" the framework sits on top of.
* [Agent Frameworks, Runtimes, and Harnesses, Oh My!](https://blog.langchain.com/agent-frameworks-runtimes-and-harnesses-oh-my/) - LangChain's decomposition of what belongs in a framework, a runtime, and a harness.

## Context, Memory & Working State

### Context Design & Delivery

* [DevProjex](https://github.com/Avazbek22/DevProjex) ⭐ 20 | 🐛 14 | 🌐 C# | 📅 2026-09-05 - GUI, TUI, and CLI tooling for selecting and exporting structured codebase context with folder trees, token estimates, ignore rules, and previews.
* [Deterministic Context Routing](https://github.com/ai-erp-collab/deterministic-context-routing) ⭐ 1 | 🐛 0 | 📅 2026-07-24 - A context-management methodology that routes only the necessary-and-sufficient context to an agent through a deterministic chain (module registry → wiki → session state), cutting overread and context loss on large, under-documented multi-module codebases.
* [Effective context engineering for AI agents](https://www.anthropic.com/engineering/effective-context-engineering-for-ai-agents) - Anthropic's guidance on managing the context window as a working memory budget rather than a dumping ground.
* [Context Engineering for AI Agents: Lessons from Building Manus](https://manus.im/blog/Context-Engineering-for-AI-Agents-Lessons-from-Building-Manus) - Manus' detailed playbook on KV-cache locality, tool masking, filesystem memory, and keeping useful failures in-context.
* [Context Engineering for Coding Agents](https://martinfowler.com/articles/exploring-gen-ai/context-engineering-coding-agents.html) - Thoughtworks guidance on shaping the task environment so coding agents can stay grounded and productive.
* [Advanced Context Engineering for Coding Agents](https://www.humanlayer.dev/blog/advanced-context-engineering) - HumanLayer patterns for reducing context drift and making coding sessions easier to resume.
* [Context-Efficient Backpressure for Coding Agents](https://www.humanlayer.dev/blog/context-efficient-backpressure) - HumanLayer's ideas for preventing agents from burning context on noisy or low-value work.
* [OpenHands Context Condensensation for More Efficient AI Agents](https://openhands.dev/blog/openhands-context-condensensation-for-more-efficient-ai-agents) - OpenHands' design for bounded conversation memory that preserves goals, progress, critical files, and failing tests while keeping long-running coding sessions efficient.
* [Writing a good CLAUDE.md](https://www.humanlayer.dev/blog/writing-a-good-claude-md) - A practical guide to creating durable, repo-local instructions that agents can repeatedly follow.

### Memory & Knowledge Systems

* [OpenViking](https://github.com/volcengine/OpenViking) ⭐ 35,622 | 🐛 632 | 🌐 Python | 📅 2026-09-05 - Context database that unifies agent memory, knowledge retrieval, and skills behind an MCP-accessible storage layer.
* [wiki](https://github.com/plasma-ai/wiki) ⭐ 82 | 🐛 1 | 🌐 Python | 📅 2026-09-04 - Indexed Markdown knowledge bases that give agents incremental project context through deterministic indexes, scoped CLI access, and merge handling for parallel edits.
* [Data Olympus](https://github.com/knaisoma/data-olympus) ⭐ 23 | 🐛 29 | 🌐 Python | 📅 2026-09-05 - Git-native project knowledge base and MCP server with governed proposal-to-acceptance workflows, validity windows, supersession chains, and retrieval of in-force engineering guidance.

## Constraints, Guardrails & Safe Autonomy

### Tool Design & Execution Boundaries

* [mcp-guardian](https://github.com/S1LV3RJ1NX/mcp-guardian) ⭐ 0 | 🐛 0 | 🌐 Python | 📅 2026-07-14 - MCP proxy for progressive tool discovery, scope-based allow/block lists, and audit logging, reducing startup context while preventing blocked tools from being discovered or called.
* [Code execution with MCP: building more efficient agents](https://www.anthropic.com/engineering/code-execution-with-mcp) - Anthropic's approach to giving agents controlled execution power through explicit, inspectable tool boundaries.
* [Writing effective tools for agents](https://www.anthropic.com/engineering/writing-tools-for-agents) - Anthropic's guidance on tool interfaces that are easier for models to call correctly and safely.

### Security, Authorization & Policy

* [APort Agent Guardrails](https://github.com/aporthq/aport-agent-guardrails) ⭐ 25 | 🐛 1 | 🌐 Shell | 📅 2026-09-04 - Deterministic pre-action authorization hooks for AI-agent tool calls, with adapters for Claude Code, Cursor, OpenClaw, LangChain, CrewAI, and related runtimes.
* [Lurkr](https://github.com/agentveil-protocol/lurkr) ⭐ 6 | 🐛 0 | 🌐 Python | 📅 2026-06-01 - Static scanner that runs in CI before deploy to surface AI-agent capability risks, including shadow capabilities, credentials into LLM context, eval/subprocess in `@tool`, direct prompt interpolation, and unverified MCP endpoints.
* [HEAAL](https://github.com/hyun06000/AIL) ⭐ 2 | 🐛 0 | 🌐 Rust | 📅 2026-08-04 - Grammar-enforced safety constraints for AI agents via AIL (AI-Intent Language).
* [Beyond permission prompts: making Claude Code more secure and autonomous](https://www.anthropic.com/engineering/claude-code-sandboxing) - Anthropic on reducing approval friction without losing control through better sandboxing and policy design.
* [Mitigating Prompt Injection Attacks in Software Agents](https://openhands.dev/blog/mitigating-prompt-injection-attacks-in-software-agents) - OpenHands' practical guide to confirmation mode, analyzers, sandboxing, and hard policies for reducing prompt-injection risk in autonomous coding agents.

### Operational Autonomy & Reliability

* [Spend rails for autonomous agents: a number, not a vibe](https://joeyycli.github.io/agent-ops-kit-guide/docs/spend-rails-for-autonomous-agents.html) - A concrete pattern for giving a scheduled agent real purchasing authority without real risk: a per-transaction autonomy line, an escalation threshold, a hard lifetime ceiling, and a transaction ledger as the actual enforcement mechanism instead of relying on the model's judgment.
* [Distributed retry patterns: bounding blast radius across a fleet](https://loopandretry.github.io/posts/fleet-retry-patterns/) - Practitioner guidance on concurrency bounds, decorrelated backoff, circuit breakers, and idempotency for preventing agent retry storms.

## Specs, Agent Files & Workflow Design

### Instruction Files & Formats

* [AGENTS.md](https://github.com/agentsmd/agents.md) ⭐ 24,149 | 🐛 169 | 🌐 TypeScript | 📅 2026-08-25 - A lightweight open format for repo-local instructions that tell agents how to work inside a codebase.
* [agent.md](https://github.com/agentmd/agent.md) ⭐ 90 | 🐛 3 | 📅 2025-07-10 - A related standardization effort for machine-readable agent instructions across projects and tools.

### Spec-Driven Development

* [GitHub Spec Kit](https://github.com/github/spec-kit) ⭐ 133,575 | 🐛 313 | 🌐 Python | 📅 2026-09-04 - GitHub's toolkit for spec-driven development, useful when you want agents to execute against explicit product and engineering specs.
* [Context Repository-Driven Development (CRDD)](https://github.com/qual-lab/CRDD) ⭐ 0 | 🐛 0 | 🌐 TypeScript | 📅 2026-09-05 - A repository-centered methodology for preserving product intent, decisions, specifications, evidence, and traceability as durable context while keeping approval authority with humans.
* [Understanding Spec-Driven-Development: Kiro, spec-kit, and Tessl](https://martinfowler.com/articles/exploring-gen-ai/sdd-3-tools.html) - Thoughtworks on why strong specs make AI-assisted software delivery more dependable.

### Operating Principles & Human Oversight

* [12 Factor Agents](https://www.humanlayer.dev/blog/12-factor-agents) - HumanLayer's operating principles for production agents, including explicit prompts, state ownership, and clean pause-resume behavior.
* [12-Factor AgentOps](https://www.12factoragentops.com/) - An operations-oriented companion focused on context discipline, validation, and reproducible agent workflows.
* [Anchoring AI to a reference application](https://martinfowler.com/articles/exploring-gen-ai/anchoring-to-reference.html) - Thoughtworks on constraining agents with concrete exemplars so they produce more consistent output.
* [Humans and Agents in Software Engineering Loops](https://martinfowler.com/articles/exploring-gen-ai/humans-and-agents.html) - A clear mental model for where humans should strengthen the harness instead of micromanaging every artifact.
* [Claude Code: Best practices for agentic coding](https://code.claude.com/docs) - Anthropic's practical recommendations for repo structure, checkpoints, validation, and delegation in agentic coding workflows.

## Evals & Observability

### Evaluation Design

* [Testing Agent Skills Systematically with Evals](https://developers.openai.com/blog/eval-skills/) - OpenAI's concrete guide to turning agent traces into repeatable evals with JSONL logs and deterministic checks.
* [How to Evaluate Agent Skills (And Why You Should)](https://openhands.dev/blog/evaluating-agent-skills) - OpenHands' hands-on playbook for measuring whether a skill actually helps using bounded tasks, deterministic verifiers, no-skill baselines, and trace review.
* [Agent evals](https://platform.openai.com/docs/guides/agent-evals) - OpenAI's product guide for measuring agent quality with reproducible task-level and workflow-level evaluations.
* [Evaluation best practices](https://platform.openai.com/docs/guides/evaluation-best-practices) - OpenAI's general guide to building eval suites that match real-world distributions and catch regressions early.
* [Trace grading](https://platform.openai.com/docs/guides/trace-grading) - OpenAI documentation on grading agent traces directly, which is especially helpful for long multi-step tasks.
* [Inspect AI](https://inspect.aisi.org.uk/) - UK AISI's open-source evaluation framework with solver, scorer, sandboxing, tool-use, MCP, and log-viewer primitives for building reproducible agent eval harnesses.
* [Demystifying Evals for AI Agents](https://www.anthropic.com/engineering/demystifying-evals-for-ai-agents) - Anthropic's guidance on what to measure when agents have many possible trajectories to success or failure.
* [Evaluating Deep Agents: Our Learnings](https://blog.langchain.com/evaluating-deep-agents-our-learnings/) - LangChain's practical breakdown of single-step, full-run, and multi-turn eval design for stateful agents.

### Verification & Quality Gates

* [Better Harness](https://github.com/QoderAI/better-harness) ⭐ 2,168 | 🐛 5 | 🌐 JavaScript | 📅 2026-09-04 - Reviewer for coding-agent workflows that turns repository and session evidence into prioritized, verifiable harness improvements while keeping unobserved behavior explicit.
* [Assessing internal quality while coding with an agent](https://martinfowler.com/articles/exploring-gen-ai/ccmenu-quality.html) - Thoughtworks on moving quality checks into the loop instead of relying on after-the-fact manual review.
* [Learning to Verify AI-Generated Code](https://openhands.dev/blog/20260305-learning-to-verify-ai-generated-code) - OpenHands' overview of a layered verification stack using trajectory critics trained on production traces for reranking, early stopping, and review-time quality control.
* [Improving Deep Agents with harness engineering](https://blog.langchain.com/improving-deep-agents-with-harness-engineering/) - LangChain's evidence that harness changes alone can significantly improve benchmark performance.

### Telemetry, Tracing & Performance

* [AgentOps](https://github.com/AgentOps-AI/agentops) ⭐ 5,808 | 🐛 177 | 🌐 Python | 📅 2026-06-25 - Open-source Python SDK for agent monitoring, session replay, cost tracking, benchmarking, and tracing across common LLM and agent frameworks.
* [agenttrace](https://github.com/luoyuctl/agenttrace) ⭐ 129 | 🐛 7 | 🌐 Rust | 📅 2026-08-24 - Local-first TUI/CLI for auditing AI coding-agent session traces, health gates, cost spikes, tool failures, latency gaps, and attempt-to-attempt diffs.
* [ax](https://github.com/Necmttn/ax) ⭐ 104 | 🐛 38 | 🌐 TypeScript | 📅 2026-09-05 - Local-first telemetry and memory graph for auditing coding-agent sessions, costs, skills, tool usage, and OTLP events across multiple agent runtimes.
* [flameox](https://github.com/morluto/flameox) ⭐ 93 | 🐛 1 | 🌐 Python | 📅 2026-09-05 - Profiling and optimization toolkit for agents: bounded CLI and MCP workflows capture traces, preserve native evidence, and compare experiments behind runtime conclusions.
* [OpenTelemetry Semantic Conventions for Generative AI Systems](https://opentelemetry.io/docs/specs/semconv/gen-ai/) - Standard span, metric, event, and attribute conventions for instrumenting LLM and agent workflows so harness traces stay portable across observability backends.
* [Quantifying infrastructure noise in agentic coding evals](https://www.anthropic.com/engineering/infrastructure-noise) - Anthropic on how runtime configuration can move coding benchmark scores by more than many leaderboard gaps.

## Benchmarks

These benchmarks are especially useful when you want to compare harness quality, not just model quality. They stress context handling, tool calling, environment control, verification logic, and the runtime scaffolding around the model.

### Coding & Terminal Agents

* [LeetCode-Hard Gym](https://github.com/GammaTauAI/leetcode-hard-gym) ⭐ 172 | 🐛 4 | 🌐 Python | 📅 2024-07-07 - An RL environment interface to LeetCode's submission server for evaluating codegen agents, giving harnesses direct access to execution-based feedback on hard algorithmic problems.
* [SEC-bench](https://github.com/SEC-bench/SEC-bench) ⭐ 95 | 🐛 3 | 🌐 Python | 📅 2026-01-27 - A benchmark for evaluating LLM agents on real-world software security tasks including vulnerability reproduction and patching, stressing harness design around code execution, containerized environments, and security-aware tooling.
* [EvoClaw: Evaluating AI Agents on Continuous Software Evolution](https://openhands.dev/blog/evoclaw-benchmark) - A benchmark write-up on evaluating agents across dependent milestone sequences from real repository history, surfacing regression accumulation and long-horizon precision loss.
* [Introducing Terminal-Bench 2.0 and Harbor](https://www.tbench.ai/news/announcement-2-0) - The Terminal-Bench 2.0 announcement, useful for understanding the harder tasks and generalized evaluation harness behind Harbor.
* [SWE-bench Verified](https://www.swebench.com/) - A strong benchmark for software engineering agents working against real GitHub issues and tests, which makes harness choices around retrieval, patching, and validation highly visible.
* [Terminal-Bench](https://www.tbench.ai/) - A benchmark suite for terminal-native agents operating in shells, filesystems, and verification-heavy environments, which is especially useful for comparing coding-agent harnesses.

### Web, GUI & Computer Use

* [VAB](https://github.com/THUDM/VisualAgentBench) ⭐ 276 | 🐛 17 | 🌐 Python | 📅 2025-04-24 - VisualAgentBench evaluates large multimodal models as visual foundation agents across embodied, GUI, and visual design tasks, useful for comparing harnesses on visually grounded, multi-step agent workflows.
* [WorkArena](https://github.com/ServiceNow/WorkArena) ⭐ 270 | 🐛 25 | 🌐 Python | 📅 2026-04-25 - A benchmark for browser agents on common knowledge-work tasks, useful for comparing harnesses on realistic enterprise-style web workflows instead of toy browser tasks.
* [AssistantBench](https://github.com/oriyor/AssistantBench) ⭐ 72 | 🐛 0 | 🌐 Python | 📅 2024-12-09 - A benchmark that evaluates web agents on realistic, time-consuming research tasks requiring multi-step tool use and information synthesis, making it a good proxy for harness quality in long-horizon web scenarios.
* [Computer Agent Arena](https://github.com/xlang-ai/computer-agent-arena) ⭐ 67 | 🐛 2 | 🌐 HTML | 📅 2026-02-26 - An open evaluation platform where users compare LLM/VLM-based agents on real-world computer tasks ranging from general computer use to coding, data analysis, and video editing, surfacing harness differences across a wide task surface.
* [WebArena-Verified](https://github.com/ServiceNow/webarena-verified) ⭐ 54 | 🐛 13 | 🌐 Python | 📅 2026-03-08 - A verified web-agent benchmark with curated tasks and deterministic evaluators over agent responses and captured network traces, making it a good fit for measuring web-facing harnesses.
* [AgentStudio](https://github.com/SkyworkAI/agent-studio) ⭐ 18 | 🐛 0 | 🌐 Python | 📅 2024-12-03 - An integrated benchmark suite with realistic environments and comprehensive toolkits for evaluating virtual agents on real computer software, useful for measuring harness depth against a broad task surface.
* [BrowseComp](https://www.kaggle.com/benchmarks/openai/browsecomp) - A benchmark that evaluates AI agents on locating hard-to-find information, stressing search strategy, context management, and retrieval harness design under difficult conditions.
* [BrowserGym Leaderboard](https://huggingface.co/spaces/ServiceNow/browsergym-leaderboard) - A gym environment and leaderboard for evaluating LLMs, VLMs, and agents on web navigation tasks, offering a reproducible framework for comparing harnesses across multiple web benchmarks in one place.
* [ClawBench: Can AI Agents Complete Everyday Online Tasks?](https://huggingface.co/papers/2604.08523) - A browser-agent benchmark of 153 everyday web tasks across 144 live production sites in 15 categories, using a lightweight interception layer that captures and blocks only the final submission request so agents can be scored end-to-end on real websites without real-world side effects.
* [OSWorld](https://os-world.github.io/) - A real computer-use benchmark with 369 tasks across Ubuntu, Windows, and macOS, complete with initial-state setup and execution-based evaluators, making it excellent for testing desktop and multimodal harnesses.
* [OSWorld-MCP](https://osworld-mcp.github.io) - An extension of OSWorld that evaluates AI agents on real-world computer tasks using the Model Context Protocol, making it useful for comparing MCP-enabled harnesses on a realistic desktop task suite.
* [VisualWebArena](https://jykoh.com/vwa) - A benchmark for multimodal web agents on realistic visually grounded tasks, extending WebArena with image and screenshot inputs that stress harness support for visual context in browser environments.
* [WebArena](https://webarena.dev/) - A standalone, self-hostable web environment for evaluating autonomous agents on realistic tasks, making it a reproducible baseline for comparing web-facing harness designs.

### Tools, APIs & MCP

* [AgentBench](https://github.com/THUDM/AgentBench) ⭐ 3,713 | 🐛 76 | 🌐 Python | 📅 2026-02-08 - A cross-environment benchmark spanning OS, databases, knowledge graphs, web browsing, and more, useful for seeing whether a harness generalizes beyond one narrow task loop.
* [tau2-bench](https://github.com/sierra-research/tau2-bench) ⭐ 1,954 | 🐛 189 | 🌐 Python | 📅 2026-09-04 - A benchmark for realistic, multi-step agent tasks where success depends on tool use and execution quality rather than a single-shot answer.
* [τ-Bench](https://github.com/sierra-research/tau-bench) ⭐ 1,422 | 🐛 53 | 🌐 Python | 📅 2026-03-18 - A benchmark that emulates dynamic conversations between a simulated user and a language agent equipped with domain-specific API tools and policy guidelines, making it useful for evaluating harnesses built around structured tool use and policy enforcement.
* [TravelPlanner](https://github.com/OSU-NLP-Group/TravelPlanner) ⭐ 544 | 🐛 2 | 🌐 Python | 📅 2026-05-24 - A benchmark for evaluating LLM agents on tool use and complex planning within multiple constraints, revealing how harness design handles multi-constraint satisfaction and long-horizon planning.
* [MCPMark](https://github.com/eval-sys/mcpmark) ⭐ 460 | 🐛 21 | 🌐 Python | 📅 2026-06-12 - A stress-testing benchmark for model and agent capabilities in real-world MCP tasks across tools like Notion, GitHub, and Postgres, making harness MCP integration quality directly measurable.
* [MCP Bench](https://github.com/modelscope/MCPBench) ⭐ 251 | 🐛 6 | 🌐 Python | 📅 2025-09-03 - A benchmark for evaluating AI models on MCP server interactions, measuring tool accuracy, latency, and token use across server types, which directly reflects harness design choices around MCP integration.
* [GTA](https://github.com/open-compass/GTA) ⭐ 152 | 🐛 1 | 🌐 Python | 📅 2026-04-20 - A benchmark that evaluates the tool-use capability of LLM-based agents using human-written queries, real deployed tools, and authentic multimodal inputs, exposing harness gaps between isolated testing and real deployment.
* [AppWorld](https://appworld.dev/) - A controllable world of apps and people for benchmarking interactive coding agents, with state-based and execution-based unit tests that surface harness quality around planning, code generation, and collateral-damage control.
* [MCP Universe](https://mcp-universe.github.io/) - A leaderboard comparing AI model performance on MCP tasks, tracking how different models and harness configurations handle tool-augmented agent workflows.

### Multi-Agent, General & Interactive

* [LLM Colosseum Leaderboard](https://github.com/OpenGenerativeAI/llm-colosseum) ⭐ 1,483 | 🐛 16 | 🌐 Jupyter Notebook | 📅 2025-03-21 - A platform that evaluates LLMs by having them fight in Street Fighter III, testing speed, adaptability, and real-time decision-making as proxies for harness responsiveness under tight latency constraints.
* [WildClawBench](https://github.com/InternLM/WildClawBench) ⭐ 516 | 🐛 4 | 🌐 Python | 📅 2026-08-17 - An in-the-wild benchmark running agents inside a live OpenClaw environment on 60 original tasks including multimodal, long-horizon, and safety-critical scenarios, making harness robustness under real-world conditions directly visible.
* [AgentBoard](https://github.com/HKUST-NLP/AgentBoard) ⭐ 444 | 🐛 17 | 🌐 SAS | 📅 2024-05-20 - A benchmark for multi-turn LLM agents complemented by an analytical evaluation board for assessing model performance beyond final success rates, making partial-progress and trajectory quality visible.
* [CharacterEval](https://github.com/morecry/CharacterEval) ⭐ 303 | 🐛 27 | 🌐 Python | 📅 2025-05-27 - A benchmark for evaluating role-playing conversational agents using multi-turn dialogues and character profiles, with metrics across four dimensions including character fidelity and conversational coherence.
* [Agent Arena](https://www.agent-arena.com/leaderboard) - A leaderboard that ranks AI agents, models, tools, and frameworks using ELO-style ratings from head-to-head battles, providing a structured way to compare harness-level choices across categories.
* [ClawBench](https://clawbench.net) - A benchmark that evaluates AI agents across search, reasoning, coding, safety, and multi-turn conversation tasks, covering the breadth of harness demands in a single suite.
* [GAIA](https://huggingface.co/datasets/gaia-benchmark/GAIA) - A benchmark for general AI assistants that is often used to compare harness-level choices around tools, planning, verification, and long-horizon autonomy.
* [Galileo Agent Leaderboard](https://huggingface.co/spaces/galileo-ai/agent-leaderboard) - An open evaluation platform tracking LLM agents on task completion and tool calling across business domains, useful for comparing harness quality in enterprise-grade agentic scenarios.
* [HAL: Holistic Agent Leaderboard](https://hal.cs.princeton.edu/) - A benchmark and leaderboard for agent systems with attention to reliability, cost, and broad task coverage, making it useful for comparing end-to-end harness behavior.
* [MAgIC](https://zhiyuanhubj.github.io/MAgIC/) - A benchmark measuring cognition, adaptability, rationality, and collaboration of LLMs in multi-agent systems, useful for evaluating how harnesses coordinate agent interactions and shared state.

### Safety, Robustness & Economic Agency

* [ClawWork](https://github.com/HKUDS/ClawWork) ⭐ 8,537 | 🐛 38 | 🌐 Python | 📅 2026-03-03 - A real-world economic benchmark where AI agents complete professional tasks spanning 44 occupations, earning income while managing token costs and economic solvency, making it a direct test of harness efficiency under resource constraints.
* [Olas Predict Benchmark](https://github.com/valory-xyz/olas-predict-benchmark) ⚠️ Archived - A benchmark for evaluating agents on historical prediction market data, testing harness design for research, retrieval, and forecasting in long-horizon reasoning tasks.

## Runtimes, Harnesses & Reference Implementations

### Runtime Foundations & Control Layers

* [AgentKit](https://github.com/inngest/agent-kit) ⭐ 926 | 🐛 49 | 🌐 TypeScript | 📅 2026-04-29 - Inngest's TypeScript toolkit for building durable, workflow-aware agents on top of event-driven infrastructure.
* [SandBase Harness](https://github.com/sandbaseai/sandbase-harness) ⭐ 642 | 🐛 11 | 🌐 TypeScript | 📅 2026-08-31 - Apache-2.0 agent runtime with persistent sessions, governed MCP tools, credential handling, audit and replay, and interchangeable local or sandboxed execution backends.
* [BitRouter](https://github.com/bitrouter/bitrouter) ⭐ 223 | 🐛 31 | 🌐 Rust | 📅 2026-09-05 - Apache-2.0 model router with cross-protocol routing, MCP gateway, guardrails, observability, virtual keys, and multi-account failover.
* [DSH Studio](https://github.com/Moresyl/dsh-studio) ⭐ 24 | 🐛 0 | 🌐 Rust | 📅 2026-08-29 - Cross-platform desktop host for DeepSeek Harness with health probes, restart backoff, collision-free ports, and whole-process-tree cleanup.
* [rust-norion](https://github.com/yanghao1143/rust-norion) ⭐ 18 | 🐛 3 | 🌐 Rust | 📅 2026-07-16 - GPL-3.0 Rust inference-control prototype exploring runtime boundaries, governed memory and replay, evidence-based writer gates, audit traces, and rollback for self-evolving agent systems.
* [Building agents with the Claude Agent SDK](https://claude.com/blog/building-agents-with-the-claude-agent-sdk) - Anthropic's guide to a production-oriented agent SDK with sessions, tools, and orchestration support.

### Sandboxes & Execution Infrastructure

* [Harbor](https://github.com/harbor-framework/harbor) ⭐ 4,966 | 🐛 817 | 🌐 Python | 📅 2026-09-05 - A generalized harness for evaluating and improving agents at scale, released alongside Terminal-Bench 2.0.
* [SWE-ReX](https://github.com/SWE-agent/SWE-ReX) ⭐ 583 | 🐛 56 | 🌐 Python | 📅 2026-08-31 - Sandboxed code execution infrastructure for AI agents, useful when harness work starts to merge into execution runtime design.
* [Mitos](https://github.com/mitos-run/mitos) ⭐ 89 | 🐛 72 | 🌐 Go | 📅 2026-07-18 - Snapshot-fork microVM sandboxes that give agent sessions clean, isolated starting states with declarative lifecycle control and parallel execution.

### Coding-Agent Harnesses

* [deepagents](https://github.com/langchain-ai/deepagents) ⭐ 29,021 | 🐛 182 | 🌐 Python | 📅 2026-09-05 - LangChain's open-source project for building deeper, longer-running agents with middleware and harness patterns.
* [SWE-agent](https://github.com/SWE-agent/SWE-agent) ⭐ 20,227 | 🐛 98 | 🌐 Python | 📅 2026-08-31 - A mature research coding agent that makes the harness, prompt, tools, and environment design directly inspectable.
* [Citadel](https://github.com/SethGammon/Citadel) ⭐ 916 | 🐛 1 | 🌐 JavaScript | 📅 2026-09-03 - A harness for Claude Code and OpenAI Codex with isolated worktrees, multi-agent coordination, and persisted memory and campaign state.
* [LoopTroop](https://github.com/looptroop-ai/LoopTroop) ⭐ 130 | 🐛 3 | 🌐 TypeScript | 📅 2026-09-05 - Local-first GUI harness for long-running coding work with multi-model planning, isolated worktrees, and fresh-context recovery loops.
* [OpenCode Agent Orchestration Kit](https://github.com/jcarlosrodicio/opencode-agent-orchestration-kit) ⭐ 107 | 🐛 5 | 🌐 JavaScript | 📅 2026-09-04 - Reproducible OpenCode harness with role-based agents, explicit handoffs, repo-local skills, safe installation, and mechanical contract validation.
* [Agent AFK](https://github.com/griffinwork40/agent-afk) ⭐ 53 | 🐛 11 | 🌐 TypeScript | 📅 2026-09-05 - Headless coding-agent harness for asynchronous runs with explicit terminal states, editable lifecycle hooks, permission gates, model routing, and append-only traces.
* [Harness Evolver](https://github.com/raphaelchristi/harness-evolver) ⭐ 49 | 🐛 4 | 🌐 Python | 📅 2026-04-18 - Claude Code plugin that autonomously evolves LLM agent harnesses using multi-agent proposers, LangSmith-backed evaluation, and git worktree isolation. Based on Meta-Harness (Lee et al., 2026).
* [forge-harness](https://github.com/chrono-meta/forge-harness) ⭐ 14 | 🐛 3 | 🌐 Shell | 📅 2026-09-05 - Claude Code plugin for adversarial validation, source-grounding audits, session-learning capture, and pre-deployment transfer simulation.
* [completely](https://github.com/23ag1/completely) ⭐ 5 | 🐛 0 | 🌐 Shell | 📅 2026-06-11 - Claude Code plugin harness with a default-fail evaluator, deterministic write and close gates, orphan recovery, and parallel-worker integration checks.
* [RailWarden](https://github.com/advaith-1212/railwarden) ⭐ 2 | 🐛 0 | 🌐 Python | 📅 2026-08-04 - Deterministic control plane for multi-agent software work with dependency-aware packages, isolated worktrees, durable validation evidence, recovery checkpoints, and integration gates.
* [Ralph Wiggum as a Software Engineer](https://ghuntley.com/ralph/) - Geoffrey Huntley's write-up of "Ralph," a minimalist `while :; do cat PROMPT.md | claude-code; done` harness pattern that uses single-task loops, deterministic prompt stacking, and bounded subagent parallelism to drive long-running autonomous coding.

### Multi-Agent Orchestration

* [Orkas](https://github.com/Orkas-AI/Orkas) ⭐ 1,723 | 🐛 13 | 🌐 TypeScript | 📅 2026-09-05 - Local-first desktop harness for coordinating multiple agents with shared files, independent work contexts, human approval gates, and resumable execution.
* [Agentlas OS](https://github.com/agentlas-ai/Agentlas-OS) ⭐ 1,101 | 🐛 1 | 🌐 Python | 📅 2026-09-05 - Local-first agent operation environment that composes specialist teams while retaining host-local tools, permissions, memory boundaries, and verification rules.
* [Cowork Forge](https://github.com/sopaco/cowork-forge) ⭐ 92 | 🐛 0 | 🌐 Rust | 📅 2026-08-25 - MIT-licensed multi-agent software-development workflow with specialized roles and a staged pipeline from requirements through delivery.
* [Squadron](https://github.com/mlund01/squadron) ⭐ 9 | 🐛 14 | 🌐 Go | 📅 2026-08-20 - MIT-licensed declarative runtime for multi-agent workflows defined in HCL, including orchestration, state, dependency resolution, routing, persistence, and resume.
* [How we built our multi-agent research system](https://www.anthropic.com/engineering/multi-agent-research-system) - Anthropic's architecture write-up for a multi-agent system with separation of roles and structured coordination.

### Browser, MCP & Tool Integration

* [browser-use/browser-harness](https://github.com/browser-use/browser-harness) ⭐ 17,385 | 🐛 318 | 🌐 Python | 📅 2026-09-05 - A thin CDP-based browser harness that lets agents extend helper functions during execution, useful for inspecting self-healing web-task workflows.
* [BrowserAct](https://github.com/browser-act/skills) ⭐ 5,633 | 🐛 7 | 🌐 Python | 📅 2026-08-24 - Open-source browser automation layer for agents with isolated parallel sessions, multi-account operation, and human handoff when automation is blocked.
* [Uni-CLI](https://github.com/olo-dot-io/Uni-CLI) ⭐ 270 | 🐛 0 | 🌐 TypeScript | 📅 2026-09-02 - Universal CLI hub connecting agents to 134 sites and desktop apps via 711 declarative YAML pipelines. Ships an 8-phase Karpathy-style self-repair loop, eval harness with a starter catalog, per-call cost ledger, hardcoded sensitive-path deny list, and `unicli mcp serve` that auto-registers one MCP tool per adapter. \~80 tokens per invocation.
* [OpenAgentRelay](https://github.com/ShakespeareLabs/open-agent-relay) ⭐ 2 | 🐛 0 | 🌐 Python | 📅 2026-07-14 - Inspectable runtime boundary for exposing a local agent or automation as a keyed LAN capability with target verification, bounded conversations, JSON output, and explicit exit codes.

### Workflow, Profiles & Asset Management

* [codex-profiles](https://github.com/Ducksss/codex-profiles) ⭐ 117 | 🐛 0 | 🌐 Shell | 📅 2026-09-04 - Codex CLI and Desktop profile launcher that isolates authentication, configuration, sessions, connectors, plugins, and logs by `CODEX_HOME`.
* [AgentPlane](https://github.com/basilisk-labs/agentplane) ⭐ 76 | 🐛 27 | 🌐 TypeScript | 📅 2026-09-05 - Git-native workflow-control harness that stores task records, policy, verification evidence, and closure state as reviewable repository artifacts.
* [Build A Harness](https://github.com/3IVIS/buildaharness) ⭐ 12 | 🐛 3 | 🌐 TypeScript | 📅 2026-09-05 - Apache-2.0 visual canvas for agent harnesses that compiles a runtime-neutral FlowSpec to several orchestration frameworks.
* [stelow](https://github.com/calionauta/stelow) ⭐ 10 | 🐛 1 | 🌐 TypeScript | 📅 2026-09-05 - Agentic product-workflow harness with Shape Up boundaries, adversarial plan review, acceptance-based execution contracts, and audit loops.
* [agent-harness](https://github.com/ar27111994/agent-harness) ⭐ 6 | 🐛 22 | 🌐 TypeScript | 📅 2026-09-05 - Reproducible lifecycle for coding-agent assets with authority-ranked discovery, pinned mirrors, quarantine routing, staged activation, and host-specific wiring.
* [Bring Your AI MCP](https://github.com/unitedideas/bringyour-mcp) ⭐ 1 | 🐛 0 | 📅 2026-05-25 - Public harness-migration reference for Claude Code to Codex moves, with installable auditor artifacts and explicit validation notes for hooks, MCP config, and instruction-file differences.
* [skills.sh](https://skills.sh) - A community marketplace for discovering, sharing, and installing reusable AI agent skills across runtimes like Claude Code and OpenClaw, making harness capabilities portable and composable.

## Contributing

Contributions are welcome. Please prefer resources that are:

* Specific about how agents are constrained, evaluated, resumed, observed, or orchestrated
* Original implementations, primary-source articles, or high-signal technical write-ups
* Useful to practitioners building real harnesses instead of generic AI commentary

If two links say the same thing, prefer the more primary, practical, and implementation-oriented one.

See [CONTRIBUTING.md](./CONTRIBUTING.md) for contribution guidelines and the preferred entry format.

## License

[CC0 1.0](./LICENSE)

***

> _Enhansomed by [enhansome](https://github.com/enhansome) on 2026-09-05._
