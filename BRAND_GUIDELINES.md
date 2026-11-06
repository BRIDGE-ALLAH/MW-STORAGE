# MW-STORAGE Brand Guidelines

> **Preserve What Matters. Keep Data Within Reach.**

This document translates the MW-STORAGE brand blueprint into practical rules for repository contributors, maintainers, designers, and anyone publishing project material.

## Brand foundation

- **Project:** MW-STORAGE
- **Category:** Object-storage infrastructure
- **Technical foundation:** RustFS
- **Promise:** Communicate integrity, resilience, control, and continuity without claiming guarantees the implementation cannot prove.
- **Personality:** Calm, precise, transparent, dependable, open, and human.

## Message hierarchy

1. **Primary tagline:** Preserve What Matters. Keep Data Within Reach.
2. **Supporting line:** Reliable object storage. Verifiable integrity. Responsible stewardship of digital information.
3. **Short description:** MW-STORAGE is a RustFS-based object-storage project focused on integrity, resilience, interoperability, and responsible data stewardship.
4. **Proof principle:** Every technical claim must be traceable to implementation, documentation, a reproducible test, or an explicit upstream capability statement.

## Color tokens

| Token | Hex | Intended use |
|---|---|---|
| Midnight | `#071323` | Primary dark background |
| Deep Navy | `#0C2037` | Secondary surface |
| Graphite | `#101827` | Neutral dark surface |
| Warm Gold | `#F4B72F` | Primary accent; use sparingly |
| Pale Gold | `#FFE69A` | Highlight accent |
| Silver | `#F3F6FA` | Primary light text / mark |
| Steel Blue | `#AFC1D4` | Secondary text |
| Network Blue | `#2D8DD2` | Diagram and link accent |

Gold is an accent, not a body-text color on white. Maintain WCAG AA contrast for text and controls; verify combinations rather than assuming palette pairs are accessible.

## Typography

- Preferred: Inter.
- Fallback: system-ui, -apple-system, Segoe UI, Arial, sans-serif.
- Use bold, compact headlines and highly readable body text.
- Avoid ultra-light weights, decorative scripts, and long all-caps paragraphs.
- In SVGs, include generic sans-serif fallbacks.

## Logo system

Primary asset: [assets/brand/mw-storage-logo.svg](assets/brand/mw-storage-logo.svg).

- Preserve aspect ratio and clear space equal to at least the height of the “M” around the mark.
- Do not skew, stretch, rotate, outline, add drop shadows, or change the mark's colors.
- Prefer dark backgrounds; on light backgrounds, use a suitable approved light-surface variant before publishing.
- Do not isolate the mountain/horizon mark in a way that makes it resemble an unrelated certification or security seal.
- Never place the logo beside a third-party mark in a way that implies endorsement.

## Graphic language

Use restrained horizon lines, network nodes, layered storage forms, and data-vault geometry. Diagrams must represent actual architecture and data flows. Do not use shields, padlocks, or glowing effects as implied proof of security.

## Voice and writing

**Do:** be factual, concise, technically specific, respectful, and transparent about trade-offs.

**Prefer:** “supports”, “is designed to”, “for supported operations”, “verify your deployment”, “tested with”.

**Avoid:** “unbreakable”, “zero risk”, “100% secure”, “permanent”, “infinite”, blanket compliance claims, or unqualified “fully S3 compatible”.

Distinguish shipped, preview, experimental, planned, and upstream capabilities. Cite the upstream RustFS implementation and preserve its licensing and trademark notices.

## Asset inventory

| Path | Use |
|---|---|
| [mw-storage-logo.svg](assets/brand/mw-storage-logo.svg) | Primary horizontal logo |
| [mw-storage-hero.svg](assets/brand/mw-storage-hero.svg) | Repository README hero |
| [mw-storage-social-preview.svg](assets/brand/mw-storage-social-preview.svg) | Social preview source artwork (SVG) |
| [README.md](assets/brand/README.md) | Asset inventory and usage notes |
| [BRAND_BLUEPRINT.md](BRAND_BLUEPRINT.md) | Strategy, positioning, narrative, governance |

## Release and community checklist

Before publishing a website, release, announcement, slide deck, or screenshot:

- [ ] Use the approved tagline and current logo asset.
- [ ] Check contrast, legibility, and mobile cropping.
- [ ] Verify all feature and compatibility claims against the current release.
- [ ] Label preview and planned capabilities accurately.
- [ ] Preserve RustFS attribution, license, and trademark boundaries.
- [ ] Avoid implying religious endorsement, certification, or guaranteed durability.
- [ ] Link to documentation and a reproducible source for technical claims.

## GitHub-specific notes

The README hero is committed as SVG. The social-preview artwork is also committed as SVG source at 1280 × 640. GitHub's repository social-preview control requires an accepted raster image and a separate settings action. Upload a PNG/JPG export in repository Settings → Social preview; do not assume the SVG source automatically changes that setting.

The repository description and topic tags are also separate GitHub repository metadata. They should be updated to:

**Description:** RustFS-based object storage focused on integrity, resilience, S3-compatible workflows, and responsible data stewardship.

**Suggested topics:** `object-storage`, `s3-compatible`, `rust`, `rustfs`, `distributed-storage`, `data-integrity`, `self-hosted`.

These metadata suggestions are guidance; this document does not claim those repository settings have been changed.
