<!-- sentinel:link-proof -->
### 🔗 Link Proof

_Click through to see exactly what this PR changes, without rebuilding the hunt context._

- **Offending line (upstream)**: [src/liveNlVerdict.ts:70](https://github.com/vibeforge1111/spark-telegram-bot/blob/main/src/liveNlVerdict.ts#L70)
- **Severity**: 🟡 MEDIUM
- **Finding ID**: `ERRO-515`
- **Category**: `error-message-actionability`
- **Detector**: `error-message-actionability` (sentinel-engine)
- **Discovered**: 2026-05-24

<!-- sentinel:link-proof -->

## Give the liveNlVerdict error message a recovery hint

This error message at <code>src/liveNlVerdict.ts:70</code> is technically correct but operator-hostile — it surfaces the policy without the recovery step. Adding a one-line hint saves a doc-spelunking detour for every user who hits it.

### 🔴 Before

`src/liveNlVerdict.ts:70`

```typescript
    throw new Error(`Live NL case ${index + 1} needs id, suite, prompt or turns, expectedRoute, and expectedOutcome.`);
```

### 🟢 After

```typescript
    throw new Error(`Live NL case ${index + 1} is missing required fields. Add string values for: id, suite, prompt (or turns[]), expectedRoute, and expectedOutcome. Example: { "id": "case-1", "suite": "routing_architecture", "prompt": "...", "expectedRoute": "operator", "expectedOutcome": "..." }.`);
```

### 🔬 Evidence

| Field | Value |
|---|---|
| File | `src/liveNlVerdict.ts:70` |
| Category | `error-message-actionability` |
| Severity | 🟡 MEDIUM |
| Detector | `error-message-actionability` |
| Discovered | 2026-05-24 |

---
Tested with the existing test fixtures; nothing regressed. Drop the proof commit before merging if you don't want the <code>.bug-hunter/</code> directory in <code>main</code>.
