# normalize-version

This is very simple GitHub Action that normalizes given version.

* It makes sure that given version is always prefixed with `v`.
* It extracts the major version from the given version, and also makes sure that it is prefixed with `v`.

## Inputs

* `version` **Required**

    The version to normalize.

## Outputs

* `semver`

    The normalized semver version.

* `major`

    The major version.

## Example usage

```yaml
name: Release

on:
  workflow_dispatch:
    inputs:
      version:
        description: 'Version to release'
        required: true

jobs:
  release:
    runs-on: ubuntu-latest
    steps:
    - id: version
      uses: cdqag/normalize-version@v1
      with:
        version: ${{ inputs.version }}

    - name: Release
      run: |
        echo "Releasing version ${{ steps.version.outputs.semver }} to branch ${{ steps.version.outputs.major }}"

```

## License

This project is licensed under the Apache-2.0 License. See the [LICENSE](LICENSE) file for details.
