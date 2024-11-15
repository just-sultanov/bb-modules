# bb-modules

Example of configuring a mono repository using [babashka](https://github.com/babashka/babashka) and [direnv](https://direnv.net/).

## How it works

When we enter the directory with the project `direnv` automatically:

- sets a `PROJECT_ROOT_PATH` environment variable
- and exposes a `bin` scripts

With this way our script works from any project directory.
That's all :)

Thus, the modules are unaware that they are a part of the project, and in the future, if necessary, a module
can be moved to its own repository without significant changes to the structure of the entire project.

## Usage

```bash
# direnv's magic
$ cd bb-modules
direnv: loading ~/ws/oss/bb-modules/.envrc
direnv: export +PROJECT_ROOT_PATH ~PATH


# show project top level tasks
$ project tasks
The following tasks are available:

help    Show help
modules List of modules
module1 Tasks of the module 1
module2 Tasks of the module 2


# show project modules
$ project modules
The following modules are available:

module1  Module 1
module2  Module 2


# show project modules and subtasks
$ project help
The following modules and subtasks are available:

module1
  module1 task1              some task 1
  module1 task2              some task 2
  module1 too-long-task-name

module2
  No tasks found


# show module1 tasks
$ project module1 tasks
The following tasks are available:

task1              some task 1
task2              some task 2
too-long-task-name


# run module1 task1
$ project module1 task1
Hello, world!


# cleanup
$ cd ..
direnv: unloading
```

## Notes

- It can be simplified after [the default task](https://github.com/babashka/babashka/issues/1219) is implemented
