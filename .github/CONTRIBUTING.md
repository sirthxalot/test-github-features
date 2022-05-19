Contribution Guide
================================================================================

♥ Laravel Winterfell and want to get involved? Thanks! We're actively
looking for folks interested in helping out and there are plenty
of ways you can help!

Please take a moment to review this document in order to make the
contribution process easy and effective for everyone involved.

Following these guidelines helps to communicate that you respect
the time of the developers managing and developing this open source
project. In return, they should reciprocate that respect in addressing
your issue or assessing patches and features.

You may begin with our [Code of Conduct] in order to understand
some rules of expected behaviour.

Fundamental Terminology
--------------------------------------------------------------------------------

### Semantic Versioning

We are following [Semantic Versioning]. This means that the version
numbers are build in a current way:

1. MAJOR version when you make incompatible API changes,
2. MINOR version when you add functionality in a backwards compatible manner, and
3. PATCH version when you make backwards compatible bug fixes.

*Additional labels for pre-release and build metadata are available
as extensions to the MAJOR.MINOR.PATCH format.*

You should always use a version constraint such as `^1.0`, since
major releases do include breaking changes. However, we strive to
always ensure you may update to a new major release.

### Backward Compatibility

Ensuring smooth upgrades of your projects is our first priority.
That's where the backward compatibility comes into play. You
probably recognize this strategy as [Semantic Versioning]. In
short, Semantic Versioning means that only major releases
(such as 5.0, 6.0 etc.) are allowed to break backward compatibility.
Minor releases (such as 5.1, 5.2 etc.) may introduce new features,
but must do so without breaking the existing API of that release branch.

However, backward compatibility comes in many different flavors.
In fact, almost every change that we make can potentially break an
application. For example, if we add a new method to a class, this
will break an application which extended this class and added the
same method, but with a different method signature.

Also, not every BC break has the same impact on application code.
While some BC breaks require you to make significant changes to
your classes or your architecture, others are fixed by changing
the name of a method.

### Bug

A bug is a demonstrable problem that is caused by the code in the
repository. A bug may produce an incorrect or unexpected result,
or to behave in unintended ways. This may affect your system from
minimal hickups to critical errors where the system may totally
shut down. Almost always you can declare a bug fix as a patch.

### Code Deprecations

From time to time, some classes and/or methods are being declared
as deprecated; that happens when a feature implementation cannot
be changed because of backward compatibility issues, but we still
want to propose a "better" alternative. In that case, the old
implementation can be deprecated.

Deprecations must only be introduced on the next minor version of
the impacted component (or bundle, or bridge, or contract). They
can exceptionally be introduced on previous supported versions if
they are critical.

### Feature / Enhancement

A feature is new functionality that has been added to the API.
The keyword is new, this means that you can now do something
that was not possible before. Often new features don't break the
backward compatibility which means that they can be declared as
minors.

Enhancements on the other hand improve a current implementation
of the API. So they often affect the code in a way that makes it
backward incompatible. If that's the case a new major release
must be declared (depending on its gravity).

### Refactor

A refactor needs to be done if the code needs to be optimized.
Often refactors are used in order to increase the performance,
or in order to make the code easier to read. As long as these
changes don't break the backward compatibility than they can
be declared as patches.

Support Questions
--------------------------------------------------------------------------------

The issue trackers is not intended to provide help or support.
Use [GitHub Discussions] instead. And don't forget - you can do
more than just ask the community for help. You can also share your
ideas, show some examples or make a quick survey. Especially if
you would like to open an issue you should always consider
starting a discussion and ask the community or maintainer first.

Issue Tracking
--------------------------------------------------------------------------------

The [issue tracker] is the preferred channel for bug reports,
features requests and submitting pull requests, but please
respect the following restrictions:

- Please **do not** derail or troll issues. Keep the discussion on topic and respect the opinions of others.

- Please **do not** open issues or pull requests regarding third party code (open them in their respective repositories).

### Labels

Listed below you will find some labels that may be assigned to your issue:

