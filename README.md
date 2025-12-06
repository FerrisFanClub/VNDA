# VNDA

VNDA stands for *Visual Novel Discord Activity*.

This project aims to provide a way to create, edit and play visual novels collaboratively directly through [Discord](https://discord.com/).

This file will be updated as the project grows.

## Github guidelines

### Branches

There are 3 types of branch:

- LTS branch: basically, this is the `main` branch, which correspond to the latest stable release of the project. This branch cannot be directly modified. It only accepts merges from *release branches* (see below).
- Releases branches: each release branch corresponds to a different version of the project and must follow the following naming convention: `releases/x.y.z<_dev>` where `x.y.z` corresponds to the version and the suffix `_dev` is only used if the version is still in development. Once the version is ready, that suffix should be removed and the branch merged into `main`. Those branches cannot be directly modified. They only accept merges from *development branches* (see below).
- Development branches: each development corresponds to an issue (feature, bug fix, etc). They should be prefixed by `dev/`. Those branches can be modified with direct commit pushes and should be merged into the target release branch (according to the milestone set in the related issue).

### Commit

#### Messages

The commit messages must follow the following convention:

```
<type>(<scope>): <subject>

<description>

--
<footer>
```

Where:

- `type` is a `+`-seperated list of the following terms (ideally only one):
    - `build`: Changes the way build is done
    - `ci`: Changes the CI/CD (Github Actions)
    - `feat`: Changes relative to a feature
    - `fix`: Changes relative to a bug fix
    - `perf`: Changes relative to performances
    - `rftr`: Refactoring changes
    - `style`: Changes relative to the code style
    - `docs`: Changes relative to the documentation
    - `test`: Changes relative to the test bench
    - `revert`: Changes relative to a commit revert
- `scope` is a `+`-seperated list of the following terms (ideally only one):
    - `player`: Changes relative to the Discord activity player
    - `editor`: Changes relative to the Discord activity editor
    - `lib`: Changes relative to the VNDA library and the PostgreSQL database
    - `server`: Changes relative to the HTTP REST server
    - `github`: Changes relative to repository architecture
- `subject` is a short summary of the changes you have made
- `description` is an optional description describing in details the changes you have made if `subject` was not enough
- `footer` is optional and can be used to describe important changes introduced by the commit (such as API breaking modifications)

#### Compilation

Any commit should compile (e.g. the `cargo build` command should pass).
This allows easier regression tracking since `git bisect` would only fail on actual regressions, not compilation errors.

### Pull requests

Each pull requests must follow the following criteria before being merged:

- up-to-date with the target branch (and no conflicts of course)
- getting reviewed and approved by another team member
- passing the CI/CD Github Actions