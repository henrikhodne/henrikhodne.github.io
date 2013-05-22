---
layout: post
title: Continuous Deployment With Travis
---

After I launched [Travis Lite](http://travis-lite.com/) last week, it didn't
take long before I got the [first pull request][first-pr]. The day after I got
[another one][second-pr]. And [another one][third-pr]. Anyways, I'm often out
and about, reading GitHub messages on my phone, and while I could merge the
changes, I couldn't immediately deploy them (well, I could, but SSH is not
exactly ideal to work with on a phone). I wanted a way for the site to be
deployed immediately if the Travis build passed.

I remembered someone writing about this in a Travis issue earlier, and sure
enough, after a quick seach I found [this article][metabates-deploy] by Mark
Bates on deploying to Heroku from Travis. It was just what I needed. There were
a few things I wanted to change, though:

- Everything was placed in the .travis.yml file. I like to keep my .travis.yml
  file as clean as possible.
- It put the Heroku API key in the .travis.yml file in clear text.
- It clears all of the SSH keys when it's done.
- *Every* passing build gets deployed. Even pull requests that haven't been
  merged yet.

After making a few updates, I came up with [this][deploy-script]. It makes sure
that we're not testing a pull request, that we tested on 1.9.3 and that we're
testing on master. If all of these things are true, and the test passed, we
deploy. I encrypted the Heroku API key using [secure environment
variables][secure-env-vars], and extracted the entire script to `script/deploy`.

I guess time will show if continuous deployment is a good idea. At the moment,
Travis Lite is a very small project, and deployment is a very easy process. If
you need to do more advanced things, like running migrations, this may not be a
good idea.

[travis-lite]: http://travis-lite.com/
[first-pr]: https://github.com/henrikhodne/travis-lite/pull/2
[second-pr]: https://github.com/henrikhodne/travis-lite/pull/6
[third-pr]: https://github.com/henrikhodne/travis-lite/pull/7
[metabates-deploy]: http://metabates.com/2012/10/23/deploying-to-heroku-from-travisci/
[deploy-script]: https://github.com/henrikhodne/travis-lite/commit/006e246c86efcd9eb70aea7bfe1100be8c7a1ebb
[secure-env-vars]: http://about.travis-ci.org/docs/user/build-configuration/#Secure-environment-variables
