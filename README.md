-- Instância principal
local ScreenGui = Instance.new("ScreenGui")
local MainFrame = Instance.new("Frame")
local TitleBar = Instance.new("Frame")
local TitleLabel = Instance.new("TextLabel")
local CloseButton = Instance.new("TextButton")
local DragButton = Instance.new("TextButton")
local SaveButton = Instance.new("TextButton")
local FloatButton = Instance.new("TextButton")
local BackgroundDecoration = Instance.new("Frame")
local CornerHandler = Instance.new("UICorner")
local TitleCorner = Instance.new("UICorner")
local ButtonCorner = Instance.new("UICorner")

-- Nome personalizado
local seuNome = "Tween"

-- Configuração do ScreenGui
ScreenGui.Name = "JanelaTween"
ScreenGui.Parent = game.Players.LocalPlayer:WaitForChild("PlayerGui")
ScreenGui.ZIndexBehavior = Enum.ZIndexBehavior.Sibling
ScreenGui.ResetOnSpawn = false

-- Configuração do Frame principal (UM POUCO MAIOR PARA OS BOTÕES GRANDES)
MainFrame.Name = "MainFrame"
MainFrame.Parent = ScreenGui
MainFrame.BackgroundColor3 = Color3.fromRGB(25, 35, 70)
MainFrame.BorderSizePixel = 0
MainFrame.Position = UDim2.new(0.4, 0, 0.4, 0)
MainFrame.Size = UDim2.new(0, 300, 0, 220)  -- Aumentado para caber botões maiores
MainFrame.Active = true
MainFrame.Draggable = true

-- Cantos arredondados para o frame principal
CornerHandler.Name = "CornerHandler"
CornerHandler.Parent = MainFrame
CornerHandler.CornerRadius = UDim.new(0, 12)

-- Decoração de fundo
BackgroundDecoration.Name = "BackgroundDecoration"
BackgroundDecoration.Parent = MainFrame
BackgroundDecoration.BackgroundColor3 = Color3.fromRGB(35, 45, 90)
BackgroundDecoration.BorderSizePixel = 0
BackgroundDecoration.Position = UDim2.new(0, 0, 0, 0)
BackgroundDecoration.Size = UDim2.new(1, 0, 0, 70)  -- Ajustado
BackgroundDecoration.ZIndex = 0

-- Barra de título
TitleBar.Name = "TitleBar"
TitleBar.Parent = MainFrame
TitleBar.BackgroundColor3 = Color3.fromRGB(15, 25, 60)
TitleBar.BorderSizePixel = 0
TitleBar.Size = UDim2.new(1, 0, 0, 35)  -- Aumentado

-- Cantos arredondados para a barra de título
TitleCorner.Name = "TitleCorner"
TitleCorner.Parent = TitleBar
TitleCorner.CornerRadius = UDim.new(0, 12)

-- Título da janela
TitleLabel.Name = "TitleLabel"
TitleLabel.Parent = TitleBar
TitleLabel.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
TitleLabel.BackgroundTransparency = 1.0
TitleLabel.Size = UDim2.new(1, -90, 1, 0)
TitleLabel.Font = Enum.Font.GothamBold
TitleLabel.Text = "✨ " .. seuNome
TitleLabel.TextColor3 = Color3.fromRGB(255, 255, 255)
TitleLabel.TextSize = 16  -- Aumentado
TitleLabel.TextXAlignment = Enum.TextXAlignment.Left
TitleLabel.Position = UDim2.new(0, 15, 0, 0)

-- Botão de arrastar
DragButton.Name = "DragButton"
DragButton.Parent = TitleBar
DragButton.BackgroundColor3 = Color3.fromRGB(45, 85, 180)
DragButton.BorderSizePixel = 0
DragButton.Position = UDim2.new(1, -80, 0, 6)  -- Ajustado
DragButton.Size = UDim2.new(0, 65, 0, 23)  -- Aumentado
DragButton.Font = Enum.Font.Gotham
DragButton.Text = "🔄"
DragButton.TextColor3 = Color3.fromRGB(255, 255, 255)
DragButton.TextSize = 12  -- Aumentado
DragButton.AutoButtonColor = false

-- Cantos arredondados para botões
ButtonCorner.Name = "ButtonCorner"
ButtonCorner.CornerRadius = UDim.new(0, 8)  -- Cantos maiores

ButtonCorner:Clone().Parent = DragButton
ButtonCorner:Clone().Parent = SaveButton
ButtonCorner:Clone().Parent = FloatButton
ButtonCorner:Clone().Parent = CloseButton

