<!-- sentinel:link-proof -->
### 🔗 Link Proof

_Click through to see exactly what this PR changes, without rebuilding the hunt context._

- **Offending line (upstream)**: [src/healthRuntime.ts:47](https://github.com/vibeforge1111/spark-telegram-bot/blob/main/src/healthRuntime.ts#L47)
- **Severity**: 🟡 MEDIUM
- **Finding ID**: `ERRO-723`
- **Category**: `error-message-actionability`
- **Detector**: `error-message-actionability` (sentinel-engine)
- **Discovered**: 2026-05-24

<!-- sentinel:link-proof -->

## Give the healthRuntime error message a recovery hint

This error message at <code>src/healthRuntime.ts:47</code> is technically correct but operator-hostile — it surfaces the policy without the recovery step. Adding a one-line hint saves a doc-spelunking detour for every user who hits it.

### 🔴 Before

`src/healthRuntime.ts:47`

```typescript
    throw new Error(`Telegram relay runtime is not reachable at ${url}: ${message}`);
```

### 🟢 After

```typescript
    throw new Error(`Telegram relay runtime is not reachable at ${url}: ${message}. Start the relay (e.g. "npm run relay:start") and confirm it is listening at ${url}, then re-run this health check.`);
```

### 🔬 Evidence

| Field | Value |
|---|---|
| File | `src/healthRuntime.ts:47` |
| Category | `error-message-actionability` |
| Severity | 🟡 MEDIUM |
| Detector | `error-message-actionability` |
| Discovered | 2026-05-24 |

---
Tested with the existing test fixtures; nothing regressed. Drop the proof commit before merging if you don't want the <code>.bug-hunter/</code> directory in <code>main</code>.
