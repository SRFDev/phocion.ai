# phocion.ai -- Project Instructions

You are building the marketing/credibility site for **Phocion**, an AI data-security gateway product. Stack: **Astro, deployed on Netlify**. This is a separate repo and separate session from the core Phocion product (Python/FastAPI/LangGraph/Streamlit) -- don't mix concerns.

## What this site is (and isn't)

A **minimal credibility page**, not a product/funnel site. It needs to exist and be true -- it does not need to sell anything or convert visitors.

**In scope:** hero, problem statement, how-it-works (high-level only), credibility line, honest status. One page or a small handful.

**Explicitly out of scope -- do not build:**
- No email capture, no lead-gen funnel, no gated content.
- No self-serve signup or pricing table.
- No rebuild of srf.dev or its content.

## Content guardrails -- real numbers only, this is load-bearing

- **Latency: no specific number, policy change 2026-08-16.** Use qualitative language only -- "low-latency". Do not state any ms figure (not 42ms, not 34.6ms, not any other value) -- the 42ms figure came from an unexplained, never-root-caused regression, too shaky for a public precise claim. Once there's a stable, reproducible number, the claim becomes a "sub-NNms" ceiling, not a precise decimal. This is public-copy-only; internal engineering tracking still uses the real measured number for its own purposes.
- **Token savings (30-50%) is unmeasured.** Do not state it as a number. Use design-intent language only ("designed to reduce token overhead via semantic caching").
- **"SOC2/HIPAA-oriented," never "SOC2/HIPAA compliant" or "certified."** Phocion is not certified.
- **No fabricated customer logos, testimonials, or traction claims.** Honest status: "in active development, running technical pilots."
- **High-level mechanism only.** Model-agnostic drop-in proxy, real-time PII/PHI masking, semantic injection screening, self-hosted/VPC. Do NOT publish the specific component breakdown (regex vs. DeBERTa split, per-stage latency) or detailed architecture -- competitive exposure.
- **No embedding or linking personalized 1:1 sales-demo videos anywhere on this site** -- those are individual artifacts made for a specific prospect, wrong register for public marketing.

## Design decisions -- already made, don't re-litigate

- **Palette, "Trusted Guardian":** Primary deep midnight blue/slate (~`#040F49`), secondary muted light blue/silver, accent electric cyan (`#00E8FF`) for interactive/active states.
- **Typography:** Space Grotesk (headlines/wordmark), Inter (body text), a monospace face (IBM Plex Mono or JetBrains Mono) for real numbers/metrics only.
- **Wordmark "CIO" highlight:** "PHOCION" contains "CIO" as a literal substring -- set "PHOCION" as real live text in Space Grotesk, with the letters "C", "I", "O" in the cyan accent color and the rest ("PHO", "N") in light silver, via a `<span>` or equivalent. **Implement as real styled HTML text, not a baked-in image** -- keeps it selectable, accessible, and SEO-indexable.
- **Logo/icon:** Φ-based mark (Greek letter Phi, the literal first letter of Phocion's namesake Φωκίων) -- placeholder raster asset lives at `public/phocion_logo_440x440.png` in this repo. Header/hero uses the two-bar version as-is; the favicon uses a simplified single-bar variant (`public/favicon.svg`) for legibility at small sizes. This is a placeholder, not final/vectorized -- don't over-invest polishing around it. **If a required asset is missing, ask -- don't fabricate a substitute in its place.**

## Priority

Real but not urgent as an ongoing background item -- except for the **first build pass, kicked off 2026-08-15**, which is active now. No hard deadlines.

## Sync protocol with the business/vault side

An internal, non-public tracking system holds business-side priorities and decisions for this site. See `VAULT_SYNC.local.md` in this repo root if present (local-only, gitignored, not part of the public repo) for the specific paths and logging convention. If that file isn't present, this file is self-contained enough to build from; just flag to Steven that cross-session sync isn't wired up on this machine.
