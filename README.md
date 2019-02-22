# buck-vs-code-example

Example showing how to connect Buck with the C/C++ extension for VS Code.

This project depends on the Eigen [Buckaroo](https://buckaroo.pm) package to demonstrate code-completion for packages.

## Usage

```bash
buckaroo install
code .
```

Open `main.cpp`, and give it a try!

## How it Works

To generate the `compile_commands.json` file, use the `compilation-database` flavor:

```bash
buck build //:app#compilation-database --show-output
```

Buck probably put the file here:

```bash
cat buck-out/gen/__app#compilation-database/compile_commands.json
```

Next, we have to tell VS Code where to find it.

```json
{
  "configurations": [
    {
      "name": "app",
      "compileCommands": "buck-out/gen/__app#compilation-database/compile_commands.json"
    }
  ],
  "version": 4
}
```