-- Botão de salvar posição (MUITO MAIOR)
SaveButton.Name = "SaveButton"
SaveButton.Parent = MainFrame
SaveButton.BackgroundColor3 = Color3.fromRGB(65, 105, 225)
SaveButton.BorderSizePixel = 0
SaveButton.Position = UDim2.new(0.05, 0, 0.3, 0)  -- Ajustado
SaveButton.Size = UDim2.new(0, 270, 0, 50)  -- MUITO MAIOR (largura quase total)
SaveButton.Font = Enum.Font.GothamBold
SaveButton.Text = "💾 SALVAR POSIÇÃO"
SaveButton.TextColor3 = Color3.fromRGB(255, 255, 255)
SaveButton.TextSize = 16  -- Aumentado
SaveButton.AutoButtonColor = false

-- Botão de flutuar (MUITO MAIOR)
FloatButton.Name = "FloatButton"
FloatButton.Parent = MainFrame
FloatButton.BackgroundColor3 = Color3.fromRGB(30, 144, 255)
FloatButton.BorderSizePixel = 0
FloatButton.Position = UDim2.new(0.05, 0, 0.65, 0)  -- Ajustado
FloatButton.Size = UDim2.new(0, 270, 0, 50)  -- MUITO MAIOR (largura quase total)
FloatButton.Font = Enum.Font.GothamBold
FloatButton.Text = "🚀 FLUTUAR - VELOCIDADE 26"
FloatButton.TextColor3 = Color3.fromRGB(255, 255, 255)
FloatButton.TextSize = 16  -- Aumentado
FloatButton.AutoButtonColor = false

-- Botão fechar
CloseButton.Name = "CloseButton"
CloseButton.Parent = TitleBar
CloseButton.BackgroundColor3 = Color3.fromRGB(220, 20, 60)
CloseButton.BorderSizePixel = 0
CloseButton.Position = UDim2.new(1, -30, 0, 6)  -- Ajustado
CloseButton.Size = UDim2.new(0, 20, 0, 20)  -- Aumentado
CloseButton.Font = Enum.Font.GothamBold
CloseButton.Text = "×"
CloseButton.TextColor3 = Color3.fromRGB(255, 255, 255)
CloseButton.TextSize = 16  -- Aumentado
CloseButton.AutoButtonColor = false

-- Efeitos de hover para botões
local function setupButtonHover(button, normalColor, hoverColor)
    button.MouseEnter:Connect(function()
        game:GetService("TweenService"):Create(button, TweenInfo.new(0.2), {BackgroundColor3 = hoverColor}):Play()
    end)
    
    button.MouseLeave:Connect(function()
        game:GetService("TweenService"):Create(button, TweenInfo.new(0.2), {BackgroundColor3 = normalColor}):Play()
    end)
    
    button.MouseButton1Down:Connect(function()
        game:GetService("TweenService"):Create(button, TweenInfo.new(0.1), {BackgroundColor3 = normalColor:Lerp(Color3.new(0,0,0), 0.3)}):Play()
    end)
    
    button.MouseButton1Up:Connect(function()
        game:GetService("TweenService"):Create(button, TweenInfo.new(0.1), {BackgroundColor3 = hoverColor}):Play()
    end)
end

-- Aplicar efeitos hover
setupButtonHover(DragButton, Color3.fromRGB(45, 85, 180), Color3.fromRGB(65, 105, 225))
setupButtonHover(SaveButton, Color3.fromRGB(65, 105, 225), Color3.fromRGB(85, 125, 255))
setupButtonHover(FloatButton, Color3.fromRGB(30, 144, 255), Color3.fromRGB(70, 170, 255))
setupButtonHover(CloseButton, Color3.fromRGB(220, 20, 60), Color3.fromRGB(255, 60, 90))

-- Variáveis para armazenamento
local savedPosition = nil
local floating = false
local bodyVelocity = nil

-- Função para salvar posição
SaveButton.MouseButton1Click:Connect(function()
    local player = game.Players.LocalPlayer
    if player.Character and player.Character:FindFirstChild("HumanoidRootPart") then
        savedPosition = player.Character.HumanoidRootPart.Position
        
        -- Efeito visual de confirmação
        game:GetService("TweenService"):Create(SaveButton, TweenInfo.new(0.3), {BackgroundColor3 = Color3.fromRGB(50, 205, 50)}):Play()
        wait(0.5)
        game:GetService("TweenService"):Create(SaveButton, TweenInfo.new(0.3), {BackgroundColor3 = Color3.fromRGB(65, 105, 225)}):Play()
        
        game.StarterGui:SetCore("SendNotification", {
            Title = "✅ Posição Salva!",
            Text = "Posição atual foi salva com sucesso.",
            Duration = 3,
            Icon = "rbxassetid://3926305904"
        })
        print("Posição salva: " .. tostring(savedPosition))
    else
        game.StarterGui:SetCore("SendNotification", {
            Title = "❌ Erro",
            Text = "Personagem não encontrado!",
            Duration = 3
        })
    end
end)

