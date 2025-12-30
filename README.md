# Agent Skills for Context Engineering

A comprehensive, open collection of Agent Skills focused on context engineering principles for building production-grade AI agent systems. These skills teach the art and science of curating context to maximize agent effectiveness across any agent platform.

## What is Context Engineering?

Context engineering is the discipline of managing the language model's context window. Unlike prompt engineering, which focuses on crafting effective instructions, context engineering addresses the holistic curation of all information that enters the model's limited attention budget: system prompts, tool definitions, retrieved documents, message history, and tool outputs.

The fundamental challenge is that context windows are constrained not by raw token capacity but by attention mechanics. As context length increases, models exhibit predictable degradation patterns: the "lost-in-the-middle" phenomenon, U-shaped attention curves, and attention scarcity. Effective context engineering means finding the smallest possible set of high-signal tokens that maximize the likelihood of desired outcomes.

## Skills Overview

### Foundational Skills

These skills establish the foundational understanding required for all subsequent context engineering work.

| Skill | Description |
|-------|-------------|
| [context-fundamentals](skills/context-fundamentals/) | Understand what context is, why it matters, and the anatomy of context in agent systems |
| [context-degradation](skills/context-degradation/) | Recognize patterns of context failure: lost-in-middle, poisoning, distraction, and clash |
| [context-compression](skills/context-compression/) | Design and evaluate compression strategies for long-running sessions |

### Architectural Skills

These skills cover the patterns and structures for building effective agent systems.

| Skill | Description |
|-------|-------------|
| [multi-agent-patterns](skills/multi-agent-patterns/) | Master orchestrator, peer-to-peer, and hierarchical multi-agent architectures |
| [memory-systems](skills/memory-systems/) | Design short-term, long-term, and graph-based memory architectures |
| [tool-design](skills/tool-design/) | Build tools that agents can use effectively |

### Operational Skills

These skills address the ongoing operation and optimization of agent systems.

| Skill | Description |
|-------|-------------|
| [context-optimization](skills/context-optimization/) | Apply compaction, masking, and caching strategies |
| [evaluation](skills/evaluation/) | Build evaluation frameworks for agent systems |
| [advanced-evaluation](skills/advanced-evaluation/) | Master LLM-as-a-Judge techniques: direct scoring, pairwise comparison, rubric generation, and bias mitigation |

### Development Methodology

These skills cover the meta-level practices for building LLM-powered projects.

| Skill | Description |
|-------|-------------|
| [project-development](skills/project-development/) | **NEW** Design and build LLM projects from ideation through deployment, including task-model fit analysis, pipeline architecture, and structured output design |

## Design Philosophy

### Progressive Disclosure

Each skill is structured for efficient context use. At startup, agents load only skill names and descriptions. Full content loads only when a skill is activated for relevant tasks.

### Platform Agnosticism

These skills focus on transferable principles rather than vendor-specific implementations. The patterns work across Claude Code, Cursor, and any agent platform that supports skills or allows custom instructions.

### Conceptual Foundation with Practical Examples

Scripts and examples demonstrate concepts using Python pseudocode that works across environments without requiring specific dependency installations.

## Usage

### Usage with Claude Code

This repository is configured as a **Claude Code Plugin**, allowing you to load context engineering skills directly into your agent development environment.

### Installation

1. **Add the Marketplace**
   Run this command in Claude Code to add this repository as a plugin source:
   ```bash
   /plugin marketplace add muratcankoylan/Agent-Skills-for-Context-Engineering

2. Install the **Skills Install** the context engineering suite:
   ```bash
   /plugin install context-engineering@context-engineering-marketplace
   
<img width="1014" height="894" alt="Screenshot 2025-12-26 at 12 34 47 PM" src="https://github.com/user-attachments/assets/f79aaf03-fd2d-4c71-a630-7027adeb9bfe" />

### For Cursor & Codex & IDE

Copy skill content into `.rules` or create project-specific Skills folders. The skills provide the context and guidelines that agent needs for effective context engineering and agent design.

### For Custom Implementations

Extract the principles and patterns from any skill and implement them in your agent framework. The skills are deliberately platform-agnostic.

## Examples

The [examples](examples/) folder contains complete system designs that demonstrate how multiple skills work together in practice.

