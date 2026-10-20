# Contributing to Wave RF projects

Thanks for helping out. This is the default guide for [Wave RF](https://github.com/Wave-RF) repositories. **If the repository you're working in has its own `CONTRIBUTING.md`, follow that one instead.** It covers that project's setup, checks, and release process.

## Before you start

- **Bugs and feature requests:** open an issue in the repository.
- **Anything bigger than a small fix:** open an issue first, so we can agree on the approach before you spend time on code.
- **Questions:** use the repository's Discussions tab if it has one. See [SUPPORT.md](https://github.com/Wave-RF/.github/blob/main/SUPPORT.md).
- **Security problems:** never in a public issue or pull request. Follow the [security policy](https://github.com/Wave-RF/.github/blob/main/SECURITY.md).

## Pull requests

- **Keep each pull request to one change.** Small, focused pull requests get reviewed faster.
- **Title it as a [Conventional Commit](https://www.conventionalcommits.org/):** `<type>(optional scope): <subject>`, for example `fix(parser): handle empty input`. Common types are `feat`, `fix`, `docs`, `refactor`, `test`, `chore`, `ci`, `deps`, `build`, `perf`, `revert` and `style`. Mark a breaking change with `!` (`feat!: …`). We squash-merge, so the title becomes the commit on `main`. In repositories with automated releases, the title also decides the version bump.
- **Say what changed and how you tested it.** The pull request template asks for both.
- **CI must pass** before we can merge.
- **Update the docs** when you change user-facing behavior.

## Licensing

Each repository's `LICENSE` file states its license. By submitting a contribution, you agree that it is licensed under that same license.

## Code of Conduct

Everyone taking part in Wave RF projects is expected to follow our [Code of Conduct](https://github.com/Wave-RF/.github/blob/main/CODE_OF_CONDUCT.md).