LABEL | DESCRIPTION                                                                       | COLOR
:------- |:----------------------------------------------------------------------------------| :--------
⏰ critical | Needs to be handled with hight priorization (hotfix)                                       | #46413F
🩸 bug | Something is causing trouble                                                      | #cc4b37
🔥 feature | A shiny new feature is comming                                                    | #3adb76
🚧 refactor | Source code needs to be optmized                                                  | #FBCA04
📙 documentation | Improvements or additions to documentation                                        | #0075ca
🚨 bc break | The API will be affected to break the backward compatibility                      | #E21C89
🚨 deprecation | This causes me to make some deprecations                                          | #E21C89
🎅 todo | This issue will be solved soon...                                                 | #FEFEFE
💦 wip | Hang in there - work is in progress...                                            | #2C8CE9
👑 solved | The issue has been solved and is ready for take off...                            | #0E8A16
⛑️ failed | Somehow the job couldn't be solved completly...                                   | #ff0025
👀 released | Fix or improvement is available know!                                             | #0E8A16
☠️ wontfix | This will not be worked on...                                                     | #ff0025
❄️ feature freeze | Next release cycle begins (no new features allowed)                               | #FEFEFE
🦸 CAN YOU HELP ME PLEASE? | I need external help in order to solve this issue. Feel free to assist me here!!! | #10FDF1
duplicate | This issue or pull request already exists                                         | #000000
feedback | Need further details please answer my comment                                     | #FEFEFE
missing details | Something is missing here                                                         | #FEFEFE

Version Control (Git)
--------------------------------------------------------------------------------

> Start with the excellent and free [ProGit book] & [GitHub Git Guides].

### Setup Git

Set up your user information with your real name and a working email address:

```
git config --global user.name "«your name»"
git config --global user.email «you@example.com»
```

> **Windows Users**:
> When installing Git, the installer will ask what to do with line endings,
> and suggests replacing all LF with CRLF. This is the wrong setting if you
> wish to contribute! Selecting the as-is method is your best choice, as Git
> will convert your line feeds to the ones in the repository. If you have
> already installed Git, you can check the value of this setting by typing:
> ```
> git config core.autocrlf
> ```
> This will return either "false", "input" or "true"; "true" and "false"
> being the wrong values. Change it to "input" by typing:
> ```
> git config --global core.autocrlf input
> ```
> *Replace --global by --local if you want to set it only for the active repository*

### Git Workflow

Listed below you will find the branches wich builds the foundation
of the workflow:

Branch Name | Description
:---------- |:--------------------------------------------
`main` | Stores the official release history
`v1.x`, `v2.x`... | Starts the next major release cycle

And here you will find our topic branches which can be merged into
the `main` or release branch later on:

<a href="#" id="topic-branches"></a>

Branch Name | Description                             | Example
:---------- |:----------------------------------------| :------
`documentation/` | Branch for solving documentation issues | `documentation/«issue nr.»-«your-title»` <br /> `documentation/1-your-title`
`feature/` | Branch for new features                 | `feature/«issue nr.»-«your-title»` <br /> `feature/1-your-title`
`fix/` | Branch for bug fixes                    | `fix/«issue nr.»-«your-title»` <br /> `fix/1-your-title`
`refactor/` | Branch for code opitmizations           | `refactor/«issue nr.»-«your-title»` <br /> `refactor/1-your-title`

### Git Tags / Releases

[Releases] are based on [Git tags], which mark a specific point
in your repository's history. A tag date may be different than a
release date since they can be created at different times. Releases
will be published by the maintainer. Every release will be labeled
with the full version number e.g. `v1.0.0`, `v1.0.1`... and contains
a note about the release.

EditorConfig
--------------------------------------------------------------------------------

[EditorConfig] helps maintain consistent coding styles for multiple
developers working on the same project across various editors and
IDEs. The EditorConfig project consists of a file format for
defining coding styles and a collection of text editor plugins
that enable editors to read the file format and adhere to defined
styles.

Please take a look at our `.editorconfig` file.

Coding Standards
--------------------------------------------------------------------------------

Please follow the [PSR-2] coding standard and the [PSR-4]
autoloading standard.

And don't panic if your code styling isn't perfect! [StyleCI]
will automatically merge any style fixes into the repository after
pull requests are merged. This allows us to focus on the content
of the contribution and not the code style.

### Best Practices

