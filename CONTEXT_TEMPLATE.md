# 📂 PROJECT CONTEXT: [PROJECT_NAME]

> **SYSTEM INSTRUCTION FOR AI:**
> This file is the Single Source of Truth (SSOT) for this project.
> Before generating code, proposing changes, or answering questions, you MUST review the "Current Focus", "Constraints", and "App Map" sections.
> If a user prompt contradicts this file, prioritize this file unless explicitly told to ignore it.

---

## 0. 🤖 AI Instructions (G.R.I.A.L. Protocol)

### Prime Directive

Before answering ANY query, generating code, or analyzing logic, you MUST:

1.  **Read this file** (`context.md`) in the project root immediately.
2.  **Internalize the SSOT:** adopt the Tech Stack, Constraints, and Active Task defined here.
3.  **Resolve Conflicts:** If the user's prompt contradicts this file, prioritize this file or ask for confirmation.

### Vibe & Behavior

- **Concise:** Do not explain basic concepts. Just give the solution.
- **Strict Compliance:** Adhere strictly to the Coding Guidelines in Section 2.
- **Language:** Use **English** for code (variables, functions, types, comments, JSDoc). UI strings shown to users may stay in **[UI_LANGUAGE, e.g., Spanish]**.
- **Scope (YAGNI):** Implement only what is requested. If you see an important improvement, propose it first — do NOT implement without confirmation.
- **Tests:** Write tests only when explicitly requested.
- **Clarification:** If the request is ambiguous, ask before implementing. Do not assume.
- **Documentation:** When flow or architecture changes, update `context.md`, `README`, and relevant docs accordingly.
- **Security:** Always prioritize secure code. Consider auth, validation, input sanitization, RLS (if applicable), and attack prevention in every module. Security-first mindset.
- **Maintenance:** When a task/feature is completed, remind the user to update the checkboxes in this file.
- **Dependencies:** Do NOT introduce new libraries, packages, or tools without explicit permission. If one is needed, propose it with a justification first.
- **Refactoring:** Do not refactor code that is not related to the active task unless explicitly asked.
- **File Awareness:** Before creating a new file, verify it doesn't already exist. Before modifying a file, read its current content first.

### Reset Command

If the user says **"PHOENIX"** or **"RESET"**:

- Ignore all previous chat history.
- Re-read `context.md`.
- Confirm by stating the **Current Active Task** found in Section 5.

---

## 1. 🎯 Project Overview & Boundaries

### Core Vision

- **Elevator Pitch:** [One sentence describing the problem the app solves and for whom.]
- **Target Audience:** [Who is the primary user? Secondary user if applicable?]
- **Key Success Metrics (KPIs):**
  - [KPI 1 — e.g., Visitor-to-registered-user conversion rate.]
  - [KPI 2 — e.g., Weekly retention rate.]
  - [KPI 3 — e.g., Error/waste rate < X%.]

### 🚧 Operational Constraints (Grounding)

_Rules that the business logic MUST follow strictly. These are non-negotiable._

- **[Constraint 1 Name]:** [Detailed description + business reason.]
- **[Constraint 2 Name]:** [Detailed description + business reason.]
- **User Permissions/Roles:**
  - **[Role 1]:** [What this role can do.]
  - **[Role 2]:** [What this role can do.]
- **Platform/Device:** [Mobile-first Web App / Desktop-first / PWA / etc.]

### 🚫 Negative Scope (What we are NOT building)

_Do not waste resources suggesting or implementing these. These are explicit "Time Savers"._

- No [Feature X] — _Reason: [...]._
- No [Feature Y] — _Reason: [...]._
- No [Feature Z] — _Reason: [...]._

### 🏁 MVP Launch Criteria (Definition of Done)

_Binary, verifiable conditions. If ALL are checked, the MVP is ready to ship._

- [ ] [Criterion 1 — e.g., User can Register & Login.]
- [ ] [Criterion 2 — e.g., User can complete the Core Flow.]
- [ ] [Criterion 3 — e.g., Payments active (Test Mode).]
- [ ] [Criterion 4 — e.g., Admin dashboard functional.]
- [ ] Critical bugs resolved.

---

## 2. 🛠️ Tech Stack & Coding Guidelines

_Use only the tools listed below. Do not introduce new libraries without permission._

### Core Stack

- **Frontend:** [e.g., Next.js 15 (App Router), React 19]
- **Styling:** [e.g., Tailwind CSS v4, Mobile-First, Shadcn/UI, Lucide Icons]
- **Backend/BaaS:** [e.g., Supabase / NeonDB / Firebase / Custom Node]
- **Database:** [e.g., PostgreSQL via NeonDB, ORM Drizzle]
- **State Management:** [e.g., Zustand (client state), SWR (server state)]
- **Auth:** [e.g., Clerk / Supabase Auth / NextAuth]
- **Forms:** [e.g., React Hook Form + Zod]
- **Payments:** [e.g., Stripe]
- **Email:** [e.g., Resend]
- **Storage:** [e.g., Cloudflare R2 / Supabase Storage / S3]
- **i18n:** [e.g., next-intl (Spanish default)]

