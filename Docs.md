

## 📦 Library Loading

```lua
-- Load Starlight UI Library
local Starlight = loadstring(game:HttpGet("https://raw.githubusercontent.com/txidstick/Update-Ui/refs/heads/main/Ui.lua"))()

-- Load NebulaIcons (Optional - for icons)
local NebulaIcons = loadstring(game:HttpGet("https://raw.nebulasoftworks.xyz/nebula-icon-library-loader"))()

-- Required Services
local Players = game:GetService("Players")
local UserInputService = game:GetService("UserInputService")
local RunService = game:GetService("RunService")
local LocalPlayer = Players.LocalPlayer

-- Mobile Detection
local isMobile = UserInputService.TouchEnabled and not UserInputService.KeyboardEnabled
```

---

## 🪟 Create Window

The window is the main container for your UI.

```lua
local Window = Starlight:CreateWindow({
    Name = "My Script Hub",              -- Main title
    Description = "Premium Features",    -- Subtitle text
    Icon = 7733955511,                   -- Roblox asset ID for icon
    IntroEnabled = true,                 -- Show intro animation
    Theme = "Starlight",                 -- Default theme
    AccentColor = Color3.fromRGB(80, 80, 80),  -- Custom accent color (grey)
    NotifyOnCallbackError = true,        -- Show errors in notifications
})
```

## 🔔 Notifications

Show popup notifications to the user.

```lua
Starlight:Notification({
    Title = "Welcome!",              -- Notification title
    Content = "UI loaded successfully",  -- Message content
    Duration = 3                     -- Duration in seconds
})
```

---

## 📑 Create Tab Section

Tab sections organize your tabs into groups.

```lua
-- Create main section for features
local MainSection = Window:CreateTabSection("Main")

-- Create settings section
local SettingsSection = Window:CreateTabSection("Settings")

-- Create utility section
local UtilitySection = Window:CreateTabSection("Utilities")
```

---

## 📂 Create Tabs

Tabs are the main navigation elements in your UI.

```lua
-- Home tab with Material icon
local HomeTab = MainSection:CreateTab({
    Name = "Home",
    Icon = NebulaIcons:GetIcon("home", "Material"),
    Visible = true
}, 1)  -- Index 1

-- Player tab
local PlayerTab = MainSection:CreateTab({
    Name = "Player",
    Icon = NebulaIcons:GetIcon("person", "Material"),
    Visible = true
}, 2)  -- Index 2

-- Combat tab with Lucide icon
local CombatTab = MainSection:CreateTab({
    Name = "Combat",
    Icon = NebulaIcons:GetIcon("swords", "Lucide"),
    Visible = true
}, 3)  -- Index 3

-- Visuals tab
local VisualsTab = MainSection:CreateTab({
    Name = "Visuals",
    Icon = NebulaIcons:GetIcon("eye", "Lucide"),
    Visible = true
}, 4)

-- Misc tab
local MiscTab = MainSection:CreateTab({
    Name = "Misc",
    Icon = NebulaIcons:GetIcon("apps", "Material"),
    Visible = true
}, 5)

-- Settings tab
local SettingsTab = SettingsSection:CreateTab({
    Name = "Settings",
    Icon = NebulaIcons:GetIcon("settings", "Material"),
    Visible = true
}, 1)
```

### Icon Sources

| Source | Description | Example Icons |
|--------|-------------|---------------|
| `Material` | Google Material Design icons | home, person, settings, apps, sun |
| `Lucide` | Lucide icon library | swords, eye, shield, target, arrow-up |
| `Phosphor` | Phosphor icon set | Various modern icons |

### Popular Icons

```lua
-- Navigation icons
NebulaIcons:GetIcon("home", "Material")
NebulaIcons:GetIcon("settings", "Material")
NebulaIcons:GetIcon("apps", "Material")

-- Player icons
NebulaIcons:GetIcon("person", "Material")
NebulaIcons:GetIcon("directions_run", "Material")

-- Combat icons
NebulaIcons:GetIcon("swords", "Lucide")
NebulaIcons:GetIcon("target", "Lucide")
NebulaIcons:GetIcon("shield", "Lucide")

-- Visual icons
NebulaIcons:GetIcon("eye", "Lucide")
NebulaIcons:GetIcon("sun", "Lucide")
NebulaIcons:GetIcon("moon", "Lucide")

-- Utility icons
NebulaIcons:GetIcon("arrow-up", "Lucide")
NebulaIcons:GetIcon("square", "Lucide")
NebulaIcons:GetIcon("code", "Material")
NebulaIcons:GetIcon("coins", "Lucide")
```

---

## 📦 Create Groupbox

Groupboxes are containers that hold UI elements within a tab.

