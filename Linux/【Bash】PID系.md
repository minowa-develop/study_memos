# PID系

command|desc
-|-
$\$|現在のPID
$!|バックグラウンドのPID
$PPID|親プロセスのPID
$BASHPID|サブプロセスのPID, バックグラウンド実行function内のPID

```bash
#!/bin/bash

echo "current PID: $$"
pstree -p "$$"

echo "parent PID: $PPID"
pstree -p "$PPID"

sleep 3 & echo "background PID: $!"
pstree -p "$$"

(
  echo "subshell PID: $BASHPID"
  pstree -p "$$"
)

echo "--- function test --"
function test_pid {
  pstree -p
  echo "\$\$: $$"
  echo "\$\!: $!"
  echo "PPID: $PPID"
  echo "BASHPID: $BASHPID"

}
test_pid & echo "BG PID: $!"

sleep 1
```