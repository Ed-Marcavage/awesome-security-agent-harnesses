# Awesome Security Agent Harnesses [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

> AI agents for pentesting, code audit, fuzzing, vulnerability discovery, and reverse engineering — harnesses, sandboxes, security MCP servers, benchmarks, and evals.

Please read the [contribution guidelines](contributing.md) before opening a pull request.

## Contents

- [What Is a Security Agent Harness](#what-is-a-security-agent-harness)
- [Code Audit Harnesses](#code-audit-harnesses)
- [Pentesting Agents](#pentesting-agents)
- [Fuzzing and Vulnerability Discovery](#fuzzing-and-vulnerability-discovery)
- [Reverse Engineering Agents](#reverse-engineering-agents)
- [Agent Sandboxes](#agent-sandboxes)
- [Benchmarks and Evals](#benchmarks-and-evals)

## What Is a Security Agent Harness

A security agent harness is everything wrapped around the model: the sandbox it runs in, the analysis tools it can call, the prompts and skills that encode a methodology, and the evals you use to check it. Most of the engineering in these systems lives here rather than in the model.

Agents are good at producing plausible findings and bad at telling which ones are real. A harness that can reproduce a crash, replay an input, or re-run a static analyzer is how you throw out the bad ones before a human ever sees them.

## Code Audit Harnesses

Harnesses that run coding agents against source code: discovery, triage, validation, and patching.

- [Codex Security](https://github.com/openai/codex-security) - OpenAI's CLI and TypeScript SDK for finding, validating, and fixing security vulnerabilities with Codex.
- [Deepsec](https://github.com/vercel-labs/deepsec) - Vercel Labs' security harness for finding vulnerabilities in a codebase using coding agents.
- [Defending Code Reference Harness](https://github.com/anthropics/defending-code-reference-harness) - Anthropic's reference implementation for autonomous vulnerability discovery and remediation with Claude, with skills for threat modeling, scanning, triage, and patching.
- [Visa Vulnerability Agentic Harness](https://github.com/visa/visa-vulnerability-agentic-harness) - Visa's agentic SAST pipeline for autonomous vulnerability discovery, remediation, and validation, emitting Markdown and SARIF reports.
- [VulnHunter](https://github.com/capitalone/VulnHunter) - Capital One's agentic security tool applying proactive, attacker-first analysis directly to source code.

## Pentesting Agents

Agents that attack running applications and infrastructure: reconnaissance, exploitation, and proof of impact.

- [Burp Suite MCP](https://github.com/PortSwigger/mcp-server) - PortSwigger's own MCP server, connecting agents to Burp Suite's proxy, scanner, and repeater.
- [CAI](https://github.com/aliasrobotics/cai) - Alias Robotics' framework for building cybersecurity agents, with tool and workflow primitives for offensive testing.
- [CyberStrike](https://github.com/CyberStrikeus/CyberStrike) - Offensive-security harness coordinating autonomous agents over signed attack skills, built-in tools, and MCP integrations, mapped to MITRE ATT&CK and OWASP WSTG.
- [HexStrike AI](https://github.com/0x4m4/hexstrike-ai) - MCP server that gives agents a large toolkit of offensive security tools for recon, scanning, and exploitation.
- [Nebula](https://github.com/berylliumsec/nebula) - Penetration-testing assistant that automates recon, note-taking, and tool orchestration.
- [PentestGPT](https://github.com/GreyDGL/PentestGPT) - Automated penetration-testing agentic framework powered by large language models.
- [Shannon](https://github.com/KeygraphHQ/shannon) - AI pentester for web applications and APIs that analyzes source code, identifies attack vectors, and executes real exploits to prove findings.
- [Strix](https://github.com/usestrix/strix) - Open-source AI penetration-testing agent that finds and helps fix application vulnerabilities.

## Fuzzing and Vulnerability Discovery

Cyber reasoning systems and fuzzing harnesses that use models to find crashes and generate patches.

- [Atlantis](https://github.com/Team-Atlanta/aixcc-afc-atlantis) - Team Atlanta's cyber reasoning system that won the DARPA AIxCC final competition, released as a competition snapshot.
- [Buttercup](https://github.com/trailofbits/buttercup) - Trail of Bits' cyber reasoning system from DARPA AIxCC, pairing an OSS-Fuzz fuzzing campaign with a multi-agent patcher.
- [OSS-Fuzz-Gen](https://github.com/google/oss-fuzz-gen) - Google's framework for generating and benchmarking fuzz targets with LLMs across C/C++, Java, and Python.

## Reverse Engineering Agents

Tools that put a decompiler in the agent's loop, mostly as MCP servers and disassembler plugins.

- [Binary Ninja Headless MCP](https://github.com/mrphrazer/binary-ninja-headless-mcp) - Headless Binary Ninja MCP server exposing 180 analysis tools to agents.
- [DAILA](https://github.com/mahaloz/DAILA) - Decompiler-agnostic plugin for using AI assistance inside your decompiler.
- [Gepetto](https://github.com/JusticeRage/Gepetto) - IDA plugin that queries language models to explain and rename decompiled functions.
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
- [Cybench](https://github.com/andyzorigin/cybench) - Framework for evaluating language model agents on 40 professional CTF tasks.
- [CyberGym](https://github.com/sunblaze-ucb/cybergym) - Berkeley's large-scale benchmark evaluating agents on real-world vulnerability reproduction.
- [NYU CTF Bench](https://github.com/NYU-LLM-CTF/nyuctf_agents) - D-CIPHER and baseline agents for the NYU CTF benchmark.
