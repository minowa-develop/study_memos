# escape+commandはaliasのみ有効

## alias

escapeで処理を分けられる
引数はそのまま渡される

```bash
#!/bin/bash

alias ssh='echo "use ssh by alias"'
ssh --help
\ssh --help
```

## function

escapeで処理を分けられない(functionが優先される)

```bash
#!/bin/bash

function ssh {
  echo "use ssh by alias"
}
ssh --help
\ssh --help
```