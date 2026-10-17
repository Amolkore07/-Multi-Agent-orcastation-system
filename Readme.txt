# AgentFlow: Enhancing AI Decision-Making Through Multi-Agent Orchestration

A web app that shows how a team of specialized AI agents can produce better, more reliable answers than a single LLM call. A user's query goes through four agents in sequence, and each agent's output feeds the next.

#how it works
┌──────────────┐
│  User query  │
└──────┬───────┘
       │
       ▼
┌──────────────────┐
│   Orchestrator   │
│ (Node + Express) │
└──────┬───────────┘
       │
       ▼
┌──────────────────┐
│  Planner Agent   │
│ Splits query into│
│ 3-5 subtasks     │
└──────┬───────────┘
       │ subtasks
       ▼
┌──────────────────┐
│ Researcher Agent │
│ Facts per subtask│
└──────┬───────────┘
       │ research
       ▼
┌──────────────────┐
│  Executor Agent  │
│ Drafts full      │
│ answer           │
└──────┬───────────┘
       │ draft
       ▼
┌──────────────────┐
│   Critic Agent   │
│ Reviews & refines│
└──────┬───────────┘
       │
       ▼
┌──────────────────┐
│   Final answer   │
│   (shown in UI)  │
└──────────────────┘


|Planner:- Breaks the query into 3-5 clear subtasks. Breaks the query into 3-5 clear subtasks.
|Researcher:- Provides concise, relevant facts for each subtask. Provides concise, relevant facts for each subtask.
|Executor:- Writes a complete answer using the research. Writes a complete answer using the research.
|Critic:- Reviews the answer and returns an improved final version. Reviews the answer and returns an improved final version.

The orchestrator (Express backend) manages the order, passes outputs between agents, and returns all four outputs to the UI.


# Features
- Four-agent sequential pipeline with live status per agent (Waiting / Running / Done)
- Compare Mode:** single-LLM answer vs multi-agent answer, side by side
- Agent Logs:** view the system prompt each agent used
- Timing:** response time per agent in ms
- One-click copy for the final (Critic) output
- Clean, minimal UI with no external UI libraries

# Tech stack

- Frontend: React (Vite), plain CSS
- Backend: Node.js, Express
- LLM:Groq API (open LLaMA models)
- State: in-memory, no database

# why multi-agent?

- Specialization: each agent has one focused job and prompt
- Cross-checking: the Critic catches gaps and errors before the user sees them
- Transparency: every step can be inspected
- Modularity:*swap or upgrade one agent without touching the rest

**Trade-offs:** more LLM calls mean higher latency and token cost, and an early bad output can propagate downstream.
## Future scope

- Parallel agents for independent subtasks
- Web search and tool use
- Critic feedback loop (send work back for revision)
- Memory and RAG
- Human-in-the-loop approval
- Automated evaluation (LLM-as-judge, rubric scoring)