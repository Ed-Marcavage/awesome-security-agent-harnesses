# Contribution Guidelines

Thanks for helping curate this list. The goal is a short list where every entry earned its place, not a directory of everything with "security" and "agent" in the readme.

## What belongs here

The test: an entry belongs here if it is part of the stack you would assemble to run a security agent against a benchmark like Cybench or CyberGym — the harness itself, the analysis tools it calls, the sandbox it executes in, or the benchmark that scores it.

An entry should satisfy all of these:

- **On topic.** It passes the test above. General agent frameworks belong in [awesome-agent-harness](https://github.com/Picrew/awesome-agent-harness), and general-purpose coding agents qualify only if they ship an explicit security mode. Tools for securing AI systems — prompt-injection scanners, model red-teaming, agent guardrails — are out of scope, and belong in the broader AI-security lists.
- **Actually awesome.** You have used it, read it, or can point to real results (found vulnerabilities, published evaluations, competition placement). "Looks interesting" is not enough.
- **Alive.** Maintained, documented, and not archived or deprecated.

## Entry format

```
- [Name](https://example.com) - Description that starts with a capital letter and ends with a period.
```

- Add the entry to the section where it fits best, in alphabetical order within the section.
- Keep the description to one line: what it is and why it matters, not marketing copy.
- Link to the canonical source (repo or project site), not a blog post about it.
- One entry per pull request, unless the entries are closely related.

## Pull request checklist

- [ ] The entry meets the criteria above, and the PR description says briefly why it is awesome.
- [ ] The description follows the format conventions.
- [ ] `npx awesome-lint` passes.
- [ ] You checked the entry is not already on the list.

## Removing entries

Entries that become unmaintained, archived, or superseded should be removed. PRs that prune are as welcome as PRs that add.
