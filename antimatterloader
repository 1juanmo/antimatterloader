-- =========================================================================
-- ANTIMATTER LOADER - WINDUI
-- Library: https://raw.githubusercontent.com/silencedevs/SilenceScripts/refs/heads/main/libraries/windui/windui.luau
-- =========================================================================

-- Services
local Players = game:GetService("Players")
local LocalPlayer = Players.LocalPlayer

-- 1. Load the WindUI Library
local WindUI = loadstring(game:HttpGet("https://raw.githubusercontent.com/silencedevs/SilenceScripts/refs/heads/main/libraries/windui/windui.luau"))()

-- 2. Create the Main Window
local Window = WindUI:CreateWindow({
    Title = "AntiMatter - Loader",
    Author = "by xamo @neoxamo",
    Icon = "solar:lock-bold",
    IconSize = 26,
    Theme = "Violet",
    NewElements = true,
    Size = UDim2.fromOffset(450, 260),
    Folder = "AntiMatter/Loader/" .. tostring(LocalPlayer.UserId),
    KeySystem = false,
})

-- 3. Create Tabs
local MainTab = Window:Tab({
    Title = "Scripts",
    Icon = "solar:folder-code-bold",
})

local SettingsTab = Window:Tab({
    Title = "Settings",
    Icon = "solar:settings-bold",
})

-- =========================================================================
-- 4. SCRIPT DATABASE (EASY TO UPDATE)
-- =========================================================================
local ScriptList = {
    {
        Name = "Steal an Egg",
        Description = "Loads the AntiMatter Steal an Egg script.",
        Url = "https://raw.githubusercontent.com/1juanmo/antimatterstealanegg/refs/heads/main/antimatter%20steal%20an%20egg.lua"
    },
    {
        Name = "Sniper Arena",
        Description = "Loads the AntiMatter Sniper Arena script.",
        Url = "https://raw.githubusercontent.com/1juanmo/antimattersniperarena/refs/heads/main/sniperarena.lua"
    },
    -- ADD FUTURE SCRIPTS HERE:
    -- { Name = "Script Name", Description = "Short description", Url = "https://raw.githubusercontent.com/..." },
}

-- =========================================================================
-- 5. SCRIPT BUTTON GENERATION
-- =========================================================================

MainTab:Section({ Title = "Available Scripts" })

-- Helper function to fetch and run loadstring(game:HttpGet(...))
local function loadScript(scriptUrl)
    local success, err = pcall(function()
        loadstring(game:HttpGet(scriptUrl))()
    end)
    
    if success then
        WindUI:Notify({
            Title = "AntiMatter",
            Content = "Script loaded successfully!",
            Duration = 3
        })
    else
        WindUI:Notify({
            Title = "Error",
            Content = "Failed to load script: " .. tostring(err),
            Duration = 5
        })
    end
end

-- Generate buttons dynamically from the ScriptList table
for _, scriptInfo in ipairs(ScriptList) do
    MainTab:Button({
        Title = scriptInfo.Name,
        Desc = scriptInfo.Description,
        Callback = function()
            loadScript(scriptInfo.Url)
        end,
    })
end

-- =========================================================================
-- 6. SETTINGS TAB
-- =========================================================================
SettingsTab:Button({
    Title = "Unload UI",
    Desc = "Closes and destroys AntiMatter Loader.",
    Callback = function()
        Window:Destroy()
    end,
})

-- Notification on launch
WindUI:Notify({
    Title = "AntiMatter Loader",
    Content = "Loader initialized successfully.",
    Duration = 3
})
