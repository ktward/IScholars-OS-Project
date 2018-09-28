## Steps to Approve a Merge Request 

1. Pull targeted branch locally from Gitlab into an empty folder.
1. Open with IDE of choice.
2. Review code, gitlab has a nice GUI for inline commenting - see below for best practices 
1. Build project outputs.
1. Verify that build succeeded and feature works.
1. In the MR verify that the build succeeded.  If the build has not succeeded and if you're comfortable in teamcity, diagnose the build issue, and try re-running.  Most of the time, re-running solves the issue.
    1. If you can't get it to build, create an issue with Peter and Mike.
1. Once the build has succeeded, retrieve the build from the CI folder in box for your project and branch.
1. Verify that the feature in that build meets the acceptance criteria.
1. Approve the MR. 
1. Merge into development and delete the source branch. 
 

### Code Review Best Practice

Code review is a widely-used technique for improving software quality by human inspection. Code review can detect many kinds of problems in code, but as a starter, here are some general principles of good code:

* Don’t Repeat Yourself (DRY)
* Comments where needed
* Fail fast
* Avoid magic numbers
* One purpose for each variable
* Use good names

**Safe from bugs.** In general, code review uses human reviewers to find bugs. DRY code lets you fix a bug in only one place, without fear that it has propagated elsewhere. Commenting your assumptions clearly makes it less likely that another programmer will introduce a bug. The Fail Fast principle detects bugs as early as possible. 

**Easy to understand.** Code review is really the only way to find obscure or confusing code, because other people are reading it and trying to understand it. Using judicious comments, avoiding magic numbers, keeping one purpose for each variable, using good names, and using whitespace well can all improve the understandability of code.

**Ready for change.** Code review helps here when it’s done by experienced software developers who can anticipate what might change and suggest ways to guard against it. DRY code is more ready for change, because a change only needs to be made in one place.


 
 