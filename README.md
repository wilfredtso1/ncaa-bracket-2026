# 2026 NCAA Tournament — KenPom Bracket Analysis

A fully data-driven bracket for the 2026 Men's NCAA Tournament, built on KenPom adjusted efficiency metrics and supplementary analytics.

**Live site:** https://wilfredtso1.github.io/ncaa-bracket-2026/

## Champion Pick: Michigan Wolverines

KenPom #2 · AdjEM ~+37.6 · #1 Defense Nationally

## Final Four

| Team | Seed | Region | AdjEM |
|------|------|--------|-------|
| Michigan | 1 | Midwest | ~+37.6 |
| Arizona | 1 | West | ~+37.7 |
| Duke | 1 | East | ~+38.5 |
| Houston | 2 | South | ~+33.0 |

## Methodology

Every game is evaluated using:

- **KenPom AdjEM, AdjO, AdjD, and Tempo** as the primary framework
- **Historical thresholds** — AdjO/AdjD/AdjEM cutoffs derived from 24 years of tournament data (2001–2025)
- **Upset model** — efficiency matchup profiles that historically produce upsets, with quantified hit rates by round
- **Tempo mismatches** — games where teams differ by 8+ possessions per game are flagged as elevated upset risk
- **Injury adjustments** — AdjEM adjusted for season-ending or significant injuries (e.g. BYU −8, UNC −9, Texas Tech −5 to −7)
- **Recency trends** — teams with 30-day AdjEM diverging 3+ points from their full-season number are weighted accordingly
- **Experience flags** — upperclassman-heavy rosters historically outperform efficiency ratings in close tournament games
- **Free throw shooting** — used as a tiebreaker in games with AdjEM gap under 5 points

## Fragile Favorites

| Team | Seed | Exit Round | Key Vulnerability |
|------|------|-----------|------------------|
| Kansas | 4 East | Round of 32 | 4-5 late skid; AdjEM below E8 threshold; injured freshman |
| UConn | 2 East | Sweet 16 | AdjO rank 26 outside champion threshold; lost 4 of last 11 |
| BYU | 6 West | Round of 32 | −8 AdjEM after Saunders ACL; 7-10 post-injury record |

## Top Upset Picks

| Upset | Round | Confidence |
|-------|-------|-----------|
| Utah State over Villanova | R64 West | Very High |
| Iowa over Clemson | R64 South | High |
| VCU over North Carolina | R64 South | Medium-High |
| Akron over Texas Tech | R64 Midwest | Medium |
| St. John's over Kansas | R32 East | Medium |

## Data Sources

- [KenPom.com](https://kenpom.com) — Adjusted Offensive/Defensive Efficiency, Tempo
- [BracketEngine](https://bracketengine.locker) — AdjEM composite estimates
- ESPN, CBS Sports, The Ringer — bracket and team context
- Historical KenPom tournament records (2001–2025)
