![Logo](static/logo.png)

# create-issue-branch

## This is the `dev` branch

[![BCH compliance](https://bettercodehub.com/edge/badge/robvanderleek/create-issue-branch?branch=master)](https://bettercodehub.com/)
[![Build Status](https://travis-ci.com/robvanderleek/create-issue-branch.svg?branch=master)](https://travis-ci.com/robvanderleek/create-issue-branch)

> A GitHub App built with [Probot](https://github.com/probot/probot) that creates a new branch after assigning an issue

Built in response to this feature reuest issue:
https://github.com/isaacs/github/issues/1125

## What does this app do?

The typical workflow is:
 1. An issue is created, for example: Issue 15: Fix nasty bug!

 *some time may pass*

 2. The issue is assigned
 3. When the issue is assigned this app will create a new issue branch
    (for the example issue this branch will be called `issue-15-Fix_nasty_bug`)

If the issue is re-assigned no new branch will be created.


## Configuration

This app does not require a configuration. However, if you want to override 
the default behaviour you can do so by placing a YAML file in your repository 
at the location: `.github/issue-branch.yml` with the overrides.

### Generated branch names

Branch names are generated from the issue, there are 3 flavours:

 1. `tiny` => an `i` followed by the issue number, for example: `i15`
 2. `short` => the word `issue` followed by the issue number, for example:
    `issue-15`
 3. `full` => the word issue followed by the issue number followed by the
    issue title, for example: `issue-15-Fix_nasty_bug`
    
The default is `full`, other types can be configured in the YAML like this:

```
branchName: tiny
```

or

```
branchName: short
```

### Select source branches based on issue label

You can override the source branch (by default the "default branch" of the
repository is used) based on the issue label.

For example, if you want branches for issues with the `enhancement` label to
have the `dev` branch as a source and branches for issues with the `bug`
label to have the `staging` branch as a source add this to your configuration
YAML:

```
branches:
  - label: enhancement
    name: dev
  - label: bug
    name: staging
```

When issues have multiple labels the branch of the first match (based on the 
order in the configuration YAML will be used).

If a configured branch does not exist in the repository the "default branch"
is used.

## Installation

You can install the app directly from [*this page*](https://github.com/apps/create-issue-branch)

## Feedback, suggestions and bug reports

Please create an issue here: https://github.com/robvanderleek/create-issue-branch/issues

## Contributing

If you have suggestions for how create-issue-branch could be improved, or want to report a bug, open an issue! We'd love all and any contributions.

For more, check out the [Contributing Guide](CONTRIBUTING.md).

## License

[ISC](LICENSE) © 2019 Rob van der Leek <robvanderleek@gmail.com> (https://twitter.com/robvanderleek)
