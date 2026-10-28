# Faso Live Sport — Prototype

Mobile-first web app to follow **live and upcoming** sports matches in **Burkina Faso**: football (Ligue 1, Étalons), basketball (national championship), handball, and more later.

- Prototype file: `index.html` (open it in a browser, no install needed)
- Language: French (main language of users in Burkina Faso)
- Status: clickable prototype with **fictional scores** and real club names

---

## 1. Design benchmark

### 1.1 Apps studied

| App | Audience / usage indicator | Sports | Key design traits |
|---|---|---|---|
| **Sofascore** | 50M+ downloads on Google Play | 20+ sports, strong on African leagues | Sport chips on top, date strip, matches grouped by competition, dark mode, very detailed stats |
| **FotMob** | Major football app, praised in UX critiques | Football only | 5-tab bottom bar with icons + labels, clean match cards, dark theme by default |
| **365Scores** | 50M+ downloads (2026 reviews) | Multi-sport, popular in Africa / Middle East | Bottom nav, "Live" filter, favorites first |
| **LiveScore** | 50M+ downloads | Football-first, multi-sport | Very compact list rows, red live minute, dark UI |
| **Flashscore** | 30+ sports | Multi-sport | Dense list, star to favorite a match, sport switcher on top |
| **ESPN** | 4.7★ from ~4M App Store reviews, #1 Sports at times | US sports + NBA | Score carousel, rich content, less suited to small leagues |

### 1.2 Patterns used by most apps

