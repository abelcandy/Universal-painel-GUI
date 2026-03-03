local Players = game:GetService("Players")
local TweenService = game:GetService("TweenService")
local UserInputService = game:GetService("UserInputService")
local ReplicatedStorage = game:GetService("ReplicatedStorage")

local player = game.Players.LocalPlayer
local playerGui = player:WaitForChild("PlayerGui")

-- ========== CRIAÇÃO DO PAINEL ==========

local screenGui = Instance.new("ScreenGui")
screenGui.Name = "PainelSidebar"
screenGui.Parent = playerGui
screenGui.IgnoreGuiInset = true

local mainFrame = Instance.new("Frame")
mainFrame.Parent = screenGui
mainFrame.Size = UDim2.new(0, 250, 0, 0)
mainFrame.Position = UDim2.new(0, 0, 0.5, 0)
mainFrame.BackgroundColor3 = Color3.new(0.1, 0.1, 0.1)
mainFrame.BorderSizePixel = 0
mainFrame.AutomaticSize = Enum.AutomaticSize.Y
mainFrame.Visible = false
mainFrame.ClipsDescendants = true

local mainCorner = Instance.new("UICorner")
mainCorner.CornerRadius = UDim.new(0, 12)
mainCorner.Parent = mainFrame

-- ========== SIDEBAR ==========

local sidebar = Instance.new("Frame")
sidebar.Parent = mainFrame
sidebar.Size = UDim2.new(0, 50, 0, 0)
sidebar.BackgroundColor3 = Color3.new(0.15, 0.15, 0.15)
sidebar.AutomaticSize = Enum.AutomaticSize.Y

local sidebarCorner = Instance.new("UICorner")
sidebarCorner.CornerRadius = UDim.new(0, 12)
sidebarCorner.Parent = sidebar

-- Botão Home
local btnHome = Instance.new("TextButton")
btnHome.Parent = sidebar
btnHome.Size = UDim2.new(1, 0, 0, 40)
btnHome.BackgroundColor3 = Color3.new(0.2, 0.2, 0.2)
btnHome.Text = "🏠"
btnHome.TextSize = 20
btnHome.Font = Enum.Font.SourceSansBold

local btnHomeCorner = Instance.new("UICorner")
btnHomeCorner.CornerRadius = UDim.new(0, 8)
btnHomeCorner.Parent = btnHome

-- Botão Character
local btnCharacter = Instance.new("TextButton")
btnCharacter.Parent = sidebar
btnCharacter.Size = UDim2.new(1, 0, 0, 40)
btnCharacter.Position = UDim2.new(0, 0, 0, 45)
btnCharacter.BackgroundColor3 = Color3.new(0.15, 0.15, 0.15)
btnCharacter.Text = "👤"
btnCharacter.TextSize = 20
btnCharacter.Font = Enum.Font.SourceSansBold

local btnCharCorner = Instance.new("UICorner")
btnCharCorner.CornerRadius = UDim.new(0, 8)
btnCharCorner.Parent = btnCharacter

-- Botão Me (NOVA ABA)
local btnMe = Instance.new("TextButton")
btnMe.Parent = sidebar
btnMe.Size = UDim2.new(1, 0, 0, 40)
btnMe.Position = UDim2.new(0, 0, 0, 90)
btnMe.BackgroundColor3 = Color3.new(0.15, 0.15, 0.15)
btnMe.Text = "⚙️"
btnMe.TextSize = 20
btnMe.Font = Enum.Font.SourceSansBold

local btnMeCorner = Instance.new("UICorner")
btnMeCorner.CornerRadius = UDim.new(0, 8)
btnMeCorner.Parent = btnMe

-- ========== CONTEÚDO ==========

local contentFrame = Instance.new("Frame")
contentFrame.Parent = mainFrame
contentFrame.Size = UDim2.new(1, -50, 0, 0)
contentFrame.Position = UDim2.new(0, 50, 0, 0)
contentFrame.BackgroundTransparency = 1
contentFrame.AutomaticSize = Enum.AutomaticSize.Y

-- ========== PÁGINA HOME ==========

