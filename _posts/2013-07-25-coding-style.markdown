---
layout: post
title: Coding Style
---

Today I decided to finally give [Go](http://golang.org) a try. One thing I
noticed when exploring some Go projects was that a lot of them recommended
running `go fmt` before committing code. Curious as to what this code did, I
decided to look it up. [This blog post](http://blog.golang.org/go-fmt-your-code)
explains it very succinctly:

> Gofmt is a tool that automatically formats Go source code.

Gofmt (the command that `go fmt` calls) has a set of rules on how to best format
Go code. At first I was a little bit skeptical of this. Having code conventions
is nice, but having one convention for all of Go?

Then I realised something. Most, if not all, of my opinions on coding style are
there because that's how I learned programming. Having a set of standard
conventions like what `go fmt` provides (and an easy way to apply them) makes it easier
to adopt the conventions right away.

Unfortunately, this also means that it'll be more or less impossible to have a similar
thing for Ruby. I would love to see a similar (configurable) tool for Ruby that
reformatted code according to some style, though.
