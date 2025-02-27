[**Take the 2021 Miller User Survey!**](https://docs.google.com/forms/d/e/1FAIpQLSfNgLS9WVRq9mu8dZlMbS7LbTyRH1diRDnT_dGiavSOh_A8xA/viewform?usp=sf_link)

# What is Miller?

**Miller is like awk, sed, cut, join, and sort for data formats such as CSV, TSV, tabular JSON and positionally-indexed.**

# What can Miller do for me?

With Miller, you get to use named fields without needing to count positional
indices, using familiar formats such as CSV, TSV, JSON, and
positionally-indexed.  Then, on the fly, you can add new fields which are
functions of existing fields, drop fields, sort, aggregate statistically,
pretty-print, and more.

![cover-art](./docs/coverart/cover-combined.png)

* Miller operates on **key-value-pair data** while the familiar
Unix tools operate on integer-indexed fields: if the natural data structure for
the latter is the array, then Miller's natural data structure is the
insertion-ordered hash map.

* Miller handles a **variety of data formats**,
including but not limited to the familiar **CSV**, **TSV**, and **JSON**.
(Miller can handle **positionally-indexed data** too!)

In the above image (color added for the illustration) you can see how Miller embraces the common themes
of key-value-pair data in a variety of data formats.

# Getting started

* [A quick tutorial on Miller](https://www.ict4g.net/adolfo/notes/data-analysis/miller-quick-tutorial.html)
* [Tools to manipulate CSV files from the Command Line](https://www.ict4g.net/adolfo/notes/data-analysis/tools-to-manipulate-csv.html)
* [www.togaware.com/linux/survivor/CSV_Files.html](https://www.togaware.com/linux/survivor/CSV_Files.html)
* [MLR for CSV manipulation](https://guillim.github.io/terminal/2018/06/19/MLR-for-CSV-manipulation.html)
* [Miller in 10 minutes](https://miller.readthedocs.io/en/latest/10min.html)
* [Linux Magazine: Process structured text files with Miller](https://www.linux-magazine.com/Issues/2016/187/Miller)
* [Miller: Command Line CSV File Processing](https://onepointzero.app/posts/miller-command-line-csv-file-processing/)

# More documentation links

* [**Full documentation**](https://miller.readthedocs.io/)
* [Miller's license is two-clause BSD](https://github.com/johnkerl/miller/blob/master/LICENSE.txt)
* [Notes about issue-labeling in the Github repo](https://github.com/johnkerl/miller/wiki/Issue-labeling)
* [Active issues](https://github.com/johnkerl/miller/issues?q=is%3Aissue+is%3Aopen+sort%3Aupdated-desc)

# Miller 6 (Go port) pre-release

* Pre-release/WIP docs are at [http://johnkerl.org/miller6](http://johnkerl.org/miller6)
* [go/README.md](./go/README.md)
* [Tracking issue](https://github.com/johnkerl/miller/issues/372)

# Installing

There's a good chance you can get Miller pre-built for your system:

[![Ubuntu](https://img.shields.io/badge/distros-ubuntu-db4923.svg)](https://launchpad.net/ubuntu/+source/miller)
[![Ubuntu 16.04 LTS](https://img.shields.io/badge/distros-ubuntu1604lts-db4923.svg)](https://launchpad.net/ubuntu/xenial/+package/miller)
[![Fedora](https://img.shields.io/badge/distros-fedora-173b70.svg)](https://apps.fedoraproject.org/packages/miller)
[![Debian](https://img.shields.io/badge/distros-debian-c70036.svg)](https://packages.debian.org/stable/miller)
[![Gentoo](https://img.shields.io/badge/distros-gentoo-4e4371.svg)](https://packages.gentoo.org/packages/sys-apps/miller)

[![Pro-Linux](https://img.shields.io/badge/distros-prolinux-3a679d.svg)](http://www.pro-linux.de/cgi-bin/DBApp/check.cgi?ShowApp..20427.100)
[![Arch Linux](https://img.shields.io/badge/distros-archlinux-1792d0.svg)](https://aur.archlinux.org/packages/miller-git)

[![NetBSD](https://img.shields.io/badge/distros-netbsd-f26711.svg)](http://pkgsrc.se/textproc/miller)
[![FreeBSD](https://img.shields.io/badge/distros-freebsd-8c0707.svg)](https://www.freshports.org/textproc/miller/)

[![Homebrew/MacOSX](https://img.shields.io/badge/distros-macosxbrew-ba832b.svg)](https://github.com/Homebrew/homebrew-core/search?utf8=%E2%9C%93&q=miller)
[![MacPorts/MacOSX](https://img.shields.io/badge/distros-macports-1376ec.svg)](https://www.macports.org/ports.php?by=name&substr=miller)
[![Chocolatey](https://img.shields.io/badge/distros-chocolatey-red.svg)](https://chocolatey.org/packages/miller)

|OS|Installation command|
|---|---|
|Linux|`yum install miller`<br/> `apt-get install miller`|
|Mac|`brew install miller`<br/>`port install miller`|
|Windows|`choco install miller`|

See also [building from source](https://miller.readthedocs.io/en/latest/build.html).

# Build status

[![Go-port multi-platform build status](https://github.com/johnkerl/miller/actions/workflows/go.yml/badge.svg)](https://github.com/johnkerl/miller/actions)

[License: BSD2](https://github.com/johnkerl/miller/blob/master/LICENSE.txt)

[Docs](https://miller.readthedocs.io/en/latest/?badge=latest)

# Community

* Discussion forum: https://github.com/johnkerl/miller/discussions
* Feature requests / bug reports: https://github.com/johnkerl/miller/issues

# Contributors

Thanks to all the fine people who help make Miller better by contributing commits/PRs! (I wish there
were an equally good way to honor all the fine people who contribute through issues and feature requests!)

<a href="https://github.com/johnkerl/miller/graphs/contributors">
  <img src="https://contributors-img.web.app/image?repo=johnkerl/miller" />
</a>

# Features

* Miller is **multi-purpose**: it's useful for **data cleaning**,
**data reduction**, **statistical reporting**, **devops**, **system
administration**, **log-file processing**, **format conversion**, and
**database-query post-processing**.

* You can use Miller to snarf and munge **log-file data**, including selecting
out relevant substreams, then produce CSV format and load that into
all-in-memory/data-frame utilities for further statistical and/or graphical
processing.

* Miller complements **data-analysis tools** such as **R**, **pandas**, etc.:
you can use Miller to **clean** and **prepare** your data. While you can do
**basic statistics** entirely in Miller, its streaming-data feature and
single-pass algorithms enable you to **reduce very large data sets**.

* Miller complements SQL **databases**: you can slice, dice, and reformat data
on the client side on its way into or out of a database. You can also reap some
of the benefits of databases for quick, setup-free one-off tasks when you just
need to query some data in disk files in a hurry.

* Miller also goes beyond the classic Unix tools by stepping fully into our
modern, **no-SQL** world: its essential record-heterogeneity property allows
Miller to operate on data where records with different schema (field names) are
interleaved.

* Miller is **streaming**: most operations need only a single record in
memory at a time, rather than ingesting all input before producing any output.
For those operations which require deeper retention (`sort`, `tac`, `stats1`),
Miller retains only as much data as needed. This means that whenever
functionally possible, you can operate on files which are larger than your
system&rsquo;s available RAM, and you can use Miller in **tail -f** contexts.

* Miller is **pipe-friendly** and interoperates with the Unix toolkit.

* Miller's I/O formats include **tabular pretty-printing**, **positionally
  indexed** (Unix-toolkit style), CSV, JSON, and others.

* Miller does **conversion** between formats.

* Miller's **processing is format-aware**: e.g. CSV `sort` and `tac` keep header lines first.

* Miller has high-throughput **performance** on par with the Unix toolkit.

* Not unlike `jq` (http://stedolan.github.io/jq/) for JSON, Miller is written
in portable, modern C, with **zero runtime dependencies**. You can download or
compile a single binary, `scp` it to a faraway machine, and expect it to work.

# What people are saying about Miller

<blockquote class="twitter-tweet"><p lang="en" dir="ltr">Today I discovered Miller—it&#39;s like jq but for CSV: <a href="https://t.co/pn5Ni241KM">https://t.co/pn5Ni241KM</a><br><br>Also, &quot;Miller complements data-analysis tools such as R, pandas, etc.: you can use Miller to clean and prepare your data.&quot; <a href="https://twitter.com/GreatBlueC?ref_src=twsrc%5Etfw">@GreatBlueC</a> <a href="https://twitter.com/nfmcclure?ref_src=twsrc%5Etfw">@nfmcclure</a></p>&mdash; Adrien Trouillaud (@adrienjt) <a href="https://twitter.com/adrienjt/status/1308963056592891904?ref_src=twsrc%5Etfw">September 24, 2020</a></blockquote>

<blockquote class="twitter-tweet"><p lang="en" dir="ltr">Underappreciated swiss-army command-line chainsaw.<br><br>&quot;Miller is like awk, sed, cut, join, and sort for [...] CSV, TSV, and [...] JSON.&quot; <a href="https://t.co/TrQqSUK3KK">https://t.co/TrQqSUK3KK</a></p>&mdash; Dirk Eddelbuettel (@eddelbuettel) <a href="https://twitter.com/eddelbuettel/status/836555980771061760?ref_src=twsrc%5Etfw">February 28, 2017</a></blockquote>

<blockquote class="twitter-tweet"><p lang="en" dir="ltr">Miller looks like a great command line tool for working with CSV data. Sed, awk, cut, join all rolled into one: <a href="http://t.co/9BBb6VCZ6Y">http://t.co/9BBb6VCZ6Y</a></p>&mdash; Mike Loukides (@mikeloukides) <a href="https://twitter.com/mikeloukides/status/632885317389950976?ref_src=twsrc%5Etfw">August 16, 2015</a></blockquote>

<blockquote class="twitter-tweet"><p lang="en" dir="ltr">Miller is like sed, awk, cut, join, and sort for name-indexed data such as CSV: <a href="http://t.co/1zPbfg6B2W">http://t.co/1zPbfg6B2W</a> - handy tool!</p>&mdash; Ilya Grigorik (@igrigorik) <a href="https://twitter.com/igrigorik/status/635134857283153920?ref_src=twsrc%5Etfw">August 22, 2015</a></blockquote>

<blockquote class="twitter-tweet"><p lang="en" dir="ltr">Btw, I think Miller is the best CLI tool to deal with CSV. I used to use this when I need to preprocess too big CSVs to load into R (now we have vroom, so such cases might be rare, though...)<a href="https://t.co/kUjrSSGJoT">https://t.co/kUjrSSGJoT</a></p>&mdash; Hiroaki Yutani (@yutannihilat_en) <a href="https://twitter.com/yutannihilat_en/status/1252392795676934144?ref_src=twsrc%5Etfw">April 21, 2020</a></blockquote>

<blockquote class="twitter-tweet"><p lang="en" dir="ltr">Miller: a *format-aware* data munging tool By <a href="https://twitter.com/__jo_ker__?ref_src=twsrc%5Etfw">@__jo_ker__</a> to overcome limitations with *line-aware* workshorses like awk, sed et al <a href="https://t.co/LCyPkhYvt9">https://t.co/LCyPkhYvt9</a><br><br>The project website is a fantastic example of good software documentation!!</p>&mdash; Donny Daniel (@dnnydnl) <a href="https://twitter.com/dnnydnl/status/1038883999391932416?ref_src=twsrc%5Etfw">September 9, 2018</a></blockquote>

<blockquote class="twitter-tweet"><p lang="en" dir="ltr">Holy holly data swiss army knife batman! How did noone suggest Miller <a href="https://t.co/JGQpmRAZLv">https://t.co/JGQpmRAZLv</a> for solving database cleaning / ETL issues to me before <br><br>Congrats to <a href="https://twitter.com/__jo_ker__?ref_src=twsrc%5Etfw">@__jo_ker__</a> for amazingly intuitive tool for critical data management tasks!<a href="https://twitter.com/hashtag/DataScienceandLaw?src=hash&amp;ref_src=twsrc%5Etfw">#DataScienceandLaw</a> <a href="https://twitter.com/hashtag/ComputationalLaw?src=hash&amp;ref_src=twsrc%5Etfw">#ComputationalLaw</a></p>&mdash; James Miller (@japanlawprof) <a href="https://twitter.com/japanlawprof/status/1006547451409518597?ref_src=twsrc%5Etfw">June 12, 2018</a></blockquote>
