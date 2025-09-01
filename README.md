# Thorbis Business OS

**Comprehensive business operating system for Home Services, Restaurants, Auto Services, and Retail industries.**

Dark-first UI. Overlay-free design. NextFaster performance. AI-first architecture.

---

## Architecture Overview

This is a **pnpm monorepo** using **Turbo** for build orchestration and **Next.js 15** with App Router.

### Monorepo Structure
```
apps/                    # Industry-specific applications
├── hs/                 # Home Services (dispatch, work orders, invoices)
├── rest/               # Restaurant (POS, KDS, reservations)  
├── auto/               # Auto Services (repair orders, estimates)
├── ret/                # Retail (POS, inventory, customers)
├── courses/            # Learning management system
├── site/               # Marketing website
└── ai/                 # AI chat interface

packages/               # Shared libraries
├── ui/                 # Design system components
├── design/             # Design tokens, themes, utilities
├── schemas/            # Industry-specific Zod schemas
└── auth/               # Authentication utilities
```

### Deployment Routes
Each app represents a different route on thorbis.com in production:
- `thorbis.com/` - Marketing website (site app)
- `thorbis.com/hs` - Home Services admin panel
- `thorbis.com/rest` - Restaurant admin panel  
- `thorbis.com/auto` - Auto Services admin panel
- `thorbis.com/ret` - Retail admin panel
- `thorbis.com/courses` - Learning platform admin panel
- `lom.thorbis.com` - LOM documentation site (only subdomain)

---

## Development

### Prerequisites
- Node 20+, pnpm 9+
- Docker or Supabase CLI

### Quick Start
```bash
# Install dependencies
pnpm install

# Development (specific apps)
pnpm dev:hs      # Home Services app (port 3001)
pnpm dev:rest    # Restaurant app (port 3011)  
pnpm dev:auto    # Auto Services app (port 3012)
pnpm dev:ret     # Retail app (port 3013)
pnpm dev:site    # Marketing site (port 3000)
pnpm dev:courses # Courses app (port 3007)

# Build and validation
pnpm build              # Build all apps
pnpm lint               # Lint all workspaces
pnpm type-check         # TypeScript validation
pnpm test               # Run all tests
```

---

## Key Features

### Design Philosophy
- **Dark-First UI**: VIP black/white with electric blue accents (#1C8BFF)
- **No Overlays Policy**: Zero dialogs, modals, or popovers - use inline panels, dedicated pages, and tooltips only
- **Per-Industry Apps**: Separate applications for each industry vertical
- **NextFaster Performance**: Sub-300ms navigation, 170KB JS budget, aggressive caching

### Technology Stack
- **Next.js 15** with App Router and Server Components
- **Supabase** for database with Row Level Security (RLS)
- **Tailwind CSS** with custom design system
- **TypeScript** with strict mode enabled
- **Turbo** for monorepo build orchestration
- **AI Integration** via MCP (Model Context Protocol)

### Security & Architecture
- **Multi-tenant by default**: All tables include tenant isolation
- **Row Level Security (RLS)** on everything - no exceptions
- **Industry-separated schemas**: Different artifact types per vertical
- **Audit logging**: Every operation logged with complete context
- **Soft deletes**: Trash/restore pattern for all destructive operations

---

## Contributing

This project follows strict architectural principles:

1. **EVOLVE DON'T DUPLICATE**: Update existing files rather than creating new ones
2. **No Overlays**: Replace dialogs with inline panels, use tooltips for help
3. **Dark-First Design**: Every component optimized for dark theme first
4. **Industry Separation**: No cross-pollination between verticals
5. **Performance First**: Server Components preferred, minimal client-side hydration

---

## License

**Proprietary — © Thorbis. All rights reserved.**
Source available to contributors for development and evaluation.