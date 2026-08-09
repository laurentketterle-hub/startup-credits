# Startup Credits

The public data repository behind Sourcey's startup-offer catalog.

Each vendor has one readable YAML file under `vendors/{shard}/`. Those
files are the contribution surface; Sourcey's private Catalog engine owns the
schemas, validation, evidence, release construction, API, MCP, feed, scanner,
and hosted runtime.

## Contribute

Copy a nearby vendor file, keep the same shape, and open a pull request. CI
downloads Sourcey's exact content-addressed verifier and validates only the
changed vendor files plus their identity dependencies. It does not scan or
rebuild the complete catalog.

See [CONTRIBUTING.md](CONTRIBUTING.md) for the data rules.

## Publication

An admitted merge to `main` is the only human activation. Sourcey consumes the
exact merge commit, incrementally publishes its changed closure, and advances
one live head used by [sourcey.com](https://sourcey.com), API v1, MCP, the
change feed, and `go.sourcey.com`. Contributors never choose a release
sequence, digest, parent, deployment, or consumer-specific selector.

Catalog facts are available under [CC BY 4.0](DATA-LICENSE.md). Repository
documentation and metadata use the [MIT License](LICENSE).


## 🚀 Enhanced by Bounty Hunter

### Quick Start
```bash
git clone https://github.com/sourcey/startup-credits.git
cd startup-credits
# Follow instructions above
```

### CI Status
Automated testing and linting configured via GitHub Actions.
