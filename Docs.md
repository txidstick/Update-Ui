

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

### Examples

```lua
-- Success notification
Starlight:Notification({
    Title = "Success",
    Content = "Feature enabled!",
    Duration = 2
})

-- Warning notification
Starlight:Notification({
    Title = "Warning",
    Content = "This may cause lag",
    Duration = 3
})

-- Error notification
Starlight:Notification({
    Title = "Error",
    Content = "Failed to execute",
    Duration = 4
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

```lua
-- Copy profile link
HomeInfo:CreateButton({
    Name = "Copy Profile Link",
    Style = 1,
    Callback = function()
        setclipboard("https://www.roblox.com/users/" .. LocalPlayer.UserId)
        Starlight:Notification({
            Title = "Copied!",
            Content = "Profile link copied to clipboard",
            Duration = 2
        })
    end
}, 1)

-- Join Discord
HomeInfo:CreateButton({
    Name = "Join Discord",
    Style = 2,
    Callback = function()
        setclipboard("discord.gg/sevcc")
        Starlight:Notification({
            Title = "Discord Link",
            Content = "Discord invite copied!",
            Duration = 2
        })
    end
}, 2)

-- Reset character
PlayerBox:CreateButton({
    Name = "Reset Character",
    Style = 1,
    Callback = function()
        if LocalPlayer.Character and LocalPlayer.Character:FindFirstChild("Humanoid") then
            LocalPlayer.Character.Humanoid.Health = 0
            print("Character reset!")
        end
    end
}, 1)

-- Rejoin server
UtilityBox:CreateButton({
    Name = "Rejoin Server",
    Style = 2,
    Callback = function()
        game:GetService("TeleportService"):TeleportToPlaceInstance(
            game.PlaceId, 
            game.JobId, 
            LocalPlayer
        )
    end
}, 2)

-- Copy JobId
UtilityBox:CreateButton({
    Name = "Copy JobId",
    Style = 2,
    Callback = function()
        setclipboard(game.JobId)
        Starlight:Notification({
            Title = "Copied",
            Content = "Server JobId copied!",
            Duration = 2
        })
    end
}, 3)

-- Collect items
MiscBox:CreateButton({
    Name = "Collect All Items",
    Style = 1,
    Callback = function()
        print("Collecting all items...")
        Starlight:Notification({
            Title = "Collecting",
            Content = "Collecting all nearby items...",
            Duration = 2
        })
    end
}, 1)

-- Anti-AFK
MiscBox:CreateButton({
    Name = "Anti-AFK",
    Style = 1,
    Callback = function()
        print("Anti-AFK activated!")
        Starlight:Notification({
            Title = "Anti-AFK",
            Content = "Anti-AFK is now active",
            Duration = 2
        })
    end
}, 1)
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

### Common Toggle Examples

