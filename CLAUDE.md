# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Structure

This is a monorepo with two sub-projects:

- `api/` — ASP.NET Core Web API (.NET 10, minimal APIs)
- `mobile/` — React Native mobile app (Expo SDK 54, Expo Router, TypeScript)

## API (`api/`)

**Stack:** .NET 10, ASP.NET Core minimal APIs, OpenAPI via `Microsoft.AspNetCore.OpenApi`

**Run:**
```
cd api
dotnet run
```

**Build:**
```
dotnet build
```

The API currently exposes a single route (`GET /weatherforecast`) defined inline in `Program.cs`. OpenAPI docs are served in Development at the `/openapi` endpoint. All new routes should be added to `Program.cs` using the minimal API pattern (`app.MapGet/Post/...`).

## Mobile (`mobile/`)

**Stack:** Expo SDK 54, React Native 0.81, Expo Router (file-based routing), React 19, TypeScript strict mode, React Compiler enabled

**Start dev server:**
```
cd mobile
npx expo start
```

Target a specific platform:
```
npx expo start --android
npx expo start --ios
npx expo start --web
```

**Lint:**
```
npx expo lint
```

**Path alias:** `@/` maps to the `mobile/` root (configured in `tsconfig.json`).

**Routing:** Expo Router uses file-system routing under `mobile/app/`. The root layout is `app/_layout.tsx`. Add new screens by creating files under `app/`.

**New Architecture:** `newArchEnabled: true` in `app.json` — the app uses React Native's new architecture (Fabric/JSI).
