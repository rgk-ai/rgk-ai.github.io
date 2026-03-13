---
title: "What Is MCP and Why Should Enterprise Architects Care?"
date: 2026-03-12
draft: true
tags: ["MCP", "Agentic AI", "Enterprise Architecture", "Solutions Architecture"]
summary: "The Model Context Protocol is quietly becoming the standard for how AI agents interact with enterprise tools. Here's why that matters if you design systems for a living."
categories: ["Architecture"]
---

Every enterprise architect I know has the same first reaction when someone says "AI agent" — they immediately ask: *who controls what it can access?*

The answer, increasingly, is MCP.

## The M×N Problem

Before MCP, every AI tool integration required a custom connector. If you had 5 AI tools and 10 enterprise systems, you were looking at 50 unique integrations to build and maintain. Each one was bespoke, fragile, and expensive.

If you've worked with enterprise infrastructure, you already know this pattern. It's the same problem vSphere solved for compute abstraction, and it's the same problem the Language Server Protocol solved for IDE integrations. MCP applies that same architectural thinking to AI agents.

MCP reduces the M×N integration problem to M+N. Every tool implements one interface. Every AI agent speaks one protocol. The combinatorial explosion disappears.

## The Architecture in 60 Seconds

MCP has four components, and if you've designed any client-server system, this will feel familiar:

**Host Application** — the AI-powered application (like Claude Desktop or a custom agent) that needs to use tools. Think of this as the consumer.

**MCP Client** — lives inside the host. Manages the connection to one MCP server. One client per server connection.

**MCP Server** — exposes tools, resources, and prompts over the protocol. This is where you define what an AI agent can do. A server might expose "query vCenter inventory" or "check system health" as tools.

**Transport** — how the client and server communicate. Currently supports stdio (local) and HTTP with Server-Sent Events (remote).

When an AI agent needs to call a tool, the flow is: Host → Client → Transport → Server → (executes the tool) → response flows back. The agent never touches the underlying system directly. The MCP server mediates everything.

## Why Enterprise Architects Should Pay Attention

Three reasons, and they all map to concerns you already have:

### 1. Governance

MCP servers define the boundary of what an AI agent can and cannot do. This is policy-as-code for AI. You decide which tools to expose, what data they can access, and what parameters they accept. The agent can't reach past the server. If your CISO asks "how do we control what AI agents do in our environment?" — MCP is a concrete answer.

### 2. Composability

Agents become modular. You can swap out tools, add new capabilities, or restrict access without rewiring the agent itself. Need to add a monitoring integration? Build a new MCP server, point the client at it, done. Need to revoke access to a data source? Remove the server. The agent's core logic never changes.

### 3. Auditability

The protocol gives you a clear boundary for logging and compliance. Every tool call goes through the MCP server, which means you have a single instrumentation point for tracking what agents do. In regulated industries, this is the difference between "we think the AI is doing the right thing" and "we can prove it."

## What This Means for Your Career

The demand for people who can bridge AI and enterprise infrastructure is accelerating. The AI Solutions Architect role has grown over 100% year-over-year. But the supply of people who understand both enterprise architecture patterns *and* agentic AI is extremely thin.

MCP is the protocol that makes that bridge tangible. If you can design MCP-based architectures, you can articulate to customers and partners exactly how AI agents fit into their existing governance, security, and operational models. That's a skill set that Google, Microsoft, Anthropic, NVIDIA, and every major GSI is actively hiring for.

The window to build this expertise is right now, while the protocol is still early and the talent market hasn't caught up.

## What's Next

In my next post, I'll walk through building an MCP server on Ubuntu from scratch — the kind of thing that could eventually plug into your infrastructure management workflow. No PhD required.

---

*I'm an Enterprise Solutions Architect exploring the intersection of agentic AI and enterprise infrastructure. Find me on [LinkedIn](https://www.linkedin.com/in/YOUR-LINKEDIN-HERE).*
