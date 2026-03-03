# Job Search Skill Plan

## Goal
Create a public, shareable `SKILL.md` version of the jobs workflow for users who are not comfortable with programming or command line tools, while continuing the Ruby path in parallel.

## Context
- This is a dual-path effort:
  - Path A: keep and continue improving Ruby automation (`jobs_agent.rb` and related scripts).
  - Path B: publish a Skill-first workflow that can run conversationally in Codex or Claude Code.
- The public Skill should be easy to adopt from a GitHub repo and support ongoing updates that can be shared on LinkedIn.

## Confirmed Decisions From Feedback
1. Prompt structure split:
   - Separate prompt content into configurable sections plus a general baseline section.
   - Keep personal/private section hidden and not bundled in the public release.
   - Mechanism for private injection will be added later when provided.
2. Input mechanism change:
   - Do not rely on local file reads for job descriptions.
   - Primary input path should be job listing URL.
   - Browser-assisted workflows (Claude/ChatGPT browser tooling) are expected for pages that block direct fetch.
3. Drop high-friction setup item:
   - Exclude functionality that requires heavy per-user configuration effort.
4. User customization required:
   - Users must be able to customize style and boilerplate messages.
   - Skill should include a guided setup flow:
     - explain how to customize;
     - offer to generate initial style/boilerplate from a short user prompt;
     - save output in user-editable sections.
5. Item 7 removed:
   - No separate split mode required for that item.

## What the Skill Should Replace
- Replace prompt intelligence and structured output behavior currently driven by `jobs_prompt.txt`:
  - role suitability scoring instructions;
  - tone/style rules;
  - required output sections;
  - guardrails on hallucinations and extra output.
- Keep Ruby responsible for scripting/orchestration where needed.

## Public Skill Design (Planned)
1. `SKILL.md` with:
   - purpose and usage;
   - required inputs (`job_url` or pasted job text fallback);
   - output contract;
   - customization workflow.
2. `templates/` folder:
   - baseline prompt section files (public).
   - editable style/boilerplate templates for users.
3. private profile mechanism (placeholder for now):
   - documented extension point for non-public personal profile injection.
4. onboarding flow in skill instructions:
   - ask user for writing preferences;
   - optionally generate starter style profile and boilerplates;
   - confirm and proceed with scoring + draft generation.

## URL Ingestion Strategy
1. Preferred:
   - user provides listing URL;
   - assistant retrieves listing text when tooling allows.
2. Fallback:
   - if fetch fails or content is blocked, user pastes job text manually.
3. Normalization:
   - convert extracted listing content into a standard internal block before scoring and drafting.

## Release Plan
1. Build first public Skill version in repo with clear README usage examples.
2. Include a minimal quick-start path that requires no coding.
3. Add versioned changelog entries for iterative updates.
4. Use LinkedIn update cadence tied to version milestones and improvements.

## Out of Scope for Initial Public Skill
- Complex per-user local environment setup.
- Tight coupling to local filesystem job description files.
- Full replacement of Ruby automation scripts.

## Immediate Next Build Steps
1. Draft Skill file structure and baseline prompt section files.
2. Define configuration schema for style and boilerplate customization.
3. Implement onboarding instructions for collecting user preferences.
4. Add URL-first intake instructions with manual-paste fallback.
5. Validate output format consistency against current jobs workflow expectations.
