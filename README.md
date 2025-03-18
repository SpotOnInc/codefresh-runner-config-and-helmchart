# Codefersh runners helm chart

[![codecov](https://codecov.io/gh/codefresh-io/venona/branch/release-1.0/graph/badge.svg?token=03h40zbvJs)](https://codecov.io/gh/codefresh-io/venona) [![Go Report Card](https://goreportcard.com/badge/github.com/codefresh-io/venona)](https://goreportcard.com/report/github.com/codefresh-io/venona)

* [venonactl](venonactl/README.md) - Codefresh installer of Kubernetes YAML's. [![Codefresh build status]( https://g.codefresh.io/api/badges/pipeline/codefresh-inc/codefresh-io%2Fvenona%2Fvenonactl-ci?type=cf-1)]( https://g.codefresh.io/public/accounts/codefresh-inc/pipelines/new/5c336db4c67fe44c098c9cd3)
* [venona](venona/README.md) - Codefresh runner process, [official docs](https://codefresh.io/docs/docs/administration/codefresh-runner/). [![Codefresh build status]( https://g.codefresh.io/api/badges/pipeline/codefresh-inc/codefresh-io%2Fvenona%2Fvenona-ci?type=cf-1&key=eyJhbGciOiJIUzI1NiJ9.NTY3MmQ4ZGViNjcyNGI2ZTM1OWFkZjYy.AN2wExsAsq7FseTbVxxWls8muNx_bBUnQWQVS8IgDTI)]( https://g.codefresh.io/pipelines/edit/new/builds?id=5edde99dcf40d573569eab9b&pipeline=venona-ci&projects=codefresh-io%2Fvenona&projectId=5c98d41cbd5b6f40758ee49c)

## Description

This is a slightly modified Codefresh runners helm chart that is being used to set up Codefresh runners on our Kubernetes KOPS corp. We added annotations to volume provisioner so it can use AWS role (via `kIAM`) to access AWS api and provision EBSes.

The major version our setup is based on is `1` while at the time of writing latest one is `6`.

## Why such an old piece of software is still around?

At the time of adoption Codefresh'es `venona` (that's a name of software that sets up Codefresh runners on private Kubernetes) it was very messy with its versioning and everything was called `release-1.0` (but it worked). We needed just one more feature to get it work properly which was to add an annotation to volume provisioner pod. We made a fork (this repository), [a PR with new feature](https://github.com/codefresh-io/venona/pull/311). Later we learned it was included in new major release (`2`). We even had a [plan to upgrade (Jira ticket)](https://spotonteam.atlassian.net/browse/DEV-5316) but that never happened due to successful Github Actions adoption.


