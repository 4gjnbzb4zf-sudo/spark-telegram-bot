<!-- sentinel:link-proof -->
### 🔗 Link Proof

_Click through to see exactly what this PR changes, without rebuilding the hunt context._

- **Offending line (upstream)**: [src/naturalRouteReplay.ts:70](https://github.com/vibeforge1111/spark-telegram-bot/blob/main/src/naturalRouteReplay.ts#L70)
- **Severity**: 🟡 MEDIUM
- **Finding ID**: `ERRO-758`
- **Category**: `error-message-actionability`
- **Detector**: `error-message-actionability` (sentinel-engine)
- **Discovered**: 2026-05-24

<!-- sentinel:link-proof -->

## Make the naturalRouteReplay error tell the user what to do next

This error message at <code>src/naturalRouteReplay.ts:70</code> is technically correct but operator-hostile — it surfaces the policy without the recovery step. Adding a one-line hint saves a doc-spelunking detour for every user who hits it.

### 🔴 Before

`src/naturalRouteReplay.ts:70`

```typescript
    throw new Error(`Replay case line ${lineNumber} is not an object.`);
```

### 🟢 After

```typescript
    throw new Error(`Replay case line ${lineNumber} is not an object. Provide a JSON object per line, e.g. {"id":"case-1","currentMessage":"...","expectedRoute":"..."}.`);
```

### 🔬 Evidence

| Field | Value |
|---|---|
| File | `src/naturalRouteReplay.ts:70` |
| Category | `error-message-actionability` |
| Severity | 🟡 MEDIUM |
| Detector | `error-message-actionability` |
| Discovered | 2026-05-24 |

---
No behavioral change beyond the surfaced log line. Happy to split this if you'd prefer separate PRs per call site.