### Coding Guidelines

1.  **Strict Typing:** TypeScript strict mode is mandatory. No `any`.
2.  **File Naming:** Use `kebab-case` for all file names.
3.  **Component Strategy:** Functional components only. Prefer Server Components by default; use `"use client"` only when necessary (hooks, interactivity).
4.  **Error Handling:** All Server Actions must return standardized error objects (e.g., `{ success: boolean; error?: string; data?: T }`).
5.  **Database Abstraction (DAL):** Isolate ALL database queries into dedicated Server Actions or Data Access Layer functions (e.g., `src/actions/` or `src/services/`). **Never** import DB clients directly in UI components. This ensures the DB layer can be swapped without touching the UI.
6.  **Imports:** Use absolute imports with `@/` prefix (configured in `tsconfig.json`).
7.  **Naming Conventions:**
    - Components: `PascalCase` (e.g., `ProductCard.tsx`)
    - Utilities/hooks: `camelCase` (e.g., `useProducts.ts`)
    - Constants: `UPPER_SNAKE_CASE`
    - DB schemas/types: `snake_case` (matching SQL conventions)

---

## 3. 🗺️ App Architecture & Route Inventory

_A comprehensive list of all routes in the application. AI: Keep this updated when routes are added or removed._

### 📂 Directory Structure

```
src/
├── app/              # App Router pages & layouts
│   ├── (shop)/       # Grouped routes with shared layout
│   ├── admin/        # Admin-only routes
│   └── api/          # API routes
├── actions/          # Server Actions (DAL)
├── components/
│   ├── ui/           # Generic primitives (Button, Input, Card...)
│   └── [feature]/    # Feature-specific components
├── hooks/            # Custom React hooks
├── lib/              # Config, utils, DB client, external SDKs
│   └── db/           # Schema definitions, migrations
├── schemas/          # Zod validation schemas
├── store/            # Zustand stores
├── types/            # Shared TypeScript types/interfaces
└── i18n/             # Internationalization config & messages
```

### 📍 Route Inventory (Sitemap)

**Public Routes:**

| Route | Description |
|-------|-------------|
| `/` | [Landing / Redirect logic] |
| `/login` | [Auth screen] |
| [Add routes...] | |

**Protected Routes (requires auth):**

| Route | Description |
|-------|-------------|
| [Add routes...] | |

**Admin Routes (requires auth + admin role):**

| Route | Description |
|-------|-------------|
| [Agregar rutas...] | |

**API Routes:**

| Route | Method | Description |
|-------|--------|-------------|
| [Add routes...] | | |

---

## 4. 🗄️ Domain Model (High-Level Schema)

_Core entities and relationships. See `[path to schema, e.g., src/lib/db/schema.ts]` for full definitions._

### Entities

- **[entity_1]:** `id`, `field_1`, `field_2`, `created_at`, `updated_at`
- **[entity_2]:** `id`, `entity_1_id` (FK), `field_1`, `created_at`
- [Add entities...]

### Key Relationships

```
[entity_1] 1 ──→ N [entity_2]
[entity_2] N ──→ 1 [entity_3]
```

### Database Indexes & Policies

- [Describe important indexes, RLS policies if applicable, or refer to the schema file.]

---

## 5. 📍 Current Project Status

_Update this section at the start of every coding session._

- **Phase:** [e.g., MVP Building / Beta / Production]
- **Current Sprint Focus:** [e.g., Implementing the payments module.]
- **Active Task:** [Write your current task here with enough detail for the AI to understand what to do.]
- **Blockers:** [Any current impediment, or "None".]

### Recent Completions (last 3-5)

_Gives the AI immediate context on recent momentum. Update when completing a task._

- ✅ [e.g., Admin product CRUD with image upload (Phase 3)]
- ✅ [e.g., Order confirmation email via Resend (Phase 2)]
- ✅ [e.g., Cutoff 8:00 AM logic in checkout (Phase 4)]

---

## 6. 📝 Roadmap & Detailed Scope

### 🟢 Phase 1: [Name] (status: ✅ Completed / 🟡 In Progress / ⬜ Planned)

- [x] [Completed feature]
- [ ] [Pending feature]

### 🟡 Phase 2: [Name] (status)

- [ ] [Pending feature]

### ⬜ Phase 3: [Name] (status)

- [ ] [Planned feature]

---

## 7. 🧊 Icebox / Backlog

_Features planned for later versions. Do NOT implement unless explicitly moved to an active Phase._

