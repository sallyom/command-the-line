---
title: "PR Checkout No Remote"
date: 2020-05-10T00:16:29-04:00
draft: false
---

### You don't have to add a remote to checkout a Pull Request or a friend's branch!

If you already know this, then move along.
Whenever I mention to somebody about how I check out a branch to review a PR, 99% of the time,
they thank me and say, `I've always just added a new remote! This is way faster, thanks!` I
figured, then, that this would be a good little blog post, if I ever got around to creating my
blog.

Say you are tasked with reviewing a colleague's pull request, _or_ your friend has a much
needed feature in their branch that you want to take advantage of _before_ there's a pull
request.  What do you do? If you don't do this, you're probably doing it the hard way:

Note: The repositories mentioned here do not exist.

Assume you have your fork of cool-repo checked out locally, and you need to work with
your friend's branch of cool-repo.

Then, here's the little bit of convenience:

```
$ cd cool-repo

$ git fetch git@github.com:your-friend/cool-repo.git much-needed-branch

$ git checkout FETCH_HEAD
```

Now, you'll be in detached mode, and if you're simply reviewing a PR, go ahead and work from there.
However, if you'll be messing around and making changes in this branch, you can create a 
full-fledged branch by:

`$ git checkout -b now-it-is-my-much-needed-branch`

That's it! Hope I save you a few seconds of adding/deleting remotes.
