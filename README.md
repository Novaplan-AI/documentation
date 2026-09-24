# Novaplan documentation

German customer guides and English technical reference for docs.novaplan.ai, maintained as a fork of [pipeshub-ai/documentation](https://github.com/pipeshub-ai/documentation).

See [NOVAPLAN-LAUNCH.md](NOVAPLAN-LAUNCH.md) for the launch checklist, translation scope, known application-link gaps, and upstream maintenance workflow.

## Preview and validate

Use the current Mintlify CLI (`mint`, not the legacy `mintlify` package):

```sh
npm install -g mint
mint validate
mint dev --port 3035
```

Mintlify reads `docs.json` from the repository root. The twelve German guides keep their original page paths. Technical identifiers and installer URLs must remain compatible with the application.

## Publishing

Connect this repository to the company Mintlify account. Review the Novaplan branch before merging to the connected production branch. A push to that branch can trigger deployment automatically.

The custom domain is configured in the Mintlify dashboard and your DNS provider, not by changing `docs.json` alone.
