# Onboarding

- Set expectations with your new manager from the start
- Setup 1:1s day one

## First 5 days

- **By day 5, learn to commit:** Basics of compiling, running, modifying, debugging, and committing changes
- Document all the tribal knowledge you can
- Once code is up and running, push a small fix (go through every part of the process of committing that change)
  - Commit to the right branch
  - Request a PR
  - Run the tests
  - Update the bug tracking system
  - ...

## First 30 days

- **By day 30, learn the process:** Go through one or two development cycles / sprints / units of development time
- Understand how different meetings are run, how estimates work, how completed work is reviewed, etc.
- Get a sense of the shipping process as well
- Know your repos
- Know your pipelines
- Know your process to take in work
- Know your backlog: Understand what decisions have already been discussed and why

## First 60 days

- Show your personality:
  - How do you approach work?
  - How can you make the team process better?
  - Do you document your "Today I learned"?
  - What's in your toolbelt?
  - What is your definition of done?

## First 90 days

- **By dat 90, learn the code:** Learn enough of the code to be comfortable taking on larger tasks, and have a general idea of the strengths and weaknesses of the architecture
- "Know where to look"
- Do you follow through to get your ideas past the finish line?
- Do you leave work unfinished?
- Have you identified and proposed in a compelling way ways to improve our process/business?
- Do your day to day work and exceed expectations

---

- Rule of thumb: Expect solid contributions after 3 months
- Prioritize up-to-date docs, async Q&A channels, and low-risk tasks
- Adopt "cautious curiosity": Learn via small, observable changes
- Build trust with 1-2 dependable PRs daily

## Principles

- Mindset: Fresh eyes spot issues; note everything (mannerism, debt hotspots)
- Habits: Weekly 1hr note review (e.g., Mondays); living doc for rewrites/ideas
- PR Rules: Atomic changes, tests/migrations, feature flags, clear descriptions (trade-offs, issue links)
- Avoid Pitfalls: No blind refactors (mind Chesterton's Fence); always test/CI; no big changes without rollout plans

## First 5 days

- Goal: Run local setup/tests; create a high-level map; aim for 1-2 small PRs
- Checklist:
  - [ ] Run code and tests; note pains (git, configs, flags, failing tests)
  - [ ] Map code owners: Use code owner files, PR authors, commit history
  - [ ] Identify errors/alerts, low-test/buggy modules, approvers, and how to deploy/rollback
- Read `README`, `CONTRIBUTING`, design docs, recent PRs, architecture diagrams
- Understand overall structure:
  - `cloc . --by-file` for big files/ratios
  - `git grep` key classes; review tests/CI for intent/deployment
  - Visualize the system
- High-level trace:
  - Services: Interactions, boundaries, goals, deploy/workflow
  - End-to-end API call: Logs/debugger/breakpoints; production metrics/telemetry
  - Break things in dev: Explore failure modes, add new tests
- Ship stuff: Docs, linting, flaky fixes

## First 30 days

### Team and process
### Codebase

- Goal: Deepen understanding; 5+ merged PRs; end-to-end intuition; team map
- Team:
  - 30min chats (manager list): 25min their world (direction/wins, system/owners, experts); 3min challenges; 2min next names. Repeat to exhaustion.
  - Pair: Workflows/files/debug; "why" on tasks/business.
  - Monitor: Chats, incidents/alerts.
- Codebase:
  - Summarize sections: Functions (input/output/gaps), patterns/abstractions.
  - Build: Diagrams (flows/relations); command cheatsheet; domain notes.
  - Explore: Tests/IDE (hierarchy/usages/hints); commits/PRs for "why".

Reflect: System desc? Interactions? Surprises/gaps?

Contribute: Templated issues (logs/fixes); docs/runbooks.
- 

## First 60 days

### Team and process
### Codebase

- Goal: Consistent PRs; basic ownership
- 

## First 90 days

### Team and process
### Codebase

- Goal: Own sub-system, advocate for improvements
- 

## Ongoing

- 

## Credits

- [https://medium.com/runkeeper-everyone-every-run/better-short-term-goals-for-new-engineering-hires-9a180f1ebc0f](https://medium.com/runkeeper-everyone-every-run/better-short-term-goals-for-new-engineering-hires-9a180f1ebc0f)
- [https://www.reddit.com/r/devops/comments/zdlrwk/whats_generally_in_your_306090_day_plan/](https://www.reddit.com/r/devops/comments/zdlrwk/whats_generally_in_your_306090_day_plan/)
