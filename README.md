# Hacktoberfest Issue Mirror

_Note: This repo has no real content, other than this README. Do not file issues or comments
here. It simply mirrors our [beginner friendly issues](http://pup.pt/contribute) to make
them discoverable. This guide should help you get started making your first PR!_


## Background

Puppet uses [Jira](https://tickets.puppetlabs.com) for most of our issue tracking. This has the
unfortunate side effect that the [Hacktoberfest filters](https://github.com/search?utf8=✓&q=label%3Ahacktoberfest&type=Issues)
won't pick them up. This repository mirrors issues so that you can find them. You should use the
Jira links to get back to the actual ticket to find more information about it, participate in
discussions, or to file your PR.


## Getting Started

When you see a Hacktoberfest issue that looks intriguing and within your skillset, you'll want
to follow it back to the original Jira ticket. That will have any further discussion and links
to other background tickets or other information. You'll use the project name to identify the
repository to work in. For example:

| Jira Project                                               | Github Repository                                                           |
|------------------------------------------------------------|-----------------------------------------------------------------------------|
| [`PUP`](https://tickets.puppetlabs.com/browse/PUP)         | [`puppetlabs/puppet`](https://github.com/puppetlabs/puppet)                 |
| [`FACT`](https://tickets.puppetlabs.com/browse/FACT)       | [`puppetlabs/facter`](https://github.com/puppetlabs/facter)                 |
| [`SERVER`](https://tickets.puppetlabs.com/browse/SERVER)   | [`puppetlabs/puppetserver`](https://github.com/puppetlabs/puppetserver)     |
| [`PDOC`](https://tickets.puppetlabs.com/browse/PDOC)       | [`puppetlabs/puppet-strings`](https://github.com/puppetlabs/puppet-strings) |
| [`PDB`](https://tickets.puppetlabs.com/browse/PDB)         | [`puppetlabs/puppetdb`](https://github.com/puppetlabs/puppetdb)             |
| [`RK`](https://tickets.puppetlabs.com/browse/RK)           | [`puppetlabs/r10k`](https://github.com/puppetlabs/r10k)                     |
| [`TK`](https://tickets.puppetlabs.com/browse/TK)           | [`puppetlabs/trapperkeeper`](https://github.com/puppetlabs/trapperkeeper)   |
| [`MODULES`](https://tickets.puppetlabs.com/browse/MODULES) | _various repositories named `puppetlabs/puppetlabs-<modulename>`_           |


## Getting Help

As you're getting into the codebase, you might run into things that don't make sense. Or you
might need a little help understanding the architecture, or the execution model. In any case
the community is here to help you out!

* Puppet uses Slack for community interactions.
   * [Sign up for an account](https://slack.puppet.com)
   * Some interesting channels:
      * [#puppet](http://puppetcommunity.slack.com/app_redirect?channel=puppet)
      * [#puppet-dev](http://puppetcommunity.slack.com/app_redirect?channel=puppet-dev)
      * [#forge-modules](http://puppetcommunity.slack.com/app_redirect?channel=forge-modules)
      * [#testing](http://puppetcommunity.slack.com/app_redirect?channel=testing)
* Google Group mailing lists:
   * [Puppet Developers](https://groups.google.com/forum/#!forum/puppet-dev)
   * [Puppet Users](https://groups.google.com/forum/#!forum/puppet-users)
* Check out our [Office Hours schedule](https://puppet.com/community/office-hours) and see if
  any sessions match up with the topic you're struggling with.
  

## Making a Pull Request

1. Make sure you have a [Jira account](https://tickets.puppetlabs.com).
    * You'll need this to participate in issue discussions.
1. Make sure you have a [GitHub account](https://github.com/signup/free).
    * You'll need this to make the pull request.
1. Make your code changes:
    * Fork the repository on GitHub.
    * Create a topic branch in your fork from the `master` branch.
        * `git checkout -b <a_name_for_your_contribution> master`
        * Please don't work directly on the `master` branch.
    * Make commits of logical and atomic units. This means that the commit contains an entire
      fix and nothing but that fix (and any docs/tests/etc that go along with it).
    * Check for unnecessary whitespace with `git diff --check` before committing.
    * Make sure your commit messages are in the proper format. See example below.
        ```
        (PUP-1234) Make the example in CONTRIBUTING imperative and concrete

        Without this patch applied the example commit message in the CONTRIBUTING
        document is not a concrete example. This is a problem because the
        contributor is left to imagine what the commit message should look like
        based on a description rather than an example. This patch fixes the
        problem by making the example concrete and imperative.

        The first line is a real-life imperative statement with a ticket number
        from our issue tracker. The body describes the behavior without the patch,
        why this is a problem, and how the patch fixes the problem when applied.
        ```
    * Make sure you have added the necessary tests for your changes. See
      [the quickstart guide](https://github.com/puppetlabs/puppet/blob/master/docs/quickstart.md)
      if you need help getting started with this.
1. Sign the [Contributor License Agreement](http://links.puppet.com/cla).
1. Commit and push your tested code changes to your topic branch in your fork of the repo.
1. Submit a pull request to the parent repository.
1. Update the Jira ticket to indicate that you're ready for it to be reviewed.
    * Status: `Ready for Merge`.
    * Include a link to the pull request in the ticket.
    * If feedback is given then make sure to update and address the feedback. Pull requests
      may be closed if there is no response.


## Complete Contributor Guidelines

This document is streamlined to cover the common use case of the beginner friendly issues only.
It doesn't cover other edge cases, such as targeting a release branch, all-in-one vendor packaging,
or any other advanced use cases. Please see the complete [CONTRIBUTING.md](https://github.com/puppetlabs/.github/blob/master/CONTRIBUTING.md)
for more information.

