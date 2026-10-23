# Contributing to Aluminium

Aluminium is a personal fork of [Helium](https://github.com/imputnet/helium). This repository contains its shared Chromium patches, resources, and development tooling. Most of these guidelines come from Helium's own contributing guide, adapted for Aluminium.

Aluminium doesn't have its own platform packaging repos yet. Until it does, Helium's are the reference:

- [Helium for macOS](https://github.com/imputnet/helium-macos)
- [Helium for Linux](https://github.com/imputnet/helium-linux)
- [Helium for Windows](https://github.com/imputnet/helium-windows)

Never open issues or PRs on Helium's repos from this project. See [AGENTS.md](AGENTS.md).

## Before you start

### General

- AI help is allowed, as long as the change is tested on a real system. The full AI policy is in [AGENTS.md](AGENTS.md).

### Issues

- Search existing issues before opening a new bug report or feature request.
- When creating an issue, please follow the template and be as specific
  as possible.
- Please do not create duplicate issues.

### Contributions

- For non-trivial changes, start with an issue so we can agree on the feature before you build it.
- Test every change on a real system before opening a PR, and say what you tested on. Untested changes are not merged.

## Development
macOS is our primary development platform, so it's the recommended
development environment for community contributions.

Linux packaging includes a similar development script, so the same guide
can be applied there too.

[> See development docs in macOS repo][macos-guide]

## Working with patches

Most code changes in this repository are maintained as quilt patches
applied on top of Chromium.

- Don't edit files in `patches/` directly unless you know exactly what
  you're doing.
- Make code changes in the Chromium source tree, then refresh the
  affected patch.
- Keep patch ordering and ownership intact.
- Follow the existing vendor grouping under `patches/` unless maintainers
  ask for something different.

When working in a platform repository, the usual workflow is:

1. Load the development environment.
1. Merge the patch series and push all patches.
1. Use `quilt` in `build/src` to create or edit a patch.
1. Refresh patches after your changes.
1. Unmerge the series, verify, commit.

## Code style

- Follow Chromium style and conventions.
- Prefer existing Chromium or Helium patterns over introducing new abstractions.
- Keep changes focused and minimal.
- Proofread surrounding code before submitting.
- When adding new Aluminium-authored files to the Chromium tree, include a copyright header like the one Helium uses in its patches, with Aluminium's name.
- Refer to existing Helium patches for guidance if necessary.

## Git style

### Clean commit messages

We use commit titles that are similar to [Linux Kernel Style][linux-style],
but with a more flexible scope-first format. And without the email prefix,
obviously.

Examples of titles from recent history as of writing:

```
- helium/ui/layout: add a ⌘+S shortcut to toggle vertical tabs
- helium/ui/pdf-viewer: fix stuck width when sidebar's collapsed
- deps: update ublock to 1.70.0
- merge: update to chromium 146.0.7680.75
- helium/core/keyboard-shortcuts: update command state correctly
```

The part before the colon should describe the area being changed (scope),
and the part after the colon should explain the change itself.

1. Pick the most helpful scope for the change.
1. Do not use generic scopes like "feat" or "chore".
1. Keep titles specific and meaningful rather than generic.
1. If the change needs extra context, add a body explaining why it was
   made and what changed.

Make sure that the title is 65 chars long or shorter. This is needed for
squash merging with a PR reference, so that the total length is 72 chars
or under.

72 is a common length limit before the title gets wrapped into the body
in most places (such as GitHub). For example, this final commit title is
exactly 72 characters long:

```
helium/ui/customize: add change wallpaper button, fix visibility (#1053)
```

If a multi-commit pull request contains uninformative or malformed commit
titles, maintainers will ask you to rewrite them before review/merge.

### Clean commit history

Keep branch history tidy before opening a pull request.

- If your changes are big, split them into several commits with a smaller scope.
- If you find a bug in an unmerged commit, prefer folding the fix into the
  commit that introduced it.
- Use interactive rebase extensively to maintain a clean and readable commit
  history in your branch.
- Use `git commit --amend` when fixing the latest commit.
- Use `git commit --fixup=<hash>` for older commits, then squash during an
  interactive rebase.
- Use `git cherry-pick <hash>` for single-commit changes if a rebase is
  too complex.
- If you rewrite commits that were already pushed, force push the branch with
  `git push -f` or alike.

This keeps the branch history easier to review, bisect, and revert.

## Pull requests

Before opening a pull request, make sure that:

- The change is tied to an approved feature request or confirmed bug.
- The branch builds and runs without issues and has been thoroughly tested.
  Otherwise, the pull request is marked as draft.
- The pull request description clearly explains the change scope. The
  description includes visuals (screenshots, videos) if applicable.
- You mention which platforms you tested on, and whether AI helped.
- The branch is rebased on `main`, or at least the latest Chromium milestone.

Small and focused pull requests are much easier to review. Please split your
changes into several follow-up PRs if necessary.

## Licensing

By contributing to Aluminium, you agree that your changes will be licensed under
the repository's existing licensing terms.

<!-- Long referenced links -->
[macos-guide]: https://github.com/imputnet/helium-macos/blob/main/docs/building.md#development-build-and-environment
[linux-style]: https://docs.kernel.org/process/submitting-patches.html#the-canonical-patch-format
