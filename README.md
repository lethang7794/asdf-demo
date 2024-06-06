# asdf-demo

## What is asdf?

`asdf`[^asdf-homepage] is a tool version manager.

All tool version definitions are contained within one file (`.tool-versions`[^tool-versions-file]) which you can check in to your project's Git repository to share with your team.

## Why use asdf?

`asdf`

- ensures teams are using the exact same versions of tools (for each project)
- supports Github Actions (you can use the same configuration for local dev machine and CI/CD workflows)
- support for many tools via a plugin system[^asdf-community]
- is simple (it's a single Shell script you include in your Shell config)

## Getting started

- Install **asdf core**[^asdf-core]: official guide[^asdf-guide]

- For each of the projects, e.g. `node-19`, `node-20`

  - "Install" **asdf plugins**[^asdf-plugins] for tools defined in `.tool-versions`

    ```bash
    cat .tool-versions | awk '{print $1}' | xargs -I _ asdf plugin add _
    ```

    > [!IMPORTANT]
    > You need to "install" plugin for a tool, before using `asdf` to install a version of that tool.
    >
    > e.g.
    >
    > ```bash
    > asdf plugin add node
    > ```

    > [!TIP]
    > Plugins are how `asdf` knows to handle different tools like Node.js, Ruby, ...

- For each of the tool, install the [**_version_**][tool-versions] defined in `.tool-versions`

  ```bash
  asdf install
  ```

  > [!TIP]
  > In `asdf` words, it's "Install all the **_package_ versions** listed in the .tool-versions file"

- Confirm that for each project, the correct version of tool is invoked

  ```bash
  cd node-19
  node -v       # Should be v19.0.0
  cd ../node-20 #
  node -v       # Should be v20.0.0
  ```

  ```bash
  cd kubectl-1.28.3
  kubectl version      # Client Version: v1.28.3
  cd ../kubectl-1.29.4 #
  kubectl version      # Client Version: v1.29.4
  ```

> [!CAUTION]
> A completions that match a version of a tool is still an unsolved problem[^1].

[tool-versions]: https://asdf-vm.com/manage/versions.html

[^asdf-homepage]: <https://asdf-vm.com/>
[^asdf-guide]: <https://asdf-vm.com/guide/getting-started.html>
[^asdf-core]: <https://asdf-vm.com/manage/core.html>
[^asdf-plugins]: <https://asdf-vm.com/manage/plugins.html>
[^asdf-community]: <https://github.com/asdf-community>
[^tool-versions-file]: <https://asdf-vm.com/manage/configuration.html#tool-versions>
[^1]: Support command completions from installed tools - [Issue #752](https://github.com/asdf-vm/asdf/issues/752)
