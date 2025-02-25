-- Crie uma tela principal
local ScreenGui = Instance.new("ScreenGui")
ScreenGui.Name = "PlayerESP"
ScreenGui.Parent = game.Players.LocalPlayer:WaitForChild("PlayerGui")

-- Slide transparente com a opção "ON/OFF"
local Frame = Instance.new("Frame")
Frame.Size = UDim2.new(0.2, 0, 0.1, 0)
Frame.Position = UDim2.new(0.4, 0, 0.85, 0)
Frame.BackgroundTransparency = 0.5
Frame.BackgroundColor3 = Color3.fromRGB(0, 0, 0)
Frame.Parent = ScreenGui

local ToggleButton = Instance.new("TextButton")
ToggleButton.Size = UDim2.new(1, 0, 1, 0)
ToggleButton.Position = UDim2.new(0, 0, 0, 0)
ToggleButton.BackgroundTransparency = 1
ToggleButton.TextScaled = true
ToggleButton.Text = "ON/OFF"
ToggleButton.TextColor3 = Color3.fromRGB(255, 255, 255)
ToggleButton.Parent = Frame

-- Lista de cores para nomes dos jogadores
local playerColors = {}

-- Função para gerar uma cor aleatória
local function getRandomColor()
    return Color3.fromRGB(math.random(0, 255), math.random(0, 255), math.random(0, 255))
end

-- Função para criar ESP (Extra Sensory Perception) para jogadores
local function createESP(player)
    -- Gerar uma cor aleatória para o jogador
    local playerColor = playerColors[player.Name] or getRandomColor()
    playerColors[player.Name] = playerColor

    -- Criar um BillboardGui para o nome do jogador
    local billboardGui = Instance.new("BillboardGui")
    billboardGui.Name = "ESP"
    billboardGui.Adornee = player.Character:WaitForChild("Head")
    billboardGui.Size = UDim2.new(2, 0, 1, 0)
    billboardGui.AlwaysOnTop = true

    -- Criar um rótulo de texto para o nome do jogador
    local nameLabel = Instance.new("TextLabel")
    nameLabel.Parent = billboardGui
    nameLabel.BackgroundTransparency = 1
    nameLabel.Size = UDim2.new(1, 0, 1, 0)
    nameLabel.Text = player.Name
    nameLabel.TextColor3 = playerColor -- Cor personalizada
    nameLabel.TextScaled = true
    nameLabel.Font = Enum.Font.SourceSansBold -- Tornar o texto grande e em negrito

    -- Aplicar transparência para ver o
