Contribution Guideline
================================================================================

Chapter-01: Common Standards
--------------------------------------------------------------------------------

### Laravel Standards

Before we are getting started you should be aware that this is 
a software made for Laravel, hence we are following the common 
Laravel standards whenever we can. 

We assume that you already know how a [Laravel package] works and 
is structured, if not checkout [Laravel package development]. 
Alexey Mezenin has also written a must-read article about 
[Laravels best practices]. And if you haven't already heard of 
[PHP design patterns], you should definitely check them out too.

### Versioning Scheme

Laravel I18n follows [Semantic Versioning 2.0.0].

When referencing Laravel I18n from your application or package, 
you should always use a version constraint such as `^1.0`, 
since major releases do include breaking changes. However, 
we strive to always ensure you may update to a new major 
release in one day.

### Code Deprecations

From time to time, some classes and/or methods are deprecated; 
that happens when a feature implementation cannot be changed 
because of backward compatibility issues, but we still want to 
propose a "better" alternative. In that case, the old 
implementation can be deprecated.

Deprecations must only be introduced on the next minor version 
of the impacted source code. They can exceptionally be introduced 
on previous supported versions if they are critical.

A feature is marked as deprecated by adding a `@deprecated` 
PHPDoc to relevant classes, methods, properties, ...:

```php
/**
 * @deprecated since 1.0.0.
 */
```

The deprecation message must indicate the version in which the 
feature was deprecated, and whenever possible, how it was replaced:

```php
/**
 * @deprecated since 1.0.0, use alternative() instead.
 */
```

A deprecation must also be triggered to help people with the 
migration (uses [symfony/deprecation-contracts]):

```php
trigger_deprecation(
    'sirthxalot/laravel-i18n', '5.1', 
    'The "%s" class is deprecated, use "%s" instead.', 
    Deprecated::class, Replacement::class
);
```

### Coding Style

Laravel I18n follows the [PSR-2] coding standard and the [PSR-4] 
autoloading standard.

#### Laravel Pint

Don't worry if your code styling isn't perfect! [Laravel Pint]
will automatically merge any style fixes into the repository 
after pull requests are merged. This allows us to focus on the 
content of the contribution and not the code style.

### PHP Doc

PHP documentation blocks (DocBlocks) should follow [Laravels 
PHP Doc convention].

#### Since & Version

Version numbers should not be prefixed (<del>`v1.0.0`</del>) 
use the semantic versioning number e.g. `1.0.0`.

All internal methods must use the `@since` Doc block tag. It
indicates at which version the associated method became 
available. This value does not change after it has been defined.

All internal methods must use the `@version` Doc block tag after 
something has been changed. It indicates the current version of 
the method.

#### Exceptions

All internal methods must use the `@throws` Doc block tag, if 
an exception will be thrown. It indicates whether the associated 
element could throw a specific type of exception.

#### Event Dispatches

All internal methods should use the `@see` Doc block tag, in 
order to declare possible event dispatches.

#### ToDo

Some methods may perform an action like updating or creating 
something but will not be validated for example. Use the `@todo` 
Doc block tag to mark those elements. It indicates whether any 
development activity should still be executed on the associated 
element.

Chapter-02: Arrangements
--------------------------------------------------------------------------------

### Step-01: Check if work is not already in progress.

Before working on a change, check to see if someone else also 
raised the topic or maybe even started working on a [pull request] 
by [searching on GitHub] or use the [project board].

If you are unsure or if you have any questions during this entire 
process, please ask your questions on the `#ideas` category on 
[GitHub Discussions].

### Step-02: Report an issue and wait.

Next you should report an issue using the [issue tracker] and 
await for orders. Seriously you should not begin to code anything 
before you have any warranties that it will be merged into the 
final source code.

You will find a comment (from a maintainer) within the issue, 
that may confirm your request. Otherwise, you will get some 
explanations why we don't support your request.

### Step-03: Fork the source code.

[Fork] the source code, clone your fork, and configure the remotes:

```shell
# Clone your fork of the repo into the current directory
git clone https://github.com/<your-username>/laravel-i18n.git

# Navigate to the newly cloned directory
cd laravel-i18n/

# Assign the original repo to a remote called "upstream"
git remote add upstream https://github.com/sirthxalot/laravel-i18n.git
```

If you cloned a while ago, get the latest changes from upstream:

```shell
git checkout main
git pull upstream main
```

### Step-04: Run tests.

Now that you have installed Laravel I18n check if all test pass by 
running the following command:

```shell
composer test
```

### Step-05: Create a topic branch.

Each time you want to work on a PR for a bug or on an enhancement, 
create a topic branch:

```shell
git checkout -b BRANCH_NAME main
```

Or, if you want to provide a bug fix for the `2.3` branch, first 
track the remote `2.3` branch locally, than create a new branch 
off the `2.3` branch to work on the bug fix:

