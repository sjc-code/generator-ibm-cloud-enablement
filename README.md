# IBM Cloud Enablement Generator

[![IBM Cloud powered][img-bluemix-powered]][url-bluemix]
[![Travis][img-travis-master]][url-travis-master]
[![Coveralls][img-coveralls-master]][url-coveralls-master]
[![Codacy][img-codacy]][url-codacy]
[![Version][img-version]][url-npm]
[![DownloadsMonthly][img-npm-downloads-monthly]][url-npm]
[![DownloadsTotal][img-npm-downloads-total]][url-npm]
[![License][img-license]][url-npm]
[![Conventional Commits](https://img.shields.io/badge/Conventional%20Commits-1.0.0-yellow.svg)](https://conventionalcommits.org)

[img-bluemix-powered]: https://img.shields.io/badge/bluemix-powered-blue.svg
[url-bluemix]: http://bluemix.net
[url-npm]: https://www.npmjs.com/package/generator-ibm-cloud-enablement
[img-license]: https://img.shields.io/npm/l/generator-ibm-cloud-enablement.svg
[img-version]: https://img.shields.io/npm/v/generator-ibm-cloud-enablement.svg
[img-npm-downloads-monthly]: https://img.shields.io/npm/dm/generator-ibm-cloud-enablement.svg
[img-npm-downloads-total]: https://img.shields.io/npm/dt/generator-ibm-cloud-enablement.svg

[img-travis-master]: https://travis-ci.org/ibm-developer/generator-ibm-cloud-enablement.svg?branch=master
[url-travis-master]: https://travis-ci.org/ibm-developer/generator-ibm-cloud-enablement/branches

[img-coveralls-master]: https://coveralls.io/repos/github/ibm-developer/generator-ibm-cloud-enablement/badge.svg
[url-coveralls-master]: https://coveralls.io/github/ibm-developer/generator-ibm-cloud-enablement

[img-codacy]: https://api.codacy.com/project/badge/Grade/a5893a4622094dc8920c8a372a8d3588?branch=master
[url-codacy]: https://www.codacy.com/app/ibm-developer/generator-ibm-cloud-enablement

Creates the files required to deploy projects to Kubernetes (using Helm Charts) and/or Cloud Foundry (using a generated manifest). Also, provides scripts to initiate IBM Cloud’s DevOps Toolchain.

## Pre-requisites

Install [Yeoman](http://yeoman.io)

```bash
npm install -g yo
```

## Installation

```bash
npm install -g generator-ibm-cloud-enablement
```

## Usage

```bash
yo ibm-cloud-enablement
```

Following command line arguments are supported:
* `--bluemix {stringified-json}` -  used by Scaffolder to supply project information from `pman`. You can also supply a local file containing compatible JSON object by using `--bluemix file:path/to/file.json`. Other options include `--bluemix='{"name":"<project-name>","backendPlatform":"<platform>"}'`
* `--storages {stringified-array}` - used to add storage deployment to helm charts
* `--isDeployableContainer` -  if true add `container` to `deploy-target` in `cli-config.yaml`
* `--nodeCFMinMemory` - used to defined a minimum requirement for node CF deployment. (e.g 384M)

## Artifacts

Here is a list of the files and folders you receive after executing the generator:  

File  | Purpose
---       | ---
Dockerfile | Configuration file for the run container
Dockerfile-tools | Configuration file for the tools container
Jenkinsfile | Groovy script used in conjunction with deploying to Cloud Foundry
chart/* | Folder containing all the Helm yaml files required to deploy to Kubernetes
cli-config.yml | Yaml file containing mappings for various commands, files, and settings, utilized by the cli commands
manifest.yml | Yaml file with configuration to deploy to Cloud Foundry

## Development Environment

Clone this repository and link it via npm

```bash
git clone https://github.com/ibm-developer/generator-ibm-cloud-enablement
cd generator-ibm-cloud-enablement
npm link
```

In a separate directory invoke the generator via

```bash
yo ibm-cloud-enablement 
```

## Testing

To run the unit tests

```
npm test
```

## Publishing Changes

In order to publish changes, you will need to fork the repository or branch off the `master` branch.

Make sure to follow the [conventional commit specification](https://conventionalcommits.org/) before contributing. To help you with commit a commit template is provide. Run `config.sh` to initialize the commit template to your `.git/config` or use [commitizen](https://www.npmjs.com/package/commitizen)

Once you are finished with your changes, run `npm test` to make sure all tests pass.

Do a pull request against `master`, make sure the build passes. A team member will review and merge your pull request.
Once merged to `master` an auto generated pull request will be created against master to update the changelog. Make sure that the CHANGELOG.md and the package.json is correct before merging the pull request. After the auto generated pull request has been merged to `master` the version will be bumped and published to Artifactory.
