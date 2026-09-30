# addyosmani/web-quality-skills

- Upstream: https://github.com/addyosmani/web-quality-skills
- Baseline: `afa8da942115f2961fdbfa80807ea0b232ff6c00`
- License: MIT
- Mode: `pointer`
- Adoption: direct, project-local
- Version family at review: 2.0

## Selected Skills

Use the upstream Skills together as one Web-quality project stack:

- `web-quality-audit`
- `performance`
- `core-web-vitals`
- `accessibility`
- `seo`
- `best-practices`

## Audit summary

The stack is measurement-first and framework-agnostic.

Observed execution surface:

- Skill content is mostly Markdown/reference guidance.
- The repository contains a read-only HTML analyzer shell script under `web-quality-audit/scripts/analyze.sh`.
- No bundled browser server is installed by the Skills themselves.
- Chrome DevTools MCP is optional.
- Some examples mention external/global tools such as Lighthouse or `@axe-core/cli`; these examples are not authorization to modify the global machine environment.

Personal boundary:

- prefer existing project/browser tooling;
- do not globally install Lighthouse, axe, Chrome DevTools MCP, or similar dependencies solely because an example mentions them;
- when no runnable page/live browser exists, label source findings as hypotheses rather than measured failures;
- preserve the distinction between field data, first-party RUM, lab measurement, and static inspection.

## Relationship to personal-data-dashboard

`personal-data-dashboard` controls dense dashboard design and interaction quality.

`web-quality-skills` measures/validates performance, accessibility, SEO, browser best practices, and Core Web Vitals.

They are complementary, not duplicates.

## Update policy

Review Base → New before changing the pinned project-local source.

Compatible upstream changes can remain direct. Fork only if future upstream behavior conflicts with personal installation boundaries or measurement semantics.
