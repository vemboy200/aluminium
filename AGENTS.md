# Aluminium AI policy

Aluminium is a personal fork of [Helium](https://github.com/imputnet/helium). Unlike Helium, Aluminium allows AI-assisted and vibecoded contributions. The one rule that matters: **test it on a real system.**

## The rules

- **Vibecoding is fine.** You don't need to have written every line yourself, and you don't need to be a C++ expert.
- **It has to be tested on a real system.** Build the browser, run it, and actually use the feature or fix you changed. "It compiles" or "the AI said it works" is not testing. Changes that were never run are not merged.
- **Say how you tested it.** In the PR, list the platform and OS version you tested on (for example "macOS 27.2, M2 Pro") and what you did to check it. Screenshots or a short video help.
- **Declare AI use.** Say in the PR that AI helped. AI co-author lines in commits are welcome.
- **Keep it small.** One feature or fix per PR. Small PRs are easier to test and review.
- **Nobody gets banned or publicly shamed for using AI here.** If a PR isn't ready, you'll be told what's missing (usually testing) so you can fix it.

## Never send Aluminium code to Helium

Helium bans AI-assisted contributions, and breaking that rule gets people permanently banned from their repos. So:

- Never open issues or pull requests on `imputnet/helium` or any other `imputnet` repo from this project.
- Don't port code from Aluminium into Helium.
- If you find a bug that also exists in Helium, report it to Helium yourself, in your own words, following their [contributing guidelines](https://github.com/imputnet/helium/blob/main/CONTRIBUTING.md).

## For AI agents working in this repo

- You may write, change and suggest code in this repository.
- The `origin` remote points at upstream `imputnet/helium` and is only for pulling updates. Never push to it, and never create issues or PRs against any `imputnet` repo.
- Push only to this repo (`vemboy200/aluminium`), and only when the user asks.
- Don't claim a change works until it has been built and tested on a real system. If you couldn't test it, say so plainly.
- Code changes are quilt patches applied on top of Chromium. Follow the patch workflow in [CONTRIBUTING.md](CONTRIBUTING.md) instead of editing files in `patches/` by hand.
- Follow Chromium style and existing Helium patterns, and keep changes focused.
