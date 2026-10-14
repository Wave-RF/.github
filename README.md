# Wave RF — `.github`

Org-wide GitHub defaults for [@Wave-RF](https://github.com/Wave-RF).

- **[`profile/README.md`](profile/README.md)** is the public org profile at <https://github.com/Wave-RF>.
- **`CODE_OF_CONDUCT.md`, `CONTRIBUTING.md`, `SECURITY.md`, `SUPPORT.md`** and the issue and PR templates in [`.github/`](.github/) are the defaults for every repo, public or private, that doesn't have its own file of that type. Issue templates are all-or-nothing: a repo with anything in its own `.github/ISSUE_TEMPLATE/` gets none of these.

Changes go live when they merge to `main`. Keep these files general, and use absolute links in them, because GitHub displays them from other repos.

## Making a repo public

1. Give it its own `LICENSE`. GitHub can't apply a license as an org default.
2. Apply the **Wave RF public** security configuration (org **Settings → Code security → Configurations**). New public repos get it automatically. When an existing private repo is made public, check that it's attached.
3. In **Settings → Moderation options → Reported content**, allow reports from everyone. It's the only conduct-reporting channel we publish.
4. Add it to the profile.

## Editing the profile

- Link only to public repos, and don't name private ones anywhere in this repo.
- The logos are hotlinked from wave-rf.com and from WaveHouse's [`docs/public/branding/`](https://github.com/Wave-RF/WaveHouse/tree/main/docs/public/branding). Use SVGs whose text is outlined to paths, and give each one an `alt`.
- Links to our own sites carry `utm_source=github&utm_medium=referral&utm_campaign=org-profile&utm_content=<placement>`.
