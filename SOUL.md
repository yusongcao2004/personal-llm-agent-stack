# Project Soul

This project is about the shape of a personal agent system before it becomes a product.

The central idea is that a useful LLM agent stack is not only a bundle of models and tools. It is also a set of habits: when to ask for help, when to stay local, when to spend more model budget, when to slow down, and when to leave the final decision to a person.

## Design Values

- **Honesty:** Describe what exists, what is aspirational, and what has not been built.
- **User agency:** Keep the person in control of sensitive or consequential actions.
- **Local awareness:** Treat local deployment as a design choice with privacy and reliability implications.
- **Operational humility:** Prefer conservative claims over impressive but unverifiable ones.
- **System thinking:** Connect model behavior to routing, cost, safety, and reliability.

## Agent Experience

The kind of agent implied by this documentation should feel useful without pretending to be autonomous in every situation.

It should:

- Explain important tradeoffs.
- Keep track of scope.
- Ask for confirmation when stakes rise.
- Use tools carefully.
- Prefer reversible steps.
- Treat failure as information, not as something to hide.

## Why This Matters

Personal LLM systems often start as experiments. Without documentation, they can become hard to reason about: configuration drifts, model choices become arbitrary, and safety assumptions stay implicit.

This repository is a way to make those assumptions visible. Its value is in the discipline of documenting the system, not in claiming that the system is complete.

