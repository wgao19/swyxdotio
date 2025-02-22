---
title: Best Practices in JavaScript Release Automation
slug: release-automation
category: Notes
begun: 2019-04-20
date: 2019-04-20
author: swyx
published: false
---

There is a step change in industry-standard knowledge when going from individual contributor to maintainer, whether working on open source projects or closed source company infrastructure. It is easy enough to fork, write code, and add PR, and it is intentionally easy to get started manually publishing releases. (This also helps keep the core infrastructure as tooling agnostic as possible, which increases its longevity.) However, a low barrier to entry and small set of enforced/required standards also makes it hard to keep up a high quality project.

Maintenance of a high quality project requires setting up systems to ensure quality ("[hold the line](https://mobile.twitter.com/sebmarkbage/status/1063585097545220096)") and automate duplicative tasks. Unfortunately, these are mostly set-and-forget tasks done by a small group of very busy, informally trained people, not all of whom agree on what to do, so the documentation for this is sparse.

I recently [asked about release automation](https://mobile.twitter.com/swyx/status/1118966159641067521) practices and got some great responses, and this will be my ongoing catalog of notes. I acknowledge and refer you to other resources at the bottom.

## Committing

_to be completed_

## Manual Publishing

What we want:

- well formatted
- autogenerated changelogs from commits
- releases to npm simultaneously tagged and published to github

How to do this:

- use [`commitizen`](https://npm.im/commitizen)
- use [`auto-changelog`](https://npm.im/auto-changelog)
  - put it in an npm hook so you run and add it every time
  - `"version": "auto-changelog -p --template keepachangelog && git add CHANGELOG.md"`
- use [`gh-release`](https://npm.im/gh-release)
  - put it in an npm hook to make sure you push tags too
  - `"prepublishOnly": "git push && git push --tags && gh-release"`

Other methods I need to explore:

- semantic-release
- https://github.com/intuit/auto
- https://egghead.io/lessons/javascript-how-to-write-a-javascript-library-automatically-running-tests-before-commits-with-ghooks
- https://github.com/algolia/shipjs
- Atlassian's [changesets tool](https://github.com/atlassian/changesets) cc [JessTelford](https://twitter.com/JessTelford/status/1179528676393672704)

## Automated Publishing

_to be completed_

## More Resources

- Kent C. Dodds: [How to write an Open Source JavaScript Library](https://egghead.io/courses/how-to-write-an-open-source-javascript-library) (dont worry it is a free egghead.io course)
