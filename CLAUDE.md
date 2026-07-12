# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository overview

This repo contains standalone static HTML mockups for an "Investment War Room" (投資戰情室) — an AI-generated daily investment briefing product aimed at Taiwanese wealth-management use cases (client segmentation, relationship-manager scripts, stock/ETF watchlists). There is no build system, package manager, server, or test suite — each file is a single self-contained `.html` document with inline `<style>` and `<script>` blocks and no external dependencies.

- `dashboard.html` — the primary report layout: fixed header/sidebar shell, section-based nav (執行摘要/市場環境/股票與ETF/投資策略/風險提示/相關資訊), and an expandable stock/ETF table (click a row to reveal a detail panel with company blurb, YTD chart bar, and key stats).
- `investment_battlecard_mock.html` — an alternate "battlecard" layout exploring a denser two-column grid (main content + sidebar aside) with tabbed panels (市場觀點/資金流向/新聞佐證/產業推導) and a client-segmentation section (客戶態樣與自動分群) with RM talk-tracks per segment.

Both files embed realistic-looking but fictional market data/dates as design placeholders — the `investment_battlecard_mock.html` is explicitly labeled "假資料示意版" (fake-data demo). Treat embedded figures, tickers, and dates as mockup content, not live data.

## Working with these files

- No build/lint/test commands exist. Open the `.html` file directly in a browser to preview (double-click, or `start dashboard.html` on Windows).
- Since everything is inlined, edits to layout/styling happen directly in the `<style>` block at the top of each file; interactive behavior (row expand/collapse, tab switching, scroll-spy nav) is in the `<script>` block at the bottom.
- `dashboard.html` uses a shared row-toggle pattern: each data row calls `toggleDetail(id, tr)`, which shows/hides a sibling `<tr class="detail-row" id="detail-{id}">` and toggles an `expanded` class. When adding a new stock/ETF row, follow this same paired-row structure (summary row + hidden detail row keyed by a matching `id` suffix).
- `investment_battlecard_mock.html` uses a generic tab-switcher: any `.view-tabs` container with `[data-tab-target]` buttons toggles matching `.tab-panel` elements by id. Reuse this pattern for new tabbed sections rather than writing bespoke JS.
- Content is authored in Traditional Chinese (zh-TW/zh-Hant) for a Taiwan audience; keep new copy consistent with that locale and tone (formal financial-report register).
