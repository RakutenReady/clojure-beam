# curbside-clojure-beam

A Clojure library for Apache Beam.

## Tests

```
docker-compose up
lein test
```

## Releasing to Artifactory

1. Retrieve Artifactory credentials from the eng.json bundle in
   https://github.com/Curbside/secrets
2. Set the environment variables ARTIFACTORY_PASS and ARTIFACTORY_USER.
3. Make sure that pgp-agent has your password cached so that you can sign stuff without being prompted. An easy way to do this is to run `gpg -ac < README.md > /dev/null`.
4. Make sure you are on the master branch, its remote branch is set to the primary repo (https://github.com/Curbside/curbside-jwt/), and your local branch is up to date.
5. Run `lein release :patch`. Replace `:patch` with `:minor` or `:major` as needed. This determines which of the version numbers will be changed in `project.clj` (the version number format is MAJOR.MINOR.PATCH).
6. If something goes wrong, you may need to `git reset --hard HEAD~1` and `git tag -d <version>` before trying again.
