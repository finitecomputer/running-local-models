# Running Local Models: From Desktop to Data Center

Expanded talk architecture

## Purpose

Communication job
-----------------
By the end, builders at every level should understand the path from a first
local model to a private, shared inference service, because the infrastructure
choices determine who can rely on an agent and who controls the system behind it.

Core promise
------------
You can run a local model in ten seconds. That is the easy part. The useful
part is learning what comes next: how to keep it private, turn it into an
agent, choose the right model for each job, serve many requests, and grow onto
hardware you control.

The talk should leave people with a map, not a shopping list. They should know
which layer they are looking at, what problem each layer solves, and what to
build next.

The quiet thesis
----------------
Freedom in AI is not only about downloading model weights. It is also about
being able to run the system, understand the boundary around it, and keep the
service dependable when the work becomes real.

Mission frame
-------------
The talk can open and close with the reason this work matters. The motivation
is the freedom-tech work around the Human Rights Foundation's AI for Individual
Rights program, Agent Camp, and Finite Computer. The practical question is how
to help activists and other people working in the freedom-tech space use small,
scalable, private systems that can run agents on hardware they can control.

Keep this human and brief. It is context for the engineering, not a manifesto.
The speaker does not need to claim that infrastructure solves every problem.
The point is that control, privacy, and resilience are engineering properties,
not just values written in a mission statement.


## The narrative spine

Act 1: The first ten seconds
----------------------------
Question: Can I run a model here, right now?

Answer: Yes. Start with one command on a laptop. Make the first step feel
close, concrete, and unromantic.

Act 2: The first model raises better questions
-----------------------------------------------
Question: What does local actually buy me, and what does it not buy me?

Answer: Local inference can keep prompts on the machine, but privacy and
security still depend on the surrounding system. Then the audience sees why
the model is only one part of the stack.

Act 3: A model becomes a system
-------------------------------
Question: How does a model do useful work, and how do I use more than one?

Answer: Add tools, files, memory, and a loop. Then specialize across models.
An agent needs a stable interface so the model can move without the app being
rewritten.

Act 4: One machine becomes infrastructure
------------------------------------------
Question: What changes when requests arrive together?

Answer: Memory, latency, throughput, batching, scheduling, and hardware begin
to matter. This is where inference engineering starts.

Act 5: The endpoint becomes a capability
----------------------------------------
Question: What does it look like when the system is something other people can
actually use?

Answer: A private, OpenAI-compatible endpoint on hardware you control, serving
many agents. Close on the live endpoint, then return to the mission that made
the infrastructure worth building.


## Expanded slide menu

This is a menu of material, not a demand to use every slide. The starred slides
are the core path. The rest can be selected for a 30, 45, or 60 minute version.

01. I did not start with infrastructure
----------------------------------------
Job: Give the technical journey a human reason.

Visible idea:
  I got into this because people need tools they can trust and control.

Speaker move: Briefly connect Agent Camp, the AI for Individual Rights work,
and Finite Computer to the problem of making useful local systems available to
people working in the freedom-tech space.

Visual: Paper Signal begins as one thin orange line on an otherwise quiet page.

02*. Running a model is the easy part
--------------------------------------
Job: Set the promise and lower the barrier to entry.

Visible copy:
  You can run your first local model in about ten seconds.
  That is the easy part.

Demo option: Run one command, or show a prepared terminal capture if the room's
network is not trustworthy.

03*. Local is a boundary, not a security policy
------------------------------------------------
Job: Add nuance before the audience overgeneralizes.

Questions to put on the page:
  Where does the prompt go?
  Who can read the logs?
  What can the model call?
  What leaves the machine when I hit enter?

Point: Local inference changes the default data path. It does not remove the
need for access control, secret handling, network boundaries, or observability.

04. The local stack in one picture
----------------------------------
Job: Give people the vocabulary for the rest of the talk.

Layer the picture from bottom to top:
  Model weights
  Runtime
  Serving process
  API
  Agent loop
  Scheduler and network

Transition: Every later problem belongs to one of these layers. If a system
feels confusing, find the layer where the decision actually lives.

