---
slug: pkg-news
title: "Why and how maintain a NEWS file for your R package?"
authors:
  - Maëlle Salmon
date: "2020-05-06"
tags:
- package development
- news
output: 
  html_document:
    keep_md: true
---





Your R package is doomed to evolve as you had new features and bug fixes.
How to inform users of changes?
NEWS files are a key instrument in documenting changes.
In this post, we shall go through why keeping track of changes, how to create and maintain a changelog, advocating for the NEWS.md format.

# Why cultivate a changelog?

You will probably change stuff in your package.
Discussing package evolutions is beyond the scope of this post, refer to e.g. [this chapter of the rOpenSci dev guide](https://devguide.ropensci.org/evolution.html).
This post is about _documenting_ changes.
Even with a very clear version control history[^gitflow], having a text version of changes can be useful:

* to you and other developers, when looking back;

* to contributors, if you acknowledge their user name;

* to users, when updating the package or wondering when something changed;

* to you and other communicators, when drafting content (blog post, tweet, email) about a release.

```r 
news(package = "knitr")
```

```
                       Changes in version 999.999                       

    o   This NEWS file is only a placeholder. The version 999.999 does
	not really exist. Please read the NEWS on Github: <URL:
	https://github.com/yihui/knitr/releases>
```

How to write such a changelog, in practice?
We shall discuss format in the next section.
As regards contents, beside referring to the changelogs you like, [the NEWs chapter of the tidyverse style guide](https://style.tidyverse.org/news.html) is a very useful read.


# Why write the changelog as NEWS.md?

There are several possible formats for maintaining an R package changelog, according to the documentation of `util::news()`: inst/NEWS.Rd formatted like other Rd files, a Markdown NEWS.md, plain-text NEWS or inst/NEWS.

The actually serious [CRAN package `ouch`](https://kingaa.github.io/ouch/) uses inst/NEWS.Rd, like [134 other packages at the time of writing](https://github.com/search?l=&o=desc&q=org%3Acran+path%3A%2Finst%2F+filename%3ANEWS.Rd&s=indexed&type=Code).
In the case of `ouch`, inst/NEWS.Rd is actually [created from a plain-text inst/NEWS using `R CMD Rdconv`](https://github.com/kingaa/ouch/blob/8a2f39b895f97b7c8e8677f4052c42bbf16055c4/Makefile#L53-L54).

As regards plain-text NEWS files, when preparing this post I found [413 inst/NEWS](https://github.com/search?q=org%3Acran+path%3A%2Finst%2F+filename%3ANEWS&type=Code) and [1,055 NEWS](https://github.com/search?l=Text&q=org%3Acran+path%3A%2F+filename%3ANEWS&type=Code) in CRAN packages.

To save the best for

# When update the changelog

<!--html_preserve-->{{% tweet "1236738064850051074" %}}<!--/html_preserve-->

Now, in terms of workflow, you could

* update the changelog for each contribution;

* only update the changelog before releases;

* use [`fledge`](https://github.com/krlmlr/fledge).

In all cases you'll probably want to polish the changelog before releases, as [e.g. `usethis` would remind you](https://github.com/r-lib/usethis/blob/582a3fa886c042fe6c91376a6e4332df09a3db2a/R/release.R#L68).

# Conclusion

In this post we made the case for maintaining a changelog for your package, and for doing it in a NEWS.md file.

[^gitflow]: A good way to achieve one is adopting [git flow](https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow). You can make many stupid commits in a branch, and then squash and merge to master! It can also be wise to learn about [rewriting history](https://git-scm.com/book/en/v2/Git-Tools-Rewriting-History).