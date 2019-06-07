# Exploring Git Repositories

## Learning Goals

- Review a repository's history with `git log`
- Focus on certain changes with `git diff`
- Unstage changes with `git reset`
- Revert changes with `git checkout`

## Introduction

Git has important major features like branching and merging, but there are also
several Git commands developers use frequently for smaller workflow tasks.
Learning how to integrate them into your own workflow will give you some extra
speed and efficiency.

## Review a Repository's History with `git log`

As we add and commit changes, we are creating a Git log that we can refer back
to when needed. Run the command:

```bash
$ git log
```

!["git log"](https://curriculum-content.s3.amazonaws.com/prework/git-workflow/git%20log.gif)

and we'll see an output of all the commits made in that repository.

Retrieving a Git log is especially useful when we've cloned someone else's
repository and want to review the changes made to it. We can retrace their steps
and build out our understanding of why the code evolved the way it did. We can
do the same thing even if the repository is our own. Sometimes it feels like our
past coding self is a different person and we need to re-evaluate our old code
based on new things we've learned since. `git log` helps us do this.

> **Tip** By adding certain flags to the `git log` command, we can see just the
> history of commits made over the last few commits, within time frames or by a
> particular author. Check out the documentation to see all the ways to customize
> your commands.

## Focus on Certain Changes with `git diff`

When examining a repository's history, it's not always apparent _what_ or _how_
something changed. Fortunately, Git gives us a command to look at changes right
next to each other:

```bash
$ git diff
```

You will use the command `git diff <commit 1> <commit 2>`.

!["git diff"](https://curriculum-content.s3.amazonaws.com/prework/git-workflow/git%20diff.gif)

This command will show us the differences between previous commits and current
work, or between different branches, or anything else we need to track changes
between. Similar to `git log`, we can customize the command with the parameters
of what we're comparing.

`git diff` gives us another layer of granularity when it comes to a Git
repository's history. We can look at the _log_ to see where changes were
committed and then look at the _diff_ to see exactly what those changes were.

## Unstage Changes with `git reset`

It happens to all developers at some point: we make quick changes, add and
commit them to the repository. But before we push our changes, we realize we
committed something incomplete or made an error in our commit message. How do we
go back and fix it? We use the `reset` command to bring our work back the state
before the commit:

```bash
$ git reset
```

This command also comes with various flags we can add to specify which point we
want to go back to. For example, if we just want to undo the last commit, we use
the command:

```bash
$ git reset --soft HEAD~1
```

!["git reset --soft head~1"](https://curriculum-content.s3.amazonaws.com/prework/git-workflow/git%20reset.gif)

Now Git rewinds to the way our code was before the last commit. If we need to go
even further back, we could ask Git to take us, for example, three commits back
in the repo history:

```bash
$ git reset --soft HEAD~3
```

> **Tip** The `--soft` tag keeps the changes we've made since last commit in our
> working state so that we can fix, add to or remove them manually. If we know we
> want to clear those changes entirely, we can use the `--hard` flag instead.
> Check the documentation to see all the ways to customize your command.

## Revert Changes with `git checkout`

We discussed the command `git checkout` earlier when describing how to switch
between different branches. We can also use it as a way to clear unwanted
changes from our working branch. After all, one of the best things about using
Git to organize and keep track of our work is that it lets us explore and
experiment without running the risk of accidentally ruining our work. Maybe
you've already encountered a situation where you started to code a new feature
or solution but after a while realized you didn't want to continue it. Instead,
you wanted to clear it all and start back at the beginning. Run:

```bash
$ git checkout .
```

!["git checkout ."](https://curriculum-content.s3.amazonaws.com/prework/git-workflow/git%20checkout%20dot.gif)

... and you'll have a nice, clean working branch.

If we want to limit our cleaning to a single file, we can specify that file
instead of cleaning out everything:

```bash
$ git checkout index.html
```

This will wipe out all the changes to index.html and revert it to the last
committed state, but keep all the other changes we made in our working state.

## Conclusion

Git has a lot of powerful features and commands. Once we progress beyond the
basic techniques, we can use tools like `git log`, `git diff`, `git reset` and
`git checkout` to optimize our Git use.

## Resources

- [`git log` documentation](https://git-scm.com/docs/git-log)
- [`git diff` documentation](https://git-scm.com/docs/git-diff)
- [`git reset` documentation](https://git-scm.com/docs/git-reset)
- [`git checkout` documentation](https://git-scm.com/docs/git-checkout)

