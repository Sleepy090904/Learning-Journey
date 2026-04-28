# 🗺️ Lernplan — Collector/Roll Game

> Ziel: Ein Roblox-Spiel entwickeln, in dem Spieler Items mit verschiedenen Seltenheitsstufen rollen und sammeln können. Mechanik inspiriert von Trend-Games wie "Steal a Brainrot" und Aura-Simulatoren.

---

## 🎯 Spielidee (Kurzfassung)

- Spieler drücken einen Button → bekommen ein zufälliges Item (Common bis Mythic)
- Seltenere Items = höherer Status → sozialer Treiber
- Leaderboard zeigt wer das seltenste Item hat
- Inventar wird gespeichert (DataStore)
- Viraler Moment: Server-Broadcast wenn jemand Mythic rollt

---

## 📅 Phasenplan

### ✅ Bereits gelernt (Grundlage)
- Luau Basics (Variablen, Funktionen, Typen)
- Events (Touched, Connect)
- Loops (for, while), Tables, GetChildren()
- Debounce-Pattern, task.wait()
- Script-Architektur (ServerScriptService)

---

### Phase 1 — Rarity-System (Woche 1–2)

**Was du lernst:**
- ModuleScripts — Logik sauber auslagern (wie eine static class in C#)
- `math.random()` — Zufallszahlen generieren
- Gewichtete Wahrscheinlichkeiten (Common 60%, Rare 25%, Epic 10%, Legendary 4%, Mythic 1%)

**Mini-Projekt:** Rarity-ModuleScript das per `math.random()` ein Item zurückgibt — testen per `print()`, noch kein UI.

**Lernziel:** Du verstehst wie ModuleScripts funktionieren und kannst Logik vom Script trennen.

---

### Phase 2 — GUI & LocalScript (Woche 2–3)

**Was du lernst:**
- ScreenGui, Frame, TextLabel, TextButton — UI-Elemente in Roblox
- LocalScript — läuft nur beim Spieler (Client), nicht auf dem Server
- GUI-Events: `Button.MouseButton1Click:Connect()`

**Mini-Projekt:** Roll-Button + Anzeige des gezogenen Items als Text. Noch ohne echte Server-Logik.

**Lernziel:** Du verstehst den Unterschied zwischen Script (Server) und LocalScript (Client).

---

### Phase 3 — RemoteEvents & Client-Server-Architektur (Woche 3–4)

**Was du lernst:**
- RemoteEvents in ReplicatedStorage platzieren
- Client → Server: `RemoteEvent:FireServer()`
- Server → Client: `RemoteEvent:FireClient(player)`
- Warum die Roll-Logik auf dem Server laufen muss (Cheating verhindern)

**Mini-Projekt:** Button-Click im LocalScript → FireServer → Server zieht Item → FireClient zurück → UI zeigt Item an.

**Lernziel:** Du verstehst die Client-Server-Architektur — das wichtigste Konzept in Roblox-Entwicklung.

---

### Phase 4 — Spieler-System & DataStore (Woche 4–5)

**Was du lernst:**
- Players Service: `Players.PlayerAdded`, `Players.PlayerRemoving`
- Leaderstats — eingebautes Leaderboard (Punkte, seltenste Roll etc.)
- DataStoreService — Inventar speichern und laden

**Mini-Projekt:** Spieler-Inventar wird beim Joinen geladen und beim Verlassen gespeichert. Leaderboard zeigt "Seltenste Roll".

**Lernziel:** Nach dieser Phase hast du ein vollständig spielbares Spiel — Fortschritte bleiben erhalten.

---

### Phase 5 — Polish & Effekte (Woche 5–6)

**Was du lernst:**
- TweenService — sanfte Animationen (Roll-Animation, Item einblenden)
- SoundService — Sounds abspielen (Epic-Sound bei Legendary Roll)
- ParticleEmitter — einfache Partikeleffekte für seltene Items

**Mini-Projekt:** Roll-Animation mit Tween + Sound-Feedback je nach Rarity.

**Lernziel:** Das Spiel fühlt sich polished an — der Unterschied zwischen "funktioniert" und "macht Spaß".

---

### Phase 6 — Sozialer Faktor & Launch (Woche 6–7)

**Was du lernst:**
- Server-Broadcast: Alle Spieler benachrichtigen wenn jemand Mythic rollt
- `RemoteEvent:FireAllClients()` — an alle Clients gleichzeitig senden
- Grundlagen des Veröffentlichens: Roblox-Spiel publizieren, Access-Settings, Thumbnails

**Mini-Projekt:** Broadcast-System + ersten Freundes-Test.

**Lernziel:** Du hast ein veröffentlichtes Spiel mit viralem Mechanismus.

---

### Phase 7 — Monetarisierung & Retention (Woche 8+)

**Was du lernst:**
- Gamepasses: 2x Luck, Extra Rolls
- Developer Products: Einmalige Käufe (Roll-Packs)
- Tägliche Belohnungen — Spieler kommen täglich zurück
- MarketplaceService — Käufe im Spiel verarbeiten

**Lernziel:** Das Spiel kann Einnahmen generieren und hält Spieler langfristig.

---

## 🗓️ Zeitplan-Übersicht

| Phase | Inhalt | Zeitraum |
|---|---|---|
| 1 | ModuleScripts + Rarity-System | Woche 1–2 |
| 2 | GUI + LocalScript | Woche 2–3 |
| 3 | RemoteEvents + Client-Server | Woche 3–4 |
| 4 | DataStore + Leaderstats | Woche 4–5 |
| 5 | TweenService + Effekte | Woche 5–6 |
| 6 | Broadcast + Launch | Woche 6–7 |
| 7 | Monetarisierung | Woche 8+ |

> **Realistisches Ziel:** Spielbares Spiel nach ~4–5 Wochen. Launch-ready nach ~6–7 Wochen.

---

## 🔗 Vergleich zu C# (Vorschau)

| Roblox-Konzept | C#-Analogie |
|---|---|
| ModuleScript | `static class` mit Utility-Methoden |
| LocalScript | Client-seitiger Code (z.B. UI-Controller) |
| RemoteEvent | Event über Netzwerk (wie SignalR oder gRPC) |
| DataStore | Datenbank / persistenter Speicher |
| TweenService | Animation / Lerp-Logik |
| `FireAllClients()` | Server-Push / Broadcast |

---

*Erstellt: April 2026 — basierend auf aktuellem Kenntnisstand nach Tag 2*
