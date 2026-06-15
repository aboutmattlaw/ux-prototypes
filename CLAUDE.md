# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

React Router v7 application with server-side rendering (SSR), built using TypeScript, Vite, and TailwindCSS v4. Uses React 19 and follows a file-based routing convention.

# Figma MCP Integration & Implementation Rules
- Refer to figma-instructions.md for guidelines for implementing Figma designs


### Core Files
- '/assets/stores' - Merchant and store logos and media
- '/assets/fonts - Use these fonts for all builds


### Core Files
- `rr-rakuten/app/root.tsx` - Root layout with `<html>`, `<head>`, `<body>` structure, global error boundary, and font preloads
- `rr-rakuten/app/routes.ts` - Route configuration defining URL-to-component mappings
- `rr-rakuten/app/routes/` - Route components (page-level components)
- `rr-rakuten/app/components/` - Reusable UI components
- `rr-rakuten/app/utils/` - Utility functions (e.g., `cn.ts` for className merging)
- `rr-rakuten/react-router.config.ts` - SSR configuration (set `ssr: false` to enable SPA mode)
- `rr-rakuten/app/app.css` - Global styles with TailwindCSS imports and theme configuration
- '/assets/stores' - Merchant and store logos and media
- '/assets/fonts - Use these fonts for all builds


### Build Output
Production build creates:
- `build/client/` - Static assets (JS, CSS, images)
- `build/server/` - Server bundle (index.js)

### Content
- Refer to /assets/stores/ for all store or merchant logos, media, and data


