# GitHub Copilot for Agentic Software Development

### A practical brief for a semi-technical audience

**The core idea:** GitHub Copilot can help a team move from a software idea to a
reviewable, tested change. It can inspect a codebase, help define requirements,
draft a plan, implement bounded tasks, coordinate other agents, and explain
failed checks. It does not replace engineering judgment: people approve the
plan, inspect the changes, and use tests and CI—not an agent's assurance—to
decide whether the work is correct.

## The lab day in one example

The workshop uses KosKo, a fictional storefront, to add product sorting by
price. The feature must work with existing search and category filters without
breaking the cart or checkout. That small example demonstrates the full
development loop:

1. **Specify before editing.** In the Copilot App's **Interactive** mode, ask
   Copilot to inspect the existing code and help define observable behavior.
   Resolve details such as default order, equal-price behavior, filter
   interaction, reset behavior, accessibility, and errors.
2. **Plan for review.** In **Plan** mode, turn the agreed behavior into a
   reviewable specification and bounded tasks. The workshop separates a shared
   sorting contract, API work, UI work, and integration, with dependencies,
   owned files, prohibited areas, and focused checks. Review and revise the
   Plan before implementation.
3. **Implement with appropriate autonomy.** Use **Interactive** for closer
   steering or **Autopilot** for clear, approved tasks. The built-in
   `/orchestrate` skill can coordinate independent tasks in isolated sessions
   or worktrees. Keep file ownership separate and review each agent's actual
   changes.
4. **Integrate and verify.** Run focused tests, the full check, and browser
   checks against the shopper journey. Verify a deployment separately if one
   is in scope; a local preview is not proof of deployment.
5. **Delegate and automate carefully.** A cloud agent can take a narrow GitHub
   issue and return a change for review. GitHub Agentic Workflows can analyze a
   failed CI run and suggest regression tests. In the lab, deterministic CI
   still decides pass or fail; the workflow is limited to explaining evidence
   and proposing next steps.

## Copilot capabilities at a glance

| Capability | Useful for | Human responsibility |
|---|---|---|
| **Interactive mode** | Exploring code, clarifying requirements, and iterating with guidance. | Confirm expected behavior and keep changes in scope. |
| **Plan mode and canvas** | Making a specification and task breakdown visible before code changes. | Check acceptance criteria, dependencies, ownership, and risks. |
| **Autopilot** | Executing clear, approved work with less step-by-step direction. | Review the diff and evidence. Autonomy does not grant extra permissions. |
| **Copilot Fusion** | App model orchestration, which may use one model or several. | Treat availability and output quality as variable; this workshop is not a benchmark. |
| **Orchestration and Fleet** | Coordinating multiple agents on independent work. | Keep work isolated, ownership non-overlapping, and integration reviewed. |
| **Cloud agent** | Taking a bounded task from a GitHub issue and returning a reviewable change. | Review the pull request, requested revisions, and test results. |
| **GitHub Agentic Workflows** | Responding to workflow events, such as explaining a failed test. | Verify explanations against logs; treat suggestions as hypotheses. CI remains authoritative. |

## Guardrails for dependable results

- **Bound every task:** state the goal, acceptance criteria, allowed and
  prohibited files, and checks to run.
- **Review before acting:** inspect the Plan before implementation and the
  actual diff before integration or merge.
- **Separate suggestion from evidence:** agent explanations are not proof.
  Use test output, CI, review, and deployment checks tied to the change.
- **Preserve security controls:** use least-privilege workflow permissions,
  GitHub OIDC for Azure, protected environments, and required human approvals.
  Do not add long-lived credentials or bypass checks.
- **Be transparent about limitations:** account policy, model access, or
  deployment setup may prevent an exercise. Record unavailable capabilities
  honestly rather than presenting them as successful.
- **Keep work traceable:** connect issues, plans, pull requests, commits, and
  exact validation results.

## Takeaway

Use Copilot in a **specify → plan → implement → review → verify** loop. It can
reduce the effort of understanding and changing software, while people retain
control over scope, permissions, quality decisions, and proof that the result
works.

## Workshop references

- [Workshop overview and setup](README.md)
- [Lab 1: Spec-driven development in the Copilot App](docs/labs/01-SDD-with-the-GHCP-app.md)
- [Lab 2: Multi-agent orchestration](docs/labs/02-multi-agent-orchestration.md)
- [Lab 3: Build, test, and deploy](docs/labs/03-build-test-deploy.md)
- [Lab 4: Cloud agent](docs/labs/04-cloud-agent.md)
- [Lab 5: Agentic workflows](docs/labs/05-gh-aw.md)
- [Optional capstone](docs/labs/optional-capstone.md)
