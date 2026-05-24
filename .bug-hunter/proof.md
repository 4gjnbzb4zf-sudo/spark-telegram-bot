<!-- sentinel:link-proof -->
### 🔗 Link Proof

_Click through to see exactly what this PR changes, without rebuilding the hunt context._

- **Offending line (upstream)**: [src/liveNlVerdict.ts:55](https://github.com/vibeforge1111/spark-telegram-bot/blob/main/src/liveNlVerdict.ts#L55)
- **Severity**: 🟡 MEDIUM
- **Finding ID**: `ERRO-739`
- **Category**: `error-message-actionability`
- **Detector**: `error-message-actionability` (sentinel-engine)
- **Discovered**: 2026-05-24

<!-- sentinel:link-proof -->

## Give the liveNlVerdict error message a recovery hint

The error at <code>src/liveNlVerdict.ts:55</code> names what went wrong but not what to do about it. An operator hitting this message has to read source to figure out the fix — which is exactly the kind of friction that turns minor failures into hour-long debug sessions.

### 🔴 Before

`src/liveNlVerdict.ts:55`

```typescript
    throw new Error(`Live NL case ${index + 1} is not an object.`);
```

### 🟢 After

```typescript
    throw new Error(`Live NL case ${index + 1} is not an object. Ensure each case is a JSON object like {"id": "...", "suite": "...", "risk": "safe", "prompt": "...", "expectedRoute": "...", "expectedOutcome": "..."}.`);
```

### 🔬 Evidence

| Field | Value |
|---|---|
| File | `src/liveNlVerdict.ts:55` |
| Category | `error-message-actionability` |
| Severity | 🟡 MEDIUM |
| Detector | `error-message-actionability` |
| Discovered | 2026-05-24 |

---
Single-purpose change. Compile-verified locally; behavior unchanged for the success path.
