# ci-info

[![PyPI version](https://badge.fury.io/py/ci-info.svg)](https://badge.fury.io/py/ci-info)
[![Build Status](https://travis-ci.org/mgxd/ci-info.svg?branch=master)](https://travis-ci.org/mgxd/ci-info)

A Python implementation of [watson/ci-info](https://github.com/watson/ci-info).
Get details about the current Continuous Integration environment.

Please [open an issue](https://github.com/mgxd/ci-info/issues/new)
if your CI server isn't properly detected :)


## Supported CI tools

Officially supported CI servers:

| Name | is PR |
|------|------|
| [AWS CodeBuild](https://aws.amazon.com/codebuild/) | 🚫 |
| [AppVeyor](http://www.appveyor.com) | ✅ |
| [Azure Pipelines](https://azure.microsoft.com/en-us/services/devops/pipelines/) | ✅ |
| [Bamboo](https://www.atlassian.com/software/bamboo) by Atlassian | 🚫 |
| [Bitbucket Pipelines](https://bitbucket.org/product/features/pipelines) | ✅ |
| [Bitrise](https://www.bitrise.io/) | ✅ |
| [Buddy](https://buddy.works/) | ✅ |
| [Buildkite](https://buildkite.com) | ✅ |
| [CircleCI](http://circleci.com) | ✅ |
| [Cirrus CI](https://cirrus-ci.org) | ✅ |
| [Codeship](https://codeship.com) | 🚫 |
| [Drone](https://drone.io) | ✅ |
| [dsari](https://github.com/rfinnie/dsari) | 🚫 |
| [GitLab CI](https://about.gitlab.com/gitlab-ci/) | 🚫 |
| [GoCD](https://www.go.cd/) | 🚫 |
| [Hudson](http://hudson-ci.org) | 🚫 |
| [Jenkins CI](https://jenkins-ci.org) | ✅ |
| [Magnum CI](https://magnum-ci.com) | 🚫 |
| [Netlify CI](https://www.netlify.com/) | ✅ |
| [Nevercode](http://nevercode.io/) | ✅ |
| [Sail CI](https://sail.ci/) | ✅ |
| [Semaphore](https://semaphoreci.com) | ✅ |
| [Shippable](https://www.shippable.com/) | ✅ |
| [Solano CI](https://www.solanolabs.com/) | ✅ |
| [Strider CD](https://strider-cd.github.io/) | 🚫 |
| [TaskCluster](http://docs.taskcluster.net) | 🚫 |
| [TeamCity](https://www.jetbrains.com/teamcity/) by JetBrains | 🚫 |
| [Travis CI](http://travis-ci.org) | ✅ |


## Installation

```
pip install ci-info
```

## Usage

```python
import ci
if ci.is_ci():
    print(ci.name())

"My CI Name"
```


## API

### `ci.name()`

Returns a string containing name of the CI server the code is running on.
If CI server is not detected, it returns `None`.

Don't depend on the value of this string not to change for a specific
vendor.

### `ci.is_ci()`

Returns a boolean. Will be `True` if the code is running on a CI server,
otherwise `False`.

Some CI servers not listed here might still trigger the `ci.is_ci()`
boolean to be set to `True` if they use certain vendor neutral
environment variables. In those cases `ci.name()` will be `None` and no
vendor specific boolean will be set to `True`.

### `ci.is_pr()`

Returns a boolean if PR detection is supported for the current CI server. Will
be `True` if a PR is being tested, otherwise `False`. If PR detection is
not supported for the current CI server, the value will be `None`.

### `ci.info()`

Returns a dictionary of all above values in key/value pairs.

## License

[MIT](LICENSE)