-- Função para flutuar até a posição salva (CORRIGIDA - SEM IR PARA BAIXO)
FloatButton.MouseButton1Click:Connect(function()
    if savedPosition then
        local player = game.Players.LocalPlayer
        if player.Character and player.Character:FindFirstChild("HumanoidRootPart") then
            local humanoidRootPart = player.Character.HumanoidRootPart
            
            -- Remove velocidade anterior se existir
            if bodyVelocity then
                bodyVelocity:Destroy()
                bodyVelocity = nil
            end
            
            -- Efeito visual de ativação
            game:GetService("TweenService"):Create(FloatButton, TweenInfo.new(0.3), {BackgroundColor3 = Color3.fromRGB(255, 165, 0)}):Play()
            
            -- Cria nova BodyVelocity
            bodyVelocity = Instance.new("BodyVelocity")
            bodyVelocity.Velocity = Vector3.new(0, 0, 0)
            bodyVelocity.MaxForce = Vector3.new(4000, 4000, 4000)
            bodyVelocity.Parent = humanoidRootPart
            
            -- Calcula direção HORIZONTAL apenas (X e Z) - SEM Y
            local currentPos = humanoidRootPart.Position
            local targetPos = Vector3.new(
                savedPosition.X,
                currentPos.Y,  -- Mantém a altura atual
                savedPosition.Z
            )
            
            local direction = (targetPos - currentPos).Unit
            bodyVelocity.Velocity = direction * 26 -- Velocidade 26
            
            floating = true
            
            game.StarterGui:SetCore("SendNotification", {
                Title = "🚀 Flutuando!",
                Text = "Movendo para posição salva...",
                Duration = 3,
                Icon = "rbxassetid://3926305904"
            })
            
            -- Para o movimento quando chegar perto
            local connection
            connection = game:GetService("RunService").Heartbeat:Connect(function()
                if floating and bodyVelocity and humanoidRootPart then
                    local currentPos2 = humanoidRootPart.Position
                    local horizontalDistance = Vector3.new(
                        currentPos2.X - savedPosition.X,
                        0,  -- Ignora diferença vertical
                        currentPos2.Z - savedPosition.Z
                    ).Magnitude
                    
                    if horizontalDistance < 5 then
                        bodyVelocity.Velocity = Vector3.new(0, 0, 0)
                        bodyVelocity:Destroy()
                        bodyVelocity = nil
                        floating = false
                        connection:Disconnect()
                        
                        -- Efeito visual de conclusão
                        game:GetService("TweenService"):Create(FloatButton, TweenInfo.new(0.3), {BackgroundColor3 = Color3.fromRGB(30, 144, 255)}):Play()
                        
                        game.StarterGui:SetCore("SendNotification", {
                            Title = "🎯 Chegou!",
                            Text = "Posição alcançada com sucesso.",
                            Duration = 3,
                            Icon = "rbxassetid://3926305904"
                        })
                    end
                else
                    connection:Disconnect()
                end
            end)
        else
            game.StarterGui:SetCore("SendNotification", {
                Title = "❌ Erro",
                Text = "Personagem não encontrado!",
                Duration = 3
            })
        end
    else
        game.StarterGui:SetCore("SendNotification", {
            Title = "⚠️ Aviso",
            Text = "Nenhuma posição salva!",
            Duration = 3
        })
    end
end)

-- Função para alternar arrasto
local dragging = false
DragButton.MouseButton1Click:Connect(function()
    dragging = not dragging
    MainFrame.Draggable = dragging
    if dragging then
        game:GetService("TweenService"):Create(DragButton, TweenInfo.new(0.2), {BackgroundColor3 = Color3.fromRGB(85, 125, 255)}):Play()
        DragButton.Text = "🎯"
    else
        game:GetService("TweenService"):Create(DragButton, TweenInfo.new(0.2), {BackgroundColor3 = Color3.fromRGB(45, 85, 180)}):Play()
        DragButton.Text = "🔄"
    end
end)

-- Função para fechar
CloseButton.MouseButton1Click:Connect(function()
    game:GetService("TweenService"):Create(MainFrame, TweenInfo.new(0.3), {Size = UDim2.new(0, 0, 0, 0)}):Play()
    game:GetService("TweenService"):Create(MainFrame, TweenInfo.new(0.3), {BackgroundTransparency = 1}):Play()
    wait(0.3)
    ScreenGui:Destroy()
end)

-- Efeito de entrada suave
MainFrame.Size = UDim2.new(0, 0, 0, 0)
MainFrame.BackgroundTransparency = 1
wait(0.1)
game:GetService("TweenService"):Create(MainFrame, TweenInfo.new(0.5), {Size = UDim2.new(0, 300, 0, 220)}):Play()
game:GetService("TweenService"):Create(MainFrame, TweenInfo.new(0.5), {BackgroundTransparency = 0}):Play()

-- Notificação de inicialização
wait(0.6)
game.StarterGui:SetCore("SendNotification", {
    Title = "🌟 Sistema Carregado!",
    Text = "Janela do " .. seuNome .. " criada com sucesso!",
    Duration = 5,
    Icon = "rbxassetid://3926305904"
})

print("✨ Script da janela do " .. seuNome .. " carregado com sucesso!")