```lua
-- Movement toggles
PlayerMovement:CreateToggle({
    Name = "Infinite Jump",
    CurrentValue = false,
    Callback = function(value)
        _G.InfiniteJump = value
        print("Infinite Jump:", value and "ON" or "OFF")
    end
}, 1)

PlayerMovement:CreateToggle({
    Name = "No Clip",
    CurrentValue = false,
    Callback = function(value)
        _G.NoClip = value
        print("No Clip:", value and "ON" or "OFF")
    end
}, 2)

-- Character toggles
PlayerCharacter:CreateToggle({
    Name = "God Mode",
    CurrentValue = false,
    Callback = function(value)
        _G.GodMode = value
        print("God Mode:", value and "ACTIVE" or "INACTIVE")
    end
}, 1)

PlayerCharacter:CreateToggle({
    Name = "Infinite Stamina",
    CurrentValue = false,
    Callback = function(value)
        _G.InfStamina = value
        print("Infinite Stamina:", value and "ON" or "OFF")
    end
}, 2)

-- Combat toggles
CombatAimbot:CreateToggle({
    Name = "Enable Aimbot",
    Icon = NebulaIcons:GetIcon("target", "Lucide"),
    CurrentValue = false,
    Callback = function(value)
        _G.Aimbot = value
        print("Aimbot:", value and "ENABLED" or "DISABLED")
    end
}, 1)

CombatAimbot:CreateToggle({
    Name = "Silent Aim",
    CurrentValue = false,
    Callback = function(value)
        _G.SilentAim = value
        print("Silent Aim:", value and "ON" or "OFF")
    end
}, 2)

CombatAimbot:CreateToggle({
    Name = "Show FOV Circle",
    CurrentValue = true,
    Callback = function(value)
        _G.ShowFOV = value
        print("FOV Circle:", value and "VISIBLE" or "HIDDEN")
    end
}, 3)

-- Weapon toggles
CombatWeapons:CreateToggle({
    Name = "Infinite Ammo",
    CurrentValue = false,
    Callback = function(value)
        _G.InfiniteAmmo = value
        print("Infinite Ammo:", value and "ACTIVE" or "INACTIVE")
    end
}, 1)

CombatWeapons:CreateToggle({
    Name = "No Recoil",
    CurrentValue = false,
    Callback = function(value)
        _G.NoRecoil = value
        print("No Recoil:", value and "ON" or "OFF")
    end
}, 2)

CombatWeapons:CreateToggle({
    Name = "Rapid Fire",
    CurrentValue = false,
    Callback = function(value)
        _G.RapidFire = value
        print("Rapid Fire:", value and "ENABLED" or "DISABLED")
    end
}, 3)

CombatWeapons:CreateToggle({
    Name = "Auto Reload",
    CurrentValue = false,
    Callback = function(value)
        _G.AutoReload = value
        print("Auto Reload:", value and "ON" or "OFF")
    end
}, 4)

-- ESP toggles
VisualsESP:CreateToggle({
    Name = "Player Box ESP",
    Icon = NebulaIcons:GetIcon("square", "Lucide"),
    CurrentValue = false,
    Callback = function(value)
        _G.BoxESP = value
        print("Box ESP:", value and "ON" or "OFF")
    end
}, 1)

VisualsESP:CreateToggle({
    Name = "Player Name ESP",
    CurrentValue = false,
    Callback = function(value)
        _G.NameESP = value
        print("Name ESP:", value and "ON" or "OFF")
    end
}, 2)

VisualsESP:CreateToggle({
    Name = "Distance ESP",
    CurrentValue = false,
    Callback = function(value)
        _G.DistanceESP = value
        print("Distance ESP:", value and "ON" or "OFF")
    end
}, 3)

VisualsESP:CreateToggle({
    Name = "Health Bar ESP",
    CurrentValue = false,
    Callback = function(value)
        _G.HealthESP = value
        print("Health ESP:", value and "ON" or "OFF")
    end
}, 4)

VisualsESP:CreateToggle({
    Name = "Tracers",
    CurrentValue = false,
    Callback = function(value)
        _G.Tracers = value
        print("Tracers:", value and "VISIBLE" or "HIDDEN")
    end
}, 5)

-- World toggles
VisualsWorld:CreateToggle({
    Name = "Fullbright",
    Icon = NebulaIcons:GetIcon("sun", "Lucide"),
    CurrentValue = false,
    Callback = function(value)
        _G.Fullbright = value
        local lighting = game:GetService("Lighting")
        if value then
            lighting.Brightness = 2
            lighting.ClockTime = 14
            lighting.FogEnd = 100000
            lighting.GlobalShadows = false
        else
            lighting.Brightness = 1
            lighting.ClockTime = 12
            lighting.FogEnd = 1000
            lighting.GlobalShadows = true
        end
        print("Fullbright:", value and "ENABLED" or "DISABLED")
    end
}, 1)

VisualsWorld:CreateToggle({
    Name = "Remove Fog",
    CurrentValue = false,
    Callback = function(value)
        local lighting = game:GetService("Lighting")
        if value then
            lighting.FogEnd = 100000
        else
            lighting.FogEnd = 1000
        end
        print("Remove Fog:", value and "ON" or "OFF")
    end
}, 2)

VisualsWorld:CreateToggle({
    Name = "Highlight Players",
    CurrentValue = false,
    Callback = function(value)
        _G.HighlightPlayers = value
        print("Highlight Players:", value and "ACTIVE" or "INACTIVE")
    end
}, 3)

-- Misc toggles
MiscFarm:CreateToggle({
    Name = "Auto Farm Coins",
    Icon = NebulaIcons:GetIcon("coins", "Lucide"),
    CurrentValue = false,
    Callback = function(value)
        _G.AutoFarmCoins = value
        print("Auto Farm Coins:", value and "RUNNING" or "STOPPED")
    end
}, 1)

MiscFarm:CreateToggle({
    Name = "Auto Farm XP",
    CurrentValue = false,
    Callback = function(value)
        _G.AutoFarmXP = value
        print("Auto Farm XP:", value and "RUNNING" or "STOPPED")
    end
}, 2)

-- Settings toggles
SettingsBox:CreateToggle({
    Name = "Show Animations",
    CurrentValue = true,
    Callback = function(value)
        print("Animations:", value and "On" or "Off")
    end
}, 1)

SettingsBox:CreateToggle({
    Name = "Show Notifications",
    CurrentValue = true,
    Callback = function(value)
        print("Notifications:", value and "Enabled" or "Disabled")
    end
}, 2)

SettingsBox:CreateToggle({
    Name = "Auto Load Config",
    CurrentValue = false,
    Callback = function(value)
        print("Auto load:", value and "On" or "Off")
    end
}, 3)
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

-- Multiplier slider with decimals
MyGroupbox:CreateSlider({
    Name = "Damage Multiplier",
    CurrentValue = 1,
    Range = {1, 5},
    Increment = 0.5,  -- 0.5 step (1, 1.5, 2, 2.5, 3, etc)
    Suffix = "x",
    Callback = function(value)
        _G.DamageMultiplier = value
        print("Damage Multiplier:", value .. "x")
    end
}, 2)  -- Index 2
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

### Common Slider Examples

```lua
-- Movement sliders
PlayerMovement:CreateSlider({
    Name = "WalkSpeed",
    Icon = NebulaIcons:GetIcon("directions_run", "Material"),
    CurrentValue = 16,
    Range = {16, 200},
    Increment = 1,
    Suffix = " speed",
    Callback = function(value)
        if LocalPlayer.Character and LocalPlayer.Character:FindFirstChild("Humanoid") then
            LocalPlayer.Character.Humanoid.WalkSpeed = value
        end
    end
}, 1)

