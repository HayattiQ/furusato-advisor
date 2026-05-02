# Furusato Advisor Skills

Codex skills for Japanese furusato nozei planning.

This repository contains two installable skills:

- `furusato-tax-advisor`: estimate a rough furusato nozei donation limit for salary earners and help compare public return gift pages.
- `furusato-gift-finder`: search and compare public return gift pages when the user already has a donation budget or deduction limit.

## Install

Install both skills from this repository:

```bash
gh skill install HayattiQ/furusato-advisor
```

Install one skill by path:

```bash
gh skill install HayattiQ/furusato-advisor/furusato-tax-advisor
gh skill install HayattiQ/furusato-advisor/furusato-gift-finder
```

If your `gh` installation requires a full GitHub URL, use:

```bash
gh skill install https://github.com/HayattiQ/furusato-advisor
```

## Usage

After installation, ask Codex in Japanese:

```text
ざっくりふるさと納税の上限額を知りたい。給与年収700万円、共働き、小学生1人。
```

Codex should use `furusato-tax-advisor` for rough donation-limit estimates.

When you already know your budget, ask:

```text
ふるさと納税で5万円くらい使える。お肉の返礼品を5個くらい探して。
```

Codex should use `furusato-gift-finder` to ask for needed preferences, search public pages, and compare a small shortlist.

## Notes

- These skills provide planning and shopping assistance only.
- They do not provide tax, legal, or financial advice.
- Product data, donation amounts, stock, delivery dates, reviews, and application periods can change.
- Always confirm current details on official product pages before donating.
- The skills must not log in to user accounts, operate carts, submit donations, or handle private account data.

## Included Skills

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
