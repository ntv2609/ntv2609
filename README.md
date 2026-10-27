<div align="center"><h1>Vinh Nguyen — Portfolio & Engineering Showcase</h1><p>A fast, accessible developer portfolio and technical showcase built with Next.js, TypeScript, and Tailwind CSS.</p><p><a href="https://vinh-nguyen-portfolio.vercel.app"><strong>Live Production</strong></a> ·<a href="https://www.linkedin.com/in/ntv2609/"><strong>LinkedIn</strong></a> ·<a href="mailto:ntv2609@gmail.com"><strong>Contact</strong></a></p><p><img src="https://img.shields.io/badge/Next.js-15-000000?style=flat-square&logo=next.js&logoColor=white" alt="Next.js" /><img src="https://img.shields.io/badge/React-19-111827?style=flat-square&logo=react&logoColor=61DAFB" alt="React" /><img src="https://img.shields.io/badge/TypeScript-5.x-111827?style=flat-square&logo=typescript&logoColor=3178C6" alt="TypeScript" /><img src="https://img.shields.io/badge/Tailwind_CSS-3.4-111827?style=flat-square&logo=tailwindcss&logoColor=38B2AC" alt="Tailwind CSS" /><img src="https://img.shields.io/badge/Deployment-Vercel-000000?style=flat-square&logo=vercel&logoColor=white" alt="Vercel" /></p></div>Overview & Visual Preview<div align="center"><!-- Replace the placeholder URL below with your actual screenshot or demo GIF --><!-- Recommended aspect ratio: 16:9 (e.g., 1600x900px) in WebP or optimized PNG/GIF --><a href="https://vinh-nguyen-portfolio.vercel.app"><img src="<img width="950" height="497" alt="image" src="https://github.com/user-attachments/assets/3d78d100-8cb0-42e9-9179-7d44691d81e3" />
" alt="Vinh Nguyen Portfolio Preview" width="100%" /></a><p><sub><em>Figure 1: Application interface and interactive layout system running on <a href="https://vinh-nguyen-portfolio.vercel.app">vinh-nguyen-portfolio.vercel.app</a>. Replace <code>public/preview.webp</code> or the image URL above with a real screen capture.</em></sub></p></div>[!NOTE]Using this file as a GitHub Profile README (ntv2609/ntv2609)?See the ready-to-use minimalist profile block in the GitHub Profile Mode section at the bottom of this document.Key FeaturesServer-First Rendering Architecture: Built on the Next.js App Router with React Server Components (RSC) to ship minimal client-side JavaScript and achieve sub-second First Contentful Paint (FCP).Strict End-to-End Type Safety: Enforced via TypeScript with strict compiler flags (strict: true, noUncheckedIndexedAccess), eliminating runtime type regressions across components and data layers.Deterministic Design System: Engineered with Tailwind CSS design tokens, fluid typography scales, and hardware-accelerated CSS transitions for consistent 60fps interaction across viewports.Zero-Runtime Content Pipeline: Static generation (SSG) with Incremental Static Regeneration (ISR) for project case studies and engineering notes, ensuring instant edge delivery via Vercel CDN.Semantic Accessibility & SEO: Full WAI-ARIA compliance, keyboard-navigable interactive primitives, dynamic OpenGraph image generation, and automated XML sitemap indexing.Tech StackLayerTechnologyPurposeFrameworkNext.js (App Router)Hybrid SSR/SSG routing, Server Components, and Edge API routesLanguageTypeScript 5.xStatic type checking and interface contractsUI & StylingReact 19, Tailwind CSSComponent architecture, utility-first styling, and dark-mode tokensTooling & DXESLint, Prettier, GitStatic code analysis, formatting, and version controlInfrastructureVercel Edge NetworkCI/CD preview deployments, edge caching, and Web AnalyticsArchitecture & Request LifecycleThe application separates static content compilation from interactive client islands, keeping the JavaScript bundle lean while supporting rich UI interactions.┌─────────────────────────────────────────────────────────────────────────┐
│                         Client Browser / Viewport                       │
└───────────────────┬─────────────────────────────────┬───────────────────┘
                    │ HTTPS Request                   │ Hydrate Interactive
                    ▼                                 │ Islands Only
┌───────────────────────────────────────┐             │
│          Vercel Edge Network          │             │
│   (Global CDN · Brotli · TLS 1.3)     │             │
└───────────────────┬───────────────────┘             │
                    │ Cache Miss / Revalidate         │
                    ▼                                 │
