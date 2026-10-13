# Security Policy

This is the default security policy for every [Wave RF](https://github.com/Wave-RF) repository that doesn't publish its own. If a repository has its own `SECURITY.md`, that one takes precedence.

## Reporting a vulnerability

**Please do not open a public issue, discussion, or pull request for a security vulnerability.**

Report it privately, either way:

- **GitHub:** open the repository's **Security** tab and choose **Report a vulnerability**. This opens a private advisory that only you and the maintainers can see.
- **Email:** write to **<security@wave-rf.com>**.

Please include:

- the repository and the affected version or commit
- a description of the vulnerability and its potential impact
- steps to reproduce, or a proof of concept
- a suggested fix, if you have one

We acknowledge reports within **48 hours** and aim to send an initial assessment within **5 business days**.

### WaveHouse Cloud

A vulnerability in the hosted [WaveHouse Cloud](https://wavehouse.cloud) service, as opposed to the source code in these repositories, goes to **<security@wavehouse.cloud>**. See [wavehouse.cloud/security](https://wavehouse.cloud/security).

### Forks

A few repositories here are forks of other projects. If the vulnerability is in the upstream code rather than in our changes, please report it to the upstream project.

## Supported versions

| Version | Supported |
| --- | --- |
| Latest release of each project | Yes |
| Older releases | Best effort |

## Disclosure policy

We follow [coordinated disclosure](https://en.wikipedia.org/wiki/Coordinated_vulnerability_disclosure). Once a fix is available, we will:

1. release a patched version;
2. publish a security advisory on GitHub;
3. credit the reporter, unless they prefer to stay anonymous.
