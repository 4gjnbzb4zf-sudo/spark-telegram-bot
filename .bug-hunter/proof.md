<!-- sentinel:link-proof -->
### 🔗 Link Proof

_Click through to see exactly what this PR changes, without rebuilding the hunt context._

- **Offending line (upstream)**: [src/liveNlVerdict.ts:73](https://github.com/vibeforge1111/spark-telegram-bot/blob/main/src/liveNlVerdict.ts#L73)
- **Severity**: 🟡 MEDIUM
- **Finding ID**: `ERRO-827`
- **Category**: `error-message-actionability`
- **Detector**: `error-message-actionability` (sentinel-engine)
- **Discovered**: 2026-05-24

<!-- sentinel:link-proof -->

## Surface the next step alongside the liveNlVerdict error

The error at <code>src/liveNlVerdict.ts:73</code> names what went wrong but not what to do about it. An operator hitting this message has to read source to figure out the fix — which is exactly the kind of friction that turns minor failures into hour-long debug sessions.

### 🔴 Before

`src/liveNlVerdict.ts:73`

```typescript
    throw new Error(`Live NL case ${parsed.id} has unsupported risk ${parsed.risk || 'unknown'}.`);
```

### 🟢 After

```typescript
    throw new Error(`Live NL case ${parsed.id} has unsupported risk ${parsed.risk || 'unknown'}. Set risk to one of: safe, mission, writes_files, external (for example, risk: "safe").`);
```

### 🔬 Evidence

| Field | Value |
|---|---|
| File | `src/liveNlVerdict.ts:73` |
| Category | `error-message-actionability` |
| Severity | 🟡 MEDIUM |
| Detector | `error-message-actionability` |
| Discovered | 2026-05-24 |

---
No behavioral change beyond the surfaced log line. Happy to split this if you'd prefer separate PRs per call site.
