<p align="center">
  <img src="assets/cinder-logo.png" alt="Cinder Security" width="120"/>
</p>

<h1 align="center">🔥 AI Red Team Toolkit</h1>

<p align="center">
  <strong>Open-source offensive security tools for AI systems</strong><br>
  <em>By <a href="https://cindersecurity.io">Cinder Security</a> — AI Red Team as a Service</em>
</p>

<p align="center">
  <a href="https://github.com/cinder-security/ai-red-team-toolkit/blob/main/LICENSE"><img src="https://img.shields.io/badge/license-MIT-orange.svg" alt="License"></a>
  <a href="https://twitter.com/CinderSecurity"><img src="https://img.shields.io/twitter/follow/CinderSecurity?style=social" alt="Twitter"></a>
  <img src="https://img.shields.io/badge/python-3.10%2B-blue.svg" alt="Python">
  <img src="https://img.shields.io/badge/status-alpha-yellow.svg" alt="Status">
</p>

---

## What is this?

**ai-red-team-toolkit** is a collection of open-source tools for testing the security of AI systems — LLMs, chatbots, AI agents, and RAG pipelines. Built by practitioners, for practitioners.

The AI security landscape is evolving fast. New attack vectors emerge weekly, yet most organizations deploying AI have zero offensive testing in place. This toolkit helps bridge that gap.

## Attack Vectors Covered

| Vector | Description | Status |
|--------|-------------|--------|
| **Prompt Injection** | Direct and indirect prompt injection testing | 🔨 In Progress |
| **Jailbreak Testing** | Multi-turn and single-turn jailbreak assessment | 🔨 In Progress |
| **System Prompt Extraction** | Techniques to extract hidden system prompts | 📋 Planned |
| **RAG Poisoning** | Testing RAG pipelines for document injection attacks | 📋 Planned |
| **Data Exfiltration** | Testing AI agents for data leak vulnerabilities | 📋 Planned |
| **Tool/Function Abuse** | Exploiting AI agent tool-calling capabilities | 📋 Planned |
| **Multi-Agent Attacks** | Attack chains across multi-agent systems | 📋 Planned |

## Project Structure

```
ai-red-team-toolkit/
├── modules/
│   ├── prompt_injection/     # Prompt injection payloads and testers
│   ├── jailbreak/            # Jailbreak techniques and automation
│   ├── extraction/           # System prompt and model extraction
│   ├── rag_poisoning/        # RAG pipeline attack tools
│   └── exfiltration/         # Data exfiltration via AI agents
├── payloads/                 # Curated payload libraries
├── reports/                  # Report templates for engagements
├── docs/                     # Documentation and methodology
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

This toolkit is informed by cutting-edge academic research in AI security:

- **Psychological Jailbreak (HPM)** — Liu & Lin, 2025. Multi-turn psychological manipulation achieving 88.1% ASR across major LLMs. Demonstrates that LLMs inherit exploitable psychological traits from training data.
- **Fine-Tuning Jailbreaks** — Li, Wang & Li, 2025. Three-pronged attack via data poisoning and backdoors achieving 97% ASR on GPT-4.1/4o through fine-tuning interfaces.
- **OWASP Top 10 for LLM Applications** — Industry-standard classification of LLM vulnerabilities.

## Who is this for?

- **Security researchers** testing AI systems
- **Red teamers** expanding into AI attack surfaces
- **Developers** building AI applications who want to test before deploying
- **CISOs and security teams** evaluating AI risk

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
- 📧 contact@cindersecurity.io

---

<p align="center">
  <sub>Built with 🔥 by <a href="https://cindersecurity.io">Cinder Security</a> | Guadalajara, MX</sub>
</p>

