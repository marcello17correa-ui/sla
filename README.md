--// 👑 IPHONEZIN007 PREMIUM ADMIN V2

local DONO = 7879416903
local Players = game:GetService("Players")
local TweenService = game:GetService("TweenService")
local UIS = game:GetService("UserInputService")

local player = Players.LocalPlayer

-- Segurança
if player.UserId ~= DONO then
	return
end

-- Remove painel antigo
pcall(function()
	local old = player.PlayerGui:FindFirstChild("IPHONEZIN007_V2")
	if old then
		old:Destroy()
	end
end)

-- Configurações
local Config = {
	Speed = 1,
	Jump = false,
	God = false,
	AutoClick = false,
	CPS = 20
}

-- Criar GUI
local gui = Instance.new("ScreenGui")
gui.Name = "IPHONEZIN007_V2"
gui.ResetOnSpawn = false
gui.IgnoreGuiInset = true
gui.Parent = player.PlayerGui


-- Janela principal
local Main = Instance.new("Frame")
Main.Parent = gui
Main.Size = UDim2.new(0,380,0,550)
Main.Position = UDim2.new(0.5,-190,0.5,-275)

Main.BackgroundColor3 = Color3.fromRGB(8,8,8)
Main.BackgroundTransparency = 0.1


local Corner = Instance.new("UICorner")
Corner.CornerRadius = UDim.new(0,15)
Corner.Parent = Main


local Stroke = Instance.new("UIStroke")
Stroke.Parent = Main
Stroke.Color = Color3.fromRGB(255,0,0)
Stroke.Thickness = 3


-- Barra superior
local Top = Instance.new("Frame")
Top.Parent = Main
Top.Size = UDim2.new(1,0,0,50)
Top.BackgroundColor3 = Color3.fromRGB(15,15,15)


local TopCorner = Instance.new("UICorner")
TopCorner.Parent = Top
TopCorner.CornerRadius = UDim.new(0,15)


-- Título
local Title = Instance.new("TextLabel")
Title.Parent = Top
Title.Size = UDim2.new(0.7,0,1,0)

Title.Text = "👑 IPHONEZIN007 PREMIUM"
Title.TextScaled = true
Title.TextColor3 = Color3.new(1,1,1)
Title.BackgroundTransparency = 1


-- Botão fechar
local Close = Instance.new("TextButton")
Close.Parent = Top
Close.Size = UDim2.new(0,35,0,35)
Close.Position = UDim2.new(1,-45,0.5,-17)

Close.Text = "✖"
Close.TextScaled = true
Close.TextColor3 = Color3.new(1,1,1)
Close.BackgroundColor3 = Color3.fromRGB(120,0,0)


local CloseCorner = Instance.new("UICorner")
CloseCorner.Parent = Close


-- Minimizar
local Mini = Instance.new("TextButton")
Mini.Parent = Top
Mini.Size = UDim2.new(0,35,0,35)
Mini.Position = UDim2.new(1,-85,0.5,-17)

Mini.Text = "—"
Mini.TextScaled = true
Mini.TextColor3 = Color3.new(1,1,1)
Mini.BackgroundColor3 = Color3.fromRGB(80,80,0)


local MiniCorner = Instance.new("UICorner")
MiniCorner.Parent = Mini


-- Botão abrir novamente
local Open = Instance.new("TextButton")
Open.Parent = gui

Open.Size = UDim2.new(0,140,0,40)
Open.Position = UDim2.new(0,15,0.5,0)

Open.Text = "👑 ABRIR ADMIN"
Open.Visible = false

Open.TextColor3 = Color3.new(1,1,1)
Open.BackgroundColor3 = Color3.fromRGB(10,10,10)


local OpenStroke = Instance.new("UIStroke")
OpenStroke.Parent = Open
OpenStroke.Color = Color3.fromRGB(255,0,0)


local OpenCorner = Instance.new("UICorner")
OpenCorner.Parent = Open


