# Implementation notes / next steps

This is a working visual and structural starter, not yet a production-complete publication.

Before public launch:

1. **Full-text RSS:** The RSS endpoint now renders Markdown to HTML with `marked` and sanitizes the output before embedding it. Test image URL rewriting under both deployment base paths.
2. **Atom feed:** Verify feed self URL and canonical IDs for both subpath and subdomain deployments.
3. **Math:** `remark-math` and `rehype-katex` are wired into Astro's Markdown pipeline; verify equation output in production.
4. **Footnotes:** Add a footnote plugin if needed; GFM covers tables, task lists, strikethrough and autolinks.
5. **Image paths:** Test local images under both `/writings` and `/` base paths. Consider a custom Markdown image transformer to prefix `BASE_URL` for `/media/...` paths.
6. **Search:** Add a small generated JSON index and client-side search only if the archive grows enough to need it.
7. **Mermaid RSS:** Include static SVG alternatives for diagrams because feed readers don't run Mermaid JavaScript.
8. **Validation:** Run `npm install`, `npm run check`, and `npm run build`; fix any version-specific Astro API differences before deployment.

## Deployment choice

For a path under an existing site (`geetansh.tech/writings`), the simplest deployment is a separate Vercel project with `PUBLIC_BASE_PATH=/writings` only if the domain routing is configured to serve that project under the subpath. Vercel does not automatically mount a second project at a subpath; use a rewrite/reverse proxy in the main site, or deploy the publication as part of the existing Astro/Next application.

For a dedicated subdomain (`writings.geetansh.tech`), a separate Vercel project is straightforward and should use `PUBLIC_BASE_PATH=/`.