PlayerMovement:CreateSlider({
    Name = "Jump Height",
    Icon = NebulaIcons:GetIcon("arrow-up", "Lucide"),
    CurrentValue = 50,
    Range = {50, 300},
    Increment = 5,
    Suffix = " power",
    Callback = function(value)
        if LocalPlayer.Character and LocalPlayer.Character:FindFirstChild("Humanoid") then
            LocalPlayer.Character.Humanoid.JumpPower = value
        end
    end
}, 2)

-- Combat sliders
CombatAimbot:CreateSlider({
    Name = "Aim Smoothness",
    CurrentValue = 5,
    Range = {1, 10},
    Increment = 1,
    Suffix = "",
    Callback = function(value)
        _G.AimSmooth = value
        print("Aim Smoothness:", value)
    end
}, 1)

CombatAimbot:CreateSlider({
    Name = "FOV Circle Size",
    CurrentValue = 150,
    Range = {50, 500},
    Increment = 10,
    Suffix = " px",
    Callback = function(value)
        _G.FOVSize = value
        print("FOV Size:", value)
    end
}, 2)

CombatWeapons:CreateSlider({
    Name = "Damage Multiplier",
    CurrentValue = 1,
    Range = {1, 5},
    Increment = 0.5,
    Suffix = "x",
    Callback = function(value)
        _G.DamageMultiplier = value
        print("Damage Multiplier:", value .. "x")
    end
}, 1)

-- Visual sliders
VisualsWorld:CreateSlider({
    Name = "Camera FOV",
    CurrentValue = 70,
    Range = {70, 120},
    Increment = 1,
    Suffix = "°",
    Callback = function(value)
        if workspace.CurrentCamera then
            workspace.CurrentCamera.FieldOfView = value
        end
        print("Camera FOV:", value)
    end
}, 1)

VisualsESP:CreateSlider({
    Name = "ESP Distance",
    CurrentValue = 1000,
    Range = {100, 5000},
    Increment = 100,
    Suffix = " studs",
    Callback = function(value)
        _G.ESPDistance = value
        print("ESP Distance:", value)
    end
}, 1)

