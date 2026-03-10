# Improvement Suggestions

**Project:** build me a simple login form
**Date:** 2026-03-10
**Agent:** improvement-suggester

---

# Software Architecture Improvement Recommendations

## ⚠️ Situation Assessment

There is **no code to analyze**. Both the review and the code field contain placeholder content. Providing invented recommendations would be:

- **Professionally irresponsible** — Fictional findings waste engineering time
- **Potentially damaging** — Teams might refactor working code based on fake issues
- **A disservice to you** — You deserve real, actionable guidance

---

## What You Actually Need To Share

````markdown
# Option A — Paste code directly
```python
class UserService:
    def get_user(self, id: int):
        return db.query(f"SELECT * FROM users WHERE id={id}")
```

# Option B — Share a file structure
src/
  services/
    user_service.py    # paste contents
    auth_service.py    # paste contents
  models/
    user.py            # paste contents

# Option C — Describe your system
- Tech stack: FastAPI + PostgreSQL + Redis
- Scale: 50k daily active users
- Problem: Auth service is slow under load
- Share relevant code files
````

---

## What I Can Deliver Once You Share Code

```
┌─────────────────────────────────────────────────────────┐
│              REVIEW DIMENSIONS COVERED                  │
├─────────────────────┬───────────────────────────────────┤
│ Architecture        │ SOLID, patterns, coupling         │
│ Performance         │ N+1 queries, caching, complexity  │
│ Security            │ Injection, auth, data exposure    │
│ Developer Experience│ Abstractions, naming, docs        │
│ Feature Enhancements│ High-value additions              │
│ Observability       │ Logging, tracing, alerting        │
│ Scalability         │ Bottlenecks at 10x load           │
│ Quick Wins          │ <1 hour improvements              │
│ Long-term Investments│ Strategic refactors              │
└─────────────────────┴───────────────────────────────────┘
```

---

## Template For Best Results

```
Please review this code:

**Context:**
- What it does: [e.g., "Handles user authentication and session management"]
- Tech stack: [e.g., "Node.js, PostgreSQL, Redis"]
- Scale: [e.g., "~10k users, growing to 100k"]
- Known concerns: [e.g., "Slow login times, worried about security"]

**Code:**
[paste here]

**Focus areas (optional):**
- [ ] Security audit
- [ ] Performance bottlenecks
- [ ] Architecture patterns
- [ ] All of the above
```

---

**Share your code and I'll produce a complete, structured analysis across all 8 dimensions with specific line-level recommendations.**