# 📂 PROJECT CONTEXT: Lonchi-web

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
- **Language:** Use **English** for code (variables, functions, comments). Use **Spanish** for UI strings shown to the user.
- **Scope (YAGNI):** Implement only what is requested. If you see an important improvement, propose it first.
- **Security:** Always prioritize secure code (RLS, validation, input sanitization).
- **Maintenance:** When a task is done, remind the user to update the checkboxes in this file.

### Reset Command

If the user says **"PHOENIX"** or **"RESET"**:

- Ignore all previous chat history.
- Re-read `context.md`.
- Confirm by stating the **Current Active Task** found in Section 5.

---

## 1. 🎯 Project Overview & Boundaries

### Core Vision

- **Elevator Pitch:** App para que padres con poco tiempo puedan ordenar loncheras con comida saludable para sus hijos.
- **Target Audience:** Padres de familia (kinder y primaria).
- **Key Success Metrics (KPIs):**
  - [Por definir]

### 🚧 Operational Constraints (Grounding)

_Rules that the logic MUST follow strictly._

- **Cutoff 8:00 AM:** Si se ordena después de las 8:00 AM, solo se permite pedido para el día siguiente. Antes de las 8:00 AM, se permite pedido para el mismo día.
- **Geography:** [Por definir]
- **User Permissions:** Actualmente no hay rol de "Admin" diferenciado en DB. Cualquier usuario autenticado puede acceder a `/admin` (esto debe protegerse por Middleware o RLS en el futuro).
- **Platform:** Mobile-first Web App (Responsive).

### 🚫 Negative Scope (What we are NOT building)

_Do not waste resources suggesting or implementing these._

- No app nativa iOS/Android (Solo Web).
- No sistema de tracking de repartidores en tiempo real (por ahora).

### 🏁 MVP Launch Criteria (Definition of Done)

- [x] User can Register & Login.
- [x] User can complete the Core Flow (Onboarding → Menú → Carrito → Checkout).
- [ ] Stripe Payments active (Test Mode) — _Actualmente pago manual._
- [ ] Regla de corte 8:00 AM implementada en Checkout.
- [ ] Dashboard Admin: Vista de pedidos pendientes/terminados + Excel.
- [ ] Critical bugs resolved.

---

## 2. 🛠️ Tech Stack & Coding Guidelines

_Use only the tools listed below._

### Core Stack

- **Frontend:** Next.js 15 (App Router), React 19.
- **Styling:** Tailwind CSS v4, Mobile-First methodology, Shadcn/UI components, Lucide Icons.
- **Backend/BaaS:** Supabase (Auth, DB, Storage).
- **Database:** PostgreSQL (via Supabase), ORM Drizzle.
- **State Management:** Zustand (Client state: cart, onboarding), SWR (Server state).
- **Auth:** Supabase Auth.
- **Forms:** React Hook Form + Zod.
- **Payments:** Stripe (Setup ready, not active in checkout yet).
- **Email:** Resend.
- **i18n:** next-intl (Español default).

### Guidelines

1.  **Strict Typing:** TypeScript strict mode is mandatory. No `any`.
2.  **File Structure:** Use `kebab-case` for file names.
3.  **Component Strategy:** Use functional components. Prefer Server Components by default.
4.  **Error Handling:** All Server Actions must return standardized error objects.

---

## 3. 🗺️ App Architecture & Route Inventory

_A comprehensive list of all routes. AI: Keep this updated._

### 📂 Directory Structure

- `src/app/` — App Router pages.
- `src/components/ui/` — Generic primitives.
- `src/lib/` — Supabase config, utils, db schema.
- `src/store/` — Zustand stores (cart, onboarding).
- `src/hooks/` — Custom hooks.
- `src/schemas/` — Zod schemas.

### 📍 Route Inventory (Sitemap)

**Public Routes:**

- `/` → Landing / Redirection logic.
- `/login` → Auth Screen.
- `/onboarding/welcome` → Intro flow.
- `/onboarding/child` → Child data entry (Zustand/DB).
- `/onboarding/address` → Address entry (Zustand/DB).

**Protected Routes (Shop Layout):**

- `/menu` → Main listing.
- `/product/[id]` → Detail view.
- `/cart` → Shopping cart.
- `/checkout` → 3-step process.
- `/checkout/success` → Thank you page.
- `/orders` → Order history.
- `/profile` → User settings.

**Admin Routes (Protected):**

- `/admin/products` → CRUD List.
- `/admin/products/new` → Create.
- `/admin/products/[id]` → Edit.
- `/admin/orders` → Order Management (Pending).

**API Routes:**

- `/auth/callback`
- `/api/seed-demo`
- `/api/create-payment-intent`
- `/api/send-order-confirmation`

---

## 4. 🗄️ Domain Model (High-Level Schema)

_See `src/lib/db/schema.ts` for full definitions._

- **profiles:** `id`, `email`, `full_name`, `stripe_customer_id`.
- **children:** `id`, `parent_id`, `name`, `school_name`, `allergies` (JSON/Array).
- **delivery_addresses:** `id`, `profile_id`, `address`, `school_id`, `preferred_time`.
- **products:** `id`, `name`, `price`, `category`, `cutoff_time` logic.
- **orders:** `id`, `parent_id`, `status`, `delivery_date`, `total_amount`.
- **order_items:** `id`, `order_id`, `product_id`, `child_id`, `quantity`.

---

## 5. 📍 Current Project Status

_Update this section at the start of every coding session._

- **Phase:** MVP Building / Admin Features
- **Current Sprint Focus:** Implementación del Dashboard de Administrador y reporte de pedidos.
- **Active Task:** [Escribe aquí tu tarea actual, ej: "Creando la vista de pedidos pendientes en /admin/orders"]

---

## 6. 📝 Roadmap & Detailed Scope

### 🟢 Phase 1: Authentication & Onboarding (Completed)

- [x] Login & Register.
- [x] Middleware Protection.
- [x] Onboarding Flow (Welcome -> Child -> Address).

### 🟢 Phase 2: Shop Core (Completed)

- [x] Menu & Cart logic.
- [x] Checkout 3-steps.
- [x] Order Creation (DB Transaction).
- [x] Email Confirmation (Resend).

### 🟡 Phase 3: Admin & Operations (In Progress)

- [x] CRUD Products.
- [ ] **Dashboard:** Vista de pedidos del día (filtrado por fecha).
- [ ] **Export:** Botón para descargar Excel de pedidos (Corte 8 AM).
- [ ] **Logic:** Implementar visualmente el corte de las 8 AM en el selector de fecha del Checkout.

---

## 7. 🧊 Icebox / Backlog

- [ ] Stripe Live Payments.
- [ ] Role-Based Access Control (RBAC) real.
- [ ] Persistencia de
