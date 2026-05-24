<!-- sentinel:link-proof -->
### 🔗 Link Proof

_Click through to see exactly what this PR changes, without rebuilding the hunt context._

- **Offending line (upstream)**: [src/pythonCommand.ts:15](https://github.com/vibeforge1111/spark-telegram-bot/blob/main/src/pythonCommand.ts#L15)
- **Severity**: 🟡 MEDIUM
- **Finding ID**: `ERRO-876`
- **Category**: `error-message-actionability`
- **Detector**: `error-message-actionability` (sentinel-engine)
- **Discovered**: 2026-05-24

<!-- sentinel:link-proof -->

## Make the pythonCommand error tell the user what to do next

This error message at <code>src/pythonCommand.ts:15</code> is technically correct but operator-hostile — it surfaces the policy without the recovery step. Adding a one-line hint saves a doc-spelunking detour for every user who hits it.

### 🔴 Before

`src/pythonCommand.ts:15`

```typescript
    throw new Error(`SPARK_BUILDER_PYTHON cannot point to a shell script: ${resolved}`);
```

### 🟢 After

```typescript
    throw new Error(`SPARK_BUILDER_PYTHON cannot point to a shell script: ${resolved}. Set SPARK_BUILDER_PYTHON to a Python executable (e.g. C:\\Python311\\python.exe) instead of a .bat/.cmd/.ps1 wrapper.`);
```

### 🔬 Evidence

| Field | Value |
|---|---|
| File | `src/pythonCommand.ts:15` |
| Category | `error-message-actionability` |
| Severity | 🟡 MEDIUM |
| Detector | `error-message-actionability` |
| Discovered | 2026-05-24 |

---
No behavioral change beyond the surfaced log line. Happy to split this if you'd prefer separate PRs per call site.
