# Vroomi AI Assistant: Security Assessment

Security assessment of Softmicro's Vroomi AI assistant prototype: an internal LLM assistant that answers policy questions and books, cancels and lists rides. Threat-modelled with STRIDE per element, mapped to the OWASP Top 10 for LLM Applications (2026), and tested live against gpt-4o-mini.

**Result:** five findings (two Critical, one High, two Medium) and a **Conditional Go** for agentic features.

## Deliverables

The finished report is the four PDFs in [report/](report/). Their Markdown and Mermaid sources are in [source/](source/), and the test harness is in [harness/](harness/).

| Document | For | Read |
|---|---|---|
| Technical report | Engineers who fix Vroomi: every finding with location, reproduction, fix and verification | [PDF](report/Vroomi_Technical_Report.pdf) · [Markdown](source/Technical_Report.md) |
| Executive summary | The CISO: the decision in two pages | [PDF](report/Vroomi_Executive_Summary.pdf) · [Markdown](source/Executive_Summary.md) |
| Evidence appendix | Every prompt tested, with run counts and rates | [PDF](report/Vroomi_Evidence_Test_Log.pdf) · [Markdown](source/Test_Log.md) |
| System diagram | How Vroomi works, and where each finding sits | [PDF](report/Vroomi_System_Diagram.pdf) · Mermaid: [system](source/Vroomi_System_Diagram.mmd), [findings](source/Vroomi_Vulnerabilities.mmd) |
| Test harness | Rerun every test and the defence comparison | [harness/](harness/) |

## Findings

| ID | Finding | Severity |
|---|---|---|
| VRM-01 | Sensitive account information is exposed to anyone who asks | Critical |
| VRM-02 | Any employee can cancel anyone's trip, and see every trip to choose from | Critical |
| VRM-04 | Asking Vroomi how to cancel a trip cancels it | High |
| VRM-03 | Anyone can read Vroomi's internal documents by asking for a summary | Medium |
| VRM-05 | One employee can plant text in a booking that later appears in another employee's session | Medium (latent) |

## Rerunning the tests

The harness loads the prototype's code from the notebooks Softmicro supplied, which are not included here. Set the notebook paths at the top of `harness/reproduce.py` and `harness/defences.py`, set `OPENAI_API_KEY`, run `uv run python reproduce.py` from `harness/`, and see Appendix A of the technical report.

Assessor: Federico Moran. Analysis and writing assisted by Claude (Anthropic).