| Pattern | Used by | Kept in prototype? |
|---|---|---|
| Bottom navigation, 4–5 tabs, icon + label | FotMob, 365Scores, Sofascore, LiveScore | ✅ 4 tabs: Matchs, Direct, Favoris, Classement |
| Sport switcher as horizontal chips at the top | Sofascore, Flashscore, 365Scores | ✅ Football / Basketball / Handball |
| Horizontal date strip (Hier / Aujourd'hui / Demain) | All of them | ✅ |
| Matches grouped by competition | All of them | ✅ |
| Compact 2-line match row (status · teams · score · star) | LiveScore, Flashscore, Sofascore | ✅ |
| Live minute in red with pulse | LiveScore, Sofascore, FotMob | ✅ |
| Live / Upcoming / Finished filter | 365Scores, Flashscore | ✅ |
| Match page with tabs (Summary / Stats / Info) that adapts to match state | FotMob, Sofascore, Goal redesign case study | ✅ (bottom sheet) |
| Favorites with a star | Flashscore, Sofascore, 365Scores | ✅ (saved in the browser) |
| Dark mode | All of them | ✅ follows phone setting + manual toggle |

### 1.3 Conclusion

The **most common design** is the **Sofascore / FotMob model**: dark-friendly UI, sport chips + date strip at the top, compact match lists grouped by competition, bottom tab bar, and a match detail page with tabs. The prototype follows this model and adds a local identity: Burkina Faso flag colors (green `#009e49`, red `#ef2b2d`, gold star `#fcd116`).

**Local adaptations for Burkina Faso:**
- French interface.
- Light page weight (no images, no framework) for slow or expensive mobile data.
- Local competitions and venues first (Stade du 4-Août, Stade Wobi, Palais des Sports de Ouaga 2000).

### 1.4 Version 2 — NBA.com inspiration

The v2 prototype (`index.html`) keeps the benchmark layout above and adds what makes NBA.com feel premium. The v1 file is kept as `index-v1.html` for comparison.

| NBA.com pattern | Faso Live v2 |
|---|---|
| Black global top bar, bold uppercase links | Black bar with logo + links on desktop; bottom tab bar stays on mobile |
| Scores ticker across the top of every page | Horizontal ticker of today's matches, all sports, live first |
| Big featured game with team colors | Home hero: split background in both teams' colors, large score |
| Bold condensed typography | "Barlow Condensed" for titles, scores, team names |
| Game cards: team record, score, game leaders, "Box Score" / "Preview" buttons | Same: record (V-N-D or W-L), top scorers, "Feuille de match", "Direct", "Aperçu" |
| Games page: sport tabs + date arrows + day strip | Same, with ‹ › arrows and day strip |
| Game page tabs: Summary · Box Score · Play-by-Play | Résumé (score per quarter, best players) · Feuille de match · Action par action · Stats · Infos |
| Standings: W, L, PCT, GB, L10, Streak | Basketball: V, D, %, ÉC, 5 derniers, Série. Football: J V N D BP BC Diff Pts + 5 derniers |
| Stats leaders cards (#1 highlighted, then 2–5) | "Stats" tab: top scorers, assists, rebounds… |
| News / "Top Stories" | "À la une" cards on the home page |

---

## 2. Prototype scope

### 2.1 Screens (v2)

Always visible: top bar + **scores ticker** (today's matches, all sports).
At the bottom of every page: **footer**, modeled on NBA.com, Sofascore, FotMob and L'Équipe: (1) brand band — logo, promise "Tout le sport burkinabè, en direct", gold "Suivre mes équipes" button, app "bientôt" pill, social icons; (2) link directory by sport (Football, Basketball, Handball, Faso Live) with deep links to matches, standings, leaders and featured matches; (3) legal bar — copyright, legal pages (placeholders), demo and photo credits.

1. **Accueil** — full-width **"À la une" news carousel** at the top (photo banner; swipe, arrows on desktop, dots, auto-slides every 5.5 s and pauses on touch/hover), then the featured match (hero), "Matchs du jour" cards, followed matches, mini standings + top scorer (side column on desktop)
2. **Matchs** — sport tabs, date arrows + day strip (3 days back to 4 ahead), filters Tous / En direct / À venir / Terminés, game cards grouped by competition
3. **Classement** — full table for the selected sport (football: CAF / relegation colors; basketball: play-off line, games behind, streak)
4. **Stats** — leader cards per sport
5. **Favoris** — starred matches
6. **Article reader** (same window as match detail) — photo header, full article with quote, "Voir le match" button linking to the related match, "À lire aussi" list
   - Photos: free-license (CC BY-SA) generic sports photos from Wikimedia Commons, credited on each slide and article. No photos of real, identifiable star players, because the articles are fictional. They are loaded from Wikimedia only when a slide is shown, and fall back to the team color when offline.
7. **Match detail** (bottom sheet on mobile, centered window on desktop)
   - Hero in team colors with records
   - Football: Résumé · Stats · Compositions · Direct texte · Infos
   - Basketball: Résumé (quarters + best players) · Feuille de match (box score) · Action par action · Stats · Infos
   - Upcoming: Aperçu (record, form, reminder button) · Infos

### 2.2 Behaviors
- Live simulation every 6 s: football minute ticks; basketball clock runs down, baskets are scored, the play-by-play and box score update, changed scores flash.
- Favorites saved in `localStorage`.
- Horizontal match rows ("Matchs du jour", "Mes matchs suivis"): ‹ › arrows on mouse devices scroll by the cards that fit on screen and hide at each end; touch users swipe.
- Light / dark theme: follows the phone, ◐ button to switch.
- Responsive: phone (bottom tabs) and desktop (top links, two-column home).

### 2.3 Data model (demo)

```js
Match = {
  id, sport: "foot" | "basket" | "hand",
  comp, round, day,          // day: 0 = today, -1 = yesterday...
  status: "live" | "upcoming" | "finished",
  min | q + clock | time,    // football minute, basketball quarter + seconds left, or kickoff "18:00"
  h, a, hs, as,              // home/away team keys and scores
  venue, tv,
  events:   [[minute, "h"|"a", "goal"|"pen"|"yellow"|"red", player]],   // football
  quarters: [[home, away], ...],                                     // basketball
  pbp:      [[time, text, score?, keyPlay?]],                        // play-by-play
  stats:    [[label, home, away, unit?]]
}
// Standings rows also store the last 5 results ("VVNDV") for form and streak.
// Players are fictional, generated from common Burkinabè surnames.
```

### 2.4 Out of scope (next steps)
- **Real data**: no free public API covers Burkinabè leagues well. Options: manual entry back-office for club/federation volunteers, partnership with the FBF / Ligue de Football Professionnel, or scraping local media (Sidwaya, Burkina24, Fasofoot) with permission.
- Push notifications (goal alerts, kickoff reminders).
- Team and player pages; real news feed (articles are fictional for now).
- More sports: volleyball, cycling (Tour du Faso), athletics.
- PWA (installable, offline cache) and SMS alerts for basic phones.

---

## 3. References

**App usage and rankings**
- Sofascore listing data — https://www.similarweb.com/app/google/com.sofascore.results/canada/
- Best Sports Scores Apps, Top 10 ranked for 2026 — https://bettorsinsider.com/news/2024/03/05/best-sports-scores-apps-top-10-apps-ranked-for-2026/
- Sofascore vs LiveScore comparison — https://www.sofascore.com/no/news/sofascore-vs-livescore-which-live-score-app-should-you-use
- LiveScore app data — https://appgoblin.info/apps/356928178
- ESPN app comparison (ratings) — https://www.apppricinglab.com/compare/apple/1482431809/317469184
- Top Sports apps US iOS, March 2026 — https://marlvel.ai/rankings/us/ios/sports/2026-03-19
- Live sports scores apps collection — https://grand-screen.com/collection/live-sports-scores-apps/

**NBA.com (v2 inspiration)**
- NBA home — https://www.nba.com/
- Games / scoreboard — https://www.nba.com/games
- Standings — https://www.nba.com/standings
- Stats leaders — https://www.nba.com/stats

**UI / UX design**
- Design Critique: FotMob (Pratt IXD) — https://ixd.prattsi.org/2021/09/design-critique-fotmob-android-app/
- Goal Live Scores redesign (state-based match page) — https://www.behance.com/gallery/32220769/Goal-Live-Scores-App-Redesign
- WinScore mobile design system case study — https://iddictive.us/cases/winscore-mobile-design-system/
- GoalZone football live score concept (tabs: Live, Upcoming, Finished…) — https://contra.com/community/YDXrSucS-goal-zone-football-live-score-app
- Material Design 3 — https://m3.material.io/ · Apple Human Interface Guidelines — https://developer.apple.com/design/human-interface-guidelines/

**Burkina Faso sports context**
- Burkinabé Premier League — https://en.wikipedia.org/wiki/Burkinab%C3%A9_Premier_League
- Burkinabé Men's Basketball Championship — https://en.wikipedia.org/wiki/Burkinab%C3%A9_Men%27s_Basketball_Championship
- Burkina Faso 2025/26 (RSSSF tables) — https://rsssf.org/tablesb/burkf2026.html
- Season 2026-27 dates — https://foot-africa.com/actualites/burkina-faso-les-dates-de-la-saison-2026-2027devoilees-1253296/
- Basketball season launch (Burkina24) — https://burkina24.com/?p=398338
- Sidwaya sport section — https://www.sidwaya.info/sport/2025/