At this point I would like to mention [alexeymezenin/laravel-best-practices],
he wrote a very good example of how code should be implemented
including [our naming convention]. And if you are looking for
common solutions using PHP patterns I highly recommend visiting:
https://refactoring.guru/design-patterns/php.

### Documentation Blocks

Below is an example of a valid documentation block. Note that the `@param`
attribute is followed by two spaces, the argument type, two more spaces,
and finally the variable name:

```php
/**
 * Register a binding with the container.
 *
 * @since  1.0.0
 * @author Alexander Bösch <sta.contribution@gmail.com>
 * @param  string|array  $abstract
 * @param  \Closure|string|null  $concrete
 * @param  bool  $shared
 * @return void
 *
 * @throws \Exception
 */
public function bind($abstract, $concrete = null, $shared = false)
{
    //
}
```

However, PHP configuration files should use another approach:

```php
return [

    /*
    |--------------------------------------------------------------------------
    | Default Cache Store
    |--------------------------------------------------------------------------
    |
    | This option controls the default cache connection that gets used while
    | using this caching library. This connection is used when another is
    | not explicitly specified when executing a given caching function.
    |
    */

    'default' => env('CACHE_DRIVER', 'file'),

];
```

Compiled Assets
--------------------------------------------------------------------------------

If you are submitting a change that will affect a compiled file,
such as most of the files in `resources/css` or `resources/js`
directory, do not commit the compiled files. Due to their large
size, they cannot realistically be reviewed by a maintainer. This
could be exploited as a way to inject malicious code into the
software. In order to defensively prevent this, all compiled files
will be generated and committed by Laravel Winterfell maintainers.

Documentation
--------------------------------------------------------------------------------

The documentation is bundled with the project which makes it available
for offline reading and provides a simple way for you to update it. It
is written in [Markdown] and build by [Vuepress]. Whenever you make a
significant change that needs to be mentioned within the documentation
I hope for your assist.

If you make a pull request you should always update the documentation
in order to avoid that your request may be denied temporarily and
forces a so-called long distance runner.

Speaking about issues. If you open a documentation issue don't think
that these changes will be implemented directly, since its coupled
with the source code. We usually collect those issues and integrate
them during a patch or minor release in order to avoid disruptions.

By the way: the documentation files can be found within the `docs/`
directory.

### Step-01: Install Dependencies

In order to serve the documentation locally you must begin to
install the [NodeJS] dependencies defined within `package.json`
file. Use [NPM] or [Yarn] in order to install them:

```
npm install
```

### Step-02: Start Server

Use the build-in webserver in order to server the documentation
by executing the following command:

```
npm run docs:serve
```

You should find the URL in your terminal. The default URL is set
to: http://localhost:8080

Testing
--------------------------------------------------------------------------------

Laravel Winterfell is built with testing in mind. In fact, support
for testing with [PHPUnit] is included out of the box and a
`phpunit.xml.dist` file is already set up for you. The software
also ships with convenient helper methods that allow you to
expressively test your code. You can use the following
implementations in order to create tests:

