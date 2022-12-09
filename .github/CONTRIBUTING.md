Contributing to $PROJECT_TITLE$
================================================================================

Introduction
--------------------------------------------------------------------------------

♥ $PROJECT_TITLE$ and want to get involved? Thanks! We're actively
looking for folks interested in helping out and there are plenty
of ways you can help!

Please take a moment to review this document to make the contribution 
process easy and effective for everyone involved.

Following these guidelines helps to communicate that you respect
the time of the developers managing and developing this open-source
project. In return, they should reciprocate that respect in 
addressing your issue or assessing patches and features.

> **Note**  
> You may begin with our [code of conduct] in order to understand some rules of expected behaviour.

Discussions & Support Questions
--------------------------------------------------------------------------------

Please do not use the issue tracker for personal support requests 
or other discussion topics. We use [GitHub Discussion] instead.

Issue Tracking
--------------------------------------------------------------------------------

The [issue tracker] is the preferred channel for bug reports, 
features requests and submitting pull requests, but please 
respect the following restrictions:

- Please **do not** use the issue tracker for personal support requests 
  (use [GitHub Discussion]).

- Please **do not** derail or troll issues. Keep the discussion on topic 
  and respect the opinions of others.

- Please **do not** open issues or pull requests regarding third-party code 
  (open them in their respective repositories).

Compiled Assets
--------------------------------------------------------------------------------

If you are submitting a change that will affect a compiled file, 
such as most of the files in `resources/css` or `resources/js` 
within the repository, do not commit the compiled files. Due to 
their large size, they cannot realistically be reviewed by a 
maintainer. This could be exploited as a way to inject malicious 
code into the software. In order to defensively prevent this, 
all compiled files will be generated and committed by the maintainers.

Coding Standards
--------------------------------------------------------------------------------

This project follows the **[PSR-2] coding standard** and the 
**[PSR-4] autoloading standard**.

### StyleCI

Don't worry if your code styling isn't perfect! [StyleCI] will 
automatically merge any style fixes into the repository after pull 
requests are merged. This allows us to focus on the content of the 
contribution and not the code style.

### EditorConfig

[EditorConfig] helps maintain consistent coding styles for multiple 
developers working on the same project across various editors and 
IDEs. The EditorConfig project consists of a file format for defining 
coding styles and a collection of text editor plugins that enable 
editors to read the file format and adhere to defined styles. 
EditorConfig files are easily readable and they work nicely with 
version control systems. Checkout the `.editorconfig` file.

### Best Practices & Naming Convention

