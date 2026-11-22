# product-bench

**Status:** In Progress

Product management skills that draft, so PMs can decide.

product-bench takes a feature from product brief to a ready-to-build engineering project. Each skill produces a draft, and a person approves it before the next step starts. The AI handles the document work. You keep the decisions.

Works with Claude Code and any agent that supports the [Agent Plugins](https://agent-plugins.org/) standard, including Cursor, VS Code, GitHub Copilot and Codex. Packaged with [fanout](https://github.com/taylortyler-1/fanout).

## The idea: draft, don't decide

Most AI product tools try to write the final version. product-bench doesn't. Every skill is named draft-* because nothing it produces is final until a person approves it.

- People own the problem. The brief, which says who has the problem and why it matters now, comes from the PM. draft-product-brief asks questions and organizes your answers. It never invents the problem.
- Every step has an approver. Each draft is reviewed before it feeds the next skill.
- Engineers own the build. The workflow stops at the engineering project. Developers write the tickets and decide how the feature gets built.
- Requirements are testable. User stories come with Gherkin scenarios, so reviewers check concrete behavior instead of skimming prose.