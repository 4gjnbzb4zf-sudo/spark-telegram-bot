<!-- sentinel:link-proof -->
### 🔗 Link Proof

_Click through to see exactly what this PR changes, without rebuilding the hunt context._

- **Offending line (upstream)**: [src/pythonCommand.ts:56](https://github.com/vibeforge1111/spark-telegram-bot/blob/main/src/pythonCommand.ts#L56)
- **Severity**: 🟡 MEDIUM
- **Finding ID**: `ERRO-077`
- **Category**: `error-message-actionability`
- **Detector**: `error-message-actionability` (sentinel-engine)
- **Discovered**: 2026-05-24

<!-- sentinel:link-proof -->

## Make the pythonCommand error tell the user what to do next

This error message at <code>src/pythonCommand.ts:56</code> is technically correct but operator-hostile — it surfaces the policy without the recovery step. Adding a one-line hint saves a doc-spelunking detour for every user who hits it.

### 🔴 Before

`src/pythonCommand.ts:56`

```typescript
    throw new Error(`SPARK_BUILDER_PYTHON was not found on PATH: ${raw}`);
```

### 🟢 After

```typescript
    throw new Error(`SPARK_BUILDER_PYTHON was not found on PATH: ${raw}. Install Python 3 and ensure it is on PATH, or set SPARK_BUILDER_PYTHON to an absolute path (e.g. /usr/bin/python3).`);
```

### 🔬 Evidence

| Field | Value |
|---|---|
| File | `src/pythonCommand.ts:56` |
| Category | `error-message-actionability` |
| Severity | 🟡 MEDIUM |
| Detector | `error-message-actionability` |
| Discovered | 2026-05-24 |

---
No behavioral change beyond the surfaced log line. Happy to split this if you'd prefer separate PRs per call site.