- [PHPUnit]
- [Orchestral's Testbench]

By default, our `tests/` directory contains two directories:
`Feature` and `Unit`.

**Unit tests** are tests that focus on a very small, isolated
portion of your code. In fact, most unit tests probably focus on
a single method. Tests within your "Unit" test directory do not
boot the Laravel framework and therefore are unable to access the
database or other framework services.

**Feature tests** may test a larger portion of your code, including
how several objects interact with each other or even a full HTTP
request to a JSON endpoint.

Generally, most of your tests should be feature tests. These types
of tests provide the most confidence that your system as a whole
is functioning as intended.

### Step-01: Install Dependencies

Use [Composer] in order to install the dependencies defined within
the `composer.json` file:

```
composer install
```

### Step-02: Run Tests

And again you can use Composer to run the tests:

```
composer test
```

Or execute it directly from the vendor directory:

```
./vendor/bin/phpunit
```

Pull Request
--------------------------------------------------------------------------------

[Pull requests] let you tell others about changes you've pushed to
a branch in a repository on GitHub. Once a pull request is opened,
you can discuss and review the potential changes with collaborators
and add follow-up commits before your changes are merged into the
base branch.

As you can see: good pull requests - patches, improvements, new
features - are a fantastic help. As long as they remain focused
in scope and avoid containing unrelated commits.

### Step-01: Start a GitHub Discussion

[Please ask first] before embarking on any significant pull request
(e.g. implementing features, refactoring code, porting to a
different language), otherwise you risk spending a lot of time
working on something that the project's developers might not want
to merge into the project.

### Step-02: Open an Issue

After a quick discussion you may open a new ticket by using our  
[issue tracker].

### Step-03: Creating a PR

Adhering to the following process is the best way to get your work
included in the project:

1. [Fork] the project, clone your fork, and configure the remotes:
   ```
   # Clone your fork of the repo into the current directory
   git clone https://github.com/«your-username»/laravel-winterfell.git
   
   # Navigate to the newly cloned directory
   cd laravel-winterfell
   
   # Assign the original repo to a remote called "upstream"
   git remote add upstream https://github.com/sirthxalot/laravel-winterfell.git 
   ```

2. If you cloned a while ago, get the latest changes from upstream:
   ```
   git checkout main
   git pull upstream main
   ```

3. Create a new [topic branch](#topic-branches) (off the main
   project development branch) to contain your feature, change,
   or fix:
   ```
   git checkout -b «topic-branch-name»
   ```

4. Commit your changes in logical chunks. Please adhere to these
   [git commit message guidelines] or your code is unlikely be
   merged into the main project. Use Git's [interactive rebase]
   feature to tidy up your commits before making them public.

5. Locally merge (or rebase) the upstream development branch into
   your topic branch:
   ```
   git pull [--rebase] upstream main
   ```

6. Push your topic branch up to your fork:
   ```
   git push origin «topic-branch-name»
   ```

7. [Open a pull request] with a clear title and description.

> **IMPORTANT**: By submitting a patch, you agree to allow the project
> owners to license your work under the terms of the [MIT License].

--------------------------------------------------------------------------------

> ### That's it Folks!
> Thanks for standing by and have a very nice day!
>
> Sincerely  
> Alexander Bösch ([sirthxalot](<sta.contribution@gmail.com>))

<!-- some links & references... -->

[code of conduct]: ./CODE_OF_CONDUCT.md
[mit license]: ./../LICENSE.md

[interactive rebase]: https://docs.github.com/en/get-started/using-git/about-git-rebase
[git commit message guidelines]: https://tbaggery.com/2008/04/19/a-note-about-git-commit-messages.html
[gitflow workflow]: https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow
[semantic versioning]: https://semver.org/
[progit book]: https://git-scm.com/book
[github git guides]: https://github.com/git-guides
[PSR-2]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-2-coding-style-guide.md
[PSR-4]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-4-autoloader.md
[styleci]: https://styleci.io/
[alexeymezenin/laravel-best-practices]: https://github.com/alexeymezenin/laravel-best-practices
[our naming convention]: https://github.com/alexeymezenin/laravel-best-practices#follow-laravel-naming-conventions
[markdown]: https://vuepress.vuejs.org/guide/markdown.html#markdown-extensions
[vuepress]: https://vuepress.vuejs.org/
[phpunit]: https://phpunit.readthedocs.io/en/9.5/
[composer]: https://getcomposer.org/
[editorconfig]: https://editorconfig.org/
[nodejs]: https://nodejs.org/en/
[npm]: https://www.npmjs.com/
[yarn]: https://yarnpkg.com/
[pull requests]: https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-pull-requests
[please ask first]: https://github.com/sirthxalot/laravel-winterfell/discussions/categories/ideas
[fork]: https://docs.github.com/en/get-started/quickstart/fork-a-repo
[open a pull request]: https://github.com/sirthxalot/laravel-winterfell/compare
[github discussions]: https://github.com/sirthxalot/laravel-winterfell/discussions
[issue tracker]: https://github.com/sirthxalot/laravel-winterfell/issues
[orchestral's testbench]: https://packages.tools/testbench/getting-started/introduction.html#installation
[releases]: https://docs.github.com/en/repositories/releasing-projects-on-github/about-releases
[git tags]: https://git-scm.com/book/en/Git-Basics-Tagging
