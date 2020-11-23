# Project Organization

## How to choose the best project layout?
**Sequence**
*When to use it?*
- When there’s clear succession of steps, without too many conditions (for example, a UI automation);
- Usually, Sequences are used to nest workflows and the high-level logic is handled through Flowcharts or State Machines.

*What are the advantages?*
- Easy to understand and follow, having a top to bottom approach;
- Great for simple logic, like searching for an item on the internet.

*What are the disadvantages?*
- Nesting too many conditions in the same Sequence makes the process hard to read;
- Not suitable for continuous flows.

**Flowchart**
*When to use it?*
- When you have a complex flow with several conditions, a Flowchart is at least visually much easier to understand and follow;
- When you need a flow that runs continuously or that terminates only in several conditions.

*What are the advantages?*
- Easy to understand, as it is similar to logic diagrams in software computing;
- Can be used for continuous workflows.

*What are the disadvantages?*
- Flowcharts can be used only as the general workflow (with sequences nested inside), not for individual parts of projects (nested inside other workflows).

**State Machine**
*When to use it?*
First of all, let’s understand what a State Machine is. It is an abstract machine consisting of a finite number of pre-defined states and transitions between these states. At any point, based on the external inputs and conditions verified, it can be in only one of the states.

State Machines can be used with a finite number of clear and stable states to go through. Some examples from your daily life include vending machines, elevators or traffic lights.

*What are the advantages?*
- Can be used for continuous workflows that are more complex;
- Transitions between states can be easily defined and offer flexibility;
- Can accommodate processes that are more complex and cannot be captured by simple loops and If statements;
- It is easier to cover all the possible cases/transitions with state machines.

*What are the disadvantages?*
- Longer development time due to their complexity: splitting the process into logical "states", figuring out transitions, and so on.