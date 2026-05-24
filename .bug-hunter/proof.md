<!-- sentinel:link-proof -->
### 🔗 Link Proof

_Click through to see exactly what this PR changes, without rebuilding the hunt context._

- **Offending line (upstream)**: [src/healthRuntime.ts:71](https://github.com/vibeforge1111/spark-telegram-bot/blob/main/src/healthRuntime.ts#L71)
- **Severity**: 🟡 MEDIUM
- **Finding ID**: `ERRO-207`
- **Category**: `error-message-actionability`
- **Detector**: `error-message-actionability` (sentinel-engine)
- **Discovered**: 2026-05-24

<!-- sentinel:link-proof -->

## Surface the next step alongside the healthRuntime error

The error at <code>src/healthRuntime.ts:71</code> names what went wrong but not what to do about it. An operator hitting this message has to read source to figure out the fix — which is exactly the kind of friction that turns minor failures into hour-long debug sessions.

### 🔴 Before

`src/healthRuntime.ts:71`

```typescript
      console.error(`Telegram runtime health: FAILED - ${(error as Error).message}`);
```

### 🟢 After

```typescript
      console.error(`Telegram runtime health: FAILED - ${(error as Error).message}. Start the relay (e.g. "npm run relay") and retry, or run with TEST_BOT_TOKEN set for token-only checks.`);
```

### 🔬 Evidence

| Field | Value |
|---|---|
| File | `src/healthRuntime.ts:71` |
| Category | `error-message-actionability` |
| Severity | 🟡 MEDIUM |
| Detector | `error-message-actionability` |
| Discovered | 2026-05-24 |

---
Single-purpose change. Compile-verified locally; behavior unchanged for the success path.