```lua
-- Left column groupbox
local MyGroupbox = HomeTab:CreateGroupbox({
    Name = "My Features",
    Column = 1    -- Left side
}, 1)  -- Index 1

-- Right column groupbox
local MyGroupbox2 = HomeTab:CreateGroupbox({
    Name = "More Features",
    Column = 2    -- Right side
}, 2)  -- Index 2
```

```lua
-- Player movement groupbox (left)
local PlayerMovement = PlayerTab:CreateGroupbox({
    Name = "Movement Controls",
    Column = 1
}, 1)

-- Player character groupbox (right)
local PlayerCharacter = PlayerTab:CreateGroupbox({
    Name = "Character Options",
    Column = 2
}, 2)

-- Combat aimbot groupbox (left)
local CombatAimbot = CombatTab:CreateGroupbox({
    Name = "Aimbot Settings",
    Column = 1
}, 1)

-- Combat weapons groupbox (right)
local CombatWeapons = CombatTab:CreateGroupbox({
    Name = "Weapon Mods",
    Column = 2
}, 2)
```

---

## 🏷️ Create Label

Labels display static or dynamic text.

```lua
-- Simple label
MyGroupbox:CreateLabel({
    Name = "This is a label"
}, 1)  -- Index 1

-- Dynamic label with player name
MyGroupbox:CreateLabel({
    Name = "Welcome, " .. LocalPlayer.Name
}, 2)  -- Index 2

-- Info label with player data
MyGroupbox:CreateLabel({
    Name = "User ID: " .. LocalPlayer.UserId
}, 3)

-- Status label
MyGroupbox:CreateLabel({
    Name = "Account Age: " .. LocalPlayer.AccountAge .. " days"
}, 4)
```

### Use Cases

```lua
-- Version info
HomeInfo:CreateLabel({Name = "Version 3.0 - December 2025"}, 1)

-- Feature list
HomeInfo:CreateLabel({Name = "• Complete UI redesign"}, 2)
HomeInfo:CreateLabel({Name = "• Mobile optimization"}, 3)
HomeInfo:CreateLabel({Name = "• New color picker"}, 4)

-- Credits
UtilityBox:CreateLabel({Name = "© 2025 sev.cc Premium"}, 1)

-- Instructions
SettingsBox:CreateLabel({Name = "Auto-save: Enabled"}, 1)
```

---

## ➖ Create Divider

Dividers create visual separation between elements.

```lua
-- Add a divider line
MyGroupbox:CreateDivider()
```

### Example Usage

```lua
-- Separate sections
PlayerBox:CreateButton({Name = "Reset"}, 1)
PlayerBox:CreateButton({Name = "Respawn"}, 2)
PlayerBox:CreateDivider()  -- Visual separator
PlayerBox:CreateToggle({Name = "God Mode"}, 1)
PlayerBox:CreateToggle({Name = "Infinite Health"}, 2)
```

---

## 🔘 Create Button

Buttons execute functions when clicked.

```lua
-- Primary button (Style 1 - filled)
MyGroupbox:CreateButton({
    Name = "Click Me",
    Style = 1,    -- Primary style (filled)
    Callback = function()
        print("Button clicked!")
        Starlight:Notification({
            Title = "Button",
            Content = "You clicked the button!",
            Duration = 2
        })
    end
}, 1)  -- Index 1

-- Secondary button (Style 2 - outlined)
MyGroupbox:CreateButton({
    Name = "Secondary Button",
    Style = 2,    -- Secondary style (outlined)
    Callback = function()
        print("Secondary clicked")
    end
}, 2)  -- Index 2
```

---

## 🎚️ Create Toggle

Toggles are switches that enable/disable features.

```lua
-- Basic toggle
MyGroupbox:CreateToggle({
    Name = "Enable Feature",
    CurrentValue = false,    -- Initial state (off)
    Callback = function(value)
        print("Toggle state:", value)
        if value then
            print("Feature enabled!")
        else
            print("Feature disabled!")
        end
    end
}, 1)  -- Index 1

-- Toggle with icon
MyGroupbox:CreateToggle({
    Name = "God Mode",
    Icon = NebulaIcons:GetIcon("shield", "Lucide"),
    CurrentValue = false,
    Callback = function(value)
        _G.GodMode = value
        print("God Mode:", value and "ON" or "OFF")
    end
}, 2)  -- Index 2
```

---

## 🎛️ Create Slider

Sliders let users select numeric values by dragging.

```lua
-- WalkSpeed slider with icon
MyGroupbox:CreateSlider({
    Name = "WalkSpeed",
    Icon = NebulaIcons:GetIcon("directions_run", "Material"),
    CurrentValue = 16,       -- Starting value
    Range = {16, 100},      -- {minimum, maximum}
    Increment = 1,          -- Step size
    Suffix = " speed",      -- Text after value
    Callback = function(value)
        print("WalkSpeed set to:", value)
        if LocalPlayer.Character and LocalPlayer.Character:FindFirstChild("Humanoid") then
            LocalPlayer.Character.Humanoid.WalkSpeed = value
        end
    end
}, 1)  -- Index 1

```

