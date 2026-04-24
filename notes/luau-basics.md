# Luau Basics — Notizen

> Vergleiche immer mit C# für schnelleres Verständnis.

---

## Variablen

```lua
-- 'local' = scope-begrenzte Variable (zwingend nötig! sonst global)
local name = "Bruce"
local age = 21
local isPlaying = true
```

**C#-Vergleich:** In C# ist der Scope durch `{}` bestimmt. In Luau musst du `local` explizit schreiben.

---

## Funktionen

```lua
local function greet(playerName: string): string
    return "Hallo, " .. playerName .. "!"  -- '..' = String-Konkatenation (wie + in C#)
end
```

---

## script.Parent

```lua
local part = script.Parent  -- gibt das Objekt zurück dem das Script gehört
```

---

## Events (Touched)

```lua
part.Touched:Connect(function(objectTouched)
    print(objectTouched.Name .. " hat berührt!")
end)
```

**C#-Vergleich:** Wie `button.Click += (sender, e) => {}` — Event + Handler verbinden.

---

## Spieler erkennen (Humanoid-Pattern)

```lua
local function onTouch(objectTouched)
    local character = objectTouched.Parent          -- eine Ebene hoch (Fuß → Charakter)
    local humanoid = character:FindFirstChild("Humanoid")  -- gibt nil zurück wenn kein Spieler
    -- Robustere Variante (sucht nach Typ statt Name):
    -- local humanoid = character:FindFirstChildWhichIsA("Humanoid")

    if humanoid then  -- nil = false in Luau (wie != null in C#)
        -- Code nur für Spieler
    end
end
```

---

## Humanoid Properties

```lua
humanoid.Health = 0       -- Spieler töten
humanoid.WalkSpeed = 16   -- Standard-Geschwindigkeit
humanoid.WalkSpeed += 10  -- Geschwindigkeit erhöhen
```

---

## Debounce-Pattern

Verhindert dass Events zu schnell mehrfach feuern:

```lua
local active = true

local function onTouch(objectTouched)
    if active then
        active = false      -- sperren
        -- Code hier
        task.wait(1)        -- Cooldown
        active = true       -- freigeben
    end
end

-- Alternative: Part-Ebene (schaltet Touch-Erkennung komplett ab)
-- part.CanTouch = false
-- task.wait(1)
-- part.CanTouch = true
```

**C#-Vergleich:** Wie `bool isOnCooldown` bei einem Ability-System.

---

## task.wait()

```lua
task.wait(1)   -- pausiert 1 Sekunde, gibt anderen Code Zeit zu laufen
```

**C#-Vergleich:** Wie `await Task.Delay(1000)` — non-blocking pause.

---

## while-Loop

```lua
local raceActive = true
local timePassed = 0

while raceActive do       -- läuft solange raceActive true ist
    task.wait(1)
    timePassed += 1
end
```

**Wichtig:** Immer `task.wait()` im Loop verwenden, sonst friert das Spiel ein!

---

## elseif-Ketten

```lua
if timePassed <= 10 then
    print("Gold!")
elseif timePassed <= 20 then   -- > 10 ist redundant, da erster Block bereits false war
    print("Silber!")
elseif timePassed <= 30 then
    print("Bronze!")
else
    print("Try again!")
end
```

---

*Zuletzt aktualisiert: 24. April 2026*
