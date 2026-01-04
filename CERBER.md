# CERBER.md - Architecture Roadmap

> **This is your single source of truth. AI agents and developers enforce this contract.**

## CERBER_CONTRACT
```yaml
version: 1
mode: team  # solo | dev | team

guardian:
  enabled: true
  schemaFile: BACKEND_SCHEMA.mjs
  hook: husky
  approvalsTag: ARCHITECT_APPROVED

health:
  enabled: true
  endpoint: /api/health
  failOn:
    critical: true
    error: true
    warning: false

ci:
  provider: github
  branches: [main]
  requiredOnPR: true
  postDeploy:
    enabled: false
    waitSeconds: 90
    healthUrlVar: CERBER_HEALTH_URL
    authHeaderSecret: CERBER_HEALTH_AUTH_HEADER

schema:
  enabled: true
  file: BACKEND_SCHEMA.ts
  mode: template_only  # strict | template_only
  description: "Project architecture contract (user-owned)"
  # strict = Cerber never creates schema, you must create it
  # template_only = Cerber creates minimal template if missing
```

---

## 🎯 Architecture Roadmap

**Status:** Initial Setup

### Phase 1: Foundation (Current)
- [ ] Setup Guardian pre-commit validation
- [ ] Configure health checks
- [ ] Integrate CI/CD pipeline

### Phase 2: Production Readiness
- [ ] Add monitoring
- [ ] Configure alerting
- [ ] Load testing

---

## 📋 Guidelines

### Code Organization
- Routes in `src/routes/`
- Business logic in `src/services/`
- Database schema in `src/shared/schema.ts`

### Standards
- TypeScript strict mode
- ESLint configuration
- Test coverage > 80%

---

## 🛡️ Guardian Rules

See `BACKEND_SCHEMA.ts` for complete architecture rules.

---

*This file is protected by CODEOWNERS. Changes require architect approval.*

