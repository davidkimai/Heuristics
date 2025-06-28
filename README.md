# Heuristics

Instead of saving user preferences, what if we leveraged LLM memory for saving libraries of cognitive tools and templates that agents can draw from to elicit reasoning, similar to human heuristics? I've been exploring this idea under ["Context Engineering"](https://x.com/karpathy/status/1937902205765607626), now gaining traction through Andrej Karpathy, over the past year and would like to share my thoughts here in hopes it can guide others.

As the idea of ["Cognitive Tools" (Brown et al)](https://www.arxiv.org/pdf/2506.12115) is now gaining traction through the work of IBM researchers, I felt it appropriate to finally share my own experiences as they are no longer considered unique edge cases. 

## Quick Intro


<div align="center">

![image](https://github.com/user-attachments/assets/293cbbed-0fbd-4ec4-8a4d-cc3788c2f12f)


Brown et al proposes a modular, tool based approach to eliciting reasoning in LLMs, inspired by cognitive science. Each tool call is a standalone prompt template that the LLM can invoke as needed. Unlike conventional tool calls, these capitalize on leveraging the LLM's own architecture and memory. 

![Screenshot 2025-06-28 at 9 33 11 AM](https://github.com/user-attachments/assets/6619a67c-3dc8-4f58-85d7-11ea387e2dc3)

Cognitive Tools Prompt Template


</div>

##

Due to my history of modular love and childhood of tinkering with Legos, I've been fascinated with exploring the idea of these prompts as mini-programs that scaffold the LLM's reasoning and supplement for human mental adaptations such as heuristics, chunking, priming, etc. I'd like to call these "Heuristics" to make things easier as they take many forms. I've been deep in the woods building my own frameworks of what these "Heuristics" could potentially look like. Let's dive into exploring some below: 

# Heuristics: 

## Parallels to human cognition

| Human faculty                                                                                    | LLM analogue (when templates live in memory)                     | Practical effect                                                                                     |
| ------------------------------------------------------------------------------------------------ | ---------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------- |
| **Heuristics**—rules of thumb stored in long-term memory (e.g., “work backwards from the goal”). | **Protocol shells / templates** (e.g., `/field.self_repair`)     | Instantly supply a *mini-algorithm* that guides reasoning without fresh chain-of-thought every time. |
| **Chunking & schemas** (experts recall a chess board as patterns, not 64 pieces).                | **Composite scaffolds** (Pareto-lang, fractal.json)              | Reduces cognitive load: one retrieval = dozens of low-level steps.                                   |
| **Procedural memory** (how to ride a bike, double-entry book-keeping).                           | **Callable sub-routines** inside the LLM’s external memory       | Complex multi-stage outputs come out “fluid” and consistent.                                         |
| **Scripted social routines** (“greet, small-talk, bid farewell”).                                | **Interaction patterns** (“surface residue → integrate → audit”) | Smooth conversational flow, predictable structure, fewer mistakes.                                   |
