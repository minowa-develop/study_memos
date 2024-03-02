# 【一般知識】CPUアーキテクチャについて

### アーキテクチャ一覧

アーキテクチャ|系統|ビット|desc
-|-|-|-
x86|x86/64|32|
x64|x86/64|64|
x86_64|x86/64|64|
amd64|x86/64|64|AMDのCPU
arm|ARM|32,64|64ビットを含めている場合もあり
arm64|ARM|64|
AArch32|ARM|32|armの次世代
AArch64|ARM|64|arm64の次世代

### 系統別

系統|命令セット|会社|主な用途
-|-|-|-
x86/64|CISC|Intel,AMD　　(amd64はAMDのみ)|パソコン、サーバ
ARM|RISC|Arm|スマートフォン、タブレット、小型ゲーム機

### 命令セットについて

命令セット名称|fullname|ja訳|実行速度|desc|
-|-|-|-|-
CISC|Complex Instruction Set Computer|複雑命令セットコンピュータ|slow|CPUに高機能な命令を持たせて、<br>一つの命令で複雑な処理を実現
RISC|Reduced Instruction Set Computer|縮小命令セットコンピュータ|rapid|CPU内部に単純な命令しか持たないかわりに<br>それらをハードウェアのみで実装

### OSによる呼び方の違い

OS|64bitを表す主なパターン
-|-
Windows|「x64」が多い
RHEL(Red Hat Enterprise Linux)|「x86_64」
CentOS|「x86_64」
Debian|「amd64」
Ubuntu|「amd64」
