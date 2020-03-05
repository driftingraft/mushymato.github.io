# DPSシミュレーター for ドラガリアロスト（ほんやく版）

## What's this?
[Dagalia Lost DPS simulator](https://github.com/Mushymato/mushymato.github.io) を**日本語に翻訳（途中）**しているものです。
これらの大本は[こちら](https://github.com/b1ueb1ues/dl) のプロジェクトの計算式を元にしています。

This is a fork of the [Dagalia Lost DPS simulator](https://github.com/Mushymato/mushymato.github.io) Mushymato forked version.
This, and Mushymato's one are fork of the [Dagalia Lost DPS simulator](https://github.com/b1ueb1ues/dl) originally created by b1ueb1ues.

## これらのデータを元にしています
- [Python simulator](https://github.com/mushymato/dl)
- [Web UI](https://wildshinobu.pythonanywhere.com/ui/dl_simc.html)
- [Skill frame data](https://github.com/mushymato/dl/tree/master/framedata/skills)
- [护符对照表 (For Mandarin users)](https://github.com/mushymato/mushymato.github.io/blob/master/dl-sim/amulet.csv)

## 計算の前提条件
- キャラクターは**レベル最大** (Lv80/Lv100) かつ**マナサークル最大** (50/70) 
- **プラス値**は竜輝の護符・キャラに**+100ずつ**振った状態
- **施設MAX**（訓練所Lv35, 祭壇Lv35）
- 各イベント施設もMAX
- ドラゴンには**竜哭碑Lv20**を反映して計算
- **ファフニール像Lv30**
- **完凸レベル100のドラゴン**を装備
- 完凸星５**真竜Ｇ２**武器を装備（訳注：*アギト武器も入っているようですが、スキルの攻撃UPや攻撃速度UPは反映されていない？*）
- 装備ドラゴンや護符はそれぞれのアイコンを参照

## ドラゴンと護符の選出ロジック
- **短剣／弓／ロッド／連続ヒット強化系**アビリティ持ちには、連続ヒット強化系の護符やドラゴンを候補に（訳注：*それ以外のキャラでは選出候補になっていない？*）
- **HP満タン系or被弾なし系**（訳注：*勇猛果敢*など？）アビリティ持ちにはHP満タン系or被弾なし系の護符やドラゴンを候補に

## 常に下記の攻撃操作をしたとして計算
- 剣: **２段目＋バースト**（いわゆる「１・２・バースト」） or **３段目＋バースト**
- 刀: **５段目＋バーストキャンセル**
- 短剣: **４段目＋バースト** or **５段目＋逆バースト**（３回ヒットとする　この動画を参照 https://www.youtube.com/watch?v=C_Cw76AQzqQ）
- 斧: **５段目**（コンボ出し切り）or **５段目＋バースト**
- 槍: **５段目＋バーストキャンセル**
- 弓: **５段目（コンボ出し切り）** or **４段目＋バースト** or **１段目＋バースト** or **バースト連打** （キャラによって異なる）
- ロッド: **５段目＋バーストキャンセル**
- 杖: **５段目**（コンボ出し切り）

## 下記のアビリティは**考慮しない**
- 各種**キラー**アビリティ (フレガノスキラー,魔法生物キラー,悪魔キラー,真竜キラーetc.)
- **状態異常が効かなかった場合**のキャラクターの状態異常特効
- 敵の攻撃により、**状態異常耐性・改**が発動した場合の影響
- **竜化した際のダメージ** (カスタム計算のページで個別に計算できるが、DPS表には加味されていない)
- **獅子奮迅**・**バースト撃破**による補正 (同上)

## 特記事項
- パーティメンバーは戦闘中常に同じDPSを稼いでいるとする (**仲間のブレイク時のダメージ増加や特効その他モロモロ**は考えない)
- **やる気が５段階たまるごとに他２名のスキル２つが超やる気対象になる**とみなし、チームDPSが 7500*0.5 ダメージ増えるとして算出
- 乱数の絡む特定のキャラクターは、100回計算した平均値を採用しています
- **竜の恩寵は戦闘中１回**発動したとして計算する（訳注：**竜の恩寵の攻撃力補正倍率は竜化の回数ごとに指数関数的に伸びる**。Ⅲで+10%,+25%+40%。*王子やザインフラッドが複数回竜化できる環境でのダメージ量は無視されている*ということ）
- （敵によってブレイクの回数やタイミングはわからないので）**ブレイク特効は戦闘時間全体の15%に寄与**していると考える (ブレイク特効+30%なら、0.3 * 0.15 = 4.5% が全体のダメージ量に加算されると計算)
- 同様に、**オーバードライブ特効は35%の時間に有効**だったと考える (オーバードライブ特効+30%なら、0.3 * 0.35 = 10.5% が加算)
- **疾風怒濤アビリティは常に発動**していると考える（スキルや操作で*コンボが途切れることは考慮していない*）

## 製作者
b1ueb1ues  
tiara (proofreading)  
luciferz2012 (first version of website)  
solofandy (front-end engineering)  
kenchendesign (UI design)  
Matt (rotation improve)  
qwewqa 
haukist
mushymato (maintainer)

## 謝辞
Totakeke, Shark3143, SanyamBansal, emrysduvent, ZedK, B3GG, 6tennis, CarelessParsley, MsNyara

## 日本語訳
漂流いかだ [@KOR_jiyugiga](https://twitter.com/KOR_jiyugiga)
