-- Roube um Brainrot HUB
-- Executor: Delta / Codex / Fluxus

local player = game.Players.LocalPlayer

-- GUI
local ScreenGui = Instance.new("ScreenGui")
ScreenGui.Parent = game.CoreGui

local Main = Instance.new("Frame")
Main.Parent = ScreenGui
Main.Size = UDim2.new(0,220,0,260)
Main.Position = UDim2.new(0.35,0,0.25,0)
Main.BackgroundColor3 = Color3.fromRGB(20,20,20)
Main.Active = true
Main.Draggable = true

local UICorner = Instance.new("UICorner", Main)

local Title = Instance.new("TextLabel")
Title.Parent = Main
Title.Size = UDim2.new(1,0,0,40)
Title.BackgroundTransparency = 1
Title.Text = "ROUBA BRAINROT HUB"
Title.TextColor3 = Color3.fromRGB(0,255,120)
Title.TextScaled = true
Title.Font = Enum.Font.GothamBold

-- Função criar botão
function criarBotao(texto,posY)
	local btn = Instance.new("TextButton")
	btn.Parent = Main
	btn.Size = UDim2.new(0,180,0,35)
	btn.Position = UDim2.new(0,20,0,posY)
	btn.BackgroundColor3 = Color3.fromRGB(35,35,35)
	btn.TextColor3 = Color3.fromRGB(255,255,255)
	btn.Font = Enum.Font.GothamBold
	btn.TextScaled = true
	btn.Text = texto
	
	local c = Instance.new("UICorner",btn)
	
	return btn
end

-- AUTO FARM
local farm = false

local AutoFarm = criarBotao("AUTO FARM",60)

AutoFarm.MouseButton1Click:Connect(function()
	farm = not farm
	
	while farm do
		pcall(function()
			for i,v in pairs(workspace:GetDescendants()) do
				if v:IsA("TouchTransmitter") then
					firetouchinterest(
						player.Character.HumanoidRootPart,
						v.Parent,
						0
					)
					wait(0.1)
					firetouchinterest(
						player.Character.HumanoidRootPart,
						v.Parent,
						1
					)
				end
			end
		end)
		wait(1)
	end
end)

-- SPEED
local Speed = criarBotao("VELOCIDADE",110)

Speed.MouseButton1Click:Connect(function()
	player.Character.Humanoid.WalkSpeed = 50
end)

-- SUPER PULO
local Jump = criarBotao("SUPER PULO",160)

Jump.MouseButton1Click:Connect(function()
	player.Character.Humanoid.JumpPower = 120
end)


-- FECHAR GUI
local Close = criarBotao("FECHAR HUB",210)

Close.MouseButton1Click:Connect(function()
	ScreenGui:Destroy()
end)
