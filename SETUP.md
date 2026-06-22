# Publish this profile

GitHub renders the README of the repo named **exactly** like your username.

## 1. Review the current live profile
The target repo already exists at `ghostON3/ghostON3`. Check it before replacing
anything:

```sh
git ls-remote https://github.com/ghostON3/ghostON3.git
```

This draft uses `assets/profile-mockup.png` so the README does not render a
broken hero image. A future wide banner can replace it with `assets/banner.png`
(1280×400 looks best).

## 2. Current local state
This workspace has a local branch named `profile-readme-ai-engineer` based on
`origin/master`, with the draft applied on top. It is intentionally not pushed.

To inspect the delta:

```sh
cd /home/ghost/projects/github-profile
git diff origin/master...HEAD
```

## 3. Publish as a reviewable branch, awake only
```sh
cd /home/ghost/projects/github-profile
git push -u origin profile-readme-ai-engineer
```

Then compare it against the current `master` profile before making it the live
profile README.

## 4. (Optional) Animated contribution snake
Add `.github/workflows/snake.yml` (template below), run it once from the Actions tab,
then it auto-regenerates daily. Swap the activity-graph `<img>` in README for the snake output.

```yaml
name: snake
on:
  schedule: [{ cron: "0 0 * * *" }]
  workflow_dispatch:
permissions:
  contents: write
jobs:
  snake:
    runs-on: ubuntu-latest
    steps:
      - uses: Platane/snk@v3
        with:
          github_user_name: ${{ github.repository_owner }}
          outputs: |
            dist/snake.svg
            dist/snake-dark.svg?palette=github-dark
      - uses: crazy-max/ghaction-github-pages@v4
        with: { target_branch: output, build_dir: dist }
        env: { GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }} }
```

## What's faithful to the mockup vs. not
- ✓ Hero banner, the 4 `> ROLE` lines, tech-stack badges, featured-project cards, stats + top-languages, contribution graph, connect row, tagline.
- ✗ The exact custom-rendered single-image layout in your screenshot is a design mockup — GitHub profiles are markdown, so the pieces stack vertically. This gets ~80% of the look with live, auto-updating cards.
- ⚠ Edit the placeholder repo names (`elo-evo-electron`, `OpenHands`, `liquid-glass`) and the LinkedIn/X/website/email links to your real ones — badges 404 silently if a repo is private or misnamed.
