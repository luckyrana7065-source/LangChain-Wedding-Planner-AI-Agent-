# LangChain-Wedding-Planner-AI-Agent-
An agentic AI wedding planning system built with LangChain and LangGraph, designed using a multi-agent architecture to coordinate different aspects of wedding planning.

Instead of relying on a single general-purpose LLM, the system uses a supervisor/coordinator agent that understands the user's requirements and delegates individual tasks to specialized agents. Each specialist focuses on a specific part of the wedding-planning workflow and contributes its results back to the overall plan.

🧠 How It Works

The user provides wedding requirements such as:

Wedding destination
Wedding date
Number of guests
Venue preferences
Travel requirements
Music preferences
Flower/decor requirements

The Wedding Planner Coordinator processes these requirements and delegates tasks to specialized agents.

                    User
                     │
                     ▼
          Wedding Planner Agent
               (Coordinator)
                     │
          ┌──────────┼──────────┐
          ▼          ▼          ▼
     Venue Agent  Travel Agent  Music Agent
          │          │          │
          ▼          ▼          ▼
       Venue      Flights     Playlist
       Search      Search     / Music DB
          │          │          │
          └──────────┼──────────┘
                     ▼
              Shared Wedding State
                     │
                     ▼
          Final Wedding Plan
🤖 Specialized Agents
🏛️ Venue Agent

Finds and evaluates suitable wedding venues based on the requirements provided by the user.

✈️ Travel Agent

Handles travel-related requirements and searches for relevant flight/travel information for the wedding destination.

🎵 Music Agent

Handles music and playlist-related requirements and retrieves suitable songs from the available music data.

💍 Coordinator Agent

Acts as the central orchestrator. It understands the overall request, maintains the wedding context, delegates tasks to specialist agents, and combines their outputs into a unified response.

🔑 Key Agentic AI Concepts

This project demonstrates several important concepts used in modern agentic AI systems:

Multi-Agent Architecture — Decomposing a complex problem into specialized agents.
Agent Delegation — A coordinator dynamically routes tasks to the appropriate specialist.
Shared State — Maintaining structured wedding information across different agents.
LangGraph Orchestration — Modeling the multi-step workflow and agent interactions as a graph.
Model Context Protocol (MCP) — Connecting agents to external tools and capabilities through standardized interfaces.
Tool Calling — Allowing agents to interact with external services instead of relying solely on LLM-generated knowledge.
Context Management — Passing relevant information between agents while maintaining the overall planning context.
🏗️ Architecture

The application follows a supervisor → specialist agents pattern:

                    ┌──────────────────┐
                    │      User        │
                    └────────┬─────────┘
                             │
                             ▼
                 ┌─────────────────────┐
                 │ Wedding Coordinator │
                 │       Agent         │
                 └──────────┬──────────┘
                            │
              ┌─────────────┼─────────────┐
              │             │             │
              ▼             ▼             ▼
        ┌──────────┐  ┌──────────┐  ┌──────────┐
        │  Venue   │  │  Travel  │  │  Music   │
        │  Agent   │  │  Agent   │  │  Agent   │
        └────┬─────┘  └────┬─────┘  └────┬─────┘
             │             │             │
             ▼             ▼             ▼
        Venue Tools   Travel Tools   Music DB
              \            │            /
               \           │           /
                └──────────┼───────────┘
                           ▼
                    Wedding State
                           │
                           ▼
                  Final Recommendations
🛠️ Tech Stack
Python
LangChain
LangGraph
LLM / Foundation Models
Model Context Protocol (MCP)
Tool Calling
Stateful Agent Workflows
External Search / Data Tools
SQLite / Structured Data (where applicable)
🎯 Why Multi-Agent?

Wedding planning is naturally a multi-domain problem. Venue selection, travel planning, music selection, and other tasks require different tools, data sources, and reasoning.

A single agent responsible for everything can become difficult to maintain and control.

The multi-agent approach allows each agent to have:

A focused responsibility
Its own tools
Specialized instructions
Independent reasoning
Access to only the context it needs

The coordinator then combines these specialized capabilities into a single user-facing experience.

🚀 What This Project Demonstrates

This project goes beyond a basic LLM chatbot and demonstrates how to design an agentic workflow for a complex real-world problem.

The primary learning outcomes include:

Designing a multi-agent system
Breaking complex tasks into specialized sub-problems
Building a coordinator/supervisor agent
Managing structured state across agents
Connecting agents to external tools through MCP
Using LangGraph to orchestrate agent workflows
Combining outputs from multiple agents into a coherent final response

The goal isn't simply to ask an LLM to plan a wedding. The goal is to build a system where multiple specialized AI agents collaborate to solve different parts of the planning problem.
