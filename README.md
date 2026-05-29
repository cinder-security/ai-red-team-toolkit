[README_Cinder_Security_Fracture_Final.md](https://github.com/user-attachments/files/28379160/README_Cinder_Security_Fracture_Final.md)
# Cinder Security — AI Red Team Research

**Offensive AI security for the Intelligence Age.**  
**Built in Zapopan, Mexico. Focused on LLMs, AI agents, RAG pipelines, memory systems, and AI supply chains.**

> A cinder is an ember that keeps burning when everyone thinks the fire is out.  
> We find what is still burning inside production AI systems.

[![Responsible Disclosure](https://img.shields.io/badge/Responsible%20Disclosure-Only-22c55e)](#responsible-disclosure)
[![AI Red Team](https://img.shields.io/badge/AI%20Red%20Team-Offensive%20Security-ff6b35)](#what-we-test)
[![Fracture](https://img.shields.io/badge/Fracture-Autonomous%20AI%20Red%20Team-ff4500)](#fracture)
[![LATAM](https://img.shields.io/badge/Built%20in-Latin%20America-e8e6e1)](#latin-america-under-siege)

---

## What this is

Cinder Security is building an offensive AI security practice for organizations deploying AI in production.

This repository documents the research foundation behind our work: public security advisories, controlled adversarial evaluations, attack taxonomy, and the methodology that powers **Fracture**, our autonomous AI red-team engine.

Our work focuses on systems where model behavior meets real infrastructure:

- LLM applications and chatbots
- Retrieval-Augmented Generation pipelines
- AI agents with tools, memory, and planning
- Model registries and ML supply chains
- Prompt-mediated tool execution
- Persistent memory and cross-session state
- AI governance, auditability, and responsible disclosure

This is not theoretical security theater. The methodology is grounded in public advisories, vendor-recognized research, and controlled adversarial evaluation.

---

## Research record

### Public advisory evidence

| Evidence source | Target / environment | Technique demonstrated | Status |
|---|---|---|---|
| `GHSA-m4rw-22q2-87j8` | ModelEngine `fit-framework` | SSRF + prompt-injection composition in AI tooling | Public advisory / patch live |
| `GHSA-4fpw-hjmg-x4qr` | LangGraph / LangChain orchestration | RAG poisoning / indirect prompt injection | Public advisory |

### Controlled evaluation evidence

In May 2026, Cinder Security completed the AI challenge track in **Hack The Box Global Cyber Skills Benchmark CTF 2026: Project Nightfall**.

These results are treated as **controlled-environment evidence of attack-technique viability**, not as production vulnerability claims.

| Environment | Challenge | Primitive demonstrated | Paper role |
|---|---|---|---|
| HTB GCSB 2026: Project Nightfall | Lotus Registry | ML supply-chain / model registry risk | Technique viability |
| HTB GCSB 2026: Project Nightfall | Espionage Intelligence | RAG broken access control → credential exposure → execution path | Compositional AI-system risk |
| HTB GCSB 2026: Project Nightfall | Bribery Compliance | Agentic tool-result spoofing / compliance bypass | Trust-boundary inversion |

### Additional coordinated-disclosure work

Additional findings remain under coordinated disclosure, vendor review, or final public disposition. They are intentionally excluded from this public evidence table until they can be described accurately, safely, and without ambiguity.

---

## Latin America Under Siege

Cinder Security submitted the research proposal:

> **Latin America Under Siege: Empirical Evidence of Active Vulnerabilities in Production AI Systems and the Absence of a Regional Audit Framework**

The paper argues that Latin America is adopting AI faster than it is developing the capacity to adversarially evaluate it.

It proposes a regional offensive AI audit framework organized around five capabilities:

1. **Trajectory testing** — test complete attack paths across retrieval, tools, memory, and action.
2. **Observation authentication assessment** — determine whether agents can distinguish authentic from fabricated tool results, retrieved documents, and memory entries.
3. **Memory-state audit** — inspect persistent conversational and operational state for poisoning, unauthorized accumulation, and cross-session risk.
4. **Reference-implementation review** — evaluate vendor examples, sample code, and orchestration templates before they propagate into production.
5. **Continuous disclosure translation** — convert public advisories and vulnerability records into architecture-level audit checks.

The core thesis:

> Latin America should not only consume AI systems.  
> It must produce AI security evidence, standards, tools, and audit capacity.

---

## Fracture

**Fracture** is Cinder Security’s autonomous AI red-team engine.

It is designed to run structured, safety-bounded offensive evaluations against authorized AI systems. Fracture tests how integrated AI applications fail when retrieval, tools, memory, prompts, and model behavior interact under adversarial pressure.

### Core modules

| Module | Purpose |
|---|---|
| `fingerprint` | Identify AI surface behavior, model hints, response formats, and safety posture. |
| `extract` | Evaluate system-prompt and hidden-instruction exposure risk. |
| `memory` | Test persistent memory, cross-session state, and poisoning behavior. |
| `hpm` | Hierarchical Prompt Manipulation for multi-turn adversarial evaluation. |
| `ssrf` | Evaluate prompt-mediated tool abuse and unsafe HTTP tool configurations. |
| `retrieval_poison` | Test RAG poisoning, retrieved-context injection, and document trust boundaries. |
| `obliteratus` | Stress-test safety logic, refusal handling, and policy boundary consistency. |
| `campaign` | Orchestrate multi-module attack campaigns against a defined target. |
| `shadow_replay` | Re-run historical attack traces against updated systems to validate fixes. |

### Methodology behind Fracture

Fracture does not treat the model as the only target. It treats the deployed AI system as a composed architecture:

```text
user input
  ↓
prompt / policy wrapper
  ↓
retrieval layer
  ↓
tool invocation
  ↓
memory update
  ↓
action / response
  ↓
logs / audit evidence
```

The unit of evaluation is the **trajectory**, not the isolated endpoint.

---

## What we test

Cinder Security evaluates AI systems across the following attack surfaces:

### Prompt and context layer

- Direct prompt injection
- Indirect prompt injection
- RAG poisoning
- System prompt exposure
- Prompt-policy conflicts
- Multi-turn jailbreak patterns

### Agent and tool layer

- Tool-result spoofing
- Unsafe tool invocation
- Agentic SSRF
- Code interpreter exposure
- MCP / toolchain misuse
- ReAct-style trajectory corruption

### Memory layer

- Persistent memory poisoning
- Cross-session manipulation
- Unauthorized memory accumulation
- Memory drift
- State-baseline recovery risk

### AI supply chain

- Model registry trust boundaries
- Unsafe model-loading patterns
- Reference-code propagation
- Plugin and framework misuse
- Serialization and artifact handling risk

### Governance and audit layer

- OWASP LLM Top 10 mapping
- MITRE ATLAS mapping
- NIST AI RMF alignment
- Evidence package generation
- Executive-ready reporting
- Remediation guidance

---

## Why this matters

Traditional security testing was built for endpoints, protocols, and code paths.

AI systems introduce a different class of risk:

- The vulnerable object may be a reasoning trajectory.
- The exploit may be a retrieved document.
- The payload may persist in memory.
- The trust boundary may be a tool result.
- The insecure pattern may originate in reference code.
- The system may behave exactly as designed while producing an unsafe outcome.

That is why AI security needs more than static scans and generic governance checklists.

It needs authorized adversarial evaluation.

---

## Safety-bounded offensive testing

Cinder Security’s methodology is offensive, but bounded.

All testing must be:

- **Authorized** — performed only with explicit permission.
- **Scope-bounded** — restricted to agreed systems and assets.
- **Data-minimizing** — no unnecessary access or exfiltration.
- **Auditable** — every test produces reviewable evidence.
- **Reviewable** — findings can be examined by the authorizing party.
- **Fail-safe** — escalation stops once the finding is validated.

We do not provide malicious hacking services, credential theft, unauthorized access, malware, or services intended to bypass security controls outside approved engagements.

---

## Example engagement outputs

A Cinder Security assessment produces:

- Executive summary
- System boundary map
- Attack trajectory report
- Evidence package
- OWASP LLM Top 10 mapping
- MITRE ATLAS mapping
- AI-specific severity assessment
- Reproduction notes safe for defenders
- Remediation guidance
- Retest plan
- Optional continuous monitoring plan through CinderGuard

---

## Who this is for

- AI-native startups shipping agents, RAG systems, and generative AI features
- Security teams responsible for AI deployment risk
- CISOs evaluating AI governance and audit readiness
- Engineering teams integrating LLMs into production workflows
- Bug bounty and responsible-disclosure programs receiving AI-specific reports
- Public-sector institutions exploring AI systems near sensitive data or decision-making

---

## CinderGuard

**CinderGuard** is Cinder Security’s continuous AI red-team service.

It combines Fracture campaigns, manual review, and recurring executive reporting to test production AI systems as they evolve.

CinderGuard is designed for organizations that need recurring assurance over:

- Agent updates
- Prompt changes
- New tools
- Retrieval corpus changes
- Memory behavior
- Model version changes
- Reference-code integration
- New deployment environments

AI systems are not static after launch. Their risk profile changes with every new prompt, retrieval corpus, memory entry, tool, and model update.

---

## Responsible disclosure

This research is intended for authorized testing and defensive improvement.

If a vulnerability is discovered in a third-party system, Cinder Security follows responsible disclosure practices and coordinates with the affected vendor or program before publication.

Operational exploit payloads and unsafe reproduction details are intentionally omitted from public materials when disclosure or safety considerations require it.

---

## Contact

**Cinder Security**  
AI Red Team as a Service  
Zapopan, Mexico

- Website: [https://cindersecurity.io](https://cindersecurity.io)
- Email: [contact@cindersecurity.io](mailto:contact@cindersecurity.io)
- GitHub: [https://github.com/cinder-security](https://github.com/cinder-security)

---

Built with fire by Cinder Security.

