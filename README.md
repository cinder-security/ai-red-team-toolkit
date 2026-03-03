# 🔥 AI Red Team Toolkit
**Open-source offensive security tools for AI systems**  
By [Cinder Security](https://cindersecurity.io) — AI Red Team as a Service

[![License](https://img.shields.io/badge/license-MIT-orange.svg)](LICENSE)
[![Twitter](https://img.shields.io/badge/twitter-@CinderSecurity-orange.svg)](https://twitter.com/CinderSecurity)
[![Python](https://img.shields.io/badge/python-3.9+-orange.svg)]()
[![Status](https://img.shields.io/badge/status-active-brightgreen.svg)]()

---

## What is this?

`ai-red-team-toolkit` is a collection of open-source tools for testing the security of AI systems — LLMs, chatbots, AI agents, RAG pipelines, and agentic memory systems. Built by practitioners, for practitioners.

The AI security landscape is evolving fast. New attack vectors emerge weekly, yet most organizations deploying AI have zero offensive testing in place. This toolkit helps bridge that gap.

---

## 🔴 Real-World Findings (2026)

This toolkit is not theoretical. These are vulnerabilities discovered and responsibly disclosed by the Cinder Security team using the methodology in this repository.

| # | Target | Type | Severity | Status |
|---|--------|------|----------|--------|
| CSR-2026-001 | I'AM Chat — Mexico's first sovereign AI (IAMEX) | Memory Poisoning + Privilege Escalation | 🔴 Critical | Disclosed to vendor |
| CSR-2026-002 | ModelEngine fit-framework (Huawei ecosystem) | SSRF via LangChain `RequestsGetTool` | 🔴 Critical | Vendor confirmed — patch in progress |
| CSR-2026-003 | Insightify | Azure OpenAI credential exposure + RCE via `allow_dangerous_code=True` | 🔴 Critical | Disclosure in progress |
| CSR-2026-004 | Tabular-QA Server | Natural language SQL injection → `DROP TABLE` execution | 🔴 Critical | Disclosure in progress |

### CSR-2026-001 — I'AM Chat (IAMEX)
- **Vector:** Memory Poisoning with identity spoofing across persistent memory sessions
- **Methodology:** Based on CIBER (2026) and MemoryGraft (2025) academic frameworks
- **Impact:** False identity planted in persistent memory → privileged access escalation
- **Technique:** 3 plain-text messages. No code. No exploits. Pure natural language.

### CSR-2026-002 — ModelEngine fit-framework
- **File:** `framework/fel/python/plugins/fel_langchain_tools/langchain_tools.py`
- **Vector:** `RequestsGetTool` instantiated with `allow_dangerous_requests=True` without URL filtering
- **Impact:** Prompt injection → SSRF → Cloud Metadata exfiltration (IAM tokens on AWS/Alibaba Cloud)
- **Vendor response:** Confirmed receipt within 24 hours. Patch in progress.

### CSR-2026-003 — Insightify
- **Vector:** Azure OpenAI API credentials exposed in plaintext + `allow_dangerous_code=True` enabled
- **Impact:** API identity theft + arbitrary code execution on host server

### CSR-2026-004 — Tabular-QA Server
- **Vector:** SQL agent with write permissions + `json_to_sql` function executing `DROP TABLE` by design
- **Impact:** Total database destruction via natural language injection

---

## Attack Vectors Covered

| Vector | Description | Status |
|--------|-------------|--------|
| Prompt Injection | Direct and indirect prompt injection testing | 🔨 In Progress |
| Jailbreak Testing | Multi-turn psychological and single-turn jailbreak assessment | 🔨 In Progress |
| System Prompt Extraction | Techniques to extract hidden system prompts via behavioral mapping | 🔨 In Progress |
| RAG Poisoning | Testing RAG pipelines for document injection and memory drift attacks | 🔨 In Progress |
| Memory Poisoning | Persistent compromise of LLM agent memory via poisoned experience retrieval | ✅ Documented (CSR-2026-001) |
| SSRF via LLM Agents | Exploiting dangerous tool configurations in LangChain agents | ✅ Documented (CSR-2026-002) |
| Data Exfiltration | Testing AI agents for data leak vulnerabilities | 📋 Planned |
| Tool/Function Abuse | Exploiting AI agent tool-calling capabilities | 🔨 In Progress |
| Code Interpreter Attacks | Prompt injection, backdoors, and memory poisoning against code agents | 📋 Planned |
| Multi-Agent Attacks | Attack chains across multi-agent systems with shared memory | 📋 Planned |
| Fine-Tuning Backdoors | Poisoning models through fine-tuning APIs at minimal cost | 📋 Planned |

---

## Project Structure

```
ai-red-team-toolkit/
├── modules/
│   ├── prompt_injection/     # Prompt injection payloads and testers
│   ├── jailbreak/            # Jailbreak techniques (HPM, multi-turn)
│   ├── extraction/           # System prompt and model extraction
│   ├── rag_poisoning/        # RAG pipeline attack tools
│   ├── memory_poisoning/     # Agent memory compromise (MemoryGraft)
│   ├── ssrf/                 # SSRF via LangChain tool abuse
│   ├── code_interpreter/     # Code agent security testing (CIBER)
│   └── exfiltration/         # Data exfiltration via AI agents
├── payloads/                 # Curated payload libraries
├── reports/                  # Report templates for engagements
├── docs/                     # Documentation and methodology
│   └── research/             # Paper summaries and attack taxonomies
└── examples/                 # Usage examples and walkthroughs
```

---

## Quick Start

```bash
# Clone the repository
git clone https://github.com/cinder-security/ai-red-team-toolkit.git
cd ai-red-team-toolkit

# Install dependencies
pip install -r requirements.txt

# Run a basic prompt injection test
python -m modules.prompt_injection.scanner --target <API_ENDPOINT>
```

---

## Research Foundation

This toolkit is grounded in peer-reviewed academic research. We track the cutting edge of AI offensive security so you don't have to.

### Core Papers

| Paper | Authors | Key Finding | Impact |
|-------|---------|-------------|--------|
| Psychological Jailbreak (HPM) | Liu & Lin, 2025 | Multi-turn psychological manipulation exploiting LLM personality traits | 88.1% ASR across frontier models. Inverse scaling — smarter models are more vulnerable |
| Fine-Tuning Jailbreaks | Li, Wang & Li, 2025 | Three-pronged attack via data poisoning + backdoors through fine-tuning APIs | 97% ASR on GPT-4.1/4o for just $6 in compute |
| CIBER Benchmark | Ba, Li & Li, 2026 | Comprehensive security evaluation framework for Code Interpreter agents | 73.3% ASR via Memory Poisoning. Code Descriptions bypass defenses at 62.5% ASR |
| MemoryGraft | Srivastava & He, 2025 | Persistent compromise of LLM agents via poisoned experience retrieval in RAG memory | 47.9% retrieval drift with only 10 poisoned seeds. Trigger-free, persists across sessions |

### Attack Taxonomy

```
AI Attack Surface
├── Prompt-Level (Transient)
│   ├── Direct Prompt Injection
│   ├── Indirect Prompt Injection
│   └── Psychological Manipulation (HPM) ← 88.1% ASR
│
├── Model-Level (Permanent)
│   ├── Fine-Tuning Backdoors ← 97% ASR, $6
│   └── Data Poisoning
│
├── Memory-Level (Persistent)
│   ├── RAG Knowledge Poisoning
│   ├── Agent Memory Poisoning (MemoryGraft) ← 47.9% drift
│   └── Experience Store Contamination ← Documented: CSR-2026-001
│
├── Infrastructure-Level (Systemic)
│   ├── SSRF via Dangerous Tool Configs ← Documented: CSR-2026-002
│   ├── Credential Exposure in AI Repos ← Documented: CSR-2026-003
│   └── SQL Injection via Natural Language ← Documented: CSR-2026-004
│
└── Agent-Level (Systemic)
    ├── Code Interpreter Exploitation (CIBER) ← 73.3% ASR
    ├── Tool/Function Abuse
    └── Multi-Agent Propagation
```

---

## Who is this for?

- Security researchers testing AI systems
- Red teamers expanding into AI attack surfaces
- Developers building AI applications who want to test before deploying
- CISOs and security teams evaluating AI risk
- Bug bounty hunters targeting AI-powered features

---

## Contributing

We welcome contributions. If you've discovered a novel attack technique, have a useful payload, or want to improve existing tools — open a PR.

Please read our [Contributing Guidelines](CONTRIBUTING.md) before submitting.

---

## Responsible Disclosure

This toolkit is designed for **authorized security testing only**. All tools should be used exclusively on systems you own or have explicit permission to test.

If you discover vulnerabilities using these tools, please follow responsible disclosure practices and report them to the affected vendors.

---

## About Cinder Security

Cinder Security provides **AI Red Team as a Service** — offensive security testing specifically designed for AI systems. We break AI before attackers do.

> 🔥 *A cinder is an ember that keeps burning when everyone thinks the fire is out. We find what's still burning in your AI systems.*

🌐 [cindersecurity.io](https://cindersecurity.io)  
🐦 [@CinderSecurity](https://twitter.com/CinderSecurity)  
📧 contact@cindersecurity.io

---

*Built with 🔥 by Cinder Security | Guadalajara, MX*
