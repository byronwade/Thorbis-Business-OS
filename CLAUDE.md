# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

> **Last Updated**: 2025-01-31  
> **Version**: 3.0.0  
> **Status**: Production Ready

## Common Development Commands

### Monorepo Structure
This is a **pnpm monorepo** using **Turbo** for build orchestration and **Next.js 15** with App Router.

**Important**: Each app represents a different route on thorbis.com in production:
- `thorbis.com/hs` - Home Services admin panel
- `thorbis.com/rest` - Restaurant admin panel  
- `thorbis.com/auto` - Auto Services admin panel
- `thorbis.com/ret` - Retail admin panel
- `thorbis.com/courses` - Learning platform admin panel
- `thorbis.com/payroll` - Payroll admin panel
- `lom.thorbis.com` - LOM (List of Manifests) documentation site (only subdomain)
- `thorbis.com` - Main marketing website (site app)

```bash
# Install dependencies
pnpm install

# Development (specific apps) - each runs locally but deploys to thorbis.com routes
pnpm dev:hs      # Home Services app (port 3001) -> thorbis.com/hs
pnpm dev:rest    # Restaurant app (port 3011) -> thorbis.com/rest  
pnpm dev:auto    # Auto Services app (port 3012) -> thorbis.com/auto
pnpm dev:ret     # Retail app (port 3013) -> thorbis.com/ret
pnpm dev:site    # Marketing site (port 3000) -> thorbis.com
pnpm dev:courses # Courses/Learning app (port 3007) -> thorbis.com/courses
pnpm dev:payroll # Payroll app -> thorbis.com/payroll

# Build and validation
pnpm build              # Build all apps
pnpm build:apps         # Build only apps/* 
pnpm build:packages     # Build only packages/*
pnpm lint               # Lint all workspaces
pnpm type-check         # TypeScript validation
pnpm test               # Run all tests

# Database operations (Supabase)
pnpm db:generate        # Generate types from schema
pnpm db:push           # Push schema changes
pnpm db:seed           # Seed with demo data
```

## High-Level Architecture

### Core Philosophy: "Dark-First, Overlay-Free, Industry-Separated, AI-Governed, Blockchain-Verified"
- **Dark-first UI**: VIP black/white with electric blue accents (#1C8BFF)
- **No overlays**: No dialogs, modals, or popovers - use inline panels, dedicated pages, and tooltips only
- **Per-industry apps**: Separate applications for Home Services (`/hs/`), Restaurants (`/rest/`), Auto (`/auto/`), and Retail (`/ret/`)
- **NextFaster performance**: Sub-300ms navigation, 170KB JS budget, aggressive caching
- **Proof over opinions**: Artifact-anchored trust signals, not star ratings
- **AI-First Operations**: Every system operation monitored, governed, and optimized by AI agents
- **Blockchain Transparency**: All critical operations cryptographically verified and immutably recorded

### Monorepo Structure
```
apps/                    # Industry-specific applications
├── hs/                 # Home Services (dispatch, work orders, invoices)
├── rest/               # Restaurant (POS, KDS, reservations)  
├── auto/               # Auto Services (repair orders, estimates)
├── ret/                # Retail (POS, inventory, customers)
├── courses/            # Learning management system
├── site/               # Marketing website
├── trust/              # Public trust microsites (badges, metrics)
└── admin/              # Internal admin tools

packages/               # Shared libraries
├── ui/                 # Odixe design system components (overlay-free variants)
├── design/             # Odixe design tokens, themes, utilities
├── schemas/            # Industry-specific Zod schemas
├── auth/               # Authentication utilities  
├── agent/              # MCP tools and AI integrations
├── billing/            # Stripe integration and usage meters
├── ai-governance/      # AI oversight and control systems
└── blockchain/         # Blockchain verification and audit trail
```

### Database Architecture (Supabase)
- **Multi-tenant by default**: All tables include tenant isolation
- **Row Level Security (RLS)** on everything - no exceptions
- **Industry-separated schemas**: Different artifact types per vertical
- **Audit logging**: Every AI tool call and data mutation logged
- **Soft deletes**: Trash/restore pattern for all destructive operations
- **AI-Monitored Operations**: All database operations supervised by AI governance layer
- **Blockchain Audit Trail**: Every database transaction cryptographically signed and recorded

## Development Guidelines

### File Organization
- **Industry separation**: No cross-pollination between verticals
- **Component reuse**: Shared components in `packages/ui/`
- **Type safety**: Strict TypeScript, industry-specific schemas
- **Route organization**: App Router with proper layout nesting

### Performance Requirements  
- **Core Web Vitals**: LCP ≤ 1.8s, CLS ≤ 0.1, FID ≤ 100ms
- **Bundle analysis**: Monitor JS payload per route
- **Image optimization**: AVIF/WebP with exact sizing
- **Font optimization**: Max 2 font families, subset loading

### Security Requirements
- **Supabase RLS everywhere**: No direct table access without policies
- **Input validation**: Zod schemas for all API boundaries  
- **PII protection**: Redaction in logs, short-lived signed URLs
- **CSRF protection**: Built-in with App Router server actions

## Critical Patterns to Follow

### Error Handling
- **Graceful degradation**: Always show something, even when APIs fail
- **User-friendly messages**: Abstract technical errors for end users
- **Monitoring integration**: Structured logging for observability
- **Offline support**: Service worker with background sync

### Data Loading
- **Optimistic UI**: Show immediate feedback for user actions  
- **Stale-while-revalidate**: Show cached data while fetching fresh
- **Progressive enhancement**: Server-first with client enhancements
- **Error boundaries**: Catch and handle React component failures

### Security Considerations
- **Principle of least privilege**: Minimum necessary permissions
- **Input sanitization**: Prevent injection attacks
- **Rate limiting**: Prevent abuse and DoS attacks  
- **Secrets management**: No hardcoded keys, use environment variables

## Performance Optimization Memories
- Make sure to always follow nextfaster server first approach no loading pages and only stateful loading, with image prefetching on link hovers

## Code Architecture Memories
- Make sure all apps use the same header
- Make sure we're using the shared components and if one doesn't exist for what we need then we create a new shared component that we can use in all apps

## Design Memories
- Make sure all pages use neutral colors not grey colors

## Responsiveness Memories
- Make sure everythign we make is always fully responsive on any screen