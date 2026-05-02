# ふるさと納税アドバイザー Skills

ふるさと納税の控除上限額のざっくり確認と、返礼品探しを支援する Codex Skills です。

このリポジトリには、次の2つの Skill が入っています。

- `furusato-tax-advisor`: 給与所得者向けに、ふるさと納税の控除上限額をざっくり見積もり、必要に応じて公開されている返礼品ページの比較も支援します。
- `furusato-gift-finder`: すでに寄付予算や控除上限額の目安がある場合に、公開ページを検索して返礼品候補を比較します。

## インストール

リポジトリ内の Skill をまとめてインストールします。

```bash
gh skill install HayattiQ/furusato-advisor
```

個別にインストールしたい場合は、Skill のパスを指定します。

```bash
gh skill install HayattiQ/furusato-advisor/furusato-tax-advisor
gh skill install HayattiQ/furusato-advisor/furusato-gift-finder
```

利用環境によって GitHub URL の指定が必要な場合は、次の形式を使ってください。

```bash
gh skill install https://github.com/HayattiQ/furusato-advisor
```

## 使い方

インストール後、Codex に日本語で依頼します。

```text
ざっくりふるさと納税の上限額を知りたい。給与年収700万円、共働き、小学生1人。
```

このような相談では、`furusato-tax-advisor` が給与年収や家族構成をもとに、控除上限額の簡易目安を出します。

すでに寄付予算や控除上限額の目安がある場合は、次のように依頼します。

```text
ふるさと納税で5万円くらい使える。お肉の返礼品を5個くらい探して。
```

このような返礼品探しでは、`furusato-gift-finder` が必要な条件を確認し、公開されている返礼品ページを少数だけ確認して候補を比較します。

## 注意事項

- この Skill は、ふるさと納税の計画と返礼品選びを補助するためのものです。
- 税務、法律、金融上の助言ではありません。
- 控除上限額の見積もりは簡易目安です。住宅ローン控除、医療費控除、副業・事業所得、年金所得、iDeCo などがある場合はズレることがあります。
- 返礼品の寄付金額、在庫、受付状況、配送時期、内容量、レビュー、申込期間などは変わることがあります。
- 寄付前に、必ず公式ページや各ポータルサイトで最新情報を確認してください。
- Skill はログイン、マイページ閲覧、カート操作、寄付申込、個人アカウント情報の取り扱いを行いません。

## 含まれる Skill

```text
furusato-advisor/
├── furusato-gift-finder/
│   ├── SKILL.md
│   └── agents/openai.yaml
└── furusato-tax-advisor/
    ├── SKILL.md
    ├── agents/openai.yaml
    └── references/simple-limit-table.md
```
