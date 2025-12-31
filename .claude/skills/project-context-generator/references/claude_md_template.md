# Project: [PROJECT_NAME]

> **One-sentence description of what this project does and who it's for**

---

## 1. Project Overview

### Goals and Success Criteria

**Primary Goals:**
- [Goal 1: e.g., "Enable users to track their daily habits with minimal friction"]
- [Goal 2: e.g., "Provide insights on habit patterns over time"]
- [Goal 3: e.g., "Sync across multiple devices"]

**Success Criteria:**
- [Measurable criterion 1: e.g., "User can create a habit in < 30 seconds"]
- [Measurable criterion 2: e.g., "95% of data syncs complete within 5 seconds"]
- [Measurable criterion 3: e.g., "Zero data loss during sync conflicts"]

### Target Users and Use Cases

**Target Users:**
- [User persona 1: e.g., "Busy professionals seeking to build consistent routines"]
- [User persona 2: e.g., "Students tracking study habits"]

**Primary Use Cases:**
- [Use case 1: e.g., "Daily habit check-in during morning routine"]
- [Use case 2: e.g., "Weekly review of progress and streaks"]
- [Use case 3: e.g., "Viewing insights and trends over months"]

---

## 2. Technical Architecture

### Technology Stack

**Frontend:**
- [Framework/Library: e.g., "React 18 with TypeScript"]
- [UI Library: e.g., "Tailwind CSS + shadcn/ui"]
- [State Management: e.g., "Zustand for client state, React Query for server state"]

**Backend:**
- [Runtime/Framework: e.g., "Node.js with Express"]
- [Language: e.g., "TypeScript"]
- [API Style: e.g., "RESTful API with JSON responses"]

**Database:**
- [Database: e.g., "PostgreSQL 15"]
- [ORM/Query Builder: e.g., "Prisma"]
- [Caching: e.g., "Redis for session storage"]

**Infrastructure:**
- [Deployment: e.g., "Docker containers on AWS ECS"]
- [CI/CD: e.g., "GitHub Actions"]
- [Monitoring: e.g., "Sentry for errors, Datadog for metrics"]

### Project Structure

```
[PROJECT_ROOT]/
├── frontend/
│   ├── src/
│   │   ├── components/     # Reusable UI components
│   │   ├── pages/          # Page-level components
│   │   ├── hooks/          # Custom React hooks
│   │   ├── lib/            # Utilities and helpers
│   │   └── types/          # TypeScript type definitions
│   └── public/             # Static assets
├── backend/
│   ├── src/
│   │   ├── routes/         # API route handlers
│   │   ├── services/       # Business logic
│   │   ├── models/         # Database models (Prisma)
│   │   └── middleware/     # Express middleware
│   └── prisma/             # Database schemas and migrations
├── shared/                 # Code shared between frontend and backend
└── docs/                   # Additional documentation
```

### Key Architectural Decisions

**Decision 1: [Topic]**
- **Choice:** [What was chosen: e.g., "Monorepo structure with workspaces"]
- **Rationale:** [Why: e.g., "Enables code sharing between frontend/backend, simplifies dependency management"]
- **Trade-offs:** [Acknowledged trade-offs: e.g., "Larger initial setup complexity, but better long-term maintainability"]

**Decision 2: [Topic]**
- **Choice:** [What was chosen]
- **Rationale:** [Why]
- **Trade-offs:** [Acknowledged trade-offs]

---

## 3. Project Constraints

### Performance Requirements

- [Requirement 1: e.g., "API response time < 200ms for 95th percentile"]
- [Requirement 2: e.g., "Frontend initial load < 2s on 3G connection"]
- [Requirement 3: e.g., "Support 10,000 concurrent users"]

### Security and Compliance

- [Requirement 1: e.g., "All user data encrypted at rest (AES-256)"]
- [Requirement 2: e.g., "Authentication via OAuth 2.0 + JWT"]
- [Requirement 3: e.g., "GDPR compliant - support data export and deletion"]
- [Requirement 4: e.g., "No PII logged in application logs"]

