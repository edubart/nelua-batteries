This is a collection of various useful libraries for Nelua,
with the following characteristics:

* All libraries are designed to work well with Nelua.
* All libraries have minor tests and examples of use.
* All libraries are classified as "Tier 2" quality,
while the Nelua compiler is "Tier 1" quality,
this means that APIs here are more unstable and less tested than the Nelua standard libraries.
* All libraries binding other C libraries provide not just the bindings,
but also a wrapper to make it easier to use it with Nelua.
* All libraries wraps its API into a namespace style record, that is, it will not pollute the global environment.
* Some libraries may be maintained irregularly.
* Some libraries are not tested on all platforms.
* Some libraries are self contained when possible.
* Some libraries may not work on all platforms or architectures.

# List of libraries

* `backtrace` - Provides a way to get trace backs at runtime, using the popular [libbacktrace](https://github.com/ianlancetaylor/libbacktrace) library.
* `ffi` - Cross platform FFI for Nelua, you can use it to load symbols from shared libraries, originally created by [Rabia](https://github.com/Rabios).
* `fs` - Cross platform file system library, you can use manage files and directories.
* `json` - Parse JSON into Nelua records, made in pure Nelua.
* `nester` - Minimal unit testing framework inspired by [lester](https://github.com/edubart/lester).
* `inspector` - Function module which receives any value and returns the contents as a string, inspired by [inspect.lua](https://github.com/kikito/inspect.lua/)
* `bigint` - Arbitrary-precision arithmetic integer module based on GMP.
* `datetime` - Date time utilities to convert ISO 8601 human readable time format to Unix timestamps.
* `signal` - Utilities to catch and raise OS application signals.
* `sqlite3` - A wrapper for [SQLite](https://www.sqlite.org/index.html), to execute SQL queries on its databases.
* `heapqueue` - Implementation of priority queue using binary trees.
* `algorithm` - Provides algorithms to work on containers, like `sort` and `removeif`.
* `tuple` - Generic that implements tuples.

# Examples

Check the `examples` folder for checking for some libraries usage examples,
also the `tests` folder to check example of its APIs.

# License

MIT, see LICENSE file. Some libraries have additional authors, and they are
credited in the end of the library file.