05*. A model that only talks is a demo
---------------------------------------
Job: Move from chat to work.

Visible copy:
  Give it tools, files, and a loop.
  Now it can do work on your hardware.

Visual: Model, tools, loop. Keep the three terms large and spare.

Speaker detail: The loop reads context, calls a tool, checks the result, and
decides what to do next. The model is not the whole agent.

06. The agent loop is where reliability begins
------------------------------------------------
Job: Make the hidden work visible.

Show one short loop:
  Observe -> decide -> call -> inspect -> continue

Questions to raise:
  What happens when a tool fails?
  Where is state kept?
  What can the agent access?
  How do you stop it?

Avoid turning this into an agent framework comparison. The point is the shape
of the problem.

07*. One model becomes many
----------------------------
Job: Introduce specialization without making it a catalog.

Visible copy:
  A big model for hard problems.
  A small model for routing.
  A code model for the editor.
  An embedding model for search.

Point: Model choice is a systems decision. The best model is the one that fits
the job, the latency budget, the memory budget, and the risk of failure.

08. Choose by job, not by leaderboard
--------------------------------------
Job: Make model selection practical and evergreen.

Use four questions:
  How hard is the task?
  How fast must the answer arrive?
  How much context must fit?
  What happens if it is wrong?

Optional example: A routing model, a code model, and a heavyweight model can
share one application without the application knowing their internals.

Do not pin the talk to a specific model ranking or GPU SKU. Those details date
quickly and distract from the decision framework.

09*. One API keeps the application portable
--------------------------------------------
Job: Explain why compatible serving matters.

Visible copy:
  Laptop. Workstation. Cluster.
  Same endpoint shape.

Show:
  POST /v1/chat/completions

Point: The application should not need to know where the model lives. Moving
from a laptop to a cluster should be a configuration change before it becomes a
rewrite.

10. The interface is simple. The service is not.
------------------------------------------------
Job: Separate API compatibility from operational simplicity.

Visible idea:
  One protocol does not mean one problem.

Name the concerns without diving too deep:
  Authentication
  Rate limits
  Model routing
  Logs and metrics
  Timeouts and retries
  Failure behavior

This is a useful place to say that an OpenAI-compatible endpoint is a common
language, not a complete production architecture.

11*. The laptop eventually hits a wall
---------------------------------------
Job: Create the need for inference engineering.

Visible copy:
  Models get bigger.
  Contexts get longer.
  Agents get more numerous.

Point: Quantization and careful runtimes buy room. They do not repeal memory,
bandwidth, or queueing.

12. Hardware tiers without the shopping list
---------------------------------------------
Job: Make hardware practical without becoming dated.

Use three broad classes:
  Laptop: first model, private experiments, one or a few agents.
  Workstation: larger models, more memory, sustained local service.
  Small cluster: shared capacity, multiple models, many concurrent agents.

For every tier, ask:
  What fits?
  How quickly does it respond?
  How many requests can it serve?
  What happens when it is busy?

13. Memory is the first constraint
-----------------------------------
Job: Give the audience a durable mental model for hardware.

Explain in plain language:
  The weights have to fit.
  The context takes room.
  The runtime needs working memory.
  Concurrent requests multiply the pressure.

Avoid a formula-heavy detour unless the audience clearly wants it. A single
memory diagram is more useful than a table of hardware specifications.

14. Latency and throughput are different promises
--------------------------------------------------
Job: Prevent a common category error.

Visible copy:
  Fast for one person is not the same as fast for sixteen.

Contrast:
  Latency: how long one request waits.
  Throughput: how much work the service completes over time.

Point: The system may be excellent for an interactive chat and poor for a
swarm of agents. The workload defines the architecture.

15*. One request versus sixteen
-------------------------------
Job: Make concurrency memorable.

Visual sequence:
  1 -> 4 -> 8 -> 16

Speaker line:
  One agent is easy. Sixteen agents change the system.

Live demo option: Show duplicated agent terminals or a clean concurrency
visualization. Display the queueing and token speed as evidence, not as the
main character.

Do not turn this into a benchmark flex. The audience should remember why
batching and runtimes exist.

