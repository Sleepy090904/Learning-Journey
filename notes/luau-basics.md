# Luau Basics — Notizen

> Vergleiche immer mit C# für schnelleres Verständnis.

## Variablen

```lua
-- Luau: 'local' = scope-begrenzte Variable (wie 'var' in C# aber zwingend nötig!)
local name = "Bruce"
local age = 21
local isPlaying = true

-- OHNE 'local' = globale Variable (vermeiden! wie public static in C#)
globalVar = "gefährlich"
```

**C#-Vergleich:** In C# ist der Scope durch `{}` bestimmt. In Luau musst du `local` explizit schreiben, sonst ist die Variable global.

---

## Funktionen

```lua
-- Einfache Funktion
local function greet(playerName: string): string
    return "Hallo, " .. playerName .. "!"
end

-- Aufruf
local message = greet("Bruce")
print(message) -- "Hallo, Bruce!"
```

**C#-Vergleich:**
```csharp
string Greet(string playerName) {
    return "Hallo, " + playerName + "!";
}
```

---

## Events (Roblox-spezifisch)

```lua
-- Part im Workspace berühren
local part = workspace.Part

-- Event verbinden (wie += in C#)
part.Touched:Connect(function(otherPart)
    print(otherPart.Name .. " hat den Part berührt!")
end)
```

**C#-Vergleich:**
```csharp
// C# Delegate/Event
button.Click += (sender, e) => {
    Console.WriteLine("Geklickt!");
};
```

---

## Parameter

```lua
-- Funktion mit Parameter
local function onTouched(hit)  -- 'hit' = das Objekt das berührt hat
    if hit.Parent:FindFirstChild("Humanoid") then
        print("Ein Spieler hat berührt!")
    end
end

part.Touched:Connect(onTouched)
```

---

*Zuletzt aktualisiert: 24. April 2026*