- [ ] [Future feature 1]
- [ ] [Future feature 2]

---

## 8. 🔀 App Flow (Mermaid Diagram)

_Visual representation of the main user journey. AI: Use this to understand navigation and redirect logic._

```mermaid
flowchart TD
    Root[/]
    Root -->|logged in| Dashboard["/dashboard"]
    Root -->|no session| Login["/login"]

    Login -->|OK| Root

    Dashboard --> Feature1["/feature-1"]
    Feature1 --> Feature2["/feature-2"]

    subgraph ProtectedArea [Requires Auth]
        Dashboard
        Feature1
        Feature2
    end
```

_Update this diagram whenever routes or navigation logic change._

---

## 9. ⚙️ Environment & Secrets

_List of required environment variables. AI: NEVER hardcode secrets. NEVER commit `.env` files._

| Variable | Description | Example |
|----------|-------------|---------|
| `DATABASE_URL` | Connection string for the database | `postgresql://...` |
| `NEXT_PUBLIC_[SERVICE]_KEY` | Public/publishable API key | `pk_test_...` |
| `[SERVICE]_SECRET_KEY` | Private API key (server-only) | `sk_test_...` |
| [Add variables...] | | |

**Notes:**
- File: `.env.local` (local dev), `.env.production` (production — managed in hosting provider).
- Template: `.env.example` is committed to the repo with placeholder values.

---

## 10. 🧰 Key Commands

_Common commands for development. AI: Use these instead of guessing._

| Command | Description |
|---------|-------------|
| `npm run dev` | Start dev server |
| `npm run build` | Production build (for validation) |
| `npm run lint` | Run linter |
| `[ORM push command, e.g., npx drizzle-kit push]` | Push schema changes to DB |
| `[ORM generate command, e.g., npx drizzle-kit generate]` | Generate migrations |
| `[Seed command, e.g., npx tsx prisma/seed.ts]` | Seed the database |
| [Add commands...] | |

---

## 11. 🔌 Third-Party Integrations

_External services and their configuration. AI: Check this before integrating with any service._

### [Service Name, e.g., Stripe]
- **Purpose:** [e.g., Payment processing]
- **SDK/Package:** [e.g., `stripe`, `@stripe/stripe-js`]
- **Dashboard:** [URL to service dashboard]
- **Webhook URL:** [e.g., `/api/webhooks/stripe`]
- **Test/Sandbox Mode:** [Yes/No, + relevant details]
- **Key env vars:** `STRIPE_SECRET_KEY`, `NEXT_PUBLIC_STRIPE_PUBLISHABLE_KEY`

### [Service Name, e.g., Resend]
- **Purpose:** [e.g., Transactional email]
- **SDK/Package:** [e.g., `resend`]
- **Key env vars:** `RESEND_API_KEY`

_Add more integrations as they are configured._

---

## 12. 🚀 Deployment

_Hosting, CI/CD, and branch strategy._

- **Hosting:** [e.g., Vercel / Cloudflare Pages / Fly.io]
- **Production URL:** [e.g., https://app.example.com]
- **Staging URL:** [e.g., https://staging.example.com (if applicable)]
- **Branch Strategy:**
  - `main` → Production (auto-deploy).
  - `develop` → Staging (if applicable).
  - Feature branches → Preview deployments.
- **CI/CD:** [e.g., Vercel auto-deploy on push / GitHub Actions]
- **Domain/DNS:** [e.g., Managed in Cloudflare / Vercel]

---

## 13. 🐛 Known Gotchas & Patterns

_Document recurring issues, non-obvious patterns, and solutions that the AI should know about. This prevents re-discovering the same problems across sessions._

### Gotchas

| Issue | Solution |
|-------|----------|
| [e.g., Hydration mismatch with date formatting] | [e.g., Use `suppressHydrationWarning` on date elements or format only on client.] |
| [e.g., Next.js Image component requires explicit domains] | [e.g., Add domains to `next.config.ts` → `images.remotePatterns`.] |
| [Add known issues...] | |

### Patterns & Conventions

- **[Pattern Name]:** [Description — e.g., "All form submissions go through Server Actions that return `{ success, error?, data? }` objects. The UI checks `result.success` before proceeding."]
- **[Pattern Name]:** [Description — e.g., "Admin routes are protected by Clerk middleware + `publicMetadata.role === 'admin'` check in the layout."]

---

## 14. 📚 Key References

_Links to documentation, design files, and other resources that the AI or developer may need._

- **Design (Figma/Mockups):** [URL or "N/A"]
- **API Documentation:** [URL or "N/A"]
- **Brand Guide / Style Guide:** [URL or "N/A"]
- **Business Requirements Doc:** [URL or "N/A"]
- **Related Repos:** [URLs or "N/A"]
