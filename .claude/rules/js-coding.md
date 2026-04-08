# JavaScript/TypeScript Coding Rules (ioRisk Project)

> These rules apply when working on the ioRisk project at `projects/ioRisk/`

## Forbidden Patterns

- NEVER nest template literals (backtick strings) more than one level — causes SyntaxError
- NEVER use `if(false){...}` to comment out code — template strings inside break bracket balance
- NEVER call `apiFetch(url, 'POST', body)` — apiFetch is GET-only, POST must use `apiPost(url, body)`

## Required Patterns

- Use string concatenation instead of nested template literals:
  ```javascript
  // CORRECT
  let html = '<div>';
  items.forEach(function(i){ html += '<span>' + esc(i) + '</span>'; });
  html += '</div>';
  ```
- Delete dead code instead of commenting it out

## Global State (React Frontend)

- Use Zustand store (`useGlobalStore`), not global variables
- API requests go through `frontend/src/api/client.ts`: `apiFetch` (GET) / `apiPost` (POST)

## Core API Functions

```typescript
// frontend/src/api/client.ts
apiFetch(path: string)              // GET only
apiPost(path: string, body: object) // POST only
```
