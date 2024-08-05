---
tags:
  - dotNet
  - blazor
  - frontend
---

# Blazor 

## Render modes (since .NET 8)

- Static server-side: The component is rendered on the server and returned as HTML. This mode is fast and simple, but does not support interactivity.
- Interactive server: The component is rendered on the server and updated via a SignalR connection. This mode supports interactivity, but has some latency and scalability issues.
- Interactive WASM: The component is rendered on the browser using WebAssembly. This mode supports interactivity and offline scenarios, but has a larger payload size and slower startup time.
- Interactive auto: The component is rendered on the server first, then switched to WebAssembly on the browser. This mode combines the benefits of both modes, but requires some extra configuration and testing.