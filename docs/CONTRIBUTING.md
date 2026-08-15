# Contributing to Startup Credits

Thank you for helping keep this catalog accurate and current. This guide explains
how to add or update a startup-credit vendor entry.

## Repository layout

Every vendor lives in its own YAML file under `vendors/<category>/<slug>.yaml`.
The `<category>` is a short grouping token (for example `cl` for cloud providers,
`ai` for AI tooling, `fin` for financial services). The `<slug>` is a
lowercase, kebab-case identifier unique to the vendor.

## Anatomy of a vendor entry

A minimal, well-formed vendor file contains:

```yaml
vendor: Example Vendor
description: >
  Short neutral summary of what the vendor offers, written in our own words.
programs:
  - name: Example Startup Program
    eligibility:
      - Funded or bootstrapped
      - Fewer than 10 employees
    offers:
      - name: Standard Tier
        credits: "up to $10,000"
        terms: >
          Credits expire 12 months after redemption.
        source: https://example.com/startup-program
```

## Rules for submissions

1. **One vendor per file.** Do not mix multiple vendors or unrelated paths in a
   single YAML file.
2. **Every factual value must be sourced.** Add a `source` URL for each offer
   and keep the URL to the vendor's own published program page where possible.
3. **Do not invent numbers.** If the vendor publishes no fixed credit amount
   (e.g. the amount varies by stage or usage), record the eligibility and
   explicitly mark the amount as variable instead of guessing.
4. **Neutral summaries only.** Summaries must be our own neutral prose, never a
   fabricated quote attributed to the vendor.
5. **Keep applications-status information current.** If a vendor has paused new
   applications or introduced a waitlist, record that plainly in the offer
   description and in `access.instructions` rather than omitting it.

## Validation

Before opening a pull request, run the repository's YAML validation locally:

```bash
pip install PyYAML
python - <<'PY'
import glob, yaml
for path in sorted(glob.glob('vendors/**/*.yaml', recursive=True)):
    with open(path, encoding='utf-8') as fh:
        yaml.safe_load(fh)
    print('OK', path)
PY
```

The CI workflow `validate-vendors.yml` runs the same check on every pull
request that touches `vendors/**`.

## Commit hygiene

- Sign off every commit (`git commit -s` or a `Signed-off-by:` trailer).
- Reference the issue you are addressing in the PR description.
- Keep the PR scoped to a single vendor or a single corrective change.

## Review process

Maintainers verify that (a) every submitted value is backed by a public source,
(b) the source URLs resolve, and (c) the file structure follows the layout
above. PRs that mix unrelated changes or that lack source URLs are returned for
revision.
