# asdf-demo

## What is asdf?

`asdf` is a tool version manager.

All tool version definitions are contained within one file (`.tool-versions`) which you can check in to your project's Git repository to share with your team, ensuring everyone is using the exact same versions of tools.

## Why use asdf?

`asdf` ensures teams are using the exact same versions of tools, with support for many tools via a plugin system, and the simplicity and familiarity of being a single Shell script you include in your Shell config.

## Getting started

- Install **asdf core**: [official guide](https://asdf-vm.com/guide/getting-started.html)

- For each of the projects, e.g. `node-19`, `node-20`

  - Install **asdf plugins** for tools defined in `.tool-versions`

    ```bash
    cat .tool-versions | awk '{print $1}' | xargs -I _ asdf plugin add _
    ```

  - Install **tools** defined in `.tool-versions`

    ```bash
    asdf install
    ```

- Confirm that for each project, the correct version of tool is invoked

  ```bash
  cd node-19
  node -v # Should be v19.0.0
  ```

  ```bash
  cd node-20
  node -v # Should be v20.0.0
  ```
