---
layout: post
nav-class: dark
categories: sam
title: Sam's Q3 2024 Update
author-id: sam
---

Here's an overview of some projects I have been working on the last few months.

### boostorg/release-tools

Adjusting publish_release.py script to stage windows executables for Tom Kent. During the first phase, they are not publicly downloadable, but then when published the files move to another folder.
Numerous fine-tuning fixes to publish_release.py during the boost release process. The file upload target is AWS S3, and from there the CDN origin servers download archives and serve the files via Fastly.
Revamping build_docs scripts. Add python venv to mac and windows. Support macos-14.
Briefly investigating docca - python issue that affected boost builds.
Deployed 24.04 version of docker image for the main boostorg/boost jobs. Fixed zip and 7z failures appearing on 24.04.

### Boost website boostorg/website-v2

Develop cost inventory spreadsheet of new infrastructure. Dealing with an outage ultimately traced back to redis -> django-health-check -> celery(bug). Frank Wiles from Revsys solved the celery puzzle, patched the Django configuration.

Wrote bootstrap scripts for local website development, that will install all prerequisites for local development in one script and then even launch docker-compose. Scripts for mac, windows, linux. Updated the corresponding documentation. It's equally feasible to go through the steps manually to see what's being installed and then launch docker-compose from the command-line, so there are multiple options.

Researched how to selectively purge the Fastly CDN cache. Implemented the k8s part. Brian coding the Django celery task.

### Mailman project

Revising runbook, steps to go-live in the future.
Incorporate Greg's changes to install a boost.io header on the mailing lists. Reduce and consolidate files. Create ansible deployment. Now temporarily removing customizations before deployment although they may be returned later.
Upgraded the OS on all mm3 test instances. Test newer OS version. Switched search engine to Xapian.
Submitted upstream pull requests (merged) which
- document an improved Xapian installation method
- further document how the core and web components interact in terms of the db.

### Slack

Discussing slackbot implementation with Kenneth. A slack inviter requires Business or Enterprise level tokens.

### wowbagger

Document and publish issues about problems on legacy web server.
Added to Kenneth's docker and docker-compose strategy for the original boost.org website to allow local development via docker-compose. Download boost archives so that environment is functional.
Collaborated with Rob to equip boost.org with Plausible analytics.

### Jenkins

Investigate/repair doc builds on mrdocs, http_proto.
Adjust doc builds beast, url.
Safe-CPP doc previews: pull requests. The master branch previews were already done, in Github actions. Added a step there, render the html upon commit.
Upgraded Jenkins executable and plugins.
Set up previews of boostlook. master/develop and PRs.

### JSON Benchmarks

After experimenting on a Hetzner server, switched JSON Benchmarks to a new Xeon processor from KnownHost. Intel core processors are aimed at the consumer market while Xeon is a server architecture and more consistent for benchmark tests. Replace Jenkins runner, cancel previous server.

### GHA

Debugging certain boost library jobs. Also, with the hosted runners, determined there was a systematic problem that the bootprocess was timing out too quickly. Adjust terraform settings and redeploy. Would be good to propose a PR upstream to terraform, the timeout is too fast.
Enable billing for math-cuda gpu tests.
Macminivault billing issues.
Resizing terraform runner Windows 2022, to add 10GB disk, and Pagefile (memory).

### Drone

Assist developers in debugging jobs.
Scripted docker image cleanup on drone instances. 
Installed a cron job to clear the autoscaler, due to the fact that occasionally jobs get stuck in pending mode preventing instances from scaling down.