```shell
git checkout --track origin/2.3
git checkout -b BRANCH_NAME 2.3
```

> **Note**: Use a descriptive name for your branch (`issue_XXX` 
> where XXX is the ticket number is a good convention for bug fixes).

### Step-06: Work on your code.

You are now ready to work on the source code and achieve some 
amazing stuff. But keep in mind the following:

- All the code you are going to submit must be released under the MIT license;
- Add unit or feature tests to prove that everything works;
- Try hard to not break backward compatibility (if you must do so, try to provide 
  a compatibility layer to support the old way) -- PRs that break backward 
  compatibility have less chance to be merged;
- Do atomic and logically separate commits (use the power of `git rebase` to have 
  a clean and logical history);
- Never fix coding standards in some existing code as it makes the code review 
  more difficult;
- Write good commit messages: Start by a short subject line (the first line), 
  followed by a blank line and a more detailed description.

Chapter-03: Documentation
--------------------------------------------------------------------------------

The documentation is bundled with the source code which makes it 
available for offline reading and makes it easier to update it for 
you. It has been written in [Markdown] using [VuePress 2] as site 
generator.

Before you can use the documentation you must install its Node 
dependencies:

```shell
npm install
```

Next you can start a build-in webserver to serve the documentation 
on localhost:

```shell
npm run docs:dev
```

Chapter-04: Testing
--------------------------------------------------------------------------------

Whenever you write a new line of code, you also potentially add 
new bugs. To build better and more reliable code, you should test 
it. This is why [PHPUnit] and [Testbench] has been implemented - 
these frameworks assist you writing clean tests. Our testing suite 
is usually separated into the following parts:

- **Unit Tests**: are located within `tests/Unit/` directory. They ensure that 
  individual units of source code (e.g. a single class) behave as intended.
- **Feature Tests**: are located within the `tests/Feature/` directory. These 
  tests may check a larger portion of your code, including how several objects 
  interact with each other or even a full HTTP request to a JSON endpoint.
- **Test Cases**: are located within the `tests/` directory. They are meant to 
  group external behavior that can be reused for other tests and don't do any 
  assertions.

Chapter-05: Submit Pull Request
--------------------------------------------------------------------------------

### Step-01: Rebase your Pull Request.

Before submitting your PR, update your branch (needed if it takes 
you a while to finish your changes):

```shell
git checkout 2.x

git fetch upstream

git merge upstream/2.x

git checkout BRANCH_NAME

git rebase 2.x
```

> **Note**: Replace `2.x` with the branch you selected previously 
> (e.g. `2.3`) if you are working on a bug fix.

When doing the `rebase` command, you might have to fix merge 
conflicts. `git status` will show you the unmerged files. Resolve 
all the conflicts, then continue the rebase:

```shell
git add ... # add resolved files

git rebase --continue
```

Check that all tests still pass and push your branch remotely:

```shell
git push --force origin BRANCH_NAME
```

### Step-02: Open a Pull Request.

You can now [make a pull request] on the `sirthxalot/laravel-i18n` 
GitHub repository.

The default pull request description contains a table which you 
must fill in with the appropriate answers. This ensures that 
contributions may be reviewed without needless feedback loops and 
that your contributions can be included into Laravel I18n as quickly 
as possible.

<!-- -------------------------- that's all folks! -------------------------- -->

[psr-2]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-2-coding-style-guide.md
[psr-4]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-4-autoloader.md
[laravel pint]: https://laravel.com/docs/10.x/pint
[laravels php doc convention]: https://laravel.com/docs/10.x/contributions#phpdoc
[laravels best practices]: https://github.com/alexeymezenin/laravel-best-practices#contents
[php design patterns]: https://refactoring.guru/design-patterns/php
[laravel package]: https://laravel.com/docs/10.x/packages
[laravel package development]: https://laravelpackage.com/
[semantic versioning 2.0.0]: https://semver.org/
[symfony/deprecation-contracts]: https://github.com/symfony/deprecation-contracts
[fork]: https://docs.github.com/de/get-started/quickstart/fork-a-repo
[markdown]: https://v2.vuepress.vuejs.org/guide/markdown.html
[vuepress 2]: https://v2.vuepress.vuejs.org/
[testbench]: https://github.com/orchestral/testbench
[phpunit]: https://phpunit.de/
[pull request]: https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-pull-requests

[searching on github]: https://github.com/sirthxalot/laravel-i18n/issues?q=+is%3Aopen+
[github discussions]: https://github.com/sirthxalot/laravel-i18n/discussions/categories/ideas
[project board]: https://github.com/sirthxalot/laravel-i18n/projects
[issue tracker]: https://github.com/sirthxalot/laravel-i18n/issues
[make a pull request]: https://github.com/sirthxalot/laravel-i18n/compare
