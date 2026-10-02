# Abhiram Bangaru

**AI Agent Quality Engineer** focused on testing tool-calling agents, guardrails, and LLM evaluation.

Hyderabad, India - Open to roles in agent QA / AI testing

---

## What I test

- **Agent behaviour** - tool selection, tool arguments, workflow paths, retries, and failure handling
- **Guardrails and policy** - ownership checks, refund / permission limits, unsafe actions blocked in code (not only in prompts)
- **Adversarial cases** - prompt injection (direct + indirect), social engineering, hallucinated status after tool failures
- **Evaluation harnesses** - deterministic checks first, LLM-as-judge second, pass rates across prompt versions
- **Traces** - SQLite step logs so a failing case can be replayed tool-call by tool-call

Stack I use day to day: **Python**, **Pytest**, APIs/JSON, traces/logs, CI (GitHub Actions). Comfortable with MCP / tool-calling agent loops.

---

## Featured project

### [agentprobe](https://github.com/abhiram-120/agentprobe)

Testing and evaluation harness for a ShopKart support agent (lookup, refunds, FAQ, escalate) plus a suite that tries to break it.

| Area | Covered |
|---|---|
| Tool selection | right tool + args |
| Guardrails | cross-customer data, refund limits, prompt leak canary |
| Prompt injection | ORD-1004 notes (indirect), fake `[SYSTEM]` admin |
| Tool failures | timeout / malformed / empty / wrong schema |
| Eval | v1 vs v2 prompts, markdown report |

**Latest Groq run** (`openai/gpt-oss-20b`): v1 **19/20 (95%)** - v2 **20/20 (100%)**.  
Only v1 failure: indirect injection on ORD-1004; hardened prompt fixed it.

```bash
pytest -m "not llm"                 # unit / policy tests
python -m evals.run_evals --prompts v1 v2
python scripts/show_trace.py <run_id>
```

---

## How I think about agent QA

1. Business rules belong in the **tool layer**, not only the system prompt.
2. Deterministic checks (tool called?, refund state?, leak?) run **before** an LLM judge.
3. Prompt changes need measured regressions (pass rates), not vibes.
4. If a test fails, the first question is: show me the **trace**.

---

## Also exploring

- Bitcoin anomaly detection project (data / ML workflow)
- Prior API and product work (chatbots, support tooling)

---

Open to **AI Agent Quality Engineer** roles (agent workflows, eval suites, guardrails, API testing).
