---
name: artifact
description: Create a self-contained HTML artifact, host it on a local server, and return its URL.
---

# Artifact

Triggered when the user invokes `/artifact` with a description of what to build.

## Behavior

1. If the request lacks a topic or content, ask one short question before building.
2. Create one self-contained HTML file at `artifacts/<slug>.html` (`<slug>` is a short lowercase hyphenated name). Inline all CSS and JS; avoid external dependencies.
3. Ensure every artifact page shows a link to the artifact list near the top (e.g. `<a href="./index.html">Artifacts</a>`).
4. Maintain `artifacts/index.html`: create it if missing, then add or update the entry for the new artifact (title, link, creation date). Keep existing entries.
5. Serve the `artifacts/` directory from a detached local static server on a free port (never disturb existing user processes; reuse the skill's running server when present), verify reachability with a bounded HTTP check, and keep it running after handoff.
6. Report the created file path, the index path, and the concrete `http://localhost:<port>/...` URLs for the new artifact and the index, with an instruction to open them in a browser.
