# START HERE: Build Instructions for AI Agents

You are being given a complete product specification to build. This folder contains everything you need to understand, plan, and implement a fully functional application.

**Your task:** Read and deeply understand all documentation in this folder, then create a comprehensive implementation plan and build the system.

---

## What You Are Building

A **personal TV & movie companion app** that lets users collect, organize, rate, and discover entertainment. The app combines traditional library management with AI-powered discovery features including conversational recommendations, concept-based exploration, and "alchemy" blending of shows.

---

## How to Use This Documentation

### Step 1: Read the Core Requirements (Mandatory)

**Start with these two documents in order:**

1. **`showbiz_prd.md`** — The primary product requirements document
   - Defines the complete product: features, data model, business rules, user journeys
   - This is the source of truth for *what* the app does
   - Read sections 1-9 carefully; they define the entire product surface
   - Section 12 references companion documents that may not be present—ignore any missing references

2. **`showbiz_infra_rider_prd.md`** — Infrastructure and execution requirements
   - Defines *how* the app must be built and run
   - Specifies: Next.js + Supabase as the required stack
   - Defines namespace/user isolation model (critical for data architecture)
   - Defines environment variable interface and repo deliverables
   - **Do not skip this**—it contains hard requirements for the build

### Step 2: Read All Supporting Documents (Mandatory)

These documents provide critical detail that the main PRD references. A build without understanding these will be incomplete or incorrect.

**`supporting_docs/ai_voice_personality.md`**
- Defines the AI persona and voice across all AI surfaces
- Contains the "non-negotiable voice pillars" that make the AI feel right
- Note: Search has no AI voice—only Scoop, Ask, Alchemy, and Explore Similar
- **Why it matters:** Without this, AI outputs will feel generic or wrong

**`supporting_docs/ai_prompting_context.md`**
- Implementation-facing prompt and context contracts
- Contains the actual prompts used for AI features
- **Why it matters:** Direct implementation guidance for AI features

**`supporting_docs/concept_system.md`**
- Defines what "concepts" are and how they're generated
- Concepts are the core of Alchemy and Explore Similar features
- Contains quality rules (specific vs generic concepts)
- **Why it matters:** The concept system is what makes discovery feel magical

**`supporting_docs/detail_page_experience.md`**
- Defines the Show Detail page hierarchy and intended experience
- **Why it matters:** The detail page is the hub of user interaction

**`supporting_docs/discovery_quality_bar.md`**
- Quality rubric for AI discovery features
- Note: Golden set intentionally unpopulated in v1
- **Why it matters:** Defines what "good" looks like for recommendations

**`supporting_docs/technical_docs/storage-schema.md`**
- Technical reference for data persistence
- Implementation-language agnostic schema representation
- **Why it matters:** Direct guidance on data model implementation

---

## Planning Requirements

After reading all documentation, create a comprehensive implementation plan that:

### Addresses Architecture
- How will you structure the Next.js application?
- How will you model data in Supabase (tables, relationships, RLS policies)?
- How will you implement namespace and user isolation per the infra rider?
- How will you handle the AI integration layer?

### Accounts for All Features
The main PRD defines these major features (section 7):
- Collection Home (library view with status sections)
- Search (external catalog integration)
- Ask (AI conversational discovery)
- Alchemy (concept blending discovery)
- Show Detail Page (comprehensive show view with all My Data)
- Person Detail Page
- Settings & Data Export

### Implements All Business Rules
The main PRD defines critical business rules (section 5):
- Collection membership and saving triggers
- Default values when saving
- Removal semantics and confirmations
- Data timestamps and merge conflict resolution
- AI data persistence rules

### Follows Cross-Cutting Principles
Section 8 of the main PRD defines non-negotiable principles:
- User's version takes precedence everywhere
- Discovery must be actionable (real shows, not hallucinations)
- Taste-aware AI using library context
- Spoiler-safe by default
- Backend is source of truth (clients can cache but must not depend on local storage for correctness)

### Meets Infrastructure Requirements
From the infra rider:
- Provide `.env.example` with all required variables
- One-command developer experience (`npm run dev`, `npm test`, etc.)
- Repeatable schema definition (migrations)
- Namespace isolation for build/test runs
- User identity on all user-owned records
- Destructive testing without global teardown

---

## Key Considerations for Success

1. **Read everything first.** Don't start planning until you've read every document. Context from supporting docs will change how you interpret the main PRD.

2. **The AI personality matters.** A technically correct build with a generic AI voice misses the point. The AI should feel like a "fun, chatty TV/movie nerd friend."

3. **Concepts are not genres.** The concept system is specific about what makes a good concept ("hopeful absurdity") vs a bad one ("good characters"). This specificity is what makes Alchemy work.

4. **User data continuity is sacred.** The system must preserve user libraries across updates. Users should never lose their collection.

5. **The infra rider is not optional.** Namespace isolation, user identity on all records, and the environment variable interface are hard requirements.

6. **Platform agnostic thinking.** While this build uses Next.js + Supabase, the PRD is designed to be rebuilt on other stacks. Don't make assumptions that lock out future portability unnecessarily.

---

## Summary: Your Workflow

```
1. READ all documents in this folder thoroughly
   ├── showbiz_prd.md (primary)
   ├── showbiz_infra_rider_prd.md (infrastructure)
   └── supporting_docs/* (all supporting documents)

2. UNDERSTAND the relationships between documents
   ├── How does the concept system relate to Alchemy?
   ├── How does the AI voice spec affect Ask and Scoop?
   └── How do the data rules in the PRD map to the storage schema?

3. PLAN your implementation
   ├── Data model and schema design
   ├── API and backend architecture
   ├── Frontend component structure
   ├── AI integration approach
   └── Testing and isolation strategy

4. BUILD the system according to your plan
   └── Implement incrementally, validating against the PRD
```

---

## Begin

Read `showbiz_prd.md` now.
