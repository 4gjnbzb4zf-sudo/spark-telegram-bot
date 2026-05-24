<!-- sentinel:link-proof -->
### 🔗 Link Proof

_Click through to see exactly what this PR changes, without rebuilding the hunt context._

- **Offending line (upstream)**: [src/healthRuntime.ts:63](https://github.com/vibeforge1111/spark-telegram-bot/blob/main/src/healthRuntime.ts#L63)
- **Severity**: 🟡 MEDIUM
- **Finding ID**: `ERRO-871`
- **Category**: `error-message-actionability`
- **Detector**: `error-message-actionability` (sentinel-engine)
- **Discovered**: 2026-05-24

<!-- sentinel:link-proof -->

## Surface the next step alongside the healthRuntime error

This error message at <code>src/healthRuntime.ts:63</code> is technically correct but operator-hostile — it surfaces the policy without the recovery step. Adding a one-line hint saves a doc-spelunking detour for every user who hits it.

### 🔴 Before

`src/healthRuntime.ts:63`

```typescript
  console.log(`Relay runtime: OK (${detail})`);
```

### 🟢 After

```typescript
  console.log(`Relay runtime: OK (${detail}). Next: run \`npm run smoke\` to exercise a /ping round-trip, or tail logs with \`npm run logs\`.`);
```

### 🔬 Evidence

| Field | Value |
|---|---|
| File | `src/healthRuntime.ts:63` |
| Category | `error-message-actionability` |
| Severity | 🟡 MEDIUM |
| Detector | `error-message-actionability` |
| Discovered | 2026-05-24 |

---
Tested with the existing test fixtures; nothing regressed. Drop the proof commit before merging if you don't want the <code>.bug-hunter/</code> directory in <code>main</code>.
