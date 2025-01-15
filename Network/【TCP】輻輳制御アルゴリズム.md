# 輻輳制御アルゴリズム

名称|タイプ|不向き|特徴(NewRenoと比べて)
-|-|-|-
Tahoe|Loss-Based||最初の輻輳制御アルゴリズム、高速recoveryがない
Reno|Loss-Based||複数のパケットが喪失するとtimeoutになる可能性が高い(※1)
NewReno|Loss-Based||基本的な輻輳制御アルゴリズム
Vegas|Delay-Based||輻輳回避時に最小のRTTと最新のRTTを比較してcwndの増減を調節
Westwood|hybrid|無線|エンド・ツー・エンドの帯域推定を基にcwndを調整
HighSpeed|Loss-Based|ロングファットパイプ|高速回復時のcwndの減少が小さく、輻輳回避時のcwnd増加が大きい
Scalable|Loss-Based|ロングファットパイプ|高速回復時のcwndの減少がHighSpeedより小さく、輻輳回避時のcwnd増加が指数関数的
Veno|Hybrid|無線|Vegasに輻輳回復を加えたイメージ、ランダムパケットロス時に高速回復時のcwndの減少が少ない
Bic|Loss-Based|ロングファットパイプ|HighSpeedやScalableのRTT公平性の悪さを改善、輻輳回避時のcwndが対数関数的に増加
H-TCP|Hybrid|ロングファットパイプ|輻輳回避時のcwndをACKではなく時間経過で増加させる
Hybla|Loss-Based|衛星通信|RTTが大きい環境でもスループットが低下しない様になっているらしい
Illinois|Hybrid||謎、bicに似てるらしい
YeAH|Hybrid|ロングファットパイプ|fastモード(HighSpeed,Scalable)とslowモード(NewReno)を使い分ける
CUBIC|Loss-Based|ロングファットパイプ|現在のLinuxカーネルで使用されている
BBR|Delay-Based||Quic(HTTP/3)で使用される

※1 複数パケットが喪失すると1つ目のパケット再送や2つ目のパケット再送に時間がかかりtimeoutとなる
