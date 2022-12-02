# Contributing to $PROJECT_TITLE$

## Introduction

♥ $PROJECT_TITLE$ and want to get involved? Thanks! We're actively
looking for folks interested in helping out and there are plenty
of ways you can help!

Please take a moment to review this document in order to make the
contribution process easy and effective for everyone involved.

Following these guidelines helps to communicate that you respect
the time of the developers managing and developing this open source
project. In return, they should reciprocate that respect in addressing
your issue or assessing patches and features.

> **Note**  
> You may begin with our [Code of Conduct] in order to understand some rules of expected behaviour.

## Discussions & Support Questions

Please do not use the issue tracker for personal support requests 
or other discussions topics. We use [Github Discussion] instead.

<a name="discussion-categories"></a>
Choose a category that fits your request:

- **[📣 Announcements]**: Updates from maintainers;
- **[💬 General]**: Chat about anything and everything here;
- **[💡 Ideas]**: Share ideas for new features, fixes or patches;
- **[🗳️ Polls]**: Take a vote from the community;
- **[🙏 Question & Answer]**: Ask the community for help;
- **[🙌 Show and Tell]**: Show off something you've made.

## Issue Tracking

The [issue tracker] is the preferred channel for bug reports, features requests and submitting pull requests, but please respect the following restrictions:

- Please **do not** use the issue tracker for personal support requests (use [Github Discussion]).

- Please **do not** derail or troll issues. Keep the discussion on topic and respect the opinions of others.

- Please **do not** open issues or pull requests regarding third party code (open them in their respective repositories).

> **Warning**  
> **[Please ask first][💡 Ideas]** before embarking on any significant pull request 
> (e.g. implementing features, refactoring code, porting to a different language), 
> otherwise you risk spending a lot of time working on something that the project's 
> developers might not want to merge into the project.

## Coding Standards

This project follows the [PSR-2] coding standard and the [PSR-4] autoloading standard.

More coding tipps can be found at [Laravel's best pracites by alexeymezenin].

> **Note**  
> Don't worry if your code styling isn't perfect! [StyleCI] will automatically merge any style fixes into the repository after pull requests are merged. This allows us to focus on the content of the contribution and not the code style.

### Avoid Compiled Assets

If you are submitting a change that will affect a compiled file, such as most of the files in `resources/css` or `resources/js` within the repository, do not commit the compiled files. Due to their large size, they cannot realistically be reviewed by a maintainer. This could be exploited as a way to inject malicious code into the software. In order to defensively prevent this, all compiled files will be generated and committed by the maintainers.

## Workflow

1. Start a [Github Discussion][💡 Ideas] and tell us about your idea.
2. Open a [new ticket][new issue] and fill in the premade templates.
3. [Fork] the project, clone your fork, and configure the remotes.
   ```
   # Clone your fork of the repo into the current directory
   git clone https://github.com/<your-username>/$project-name$.git
   # Navigate to the newly cloned directory
   cd $project-name$/
   # Assign the original repo to a remote called "upstream"
   git remote add upstream https://github.com/$project-user$/$project-name$.git
   ```
   > **Note**  
   > If you cloned a while ago, get the latest changes from upstream:
   > ```
   > git checkout main
   > git pull upstream main
   > ```
4. Create a new topic branch to contain your feature, change, or fix:
   ```
   git checkout -b <topic-branch-name>
   ```
   A few example branch names:
   - feature-xyz
   - patch-xyz
   - refactor-xyz
   - fix-xyz
   - documentation-xyz  
5. Commit your changes in logical chunks. Please adhere to these [git commit
   message guidelines]
   or your code is unlikely be merged into the main project. Use Git's
   [interactive rebase]
   feature to tidy up your commits before making them public.
6. Locally merge (or rebase) the upstream development branch into your topic branch:

   ```bash
   git pull [--rebase] upstream main
   ```
7. Push your topic branch up to your fork:

   ```bash
   git push origin <topic-branch-name>
   ```
8. Open a [Pull Request] with a clear title and description.     

[code of conduct]:              ./CODE_OF_CONDUCT.md
[github discussion]:            PROJECT_URL$/discussions/
[📣 Announcements]:         $PROJECT_URL$/discussions/categories/announcements
[💬 General]:     $PROJECT_URL$/discussions/categories/general
[💡 Ideas]:     $PROJECT_URL$/discussions/categories/ideas
[🗳️ Polls]: $PROJECT_URL$/discussions/categories/polls
[🙏 Question & Answer]: $PROJECT_URL$/discussions/categories/q-a
[🙌 Show and Tell]: $PROJECT_URL$/discussions/categories/show-and-tell
[issue tracker]: $PROJECT_URL$/issues/
[new issue]: $PROJECT_URL$/issues/new/choose/
[fork]: https://docs.github.com/de/get-started/quickstart/fork-a-repo
[git commit
   message guidelines]: https://tbaggery.com/2008/04/19/a-note-about-git-commit-messages.html
[interactive rebase]: https://help.github.com/articles/about-git-rebase/
[Pull Request]: https://help.github.com/articles/using-pull-requests/
[psr-2]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-2-coding-style-guide.md
[psr-4]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-4-autoloader.md
[styleci]: https://styleci.io
[Laravel's best pracites by alexeymezenin]: https://github.com/alexeymezenin/laravel-best-practices#contents