### Resource Limitations

- [Limitation 1: e.g., "AWS budget capped at $500/month"]
- [Limitation 2: e.g., "Solo developer - prioritize simple, maintainable solutions"]
- [Limitation 3: e.g., "Must work offline with local-first architecture"]

### Timeline and Milestones

- [Milestone 1: e.g., "MVP with core habit tracking - 4 weeks"]
- [Milestone 2: e.g., "Data sync and multi-device support - 8 weeks"]
- [Milestone 3: e.g., "Insights and analytics dashboard - 12 weeks"]

---

## 4. Development Conventions

### Naming Conventions

**Files and Directories:**
- Components: `PascalCase.tsx` (e.g., `HabitCard.tsx`)
- Utilities: `camelCase.ts` (e.g., `formatDate.ts`)
- Hooks: `use + PascalCase.ts` (e.g., `useHabits.ts`)
- Test files: `[name].test.ts` (e.g., `formatDate.test.ts`)

**Code:**
- Variables and functions: `camelCase` (e.g., `getUserHabits`)
- Constants: `UPPER_SNAKE_CASE` (e.g., `MAX_HABITS_PER_USER`)
- Classes and types: `PascalCase` (e.g., `User`, `HabitData`)
- Interfaces: `PascalCase` with `I` prefix (e.g., `IHabitRepository`) OR without prefix based on preference
- Database tables: `snake_case` plural (e.g., `user_habits`)

### Code Organization

**Component Structure:**
```tsx
// 1. Imports (grouped: external, internal, types, styles)
// 2. Type definitions
// 3. Component definition
// 4. Styled components or sub-components (if any)
// 5. Export
```

**API Route Structure:**
```
routes/
  └── habits/
      ├── index.ts          # Route registration
      ├── get.ts            # GET /habits
      ├── post.ts           # POST /habits
      └── [id]/
          ├── get.ts        # GET /habits/:id
          ├── patch.ts      # PATCH /habits/:id
          └── delete.ts     # DELETE /habits/:id
```

### Code Style

**General:**
- Use TypeScript strict mode
- Prefer functional components and hooks over class components
- Use async/await over raw Promises
- Prefer named exports over default exports
- Maximum line length: 100 characters

**Error Handling:**
- Always handle errors explicitly
- Use custom error classes for domain errors
- Log errors with context (user ID, request ID, etc.)

**Comments:**
- JSDoc for public functions and complex logic
- Inline comments only for non-obvious "why", not "what"
- Keep comments concise and up-to-date

### Testing Approach

**Testing Strategy:**
- Unit tests: Business logic and utilities (target 80% coverage)
- Integration tests: API endpoints with database
- E2E tests: Critical user flows only (login, create habit, view dashboard)

**Testing Tools:**
- Unit: Jest + Testing Library
- E2E: Playwright
- API: Supertest

**Test Naming:**
```typescript
describe('ComponentName or functionName', () => {
  it('should [expected behavior] when [condition]', () => {
    // Test implementation
  })
})
```

---

## 5. Available Skills

> **Note:** This section is populated by the `skill-analyzer` meta-skill.
>
> It contains skills from the SkillOS library that are relevant to this project,
> along with guidance on how to use them in this specific context.

[This section will be filled by skill-analyzer]

---

## 6. Missing Skills (Project-Specific)

> **Note:** This section is populated by the `skill-analyzer` meta-skill.
>
> It identifies project-specific skills that should be created to capture
> domain knowledge, workflows, or patterns unique to this project.

[This section will be filled by skill-analyzer]

---

## Maintenance Notes

**Last Updated:** [DATE]

**Recent Changes:**
- [Change 1: e.g., "Migrated from REST to GraphQL"]
- [Change 2: e.g., "Added Redis caching layer"]

**Known Issues:**
- [Issue 1: e.g., "Sync conflicts not fully resolved - temporary solution in place"]
- [Issue 2: e.g., "Performance degrades with >100 habits per user"]

---

*This CLAUDE.md file is a living document. Update it as the project evolves.*
