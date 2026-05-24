<!-- sentinel:link-proof -->
### 🔗 Link Proof

_Click through to see exactly what this PR changes, without rebuilding the hunt context._

- **Offending line (upstream)**: [src/healthPolling.ts:41](https://github.com/vibeforge1111/spark-telegram-bot/blob/main/src/healthPolling.ts#L41)
- **Severity**: 🟡 MEDIUM
- **Finding ID**: `ERRO-449`
- **Category**: `error-message-actionability`
- **Detector**: `error-message-actionability` (sentinel-engine)
- **Discovered**: 2026-05-24

<!-- sentinel:link-proof -->

## Make the healthPolling error tell the user what to do next

The error at <code>src/healthPolling.ts:41</code> names what went wrong but not what to do about it. An operator hitting this message has to read source to figure out the fix — which is exactly the kind of friction that turns minor failures into hour-long debug sessions.

### 🔴 Before

`src/healthPolling.ts:41`

```typescript
    throw new Error('BOT_TOKEN is required for Telegram long polling.');
```

### 🟢 After

```typescript
    throw new Error('BOT_TOKEN is required for Telegram long polling. Create a bot via @BotFather, then run `spark setup --bot-token <token>` or set BOT_TOKEN in your .env file.');
```

### 🔬 Evidence

| Field | Value |
|---|---|
| File | `src/healthPolling.ts:41` |
| Category | `error-message-actionability` |
| Severity | 🟡 MEDIUM |
| Detector | `error-message-actionability` |
| Discovered | 2026-05-24 |

---
No behavioral change beyond the surfaced log line. Happy to split this if you'd prefer separate PRs per call site.
