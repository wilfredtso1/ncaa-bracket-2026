# Project Notes — 2026 NCAA Tournament KenPom Bracket

## Overview

This project builds a complete 2026 Men's NCAA Tournament bracket using KenPom adjusted efficiency data as the primary analytical framework. The goal is to remove narrative bias, brand-name reputation, and recency hype from bracket decisions and replace them with a reproducible, data-driven process grounded in 24 years of tournament history.

All 67 games are picked — First Four through the National Championship — with explicit AdjO, AdjD, AdjEM, and tempo figures for every matchup, historical threshold checks, upset profile flags, and confidence levels.

---

## Analytical Framework

### Step 1 — Historical KenPom Thresholds

Before any picks were made, historical baselines were established from 2001–2025 tournament data:

**National Champions**
- Every champion since 2001 ranked top 25 in AdjEM — 100% compliance
- 96% ranked top 21 in AdjO (outliers: UConn 2014, Baylor 2021 — both ranked top 5 in AdjD)
- 92% ranked top 31 in AdjD
- Modern numerical thresholds: AdjO 124.1+, AdjD 91.3 or lower
- 12 of the last 13 champions ranked top 7 in either AdjO or AdjD

**Final Four (2021–2025 average)**
- AdjO rank: top 19
- AdjD rank: top 23
- AdjEM rank: top 11–12

**Elite Eight**
- AdjO rank: top 25–30
- AdjD rank: top 25–30
- AdjEM rank: top 15–18

These thresholds function as hard filters in later rounds. A team outside the top 25 AdjEM has never won a national championship in the KenPom era.

---

### Step 2 — Upset Model

Three upset profiles were established from historical efficiency matchup data:

**Profile A — High-seed offense-dominant, defensively weak vs. defense-first lower seed**
Lower seed covers ~38% of the time — nearly double the base rate. Classic "slow it down and win ugly" formula.

**Profile B — Lower seed with elite offense vs. defensive-minded higher seed**
Lower seed wins ~29% of the time. Less reliable but produces high-scoring upsets.

**Profile C — AdjEM Gap Thresholds**

| Gap | Higher Seed Win Rate |
|-----|---------------------|
| > 15 points | ~97% |
| 10–15 points | ~88% |
| 5–10 points | ~72% |
| < 5 points | ~55% (coin flip) |
| < 2 points | ~50% (supplementary factors decide) |

---

### Step 3 — Supplementary Variables

Five secondary filters were applied on top of the efficiency model:

**Tempo mismatches**
Any game where teams differ by 8+ possessions per game is flagged. Slower teams shorten games and increase variance — generally favoring the slower team by compressing the sample size.

