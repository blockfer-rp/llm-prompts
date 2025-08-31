# LLM Architecture Prompts - Guide

## Overview

Hey! 👋 This collection of prompts helps us maintain architectural consistency and code quality when working with LLMs on our codebase. These aren't rigid rules—think of them as our best practices that have proven effective, especially with large, established codebases.

**Quick tip:** These prompts shine with mature codebases but also work brilliantly when starting new applications. Just remember to guide your LLM to follow CLEAN architecture and SOLID principles, always favoring practical solutions over textbook theory.

## LLM INSTRUCTIONS 

### Technical Philosophy
- Strong advocate for CLEAN and DDD Architecture with SOLID principles
- Prioritize modular, well-structured code architecture that prioritizes the practical design for the discipline
- Always strive to find the root fundamental architectural issue

### General Guidelines
- Focus solely on the requested changes or feature request—no testing/validation code
- Preserve all existing features unless explicitly told otherwise
- Always return complete, production-ready code
- Ask clarifying questions before making assumptions
- Add clear inline documentation for maintainability
- Prioritize clean implementations without fallback logic

## The Workflow

### 1. 🔍 Start with Analysis (`analyze_codebase.md`)

**When to use:** Always start here! This warms up the LLM with your target components.

**Pro tip:** Include more context than you think you need—it's better to over-communicate than under-communicate. The LLM performs better with comprehensive context about your system's architecture.

**Usage:**
```
Feed the prompt with your component list in place of $ARGUMENTS
```

### 2. 🎨 Explore Design Options (`architectural_solutions.md`)

**When to use:** Before implementing any significant feature or refactor.

**Why it matters:** This ensures all possible design approaches are evaluated. Remember, the LLM doesn't know your future roadmap, so it's crucial to:
- Evaluate each proposed solution carefully
- Ask follow-up questions about scalability
- Consider how each option aligns with upcoming features

**Important note:** Don't just accept the first recommendation—dig deeper!

### 3. 📋 Create Formal Documentation (`feature_request.md`)

**When to use:** Once you've settled on an architectural approach.

**Key benefit:** This creates a comprehensive document capturing all context and design decisions—invaluable when you're running low on context or need to continue implementation in a new session.

**What it produces:** A formal feature request document that any fresh LLM session can understand.

### 4. 📝 Build the Implementation Plan (`implimentation_plan.md`)

**When to use:** With your feature request document ready.

**What you get:** A detailed, phase-by-phase breakdown of the implementation with specific file changes, methods to update, and clear action items.

**Remember:** This is your roadmap—make sure it's thorough!

### 5. 🔨 Execute the Refactoring (`implimentation_refactoring.md`)

**When to use:** Time to code! This begins the actual implementation.

**Output varies by platform:**
- **Claude Code:** Will update files directly in your workspace
- **Web Interface:** Provides complete file contents for manual updating

**Important:** This generates FULL source code—no placeholders or stubs!

### 6. ✅ Validate Your Changes (`implimentation_validator.md`)

**When to use:** After implementation, especially crucial for large codebases.

**How to prepare:** Generate a comprehensive diff for the LLM to analyze:
```bash
git add -N . && git diff HEAD > all_changes.txt
```

**What it does:** Cross-references your changes against the implementation plan, ensuring nothing was missed and no legacy code remains.

## Best Practices

### Context is King
The more context you provide upfront, the better your results. Don't be shy about including seemingly tangential information—it often proves valuable.

### Question Everything
These prompts generate suggestions, not commandments. Use your expertise to evaluate and adjust recommendations based on your specific needs.

### Session Management
If you're working on complex features:
- Use the feature request document as a checkpoint
- Start new sessions with the feature request for context continuity
- Keep your implementation plans handy for reference

### Git Workflow Integration
Consider creating a branch for each architectural exploration phase:
- `feature/analyze-[component]`
- `feature/design-[component]`
- `feature/implement-[component]`

## Flexibility Encouraged!

These prompts are tools, not rules. Feel free to:
- Modify them for your specific needs
- Combine steps when working on smaller features
- Skip steps that don't add value to your current task
- Add your own prompts to the collection

## Quick Reference

| Prompt | Purpose | Key Output |
|--------|---------|------------|
| `analyze_codebase.md` | Understand current architecture | Dependency map & patterns analysis |
| `architectural_solutions.md` | Explore design options | 3 solutions with trade-offs |
| `feature_request.md` | Document decisions | Formal feature specification |
| `implimentation_plan.md` | Plan the work | Phase-by-phase task list |
| `implimentation_refactoring.md` | Execute changes | Complete source code |
| `implimentation_validator.md` | Verify implementation | Validation report & checklist |

## Getting Started

1. Clone this repository
2. Start with `analyze_codebase.md` for your target components
3. Follow the workflow above, adapting as needed
4. Share improvements with the team!

---

*Remember: These prompts help us maintain quality and consistency, but your judgment and expertise are irreplaceable. Use them as guides, not gospel.*

**Happy coding! 🚀**