local homePage = Instance.new("Frame")
homePage.Parent = contentFrame
homePage.Size = UDim2.new(1, 0, 0, 0)
homePage.BackgroundTransparency = 1
homePage.AutomaticSize = Enum.AutomaticSize.Y

local titulo = Instance.new("TextLabel")
titulo.Parent = homePage
titulo.Size = UDim2.new(1, 0, 0, 40)
titulo.BackgroundTransparency = 1
titulo.Text = "Painel Admin"
titulo.TextColor3 = Color3.new(1, 1, 1)
titulo.TextSize = 22
titulo.Font = Enum.Font.SourceSansBold

local keybindText = Instance.new("TextLabel")
keybindText.Parent = homePage
keybindText.Size = UDim2.new(1, 0, 0, 30)
keybindText.Position = UDim2.new(0, 0, 0, 45)
keybindText.BackgroundTransparency = 1
keybindText.Text = "Keybind: [ B ] para abrir menu"
keybindText.TextColor3 = Color3.new(0.6, 0.6, 0.6)
keybindText.TextSize = 14
keybindText.Font = Enum.Font.SourceSans

local keybindText2 = Instance.new("TextLabel")
keybindText2.Parent = homePage
keybindText2.Size = UDim2.new(1, 0, 0, 25)
keybindText2.Position = UDim2.new(0, 0, 0, 70)
keybindText2.BackgroundTransparency = 1
keybindText2.Text = "Keybind: [ F ] para voar"
keybindText2.TextColor3 = Color3.new(0.6, 0.6, 0.6)
keybindText2.TextSize = 14
keybindText2.Font = Enum.Font.SourceSans

local statusText = Instance.new("TextLabel")
statusText.Parent = homePage
statusText.Size = UDim2.new(1, 0, 0, 25)
statusText.Position = UDim2.new(0, 0, 0, 100)
statusText.BackgroundTransparency = 1
statusText.Text = "Status: Ativado"
statusText.TextColor3 = Color3.new(0, 1, 0)
statusText.TextSize = 12

-- ========== PÁGINA CHARACTER ==========

local characterPage = Instance.new("Frame")
characterPage.Parent = contentFrame
characterPage.Size = UDim2.new(1, 0, 0, 0)
characterPage.BackgroundTransparency = 1
characterPage.AutomaticSize = Enum.AutomaticSize.Y
characterPage.Visible = false

local tituloChar = Instance.new("TextLabel")
tituloChar.Parent = characterPage
tituloChar.Size = UDim2.new(1, 0, 0, 30)
tituloChar.BackgroundTransparency = 1
tituloChar.Text = "Gerenciar Players"
tituloChar.TextColor3 = Color3.new(1, 1, 1)
tituloChar.TextSize = 18
tituloChar.Font = Enum.Font.SourceSansBold

local scrollFrame = Instance.new("ScrollingFrame")
scrollFrame.Parent = characterPage
scrollFrame.Size = UDim2.new(1, 0, 0, 150)
scrollFrame.Position = UDim2.new(0, 0, 0, 40)
scrollFrame.BackgroundColor3 = Color3.new(0.12, 0.12, 0.12)
scrollFrame.BorderSizePixel = 0
scrollFrame.ScrollBarThickness = 4

local scrollCorner = Instance.new("UICorner")
scrollCorner.CornerRadius = UDim.new(0, 8)
scrollCorner.Parent = scrollFrame

local scrollList = Instance.new("UIListLayout")
scrollList.Parent = scrollFrame
scrollList.Padding = UDim.new(0, 2)
scrollList.HorizontalAlignment = Enum.HorizontalAlignment.Center

scrollFrame.CanvasSize = UDim2.new(0, 0, 0, 0)
scrollList:GetPropertyChangedSignal("AbsoluteContentSize"):Connect(function()
	scrollFrame.CanvasSize = UDim2.new(0, 0, 0, scrollList.AbsoluteContentSize.Y + 10)
end)

local btnEspiar = Instance.new("TextButton")
btnEspiar.Parent = characterPage
btnEspiar.Size = UDim2.new(1, 0, 0, 35)
btnEspiar.Position = UDim2.new(0, 0, 0, 200)
btnEspiar.BackgroundColor3 = Color3.new(1, 0.5, 0)
btnEspiar.Text = "🔍 Espiar Player"
btnEspiar.TextColor3 = Color3.new(1, 1, 1)
btnEspiar.TextSize = 14

