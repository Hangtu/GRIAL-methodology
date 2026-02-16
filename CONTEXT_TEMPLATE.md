# 📂 PROJECT CONTEXT: [Insert Project Name]

> **SYSTEM INSTRUCTION FOR AI:**
> This file is the Single Source of Truth (SSOT) for this project.
> Before generating code, proposing changes, or answering questions, you MUST review the "Current Focus", "Constraints", and "App Map" sections.
> If a user prompt contradicts this file, prioritize this file unless explicitly told to ignore it.

---

## 1. 🎯 Project Overview & Boundaries

### Core Vision

- **Elevator Pitch:** [One sentence describing what the app does.]
- **Target Audience:** [Who is this exactly for? e.g., Freelancers, Enterprise Sales Teams.]
- **Key Success Metrics (KPIs):**
  - [e.g., Page load under 1s]
  - [e.g., User conversion rate > 5%]

### 🚧 Operational Constraints (Grounding)

_Rules that the logic MUST follow strictly._

- **Geography/Localization:** [e.g., App only accepts Phone Numbers (+52) from Mexico.]
- **User Permissions:** [e.g., Only "Admins" can delete records. Regular users can only archive.]
- **Platform/Device:** [e.g., Mobile-first Web App (PWA optimized). Desktop is secondary.]

### 🚫 Negative Scope (What we are NOT building)

_Do not waste resources suggesting or implementing these._

- [e.g., No Native iOS/Android App (Web only).]
- [e.g., No "Dark Mode" for MVP.]
- [e.g., No social login except Google.]

### 🏁 MVP Launch Criteria (Definition of Done)

- [ ] User can Register & Login.
- [ ] User can complete the Core Flow (Create -> Edit -> Save).
- [ ] Stripe Payments are active (Test Mode).
- [ ] Critical bugs resolved.

---

## 2. 🛠️ Tech Stack & Coding Guidelines

_Use only the tools listed below. Do not introduce new libraries without permission._

### Core Stack

- **Frontend:** [Next.js 15 (App Router), React 19]
- **Styling:** [Tailwind CSS v4, Shadcn/UI, Lucide Icons]
- **Backend/BaaS:** [Supabase, Node.js]
- **Database:** [PostgreSQL]
- **State Management:** [Zustand, React Query]
- **Auth:** [Supabase Auth]

### Guidelines

1.  **Strict Typing:** TypeScript strict mode is mandatory. No `any`.
2.  **File Structure:** Use `kebab-case` for file names.
3.  **Component Strategy:** Use functional components. Prefer server components by default (if using Next.js).
4.  **Error Handling:** All server actions must return standardized error objects.

---

## 3. 🗺️ App Architecture & Route Inventory

_A comprehensive list of all routes in the application. AI: Keep this updated._

### 📂 Directory Structure

- `app/` - App Router pages.
- `components/ui/` - Generic primitives.
- `lib/` - Utilities & Helpers.
- `server/` - Actions & DB queries.
- `types/` - Global TS interfaces.

### 📍 Route Inventory (Sitemap)

**Public Routes:**

- `/` -> Landing Page (Marketing).
- `/login` -> Auth Screen (Login/Register).
- `/legal/privacy` -> Privacy Policy.

**Protected Routes (Requires Auth):**

- `/dashboard` -> Main overview (Stats).
- `/settings` -> User profile & preferences.
- `/[feature]` -> List view of [Feature].
- `/[feature]/[id]` -> Detail/Edit view of [Feature].

---

## 4. 🗄️ Domain Model (High-Level Schema)

_Core entities and relationships._

- **User:** `id`, `email`, `role`, `created_at`
- **[Entity A]:** `id`, `user_id` (FK), `title`, `status`
- **[Entity B]:** `id`, `entity_a_id` (FK), `content`

---

## 5. 📍 Current Project Status

_Update this section at the start of every coding session._

- **Phase:** [e.g., MVP Building / Polishing / Bug Fixing]
- **Current Sprint Focus:** [e.g., Developing the core "Create" flow.]
- **Active Task:** [e.g., Connecting the Form to Supabase.]

---

## 6. 📝 Roadmap & Detailed Scope

### 🟢 Phase 1: Authentication

**Scope:**

- [ ] **Login Screen:** Email/Pass + Google Auth.
- [ ] **Onboarding:** Profile setup.
- [ ] **Middleware:** Protect `/dashboard`.

### 🟢 Phase 2: Core Feature (Dashboard)

**Scope:**

- [ ] **Overview:** KPI Cards + Header.
- [ ] **List View:** Table with Pagination + Search.
- [ ] **Create Action:** Modal/Form to add new items.

### 🟢 Phase 3: Secondary Features

**Scope:**

- [ ] **Settings:** Update profile.
- [ ] **Billing:** Subscription management.

---

## 7. 🧊 Icebox / Backlog

_Features planned for later versions. Do not implement yet._

- [ ] Multi-language support.
- [ ] Export to PDF.