-- Misc sliders
MiscSettings:CreateSlider({
    Name = "Farm Speed",
    CurrentValue = 5,
    Range = {1, 10},
    Increment = 1,
    Suffix = " speed",
    Callback = function(value)
        _G.FarmSpeed = value
        print("Farm Speed:", value)
    end
}, 1)

MiscSettings:CreateSlider({
    Name = "Collection Radius",
    CurrentValue = 50,
    Range = {10, 200},
    Increment = 10,
    Suffix = " studs",
    Callback = function(value)
        _G.CollectRadius = value
        print("Collection Radius:", value)
    end
}, 2)
```

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

-- Command input (clears on focus)
MyGroupbox:CreateInput({
    Name = "Command",
    PlaceholderText = "/help",
    RemoveTextOnFocus = true,  -- Clear text when clicked
    Callback = function(text)
        print("Executing command:", text)
    end
}, 2)  -- Index 2
```

### Input Parameters

| Parameter | Type | Description | Example |
|-----------|------|-------------|---------|
| `Name` | string | Input label | "Enter Text" |
| `PlaceholderText` | string | Placeholder hint | "Type here..." |
| `RemoveTextOnFocus` | boolean | Clear on click | true or false |
| `Callback` | function | Called on submit | function(text) ... end |

### Common Input Examples

```lua
-- Username input
PlayerBox:CreateInput({
    Name = "Target Player",
    PlaceholderText = "Enter username...",
    RemoveTextOnFocus = false,
    Callback = function(text)
        print("Target set to:", text)
        _G.TargetPlayer = text
    end
}, 1)

-- Command input
MiscUtils:CreateInput({
    Name = "Custom Command",
    PlaceholderText = "Enter command...",
    RemoveTextOnFocus = false,
    Callback = function(text)
        print("Command executed:", text)
    end
}, 1)

-- Config name input
SettingsConfig:CreateInput({
    Name = "Config Name",
    PlaceholderText = "Enter config name...",
    RemoveTextOnFocus = false,
    Callback = function(text)
        print("Config name:", text)
        _G.ConfigName = text
    end
}, 1)

-- Search input
UtilityBox:CreateInput({
    Name = "Search Player",
    PlaceholderText = "Type player name...",
    RemoveTextOnFocus = true,
    Callback = function(text)
        print("Searching for:", text)
        -- Search logic here
    end
}, 1)

-- Teleport coordinates
PlayerTeleport:CreateInput({
    Name = "X Coordinate",
    PlaceholderText = "0",
    RemoveTextOnFocus = false,
    Callback = function(text)
        local x = tonumber(text)
        if x then
            _G.TeleportX = x
            print("X set to:", x)
        end
    end
}, 1)

PlayerTeleport:CreateInput({
    Name = "Y Coordinate",
    PlaceholderText = "0",
    RemoveTextOnFocus = false,
    Callback = function(text)
        local y = tonumber(text)
        if y then
            _G.TeleportY = y
            print("Y set to:", y)
        end
    end
}, 2)

PlayerTeleport:CreateInput({
    Name = "Z Coordinate",
    PlaceholderText = "0",
    RemoveTextOnFocus = false,
    Callback = function(text)
        local z = tonumber(text)
        if z then
            _G.TeleportZ = z
            print("Z set to:", z)
        end
    end
}, 3)

-- Chat message input
MiscChat:CreateInput({
    Name = "Chat Message",
    PlaceholderText = "Type message...",
    RemoveTextOnFocus = true,
    Callback = function(text)
        game:GetService("ReplicatedStorage").DefaultChatSystemChatEvents.SayMessageRequest:FireServer(text, "All")
    end
}, 1)
```

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

