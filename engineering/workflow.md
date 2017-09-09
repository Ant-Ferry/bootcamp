# Workflow

- [Epic Workflow](#epic-workflow)
- [Git Workflow](#git-workflow)
    - [Branching Model](#branching-model)
    - [Commit Message](#commit-message)

## Epic Workflow

## Git Workflow

The zen of Git workflow is all about [`branching`](./git.md#learn-git-branching), whose models differ among teams.

We basicly follow a classic `DRM-FH(develop;release;master-feature;hotfix)` model with some slightly differences(due to some tech debt), which has been proved quite effective in FIP. 


### Branching Model

<img src="./a-successful-git-branching-model/img/git-model@2x.png" width="100%">

*Chart by: [Vincent Driessen](http://nvie.com/about/)*

We follow a well-known branching model made by Vincent Driessen which is almost de facto default workflow of many Git Tools.

The model is detailed in [_A Successful Git Branching Model_](./a-successful-git-branching-model/article.md) [[ORIGIN]](http://nvie.com/posts/a-successful-git-branching-model/) by Vincent Driessen. 

Read the whole article and __MAKE SURE YOU ARE VERY FAMILIAR WITH IT__.

__ATTENTION:__ We use convention like `feature/new-parser`, which separate prefix and subject with `/` but `-`, which used by the original article in branch naming.

The valid retained prefixes are listed below:

- `feature/`
- `release/`
- `hotfix/`
- `support/`

You can setup and operate the whole git work flow by using [gitflow](https://github.com/nvie/gitflow) created by Vincent.

### Commit Message

Writing meaningful and well-constructed commit messages is important. Good commit messages serve at least three purposes:

* To make the reviewing process more efficient.
* To help the future maintainers(maybe yourself in the future) to find out why a particular change was made to the code or why a specific feature was added.
* To help us write a good release note.

And it's quite easy to write a good commit message by following [The Six Rules](./how-to-write-a-git-commit-message/article.md#seven-rules):

> _Keep in mind: [This](http://tbaggery.com/2008/04/19/a-note-about-git-commit-messages.html) [has](https://www.git-scm.com/book/en/v2/Distributed-Git-Contributing-to-a-Project#_commit_guidelines) [all](https://github.com/torvalds/subsurface-for-dirk/blob/master/README#L92-L120) [been](http://who-t.blogspot.co.at/2009/12/on-commit-messages.html) [said](https://github.com/erlang/otp/wiki/writing-good-commit-messages) [before](https://github.com/spring-projects/spring-framework/blob/30bce7/CONTRIBUTING.md#format-commit-messages)._

1.  [Separate subject from body with a blank line](#separate)
2.  [Limit the subject line to 50 characters](#limit-50)
3.  [Do not end the subject line with a period](#end)
4.  [Use the imperative mood in the subject line](#imperative)
5.  [Wrap the body at 72 characters](#wrap-72)
6.  [Use the body to explain _what_ and _why_ vs. _how_](#why-not-how)

Please go through the list and __MAKE SURE YOU ARE VERY FAMILIAR WITH IT!!__ And you can find the full article [How To Write A Git Commit Message](./how-to-write-a-git-commit-message/article.md) by [Chris Beams](https://github.com/cbeams).

__ATTENTION:__ You can use these [commit message template](https://github.com/zaoshu/gitmatic/tree/master/templates) or just auto configure them with [Gitmatic](https://github.com/zaoshu/gitmatic).

> P.S.
> If it seems difficult to summarize what your commit does, it may be because it includes several logical changes or bug fixes, and are better split up into several commits using `git add -p`.