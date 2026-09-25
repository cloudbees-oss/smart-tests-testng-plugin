# launchableinc/testng

test selector for TestNG

## How to use

### Using subset result

```
# create subset list file
$ launchable subset --target 30% maven src/test/java > subset.txt

# set subset result file path to ENV
$ export SMART_TESTS_SUBSET_FILE_PATH=subset.txt

# run tests
$ mvn test
```

### Using rest result

```
# create rest list file
$ launchable subset --target 30% --rest rest.txt maven src/test/java > subset.txt

# set rest result file path to ENV
$ export SMART_TESTS_REST_FILE_PATH=rest.txt

# run tests
$ mvn test
```

### Legacy environment variables

`LAUNCHABLE_SUBSET_FILE_PATH` and `LAUNCHABLE_REST_FILE_PATH` are still read as
deprecated fallbacks if the `SMART_TESTS_*` variables above are not set, so
existing pipelines keep working. A warning is logged when a legacy variable is
used — switch to the `SMART_TESTS_*` names when convenient.

## Author

Launchable, Inc.

## Releases

Releases are managed by tagpr. On every push to `main`, tagpr creates or
updates a release pull request. Merging that pull request creates a
`launchable-testng/<version>` tag and a GitHub Release. The same workflow then
publishes the tagged revision to Maven Central.

Repository administrators must enable **Settings → Actions → General →
Workflow permissions → Allow GitHub Actions to create and approve pull
requests**. Configure these repository secrets before merging a release PR:

- `MAVEN_CENTRAL_USERNAME` and `MAVEN_CENTRAL_PASSWORD`: Central Portal user
  token credentials.
- `MAVEN_GPG_PRIVATE_KEY` and `MAVEN_GPG_PASSPHRASE`: the signing key and its
  passphrase.