-- Multiple selection dropdown
local dropdown2 = MyGroupbox:CreateLabel({Name = "Select Multiple"}, 4):AddDropdown({
    Options = {"Red", "Blue", "Green", "Yellow"},
    CurrentOption = {"Red", "Blue"},  -- Multiple defaults (table)
    MultipleOptions = true,           -- Allow multiple selections
    Callback = function(values)
        print("Selected options:")
        for i, v in pairs(values) do
            print(i, v)
        end
    end
}, 2)  -- AddDropdown index
```

### Dropdown Parameters

| Parameter | Type | Description | Example |
|-----------|------|-------------|---------|
| `Options` | table | List of options | {"A", "B", "C"} |
| `CurrentOption` | string/table | Default selection | "A" or {"A", "B"} |
| `MultipleOptions` | boolean | Allow multiple | true or false |
| `Callback` | function | Called on change | function(value) ... end |

### Common Dropdown Examples

```lua
-- Teleport location dropdown
PlayerCharacter:CreateLabel({Name = "Teleport Location"}, 4):AddDropdown({
    Options = {"Spawn Point", "Shop Area", "Safe Zone", "Arena", "Secret Room"},
    CurrentOption = "Spawn Point",
    MultipleOptions = false,
    Callback = function(value)
        print("Teleporting to:", value)
        -- Teleport logic here
        if value == "Spawn Point" then
            -- Teleport to spawn
        elseif value == "Shop Area" then
            -- Teleport to shop
        elseif value == "Safe Zone" then
            -- Teleport to safe zone
        elseif value == "Arena" then
            -- Teleport to arena
        elseif value == "Secret Room" then
            -- Teleport to secret room
        end
    end
}, 1)

-- Farm speed dropdown
MiscFarm:CreateLabel({Name = "Farm Speed"}, 4):AddDropdown({
    Options = {"Slow", "Normal", "Fast", "Ultra Fast"},
    CurrentOption = "Normal",
    MultipleOptions = false,
    Callback = function(value)
        print("Farm Speed set to:", value)
        if value == "Slow" then
            _G.FarmSpeed = 1
        elseif value == "Normal" then
            _G.FarmSpeed = 2
        elseif value == "Fast" then
            _G.FarmSpeed = 3
        elseif value == "Ultra Fast" then
            _G.FarmSpeed = 5
        end
    end
}, 1)

-- Theme selection dropdown
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

-- Weapon selection dropdown
CombatWeapons:CreateLabel({Name = "Select Weapon"}, 1):AddDropdown({
    Options = {"Sword", "Gun", "Bow", "Staff", "Axe"},
    CurrentOption = "Sword",
    MultipleOptions = false,
    Callback = function(weapon)
        print("Selected weapon:", weapon)
        _G.CurrentWeapon = weapon
    end
}, 1)

-- ESP type dropdown (multiple selection)
VisualsESP:CreateLabel({Name = "ESP Types"}, 1):AddDropdown({
    Options = {"Box", "Name", "Distance", "Health", "Tracers"},
    CurrentOption = {"Box", "Name"},
    MultipleOptions = true,
    Callback = function(types)
        print("Enabled ESP types:")
        for i, espType in pairs(types) do
            print("-", espType)
        end
        _G.ESPTypes = types
    end
}, 1)

-- Game mode dropdown
MiscSettings:CreateLabel({Name = "Game Mode"}, 1):AddDropdown({
    Options = {"PvP", "PvE", "Farming", "Trading", "Exploration"},
    CurrentOption = "PvP",
    MultipleOptions = false,
    Callback = function(mode)
        print("Game mode set to:", mode)
        _G.GameMode = mode
    end
}, 1)

-- Target selection dropdown
PlayerTarget:CreateLabel({Name = "Target Player"}, 1):AddDropdown({
    Options = {"All", "Friends", "Enemies", "Admins", "VIPs"},
    CurrentOption = "All",
    MultipleOptions = false,
    Callback = function(target)
        print("Targeting:", target)
        _G.TargetType = target
    end
}, 1)

-- Auto-collect items (multiple)
MiscCollect:CreateLabel({Name = "Collect Items"}, 1):AddDropdown({
    Options = {"Coins", "Gems", "Weapons", "Armor", "Potions", "Food"},
    CurrentOption = {"Coins", "Gems"},
    MultipleOptions = true,
    Callback = function(items)
        print("Auto-collecting:")
        for i, item in pairs(items) do
            print("-", item)
        end
        _G.CollectItems = items
    end
}, 1)
```

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

## 📖 Complete Working Example

Full implementation of a feature-rich UI with all elements.

```lua
local ExampleTab = Window:CreateTabSection("Examples"):CreateTab({
    Name = "Full Example",
    Icon = NebulaIcons:GetIcon("code", "Material"),
    Visible = true
}, 1)

local MovementBox = ExampleTab:CreateGroupbox({
    Name = "Movement",
    Column = 1
}, 1)

