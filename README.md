# PRAXO-CORE for Fortran

Dedicated repository for the Fortran implementation of PRAXO-CORE: an
embeddable, MIT-licensed agent execution kernel with policy controls,
human-in-the-loop approval, checkpoints, events, and tool calling.

- Package: `praxo-core-fortran` (`0.6.0`)
- Registry: Source / CMake
- Install: `Source build (see README)`
- Documentation: https://axisvela.github.io/praxo-core/languages/fortran/
- Mirror repository: https://github.com/axisvela/praxo-core-fortran
- Canonical source: https://github.com/axisvela/praxo-core/tree/main/language/fortran
- Release index: https://axisvela.github.io/praxo-core/languages/registry-status/

This repository is a discovery mirror of the canonical Fortran source.
The monorepo remains the source of truth and the release workflow source. Shared
conformance vectors are included under `spec/`, so the implementation can be
built and tested here.

## Verify

Build and test instructions are in `language/fortran/README.md`. The
monorepo CI runs the language's conformance, API snapshot, and native tests.

PRAXO-CORE is not a hosted model, workflow engine, identity provider, or safety
controller. Do not infer exactly-once execution, complete sandbox isolation,
production security certification, live-provider behavior, or physical safety
from this package.

MIT licensed.
