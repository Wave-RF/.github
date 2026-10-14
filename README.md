# Wave RF — `.github`

Org-wide GitHub defaults for [@Wave-RF](https://github.com/Wave-RF).

| File | What it does |
| --- | --- |
| [`profile/README.md`](profile/README.md) | Rendered on the **public** org profile at <https://github.com/Wave-RF>. |
| [`CODE_OF_CONDUCT.md`](CODE_OF_CONDUCT.md) | Contributor Covenant 2.1. Reports go through GitHub's **Report content**, or to `hello@wave-rf.com`. |
| [`CONTRIBUTING.md`](CONTRIBUTING.md) | General contribution guide: issues first, Conventional Commit PR titles, squash merges. |
| [`SECURITY.md`](SECURITY.md) | Private reporting via GitHub or `security@wave-rf.com`. No response-time promise. WaveHouse and chtypes state theirs in their own `SECURITY.md`. |
| [`SUPPORT.md`](SUPPORT.md) | Where to ask what. |
| [`.github/PULL_REQUEST_TEMPLATE.md`](.github/PULL_REQUEST_TEMPLATE.md) | Summary, test plan, related issues. |
| [`.github/ISSUE_TEMPLATE/`](.github/ISSUE_TEMPLATE/) | Bug report and feature request forms. Blank issues stay allowed. |

Everything goes live as soon as it lands on `main`.

## How the defaults apply

GitHub uses each file here for **every** repository in the org, **public and private**, that doesn't have its own file of that type ([GitHub docs](https://docs.github.com/en/communities/setting-up-your-project-for-healthy-contributions/creating-a-default-community-health-file)). So:

- **Keep them general.** Nothing project-specific belongs here, and nothing that would read oddly on an internal or hardware repository.
- **A repository's own file always wins.** WaveHouse, chtypes and most of the public tools have their own `CONTRIBUTING.md`, and some have their own `SECURITY.md` and PR template.
- **Issue templates are all-or-nothing.** If a repository has anything in its own `.github/ISSUE_TEMPLATE/`, including just a `config.yml`, none of these forms are used there.
- **Labels set by an issue form must exist** in the repository where it's used. `bug` and `enhancement` are GitHub's defaults.
- **Links inside these files are absolute** (`https://github.com/Wave-RF/.github/blob/main/…`), because they're displayed from other repositories.
- `LICENSE`, `dependabot.yml`, `CODEOWNERS` and workflow files **can't** be defaults. They have to live in each repository.

## Making a repository public

1. Make sure it has its own `LICENSE` and a `README.md`.
2. Turn on the same security settings every public Wave RF repository has:

   ```sh
   r=<repo>
   gh api -X PUT repos/Wave-RF/$r/private-vulnerability-reporting
   gh api -X PUT repos/Wave-RF/$r/vulnerability-alerts
   gh api -X PUT repos/Wave-RF/$r/automated-security-fixes
   gh api -X PATCH repos/Wave-RF/$r --input - <<'EOF'
   {"security_and_analysis":{"secret_scanning":{"status":"enabled"},"secret_scanning_push_protection":{"status":"enabled"},"secret_scanning_non_provider_patterns":{"status":"enabled"},"secret_scanning_validity_checks":{"status":"enabled"}}}
   EOF
   ```

   `SECURITY.md` tells reporters to use the **Report a vulnerability** button, so private vulnerability reporting must be on.
3. If its issue `config.yml` links to Discussions, turn Discussions on (`gh api -X PATCH repos/Wave-RF/$r -F has_discussions=true`). Otherwise that link is a 404.
4. Add it to the profile.

## Maintaining the profile

- **Only link to public repositories.** A link to a private repository is a 404 for every visitor. Check with `gh repo view Wave-RF/<name> --json visibility` before adding one, and don't name private repositories anywhere in this repository.
- **Logos are hotlinked, not copied**, so a rebrand at the source shows up here automatically. If a source file is moved or renamed, update its URLs in the profile.
  - **Wave RF:** `https://wave-rf.com/images/Combined{Black,White}Large.svg`, the same files the wave-rf.com header uses.
  - **WaveHouse:** [`Wave-RF/WaveHouse` → `docs/public/branding/lockup-{light,dark}.svg`](https://github.com/Wave-RF/WaveHouse/tree/main/docs/public/branding). These are generated with the wordmark already outlined to paths, so they render in the real typeface on GitHub.
  - Only use SVGs whose text is outlined to paths. GitHub renders SVG `<text>` in the viewer's system font.
  - Give every logo `<img>` a real `alt`. A screen reader reads the `alt`, not anything inside the SVG.
- **Links to our own sites carry standard UTM parameters:** `utm_source=github&utm_medium=referral&utm_campaign=org-profile&utm_content=<placement>`. `utm_content` names the spot on the page (`header`, `cloud-cta`, `footer`, …) so you can tell which link was clicked.
- **Release badges filter by tag.** WaveHouse also tags `clients/ts/v*` SDK releases, so its badge uses `filter=v*` to show the server version.
