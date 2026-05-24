<!-- sentinel:link-proof -->
### 🔗 Link Proof

_Click through to see exactly what this PR changes, without rebuilding the hunt context._

- **Offending line (upstream)**: [src/healthRuntime.ts:39](https://github.com/vibeforge1111/spark-telegram-bot/blob/main/src/healthRuntime.ts#L39)
- **Severity**: 🟡 MEDIUM
- **Finding ID**: `ERRO-642`
- **Category**: `error-message-actionability`
- **Detector**: `error-message-actionability` (sentinel-engine)
- **Discovered**: 2026-05-24

<!-- sentinel:link-proof -->

## Surface the next step alongside the healthRuntime error

The error at <code>src/healthRuntime.ts:39</code> names what went wrong but not what to do about it. An operator hitting this message has to read source to figure out the fix — which is exactly the kind of friction that turns minor failures into hour-long debug sessions.

### 🔴 Before

`src/healthRuntime.ts:39`

```typescript
      throw new Error(`Telegram polling is ${pollingState}`);
```

### 🟢 After

```typescript
      throw new Error(`Telegram polling is ${pollingState}; expected 'active' or 'disabled_smoke'. Restart the relay (npm run relay) or check BOT_TOKEN and SPARK_PROFILE settings.`);
```

### 🔬 Evidence

| Field | Value |
|---|---|
| File | `src/healthRuntime.ts:39` |
| Category | `error-message-actionability` |
| Severity | 🟡 MEDIUM |
| Detector | `error-message-actionability` |
| Discovered | 2026-05-24 |

---
Single-purpose change. Compile-verified locally; behavior unchanged for the success path.
