# Generative Pages (GenPages) - Manual Code-First Setup

This project lets you develop **Generative Pages** for Power Apps Model-Driven Apps using **PAC CLI** without relying on AI plugins.

## Project Structure
```
my-genpage/
├── package.json
├── tsconfig.json
├── page.tsx                 # Main page code (edit this)
├── RuntimeTypes.ts          # Generated type-safe Dataverse types
├── README.md
└── .eslintrc.json / .prettierrc (optional)
```

## 1. Initial Setup

```bash
# 1. Install dependencies (includes Fluent UI v9 + D3)
npm install

# 2. Generate type-safe Dataverse types
pac model genpage generate-types \
  --data-sources "account,contact,opportunity" \
  -o RuntimeTypes.ts
```

## 2. Bootstrap a New Page (One-time)

1. In **make.powerapps.com**, open your model-driven app.
2. Go to **Add page > Describe a page** and create a simple starter page.
3. Publish the app.
4. Download the generated code:

```bash
pac model genpage download \
  --app-id "Your App Name or GUID" \
  --page-id "<page-guid>" \
  -o .
```

## 3. Available npm Scripts

| Script              | Command                          | Description                              |
|---------------------|----------------------------------|------------------------------------------|
| `typecheck`         | `npm run typecheck`              | Type-check without emitting files        |
| `build`             | `npm run build`                  | Compile TypeScript                       |
| `transpile`         | `npm run transpile`              | Transpile page.tsx using PAC CLI         |
| `lint`              | `npm run lint`                   | Lint TypeScript files                    |
| `lint:fix`          | `npm run lint:fix`               | Auto-fix lint issues                     |
| `format`            | `npm run format`                 | Format code with Prettier                |

## 4. PAC CLI Commands for GenPages

### Core Commands

| Command | Purpose | Example |
|---------|---------|---------|
| `pac model genpage list` | List all generated pages in an app | `pac model genpage list --app-id "Contoso Sales"` |
| `pac model genpage generate-types` | Create `RuntimeTypes.ts` (type-safe Dataverse) | `pac model genpage generate-types --data-sources "account,contact" -o RuntimeTypes.ts` |
| `pac model genpage download` | Download existing page source code | `pac model genpage download --app-id "Contoso" --page-id "guid-here" -o .` |
| `pac model genpage upload` | **Deploy / Update** your page | See examples below |
| `pac model genpage transpile` | Transpile `.tsx` → `.js` locally | `pac model genpage transpile --code-file page.tsx` |

### Upload Examples

**Create new page:**
```bash
pac model genpage upload \
  --app-id "Contoso Sales Hub" \
  --code-file ./page.tsx \
  --name "Account Dashboard" \
  --data-sources "account,contact" \
  --prompt "Dashboard showing top accounts with revenue chart" \
  --add-to-sitemap
```

**Update existing page:**
```bash
pac model genpage upload \
  --app-id "Contoso Sales Hub" \
  --page-id "e5f6a7b8-..." \
  --code-file ./page.tsx \
  --data-sources "account,contact" \
  --prompt "Added filters and improved chart"
```

## 5. Typical Development Workflow

1. `npm install`
2. Generate types: `pac model genpage generate-types ...`
3. Download template (first time only)
4. Edit `page.tsx` in VS Code (full IntelliSense)
5. Type check: `npm run typecheck`
6. Upload changes: `pac model genpage upload ...`
7. Test inside your model-driven app
8. Repeat steps 4–7

## 6. Supported Libraries & Best Practices

**Recommended / Supported in GenPages:**

| Library | Purpose | Recommended? | Notes |
|---------|---------|--------------|-------|
| React 17 + TypeScript | Core framework | Yes (provided by host) | Use types locally |
| `@fluentui/react-components` | Fluent UI v9 components | Yes | Primary UI library |
| `@fluentui/react-datepicker-compat` | Date picker | Yes | For date fields |
| `@fluentui/react-timepicker-compat` | Time picker | Yes | For time fields |
| `d3` | Charts & data visualization | Yes | Approved for charts |
| `dataApi` | Type-safe Dataverse queries | Yes (via `RuntimeTypes.ts`) | Use `dataApi.queryTable()` |

**Important Rules:**
- Keep it **single file** (`page.tsx`) when possible.
- Prefer **Fluent UI v9** components.
- Use `RuntimeTypes.ts` for all Dataverse queries (type safety).
- Do **not** install heavy external UI libraries (MUI, AntD, etc.) for runtime — they may not work after deployment.
- The host provides React and Fluent UI at runtime. Your `package.json` is mainly for **local development** and type checking.

## 7. Useful Files

- `page.tsx` — Your main page component
- `RuntimeTypes.ts` — Strongly typed Dataverse entities & columns
- `genpage.d.ts` (auto-generated on first download) — Ambient types for `dataApi`, `pageInput`, etc.

## 8. Quick Reference

```bash
# Full daily workflow example
npm run typecheck
pac model genpage generate-types --data-sources "account,contact" -o RuntimeTypes.ts
pac model genpage upload --app-id "MyApp" --page-id "xxx" --code-file page.tsx --data-sources "account,contact"
```

For the latest official documentation, always refer to:
- https://learn.microsoft.com/en-us/power-apps/maker/model-driven-apps/generative-page-external-tools
- `pac model genpage --help`

Happy coding!
```

Now I have both files created in `/home/workdir/artifacts/genpage-manual/`.
