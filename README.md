# BlazorApp-PWA-Demo

A Progressive Web App (PWA) demo built with [Blazor](https://dotnet.microsoft.com/apps/aspnet/web-apps/blazor) using .NET 10.

## Features

- **Home** – Welcome page for the application.
- **Counter** – Interactive counter component demonstrating Blazor's event handling and state management.
- **Weather** – Weather forecast page demonstrating asynchronous data loading and table rendering.

## Getting Started

### Prerequisites

- [.NET 10 SDK](https://dotnet.microsoft.com/download)

### Run the application

```bash
dotnet run --project BlazorApp-PWA-Demo
```

Then open your browser and navigate to `https://localhost:5001`.

## Project Structure

- `BlazorApp-PWA-Demo/` – Server-side Blazor host application.
- `BlazorApp-PWA-Demo.Client/` – Client-side WebAssembly Blazor project containing pages and layout components.