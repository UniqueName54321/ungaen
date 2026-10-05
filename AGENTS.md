# Ungaen Contributor Instructions

Ungaen is a Scratch-inspired block-based game engine intended to combine an approachable sprite/block workflow with a serious native runtime.

## Git workflow

Use Git throughout development.

- Work on the existing branch unless the user asks for a separate branch.
- Before making changes, inspect `git status` and relevant recent history when useful.
- Do not discard, overwrite, reset, or otherwise destroy unrelated user changes.
- Make commits for coherent completed units of work rather than one giant commit containing unrelated changes.
- Use concise descriptive commit messages.
- Prefer Conventional Commit-style prefixes where appropriate:
  - `feat:` for new functionality
  - `fix:` for bug fixes
  - `refactor:` for internal restructuring
  - `docs:` for documentation
  - `test:` for tests
  - `build:` for build-system changes
  - `chore:` for repository/tooling maintenance
- Run relevant tests/build checks before committing when practical.
- After successfully completing a requested task, commit the changes unless the user explicitly asks not to commit.
- Push completed commits to `origin` when network access and authentication are available, unless the user asks not to push.
- Never use `git push --force`, destructive resets, or history rewriting unless the user explicitly requests it and the consequences are clear.

## Releases and versions

Normal development commits do not require version tags or GitHub Releases.

Create a new version only when the user explicitly requests a release, declares a milestone complete, or clearly asks for a new version.

For a release:

1. Ensure the working tree is clean.
2. Run the relevant test/build checks.
3. Update any version metadata and changelog/release documentation used by the project.
4. Commit the release preparation with a message such as:
   `chore(release): v0.0.1`
5. Create an annotated Git tag:
   `git tag -a vX.Y.Z -m "Ungaen vX.Y.Z"`
6. Push the commit and tag:
   `git push origin main`
   `git push origin vX.Y.Z`
7. Create the corresponding GitHub Release using `gh release create`.
8. Use release notes that clearly summarize important user-visible changes.
9. During early development, mark releases as prereleases unless the user says otherwise.

Never silently invent a major/minor version bump. If the appropriate version is not evident from explicit project instructions, use the existing versioning convention and choose the smallest sensible increment.

## Prototype-era versioning

Until Ungaen establishes a stable release policy:

- Use `v0.0.x` for early prototype releases.
- Prototype 0 should become the first meaningful release, `v0.0.1`, unless the user chooses another version.
- GitHub release titles may use human-readable milestone names such as `Ungaen Prototype 0`.
- Development between releases should be represented by normal commits, not a new tag for every change.

## Repository safety

Do not commit:

- passwords
- API keys
- authentication tokens
- `.env` secrets
- signing keys
- platform NDA material
- generated build directories
- large temporary artifacts

Before adding a new generated/cache directory, consider whether it belongs in `.gitignore`.

Do not add or change the project's software license unless the user explicitly chooses one.
