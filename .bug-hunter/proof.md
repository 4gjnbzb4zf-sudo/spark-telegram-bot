<!-- sentinel:link-proof -->
### 🔗 Link Proof

_Click through to see exactly what this PR changes, without rebuilding the hunt context._

- **Offending line (upstream)**: [src/healthRuntime.ts:36](https://github.com/vibeforge1111/spark-telegram-bot/blob/main/src/healthRuntime.ts#L36)
- **Severity**: 🟡 MEDIUM
- **Finding ID**: `ERRO-825`
- **Category**: `error-message-actionability`
- **Detector**: `error-message-actionability` (sentinel-engine)
- **Discovered**: 2026-05-24

<!-- sentinel:link-proof -->

## Make the healthRuntime error tell the user what to do next

This error message at <code>src/healthRuntime.ts:36</code> is technically correct but operator-hostile — it surfaces the policy without the recovery step. Adding a one-line hint saves a doc-spelunking detour for every user who hits it.

### 🔴 Before

`src/healthRuntime.ts:36`

```typescript
      throw new Error('Telegram polling status is missing');
```

### 🟢 After

```typescript
      throw new Error('Telegram polling status is missing from relay /health response; ensure the relay reports runtime.telegramPolling (expected "active" or "disabled_smoke") and restart the relay.');
```

### 🔬 Evidence

| Field | Value |
|---|---|
| File | `src/healthRuntime.ts:36` |
| Category | `error-message-actionability` |
| Severity | 🟡 MEDIUM |
| Detector | `error-message-actionability` |
| Discovered | 2026-05-24 |

---
Single-purpose change. Compile-verified locally; behavior unchanged for the success path.
