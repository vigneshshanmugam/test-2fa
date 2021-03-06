# Releasing

Before releasing a new version of packages to the NPM and GitHub, Set all the environment variables necessary for the release scripts. The required variables are:

- GITHUB_TOKEN
- NPM_TOKEN
- VAULT_NPM_TOTP_TOKEN
- VAULT_URL

```
$ GITHUB_TOKEN=<token> \
    NPM_TOKEN=<token> \
    VAULT_NPM_TOTP_TOKEN=<token> \
    VAULT_URL=<url> \
    npm run release
```

## Releasing all packages

To publish all the packages run `npm run release` with the required environment variables. It will run `lerna publish`(we use --independent) so it will prompt the version number for every package.

- Automatically determining a semantic version bump (based on the types of commits landed)
- Creating annotated Git tags for all the packages that has changed since last release
- Generating `CHANGELOG.md` using conventional commit messages.
- Publishing the packages via `npm publish`

**Note: To override the semantic version bump, use `npm run release -- (minor|patch|major)`**

## Releasing artifacts to GitHub

Use `npm run github-release` in the root directory, the script takes care packaging and creating a release for `@v1v/test-2fa` in GitHub with the previous annonated tag.

**Note: Make sure you pass the GITHUB_TOKEN (with push access) in your environment variable while releasing**
