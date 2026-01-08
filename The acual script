local Players = game:GetService("Players")
local player = Players.LocalPlayer
local playerGui = player:WaitForChild("PlayerGui")

local screenGui = Instance.new("ScreenGui")
screenGui.Name = "WordDisplay"
screenGui.ResetOnSpawn = false
screenGui.Parent = playerGui

local displayLabel = Instance.new("TextLabel")
displayLabel.Name = "DisplayWord"
displayLabel.Size = UDim2.new(0, 200, 0, 50)
displayLabel.Position = UDim2.new(1, -210, 0, 10)
displayLabel.AnchorPoint = Vector2.new(0, 0)
displayLabel.BackgroundColor3 = Color3.fromRGB(50, 50, 50)
displayLabel.BackgroundTransparency = 0.3
displayLabel.BorderSizePixel = 2
displayLabel.BorderColor3 = Color3.fromRGB(255, 255, 255)
displayLabel.Text = "Waiting..."
displayLabel.TextColor3 = Color3.fromRGB(255, 255, 255)
displayLabel.TextScaled = true
displayLabel.Font = Enum.Font.GothamBold
displayLabel.Parent = screenGui

local recheckButton = Instance.new("TextButton")
recheckButton.Name = "RecheckButton"
recheckButton.Size = UDim2.new(0, 200, 0, 35)
recheckButton.Position = UDim2.new(1, -210, 0, 65)
recheckButton.AnchorPoint = Vector2.new(0, 0)
recheckButton.BackgroundColor3 = Color3.fromRGB(70, 130, 180)
recheckButton.BackgroundTransparency = 0.2
recheckButton.BorderSizePixel = 2
recheckButton.BorderColor3 = Color3.fromRGB(255, 255, 255)
recheckButton.Text = "Recheck Word"
recheckButton.TextColor3 = Color3.fromRGB(255, 255, 255)
recheckButton.TextScaled = true
recheckButton.Font = Enum.Font.GothamBold
recheckButton.Parent = screenGui

local function updateDisplay(wordLabel)
	if wordLabel then
		displayLabel.Text = wordLabel.Value
	end
end

local function monitorWordLabel()
	local wordFolder = player:FindFirstChild("WordFolder")
	
	if wordFolder then
		local wordValue = wordFolder:FindFirstChild("Word")
		
		if wordValue then
			displayLabel.Text = wordValue.Value
			
			wordValue:GetPropertyChangedSignal("Value"):Connect(function()
				displayLabel.Text = wordValue.Value
			end)
			
			return true
		end
	end
	
	return false
end

if not monitorWordLabel() then
	player.ChildAdded:Connect(function(child)
		if child.Name == "WordFolder" then
			wait(0.1)
			monitorWordLabel()
		end
	end)
end

recheckButton.MouseButton1Click:Connect(function()
	displayLabel.Text = "Checking..."
	wait(0.5)
	
	if not monitorWordLabel() then
		displayLabel.Text = "Word not found!"
		wait(1)
		displayLabel.Text = "Waiting..."
	end
end)

-- ImA_Programmer404 waz here :]
