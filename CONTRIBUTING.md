# How to Contribute

## Reporting Issues

Should you run into other issues with the project, please file an [issue][issue]. When filing issues a repo case running against the latest version of the code is appreciated. A [jsfiddle template][jsfiddle] is available for this purpose. As new versions are released this link will be updated to point to a fiddle template with the latest version.

Failing test pull requests are welcomed for issues that can easily be reproduced and this also helps ensure that your issue won't regress in the future once it's fixed.

## Pull Requests

We also accept [pull requests][pull-request]!

Generally we like to see pull requests that
- Maintain the existing code style
- Are focused on a single change (i.e. avoid large refactoring or style adjustments in untouched code if not the primary goal of the pull request)
- Have [good commit messages](http://tbaggery.com/2008/04/19/a-note-about-git-commit-messages.html)
- Have tests
- Don't significantly decrease the current code coverage (see coverage/lcov-report/index.html)

## Building

To build Handlebars.js you'll need a few things installed.

* Node.js
* [Grunt](http://gruntjs.com/getting-started)

Project dependencies may be installed via `npm install`.

To build Handlebars.js from scratch, you'll want to run `grunt`
in the root of the project. That will build Handlebars and output the
results to the dist/ folder. To re-run tests, run `grunt test` or `npm test`.
You can also run our set of benchmarks with `grunt bench`.

The `grunt dev` implements watching for tests and allows for in browser testing at `http://localhost:9999/spec/`.

If you notice any problems, please report them to the GitHub issue tracker at
[http://github.com/wycats/handlebars.js/issues](http://github.com/wycats/handlebars.js/issues).

## Ember testing

The current ember distribution should be tested as part of the handlebars release process. This requires building the `handlebars-source` gem locally and then executing the ember test script.

```sh
grunt build release
export HANDLEBARS_PATH=`pwd`

cd $emberRepoDir
bundle exec rake clean
bundle exec rake test
```

## Releasing

Handlebars utilizes the [release yeoman generator][generator-release] to perform most release tasks.

A full release may be completed with the following:

```
yo release
npm publish
yo release:publish cdnjs handlebars.js dist/cdnjs/
yo release:publish components handlebars.js dist/components/

cd dist/components/
gem build handlebars-source.gemspec
gem push handlebars-source-*.gem
```

After this point the handlebars site needs to be updated to point to the new version numbers. The jsfiddle link should be updated to point to the most recent distribution for all instances in our documentation.

[generator-release]: https://github.com/walmartlabs/generator-release
[pull-request]: https://github.com/wycats/handlebars.js/pull/new/master
[issue]: https://github.com/wycats/handlebars.js/issues/new
[jsfiddle]: http://jsfiddle.net/9D88g/11/