# Awesome Graph Harness

> Knowledge sources for AI agent harnesses: graphs, models, provenance. Papers, tools, inspiration.

Many entries are 2025–2026 preprints without peer review; a venue is listed only where the paper's page shows one.

## Contents

- [Papers](#papers)
  - [Software factories](#software-factories)
  - [Benchmarks for whole-repo and backend generation](#benchmarks-for-whole-repo-and-backend-generation)
  - [Specifications and clarification](#specifications-and-clarification)
  - [Why agents fail](#why-agents-fail)
  - [Parallel agents and coordination](#parallel-agents-and-coordination)
  - [Cost and token use](#cost-and-token-use)
  - [Graph-grounded code generation](#graph-grounded-code-generation)
  - [Code graphs for retrieval and navigation](#code-graphs-for-retrieval-and-navigation)
  - [Agent tool interfaces (MCP)](#agent-tool-interfaces-mcp)
  - [Architecture models and traceability](#architecture-models-and-traceability)
  - [Architecture design with LLM agents](#architecture-design-with-llm-agents)
  - [Architecture decisions and knowledge](#architecture-decisions-and-knowledge)
  - [Provenance](#provenance)
  - [Surveys](#surveys)
- [Contributing](#contributing)
- [License](#license)

## Papers

### Software factories

- [MetaGPT](https://arxiv.org/abs/2308.00352) – Role-based "software company" where roles pass structured documents (PRD, design, interfaces), not chat. *ICLR 2024.*
- [ChatDev](https://arxiv.org/abs/2307.07924) – Role-based software company pipeline of communicating agents. *ACL 2024.*
- [Agentless](https://arxiv.org/abs/2407.01489) – Fixed localize → repair → validate pipeline matches agents at ~$0.70/task; a fixed workflow often beats free agent choice. *2024.*
- [Can AI Agents Generate Microservices? How Far are We?](https://arxiv.org/abs/2603.09004) – 144 generated microservices: with clear contracts 81–98% of integration tests pass; minimal prompts beat detailed ones. *ICSA 2026.*
- [LLM Agents for Generating Microservice-based Applications](https://arxiv.org/abs/2508.20119) – Difficulty metric for specs; agents fail on complex logic, external services, databases and auth. *Preprint, 2025.*

### Benchmarks for whole-repo and backend generation

- [Zero2Repo](https://arxiv.org/abs/2609.38269) – Build a repo from PRD + interface contract with hidden acceptance tests; most failures trace to one omitted or rare spec rule. *Preprint, 2026.*
- [NL2Repo-Bench](https://arxiv.org/abs/2512.12730) – One requirements doc → installable library; best agents pass <40% of tests, losing global coherence and cross-file dependencies. *2025.*
- [BaxBench](https://arxiv.org/abs/2502.11844) – 392 backends from OpenAPI; best model 62% correct, and about half of the correct backends are exploitable. *ICML 2025.*
- [SWE-Sharp-Bench](https://arxiv.org/abs/2511.02352) – 150 C# tasks; agents solve ~40% vs ~70% in Python, tripped up by `.sln`, multi-`.csproj`, NuGet. *AIware 2025.*

### Specifications and clarification

- [Specification Before Generation](https://arxiv.org/abs/2609.23270) – A fixed 267-word "what must be true" frame (money, time, idempotency, access) cut defects in all 5 models. *Preprint, pre-registered, 2026.*
- [Grounding AI Agents in Contracts](https://arxiv.org/abs/2608.17177) – Pre/postconditions and undefined behaviours first, tests from them: +9.8 pp real bugs found. *SpecOps 2026.*
- [AgentCoder](https://arxiv.org/abs/2312.13010) – Classic: the test designer never sees the code. *2023.*
- [Citation Discipline in Spec-Driven Development](https://arxiv.org/abs/2606.30689) – A requirement-ID citation on every line gives ~87% hallucination detection. *Preprint, single author, 2026.*
- [Ask or Assume?](https://arxiv.org/abs/2603.26233) – Separate agent detects underspecification; 69.4% on underspecified SWE-bench Verified, close to full specs. *EMNLP 2026.*
- [Ambig-SWE](https://arxiv.org/abs/2502.13069) – Models struggle to spot underspecified tasks; specific, actionable questions give up to 74% better results. *ICLR 2026.*
- [Asking What Matters](https://arxiv.org/abs/2604.14624) – 8B RL module asks 41% fewer questions than GPT-5 with matching results. *2026.*
- [Don't Guess, Just Ask](https://arxiv.org/abs/2610.13022) – Agent harnesses do not write better requirement documents than their base models. *2026.*

### Why agents fail

- [Why Do Multi-Agent LLM Systems Fail? (MAST)](https://arxiv.org/abs/2503.13657) – 14 failure modes from 1,642 traces; many failures come from system design, not the model. *2025.*
- [Where Do AI Coding Agents Fail?](https://arxiv.org/abs/2601.15195) – 33k agent PRs; rejected ones are larger, touch more files, fail CI, or are unwanted. *MSR 2026.*
- [AIDev](https://arxiv.org/abs/2507.15003) – 456k agent PRs: faster but accepted less often (a "trust gap"). *2025.*

### Parallel agents and coordination

- [Passes Alone, Fails Together](https://arxiv.org/abs/2609.25396) – Patches pass alone and break after merge; one message describing an interface change recovers 82%. *EXPRESS 2026.*
- [AgenticFlict](https://arxiv.org/abs/2604.03551) – Textual merge conflicts in 27.67% of 107k agent PRs. *2026.*
- [Claim Plane](https://arxiv.org/abs/2607.21909) – Workers declare their scope before they write. *Small study, 2026.*

### Cost and token use

- [Analyzing and Mitigating Cost-Inefficient Behaviors in Coding Agents](https://arxiv.org/abs/2609.30725) – Repeated retrieval and re-runs cost up to 22.75% per task; developer-written skills cut cost up to 41.73%. *Under review, 2026.*
- [Tokenomics](https://arxiv.org/abs/2601.14470) – Code review takes 59.4% of tokens; refinement and verification dominate cost. *Preprint, 2026.*
- [When Agents Coordinate](https://arxiv.org/abs/2608.16801) – Coordinator agent gives no reliable gain; shared files cut output tokens ~42%. *2026.*

### Graph-grounded code generation

- [RPG: Repository Planning Graph](https://arxiv.org/abs/2509.16198) – One graph (capabilities, files, interfaces, data flows) replaces the text plan; topological, test-first generation. *2025.*
- [iEcoreGen](https://arxiv.org/abs/2512.05498) – Deterministic generator writes structure from an EMF model; the LLM only fills method bodies. *Preprint, 2025.*
- [Metamodel-Guided Model Generation with Layered Constraints](https://arxiv.org/abs/2510.25890) – Spec constraints linked to metamodel elements, enforced at generation time, then validated with bounded repair; all 60 AUTOSAR runs passed acceptance and all 255 ARXML files passed XSD. *Preprint, 2025.*
- [Type-Constrained Code Generation](https://arxiv.org/abs/2504.09246) – Type-constrained decoding cuts compile errors by more than half. *PLDI 2025.*
- [Grammar Prompting](https://arxiv.org/abs/2305.19234) – Constrain generation with a domain-specific grammar. *NeurIPS 2023.*
- [Private-Library-Oriented Code Generation](https://arxiv.org/abs/2307.15370) – Generating code against APIs the model never saw. *2023.*
- [Code Graph Model](https://arxiv.org/abs/2505.16901) – Code graph structure fed directly into the model. *NeurIPS 2025.*

### Code graphs for retrieval and navigation

- [LocAgent](https://arxiv.org/abs/2503.09089) – Typed graph (contain, import, invoke, inherit) + search/traverse/retrieve tools; 92.7% file-level localization at ~86% lower cost. *2025.*
- [RepoGraph](https://arxiv.org/abs/2410.14684) – k-hop ego-graphs around relevant entities as a plug-in for other frameworks. *ICLR 2025.*
- [CodexGraph](https://arxiv.org/abs/2408.03910) – "Write then translate": one agent asks in natural language, another turns it into a fixed-schema graph query. *NAACL 2025.*
- [KGCompass](https://arxiv.org/abs/2503.21710) – Knowledge graph links issues and PRs to code; multi-hop paths find 89.7% of bugs with no location hint. *2025.*
- [Codebase-Memory](https://arxiv.org/abs/2603.27277) – Tree-sitter code graph via 14 typed MCP tools; 10× fewer tokens than reading files. *Preprint, 2026.*
- [Codified Context](https://arxiv.org/abs/2602.20478) – Agent knowledge split into a "hot" constitution and a "cold" spec base served through MCP. *2026.*
- [GraphRAG-Bench](https://arxiv.org/abs/2506.05690) – GraphRAG helps on multi-hop questions, often loses to plain RAG on simple lookups. *ICLR 2026.*

### Agent tool interfaces (MCP)

- [MCP Tool Descriptions Are Smelly!](https://arxiv.org/abs/2602.14878) – 97.1% of 856 tool descriptions have a smell; fixing them gives +5.85 pp median task success. *Preprint, 2026.*
- [MCP-Universe](https://arxiv.org/abs/2508.14704) – Benchmark of agents on real MCP servers. *2025.*
- [MCP-Bench](https://arxiv.org/abs/2508.20453) – Benchmark of tool-using agents over MCP. *2025.*

### Architecture models and traceability

- [Software Reflexion Models](https://bibtex.github.io/FSE-1995-MurphyNS.html) – Classic: compare a high-level model with one extracted from code; report convergences, divergences, absences. *FSE 1995.*
- [TransArC: Recovering Trace Links Between Documentation and Code](https://conf.researchr.org/details/icse-2024/icse-2024-research-track/129/Recovering-Trace-Links-Between-Software-Documentation-And-Code) – Architecture model as intermediate artifact: F1 0.98 model → code, 0.82 docs → code. *ICSE 2024.*
- [Who's Who? (ExArch / ArTEMiS)](https://arxiv.org/abs/2511.02434) – LLM recovers the architecture model from docs and code without a hand-made model (F1 ~0.86). *2025.*
- [Detecting Inconsistencies in Software Architecture Documentation (ArDoCo)](https://publikationen.bibliothek.kit.edu/1000158208) – Finds model elements the docs never mention and vice versa. *ICSA 2023.*
- [Model-Based Construction of EA Knowledge Graphs](https://repositum.tuwien.at/handle/20.500.12708/136173) – ArchiMate models as a property graph; graph queries detect EA smells. *EDOC 2022.*
- [EA smells on 347 models (Smajevic, Hacks, Bork)](https://dl.gi.de/items/b8be98b7-d199-49bb-a700-c2445675c536/full) – Predecessor of the EA knowledge graph work. *PoEM 2021.*
- [LLMs on an ArchiMate knowledge graph (Reitemeyer & Fill)](https://arxiv.org/abs/2501.03566) – Narrow tasks go well, complex tasks badly. *2025.*
- [Automated Domain Modeling with LLMs](https://dblp.org/rec/conf/models/ChenYCLMV23) – F1 0.76 for classes, 0.34 for relationships; LLMs miss elements rather than invent them. *MODELS 2023.*

### Architecture design with LLM agents

- [A-SAW: Agentic Software Architecture Workflow](https://arxiv.org/abs/2610.13647) – C4 model in git + typed element catalog; agent drafts, human approves; traceability is the weak spot. *Preprint, 2026.*
- [Collaborative LLM Agents for C4 Architecture Design](https://arxiv.org/abs/2510.22787) – Agents produce C4 views, evaluated by deterministic checks plus an LLM judge. *HICSS-59, 2026.*
- [Service Cutter](https://doi.org/10.1007/978-3-319-44482-6_12) – Coupling graph with 16 criteria clustered into service candidates. *ESOCC 2016.*
- [Automating Domain-Driven Design](https://arxiv.org/abs/2603.26244) – LLM handles early DDD steps; errors compound at aggregates, contexts split too finely. *2026.*

### Architecture decisions and knowledge

- [Software Architecture as a Set of Architectural Design Decisions](https://doi.org/10.1109/WICSA.2005.61) – Classic: architecture as decisions, not just structure. *WICSA 2005.*
- [Architecture Decisions: Demystifying Architecture](https://ieeexplore.ieee.org/document/1407822) – Classic decision record template. *IEEE Software 2005.*
- [Building Up and Reasoning About Architectural Knowledge](https://doi.org/10.1007/11921998_8) – Classic ontology of architectural knowledge. *QoSA 2006.*
- [Understanding Software Architecture Erosion](https://arxiv.org/abs/2112.10934) – Technical and non-technical causes of erosion, including "knowledge vaporization". *JSEP 2022.*
- [Context Matters: Context Strategies for ADR Generation](https://arxiv.org/abs/2604.03826) – 750 repos; the last 3–5 ADRs give the best quality/cost trade-off. *EASE 2026.*
- [DRAFT-ing Architectural Design Decisions using LLMs](https://arxiv.org/abs/2504.08207) – Retrieval + few-shot + fine-tuning on 4,911 ADRs. *2025.*
- [ADR generation with LLMs (DRAFT predecessor)](https://arxiv.org/abs/2403.01709) – Earlier study of LLM-generated design decisions. *ICSA 2024.*
- [Using LLMs in Generating Design Rationale](https://arxiv.org/abs/2504.20781) – Precision ~0.27, recall 0.63–0.72: good at "what did we forget", bad at "what is true". *ACM TOSEM 2025.*
- Semantic Modeling of ADRs (Karetnikov et al.) – ADRs as semantic models. *SANER 2024 ERA.*
- Using ADRs in Open Source Projects (Buchgeher et al.) – How ADRs are used in practice. *IEEE Access 2023.*

### Provenance

- [PROV-AGENT](https://arxiv.org/abs/2508.02866) – Provenance graph for tracing AI agent decisions in workflows.

### Surveys

- [Software Architecture Meets LLMs](https://arxiv.org/abs/2505.16697) – SLR: code generation from architecture and conformance checking are under-explored. *2025.*
- [Generative AI for Software Architecture](https://arxiv.org/abs/2503.13310) – Multivocal review: hallucination, weak output testing, no architecture datasets. *2025.*
- [Repository-level RAG for code](https://arxiv.org/abs/2510.04905) – Survey of retrieval-augmented generation over whole repositories. *2025.*

## Contributing

PRs welcome. One line per entry: link + why it matters.

## License

[CC0](https://creativecommons.org/publicdomain/zero/1.0/)