16*. Why runtimes exist
-----------------------
Job: Answer the question created by the concurrency demo.

Visible copy:
  The runtime is the part that knows the requests arrived together.

Explain at a high level:
  It keeps model weights loaded.
  It manages memory.
  It batches work.
  It schedules requests.
  It exposes a service other programs can call.

Optional advanced terms: KV cache, continuous batching, quantization, tensor
parallelism. Say the terms only if the room benefits from naming them.

17. One model loaded once, many agents sharing it
--------------------------------------------------
Job: Make the payoff of batching and serving concrete.

Visual: One model block feeding several agent loops. Keep the lines simple.

Point: The system gets more efficient when the expensive parts are shared.
That is the bridge from one process to a service.

18*. Pool the hardware you already control
-------------------------------------------
Job: Reframe the cluster as an incremental step, not a datacenter fantasy.

Visible copy:
  Spare workstations count.
  Used servers count too.

Point: A cluster can begin with machines that already exist. The core change is
coordination: shared capacity, a scheduler, and a stable endpoint.

19. What the small cluster actually adds
-----------------------------------------
Job: Name the new responsibilities.

The cluster adds:
  Placement: where a request runs.
  Capacity: how much work can run at once.
  Failure: what happens when a node disappears.
  Policy: who can use which model.
  Observability: how you know the system is healthy.

This is a good advanced branch or a short spoken expansion.

20. The cluster is a control surface
-------------------------------------
Job: Keep ownership and infrastructure connected.

Visible idea:
  The point is not to imitate a cloud.
  The point is to make your own capacity usable.

Visual: Replace the single orange line with a shared rail that passes through
several machines, then returns to one endpoint.

21. Security grows with the service
-----------------------------------
Job: Keep the freedom-tech frame technically honest.

Questions:
  Who can reach the endpoint?
  What credentials are in the agent environment?
  What gets logged?
  Can one agent see another agent's context?
  What can be disconnected quickly?

Point: Moving from local to shared infrastructure increases capability and
attack surface at the same time. Control means understanding both.

22*. One endpoint for the people and agents around it
------------------------------------------------------
Job: Make the system feel real.

Visible copy:
  One endpoint. A swarm of agents.

Show a placeholder endpoint or the real endpoint only if it is safe to expose:
  https://models.yourdomain.internal/v1

The endpoint should be framed as the consequence of the journey, not a magic
trick. Explain what it serves, who can access it, and what boundary protects it.

23. The live service is the closer
-----------------------------------
Job: Resolve the opening promise in the room.

Demo sequence:
  1. Point an agent or client at the endpoint.
  2. Send one request.
  3. Add several requests.
  4. Show the service handling them together.
  5. Change the model or machine without changing the client interface.

Have a recorded fallback. The talk should not depend on venue Wi-Fi, a single
node, or an untested hardware path.

24*. Start with one command. Build the next layer when you need it.
-------------------------------------------------------------------
Job: Give the audience a clear next step and close the loop.

Possible close:
  Start with one model.
  Learn where the boundary is.
  Add the agent loop.
  Give each job the right model.
  Put one interface in front.
  Scale only when the workload asks you to.

Final mission line:
  The goal is not a cluster for its own sake. It is infrastructure people can
  actually rely on, on hardware they can understand and control.


## Audience branches

Beginner lane
-------------
Spend more time on:
  What local means
  The first command
  Model versus runtime versus agent
  Hardware tiers
  The one endpoint idea

Use fewer internal terms. Make the 1 to 16 concurrency moment the first time
the room feels why infrastructure exists.

Advanced lane
-------------
Spend more time on:
  Memory pressure and context length
  Quantization tradeoffs
  KV cache and continuous batching
  Routing and model placement
  Authentication and observability
  Failure modes in a small cluster

Keep advanced detail tied to a question from the story. Do not add a taxonomy
of runtimes simply because the names are available.

Freedom-tech lane
-----------------
Spend more time on:
  The difference between local, private, secure, and resilient
  Who controls the endpoint and its logs
  What a disconnected or degraded mode should do
  How small models change the hardware requirement
  Why open interfaces make it easier to change the underlying model

