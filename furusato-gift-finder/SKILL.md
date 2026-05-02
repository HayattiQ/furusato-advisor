---
name: furusato-gift-finder
description: Use when a user already has a furusato nozei donation budget or deduction limit and wants an AI agent to ask preferences, search public web pages, and recommend return gift candidates.
---

# Furusato Gift Finder

## Overview

Find and compare furusato nozei return gifts within a user's stated donation budget. This skill assumes the user already has a rough deduction limit; if they need that estimated first, use `furusato-tax-advisor`.

## Hard Rules

- Ask for the user's remaining donation budget before recommending products.
- Treat all product data as volatile. Verify current pages when availability, donation amount, delivery, reviews, or application period matters.
- Use public web search or browser access only. Do not log in, access My Page, operate carts, submit donations, or handle private account data.
- Do not bulk scrape. Inspect only a small shortlist of relevant public pages.
- Do not guarantee stock, delivery, tax treatment, rankings, value, or suitability.
- Include a final reminder that the user must confirm details on the official page before donating.

## Intake Questions

Ask concise questions in Japanese. Gather enough information to search well:

1. `今回使える寄付額`: remaining donation budget in yen.
2. `ほしいもの`: category or concrete item, such as rice, beef, seafood, toilet paper, fruit, beer, travel voucher.
3. `優先条件`: choose or infer from the user:
   - quantity/value
   - quality/brand
   - review count/rating
   - delivery speed
   - storage constraints: frozen, refrigerated, room temperature
   - one-time gift or subscription
   - region or municipality preference
   - avoidances: allergies, alcohol, bulky items, perishables
4. `候補数`: default to 5 if unspecified.

If the user gives only budget and item, proceed with reasonable defaults instead of over-questioning.

## Search Strategy

Prefer official product pages over blog posts or affiliate roundups. For Satofull-focused searches:

```text
site:satofull.jp/products/detail.php ふるさと納税 <ほしいもの> <寄付額>
site:satofull.jp/products/detail.php <ほしいもの> 寄付金額 <上限額>
site:satofull.jp/products/detail.php <地域> <ほしいもの> ふるさと納税
```

For broader searches, include the target site or platform when the user names one:

```text
site:furusato-tax.jp <ほしいもの> <寄付額>
site:furunavi.jp <ほしいもの> <寄付額>
site:furusato.rakuten.co.jp <ほしいもの> <寄付額>
```

Use snippets only for discovery. Open candidate pages before presenting specific facts when possible.

## Candidate Filtering

Keep candidates that:

- fit within the remaining donation budget, or are clearly labeled as over budget
- match the requested category
- have visible donation amount and official URL
- include enough public information to compare

Prefer excluding candidates when:

- donation amount is unclear
- page appears unavailable or stale
- details require login
- important constraints conflict with the user's preferences

## Extracted Fields

For each candidate, extract only visible public facts:

- gift name
- donation amount
- municipality/prefecture
- contents and quantity
- delivery method or expected timing when visible
- review rating/count when visible
- application period, stock note, delivery exclusion, or other visible caveat
- official URL

If a field is not visible, write `不明` rather than guessing.

## Recommendation Output

Use Japanese by default. Structure the answer like this:

1. `前提`: user's budget and preferences.
2. `おすすめ候補`: table sorted by best fit, not necessarily cheapest.
3. `選び方`: concise comparison and trade-offs.
4. `予算管理`: total if combining multiple gifts, remaining budget, over-budget notes.
5. `確認事項`: official page checks before donation.
6. `免責`: product and tax details may change; final decision is the user's responsibility.

Table columns:

```text
候補 | 寄付金額 | 自治体 | 内容量 | 良い点 | 注意点 | URL
```

## Required Disclaimer

Include this or equivalent wording near the end:

```text
返礼品の寄付金額、在庫、受付状況、配送時期、内容量、レビュー等は変更される場合があります。寄付前に必ず公式ページで最新情報を確認してください。この回答は返礼品選びの補助であり、税務・法律上の助言ではありません。
```

## Redirects

- If the user does not know their donation limit, switch to `furusato-tax-advisor` if available.
- If the user asks for exact tax calculations, explain that this skill only helps select return gifts and recommend official detailed simulators or a tax professional.
- If the user asks to use a logged-in account or cart, decline and offer a manual checklist.