-- Container
local Container = Instance.new("Frame")
Container.Parent = Main
Container.Position = UDim2.new(0,10,0,60)
Container.Size = UDim2.new(1,-20,1,-70)
Container.BackgroundTransparency = 1


local Layout = Instance.new("UIListLayout")
Layout.Parent = Container
Layout.Padding = UDim.new(0,8)


-- Título Speed atual
local SpeedLabel = Instance.new("TextLabel")
SpeedLabel.Parent = Container
SpeedLabel.Size = UDim2.new(1,0,0,35)

SpeedLabel.Text = "⚡ SPEED ATUAL: 1X"
SpeedLabel.TextScaled = true
SpeedLabel.TextColor3 = Color3.fromRGB(0,255,0)
SpeedLabel.BackgroundTransparency = 1


-- Criador de botão premium
local function CriarBotao(Texto)

	local B = Instance.new("TextButton")
	B.Parent = Container
	
	B.Size = UDim2.new(1,0,0,40)
	B.Text = Texto
	B.TextScaled = true
	
	B.TextColor3 = Color3.new(1,1,1)
	B.BackgroundColor3 = Color3.fromRGB(25,25,25)

	local C = Instance.new("UICorner")
	C.Parent = B
	
	local S = Instance.new("UIStroke")
	S.Parent = B
	S.Color = Color3.fromRGB(255,0,0)

	return B
end


-- Speed
local S2 = CriarBotao("💨 SPEED 2X")
local S5 = CriarBotao("💨 SPEED 5X")
local S10 = CriarBotao("💨 SPEED 10X")
local S20 = CriarBotao("💨 SPEED 20X")
local S40 = CriarBotao("💨 SPEED 40X")
local S50 = CriarBotao("💨 SPEED 50X")

-- Funções
local JumpBtn = CriarBotao("🦘 SUPER PULO OFF")
local GodBtn = CriarBotao("❤️ VIDA INFINITA OFF")
local ClickBtn = CriarBotao("🖱 AUTO CLICK OFF")
local InfoBtn = CriarBotao("📊 INFORMAÇÕES")


-- Animação de entrada
Main.Size = UDim2.new(0,0,0,0)

TweenService:Create(
	Main,
	TweenInfo.new(0.4, Enum.EasingStyle.Back),
	{
		Size = UDim2.new(0,380,0,550)
	}
):Play()


print("🔥 Interface PREMIUM V2 carregada")
--=============================
-- SISTEMA DE CORES DOS BOTÕES
--=============================

local function DesligarCor(botao)
	botao.BackgroundColor3 = Color3.fromRGB(25,25,25)
end

local function LigarCor(botao)
	botao.BackgroundColor3 = Color3.fromRGB(0,180,0)
end


--=============================
-- SPEED PREMIUM
--=============================

local SpeedButtons = {
	S2, S5, S10, S20, S40, S50
}

local function ResetarSpeed()
	for _, b in pairs(SpeedButtons) do
		DesligarCor(b)
	end
end


local function AplicarSpeed(valor, botao)

	Config.Speed = valor

	SpeedLabel.Text = "⚡ SPEED ATUAL: "..valor.."X"

	ResetarSpeed()
	LigarCor(botao)

	local Char = player.Character
	local Hum = Char and Char:FindFirstChild("Humanoid")

	if Hum then
		Hum.WalkSpeed = 16 * valor
	end
end


S2.MouseButton1Click:Connect(function()
	AplicarSpeed(2, S2)
end)

S5.MouseButton1Click:Connect(function()
	AplicarSpeed(5, S5)
end)

S10.MouseButton1Click:Connect(function()
	AplicarSpeed(10, S10)
end)

S20.MouseButton1Click:Connect(function()
	AplicarSpeed(20, S20)
end)

S40.MouseButton1Click:Connect(function()
	AplicarSpeed(40, S40)
end)

S50.MouseButton1Click:Connect(function()
	AplicarSpeed(50, S50)
end)


--=============================
-- SUPER PULO
--=============================