### Slider Parameters

| Parameter | Type | Description | Example |
|-----------|------|-------------|---------|
| `Name` | string | Slider label | "WalkSpeed" |
| `Icon` | image | Optional icon | NebulaIcons:GetIcon(...) |
| `CurrentValue` | number | Starting value | 16 |
| `Range` | table | {min, max} | {16, 100} |
| `Increment` | number | Step size | 1 or 0.5 |
| `Suffix` | string | Text after value | " speed" or "x" |
| `Callback` | function | Called on change | function(value) ... end |

### Mobile Touch Support

Sliders automatically support touch dragging on mobile devices. The slider knob is optimized for mobile with:
- 20x20 circular touch target
- Direct position calculation (no animation lag)
- Smooth drag response
- Works with both mouse and touch input

---

## ✏️ Create Input

Text input fields for user-entered text.

```lua
-- Basic input
MyGroupbox:CreateInput({
    Name = "Enter Text",
    PlaceholderText = "Type here...",  -- Placeholder text
    RemoveTextOnFocus = false,         -- Keep text when clicked
    Callback = function(text)
        print("Input text:", text)
    end
}, 1)  -- Index 1

```

### Input Parameters

| Parameter | Type | Description | Example |
|-----------|------|-------------|---------|
| `Name` | string | Input label | "Enter Text" |
| `PlaceholderText` | string | Placeholder hint | "Type here..." |
| `RemoveTextOnFocus` | boolean | Clear on click | true or false |
| `Callback` | function | Called on submit | function(text) ... end |

---

## 📋 Create Dropdown

Dropdowns provide selection from a list of options.

> **Important:** Dropdowns must be created using `CreateLabel():AddDropdown()` pattern

```lua
-- Single selection dropdown
local dropdown1 = MyGroupbox:CreateLabel({Name = "Select Option"}, 3):AddDropdown({
    Options = {"Option 1", "Option 2", "Option 3", "Option 4"},
    CurrentOption = "Option 1",  -- Default selected
    MultipleOptions = false,     -- Single selection only
    Callback = function(value)
        print("Selected:", value)
    end
}, 1)  -- AddDropdown index

```

### Dropdown Parameters

| Parameter | Type | Description | Example |
|-----------|------|-------------|---------|
| `Options` | table | List of options | {"A", "B", "C"} |
| `CurrentOption` | string/table | Default selection | "A" or {"A", "B"} |
| `MultipleOptions` | boolean | Allow multiple | true or false |
| `Callback` | function | Called on change | function(value) ... end |

### Dropdown vs Multiple Selection

```lua
-- Single Selection (returns string)
Callback = function(value)
    print(value)  -- "Option 1"
end

-- Multiple Selection (returns table)
Callback = function(values)
    for i, v in pairs(values) do
        print(i, v)  -- 1, "Option 1"  |  2, "Option 2"
    end
end
```

---

## 🎨 Change Theme

Change the UI theme programmatically or with a dropdown.

### Programmatic Theme Change

```lua
-- Change theme directly
Window:SetTheme("Hollywood Dark")

-- Change with notification
Window:SetTheme("Orca")
Starlight:Notification({
    Title = "Theme Changed",
    Content = "Now using Orca theme",
    Duration = 2
})
```

### Theme Dropdown

```lua
local SettingsTheme = SettingsTab:CreateGroupbox({
    Name = "Theme Settings",
    Column = 1
}, 1)

SettingsTheme:CreateLabel({Name = "UI Theme"}, 1):AddDropdown({
    Options = {"Starlight", "Hollywood Dark", "Hollywood Light", "Orca", "Glacier", "Pacific"},
    CurrentOption = "Starlight",
    MultipleOptions = false,
    Callback = function(theme)
        Window:SetTheme(theme)
        Starlight:Notification({
            Title = "Theme Changed",
            Content = "Applied theme: " .. theme,
            Duration = 2
        })
    end
}, 1)
```

### Available Themes

