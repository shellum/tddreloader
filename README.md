# tddreloader

This module runs inside an Erlang shell alongside development. It watches the `src/` directory for changed files, and when any file changes, it recompiles, loads, and runs tests on the file.

## Usage

```sh
cd myproject
erl -pa ebin -s tddreloader start
```

Or, in a running shell:

```erlang
tddreloader:start().
```

Or, in a project Makefile:

```make
shell:
  erl -pa ebin -s tddreloader start
```

Once tddreloader is started, it'll watch for file changes and do its thing. But if you want, you can reload stuff and run tests without starting the application.

`tddreloader:reload_all()` - reload everything under `src/`.

`tddreloader:test_all()` - run all tests for beams in `ebin/`.

### How I use it

My actual workflow is to split my terminal (I use tmux for that) and run my editor (vim) over my Erlang shell. That way, every time I save a file, it triggers a compile, a reload, and running all the tests for that module.

## Installing

Using erlang.mk:

```make
DEPS = ... tddreloader ...
...
dep_tddreloader = https://github.com/Version2beta/tddreloader.git master
```


