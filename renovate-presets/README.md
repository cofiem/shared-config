# Renovate bot config presets

Uses the [Shared config presets for GitHub](https://docs.renovatebot.com/config-presets/#github).

Example:

```
{
  "extends": ["github>cofiem/shared-config//renovate-presets/default"]
}
```

## Default

- [Use renovate best practices](https://docs.renovatebot.com/presets-config/#configbest-practices)
- [Max 10 PRs](https://docs.renovatebot.com/presets-default/#prconcurrentlimit10)
- [All PRs must be manually merged](https://docs.renovatebot.com/presets-default/#automergedisabled)
- [Add label 'dependencies' to PRs](https://docs.renovatebot.com/configuration-options/#addlabels)
- [Rebase PRs when they are conflicted](https://docs.renovatebot.com/configuration-options/#rebasewhen)
- [Wait until updates are 5 days or older](https://docs.renovatebot.com/key-concepts/minimum-release-age/)
- [Create PRs after checks pass](https://docs.renovatebot.com/configuration-options/#prcreation)
- [Full lock file update each weekend](https://docs.renovatebot.com/configuration-options/#lockfilemaintenance)
- [Custom manager using formatted comment](https://docs.renovatebot.com/modules/manager/regex/)

### Custom manager using formatted comment

Will look in files that end with `.yaml`, `.yml`, `.hcl`, `.sh`, `.toml`, `Dockerfile`.
Each element must be separated by at least one whitespace.

- Comment can start with `//` or `#` (trailing whitespace optional)
- Then 'renovate:'
- Then must have 'datasource='
- Then must have 'packageName=' (exact package name)
- Then optional 'depName=' (displayed dependency name)
- Then optional 'datasourceTemplate='
- Then optional 'versioning='
- Then optional 'extractVersion='
- Then optional 'depType='
- Then optional 'registryUrl='
- Then optional 'currentDigest='
- Then on next line must have variable name that ends with 'version', 'VERSION', 'default'
- Then must have separator either `:` or `=`
- Then must have current version surrounded by `'` or `"`
- Then must have one whitespace (space, tab, newline, etc.)

Examples:

```
# renovate: datasource=deb packageName=docker-ce registryUrl=https://download.docker.com/linux/ubuntu?suite=noble&components=stable&binaryArch=amd64 
docker_version: '5:28.5.2-1~ubuntu.24.04~noble'

# renovate: datasource=python-version packageName=python versioning=python
PYTHON_VERSION="3.13"

# renovate: datasource=pypi packageName=pip versioning=pep440
PIP_VERSION="25.3"
```