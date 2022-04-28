local Library = loadstring(game:HttpGet("https://raw.githubusercontent.com/xHeptc/Kavo-UI-Library/main/source.lua"))()
local Window = Library.CreateLib("1ol : Auto Equip", "BloodTheme")
local Tab = Window:NewTab("Main")
local Section = Tab:NewSection("Auto Equip")


local Weaponlist = {}
local Weapon = nil


for i,v in pairs(game:GetService("Players").LocalPlayer.Backpack:GetChildren()) do
    table.insert(Weaponlist,v.Name)
    end


Section:NewDropdown("select weapon", " ",Weaponlist, function(currentOption)
    Weapon = currentOption
end)

Section:NewToggle("Auto Equip", "", function(a)
AutoEquiped = a
end)


spawn(function()
while wait() do
if AutoEquiped then
    pcall(function()
game.Players.LocalPlayer.Character.Humanoid:EquipTool(game:GetService("Players").LocalPlayer.Backpack:FindFirstChild(Weapon))
end)
end
end
end)