local btnEspiarCorner = Instance.new("UICorner")
btnEspiarCorner.CornerRadius = UDim.new(0, 6)
btnEspiarCorner.Parent = btnEspiar

local btnTeleport = Instance.new("TextButton")
btnTeleport.Parent = characterPage
btnTeleport.Size = UDim2.new(1, 0, 0, 35)
btnTeleport.Position = UDim2.new(0, 0, 0, 240)
btnTeleport.BackgroundColor3 = Color3.new(0, 0.5, 1)
btnTeleport.Text = "📍 Teletransportar"
btnTeleport.TextColor3 = Color3.new(1, 1, 1)
btnTeleport.TextSize = 14

local btnTeleportCorner = Instance.new("UICorner")
btnTeleportCorner.CornerRadius = UDim.new(0, 6)
btnTeleportCorner.Parent = btnTeleport

local playerSelecionado = Instance.new("TextLabel")
playerSelecionado.Parent = characterPage
playerSelecionado.Size = UDim2.new(1, 0, 0, 20)
playerSelecionado.Position = UDim2.new(0, 0, 0, 280)
playerSelecionado.BackgroundTransparency = 1
playerSelecionado.Text = "Nenhum player selecionado"
playerSelecionado.TextColor3 = Color3.new(0.5, 0.5, 0.5)
playerSelecionado.TextSize = 12

-- ========== PÁGINA ME (NOVA ABA) ==========

local mePage = Instance.new("Frame")
mePage.Parent = contentFrame
mePage.Size = UDim2.new(1, 0, 0, 0)
mePage.BackgroundTransparency = 1
mePage.AutomaticSize = Enum.AutomaticSize.Y
mePage.Visible = false

local tituloMe = Instance.new("TextLabel")
tituloMe.Parent = mePage
tituloMe.Size = UDim2.new(1, 0, 0, 30)
tituloMe.BackgroundTransparency = 1
tituloMe.Text = "Minhas Funções"
tituloMe.TextColor3 = Color3.new(1, 1, 1)
tituloMe.TextSize = 18
tituloMe.Font = Enum.Font.SourceSansBold

-- Toggle Voo
local labelVoo = Instance.new("TextLabel")
labelVoo.Parent = mePage
labelVoo.Size = UDim2.new(1, 0, 0, 25)
labelVoo.Position = UDim2.new(0, 0, 0, 40)
labelVoo.BackgroundTransparency = 1
labelVoo.Text = "Modo Voo"
labelVoo.TextColor3 = Color3.new(1, 1, 1)
labelVoo.TextSize = 14

local btnVoo = Instance.new("TextButton")
btnVoo.Parent = mePage
btnVoo.Size = UDim2.new(1, 0, 0, 35)
btnVoo.Position = UDim2.new(0, 0, 0, 70)
btnVoo.BackgroundColor3 = Color3.new(0.15, 0.15, 0.15)
btnVoo.Text = "Ativar Voo: OFF"
btnVoo.TextColor3 = Color3.new(1, 0, 0)
btnVoo.TextSize = 14

local btnVooCorner = Instance.new("UICorner")
btnVooCorner.CornerRadius = UDim.new(0, 6)
btnVooCorner.Parent = btnVoo

local labelKeyVoo = Instance.new("TextLabel")
labelKeyVoo.Parent = mePage
labelKeyVoo.Size = UDim2.new(1, 0, 0, 20)
labelKeyVoo.Position = UDim2.new(0, 0, 0, 110)
labelKeyVoo.BackgroundTransparency = 1
labelKeyVoo.Text = "Keybind: [ F ] para ativar/desativar"
labelKeyVoo.TextColor3 = Color3.new(0.5, 0.5, 0.5)
labelKeyVoo.TextSize = 11

