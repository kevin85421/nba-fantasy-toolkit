# NBA Fantasy Toolkit

Free, zero-install browser tools for **9-category head-to-head** fantasy basketball. Every tool is a static HTML page: no build step, no server, no account. Open it and go. Your data stays in your browser (`localStorage`).

**Live:** https://kevin85421.github.io/nba-fantasy-toolkit/ (once GitHub Pages is enabled)

## Tools

| Tool | Status | Path |
| --- | --- | --- |
| Draft assistant (選秀作戰室) | ✅ Ready | [`draft/`](draft/) |
| Lineup: daily starters | 🛠 Planned | |
| Waiver: best adds | 🛠 Planned | |
| Matchup: weekly win odds | 🛠 Planned | |
| Trade evaluator | 🛠 Planned | |

## League format it targets

The defaults are built around this league. Most of the math carries over to any 9-cat league.

- **12 teams**, head-to-head, **most categories** wins the week
- **9 categories:** PTS, REB, AST, ST, BLK, 3PTM, FG%, FT%, TO (fewer is better)
- **Lineup:** PG, SG, G, SF, PF, F, C, C, Util, Util + 3 BN + 3 IL
- **4 adds per week**, FAAB waivers
- Snake draft

## Draft assistant

A single-page assistant for a 9-cat snake draft.

- **Rankings:** 153 players with 2026-27 per-game estimates. The ordering follows Rotowire's 2026-27 9-cat top 150 (Oct 2026). The per-player stat lines are estimates, not official projections.
- **Z-scores** per category. FG% and FT% are volume-weighted, so a 60% shooter on 3 attempts doesn't outrank a 55% shooter on 15.
- **Team-need weighting:** as you draft, categories where your roster is weak get a higher weight in the recommendation.
- **Punt toggles:** drop any categories you've decided to punt and the rankings recompute.
- **Survival odds:** from ADP, the chance each player is still available at your next pick, so you know who you can wait on.
- **Roster slot matching:** checks that picks still fit the PG/SG/G/SF/PF/F/C/Util slots.
- **Saves automatically:** picks are kept in `localStorage`, so a refresh or a closed tab doesn't lose the draft.

### Use it

- **Online:** open the live link above and click *Draft assistant*.
- **Locally:** clone the repo and open `draft/index.html` in any modern browser. No server needed.

```bash
git clone https://github.com/kevin85421/nba-fantasy-toolkit.git
open nba-fantasy-toolkit/draft/index.html
```

During the draft, log every pick (yours and other teams') as it happens. The recommendation card, survival odds and team-need weights update after each one. Use *重新開始* (reset) to clear the draft.

### Claude Code skill

[`.claude/skills/draft/`](.claude/skills/draft/) is a [Claude Code](https://claude.com/claude-code) skill for the same draft. It has must-pick players, rankings by position, and rules for choosing between several available players. Open Claude Code in this repo, run `/draft`, and report picks as they happen. Player rankings are in [`references/rankings-2026-27.md`](.claude/skills/draft/references/rankings-2026-27.md). To update for a new season, replace that file; the rules in `SKILL.md` stay the same.

## Roadmap

- **Lineup:** pick daily starters from your roster around games played and slot eligibility.
- **Waiver:** rank free agents by how much they help your weakest categories, while respecting the 4-adds-per-week cap.
- **Matchup:** per-category win probability for the current week, factoring in games remaining.
- **Trade evaluator:** category-by-category impact of a proposed trade on both teams.
- **Yahoo league integration:** import your league, rosters and settings instead of entering them by hand.

## 中文說明

這是一套給 **9-cat H2H（比類別數）** 夢幻籃球用的免安裝網頁工具。全部是純靜態 HTML，打開瀏覽器就能用，資料只存在你自己的瀏覽器裡。

- **選秀作戰室**（`draft/`）：蛇形選秀助手。依 z-score 排名（FG%、FT% 依出手數加權），會根據你隊伍弱項調整推薦、支援 punt 類別、用 ADP 估算球員撐到你下一順位的機率，並檢查位置是否塞得進陣容。選秀紀錄會自動存檔。
- 預設聯盟：12 隊、9 類別（PTS REB AST ST BLK 3PTM FG% FT% TO）、PG SG G SF PF F C C Util Util + 3 BN + 3 IL、每週 4 次 add、FAAB。
- 排名順序參考 Rotowire 2026-27 9-cat 前 150 名（2026 年 10 月），個別數據為估計值，不是官方預測。
- 接下來會做：每日先發、waiver 推薦、每週對戰勝率、交易評估、Yahoo 聯盟串接。

## License

[MIT](LICENSE)
