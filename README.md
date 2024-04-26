local PlayerTP1
local TweenService = game:GetService("TweenService")
Section:CreateLabel("Stats ! Combat [20K]")
local Toggle = Section:CreateToggle("Farm >FireKing<", function(Value)
_G.King = Value
while _G.King do
wait(1)  -- Wait for 1 second before checking for enemies
pcall(function()
for i,v in pairs(workspace.NPCS:GetDescendants()) do
if v.Name == _G.Name then
if v.Humanoid.Health > 0 then
repeat
    local toolName = "Combat" -- Replace "YourToolNameHere" with the name of your tool

    local LocalPlayer = game:GetService("Players").LocalPlayer
    for i, v in pairs(LocalPlayer.Backpack:GetChildren()) do
        if v:IsA('Tool') and v.Name == toolName then
            v.Parent = LocalPlayer.Character
            break -- Stop the loop after picking up the tool
        end
    end
    
    LocalPlayer.Character:FindFirstChild(toolName):Activate() 
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = v.HumanoidRootPart.CFrame * CFrame.new(0,0,4)
wait()  -- Wait a short time before checking again
until not _G.Hit or v.Humanoid.Health <= 0
end
end
end
end)
end
end)
    
local Player = game.Players.LocalPlayer
local function onCharacterAdded(character)
character.Archivable = false
character:WaitForChild("HumanoidRootPart").Anchored = false
if Player.Character then
onCharacterAdded(Player.Character)
Player.CharacterAdded:Connect(onCharacterAdded)
end
end
