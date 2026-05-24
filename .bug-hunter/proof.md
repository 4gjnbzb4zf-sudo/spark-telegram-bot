<!-- sentinel:link-proof -->
### 🔗 Link Proof

_Click through to see exactly what this PR changes, without rebuilding the hunt context._

- **Offending line (upstream)**: [src/naturalRouteReplay.ts:76](https://github.com/vibeforge1111/spark-telegram-bot/blob/main/src/naturalRouteReplay.ts#L76)
- **Severity**: 🟡 MEDIUM
- **Finding ID**: `ERRO-610`
- **Category**: `error-message-actionability`
- **Detector**: `error-message-actionability` (sentinel-engine)
- **Discovered**: 2026-05-24

<!-- sentinel:link-proof -->

## Surface the next step alongside the naturalRouteReplay error

The error at <code>src/naturalRouteReplay.ts:76</code> names what went wrong but not what to do about it. An operator hitting this message has to read source to figure out the fix — which is exactly the kind of friction that turns minor failures into hour-long debug sessions.

### 🔴 Before

`src/naturalRouteReplay.ts:76`

```typescript
    throw new Error(`Replay case line ${lineNumber} needs id, currentMessage, and expectedRoute.`);
```

### 🟢 After

```typescript
    throw new Error(`Replay case line ${lineNumber} is missing required fields. Add non-empty "id", "currentMessage", and "expectedRoute" string properties to the JSON object on this line, e.g. {"id":"case-1","currentMessage":"hello","expectedRoute":"smalltalk"}.`);
```

### 🔬 Evidence

| Field | Value |
|---|---|
| File | `src/naturalRouteReplay.ts:76` |
| Category | `error-message-actionability` |
| Severity | 🟡 MEDIUM |
| Detector | `error-message-actionability` |
| Discovered | 2026-05-24 |

---
No behavioral change beyond the surfaced log line. Happy to split this if you'd prefer separate PRs per call site.