-- Velocidade do Voo
local labelVelVoo = Instance.new("TextLabel")
labelVelVoo.Parent = mePage
labelVelVoo.Size = UDim2.new(1, 0, 0, 25)
labelVelVoo.Position = UDim2.new(0, 0, 0, 140)
labelVelVoo.BackgroundTransparency = 1
labelVelVoo.Text = "Velocidade do Voo"
labelVelVoo.TextColor3 = Color3.new(1, 1, 1)
labelVelVoo.TextSize = 14

local inputVelVoo = Instance.new("TextBox")
inputVelVoo.Parent = mePage
inputVelVoo.Size = UDim2.new(1, 0, 0, 35)
inputVelVoo.Position = UDim2.new(0, 0, 0, 170)
inputVelVoo.BackgroundColor3 = Color3.new(0.15, 0.15, 0.15)
inputVelVoo.Text = "50"
inputVelVoo.TextColor3 = Color3.new(1, 1, 1)
inputVelVoo.TextSize = 16
inputVelVoo.PlaceholderText = "Velocidade..."
inputVelVoo.PlaceholderColor3 = Color3.new(0.5, 0.5, 0.5)

local inputVelVooCorner = Instance.new("UICorner")
inputVelVooCorner.CornerRadius = UDim.new(0, 6)
inputVelVooCorner.Parent = inputVelVoo

-- WalkSpeed
local labelWalk = Instance.new("TextLabel")
labelWalk.Parent = mePage
labelWalk.Size = UDim2.new(1, 0, 0, 25)
labelWalk.Position = UDim2.new(0, 0, 0, 220)
labelWalk.BackgroundTransparency = 1
labelWalk.Text = "WalkSpeed (Velocidade)"
labelWalk.TextColor3 = Color3.new(1, 1, 1)
labelWalk.TextSize = 14

local inputWalk = Instance.new("TextBox")
inputWalk.Parent = mePage
inputWalk.Size = UDim2.new(1, 0, 0, 35)
inputWalk.Position = UDim2.new(0, 0, 0, 250)
inputWalk.BackgroundColor3 = Color3.new(0.15, 0.15, 0.15)
inputWalk.Text = "16"
inputWalk.TextColor3 = Color3.new(1, 1, 1)
inputWalk.TextSize = 16
inputWalk.PlaceholderText = "WalkSpeed..."
inputWalk.PlaceholderColor3 = Color3.new(0.5, 0.5, 0.5)

local inputWalkCorner = Instance.new("UICorner")
inputWalkCorner.CornerRadius = UDim.new(0, 6)
inputWalkCorner.Parent = inputWalk

local btnAplicarWalk = Instance.new("TextButton")
btnAplicarWalk.Parent = mePage
btnAplicarWalk.Size = UDim2.new(1, 0, 0, 35)
btnAplicarWalk.Position = UDim2.new(0, 0, 0, 290)
btnAplicarWalk.BackgroundColor3 = Color3.new(0, 0.7, 0)
btnAplicarWalk.Text = "✓ Aplicar WalkSpeed"
btnAplicarWalk.TextColor3 = Color3.new(1, 1, 1)
btnAplicarWalk.TextSize = 14

local btnAplicarWalkCorner = Instance.new("UICorner")
btnAplicarWalkCorner.CornerRadius = UDim.new(0, 6)
btnAplicarWalkCorner.Parent = btnAplicarWalk

-- Status Voo
local statusVoo = Instance.new("TextLabel")
statusVoo.Parent = mePage
statusVoo.Size = UDim2.new(1, 0, 0, 20)
statusVoo.Position = UDim2.new(0, 0, 0, 330)
statusVoo.BackgroundTransparency = 1
statusVoo.Text = "Voo: Inativo"
statusVoo.TextColor3 = Color3.new(1, 0, 0)
statusVoo.TextSize = 12

-- ========== LÓGICA DO PAINEL ==========

local painelAberto = false
local playerAtual = nil
local vooAtivo = false
local flySpeed = 50
local char = player.Character or player.CharacterAdded:Wait()
local humanoid = char:WaitForChild("Humanoid")
local rootPart = char:WaitForChild("HumanoidRootPart")

-- Variáveis de voo
local flyConnection = nil
local camera = workspace.CurrentCamera

-- ========== FUNÇÕES DE VOO ==========

