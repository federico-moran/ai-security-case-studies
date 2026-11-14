# AI Security Case Studies

Security assessments of LLM applications and AI agents: threat models, measured test results and remediation guidance written for the people who build and fix these systems.

I'm a cybersecurity engineer with extensive IT experience behind me. My main areas are Active Directory and identity management, vulnerability management, threat hunting, incident response and automation, but I've worked across a lot of other technical areas too. Lately I've been moving into AI security, and these case studies are where I test LLM applications and agents and write up what I find.

## Case studies

| Case study | System | Methods | Course | Status |
|---|---|---|---|---|
| [Vroomi AI Assistant](vroomi/) | Internal LLM assistant that answers policy questions and books, cancels and lists rides | STRIDE threat model, OWASP Top 10 for LLM Applications (2026), live testing | AISF Level 1 capstone | Complete |

## Training: AI Security Fundamentals

Several case studies here come from [**AI Security Fundamentals (AISF)**](https://aisecurityfundamentals.com/curriculum), a three-level training program from [Mileva Security Labs](https://www.milev.ai/fundamentals).

- **[Level 1: Foundation](https://www.milev.ai/fundamentals)**: practical AI threat modeling, attacks, defenses, governance and applied assessment, with hands-on technical exercises. Open to professionals in any field.
- **[Level 2: Strategic](https://www.milev.ai/level2)**: integrating AI security into governance, procurement and organizational risk management. Designed for CISOs, risk managers and leaders.
- **[Level 3: Practitioner](https://www.milev.ai/level3)**: advanced technical AI security, covering adversarial machine learning, simulated attacks on AI systems and building defensive tools. For cyber and AI security professionals; builds on Level 1.

| Level | Status | Case studies |
|---|---|---|
| Level 1: Foundation | In progress | [Vroomi AI Assistant](vroomi/) (capstone) |
| Level 2: Strategic | Planned | – |
| Level 3: Practitioner | Planned | – |

Course systems and lab notebooks belong to the course and are not reproduced here. This repository holds only my own analysis, write-ups and diagrams.

## How these were made

I used Claude (Anthropic) to help analyze the systems and create the assessments. The testing, findings and judgment are mine.

## License

Reports and diagrams are licensed under CC BY 4.0; code under MIT. See [LICENSE.md](LICENSE.md).

## Contact

- LinkedIn: [Federico Moran](https://www.linkedin.com/in/fredmoran/)
- GitHub: [@federico-moran](https://github.com/federico-moran)
