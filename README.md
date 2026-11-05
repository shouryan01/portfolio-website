# portfolio-website

Source code for [shouryannikam.com](https://shouryannikam.com).

## Architecture & Toolchain

- **Framework:** Next.js 16 (App Router) with React 19 & Turbopack
- **Styling:** Tailwind CSS v4 with custom CSS variable design tokens
- **Typography:** Editorial serif (`Newsreader`), clean sans (`Plus Jakarta Sans`), monospace (`JetBrains Mono`)
- **Themes:** Light & Dark mode support via `next-themes` with persistent class switching
- **Toolchain:** Rust-powered `oxlint` and `oxfmt`

## Scripts

```bash
# Start development server
pnpm dev

# Build for production
pnpm build

# Lint code with oxlint
pnpm lint
pnpm lint:fix

# Format code with oxfmt
pnpm format
pnpm format:check
```
