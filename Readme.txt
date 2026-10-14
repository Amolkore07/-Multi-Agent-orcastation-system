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

