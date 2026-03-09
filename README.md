TABS
```lua
local Tab = Window:Tab({
    Name = "Aimbot",                    -- Tab name
    Icon = "rbxassetid://112730572155522" -- Tab icon asset ID
})
```
SECTIONS
```lua
-- Left side section
local LeftSection = Tab:Section({
    Name = "Main Settings",
    Side = "Left"  -- or "Right"
})

-- Right side section
local RightSection = Tab:Section({
    Name = "Visuals",
    Side = "Right"
})
```
TOGGLES
```lua
local Toggle = Section:Toggle({
    Name = "Enabled",
    Flag = "aimbot_enabled",  -- Unique identifier for flags
    Default = false,          -- Default state
    Callback = function(value)
        print("Toggle is:", value)
    end
})

-- Methods
Toggle:Set(true)  -- Set toggle on
Toggle:Set(false) -- Set toggle off
```
SLIDERS
```lua
local Slider = Section:Slider({
    Name = "Smoothness",
    Flag = "aimbot_smooth",
    Min = 0,
    Max = 100,
    Default = 50,
    Decimal = 1,     -- 1 for integers, 0.1 for decimals
    Suffix = "%",     -- Optional suffix
    Callback = function(value)
        print("Slider value:", value)
    end
})

-- Methods
Slider:Set(75)  -- Set slider value
```
DROPDOWNS
```lua
local Dropdown = Section:Dropdown({
    Name = "Target Part",
    Flag = "target_part",
    Options = {"Head", "Torso", "HumanoidRootPart"},
    Default = "Head",
    Multi = false,           -- Allow multiple selections
    Callback = function(value)
        print("Selected:", value)
    end
})

-- For multi-select dropdown
local MultiDropdown = Section:Dropdown({
    Name = "Target Parts",
    Flag = "target_parts",
    Options = {"Head", "Torso", "Left Arm", "Right Arm"},
    Default = {"Head", "Torso"},
    Multi = true,
    Callback = function(values)
        print("Selected:", table.concat(values, ", "))
    end
})

-- Methods
Dropdown:RefreshOptions({"New", "Options", "Here"})
Dropdown:Set("Head")  -- Set selected option
```
LABELS
```lua
local Label = Section:Label({
    Name = "Status: Connected"
})

-- Methods
Label:Set("Status: Disconnected")  -- Update label text
```
COLORPICKERS
```lua
local Colorpicker = Section:Label({Name = "ESP Color"}):Colorpicker({
    Flag = "esp_color",
    Color = Color3.fromRGB(255, 0, 0),     -- Default color
    Alpha = 0.5,                            -- Transparency (0-1)
    Callback = function(color, alpha)
        print("Color:", color, "Alpha:", alpha)
    end
})

-- Methods
Colorpicker:Set(Color3.new(1, 1, 1), 0.8)
```
KEYPICKERS
```lua
local Keypicker = Section:Label({Name = "Hotkey"}):Keypicker({
    Flag = "menu_key",
    Color = Color3.new(1, 1, 1),
    Alpha = 0,
    Callback = function() end
})
```
TEXTBOX
```lua
local Textbox = Section:Textbox({
    Name = "Username",
    Flag = "username_input",
    Default = "Player123",
    PlaceHolder = "Enter username...",
    Callback = function(text)
        print("Text entered:", text)
    end
})

-- Methods
Textbox:Set("New Text")
```
KEYBINDS
```lua
local Keybind = Section:Keybind({
    Name = "Menu Toggle",
    Flag = "menu_toggle",
    Key = Enum.KeyCode.RightShift,
    Mode = "Toggle",  -- "Toggle", "Hold", or "Always"
    Default = true,   -- Default active state
    Callback = function(active)
        print("Keybind active:", active)
    end
})

-- Methods
Keybind:Set(Enum.KeyCode.F1)  -- Change key
Keybind:Set("Hold")            -- Change mode
Keybind:Set({Key = Enum.KeyCode.F2, Mode = "Toggle", Active = true})
```
BUTTONS
```lua
local Button = Section:Button({
    Name = "Execute",
    Callback = function()
        print("Button clicked!")
    end
})
```
NOTIFICATIONS
```lua
-- Show a notification
Library.Notifications:Create({
    Name = "Config saved successfully!",
    LifeTime = 3  -- Seconds to display (default: 3)
})
```