| Example | Description | Skills Applied |
|---------|-------------|----------------|
| [digital-brain-skill](examples/digital-brain-skill/) | **NEW** Personal operating system for founders and creators. Complete Claude Code skill with 6 modules, 4 automation scripts | context-fundamentals, context-optimization, memory-systems, tool-design, multi-agent-patterns, evaluation, project-development |
| [x-to-book-system](examples/x-to-book-system/) | Multi-agent system that monitors X accounts and generates daily synthesized books | multi-agent-patterns, memory-systems, context-optimization, tool-design, evaluation |
| [llm-as-judge-skills](examples/llm-as-judge-skills/) | Production-ready LLM evaluation tools with TypeScript implementation, 19 passing tests | advanced-evaluation, tool-design, context-fundamentals, evaluation |
| [book-sft-pipeline](examples/book-sft-pipeline/) | Train models to write in any author's style. Includes Gertrude Stein case study with 70% human score on Pangram, $2 total cost | project-development, context-compression, multi-agent-patterns, evaluation |

Each example includes:
- Complete PRD with architecture decisions
- Skills mapping showing which concepts informed each decision
- Implementation guidance

### Digital Brain Skill Example

The [digital-brain-skill](examples/digital-brain-skill/) example is a complete personal operating system demonstrating comprehensive skills application:

- **Progressive Disclosure**: 3-level loading (SKILL.md → MODULE.md → data files)
- **Module Isolation**: 6 independent modules (identity, content, knowledge, network, operations, agents)
- **Append-Only Memory**: JSONL files with schema-first lines for agent-friendly parsing
- **Automation Scripts**: 4 consolidated tools (weekly_review, content_ideas, stale_contacts, idea_to_draft)

Includes detailed traceability in [HOW-SKILLS-BUILT-THIS.md](examples/digital-brain-skill/HOW-SKILLS-BUILT-THIS.md) mapping every architectural decision to specific skill principles.

### LLM-as-Judge Skills Example

The [llm-as-judge-skills](examples/llm-as-judge-skills/) example is a complete TypeScript implementation demonstrating:

- **Direct Scoring**: Evaluate responses against weighted criteria with rubric support
- **Pairwise Comparison**: Compare responses with position bias mitigation
- **Rubric Generation**: Create domain-specific evaluation standards
- **EvaluatorAgent**: High-level agent combining all evaluation capabilities

### Book SFT Pipeline Example

The [book-sft-pipeline](examples/book-sft-pipeline/) example demonstrates training small models (8B) to write in any author's style:

- **Intelligent Segmentation**: Two-tier chunking with overlap for maximum training examples
- **Prompt Diversity**: 15+ templates to prevent memorization and force style learning
- **Tinker Integration**: Complete LoRA training workflow with $2 total cost
- **Validation Methodology**: Modern scenario testing proves style transfer vs content memorization

Integrates with context engineering skills: project-development, context-compression, multi-agent-patterns, evaluation.

## Star History
<img width="1832" height="1324" alt="star-history-20251229" src="https://github.com/user-attachments/assets/153f691a-12db-4fb9-8960-53bc431b202a" />

## Structure

Each skill follows the Agent Skills specification:

```
skill-name/
├── SKILL.md              # Required: instructions + metadata
├── scripts/              # Optional: executable code demonstrating concepts
└── references/           # Optional: additional documentation and resources
```

See the [template](template/) folder for the canonical skill structure.

## Contributing

This repository follows the Agent Skills open development model. Contributions are welcome from the broader ecosystem. When contributing:

1. Follow the skill template structure
2. Provide clear, actionable instructions
3. Include working examples where appropriate
4. Document trade-offs and potential issues
5. Keep SKILL.md under 500 lines for optimal performance

Feel free to contact [Muratcan Koylan](https://x.com/koylanai) for collaboration opportunities or any inquiries.

[![Sponsor via GitHub](https://img.shields.io/badge/Sponsor-muratcankoylan-pink?logo=github-sponsors&style=for-the-badge)](https://github.com/sponsors/muratcankoylan)

## License

MIT License - see LICENSE file for details.

## References

The principles in these skills are derived from research and production experience at leading AI labs and framework developers. Each skill includes references to the underlying research and case studies that inform its recommendations.

