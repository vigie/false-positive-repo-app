# FalsePositiveRepoApp

This repo exists solely to illustrate the Angular CLI issue
https://github.com/angular/angular-cli/issues/23751.

There are only 2 relevant commits - the initial commit generated by
the latest Angular CLI `ng new` command and then the next one that

1. Makes a syntax error in `app.component.spec.ts`
2. Adds the following property to `karma.conf.js`: 
   * `failOnEmptyTestSuite: false`

## To Reproduce the False Positive Test Run Issue:

* Clone this repo
* `npm ci`
* `npm test -- --watch=false`
* `echo $?`

Observe that the exit code is `0`. This would allow changesets
containing syntax errors or broken tests to continue down a 
CICD pipeline.

Note that prior to Angular CLI v13.2.3 the exit code
in this exact scenario was non-zero.