# ADR-002: UI Modularization Strategy for Vite-based Frontend

## Status
Accepted

## Date
2026-02-12


## Context
The current UI is implemented as a single static HTML block.
This approach does not align with the modular architecture introduced by Vite.

Problems:

- No separation of concerns
- No reusable UI components
- Difficult maintenance and scaling
- Tight coupling between markup and logic


Additionally, `index.html` now serves as a Vite template entry rather than a standalone HTML file.


## Decision

The UI will be decomposed into modular JavaScript components located in the `src/modules/` directory.

Proposed structure:

src/
  modules/
    layout/
    header/
    bottomSheet/
    map/
  state/
  main.js



Each module:

is responsible for its own DOM

exports the render() function

does not contain global variables

is connected via ES modules

main.js becomes the orchestrator:

initializes the state

mounts the layout

connects modules

## Consequences

Pros:

Clear separation of concerns

Reusable UI modules

Easier testing

Scalable architecture

Alignment with modern frontend practices

Cons:

Initial refactoring effort

Slightly higher entry complexity

## Next Steps

The following steps will be executed after this ADR is accepted:

Remove demo Vite template code

Create module directory structure

Extract existing HTML into layout module

Implement module mounting via main.js

Introduce basic state container