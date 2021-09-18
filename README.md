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
* Some libraries may be maintained irregularly, depending on the author.
* Some libraries are created and maintained by the community, thus the quality may vary.
* Some libraries are not fully tested.
* Some libraries are self contained when possible.
* Some libraries may not work on all platforms or architectures.
* Some libraries are under research and could perhaps be merged into Nelua standard library in the future, but probably won't.

# List of libraries

* `backtrace` - Provides a way to get tracebacks at runtime, using the popular [libbacktrace](https://github.com/ianlancetaylor/libbacktrace) library.
* `ffi` - Cross platform FFI for Nelua, you can use it to load symbols from shared libraries.
* `fs` - Cross platform system library, you can use manage files and directories.
