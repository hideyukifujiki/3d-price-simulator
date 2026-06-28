# 料金シミュレーター Vercel デプロイ手順

このフォルダ（`simulator-vercel`）をそのままVercelに公開すると、料金シミュレーターがWeb上で動きます。

- `index.html` … シミュレーター本体（これがトップページになります）
- `vercel.json` … Vercelの設定（キャッシュ等。触らなくてOK）

公開方法は2つあります。かんたんなのは方法B（GitHub）ですが、ターミナルが使えるなら方法A（CLI）が最速です。

---

## 方法A: Vercel CLI（最速・ターミナル使用）

1. Node.js を入れる（未導入なら https://nodejs.org からLTS版）
2. ターミナルで Vercel CLI を入れる:

   ```
   npm i -g vercel
   ```

3. このフォルダに移動して deploy:

   ```
   cd ".../web/simulator-vercel"
   vercel
   ```

4. 初回はログイン（メールやGitHub連携）と、いくつかの質問（プロジェクト名など）が出ます。基本はEnterで進めてOK。
5. 完了すると `https://〜.vercel.app` のURLが表示されます。これが公開URLです。
6. 本番公開（独自URL固定）にするには:

   ```
   vercel --prod
   ```

---

## 方法B: GitHub 経由（管理画面だけで完結）

1. https://vercel.com にサインアップ（GitHubアカウント連携が簡単）
2. このフォルダの中身（`index.html` と `vercel.json`）をGitHubの新規リポジトリにアップロード
   - GitHubの「Add file → Upload files」でドラッグ＆ドロップでもOK
3. Vercelダッシュボードで「Add New… → Project」→ 該当リポジトリを「Import」
4. 設定はそのまま「Deploy」を押すだけ（Framework Preset = Other / Output = ルート）
5. 数十秒で `https://〜.vercel.app` が発行されます

---

## 公開後

- 料金を更新したいとき: 大元のExcel（`shared/...v16...xlsx`）で数値を直し、シミュレーターのデータを作り直して `index.html` を差し替え→再デプロイ
- 独自ドメイン（例: price.3d-academy.com）はVercelのプロジェクト設定 → Domains から追加できます

困ったら、再デプロイ用のデータ反映もこちらで対応します。
