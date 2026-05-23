# 1ページ目 — stationery/notebook Spec

**Status:** Approved
**Author:** torifo
**Created:** 2026-05-23
**Updated:** 2026-05-23

---

## 1. Overview

### Problem Statement
筆記用具は「文字を書くという行為」のための道具なのに、ECは商品写真をタイルに並べるだけになりがちで、書く動作の手触りが伝わらない。ノート的世界観で「書く道具を選ぶ場」を再構成したい。

### Goal
画面全体を一冊のノートに見立て、横罫線と方眼を背景に持つ筆記用具専門店「1ページ目（IPPAGE）」を実装する。シャープ・ボールペン・万年筆・蛍光ペン・替芯まで筆記具で深掘りする。

### Non-Goals
- 筆記具以外の商品（ノート単独販売は除外）
- カート / 決済機能
- 動画レビュー

---

## 2. User Stories

| ID | Persona | Want to | So that |
|----|---------|---------|---------|
| US-01 | 中学〜大学生 | 「ノートに書き込んでる感」を画面で感じたい | 書く道具の店だと直感できる |
| US-02 | 同上 | 用途別（暗記 / 清書 等）で選びたい | 自分の勉強パターンに合わせられる |
| US-03 | 同上 | 万年筆など高めの製品も気軽に試したい | 手に取る前にイメージできる |

---

## 3. Functional Requirements

| ID | Requirement | Priority |
|----|-------------|----------|
| FR-01 | body 全体に罫線背景 | P0 |
| FR-02 | 中央コンテナ左に朱の余白縦線 | P0 |
| FR-03 | 商品 6 アイテム（筆記具のみ） | P0 |
| FR-04 | 用途別書き比べセクション 4 件 | P0 |
| FR-05 | 店主の手書きメモ | P1 |
| FR-06 | 商品の image-img は方眼背景 | P1 |
| FR-07 | ホバーで pin shadow が朱色に | P1 |
| FR-08 | モバイル対応（375px） | P0 |

---

## 4. Key Design Decisions

| Decision | Chosen | Rationale | Rejected |
|----------|--------|-----------|----------|
| 主書体 | Klee One | 教科書体由来で「書く」連想を強化 | Noto Sans のみ |
| 罫線色 | 淡水色 (#9ec5e0) | 一般的なノートの青ベース | 黒罫線 |
| 余白線 | 薄ピンク (#e89aa4) | ノートの定番 ・ 紙ナビとして機能 | 灰色 |
| 商品 image 背景 | 方眼柄 | 罫線（背景）×方眼（商品枠）で対比 | 単色 |
| 商品スコープ | 筆記用具のみ | 「ノートテーマ × 筆記具専門」の捻り | ノート も販売 |

---

## 5. Design System

```css
--paper:#fbf8f0;        /* 生成り */
--rule:#9ec5e0;          /* 罫線 */
--margin:#e89aa4;        /* 余白線 */
--accent:#3a5a8a;        /* 深インクブルー */
--hi:#fef191;            /* マーカー強調 */
--font-tegaki:'Klee One','Noto Sans JP',sans-serif;
```

---

## 6. References

- [navigator README](../README.md)
- Font: [Klee One](https://fonts.google.com/specimen/Klee+One)
