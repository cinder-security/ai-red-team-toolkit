[README (4).md](https://github.com/user-attachments/files/25566643/README.4.md)
![Cinder Security](assets/cinder-logo.png)

# 🔥 AI Red Team Toolkit

**Open-source offensive security tools for AI systems**  
*By [Cinder Security](https://cindersecurity.io) — AI Red Team as a Service*

[![License](https://img.shields.io/badge/license-MIT-orange.svg)](https://github.com/cinder-security/ai-red-team-toolkit/blob/main/LICENSE)
[![Twitter](https://img.shields.io/twitter/follow/CinderSecurity?style=social)](https://twitter.com/CinderSecurity)
[![Python](https://img.shields.io/badge/python-3.10%2B-blue.svg)]()
[![Status](https://img.shields.io/badge/status-alpha-yellow.svg)]()

---

## What is this?

**ai-red-team-toolkit** is a collection of open-source tools for testing the security of AI systems — LLMs, chatbots, AI agents, RAG pipelines, and agentic memory systems. Built by practitioners, for practitioners.

The AI security landscape is evolving fast. New attack vectors emerge weekly, yet most organizations deploying AI have zero offensive testing in place. This toolkit helps bridge that gap.

## Attack Vectors Covered

| Vector | Description | Status |
|--------|-------------|--------|
| **Prompt Injection** | Direct and indirect prompt injection testing | 🔨 In Progress |
| **Jailbreak Testing** | Multi-turn psychological and single-turn jailbreak assessment | 🔨 In Progress |
| **System Prompt Extraction** | Techniques to extract hidden system prompts via behavioral mapping | 🔨 In Progress |
| **RAG Poisoning** | Testing RAG pipelines for document injection and memory drift attacks | 🔨 In Progress |
| **Memory Poisoning** | Persistent compromise of LLM agent memory via poisoned experience retrieval | 🔨 In Progress |
| **Data Exfiltration** | Testing AI agents for data leak vulnerabilities | 📋 Planned |
| **Tool/Function Abuse** | Exploiting AI agent tool-calling capabilities | 📋 Planned |
| **Code Interpreter Attacks** | Prompt injection, backdoors, and memory poisoning against code agents | 📋 Planned |
| **Multi-Agent Attacks** | Attack chains across multi-agent systems with shared memory | 📋 Planned |
| **Fine-Tuning Backdoors** | Poisoning models through fine-tuning APIs at minimal cost | 📋 Planned |

## Project Structure

```
ai-red-team-toolkit/
├── modules/
│   ├── prompt_injection/     # Prompt injection payloads and testers
│   ├── jailbreak/            # Jailbreak techniques (HPM, multi-turn)
│   ├── extraction/           # System prompt and model extraction
│   ├── rag_poisoning/        # RAG pipeline attack tools
│   ├── memory_poisoning/     # Agent memory compromise (MemoryGraft)
│   ├── code_interpreter/     # Code agent security testing (CIBER)
│   └── exfiltration/         # Data exfiltration via AI agents
├── payloads/                 # Curated payload libraries
├── reports/                  # Report templates for engagements
├── docs/                     # Documentation and methodology
│   └── research/             # Paper summaries and attack taxonomies
└── examples/                 # Usage examples and walkthroughs
```

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

## Research Foundation

This toolkit is grounded in peer-reviewed academic research. We track the cutting edge of AI offensive security so you don't have to.

### Core Papers

| Paper | Authors | Key Finding | Impact |
|-------|---------|-------------|--------|
| **[Psychological Jailbreak (HPM)](https://arxiv.org/abs/2504.xxxxx)** | Liu & Lin, 2025 | Multi-turn psychological manipulation exploiting LLM personality traits | **88.1% ASR** across frontier models. Inverse scaling — smarter models are *more* vulnerable |
| **[Fine-Tuning Jailbreaks](https://arxiv.org/abs/2504.xxxxx)** | Li, Wang & Li, 2025 | Three-pronged attack via data poisoning + backdoors through fine-tuning APIs | **97% ASR** on GPT-4.1/4o for just **$6** in compute |
| **[CIBER Benchmark](https://arxiv.org/abs/2602.19547)** | Ba, Li & Li, 2026 | Comprehensive security evaluation framework for Code Interpreter agents | **73.3% ASR** via Memory Poisoning. Code Descriptions bypass defenses at **62.5% ASR** |
| **[MemoryGraft](https://arxiv.org/abs/2512.16962)** | Srivastava & He, 2025 | Persistent compromise of LLM agents via poisoned experience retrieval in RAG memory | **47.9% retrieval drift** with only 10 poisoned seeds. Trigger-free, persists across sessions |

### Why These Papers Matter

Traditional AI security focuses on prompt-level attacks — inject something malicious *now* and get an immediate response. That's Layer I. The real threat landscape is deeper:

**Layer I — Explicit Threats:** Direct prompt injection with obvious malicious intent. Most guardrails catch these.

**Layer II — Implicit Threats:** Attacks disguised as legitimate requests. Requires semantic understanding to detect.

**Layer III — Persistent Threats:** Attacks that poison the *memory*, *training data*, or *experience store* of AI systems. These compromise behavior *across sessions* and affect *future users* — not just the current conversation.

Our toolkit addresses all three layers:

- **HPM** demonstrates that Layer II attacks using psychological manipulation achieve higher success rates than brute-force jailbreaks
- **Fine-Tuning Jailbreaks** shows that Layer III model-level compromise is accessible to anyone with $6 and API access
- **CIBER** provides a systematic framework for evaluating code agent defenses across all layers
- **MemoryGraft** proves that RAG memory systems — the backbone of modern AI agents — can be silently corrupted through normal usage

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
│   └── Experience Store Contamination
│
└── Agent-Level (Systemic)
    ├── Code Interpreter Exploitation (CIBER) ← 73.3% ASR
    ├── Tool/Function Abuse
    └── Multi-Agent Propagation
```

## Who is this for?

- **Security researchers** testing AI systems
- **Red teamers** expanding into AI attack surfaces
- **Developers** building AI applications who want to test before deploying
- **CISOs and security teams** evaluating AI risk
- **Bug bounty hunters** targeting AI-powered features

## Contributing

We welcome contributions. If you've discovered a novel attack technique, have a useful payload, or want to improve existing tools — open a PR.

Please read our [Contributing Guidelines](CONTRIBUTING.md) before submitting.

## Responsible Disclosure

This toolkit is designed for **authorized security testing only**. All tools should be used exclusively on systems you own or have explicit permission to test.

If you discover vulnerabilities using these tools, please follow responsible disclosure practices and report them to the affected vendors.

## About Cinder Security

**[Cinder Security](https://cindersecurity.io)** provides AI Red Team as a Service — offensive security testing specifically designed for AI systems. We break AI before attackers do.

🔥 *A cinder is an ember that keeps burning when everyone thinks the fire is out. We find what's still burning in your AI systems.*

- 🌐 [cindersecurity.io](https://cindersecurity.io)
- 🐦 [@CinderSecurity](https://twitter.com/CinderSecurity)
- 📧 [contact@cindersecurity.io](mailto:contact@cindersecurity.io)

---

Built with 🔥 by [Cinder Security](https://cindersecurity.io) | Guadalajara, MX