Avoid turning activists into an abstract persona. Use the speaker's real
experience through Agent Camp and Finite Computer, or keep the framing general.


## Three timing versions

30 minutes
----------
Use the starred slides: 01, 02, 03, 05, 07, 09, 11, 15, 16, 18, 22, 24.
Choose one demo: either the first model or the concurrency sequence. Keep the
cluster architecture to one clean picture.

45 minutes
----------
Use the core path plus 04, 08, 12, 14, 17, and 21. Include the first model as
a quick opening proof and the concurrency sequence as the main live demo.

60 minutes
----------
Use most of the expanded menu, but protect the narrative. Add one technical
deep dive, not three. The strongest deep dive is usually concurrency to
runtime to cluster because it answers why the hardware layers exist.


## Demo choreography

Demo 1: The ten-second start
----------------------------
Purpose: Make local inference feel accessible.
Show: One command, one prompt, one response.
Fallback: A short recording or a preloaded model with the command still visible.

Demo 2: One, four, eight, sixteen
---------------------------------
Purpose: Make batching and throughput intuitive.
Show: Several identical agent terminals or a purpose-built harness. Keep the
numbers secondary to the behavior: queueing, shared work, and the point where
the runtime matters.
Fallback: A prepared visual with the same sequence and recorded timings.

Demo 3: The live endpoint
-------------------------
Purpose: Make the whole stack real at the end.
Show: A client or agent using the OpenAI-compatible endpoint, then several
requests arriving together.
Safety: Use a disposable audience-facing endpoint with no sensitive data, a
clear access boundary, and a kill switch. Do not expose internal infrastructure
or credentials from the stage.


## Paper Signal design direction

The expanding machine sequence
------------------------------

Use the new six-stage visual sequence as the recurring visual logic of the
talk. It should appear early enough that the audience has the vocabulary before
the agent, concurrency, and cluster sections introduce more detail.

  1. One box: Ollama bundles enough of the stack to make the first model easy.
  2. Pull it apart: model source, model weights, and runtime become separate.
  3. Local stack: hardware, OS and drivers, runtime, and loaded model are visible.
  4. Agent contract: the client-side agent uses a stable serving API and owns its tools.
  5. Shared service: a gateway adds queueing, routing, and policy for many agents;
     runtimes batch and schedule the work.
  6. Complete machine: one endpoint resolves into agent, gateway, API, runtime,
     model, OS and drivers, and hardware.

The corrected relationship is important. The model is loaded and executed by the
runtime. The agent owns its tools, memory, and loop. Tool calls cross the agent
boundary through the serving contract. A gateway sits in front of shared
inference services when traffic needs routing, queueing, policy, or
observability. The runtime is where batching, memory management, and execution
belong.

Suggested use in the full deck:

  Start with stages 1 and 2 immediately after the ten-second model demo.
  Use stage 3 before explaining hardware tiers and memory.
  Use stage 4 to introduce the agent loop and the OpenAI-compatible API.
  Use stage 5 to set up the one, four, eight, sixteen concurrency demo.
  Use stage 6 as the visual before the live endpoint closer.

The orange signal should be the narrative device, not decoration.

Early slides: one small orange mark or rule.

Agent slides: three orange rules for model, tools, and loop.

Concurrency: the signal gets repeated across 1, 4, 8, and 16.

Cluster: the single line becomes a shared rail across several machines.

Final endpoint: the signal resolves into one visible route from the audience to
the service.

Keep the deck editorial and flat. Avoid card grids, product-dashboard layouts,
vendor logos, and excessive hardware photography. The strongest visual contrast
is between a quiet paper field and one precise signal color.


## Questions to resolve before the full draft

1. What is the actual conference duration and how much live-demo risk is acceptable?
2. Which parts of the cluster stack can be shown publicly?
3. Is the real endpoint safe to offer to the audience, or should the talk use a
   temporary isolated endpoint?
4. Which model and runtime names are stable enough to mention in the room?
5. Should the freedom-tech motivation include a specific story from Agent Camp,
   or stay at the mission level?
6. What should a beginner be able to do the same evening after the talk?
7. What is the one advanced concept worth giving extra time to?