JumpBtn.MouseButton1Click:Connect(function()

	Config.Jump = not Config.Jump

	local Hum = player.Character and 
		player.Character:FindFirstChild("Humanoid")

	if Config.Jump then

		LigarCor(JumpBtn)
		JumpBtn.Text = "🦘 SUPER PULO ON"

		if Hum then
			Hum.JumpPower = 160
		end

	else

		DesligarCor(JumpBtn)
		JumpBtn.Text = "🦘 SUPER PULO OFF"

		if Hum then
			Hum.JumpPower = 50
		end

	end
end)


--=============================
-- VIDA INFINITA
--=============================

JumpLoop = false

GodBtn.MouseButton1Click:Connect(function()

	Config.God = not Config.God

	if Config.God then

		LigarCor(GodBtn)
		GodBtn.Text = "❤️ VIDA INFINITA ON"

		task.spawn(function()

			while Config.God do

				local Hum = player.Character 
				and player.Character:FindFirstChild("Humanoid")

				if Hum and Hum.Health < Hum.MaxHealth then
					Hum.Health = Hum.MaxHealth
				end

				task.wait(0.1)

			end

		end)

	else

		DesligarCor(GodBtn)
		GodBtn.Text = "❤️ VIDA INFINITA OFF"

	end

end)


--=============================
-- AUTO CLICK 20 CPS
--=============================

ClickBtn.MouseButton1Click:Connect(function()

	Config.AutoClick = not Config.AutoClick

	if Config.AutoClick then

		LigarCor(ClickBtn)
		ClickBtn.Text = "🖱 AUTO CLICK 20 CPS"

		task.spawn(function()

			local VU = game:GetService("VirtualUser")

			while Config.AutoClick do

				pcall(function()

					VU:Button1Down(
						Vector2.new(500,500),
						workspace.CurrentCamera.CFrame
					)

					task.wait(0.01)

					VU:Button1Up(
						Vector2.new(500,500),
						workspace.CurrentCamera.CFrame
					)

				end)

				task.wait(0.05)

			end

		end)

	else

		DesligarCor(ClickBtn)
		ClickBtn.Text = "🖱 AUTO CLICK OFF"

	end

end)


--=============================
-- INFORMAÇÕES
--=============================

InfoBtn.MouseButton1Click:Connect(function()

	print("======== IPHONEZIN007 ========")
	print("Nome:", player.Name)
	print("ID:", player.UserId)
	print("Speed:", Config.Speed.."X")
	print("Pulo:", Config.Jump)
	print("Vida Infinita:", Config.God)
	print("Auto Click:", Config.AutoClick)
	print("==============================")

end)


print("🔥 Sistema de poderes carregado")
--=============================
-- REAPLICAR APÓS MORRER
--=============================

player.CharacterAdded:Connect(function(Char)

	local Hum = Char:WaitForChild("Humanoid")

	task.wait(0.5)

	-- Speed salvo
	if Config.Speed > 1 then
		Hum.WalkSpeed = 16 * Config.Speed
	end

	-- Pulo salvo
	if Config.Jump then
		Hum.JumpPower = 160
	end

	-- Vida infinita continua
	if Config.God then
		task.spawn(function()

			while Config.God and Hum.Parent do

				if Hum.Health < Hum.MaxHealth then
					Hum.Health = Hum.MaxHealth
				end

				task.wait(0.1)

			end

		end)
	end

end)


--=============================
-- ARRASTAR (PC E CELULAR)
--=============================

local Arrastando = false
local InicioMouse
local InicioPos

local function AtualizarPos(Input)

	local Delta = Input.Position - InicioMouse

	Main.Position = UDim2.new(
		InicioPos.X.Scale,
		InicioPos.X.Offset + Delta.X,
		InicioPos.Y.Scale,
		InicioPos.Y.Offset + Delta.Y
	)

end