**Strength of schedule context**
Mid-major and non-power conference teams with strong AdjEM profiles are flagged when their conference SOS may inflate their metrics. KenPom adjusts for opponent quality, but the adjustment is imperfect for teams that play few true Quad 1 opponents. Discounts of 1–3 AdjEM points were applied to WCC (Gonzaga, Saint Mary's, Santa Clara) and select A-10 (VCU, Saint Louis) teams.

**Experience and roster continuity**
Teams ranked in the top 20 nationally in D1 experience (minutes played by upperclassmen) receive a positive flag in close games (AdjEM gap < 5). Freshman-heavy teams with NBA-level stars (Duke, Arizona, BYU, Illinois) receive a pressure flag for tournament debuts.

**Free throw shooting**
For any projected close game (AdjEM gap < 5), both teams' FT% are noted. Teams shooting below 70% from the line historically surrender late-game leads. Used as a tiebreaker in coin-flip matchups. Saint Mary's (81.1%) and Vanderbilt (79.3%) received positive flags; Missouri received a risk flag.

**Recency trends (30-day AdjEM divergence)**
Full-season AdjEM is compared to each team's last 30 days of performance. Any divergence of 3+ points — positive or negative — is flagged and weighted more heavily than the full-season number when making the pick. Major positive flags: Arizona (+, 9-game streak), St. John's (+, 19-1 run), VCU (+, 16-1 run). Major negative flags: Kansas (−, 4-5 skid with blowout losses), UConn (−, lost 4 of 11), BYU (−, 7-10 post-Saunders), Texas Tech (−, 3 straight after Toppin ACL).

---

### Step 4 — Injury Adjustments

The following AdjEM adjustments were applied before picks were made:

| Team | Player Lost | Adjustment | Reason |
|------|------------|-----------|--------|
| BYU | Richie Saunders (ACL) | −8.0 | Primary facilitator and spacer; team went 7-10 without him |
| North Carolina | Caleb Wilson (season-ending) | −9.0 | Starter-level loss; directly flips UNC vs. VCU to a VCU favorite |
| Texas Tech | JT Toppin (ACL, 21.8 PPG) | −5 to −7 | Star player; team dropped 3 straight post-injury |
| UCLA | Bilodeau + Dent (managing) | −6.0 | Two contributors limited; Round of 32 path affected |
| Duke | Foster (out) + Ngongba II (questionable) | −3.5 | PG and center depth reduced; applied to Final Four matchup |
| Louisville | Mikel Brown Jr. (day-to-day) | −4.0 | Key scorer; Round of 64 game with South Florida became closer |

---

## Key 2026 Context

**Record-setting efficiency class**
- Illinois: AdjO 131.1 — highest ever recorded in the KenPom era (since 2002)
- Purdue: AdjO ~131.0 — second-highest ever
- The 2026 1-seed class averaged AdjEM +37.18 — strongest in KenPom history
- The 2026 2-seed class averaged AdjEM +31.03 — strongest ever

**Notable team profiles**
- Michigan: #1 defense nationally (AdjD ~88.5), but turnover-prone (179th in turnover rate)
- Illinois: historic offense but AdjD rank 28 — just outside the champion defensive threshold
- Purdue: historic offense but AdjD rank 36–37 — disqualifying for a deep run against elite offenses
- Arkansas: AdjO rank 5, AdjD rank 46 — elite offense, porous defense; Classic Profile A fragile team
- Kansas: KenPom 21st — the weakest 4-seed in the field

**Defending champion Florida**
Florida entered as the 4th overall KenPom team and defending national champion. No team has won back-to-back championships since UConn in 2024 (and only Florida/UConn/Duke twice in modern era). Florida's 12-game win streak ended in the SEC Tournament — a recency flag applied. Picked to exit in the Elite Eight vs. Houston.

---

## Model Overrides

Three picks were made against what the raw AdjEM suggested:

1. **Houston over Illinois (Sweet 16):** Illinois holds a 2.6-point AdjEM advantage (+35.6 vs +33.0). Override rationale: Houston's AdjD rank (5th) better matches the historical champion profile than Illinois's rank (28th). Houston's 63.4-possession tempo reduces Illinois's offensive volume by ~7–8 possessions. If Illinois's defense performs above its season average, this pick is wrong.

2. **Tennessee over Virginia (Round of 32):** Identical AdjEM of +24.5. Chose Tennessee's nation-leading offensive rebounding rate (44.7%) over Virginia's tempo-slowing advantage as the tiebreaker in a true coin flip.

3. **Houston over Florida (Elite Eight):** Followed the model (Houston +3.5 AdjEM edge) despite Florida's championship pedigree. Noted as a genuine coin flip.

---

## Fragile Favorites Analysis

**Kansas (4-seed, East)** — exits Round of 32
AdjEM below Elite Eight historical threshold. 4-5 late-season skid with blowout losses to eventual tournament teams. Star freshman Darryn Peterson missed 11 games. Recency AdjEM divergence of 6+ points. Draws St. John's (nearly identical AdjEM, 19-1 recent record) in Round 2.

**UConn (2-seed, East)** — exits Sweet 16
AdjO rank 26 falls outside the historical champion threshold (top 21). Only two exceptions in 24 seasons — both ranked top 5 in AdjD (UConn's AdjD is 11th). Lost 4 of last 11 and was blown out in the Big East final. Faces Michigan State's 12th-ranked defense in the Sweet 16 where offensive limitations become disqualifying.

**BYU (6-seed, West)** — exits Round of 32
Richie Saunders ACL tear applies a −8 AdjEM adjustment, dropping effective AdjEM from +26 to +18. Team went 7-10 in 17 games post-injury. AJ Dybantsa (25.3 PPG, projected top-3 pick) is extraordinary but now fully scoutable as a one-man offense. Gonzaga's 9th-ranked defense neutralizes him.

---

## Files

| File | Description |
|------|-------------|
| `index.html` | Full bracket analysis — styled dark-theme single-page site |
| `README.md` | Project summary and methodology overview |
| `project.md` | This file — detailed analytical notes and framework documentation |

---

## Data Sources

- **KenPom.com** — Adjusted Offensive Efficiency, Adjusted Defensive Efficiency, Adjusted Efficiency Margin, Tempo (through March 15, 2026)
- **BracketEngine** — Composite AdjEM and T-Rank estimates
- **ESPN** — Bracket structure, team notes, Joe Lunardi bracket guide
- **CBS Sports** — Full 1–68 seed list
- **The Ringer** — 2026 bracket breakdown and context
- **FOX Sports** — KenPom trend analysis, Cinderella profiles
- **On3 / 247Sports** — Historical KenPom tournament patterns
- **NCAA.com** — Official bracket and First Four schedule
