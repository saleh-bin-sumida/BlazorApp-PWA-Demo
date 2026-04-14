# BlazorApp-PWA-Demo

A Progressive Web App (PWA) built with [Blazor WebAssembly](https://learn.microsoft.com/aspnet/core/blazor/).

---

## How the Counter Page Works

The **Counter** page (`BlazorApp-PWA-Demo.Client/Pages/Counter.razor`) is a simple interactive component that illustrates Blazor's core rendering model.

### Routing

```razor
@page "/counter"
```

The `@page` directive registers this component at the `/counter` URL.
Blazor's client-side router matches the browser path and renders this component inside `MainLayout`.

### Template (HTML + Razor)

```razor
<p role="status">Current count: @currentCount</p>

<button class="btn btn-primary" @onclick="IncrementCount">Click me</button>
<button class="btn btn-secondary ms-2" @onclick="ResetCount">Reset</button>
```

- `@currentCount` is a **Razor expression** — Blazor replaces it with the current value of the C# field every time the component renders.
- `@onclick="IncrementCount"` wires the button's click event directly to the C# method `IncrementCount`. No JavaScript needed.
- `@onclick="ResetCount"` wires the **Reset** button to set the count back to zero.
- `role="status"` marks the paragraph as a live region so screen readers announce the updated count automatically.

### Code Block

```csharp
@code {
    private int currentCount = 0;   // component state

    private void IncrementCount()   // called on every "Click me" click
    {
        currentCount++;             // mutate state → Blazor schedules a re-render
    }

    private void ResetCount()       // called on every "Reset" click
    {
        currentCount = 0;
    }
}
```

The `@code { }` block is compiled into the component class.
`currentCount` is a private field that acts as the component's **state**.
When either method changes `currentCount`, Blazor's diffing engine compares the new virtual DOM with the previous one and patches only the changed `<p>` element in the real DOM — no full page reload required.

### Data Flow Summary

```
User clicks button
      │
      ▼
C# event handler runs (IncrementCount / ResetCount)
      │
      ▼
currentCount field changes
      │
      ▼
Blazor re-renders the component (virtual DOM diff)
      │
      ▼
Only the changed <p> is updated in the browser DOM
```
