# 1ページ目 Design Learnings

## 目的

「ノート」を視覚テーマとして扱いつつ、扱う商品は**筆記用具で専門化**する、というユーザー指示の捻りを実装する。視覚と商品スコープのギャップを成立させる方法を探った。

このブランドは架空店舗であり、実在の店舗・商品ではない。

## 設計したこと

- body 全体に横罫線を `linear-gradient` で敷き、画面が一冊のノートになるようにした
- 中央コンテナの左に薄ピンクの余白縦線を `::before` で立て、「左閉じノート」を再現
- 商品 image の中だけは方眼背景にし、罫線（外）× 方眼（内）の二段構えで視覚を分割
- 章タイトル「●」プレフィックスをピンクで配置し、ノートの「項目印」を再現
- 店主の声は「手書きメモ」セクションに変えて、Klee One の手書き感をフル活用

## CSS

```css
:root {
  --rh:36px;
  --rule:#9ec5e0;
  --margin:#e89aa4;
  --hi:#fef191;
  --font-tegaki:'Klee One','Noto Sans JP',sans-serif;
}

/* 横罫線 */
body {
  background-image: linear-gradient(to bottom,
    transparent calc(var(--rh) - 1px),
    rgba(158,197,224,.55) calc(var(--rh) - 1px),
    rgba(158,197,224,.55) var(--rh),
    transparent var(--rh)
  );
  background-size: 100% var(--rh);
  background-position: 0 12px;
}

/* 余白縦線 */
.page::before {
  content:"";
  position:absolute;
  left: clamp(3rem,8vw,5rem);
  top:0; bottom:0;
  width: 1.5px;
  background: var(--margin);
}

/* 商品 image-img を方眼に */
.item-img {
  background-image:
    linear-gradient(rgba(158,197,224,.4) 1px, transparent 1px),
    linear-gradient(90deg, rgba(158,197,224,.4) 1px, transparent 1px);
  background-size: 14px 14px;
}
```

罫線の高さ `--rh: 36px` を CSS 変数化したことで、line-height との同期を後から調整できる余地を残した。

## アニメーション

- リビールなし
- 商品カードのホバー時に `translate(-2px,-2px)` + 影をピンクに変える、軽い feedback のみ
- ノートをめくるような派手な遷移は避けた（「シンプル」原則）

## フォント

- 全体: `Klee One`（教科書体）
- 一部本文: `Noto Sans JP`
- セリフ系は不採用（手書き感と相性が悪い）

## ボタン

ボタンは存在しない。`nav a:hover` で蛍光ペン色の下線（マーカー風）が引かれるのみ。

## UI/UX

- ナビ4項目（筆記具 / 書き比べ / 店主のメモ / 店）
- 商品グリッドは「方眼背景の中の筆記具1点」が並ぶ構成
- 用途別の「書き比べ」セクションが、商品ページの代わりに購買意思決定の補助になる

## レイアウト

中央 `.page` コンテナを `max-width: 1100px` で取り、左 `padding-left: clamp(2.5rem,7vw,4.5rem)` で余白縦線の右側にコンテンツを配置。

商品カードに `box-shadow: 2px 2px 0 var(--paper-deep)` を入れ、ノートに付箋を貼ったような気配を演出。
