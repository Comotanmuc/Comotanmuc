local player = game.Players.LocalPlayer
local character = player.Character or player.CharacterAdded:Wait()

-- Función para teletransportarse a una posición
local function teleportTo(position)
    character:SetPrimaryPartCFrame(CFrame.new(position))
end

-- Auto-recolección de frutas
local function autoCollectFruits()
    for _, v in pairs(workspace:GetChildren()) do
        if v.Name == "Fruit" and v:IsA("Tool") then
            character.HumanoidRootPart.CFrame = v.Handle.CFrame
            wait(1)
        end
    end
end

-- Auto-ataque
local function autoAttack()
    local tool = character:FindFirstChildOfClass("Tool")
    if tool then
        tool:Activate()
    end
end

-- Bucle principal
while true do
    autoCollectFruits()
    autoAttack()
    wait(1)
end
