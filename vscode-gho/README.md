# ghoLang for VS Code

Syntax highlighting, comment toggling, bracket matching and snippets for `.gho` files.

## Install (no packaging needed)

```sh
ln -s "$(pwd)" ~/.vscode/extensions/gholang
```

Then reload VS Code (Developer: Reload Window).

## Or build a .vsix

```sh
npx @vscode/vsce package
code --install-extension gholang-0.1.0.vsix
```
