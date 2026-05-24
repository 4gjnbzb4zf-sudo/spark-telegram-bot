<!-- sentinel:link-proof -->
### 🔗 Link Proof

_Click through to see exactly what this PR changes, without rebuilding the hunt context._

- **Offending line (upstream)**: [src/pythonCommand.ts:19](https://github.com/vibeforge1111/spark-telegram-bot/blob/main/src/pythonCommand.ts#L19)
- **Severity**: 🟡 MEDIUM
- **Finding ID**: `ERRO-760`
- **Category**: `error-message-actionability`
- **Detector**: `error-message-actionability` (sentinel-engine)
- **Discovered**: 2026-05-24

<!-- sentinel:link-proof -->

## Surface the next step alongside the pythonCommand error

This error message at <code>src/pythonCommand.ts:19</code> is technically correct but operator-hostile — it surfaces the policy without the recovery step. Adding a one-line hint saves a doc-spelunking detour for every user who hits it.

### 🔴 Before

`src/pythonCommand.ts:19`

```typescript
    throw new Error(`SPARK_BUILDER_PYTHON is not a file: ${resolved}`);
```

### 🟢 After

```typescript
    throw new Error(`SPARK_BUILDER_PYTHON is not a file: ${resolved}. Set SPARK_BUILDER_PYTHON to the full path of a Python executable (e.g. /usr/bin/python3).`);
```

### 🔬 Evidence

| Field | Value |
|---|---|
| File | `src/pythonCommand.ts:19` |
| Category | `error-message-actionability` |
| Severity | 🟡 MEDIUM |
| Detector | `error-message-actionability` |
| Discovered | 2026-05-24 |

---
Single-purpose change. Compile-verified locally; behavior unchanged for the success path.