Top.InputBegan:Connect(function(Input)

	if Input.UserInputType == Enum.UserInputType.MouseButton1
	or Input.UserInputType == Enum.UserInputType.Touch then

		Arrastando = true
		InicioMouse = Input.Position
		InicioPos = Main.Position

	end

end)


Top.InputEnded:Connect(function(Input)

	if Input.UserInputType == Enum.UserInputType.MouseButton1
	or Input.UserInputType == Enum.UserInputType.Touch then

		Arrastando = false

	end

end)


UIS.InputChanged:Connect(function(Input)

	if Arrastando and
	(
		Input.UserInputType == Enum.UserInputType.MouseMovement
		or Input.UserInputType == Enum.UserInputType.Touch
	) then

		AtualizarPos(Input)

	end

end)


--=============================
-- MINIMIZAR COM ANIMAÇÃO
--=============================

Mini.MouseButton1Click:Connect(function()

	TweenService:Create(
		Main,
		TweenInfo.new(0.25),
		{
			Size = UDim2.new(0,380,0,0)
		}
	):Play()

	task.wait(0.25)

	Main.Visible = false
	Open.Visible = true

end)


Open.MouseButton1Click:Connect(function()

	Main.Visible = true

	Main.Size = UDim2.new(0,380,0,0)

	TweenService:Create(
		Main,
		TweenInfo.new(
			0.35,
			Enum.EasingStyle.Back
		),
		{
			Size = UDim2.new(0,380,0,550)
		}
	):Play()

	Open.Visible = false

end)


--=============================
-- FECHAR COM ANIMAÇÃO
--=============================

Close.MouseButton1Click:Connect(function()

	TweenService:Create(
		Main,
		TweenInfo.new(0.25),
		{
			Size = UDim2.new(0,0,0,0)
		}
	):Play()

	task.wait(0.25)

	gui:Destroy()

end)


--=============================
-- EFEITO DE BORDA NEON
--=============================

task.spawn(function()

	local Valor = 0

	while gui.Parent do

		Valor += 0.05

		local brilho =
			(math.sin(Valor) + 1) / 2

		Stroke.Color = Color3.new(
			1,
			brilho * 0.2,
			brilho * 0.2
		)

		task.wait(0.03)

	end

end)


local ResizeHandle = Instance.new("Frame")
ResizeHandle.Parent = Main
ResizeHandle.Size = UDim2.new(0, 20, 0, 20)
ResizeHandle.Position = UDim2.new(1, -20, 1, -20)
ResizeHandle.BackgroundColor3 = Color3.fromRGB(255, 0, 0)
ResizeHandle.BackgroundTransparency = 0.3

local UICorner = Instance.new("UICorner")
UICorner.CornerRadius = UDim.new(0, 4)
UICorner.Parent = ResizeHandle
local dragging = false
local startInput
local startSize

ResizeHandle.InputBegan:Connect(function(input)
	if input.UserInputType == Enum.UserInputType.MouseButton1
	or input.UserInputType == Enum.UserInputType.Touch then

		dragging = true
		startInput = input.Position
		startSize = Main.Size
	end
end)

UIS.InputChanged:Connect(function(input)
	if not dragging then return end

	if input.UserInputType == Enum.UserInputType.MouseMovement
	or input.UserInputType == Enum.UserInputType.Touch then

		local delta = input.Position - startInput

		local newX = math.max(250, startSize.X.Offset + delta.X)
		local newY = math.max(300, startSize.Y.Offset + delta.Y)

		Main.Size = UDim2.new(0, newX, 0, newY)
	end
end)

UIS.InputEnded:Connect(function(input)
	if input.UserInputType == Enum.UserInputType.MouseButton1
	or input.UserInputType == Enum.UserInputType.Touch then
		dragging = false
	end
end)


--=============================
-- MENSAGEM FINAL
--=============================

print([[
👑================================👑
       IPHONEZIN007 PREMIUM V2
          CARREGADO COM SUCESSO
👑================================👑
]])

print("🛡 DONO AUTORIZADO:", player.Name)
print("🆔 ID:", player.UserId)
