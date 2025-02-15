---

title: LLM-based Code Assistants
author: Jiří Bajer
format: revealjs
theme: league
highlight-style: base16-tomorrow
defaultTiming: 140
width: 1024
height: 768

---

## 🔮 LLM-based Code Assistants 🪄

Jiří Bajer, Jakub Urban, Peter Hozák, Petr Glaser

---

## 🫀 Anatomy

- LLM for **chat** and tool execution (*)
- Low-latency LLM for **autocompletion** (**)
- **Context retrieval** (codebase, IDE, AST, shell, web)
- Prompt to generate code + **reasoning**
- Preview + apply the proposed changes

> (*) _Reinf. Learning from Human Feedback_<br/>
> (**) _Fill In The Middle training objective_

note: Components needed for building from scratch. Autocompletion and context retrieval vs. plain LLM chat. Reasoning uses LLM to find keywords for fuzzy search.

---

## 🤩 Use Cases

- Autocomplete for repeating boilerplate
- Generate tests, docs, commit messages, IaC
- Prototype, code review, refactor
- Explain and onboard, troubleshoot

> While respecting the existing coding style

note: Complements with linter and type checker. Needs supervision, can hallucinate.

---

## 🧐 Context is the King

- Finetuning => **HOW** to code in \<language\>
- Context => **WHAT** option to pick

> Auto-selection of context for chat query<br/>

- Identifiers and type annotations
- Docstrings/comments/README/URL/ticket

note: End of debates whether to document or not. Finetuning only for under-represented languages like COBOL.

---

## 🤮 SLOP

LLM picks the next word which:

- Is the most probable/expectable
- Best matches the existing context
- Adds the least amount of surprise

> Doesn't add any new knowledge!<br/>
> (unless is hallucinating)

note: Docstring derived from implementation is useless. Rise of SLOPpy PRs from lazy devs.

---

## 🪓 CHOP/ChatOPS

- For prototyping and tiny projects
- Refactor/review selected range

> LLM loses focus when context gets longer<br/>
> LLM can obey only few constraints at once<br/>
> LLM can get stuck and run in circles

note: 80/20 rule: LLM sketches, human polishes. No groundbreaking change (at least yet).

---

## 🪤 Pitfalls

- Codebase leaking to LLM training 😱
- Data retention policy and jurisdiction
- Fixed price but token consumption limits
- Latency of LLM middleware (AWS Bedrock)
- Pollution by opensource with viral license
- Missing SSO and central RBAC

note: TOS:DR, middleman is fair but uses cheap LLM subscription.

---

## 🤹🏻 Practical Experience ✨

note: Panelists share their preferred tool + concrete use cases

note: My use cases:
note: + Adding attestations and SBOM to OCI images (me: GHA, found Dockerfile)
note: + Autocomplete for SQLAlchemy queries in DAO methods
note: + PBX simulator (offers library reuse, finds user list for SIP registration, adds missing fields)
note: + Fake replacement for a service from reverse-engineered JSON payload + configure its counterpart
note: + Dockerize a Java web service (me: GitHub repo)
note: - Used Pydantic v1 syntax in Pydantic v2 codebase (after validator, ConfigDict(extra="allow"))
note: - Python 3.12 generics (binding of service and its config + type introspection-based instantiation of config)
note: - Hallucinated POST method in tests instead of PUT

note: Questions:
note: - Where are the limits of current technology? (what works, what not yet)
note: - How well the context works for large legacy codebase?
note: - Does your employer know you are using an assistant? (impact on expectations)
note: - How to justify the investment? (productivity gain not measurable)
note: - How did the internal PoC/evaluation look like?
note: - Have you tried local LLM or private serving? (performance and cost)
note: - Did you change yor opinion on comments in code?

---

## 🎤 Questions and Opinions 🫵🏻

---

## 🔮 Thank You 🪄
