# Ship verbs

This file defines `launch` and `distribute`.

## launch

Purpose: make the product safely usable by real users.

Launch is broader than deployment, but should still match product size.

### Check only what applies

- production build works
- required environment/config exists
- main user flow works
- domain/URL works when relevant
- mobile/basic responsive path works for web products
- favicon/app metadata is not obviously missing
- basic SEO/share metadata for public web products
- analytics only if it serves a current feedback need
- no exposed secrets
- user-facing setup/instructions are sufficient
- known blockers are explicit

Do not add an enterprise release process to a small personal product.

If launch requires code/config changes and the user asked to launch, make them when capabilities allow.

Never claim a deployment succeeded unless it was actually verified.

## distribute

Purpose: find the smallest realistic path to first users and useful feedback.

### Flow

1. Identify the narrowest audience that would care.
2. Identify where those people already are.
3. Choose one product story or demo angle.
4. Recommend 1-3 channels, not every platform.
5. Define the smallest feedback loop.
6. Reuse the build process as content when natural.

### Output

Prefer:

- **Who**
- **Message**
- **Where**
- **Demo**
- **Feedback signal**

Do not default to a 30-day marketing calendar.

Distribution advice should match the product's current maturity. A tiny new tool usually needs a few relevant users, not a growth funnel.