┌─────────────────────────────────────────────────────┴───────────────────┐
│                         Next.js App Router Runtime                      │
│                                                                         │
│  ┌─────────────────────────────────┐  ┌──────────────────────────────┐  │
│  │   React Server Components (RSC) │  │    Client Components ('use   │  │
│  │  • Layouts & Route Shells       │  │    client')                  │  │
│  │  • Project Case Study MDX/Data  │  │  • Command Palette / Filter  │  │
│  │  • Dynamic Metadata & OpenGraph │  │  • Theme & Motion Controllers│  │
│  └────────────────┬────────────────┘  └──────────────────────────────┘  │
└───────────────────┼─────────────────────────────────────────────────────┘
                    │ Build-Time / ISR Validation
                    ▼
┌─────────────────────────────────────────────────────────────────────────┐
│                     Typed Content & Asset Layer                         │
│             src/data/*.ts  ·  src/content/*.mdx  ·  public/*            │
└─────────────────────────────────────────────────────────────────────────┘
Directory Structure.
├── public/                 # Static assets, fonts, OpenGraph images
├── src/
│   ├── app/                # Next.js App Router pages, layouts, and metadata
│   ├── components/
│   │   ├── ui/             # Low-level reusable design system primitives
│   │   └── sections/       # Page-level feature modules (Hero, Projects, Contact)
│   ├── content/            # Project case studies and structured portfolio data
│   ├── lib/                # Utility functions, class mergers, and constants
│   └── types/              # Shared TypeScript interfaces and domain models
├── next.config.mjs         # Next.js compiler and headers configuration
├── tailwind.config.ts      # Design tokens, color palette, and typography scale
└── tsconfig.json           # TypeScript strict compiler configuration
Getting StartedPrerequisitesNode.js: >= 20.0.0 (LTS recommended)Package Manager: pnpm (>= 9.0.0), npm, or bunInstallation# 1. Clone the repository
git clone https://github.com/ntv2609/vinh-nguyen-portfolio.git
cd vinh-nguyen-portfolio

# 2. Install dependencies
pnpm install

# 3. Bootstrap local environment variables
cp .env.example .env.local
Local Development & Production Build# Start the local development server with Fast Refresh (http://localhost:3000)
pnpm dev

# Run static type checking and linter verification
pnpm typecheck && pnpm lint

# Compile and verify an optimized production build locally
pnpm build && pnpm start
Configuration & Environment VariablesCreate a .env.local file in the root directory. All client-exposed variables must be prefixed with NEXT_PUBLIC_.VariableTypeRequiredDefaultDescriptionNEXT_PUBLIC_SITE_URLstringYeshttp://localhost:3000Canonical base URL used for OpenGraph metadata and sitemapsNEXT_PUBLIC_CONTACT_EMAILstringNontv2609@gmail.comPublic contact address rendered in the footer and command menuRESEND_API_KEYstringNo—Server-side API key for transactional contact form emailsNEXT_PUBLIC_ENABLE_ANALYTICSbooleanNofalseToggles Vercel Web Analytics and Speed Insights in productionGitHub Profile Mode (Optional)<details><summary><strong>Click to expand: Minimalist GitHub Profile README (for <code>ntv2609/ntv2609</code>)</strong></summary><br />If you are using this file for your personal GitHub Profile repository (ntv2609/ntv2609) rather than a single project repository, you can replace the sections above with this stripped-down, zero-slop engineering profile block:### Vinh Nguyen

Frontend Engineer focused on high-performance web applications, design systems, and React/Next.js architecture.

- **Focus**: React Server Components, TypeScript type-level design, web performance (Core Web Vitals), and accessible UI primitives.
- **Stack**: TypeScript, React, Next.js, Tailwind CSS, C++, Git, Vercel.
- **Links**: [vinh-nguyen-portfolio.vercel.app](https://vinh-nguyen-portfolio.vercel.app) · [LinkedIn (in/ntv2609)](https://www.linkedin.com/in/ntv2609/) · [ntv2609@gmail.com](mailto:ntv2609@gmail.com)

| Domain | Technologies |
| :--- | :--- |
| **Languages** | TypeScript, JavaScript (ES2024), C++, HTML5, CSS3 |
| **Frontend & UI** | React, Next.js (App Router), Tailwind CSS, CSS Modules, Figma |
| **Tooling & Infra** | Git, GitHub Actions, Vercel, ESLint, Vite, VS Code |
</details>LicenseReleased under the MIT License. Built and maintained by Vinh Nguyen.
