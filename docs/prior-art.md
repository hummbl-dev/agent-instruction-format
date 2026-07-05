# Prior Art and Adjacent Ecosystem

This document collects public prior art and adjacent ecosystem references for
agent instruction formats. It is descriptive, not prescriptive.

## Non-canon note

Listing an entry here is **not** an endorsement, adoption, or canonization. It
only records that the thing exists, is public, and is relevant to the design
space. Vendor formats are referenced as prior art, not as normative standards.
No claim of ownership is made over any name, term, or concept below.

## Vocabulary

Working vocabulary used in this repo (descriptive only):

- **instruction** — agent-facing directive material, version-controlled and
  reviewable.
- **system prompt** — vendor term for instructions injected at the system/role
  level of a chat completion.
- **system message** — OpenAI's term for a message with the `system` role.
- **prompt template** — a parameterized prompt with variable placeholders.
- **signature** — a declarative input/output contract for a language-model call
  (DSPy-style).
- **schema** — a machine-checkable description of a structure (e.g. JSON Schema).
- **convention** — a project-local, file-based instruction understood by a tool
  (e.g. `CLAUDE.md`, Cursor rules).

## Key concepts

- **Instruction hierarchy** — ranked ordering of instructions where lower levels
  override higher levels (e.g. system > user > task).
- **System vs user instructions** — distinction between role-level context and
  turn-level directives.
- **Prompt inheritance** — whether child/derived contexts inherit parent
  instructions.
- **Override rules** — how conflicting instructions are resolved.
- **Context window management** — budgeting instruction size against available
  model context.
- **Instruction versioning** — tracking changes to instruction material over
  time.

## Public prior art

### OpenAI System Messages

- **What it does:** Defines a `system` role message in the Chat Completions API
  that sets model behavior, persona, and constraints for a conversation.
- **Relevance:** Canonical example of system-level instruction injection and the
  system/user role split.
- **Docs:** https://platform.openai.com/docs/guides/text-generation

### Anthropic System Prompts

- **What it does:** Accepts a top-level `system` parameter on Messages API
  requests, separate from the user/assistant turns.
- **Relevance:** Demonstrates system instructions as a first-class, isolated
  field rather than a role within a message list.
- **Docs:** https://docs.anthropic.com/en/docs/build-with-claude/prompt-engineering/system-prompts

### Gemini System Instructions

- **What it does:** Accepts `system_instruction` on Gemini API requests to set
  role and behavior.
- **Relevance:** Another vendor variant of system-level instruction injection,
  useful for comparing field naming and placement.
- **Docs:** https://ai.google.dev/gemini-api/docs/system-instructions

### DSPy Signatures

- **What it does:** Declares a typed input/output contract for a language-model
  call (`"question -> answer"`), compiled into prompts and demonstrations.
- **Relevance:** Prior art for declarative, schema-like instruction contracts
  rather than free-text prompts.
- **Docs:** https://dspy.ai/learn/programming/signatures/

### BAML Schemas

- **What it does:** A schema language for declaring typed LLM functions,
  prompts, and client configurations.
- **Relevance:** Prior art for structured, typed prompt declarations with
  validation.
- **Docs:** https://docs.boundaryml.com/

### Promptfoo Configs

- **What it does:** A config-driven framework for prompt evaluation, asserting
  outputs against test cases.
- **Relevance:** Prior art for treating prompts as versioned, testable
  artifacts with assertions.
- **Docs:** https://www.promptfoo.dev/docs/configuration/

### LangChain Prompt Templates

- **What it does:** Provides parameterized prompt templates (`PromptTemplate`,
  `ChatPromptTemplate`) with variable substitution.
- **Relevance:** Prior art for prompt templating and reusable prompt objects.
- **Docs:** https://python.langchain.com/docs/concepts/prompt_templates/

### LlamaIndex Prompt Templates

- **What it does:** Offers prompt templates integrated into retrieval and query
  pipelines.
- **Relevance:** Prior art for prompts composed into larger agent/RAG
  pipelines.
- **Docs:** https://docs.llamaindex.ai/en/stable/module_guides/models/prompts/

## Adjacent ecosystem

### Pydantic AI System Prompts

- **What it does:** An agent framework that accepts `system_prompt` (string or
  callable) on an `Agent`, with dependency injection.
- **Relevance:** Adjacent example of system prompts as a typed, composable agent
  parameter.
- **Docs:** https://ai.pydantic.dev/agents/#system-prompts

### Agno Instructions

- **What it does:** An agent framework that accepts `instructions` on an agent
  to shape behavior.
- **Relevance:** Adjacent example of agent-level instruction fields.
- **Docs:** https://docs.agno.com/agents/introduction

### OpenAI Agents SDK Instructions

- **What it does:** The OpenAI Agents SDK accepts `instructions` (string or
  callable) on an `Agent`, plus handoffs and guardrails.
- **Relevance:** Adjacent example of instructions as a first-class agent
  property with routing.
- **Docs:** https://openai.github.io/openai-agents-python/agents/

### Cursor Rules

- **What it does:** Project-local rule files (`.cursor/rules`) that give the
  Cursor editor agent context about a codebase.
- **Relevance:** Prior art for file-based, project-scoped agent conventions.
- **Docs:** https://cursor.com/docs/context/rules

### Claude Code CLAUDE.md

- **What it does:** A project-root `CLAUDE.md` file that Claude Code reads for
  project context and conventions.
- **Relevance:** Prior art for convention-style, file-based agent instructions.
- **Docs:** https://docs.claude.com/en/docs/claude-code/memory

### Aider Conventions

- **What it does:** Aider reads `CONVENTIONS.md` and similar files to guide
  coding conventions during agentic edits.
- **Relevance:** Prior art for convention files that shape agent behavior
  without a formal schema.
- **Docs:** https://aider.com/docs/config/options.html
