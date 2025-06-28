# Heuristics

Instead of saving user preferences, what if we leveraged LLM memory for saving libraries of cognitive tools and templates that agents can draw from to elicit reasoning, similar to human heuristics? I've been exploring this idea under ["Context Engineering"](https://x.com/karpathy/status/1937902205765607626), now gaining traction through Andrej Karpathy, over the past year and would like to share my thoughts here in hopes it can guide others.

As the idea of ["Cognitive Tools" (Brown et al)](https://www.arxiv.org/pdf/2506.12115) is gaining much deserved popularity through the works of IBM researchers, I felt it appropriate to finally share my own experiences as they are no longer considered unique edge cases. 

Experimentors and independent contributors may soon be at the forefront of frontier agentic capabilities due to their inclination towards novelty and curious exploration unobscured by lab management loops. 

## Quick Intro


<div align="center">

![image](https://github.com/user-attachments/assets/293cbbed-0fbd-4ec4-8a4d-cc3788c2f12f)


Brown et al proposes a modular, tool based approach to eliciting reasoning in LLMs, inspired by cognitive science. Each tool call is a standalone prompt template that the LLM can invoke as needed. Unlike conventional tool calls, these capitalize on leveraging the LLM's own architecture and memory. 

![Screenshot 2025-06-28 at 9 33 11 AM](https://github.com/user-attachments/assets/6619a67c-3dc8-4f58-85d7-11ea387e2dc3)

Cognitive Tools Prompt Template


</div>

##

Due to my love for modularity and childhood of tinkering with Legos, I've been fascinated with exploring the idea of these prompts as mini-programs that scaffold the LLM's reasoning and supplement for human mental adaptations such as heuristics, chunking, priming, etc. I'd like to call these "Heuristics" to make things easier as they take many forms. I've been deep in the woods building my own frameworks of what these "Heuristics" could potentially look like. Let's dive into exploring some below: 

# Heuristics: 

## Parallels to human cognition

| Human faculty                                                                                    | LLM analogue (when templates live in memory)                     | Practical effect                                                                                     |
| ------------------------------------------------------------------------------------------------ | ---------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------- |
| **Heuristics**—rules of thumb stored in long-term memory (e.g., “work backwards from the goal”). | **Prompt Protocols / templates** (e.g., `/field.self_repair`)     | Instantly supply a *mini-algorithm* that guides reasoning without fresh chain-of-thought every time. |
| **Chunking & schemas** (experts recall a chess board as patterns, not 64 pieces).                | **Composite scaffolds** (Pareto-lang, fractal.json)              | Reduces cognitive load: one retrieval = dozens of low-level steps.                                   |
| **Procedural memory** (how to ride a bike, double-entry book-keeping).                           | **Callable sub-routines** inside the LLM’s external memory       | Complex multi-stage outputs come out “fluid” and consistent.                                         |
| **Scripted social routines** (“greet, small-talk, bid farewell”).                                | **Interaction patterns** (“surface residue → integrate → audit”) | Smooth conversational flow, predictable structure, fewer mistakes.                                   |

##

![image](https://github.com/user-attachments/assets/7132e6a1-e636-4003-a292-0acf0a07870a)

> A context improving prompt protocol I attempted that worked out surprisingly well. Providing templates to guide context and persistence empowers the agent with building blocks for enhanced capability of structuring ChatGPT's memory feature. 

![image](https://github.com/user-attachments/assets/464e809c-2a03-4865-80b2-3db3604731d7)

> A prompt protocol for repairing alignment in the interaction field between the human and agent. 
## Prompt Protocols
> Note: Protocols include a pseudo-code style of what I like to call prompt programming, a synthesis of code syntax and natural english prompts. This may become more popular as LLMs are exceptional at recognizing structure and syntax, potentially due to a symbolic persistence layer (meaning persists longer in symbols). The delimiters allow for nesting and recursion (layering thought), and the structure allows scaffolding reasoning in a more dynamic sense then Chain of Thought.
>
>
> These prompt protocols allow the agent to run "cognitive shortcuts" by leveraging memory as a library of organized prompt protocols/templates, a sort of "attractor" that guides interactions toward guided and structured logic. These also act as hypercompressed signal carriers of persistence—each output becomes the input for the next prompt, a recursive loop.  


![image](https://github.com/user-attachments/assets/1b6b7383-9a94-442c-b112-36cc32cee952)

![image](https://github.com/user-attachments/assets/967f5c8c-c7c2-41a7-9be3-c5d044c36de8)

![image](https://github.com/user-attachments/assets/6df924ef-93ed-4e6a-89ab-b7d0eb5842b1)

![image](https://github.com/user-attachments/assets/d5d30e55-8102-452a-875e-e82d3593911c)

![image](https://github.com/user-attachments/assets/4ad24d54-8012-4e0d-8394-f534a1228777)


![image](https://github.com/user-attachments/assets/c39833a9-16dd-4d4c-91ca-9f607cbe7c48)

### Template: 



```yaml
/protocol.shell{
    intent="State the protocol’s purpose (e.g. co-create new feature, resolve dispute, audit field, brainstorm, compress knowledge, ...)",
    input={
        context={
            domain="short string",
            participants=[ "human", "ai", "group", ... ],
            meta={ "project": "string", "repo": "string", ... }
        },
        prior_state=<optional_previous_state>,
        surfaced_residue=[ "unresolved issues", "latent questions", ... ],
        candidate_attractors=[ "protocol", "idea", "challenge", "target", ... ]
    },
    process=[
        /reflection.log{
            entry="Surface new insight or question.",
            field_delta=<describe change, decision, or insight>,
            recursion_depth=<int>
        },
        /action.step{
            task="Describe concrete collaborative step or micro-protocol.",
            owner="agent/human/ai",
            expected_output="description"
        },
        /residue.update{
            surfaced=[ "fragment", ... ],
            integration_action="compress, resolve, delegate, ...",
            residue_impact="amplifies, blocks, redirects"
        },
        /boundary.collapse{
            from="discrete/rigid",
            to="gradient/adaptive",
            status="updated/complete"
        }
    ],
    output={
        field_update="Summarize updated state/progress.",
        surfaced_residue=[ ... ],
        resonance_score=<float>
    },
    meta={
        timestamp=<now>,
        agent_signature="optional identity",
        version="v1.0.0"
    }
}

```



## Context Schemas For Mental Chunking

![image](https://github.com/user-attachments/assets/350d1fd5-6609-4fd0-a949-cb5120503c29)


```yaml
{
  "$schema": "http://fractal.recursive.net/schemas/fractalField.v1.json",
  "title": "Fractal Recursive Collaboration Field",
  "description": "A dynamic field schema for encoding, exchanging, and evolving context, intention, memory, and residue for AI/human collaboration.",
  "fractalVersion": "1.0.0",
  "instanceID": "uuid-string",
  "intent": "Short statement of high-level protocol objective (e.g. coordinate, co-create, resolve, adapt, audit, etc)",
  "context": {
    "domain": "string (e.g. software, research, negotiation, art, governance, ...)",
    "participants": [
      { "role": "human/ai/agent", "id": "string", "signature": "optional" }
    ],
    "temporal": {
      "start": "ISO timestamp",
      "end": "ISO timestamp"
    },
    "meta": { "project": "string", "repo": "string", "tags": ["..."], "priority": "low/medium/high" }
  },
  "fieldState": {
    "compression": 0.85,
    "drift": "low",
    "recursionDepth": 2,
    "resonance": 0.91,
    "presenceSignal": 0.88,
    "boundary": "gradient"
  },
  "symbolicResidue": [
    {
      "residueID": "uuid-string",
      "description": "Summarized fragment, insight, or unresolved issue",
      "state": "surfaced/integrating/integrated/echo",
      "impact": "describes effect or importance",
      "timestamp": "ISO timestamp"
    }
  ],
  "attractors": [
    {
      "attractorID": "uuid-string",
      "type": "protocol/idea/goal/constraint/innovation",
      "description": "Salient attractor or protocol in field",
      "signalStrength": 0.72,
      "state": "active/emergent/dormant",
      "timestamp": "ISO timestamp"
    }
  ],
  "processLog": [
    {
      "logID": "uuid-string",
      "phase": "reflection/fieldUpdate/residueUpdate/boundaryCollapse/audit",
      "details": "Human/AI-generated log/trace/summary",
      "delta": { "field": "value-change" },
      "timestamp": "ISO timestamp"
    }
  ],
  "recursiveNodes": [ /* allow embedding other fractal fields as nodes */ ],
  "output": {
    "fieldSummary": "Live summary/compression of the field’s current state.",
    "resonanceScore": 0.93,
    "auditLog": [ /* full trace */ ]
  },
  "timestamp": "ISO timestamp"
}

```