| Theme | Style | Accent Color |
|-------|-------|--------------|
| **Starlight** | Light with grey accents | Grey (#505050) |
| **Hollywood Dark** | Dark with grey accents | Grey (#505050) |
| **Hollywood Light** | Bright light theme | Grey (#505050) |
| **Orca** | Dark blue theme | Blue |
| **Glacier** | Ice blue theme | Light Blue |
| **Pacific** | Ocean blue theme | Ocean Blue |

### Custom Accent Color

```lua
-- Set custom accent color when creating window
local Window = Starlight:CreateWindow({
    Name = "My Hub",
    AccentColor = Color3.fromRGB(80, 80, 80),  -- Grey
    -- or
    AccentColor = Color3.fromRGB(255, 100, 100),  -- Red
    -- or  
    AccentColor = Color3.fromRGB(100, 255, 100),  -- Green
})
```


---

## 🎯 Quick Reference

### Element Index Chart

All elements require an Index parameter for ordering:

```lua
-- Groupbox indices
Groupbox1 = Tab:CreateGroupbox({...}, 1)  -- First groupbox
Groupbox2 = Tab:CreateGroupbox({...}, 2)  -- Second groupbox

-- Element indices within groupbox
Groupbox1:CreateLabel({...}, 1)   -- First element
Groupbox1:CreateButton({...}, 2)  -- Second element  
Groupbox1:CreateToggle({...}, 3)  -- Third element
Groupbox1:CreateSlider({...}, 4)  -- Fourth element
```

### Common Patterns

```lua
-- Pattern: Label + Dropdown
Groupbox:CreateLabel({Name = "Options"}, 1):AddDropdown({
    Options = {"A", "B", "C"},
    CurrentOption = "A",
    MultipleOptions = false,
    Callback = function(value) print(value) end
}, 1)

-- Pattern: Icon + Element
Groupbox:CreateToggle({
    Name = "Feature",
    Icon = NebulaIcons:GetIcon("icon_name", "Material"),
    CurrentValue = false,
    Callback = function(value) end
}, 1)

-- Pattern: Slider with Character Check
Groupbox:CreateSlider({
    Name = "Value",
    CurrentValue = 50,
    Range = {1, 100},
    Increment = 1,
    Callback = function(value)
        if LocalPlayer.Character then
            -- Apply value
        end
    end
}, 1)
```

---

## 📱 Mobile Optimization

The UI is fully optimized for mobile devices:

### Automatic Features
- ✅ Touch input detection
- ✅ Slider drag with touch
- ✅ Optimized button sizes
- ✅ Responsive layout
- ✅ No animation lag

### Mobile Detection

```lua
local isMobile = UserInputService.TouchEnabled and not UserInputService.KeyboardEnabled

if isMobile then
    print("Running on mobile device")
else
    print("Running on desktop")
end
```

### Mobile-Specific Code

```lua
-- Adjust for mobile
if isMobile then
    -- Larger touch targets
    -- Simplified UI
    -- Reduced effects
end
```

---

## ⚠️ Common Errors & Fixes

### Error: "missing method CreateDropdown"
**Fix:** Use `CreateLabel():AddDropdown()` pattern instead

```lua
-- ❌ Wrong
Groupbox:CreateDropdown({...})

-- ✅ Correct
Groupbox:CreateLabel({Name = "Dropdown"}, 1):AddDropdown({...}, 1)
```

### Error: "Index required"
**Fix:** All elements need an Index parameter

```lua
-- ❌ Wrong
Groupbox:CreateButton({Name = "Click"})

-- ✅ Correct
Groupbox:CreateButton({Name = "Click"}, 1)
```

### Error: "Character not found"
**Fix:** Always check if Character exists

```lua
-- ❌ Wrong
LocalPlayer.Character.Humanoid.WalkSpeed = 50

-- ✅ Correct
if LocalPlayer.Character and LocalPlayer.Character:FindFirstChild("Humanoid") then
    LocalPlayer.Character.Humanoid.WalkSpeed = 50
end
```

---

## 🔧 Advanced Tips

### Global Variables

Use `_G` for persistent state across scripts:

```lua
-- Set global
_G.GodMode = true
_G.WalkSpeed = 50

-- Access from another script
if _G.GodMode then
    print("God Mode is enabled")
end
```

### Error Handling

```lua
-- Use pcall for risky operations
local success, error = pcall(function()
    LocalPlayer.Character.Humanoid.WalkSpeed = 200
end)

if not success then
    print("Error:", error)
    Starlight:Notification({
        Title = "Error",
        Content = "Failed to set WalkSpeed",
        Duration = 3
    })
end
```

### Debouncing

```lua
-- Prevent spam clicks
local debounce = false

Button:CreateButton({
    Name = "Click",
    Style = 1,
    Callback = function()
        if debounce then return end
        debounce = true
        
        print("Button clicked!")
        
        wait(1)  -- 1 second cooldown
        debounce = false
    end
}, 1)
```

### Save/Load Settings

```lua
-- Save settings
local Settings = {
    WalkSpeed = 50,
    JumpPower = 100,
    GodMode = true
}

writefile("settings.json", game:GetService("HttpService"):JSONEncode(Settings))

-- Load settings
if isfile("settings.json") then
    local data = readfile("settings.json")
    Settings = game:GetService("HttpService"):JSONDecode(data)
    print("Settings loaded:", Settings.WalkSpeed)
end
```



