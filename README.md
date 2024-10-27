local ScreenGui = Instance.new("ScreenGui")
local Frame = Instance.new("Frame")
local ActivateButton = Instance.new("TextButton")
local DeactivateButton = Instance.new("TextButton")
local StatusLabel = Instance.new("TextLabel")

ScreenGui.Name = "FarmLevelGui"
ScreenGui.Parent = game.CoreGui

Frame.Name = "Frame"
Frame.Parent = ScreenGui
Frame.BackgroundColor3 = Color3.new(0.1, 0.1, 0.1)
Frame.Size = UDim2.new(0, 200, 0, 150)
Frame.Position = UDim2.new(0, 50, 0, 50)

ActivateButton.Name = "ActivateButton"
ActivateButton.Parent = Frame
ActivateButton.Text = "Ativar Farm Level"
ActivateButton.Size = UDim2.new(1, -10, 0, 50)
ActivateButton.Position = UDim2.new(0, 5, 0, 5)
ActivateButton.MouseButton1Click:Connect(function()
    StartFarmLevel()
end)

DeactivateButton.Name = "DeactivateButton"
DeactivateButton.Parent = Frame
DeactivateButton.Text = "Desativar Farm Level"
DeactivateButton.Size = UDim2.new(1, -10, 0, 50)
DeactivateButton.Position = UDim2.new(0, 5, 0, 60)
DeactivateButton.MouseButton1Click:Connect(function()
    StopFarmLevel()
end)

StatusLabel.Name = "StatusLabel"
StatusLabel.Parent = Frame
StatusLabel.Text = "Status: Desativado"
StatusLabel.Size = UDim2.new(1, -10, 0, 30)
StatusLabel.Position = UDim2.new(0, 5, 0, 115)
StatusLabel.TextColor3 = Color3.new(1, 1, 1)

local farmingActive = false

function StartFarmLevel()
    farmingActive = true
    StatusLabel.Text = "Status: Ativado"
    CheckQuest()
end

function StopFarmLevel()
    farmingActive = false
    StatusLabel.Text = "Status: Desativado"
end

function CheckQuest()
    while farmingActive do
        local MyLevel = game:GetService("Players").LocalPlayer.Data.Level.Value
        if game.PlaceId == 2753915549 then
            World1 = true
        elseif game.PlaceId == 4442272183 then
            World2 = true
        elseif game.PlaceId == 7449423635 then
            World3 = true
        else
            game:GetService("Players").LocalPlayer:Kick("Do not Support, Please wait...")
            break
        end

        if World1 then
            if MyLevel == 1 or MyLevel <= 9 then
                Mon = "Bandit"
                LevelQuest = 1
                NameQuest = "BanditQuest1"
                NameMon = "Bandit"
                CFrameQuest = CFrame.new(1059.37195, 15.4495068, 1550.4231)
                CFrameMon = CFrame.new(1045.962646484375, 27.00250816345215, 1560.8203125)
            elseif MyLevel == 10 or MyLevel <= 14 then
                Mon = "Monkey"
                LevelQuest = 1
                NameQuest = "JungleQuest"
                NameMon = "Monkey"
                CFrameQuest = CFrame.new(-1598.08911, 35.5501175, 153.377838)
                CFrameMon = CFrame.new(-1448.51806640625, 67.85301208496094, 11.46579647064209)
            end
        elseif World2 then
        elseif World3 then
        end
        wait(1)
    end
end
