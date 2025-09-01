# Thorbis Business OS

**Comprehensive business operating system for Home Services, Restaurants, Auto Services, and Retail industries.**

Dark-first UI. Overlay-free design. NextFaster performance. AI-first architecture.

---

## Repository Status

✅ **Optimized Repository**: Clean monorepo with comprehensive .gitignore patterns
✅ **Git LFS Enabled**: Large binary files tracked with Git LFS
✅ **Performance Optimized**: Git fsmonitor and untracked cache enabled
✅ **Build System Ready**: Turbo monorepo with industry-separated apps

**Total Size**: 1.3GB → Optimized repository structure
**Files Tracked**: 11,987 objects with delta compression
**LFS Objects**: Binary files (images, binaries) handled via Git LFS

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
├── ai/                 # AI chat interface
├── books/              # Accounting and bookkeeping
├── payroll/            # Payroll management
├── investigations/     # Investigation tools
└── lom/                # List of Manifests documentation

packages/               # Shared libraries
├── ui/                 # Design system components (overlay-free)
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
- `thorbis.com/books` - Accounting and bookkeeping
- `thorbis.com/payroll` - Payroll management
- `lom.thorbis.com` - LOM documentation site (only subdomain)

---

## Development

### Prerequisites
- Node 20+, pnpm 9+
- Docker or Supabase CLI
- Git LFS installed (`brew install git-lfs`)

### Quick Start
```bash
# Install dependencies
pnpm install

# Development (specific apps)
pnpm dev:hs           # Home Services app (port 3001)
pnpm dev:rest         # Restaurant app (port 3011)  
pnpm dev:auto         # Auto Services app (port 3012)
pnpm dev:ret          # Retail app (port 3013)
pnpm dev:site         # Marketing site (port 3000)
pnpm dev:courses      # Courses app (port 3007)
pnpm dev:books        # Accounting app
pnpm dev:payroll      # Payroll app
pnpm dev:investigations # Investigation tools
pnpm dev:ai           # AI chat interface

# Build and validation
pnpm build              # Build all apps
pnpm build:apps         # Build only apps/*
pnpm build:packages     # Build only packages/*
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
- **AI-First Operations**: Every system operation monitored and optimized by AI agents

### Technology Stack
- **Next.js 15** with App Router and Server Components
- **Supabase** for database with Row Level Security (RLS)
- **Tailwind CSS** with custom design system
- **TypeScript** with strict mode enabled
- **Turbo** for monorepo build orchestration
- **AI Integration** via MCP (Model Context Protocol)
- **Git LFS** for large binary file management

### Security & Architecture
- **Multi-tenant by default**: All tables include tenant isolation
- **Row Level Security (RLS)** on everything - no exceptions
- **Industry-separated schemas**: Different artifact types per vertical
- **Audit logging**: Every operation logged with complete context
- **Soft deletes**: Trash/restore pattern for all destructive operations
- **AI Governance**: AI oversight and control systems for all operations

### Performance Optimizations
- **Repository Size**: Optimized from 10GB+ to 1.3GB
- **Git Performance**: fsmonitor and untracked cache enabled
- **Build System**: Turbo with parallel builds and smart caching
- **NextFaster Doctrine**: Instant navigation with zero loading spinners

---

## Contributing

This project follows strict architectural principles:

1. **EVOLVE DON'T DUPLICATE**: Update existing files rather than creating new ones
2. **No Overlays**: Replace dialogs with inline panels, use tooltips for help
3. **Dark-First Design**: Every component optimized for dark theme first
4. **Industry Separation**: No cross-pollination between verticals
5. **Performance First**: Server Components preferred, minimal client-side hydration
6. **Comprehensive Documentation**: Every file must have detailed header documentation

### File Standards
- **MANDATORY FILE DOCUMENTATION**: Every file must have elaborate top comment explaining purpose, dependencies, and integration
- **TODO.md Files**: Every directory must contain todo.md tracking incomplete features
- **Responsive Design**: All components work on any screen size
- **Accessibility**: WCAG 2.1 AA compliance required

---

## Project Status

### Recently Completed
- ✅ Repository optimization and cleanup (removed 1.2M+ deleted lines)
- ✅ Enhanced .gitignore with comprehensive monorepo patterns  
- ✅ Git LFS setup for large binary files
- ✅ Git performance optimizations (fsmonitor, untracked cache)
- ✅ Comprehensive file documentation standards
- ✅ AI-first architecture implementation

### Next Phase
- 🔄 Complete GitHub repository upload
- 📋 Deploy industry-specific applications
- 🤖 AI governance system activation
- 🔐 Advanced security implementations

---

## License

**Proprietary — © Thorbis. All rights reserved.**
Source available to contributors for development and evaluation.

---

## Repository Optimization Notes

This repository has been optimized for large-scale monorepo development:

- **Before**: 10GB+ with extensive cache files and build outputs
- **After**: 1.3GB optimized repository with Git LFS for binaries
- **Improvements**: 
  - Comprehensive .gitignore patterns for monorepo
  - Git LFS tracking for *.png, *.jpg, *.dylib, *.dll, *.node, *.wasm, *.pack
  - Git performance optimizations enabled
  - Clean commit history with 11,987 optimized objects

For development questions or contributions, see CLAUDE.md for comprehensive guidance.