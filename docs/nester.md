## Nester module

Nester is a minimal unit testing framework for Nelua with a focus on being simple to use.

## Features

* Minimal, just one file.
* Self contained, no external dependencies.
* Simple and hackable when needed.
* Use `describe` and `it` blocks to describe tests.
* Supports `before` and `after` handlers.
* Colored output.
* Configurable via the script or with environment variables.
* Quiet mode, to use in live development.
* Optionally filter tests by name.
* Show location of tests  errors.
* Show time to complete tests.

## Usage

Copy `nester.nelua` file to a project and require it,
and use it the following way:

```lua
require 'nester'

-- Customize nester configuration.
nester.stop_on_fail = false

nester.describe('my project', function()
  nester.before(function(name: string)
    -- This function is run before every test.
  end)

  nester.describe('module1', function() -- Describe blocks can be nested.
    nester.it('feature1', function()
      expect.equal('something', 'something') -- Pass.
    end)

    nester.it('feature2', function()
      expect.truthy(false) -- Fail.
    end)
  end)
end)

nester.report() -- Print overall statistic of the tests run.
nester.exit() -- Exit with success if all tests passed.
```

## Customizing output with environment variables

To customize the output of nester externally,
you can set the following environment variables before running a test suite:

* `NESTER_QUIET="true"`, omit print of passed tests.
* `NESTER_COLORED="false"`, disable colored output.
* `NESTER_SHOW_TRACEBACK="false"`, disable traceback on test failures.
* `NESTER_SHOW_ERROR="false"`, omit print of error description of failed tests.
* `NESTER_STOP_ON_FAIL="true"`, stop on first test failure.
* `NESTER_UTF8TERM="false"`, disable printing of UTF-8 characters.
* `NESTER_FILTER="some text"`, filter the tests that should be run.

Note that these configurations can be changed via script too, check the documentation.

### nester

```nelua
global nester: type = @record{}
```

The nester module.

### nester.quiet

```nelua
global nester.quiet: boolean
```

Whether lines of passed tests should not be printed. False by default.

### nester.colored

```nelua
global nester.colored: boolean
```

Whether the output should be colorized. True by default.

### nester.show_error

```nelua
global nester.show_error: boolean
```

Whether the error description of a test failure should be shown. True by default.

### nester.stop_on_fail

```nelua
global nester.stop_on_fail: boolean
```

Whether test suite should exit on first test failure. False by default.

### nester.utf8term

```nelua
global nester.utf8term: boolean
```

Whether we can print UTF-8 characters to the terminal. True by default when supported.

### nester.filter

```nelua
global nester.filter: string
```

A string with a Lua pattern to filter tests. Empty by default.

### nester.seconds

```nelua
global nester.seconds: auto
```

Function to retrieve time in seconds with milliseconds precision, `os.now` by default.

### nester.exit

```nelua
function nester.exit(): void
```

Exit the application with success code if all tests passed, or failure code otherwise.

### nester.describe

```nelua
function nester.describe(name: string, func: function()): void
```

Describe a block of tests, which consists in a set of tests.
Describes can be nested.
`name` is a string used to describe the block.
`func` a function containing all the tests or other describes.

### nester.it

```nelua
function nester.it(name: string, func: function()): void
```

Declare a test, which consists of a set of assertions.
Where `name` is the test name,
and `func` is the function containing all assertions.

### nester.before

```nelua
function nester.before(func: function(string)): void
```

Set a function that is called before every test inside a describe block.
A single string containing the name of the test about to be run will be passed to `func`.

### nester.after

```nelua
function nester.after(func: function(string)): void
```

Set a function that is called after every test inside a describe block.
A single string containing the name of the test that was finished will be passed to `func`.
The function is executed independently if the test passed or failed.

### nester.report

```nelua
function nester.report(): boolean
```

Pretty print statistics of all test runs.
With total success, total failures and run time in seconds.

### expect

```nelua
global expect: type = @record{}
```

Expect module, containing utility function for doing assertions inside a test.

### expect.equal

```nelua
function expect.equal(a: auto, b: auto): void
```

Checks if `a` is equals to `b`, if not raises a test error.

### expect.not_equal

```nelua
function expect.not_equal(a: auto, b: auto): void
```

Checks if `a` is different from `b`, if not raises a test error.

### expect.truthy

```nelua
function expect.truthy(v: boolean): void
```

Checks if `v` is true, if not raises a test error.

### expect.falsy

```nelua
function expect.falsy(v: boolean): void
```

Checks if `v` is false, if not raises a test error.

### expect.error

```nelua
function expect.error(msg: facultative(string)): void
```

Raises test error message `msg`.

### expect.assert

```nelua
function expect.assert(cond: boolean, msg: string): void
```

Raises test error message `msg` if `cond` is false.

---