local function startFly()
	if vooAtivo then return end
	vooAtivo = true
	
	btnVoo.Text = "Ativar Voo: ON"
	btnVoo.TextColor3 = Color3.new(0, 1, 0)
	statusVoo.Text = "Voo: Ativo"
	statusVoo.TextColor3 = Color3.new(0, 1, 0)
	
	local bodyVelocity = Instance.new("BodyVelocity")
	bodyVelocity.Name = "FlyVelocity"
	bodyVelocity.Parent = rootPart
	bodyVelocity.MaxForce = Vector3.new(math.huge, math.huge, math.huge)
	bodyVelocity.Velocity = Vector3.new(0, 0, 0)
	
	local bodyGyro = Instance.new("BodyGyro")
	bodyGyro.Name = "FlyGyro"
	bodyGyro.Parent = rootPart
	bodyGyro.MaxTorque = Vector3.new(math.huge, math.huge, math.huge)
	bodyGyro.CFrame = rootPart.CFrame
	
	humanoid.PlatformStand = true
	
	flyConnection = game:GetService("RunService").RenderStepped:Connect(function()
		if not vooAtivo then return end
		
		local moveDirection = Vector3.new(0, 0, 0)
		local userInputService = game:GetService("UserInputService")
		
		if userInputService:IsKeyDown(Enum.KeyCode.W) then
			moveDirection = moveDirection + (camera.CFrame.LookVector * Vector3.new(1, 0, 1)).Unit
		end
		if userInputService:IsKeyDown(Enum.KeyCode.S) then
			moveDirection = moveDirection - (camera.CFrame.LookVector * Vector3.new(1, 0, 1)).Unit
		end
		if userInputService:IsKeyDown(Enum.KeyCode.A) then
			moveDirection = moveDirection - camera.CFrame.RightVector
		end
		if userInputService:IsKeyDown(Enum.KeyCode.D) then
			moveDirection = moveDirection + camera.CFrame.RightVector
		end
		if userInputService:IsKeyDown(Enum.KeyCode.Space) then
			moveDirection = moveDirection + Vector3.new(0, 1, 0)
		end
		if userInputService:IsKeyDown(Enum.KeyCode.LeftControl) then
			moveDirection = moveDirection - Vector3.new(0, 1, 0)
		end
		
		if moveDirection.Magnitude > 0 then
			moveDirection = moveDirection.Unit
		end
		
		bodyVelocity.Velocity = moveDirection * flySpeed
		bodyGyro.CFrame = camera.CFrame
	end)
end

local function stopFly()
	if not vooAtivo then return end
	vooAtivo = false
	
	if flyConnection then
		flyConnection:Disconnect()
		flyConnection = nil
	end
	
	btnVoo.Text = "Ativar Voo: OFF"
	btnVoo.TextColor3 = Color3.new(1, 0, 0)
	statusVoo.Text = "Voo: Inativo"
	statusVoo.TextColor3 = Color3.new(1, 0, 0)
	
	local bodyVelocity = rootPart:FindFirstChild("FlyVelocity")
	local bodyGyro = rootPart:FindFirstChild("FlyGyro")
	
	if bodyVelocity then bodyVelocity:Destroy() end
	if bodyGyro then bodyGyro:Destroy() end
	
	humanoid.PlatformStand = false
end

local function toggleFly()
	flySpeed = tonumber(inputVelVoo.Text) or 50
	if vooAtivo then
		stopFly()
	else
		startFly()
	end
end

-- ========== FUNÇÕES DE PAINEL ==========

local function abrirPainel()
	painelAberto = true
	
	local tweenInfo = TweenInfo.new(
		0.3,
		Enum.EasingStyle.Quad,
		Enum.EasingDirection.Out
	)
	
	local tween = TweenService:Create(mainFrame, tweenInfo, {Size = UDim2.new(0, 300, 0, 400)})
	tween:Play()
	
	mainFrame.Visible = true
end

local function fecharPainel()
	painelAberto = false
	
	local tweenInfo = TweenInfo.new(
		0.3,
		Enum.EasingStyle.Quad,
		Enum.EasingDirection.In
	)
	
	local tween = TweenService:Create(mainFrame, tweenInfo, {Size = UDim2.new(0, 0, 0, 0)})
	tween:Play()
	
	tween.Completed:Connect(function()
		mainFrame.Visible = false
	end)
