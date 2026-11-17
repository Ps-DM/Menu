# AGENT INSTRUCTIONS

## Project overview
This repository is a Vite + React single-page menu application for a Khmer/English restaurant ordering experience. The project is a front-end app that showcases food and beverage items, supports category filtering, product search, cart management, checkout flow, and bilingual locale switching.

## Stack and structure
- React 18 + Vite 5
- Tailwind CSS 3 for styling
- lucide-react for icons
- `src/App.jsx` is the main orchestration layer
- `src/components/` contains UI and modal components
- `src/data/products.js` is the canonical product catalog
- `src/data/categories.js` stores category metadata
- `src/hooks/useLanguage.js` manages locale selection and translations
- `src/hooks/useCart.js` manages cart state
- `src/locales/*.js` contains the Khmer and English string dictionaries
- `src/utils/*.js` contains formatting and fallback helpers
- `src/index.css` holds Tailwind directives and app-wide typography rules

## Product and content conventions
- Treat the menu data as the source of truth. Preserve unique product IDs and category IDs when modifying or adding items.
- Prices are in Khmer Riel. Keep values consistent with the existing numeric format.
- Product objects include `id`, `category`, `price`, `available`, `emoji`, `hue`, `image`, `name`, and `desc` using a `{ km, en }` translation pattern.
- When changing text, prefer the locale dictionaries and `pick()`/`useLanguage()` patterns instead of hard-coded strings.
- Keep UI and product labels bilingual and accessible. Do not introduce English-only labels where Khmer text already exists.
- For category navigation, maintain the language-independent category IDs. Labels come from locale keys in `src/locales/*`.

## UI and behavior expectations
- Keep the application responsive and mobile-first.
- Preserve modals, overlays, cart interactions, toast feedback, and smooth scrolling behavior.
- Do not break keyboard interactions or accessibility semantics when editing components.
- Prefer small, targeted updates over broad rewrites.
- When handling data-driven UI, keep functions pure and rely on existing state hooks instead of introducing new state libraries.
- The app intentionally uses a localized Khmer display by default; respect that default unless a user explicitly requests a change.

## Validation
- This project does not currently include a dedicated unit test suite.
- Always validate changes with a production build: `npm run build`
- Run the smallest relevant command needed for the change; for this repo, the build is the expected completion check.

## Working style
- Follow the existing naming and component patterns already used in the repo.
- Keep imports relative and consistent with the current structure.
- Do not add unrelated dependencies or frameworks.
- Preserve the current architecture unless the user explicitly asks for a larger refactor.
- Be careful with external image URLs; prefer the existing `fallbackImage` logic when image sources may be unreliable.
