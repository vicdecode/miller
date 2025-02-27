<!---  PLEASE DO NOT EDIT DIRECTLY. EDIT THE .md.in FILE PLEASE. --->
# What's new in Miller 6

See also the [list of issues tagged with go-port](https://github.com/johnkerl/miller/issues?q=label%3Ago-port).

## Documentation improvements

Documentation (what you're reading here) and online help (`mlr --help`) have been completely reworked.

In the initial release, the focus was convincing users already familiar with
`awk`/`grep`/`cut` that Miller was a viable alternative -- but over time it's
become clear that many Miller users aren't expert with those tools. The focus
has shifted toward a higher quantity of more introductory/accessible material
for command-line data processing.

Similarly, the FAQ/recipe material has been expanded to include more, and
simpler, use-cases including resolved questions from
[Miller Issues](https://github.com/johnkerl/miller/issues)
and
[Miller Discussions](https://github.com/johnkerl/miller/discussions);
more complex/niche material has been pushed farther down. The long reference
pages have been split up into separate pages. (See also
[Structure of these documents](structure-of-these-documents.md).)

Since CSV is overwhelmingly the most popular data format for Miller, it is
now discussed first, and more examples use CSV.

## JSON support, and arrays

Arrays are now supported in Miller's `put`/`filter` programming language, as
described in the [Arrays reference](reference-dsl-arrays.md). Also, `array` is
now a keyword so this is no longer usable as a local-variable or UDF name.

JSON support is improved:

* Direct support for arrays means that you can now use Miller to process more JSON files.
* Streamable JSON parsing: Miller's internal record-processing pipeline starts as soon as the first record is read (which was already the case for other file formats). This means that, unless records are wrapped with outermost `[...]`, Miller now handles JSON in `tail -f` contexts like it does for other file formats.
* Flatten/unflatten -- conversion of JSON nested data structures (arrays and/or maps in record values) to/from non-JSON formats is a powerful new feature, discussed in the page [Flatten/unflatten: JSON vs. tabular formats](flatten-unflatten.md).

## Improved Windows experience

Stronger support for Windows (with or without MSYS2), with a couple of
exceptions.  See [Miller on Windows](miller-on-windows.md) for more information.

Binaries are reliably available using GitHub Actions: see also [Installation](installation.md).

## In-process support for compressed input

In addition to `--prepipe gunzip`, you can now use the `--gzin` flag. In fact, if your files end in `.gz` you don't even need to do that -- Miller will autodetect by file extension and automatically uncompress `mlr --csv cat foo.csv.gz`. Similarly for `.z` and `.bz2` files.  Please see the page on [Compressed data](reference-main-compressed-data.md) for more information.

## Output colorization

Miller uses separate, customizable colors for keys and values whenever the output is to a terminal. See [Output Colorization](output-colorization.md).

## Improved numeric conversion

The most central part of Miller 6 is a deep refactor of how data values are parsed
from file contents, how types are inferred, and how they're converted back to
text into output files.

This was all initiated by [https://github.com/johnkerl/miller/issues/151](https://github.com/johnkerl/miller/issues/151).

In Miller 5 and below, all values were stored as strings, then only converted
to int/float as-needed, for example when a particular field was referenced in
the `stats1` or `put` verbs. This led to awkwardnesses such as the `-S`
and `-F` flags for `put` and `filter`.

In Miller 6, things parseable as int/float are treated as such from the moment
the input data is read, and these are passed along through the verb chain.  All
values are typed from when they're read, and their types are passed along.
Meanwhile the original string representation of each value is also retained. If
a numeric field isn't modified during the processing chain, it's printed out
the way it arrived. Also, quoted values in JSON strings are flagged as being
strings throughout the processing chain.

For example (see [https://github.com/johnkerl/miller/issues/178](https://github.com/johnkerl/miller/issues/178)) you can now do

<pre class="pre-highlight-in-pair">
<b>echo '{ "a": "0123" }' | mlr --json cat</b>
</pre>
<pre class="pre-non-highlight-in-pair">
{
  "a": "0123"
}
</pre>

<pre class="pre-highlight-in-pair">
<b>echo '{ "x": 1.230, "y": 1.230000000 }' | mlr --json cat</b>
</pre>
<pre class="pre-non-highlight-in-pair">
{
  "x": 1.230,
  "y": 1.230000000
}
</pre>

## REPL

Miller now has a read-evaluate-print-loop ([REPL](repl.md)) where you can single-step through your data-file record, express arbitrary statements to converse with the data, etc.

## New DSL functions / operators

* String-hashing functions [md5](reference-dsl-builtin-functions.md#md5), [sha1](reference-dsl-builtin-functions.md#sha1), [sha256](reference-dsl-builtin-functions.md#sha256), and [sha512](reference-dsl-builtin-functions.md#sha512).

* Platform-property functions [hostname](reference-dsl-builtin-functions.md#hostname), [os](reference-dsl-builtin-functions.md#os), and [version](reference-dsl-builtin-functions.md#version).

* Unsigned right-shift [`>>>`](reference-dsl-builtin-functions.md#ursh) along with `>>>=`.

* Absent-coalesce operator [`??`](reference-dsl-builtin-functions.md#absent-coalesce) along with `??=`;
absent-empty-coalesce operator [`???`](reference-dsl-builtin-functions.md#absent-empty-coalesce) along with `???=`.

## Improved command-line parsing

Miller 6 has getoptish command-line parsing ([pull request 467](https://github.com/johnkerl/miller/pull/467)):

* `-xyz` expands automatically to `-x -y -z`, so (for example) `mlr cut -of shape,flag` is the same as `mlr cut -o -f shape,flag`.
* `--foo=bar` expands automatically to  `--foo bar`, so (for example) `mlr --ifs=comma` is the same as `mlr --ifs comma`.
* `--mfrom`, `--load`, `--mload` as described on the [keystroke-savers page](keystroke-savers.md).

## Improved error messages for DSL parsing

For `mlr put` and `mlr filter`, parse-error messages now include location information:

<pre class="pre-non-highlight-non-pair">
mlr: cannot parse DSL expression.
Parse error on token ">" at line 63 columnn 7.
</pre>

## Developer-specific aspects

* Miller has been ported from C to Go. Developer notes: [https://github.com/johnkerl/miller/blob/main/go/README.md](https://github.com/johnkerl/miller/blob/main/go/README.md).
* Regression testing has been completely reworked, including regression-testing now running fully on Windows (alongside Linux and Mac) [on each GitHub commit](https://github.com/johnkerl/miller/actions).
