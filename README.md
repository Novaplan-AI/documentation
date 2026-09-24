# Novaplan AI documentation

Mintlify documentation for Novaplan AI, adapted from the PipesHub documentation repository. The site configuration is in `docs.json`; guide content is in `.mdx` files.

## Local review

With the Mintlify CLI installed, run these commands from this directory:

```sh
mint dev --port 3036
mint validate
```

Use the preview URL printed by the CLI. It may select another port if the requested port is occupied.

## Editing rules

- Use **Novaplan AI**, the supplied Novaplan logo, and the existing brand styles.
- Preserve the Mintlify layout and existing page paths. Keep redirects when retiring published guides.
- Customer access is invitation-based. Do not add platform installation, self-registration, or open-source contribution instructions.
- Existing-workspace support: `support@novaplan.ai`. The website contact form is for sales and demo enquiries.
- Keep working API paths, package names, scopes, environment variables, and third-party product names intact.
- Skip guides that are missing upstream until PipesHub supplies them. Review and rebrand them before adding them here.
- Keep internal audit reports, Enterprise artifacts, credentials, and deferred review material outside this public repository.

## Upstream updates

Compare incoming changes with the upstream PipesHub documentation and apply selected updates. Review each update for product applicability, instructions, links, screenshots, and branding. Do not overwrite Novaplan configuration with upstream defaults. Preserve any upstream license or attribution notices supplied with imported material.

## Publication

Preview and validate the approved changes first. Confirm the repository, deployment branch, and custom domain in Mintlify before publishing. Work on a review branch does not imply approval to publish or merge.
