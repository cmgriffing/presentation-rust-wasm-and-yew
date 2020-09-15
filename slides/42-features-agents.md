# Features: Agents

## Agents

Similar to Angular Services

Uses web-workers for concurrency

Useful for:

- pass messages to any other component
- share state
- offload heavy computation to worker thread

<div class="notes">
Plans for cross-tab communication
</div>

## Agents: Lifecycle

<img class="no-border" src="./assets/agentsv4.png" />

## Agents: Types

- Context (UI Thread Singleton)
- Job (UI Thread)
- Public (New Thread Singleton)
- Private (New Thread)

<div class="notes">
Singleton = creates new if none. Otherwise uses existing

Non Singleton = New Agent per connection/bridge

</div>

## Agents: Bridges and Dispatchers

- Bridge: bi-directional communication

  - (component <-> agent and agent <-> agent)

- Dispatcher: unidirectional
  - sends from component to Agent

<div class="notes">
Seperate threaded agents have serialization overhead
</div>
