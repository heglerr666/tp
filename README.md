-- Телепорт по нажатию на экран
local Players = game:GetService("Players")
local UIS = game:GetService("UserInputService")
local player = Players.LocalPlayer

-- Куда телепортировать
local teleportPosition = Vector3.new(0, 50, 0)

local function teleport()
    local char = player.Character or player.CharacterAdded:Wait()
    local hrp = char:WaitForChild("HumanoidRootPart")
    hrp.CFrame = CFrame.new(teleportPosition)
end

-- Слушаем нажатие ЛКМ
UIS.InputBegan:Connect(function(input, gameProcessed)
    if not gameProcessed and input.UserInputType == Enum.UserInputType.MouseButton1 then
        teleport()
    end
end)
