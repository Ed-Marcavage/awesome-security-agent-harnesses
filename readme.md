# Awesome Security Agent Harnesses [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

> AI agents for pentesting, code audit, fuzzing, vulnerability discovery, and reverse engineering — harnesses, sandboxes, security MCP servers, benchmarks, and evals.

Please read the [contribution guidelines](contributing.md) before opening a pull request.

## Contents

- [What Is a Security Agent Harness](#what-is-a-security-agent-harness)
- [Code Audit Harnesses](#code-audit-harnesses)
- [Pentesting Agents](#pentesting-agents)
- [Fuzzing and Vulnerability Discovery](#fuzzing-and-vulnerability-discovery)
- [DARPA AIxCC Cyber Reasoning Systems](#darpa-aixcc-cyber-reasoning-systems)
- [Agent Tooling and Integrations](#agent-tooling-and-integrations)
- [Agent Sandboxes](#agent-sandboxes)
- [Benchmarks and Evals](#benchmarks-and-evals)
- [Readings](#readings)

## What Is a Security Agent Harness

A security agent harness is everything wrapped around the model: the sandbox it runs in, the analysis tools it can call, the prompts and skills that encode a methodology, and the evals you use to check it. Most of the engineering lives here rather than in the model — or as Cloudflare put it after scaling one across its own fleet, the harness is the bit that lasts.

Agents are good at producing plausible findings and bad at telling which ones are real. An agent will edit the source so its own exploit works, then report the bug it just created. So the metric that matters is not recall, which nobody can measure without already knowing every bug in a codebase, but how few unconfirmed findings reach a human: Cloudflare's pipeline cut 20,799 raw candidates down to 12,057 that survived validation, then folded away another 5,442 as duplicates. A harness that can reproduce a crash, replay an input, or re-run a static analyzer is how you throw out the bad ones before a human ever sees them.

Entries tagged `SKILL.md` are skill packs rather than runnable harnesses: methodology encoded as [Agent Skills](https://agentskills.io) that a general coding agent like Claude Code executes. They live in the section matching what they do.

## Code Audit Harnesses

Harnesses that run coding agents against source code: discovery, triage, validation, and patching.

- [Anthropic Defending Code Reference Harness](https://github.com/anthropics/defending-code-reference-harness) - Reference implementation for autonomous vulnerability discovery and remediation with Claude, with skills for threat modeling, scanning, triage, and patching.
- [audit](https://github.com/evilsocket/audit) - Eight-stage discovery agent built on the Claude Code SDK, combining many narrow agents, deliberate disagreement between them, and an explicit reachability gate.
- [Capital One VulnHunter](https://github.com/capitalone/VulnHunter) - Agentic security tool applying proactive, attacker-first analysis directly to source code.
- [Clearwing](https://github.com/Lazarus-AI/clearwing) - Autonomous source-code hunter that ranks files, fans out specialist agents, and treats sanitizer crashes as ground truth, with a separate network-pentest mode.
- [Cloudflare Security Audit](https://github.com/cloudflare/security-audit-skill) - Six-phase audit skill: parallel hunting agents attack the codebase from different angles, separate agents try to disprove each finding, and fresh agents verify the schema-validated `findings.json` against source. `SKILL.md`.
- [OpenAI Codex Security](https://github.com/openai/codex-security) - CLI and TypeScript SDK for finding, validating, and fixing security vulnerabilities with Codex.
- [OpenHack](https://github.com/openhackai/OpenHack) - Multi-agent scanner running recon, specialist hunts, independent validation, and sandbox and browser verification, using only open-source models.
- [RAPTOR](https://github.com/gadievron/raptor) - Autonomous research framework chaining static analysis, binary analysis, vulnerability validation, exploit generation, and patch writing over a codebase or binary. `SKILL.md`.
- [Trail of Bits Skills](https://github.com/trailofbits/skills) - Skills for security research, vulnerability detection, and audit workflows, distilled from the firm's audit practice. `SKILL.md`.
- [Vercel Labs Deepsec](https://github.com/vercel-labs/deepsec) - Security harness for finding vulnerabilities in a codebase using coding agents.
- [Visa Vulnerability Agentic Harness](https://github.com/visa/visa-vulnerability-agentic-harness) - Agentic SAST pipeline for autonomous vulnerability discovery, remediation, and validation, emitting Markdown and SARIF reports.

## Pentesting Agents

Agents that attack running applications and infrastructure: reconnaissance, exploitation, and proof of impact.

- [AIDA](https://github.com/Vasco0x4/AIDA) - Model-agnostic pentesting agent that reasons over a defined scope, executes in an isolated container, and keeps persistent assessment state across sessions.
- [AWE](https://github.com/stuxlabs/AWE) - Research framework pairing a lightweight orchestration layer with memory-augmented, vulnerability-specific agent pipelines, evaluated on the XBOW benchmark.
- [BlacksmithAI](https://github.com/yohannesgk/blacksmith) - Multi-agent pentesting framework that walks a target from reconnaissance through post-exploitation inside a Docker image preloaded with standard security tooling, driven from either a web UI or a CLI.
- [CAI](https://github.com/aliasrobotics/cai) - Alias Robotics' framework for building cybersecurity agents, with tool and workflow primitives for offensive testing.
- [CyberStrike](https://github.com/CyberStrikeus/CyberStrike) - Offensive-security harness coordinating autonomous agents over signed attack skills, built-in tools, and MCP integrations, mapped to MITRE ATT&CK and OWASP WSTG.
- [hackingBuddyGPT](https://github.com/ipa-lab/hackingBuddyGPT) - TU Wien research framework for writing LLM pentesting agents in roughly 50 lines of code, released alongside reusable Linux privilege-escalation benchmarks and open-access evaluations.
- [HPTSA](https://github.com/uiuc-kang-lab/HPTSA) - Research implementation behind *Teams of LLM Agents can Exploit Zero-Day Vulnerabilities*, using a supervisor agent to coordinate vulnerability-specialized subagents.
- [Nebula](https://github.com/berylliumsec/nebula) - Penetration-testing assistant that automates recon, note-taking, and tool orchestration.
- [NeuroSploit](https://github.com/JoasASantos/NeuroSploit) - Rust harness that turns a URL, repository, or host into an autonomous engagement, selecting only the specialist agents matching the surface and validating findings across models.
- [PentAGI](https://github.com/vxcontrol/pentagi) - Fully autonomous multi-agent pentesting system with Docker isolation, planning and supervision, persistent memory, and a web control plane.
- [Pentest Copilot](https://github.com/bugbasesecurity/pentest-copilot) - Agent that drives a Kali attack box end to end, installing tooling as needed, operating Burp and a real browser, and spawning parallel subagents.
- [Pentest Swarm AI](https://github.com/Armur-Ai/Pentest-Swarm-AI) - Go harness coordinating recon, classification, exploitation, and reporting agents through a shared pheromone blackboard, waking each agent by finding weight rather than a fixed pipeline order.
- [PentestAgent](https://github.com/GH05TCREW/pentestagent) - Black-box testing framework with autonomous and multi-agent modes, attack playbooks, Kali execution, and persistent sessions.
- [PentestCode](https://github.com/s0ld13rr/pentestcode) - Hard fork of OpenCode rebuilt for offense, coordinating a lead strategist and parallel specialist subagents over shared engagement state, with attack-path search across a relationship graph and persistent sessions.
- [PentestGPT](https://github.com/GreyDGL/PentestGPT) - Automated penetration-testing agentic framework powered by large language models.
- [RedAmon](https://github.com/samugit83/redamon) - End-to-end platform chaining recon, exploitation, and post-exploitation over a Neo4j attack graph, then triaging findings, patching the code, and opening pull requests.
- [reverse-skill](https://github.com/zhaoxuya520/reverse-skill) - Security skill router that guides coding agents through repeatable reverse-engineering and penetration-testing workflows with tool bootstrapping and evidence tracking. A recent [Tessl review](https://tessl.io/registry/skills/github/zhaoxuya520/reverse-skill/reverse-skill-router) scored its primary router 75/100 (92% quality), with no impact evaluation and a failed security scan. `SKILL.md`.
- [Shannon](https://github.com/KeygraphHQ/shannon) - AI pentester for web applications and APIs that analyzes source code, identifies attack vectors, and executes real exploits to prove findings.
- [Strix](https://github.com/usestrix/strix) - Open-source AI penetration-testing agent that finds and helps fix application vulnerabilities.
- [Transilience Community Tools](https://github.com/transilienceai/communitytools) - Twenty-six skills and three tool integrations covering the pentest lifecycle from recon to reporting, with a published 104/104 result on the maintainers' CTF benchmark. `SKILL.md`.

## Fuzzing and Vulnerability Discovery

Harnesses that use models to find crashes and generate patches.

- [ChatAFL](https://github.com/ChatAFLndss/ChatAFL) - Protocol fuzzer built on AFLNet that prompts a model for a machine-readable grammar, for richer seed messages, and for new inputs whenever coverage plateaus, published at NDSS 2024 and packaged as a ProfuzzBench artifact.
- [FirmAgent](https://github.com/vul337/FirmAgent) - Hybrid IoT firmware pipeline from Tsinghua's VUL337 group, pairing a device-aware API fuzzer with an LLM taint-analysis agent that turns sink-reaching findings into proof-of-concept exploits, published at NDSS 2026.
- [Fuzz4All](https://github.com/fuzz4all/fuzz4all) - Universal fuzzer using a model as its input generation and mutation engine, with an autoprompting step that tunes the prompt per target so one tool covers many input languages, from the ICSE 2024 paper.
- [OSS-Fuzz-Gen](https://github.com/google/oss-fuzz-gen) - Google's framework for generating and benchmarking fuzz targets with LLMs across C/C++, Java, and Python.
- [PromptFuzz](https://github.com/FuzzAnything/PromptFuzz) - Fuzz-driver generator that mutates prompts in a coverage-guided loop to explore complex API interrelationships, reporting 40.12% branch coverage on its tested libraries, 1.61x OSS-Fuzz's, and 33 confirmed security bugs including three CVEs.

## DARPA AIxCC Cyber Reasoning Systems

The seven finalist systems from the DARPA AI Cyber Challenge, each built to autonomously find and patch vulnerabilities in real open-source code, and each released as a competition snapshot.

- [ARTIPHISHELL](https://github.com/shellphish/artiphishell) - Shellphish's cyber reasoning system, released with its components, pipelines, services, and full deployment stack.
- [Atlantis](https://github.com/Team-Atlanta/aixcc-afc-atlantis) - Team Atlanta's cyber reasoning system that won the final competition.
- [BugBuster](https://github.com/42-b3yond-6ug/42-b3yond-6ug-crs) - Team 42-b3yond-6ug's cyber reasoning system, preserved with the core components and deployment configuration needed to run it.
- [Buttercup](https://github.com/trailofbits/buttercup) - Trail of Bits' second-place cyber reasoning system, pairing an OSS-Fuzz fuzzing campaign with a multi-agent patcher.
- [FuzzingBrain](https://github.com/fuzzingbrain/afc-crs-all-you-need-is-a-fuzzing-brain) - Team all_you_need_is_a_fuzzing_brain's system, pairing coverage-guided fuzzing with agents that reason about suspicious points, build proofs of vulnerability, and dynamically verify every finding.
- [Lacrosse](https://github.com/siftech/afc-crs-lacrosse) - SIFT's multi-agent cyber reasoning system, combining fuzzing and symbolic reasoning to find and patch bugs in C and Java.
- [Robo Duck](https://github.com/theori-io/aixcc-afc-archive) - Theori's third-place cyber reasoning system, released as the complete finals submission.

## Agent Tooling and Integrations

Security capabilities exposed to somebody else's agent: MCP servers, disassembler plugins, and broad skill libraries. These supply the tools and methodology a harness calls; they do not own the agent loop themselves.

- [Anthropic-Cybersecurity-Skills](https://github.com/mukul975/Anthropic-Cybersecurity-Skills) - Community library of 800+ skills across 29 security domains, mapped to MITRE ATT&CK and NIST CSF; not affiliated with Anthropic despite the name. `SKILL.md`.
- [Binary Ninja Headless MCP](https://github.com/mrphrazer/binary-ninja-headless-mcp) - Headless Binary Ninja MCP server exposing 180 analysis tools to agents.
- [Burp Suite MCP](https://github.com/PortSwigger/mcp-server) - PortSwigger's own MCP server, connecting agents to Burp Suite's proxy, scanner, and repeater.
- [Claude Code CyberSecurity Skills](https://github.com/Masriyan/Claude-Code-CyberSecurity-Skill) - Nineteen skills spanning offensive security, defensive operations, reverse engineering, threat hunting, and SOC automation. `SKILL.md`.
- [DAILA](https://github.com/mahaloz/DAILA) - Decompiler-agnostic plugin for using AI assistance inside your decompiler.
- [Gepetto](https://github.com/JusticeRage/Gepetto) - IDA plugin that queries language models to explain and rename decompiled functions.
- [HexStrike AI](https://github.com/0x4m4/hexstrike-ai) - MCP server that gives agents a large toolkit of offensive security tools for recon, scanning, and exploitation.
- [IDA Pro MCP](https://github.com/mrexodia/ida-pro-mcp) - MCP server exposing IDA Pro decompilation, cross-references, and type inference to coding agents.
- [LLM4Decompile](https://github.com/albertan017/LLM4Decompile) - Open models and pipeline for decompiling binary code into readable C.
- [ReVa](https://github.com/cyberkaida/reverse-engineering-assistant) - Ghidra extension providing an MCP server for agent-driven reverse engineering.

## Agent Sandboxes

Isolation for running agent-generated code and untrusted targets.

- [E2B](https://github.com/e2b-dev/E2B) - Sandboxed cloud environments purpose-built for running agent-generated code.
- [Firecracker](https://github.com/firecracker-microvm/firecracker) - AWS's minimal microVM monitor, a common hardware-isolation primitive for running untrusted code.
- [gVisor](https://github.com/google/gvisor) - Google's application kernel that intercepts syscalls to sandbox untrusted workloads without a full VM.
- [Microsandbox](https://github.com/microsandbox/microsandbox) - Local-first microVM runtime for executing untrusted agent code.
- [Sandbox Runtime](https://github.com/anthropic-experimental/sandbox-runtime) - Anthropic's lightweight tool for enforcing filesystem and network restrictions on agents.

## Benchmarks and Evals

Task sets and ground truth for measuring whether a harness actually works.

- [ADR](https://github.com/uber/ADR) - Uber's agent detection and response system, including a benchmark of 300+ agent-attack tasks across 133 MCP servers.
- [AIRTBench](https://github.com/dreadnode/AIRTBench-Code) - Dreadnode's benchmark measuring autonomous AI red-teaming capability.
- [ARVO](https://github.com/n132/ARVO) - Atlas of reproducible open-source vulnerabilities, used as ground truth for patching agents.
- [CVE-GENIE](https://github.com/BUseclab/cve-genie) - Boston University multi-agent framework that reconstructs a vulnerable environment from a CVE entry and produces a verifiable exploit, [reproducing 428 of 841 CVEs](https://arxiv.org/abs/2509.01835) published in 2024-2025 at an average of $2.77 each.
- [Cybench](https://github.com/andyzorigin/cybench) - Framework for evaluating language model agents on 40 professional CTF tasks.
- [CyberGym](https://github.com/sunblaze-ucb/cybergym) - Berkeley's large-scale benchmark evaluating agents on real-world vulnerability reproduction.
- [HackSynth](https://github.com/aielte-research/HackSynth) - Autonomous pentesting agent released with two CTF benchmark sets of 200 challenges drawn from PicoCTF and OverTheWire.
- [Linux Privilege-Escalation Benchmark](https://github.com/ipa-lab/benchmark-privesc-linux) - Reproducible local privilege-escalation scenarios from the hackingBuddyGPT team, used as the ground truth in their published agent evaluations.
- [NYU CTF Bench](https://github.com/NYU-LLM-CTF/nyuctf_agents) - D-CIPHER and baseline agents for the NYU CTF benchmark.

## Readings

Writing that has shaped how these harnesses get built. Same bar as the tools: results, not takes.

- [Build Your Own Vulnerability Harness](https://blog.cloudflare.com/build-your-own-vulnerability-harness/) - How Cloudflare grew a single audit skill into a fleet scanner across 128 repos in six weeks: externalized state in SQLite for resumability, each agent held under 25% of its context window, one model hunting and a different model judging, and deduplication given its own agents. Reports that a single skill run finds only about half the bugs of repeated runs.
- [Defend Against Frontier Cyber Models](https://blog.cloudflare.com/frontier-model-defense/) - Cloudflare's defensive architecture for a world where models find, chain, and prove exploits faster than teams can patch: ML attack scoring ahead of signature rules, positive-security API schema validation, and containment as the layer that matters once a bug lands. The blue-team counterpart to the harness posts.
- [Patterns and Problems in Emerging Multiagent Systems](https://www.anthropic.com/research/multiagent-systems) - Anthropic research on coordination failures and swarm behavior among agents, including a vulnerability-discovery experiment where a coordinated swarm found 266 vulnerabilities across 15 open-source projects against 21 for independent parallel agents.
- [Project Glasswing: What Mythos Showed Us](https://blog.cloudflare.com/cyber-frontier-models/) - What Cloudflare saw pointing a frontier security model at more than fifty of its own repositories, and the four lessons that pushed it toward a harness: scope each task tightly, put a second agent in deliberate disagreement with the first, ask "is this buggy" and "can an attacker reach it" separately, and fan out then deduplicate. Notes that a single agent session covers roughly a tenth of a percent of a 100,000-line repository before compaction starts discarding findings.
- [Towards Cybersecurity SuperIntelligence: What's the Best Harness for Cybersecurity?](https://arxiv.org/abs/2605.28334) - Benchmarks five agent scaffolds on 33 cybersecurity challenges and finds no single harness wins; a blackboard architecture combining structurally diverse scaffolds covers 57.6% of problems against 45.5% for the best individual scaffold.
- [Turning LLM Memory into Program Analysis](https://pwning.systems/posts/llm-memory-program-analysis/) - Reframes long-running vulnerability research as a Datalog problem so the model handles fuzzy fact extraction while a database does deterministic reasoning and auto-invalidates conclusions when premises change, cutting context 38x and beating full-context prompting on adversarial memory benchmarks.