end

local function mudarPagina(pagina)
	homePage.Visible = false
	characterPage.Visible = false
	mePage.Visible = false
	
	if pagina == "home" then
		homePage.Visible = true
	elseif pagina == "character" then
		characterPage.Visible = true
		atualizarListaPlayers()
	elseif pagina == "me" then
		mePage.Visible = true
	end
end

-- ========== LISTA DE PLAYERS ==========

local function atualizarListaPlayers()
	-- Limpar items antigos
	for _, item in pairs(scrollFrame:GetChildren()) do
		if item:IsA("TextButton") then
			item:Destroy()
		end
	end
	
	-- Adicionar novos players
	for _, p in pairs(Players:GetPlayers()) do
		if p ~= player then
			local playerButton = Instance.new("TextButton")
			playerButton.Parent = scrollFrame
			playerButton.Size = UDim2.new(1, -10, 0, 30)
			playerButton.BackgroundColor3 = Color3.new(0.2, 0.2, 0.2)
			playerButton.Text = p.Name
			playerButton.TextColor3 = Color3.new(1, 1, 1)
			playerButton.TextSize = 13
			
			local playerButtonCorner = Instance.new("UICorner")
			playerButtonCorner.CornerRadius = UDim.new(0, 4)
			playerButtonCorner.Parent = playerButton
			
			playerButton.MouseButton1Click:Connect(function()
				playerAtual = p
				playerSelecionado.Text = "Selecionado: " .. p.Name
				playerSelecionado.TextColor3 = Color3.new(0, 1, 0)
			end)
		end
	end
end

-- ========== BOTÕES ==========

btnHome.MouseButton1Click:Connect(function()
	mudarPagina("home")
end)

btnCharacter.MouseButton1Click:Connect(function()
	mudarPagina("character")
end)

btnMe.MouseButton1Click:Connect(function()
	mudarPagina("me")
end)

btnVoo.MouseButton1Click:Connect(toggleFly)

btnAplicarWalk.MouseButton1Click:Connect(function()
	local walkSpeed = tonumber(inputWalk.Text)
	if walkSpeed and humanoid then
		humanoid.WalkSpeed = walkSpeed
	end
end)

btnEspiar.MouseButton1Click:Connect(function()
	if playerAtual and playerAtual.Character then
		camera.CFrame = playerAtual.Character:FindFirstChild("Head").CFrame + playerAtual.Character:FindFirstChild("Head").CFrame.LookVector * 5
	end
end)

btnTeleport.MouseButton1Click:Connect(function()
	if playerAtual and playerAtual.Character and rootPart then
		rootPart.CFrame = playerAtual.Character:FindFirstChild("HumanoidRootPart").CFrame + Vector3.new(3, 3, 3)
	end
end)

-- ========== KEYBINDS ==========

UserInputService.InputBegan:Connect(function(input, gameProcessed)
	if gameProcessed then return end
	
	if input.KeyCode == Enum.KeyCode.B then
		if painelAberto then
			fecharPainel()
		else
			abrirPainel()
		end
	end
	
	if input.KeyCode == Enum.KeyCode.F then
		toggleFly()
	end
end)

-- ========== PLAYER UPDATED ==========

Players.PlayerAdded:Connect(function(newPlayer)
	if painelAberto then
		atualizarListaPlayers()
	end
end)

Players.PlayerRemoving:Connect(function(removedPlayer)
	if painelAberto then
		atualizarListaPlayers()
	end
	if playerAtual == removedPlayer then
		playerAtual = nil
		playerSelecionado.Text = "Nenhum player selecionado"
		playerSelecionado.TextColor3 = Color3.new(0.5, 0.5, 0.5)
	end
end)

player.CharacterAdded:Connect(function(newChar)
	char = newChar
	humanoid = char:WaitForChild("Humanoid")
	rootPart = char:WaitForChild("HumanoidRootPart")
	
	if vooAtivo then
		stopFly()
	end
end)

print("✓ Painel Admin carregado com sucesso!")