If you would like to dig in deeper - then you may also check out 
[Laravel's best practices by alexeymezenin].

Documentation
--------------------------------------------------------------------------------

This documentation is bundled with the project which makes it 
available for offline reading and makes it easier to update it 
for you.

You must update or extend the documentation if you make significant 
changes. But don't worry you will find instructions within the 
ticket - a maintainer will instruct you.

### File Structure

All files can be found within the `docs/` directory. It has been 
written in [Markdown syntax] and will be compiled by [VuePress].

VuePress requires [Node.js] ([NPM]) and/or [Yarn] to build the site 
for you. Please ensure that you are using the *latest version*.

### Run Documentation

Please follow these instructions to serve the documentation on 
a local server:

#### Step 01: Install NPM Dependencies

Install all Node dependencies defined within the `package.json` 
file by running the following command within your terminal:

```bash
npm install
```

> **Note**  
> This needs to be done only once and it will install all dependencies into the `node_modules/` directory

#### Step 02: Run Server

Next let's start a [build-in server] to serve the site:

```bash
npm run docs:serve
```

> **Note**  
> The doumentation is usally available under: [localhost:8080](http://localhost:8080) after serving it.

Testing
--------------------------------------------------------------------------------

Whenever you write a new line of code, you also potentially add 
new bugs. To build better and more reliable applications, you 
should test your code using both functional and unit tests.

- **Unit Tests**: These tests ensure that individual units of source code 
  (e.g. a single class) behave as intended. Located in `tests/Unit/` directory.

- **Feature Tests**: Feature tests may test a larger portion of your code, 
  including how several objects interact with each other or even a full 
  HTTP request to a JSON endpoint. Generally, most of your tests should 
  be feature tests. These types of tests provide the most confidence that 
  your system as a whole is functioning as intended. Located within the 
  `tests/Feature/` directory.

- **Test Cases**: Test cases can be used to group external behavior that can 
  be reused for other tests. More about test cases can be found within 
  the [PHPUnit documentation][PHPUnit Doc Test Cases]. Files are located 
  within the `tests/` directory.

### Testing Frameworks

$PROJECT_TITLE$ integrates with an independent library called 
**[PHPUnit]** to give you a rich testing framework. This article 
won't cover PHPUnit itself, which has its own excellent [documentation][PHPUnit Doc].

We also use **[Testbench]** to cover more Laravel related test scenarios.

### Install Composer Dependencies

Before you can create your first test. You will need to install 
the [Composer] dependencies (defined within the `composer.json` 
file) by running the following command:

```bash
composer install
```

### Run Tests

After installing the dependencies you can simply run the tests by 
executing the following command:

```bash
composer test
```

This command automatically runs the test suite. Each test is a PHP 
class ending with "Test" (e.g. `BlogControllerTest`) that lives 
in the `tests/` directory.

### Configuration & Env Variables

PHPUnit is configured by the `phpunit.xml.dist` file. The default 
configuration provided by us will be enough in most cases. Read 
the [PHPUnit documentation][PHPUnit Doc Config] to discover all 
possible configuration options (e.g. to enable code coverage or 
to split your test into multiple "test suites").

General Workflow
--------------------------------------------------------------------------------

1. Start a [GitHub Discussion][💡 Ideas] and tell us about your idea.

2. Open a [new issue][new issue] and fill-in our premade templates.

3. [Fork] the project, clone your fork, and configure the remotes.

   ```bash
   # Clone your fork of the repo into the current directory
   git clone https://github.com/<your-username>/$project-name$.git
   # Navigate to the newly cloned directory
   cd $project-name$/
   # Assign the original repo to a remote called "upstream"
   git remote add upstream https://github.com/$project-user$/$project-name$.git
   ```

   > **Note**  
   > If you cloned a while ago, get the latest changes from upstream:
   > ```bash
   > git checkout main
   > git pull upstream main
   > ```

4. Create a new topic branch to contain your feature, change, or fix:

   ```bash
   git checkout -b <topic-branch-name>
   ```

   A few example branch names:
   - feature-xyz
   - patch-xyz
   - refactor-xyz
   - fix-xyz
   - documentation-xyz  

5. Commit your changes in logical chunks. Please adhere to these 
   [git commit message guidelines] or your code is unlikely being 
   merged into the main project. Use Git's [interactive rebase] 
   feature to tidy up your commits before making them public.

6. Locally merge (or rebase) the upstream development branch into 
   your topic branch:

   ```bash
   git pull [--rebase] upstream main
   ```

7. Push your topic branch up to your fork:

   ```bash
   git push origin <topic-branch-name>
   ```

8. Open a [Pull Request] with a clear title and description.     

<!--                            that's all folks!                            -->

[code of conduct]: ./CODE_OF_CONDUCT.md#contributor-covenant-code-of-conduct
[github discussion]: ./../../../discussions/
[issue tracker]: ./../../../issues/
[new issue]: ./../../../issues/new/choose/

[fork]: https://docs.github.com/de/get-started/quickstart/fork-a-repo
[git commit message guidelines]: https://tbaggery.com/2008/04/19/a-note-about-git-commit-messages.html
[interactive rebase]: https://help.github.com/articles/about-git-rebase/
[pull request]: https://help.github.com/articles/using-pull-requests/
[psr-2]: https://github.com/php-fig/fig-standards/blob/master/accepted/psr-2-coding-style-guide.md
[psr-4]: https://github.com/php-fig/fig-standards/blob/master/accepted/psr-4-autoloader.md

[styleci]: https://styleci.io
[laravel's best practices by alexeymezenin]: https://github.com/alexeymezenin/laravel-best-practices#contents
[markdown syntax]: https://vuepress.vuejs.org/guide/markdown.html
[vuepress]: https://vuepress.vuejs.org/
[node.js]: https://nodejs.org/en/
[npm]: https://www.npmjs.com/
[yarn]: https://yarnpkg.com/
[build-in server]: https://vuepress.vuejs.org/guide/#how-it-works
[phpunit]: https://phpunit.de/
[phpunit doc]: https://phpunit.de/documentation.html
[testbench]: https://packages.tools/testbench/getting-started/introduction.html
[composer]: https://getcomposer.org
[phpunit doc config]: https://phpunit.readthedocs.io/en/9.5/configuration.html
[phpunit doc test cases]: https://phpunit.readthedocs.io/en/9.5/writing-tests-for-phpunit.html
[editorconfig]: https://editorconfig.org/
