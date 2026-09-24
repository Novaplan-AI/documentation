# Novaplan documentation: launch handoff

## Decision

Use the public GitHub fork `Novaplan-AI/documentation`, with `pipeshub-ai/documentation` as upstream. Clone the fork locally for editing. A clone is a local working copy; a fork is the independently managed GitHub repository. Keeping the upstream relationship makes later documentation updates easier to review and merge.

## First release

- Site name: Novaplan.
- Destination: `https://docs.novaplan.ai`.
- Support: `support@novaplan.ai`.
- Logos and favicon: original files from the public Novaplan website, copied locally.
- 12 German customer guides: introduction, contact, onboarding, authentication overview, password, OTP, users, groups, teams, connector overview, agent overview, agent setup.
- 160 English reference pages retained under **Technische Referenz (Englisch)**. They still include upstream product references and screenshots. Their full localization and visual rebranding are a later phase.
- All 172 original page paths remain available and in navigation. No `/de/` prefix was introduced.
- German pages use text instructions instead of upstream screenshots showing a different brand. English control names accompany German labels where helpful; check them against the deployed Novaplan version.
- Installation URLs, package names, environment variables, OAuth endpoints, and upstream source links are not renamed.
- The documentation index `llms.txt` lists all 172 pages under the Novaplan docs domain.

These are edited German customer guides, not sentence-for-sentence translations. The underlying source and history remain available in the fork.

## Connect Mintlify

1. Create a company-controlled account at <https://dashboard.mintlify.com>.
2. Create the Novaplan documentation project and connect the existing GitHub repository `Novaplan-AI/documentation`. Do not replace it with a starter template.
3. Authorize the Mintlify GitHub app for this repository. A GitHub organization owner may need to approve installation.
4. The docs configuration is `docs.json` in the repository root. The intended production branch is `main` after the reviewed Novaplan changes are merged. Before merging, use a branch preview if the dashboard provides one.
5. Review the Mintlify preview: logo visibility in both themes, German navigation, support link, mobile navigation, and representative deep links.
6. Check the plan's custom-domain and Mintlify-footer branding options in the dashboard before choosing a paid plan. No subscription has been purchased as part of this change.
7. In Domain Setup, add `docs.novaplan.ai`. Copy the exact DNS records Mintlify supplies into the DNS provider managing `novaplan.ai`. Do not guess a CNAME target or replace the main site's records.
8. Wait for Mintlify to verify the domain and provision HTTPS. Open the introduction and several connector deep links on the custom domain.
9. Only then have Abhishek change the Novaplan application's documentation base URL to `https://docs.novaplan.ai`.

Official guidance: <https://www.mintlify.com/docs/quickstart> and <https://www.mintlify.com/docs/settings/custom-domain>.

## Application link audit

The local PipesHub application checkout contains 64 distinct documentation paths across frontend and backend source. Nine did not exist in the upstream documentation snapshot.

Two exact replacements now have permanent redirects:

| Existing app link | Documentation destination |
| --- | --- |
| `/connectors/azure/azureblob` | `/connectors/azure-blob/azure-blob` |
| `/connectors/azure/azurefiles` | `/connectors/azure-files/azure-files` |

Seven upstream gaps still require a correct guide or an application-link correction:

- `/connectors/google-workspace/meet/meet`
- `/connectors/google-workspace/forms/forms`
- `/connectors/microsoft-365/outlook-personal`
- `/connectors/minio/minio`
- `/workspace/prompts`
- `/agents/skills`
- `/workspace/web-search`

Do not silently redirect Outlook Personal to the organizational Outlook setup: the authentication requirements may differ. Likewise, do not assume MinIO and Amazon S3 instructions are interchangeable.

Abhishek's domain change should cover backend connector metadata and hardcoded frontend URLs, not just one frontend constant. This task does not change the application checkout. Recheck links against the actual release used by Novaplan; the local checkout may differ.

Page filenames are preserved. German heading text differs, so pre-existing links to English heading fragments on translated pages need a separate review if they are used outside the repository.

## Verification

- Mintlify's official `mint validate`: passed.
- Configuration checked against the downloaded official JSON schema: passed.
- All 172 original page files and navigation entries: present.
- Internal page and asset links in the 12 German guides: no missing targets.
- Browser preview: introduction rendered successfully; both theme logos and German navigation checked. Local search requires Mintlify login and was not tested.
- Application links: two redirects added; seven inherited gaps listed above.
- Customer flows are adapted from upstream documentation; they still need confirmation against the deployed Novaplan product.
- Live custom-domain deployment, DNS, HTTPS, and email delivery are not yet verified.

## Maintaining the fork

Keep Novaplan changes in reviewable commits. Fetch changes from upstream into a separate update branch, review the diff, and merge deliberately. Do not force-sync the fork to upstream: that can discard Novaplan branding and translations.

For each upstream update, check `docs.json`, changed customer guides, new page paths, redirects, and retained English screenshots. Translate changed customer-facing instructions and run `mint validate` before merging. Technical strings must stay compatible with the deployed application.