MovementBox:CreateSlider({
    Name = "WalkSpeed",
    Icon = NebulaIcons:GetIcon("directions_run", "Material"),
    CurrentValue = 16,
    Range = {16, 200},
    Increment = 1,
    Suffix = " speed",
    Callback = function(value)
        if LocalPlayer.Character and LocalPlayer.Character:FindFirstChild("Humanoid") then
            LocalPlayer.Character.Humanoid.WalkSpeed = value
        end
    end
}, 1)

MovementBox:CreateSlider({
    Name = "Jump Power",
    Icon = NebulaIcons:GetIcon("arrow-up", "Lucide"),
    CurrentValue = 50,
    Range = {50, 300},
    Increment = 5,
    Suffix = " power",
    Callback = function(value)
        if LocalPlayer.Character and LocalPlayer.Character:FindFirstChild("Humanoid") then
            LocalPlayer.Character.Humanoid.JumpPower = value
        end
    end
}, 2)

MovementBox:CreateToggle({
    Name = "Infinite Jump",
    CurrentValue = false,
    Callback = function(value)
        _G.InfiniteJump = value
    end
}, 3)

MovementBox:CreateToggle({
    Name = "No Clip",
    CurrentValue = false,
    Callback = function(value)
        _G.NoClip = value
    end
}, 4)

local UtilityBox = ExampleTab:CreateGroupbox({
    Name = "Utilities",
    Column = 2
}, 2)

UtilityBox:CreateButton({
    Name = "Copy Profile Link",
    Style = 1,
    Callback = function()
        setclipboard("https://www.roblox.com/users/" .. LocalPlayer.UserId)
        Starlight:Notification({
            Title = "Copied!",
            Content = "Profile link copied",
            Duration = 2
        })
    end
}, 1)

UtilityBox:CreateButton({
    Name = "Rejoin Server",
    Style = 2,
    Callback = function()
        game:GetService("TeleportService"):TeleportToPlaceInstance(game.PlaceId, game.JobId, LocalPlayer)
    end
}, 2)

UtilityBox:CreateDivider()
UtilityBox:CreateLabel({Name = "Player: " .. LocalPlayer.Name}, 1)
UtilityBox:CreateLabel({Name = "UserID: " .. LocalPlayer.UserId}, 2)
UtilityBox:CreateLabel({Name = "Account Age: " .. LocalPlayer.AccountAge .. " days"}, 3)
```

---

## 🎯 Advanced Examples

### ESP Toggle

```lua
local ESPBox = VisualsTab:CreateGroupbox({
    Name = "ESP Settings",
    Column = 1
}, 1)

ESPBox:CreateToggle({
    Name = "Player Box ESP",
    Icon = NebulaIcons:GetIcon("square", "Lucide"),
    CurrentValue = false,
    Callback = function(value)
        _G.BoxESP = value
        if value then
            print("ESP Enabled")
        else
            print("ESP Disabled")
        end
    end
}, 1)

ESPBox:CreateSlider({
    Name = "FOV Size",
    CurrentValue = 150,
    Range = {50, 500},
    Increment = 10,
    Suffix = " px",
    Callback = function(value)
        _G.FOVSize = value
    end
}, 2)
```

### Fullbright Toggle

```lua
WorldBox:CreateToggle({
    Name = "Fullbright",
    Icon = NebulaIcons:GetIcon("sun", "Lucide"),
    CurrentValue = false,
    Callback = function(value)
        local Lighting = game:GetService("Lighting")
        if value then
            Lighting.Brightness = 2
            Lighting.ClockTime = 14
            Lighting.FogEnd = 100000
            Lighting.GlobalShadows = false
        else
            Lighting.Brightness = 1
            Lighting.ClockTime = 12
            Lighting.FogEnd = 1000
            Lighting.GlobalShadows = true
        end
    end
}, 1)
```

### Camera FOV

```lua
WorldBox:CreateSlider({
    Name = "Camera FOV",
    CurrentValue = 70,
    Range = {70, 120},
    Increment = 1,
    Suffix = "°",
    Callback = function(value)
        if workspace.CurrentCamera then
            workspace.CurrentCamera.FieldOfView = value
        end
    end
}, 2)
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
