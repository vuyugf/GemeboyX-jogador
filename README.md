-- Services
local CoreGui = game:GetService("CoreGui")
local Players = game:GetService("Players")
local LocalPlayer = Players.LocalPlayer

-- Destruir GUI anterior se existir
if CoreGui:FindFirstChild("GameBoyXJogadoresGui") then
    CoreGui.GameBoyXJogadoresGui:Destroy()
end

-- ScreenGui Principal
local ScreenGui = Instance.new("ScreenGui")
ScreenGui.Name = "GameBoyXJogadoresGui"
ScreenGui.ResetOnSpawn = false

if syn and syn.protect_gui then
    syn.protect_gui(ScreenGui)
    ScreenGui.Parent = CoreGui
elseif gethui then
    ScreenGui.Parent = gethui()
else
    ScreenGui.Parent = CoreGui
end

----------------------------------------------------
-- BOTÃO FLUTUANTE (BOLINHA MOVÍVEL VERDE-NEON)
----------------------------------------------------
local ToggleButton = Instance.new("TextButton")
local UICornerBtn = Instance.new("UICorner")
local UIStrokeBtn = Instance.new("UIStroke")

ToggleButton.Name = "ToggleButton"
ToggleButton.Size = UDim2.new(0, 65, 0, 65)
ToggleButton.Position = UDim2.new(0.05, 0, 0.4, 0)
ToggleButton.BackgroundColor3 = Color3.fromRGB(15, 15, 15)
ToggleButton.Active = true
ToggleButton.Draggable = true
ToggleButton.Text = "Jogadores"
ToggleButton.TextColor3 = Color3.fromRGB(57, 255, 20)
ToggleButton.Font = Enum.Font.SourceSansBold
ToggleButton.TextSize = 12
ToggleButton.Parent = ScreenGui

UICornerBtn.CornerRadius = UDim.new(1, 0)
UICornerBtn.Parent = ToggleButton

UIStrokeBtn.Color = Color3.fromRGB(57, 255, 20)
UIStrokeBtn.Thickness = 3
UIStrokeBtn.ApplyStrokeMode = Enum.ApplyStrokeMode.Border
UIStrokeBtn.Parent = ToggleButton

----------------------------------------------------
-- PAINEL PRINCIPAL (GAMEBOYX JOGADORES)
----------------------------------------------------
local MainFrame = Instance.new("Frame")
local UICornerMain = Instance.new("UICorner")
local UIStrokeMain = Instance.new("UIStroke")
local Title = Instance.new("TextLabel")
local CloseButton = Instance.new("TextButton")

MainFrame.Name = "MainFrame"
MainFrame.Size = UDim2.new(0, 360, 0, 140)
MainFrame.Position = UDim2.new(0.5, -180, 0.5, -70)
MainFrame.BackgroundColor3 = Color3.fromRGB(18, 18, 18)
MainFrame.Visible = true
MainFrame.Active = true
MainFrame.Draggable = true
MainFrame.Parent = ScreenGui

UICornerMain.CornerRadius = UDim.new(0, 16)
UICornerMain.Parent = MainFrame

UIStrokeMain.Color = Color3.fromRGB(57, 255, 20)
UIStrokeMain.Thickness = 2
UIStrokeMain.Parent = MainFrame

Title.Name = "Title"
Title.Size = UDim2.new(1, -50, 0, 45)
Title.Position = UDim2.new(0, 20, 0, 0)
Title.BackgroundTransparency = 1
Title.Text = "GameBoy<font color=\"rgb(57,255,20)\">X Jogadores</font>"
Title.RichText = true
Title.TextColor3 = Color3.fromRGB(57, 255, 20)
Title.TextSize = 22
Title.Font = Enum.Font.SourceSansBold
Title.TextXAlignment = Enum.TextXAlignment.Left
Title.Parent = MainFrame

CloseButton.Name = "CloseButton"
CloseButton.Size = UDim2.new(0, 30, 0, 30)
CloseButton.Position = UDim2.new(1, -40, 0, 10)
CloseButton.BackgroundTransparency = 1
CloseButton.Text = "X"
CloseButton.TextColor3 = Color3.fromRGB(57, 255, 20)
CloseButton.TextSize = 20
CloseButton.Font = Enum.Font.SourceSansBold
CloseButton.Parent = MainFrame

----------------------------------------------------
-- BOTÃO ÚNICO DA TELA INICIAL
----------------------------------------------------
local OpenPlayerBtn = Instance.new("TextButton")
OpenPlayerBtn.Size = UDim2.new(1, -40, 0, 50)
OpenPlayerBtn.Position = UDim2.new(0, 20, 0, 60)
OpenPlayerBtn.BackgroundColor3 = Color3.fromRGB(25, 25, 25)
OpenPlayerBtn.Text = "👤 Jogador Eu"
OpenPlayerBtn.TextColor3 = Color3.fromRGB(57, 255, 20)
OpenPlayerBtn.Font = Enum.Font.SourceSansBold
OpenPlayerBtn.TextSize = 18
OpenPlayerBtn.Parent = MainFrame
Instance.new("UICorner", OpenPlayerBtn).CornerRadius = UDim.new(0, 8)
local StrokeBtn1 = Instance.new("UIStroke", OpenPlayerBtn)
StrokeBtn1.Color = Color3.fromRGB(57, 255, 20)

----------------------------------------------------
-- ABA: JOGADOR EU (ATRIBUTOS DO PERSONAGEM)
----------------------------------------------------
local PlayerFrame = Instance.new("Frame")
PlayerFrame.Name = "PlayerFrame"
PlayerFrame.Size = UDim2.new(0, 360, 0, 310)
PlayerFrame.Position = UDim2.new(0.5, -180, 0.5, -155)
PlayerFrame.BackgroundColor3 = Color3.fromRGB(22, 22, 22)
PlayerFrame.Visible = false
PlayerFrame.Active = true
PlayerFrame.Draggable = true
PlayerFrame.Parent = ScreenGui

Instance.new("UICorner", PlayerFrame).CornerRadius = UDim.new(0, 14)
local PlayerFrameStroke = Instance.new("UIStroke")
PlayerFrameStroke.Color = Color3.fromRGB(57, 255, 20)
PlayerFrameStroke.Thickness = 2
PlayerFrameStroke.Parent = PlayerFrame

local PlayerTitle = Instance.new("TextLabel")
PlayerTitle.Size = UDim2.new(1, -50, 0, 35)
PlayerTitle.Position = UDim2.new(0, 15, 0, 0)
PlayerTitle.BackgroundTransparency = 1
PlayerTitle.Text = "Atributos do Jogador"
PlayerTitle.TextColor3 = Color3.fromRGB(57, 255, 20)
PlayerTitle.Font = Enum.Font.SourceSansBold
PlayerTitle.TextSize = 18
PlayerTitle.TextXAlignment = Enum.TextXAlignment.Left
PlayerTitle.Parent = PlayerFrame

local ClosePlayerFrameBtn = Instance.new("TextButton")
ClosePlayerFrameBtn.Size = UDim2.new(0, 30, 0, 30)
ClosePlayerFrameBtn.Position = UDim2.new(1, -35, 0, 3)
ClosePlayerFrameBtn.BackgroundTransparency = 1
ClosePlayerFrameBtn.Text = "X"
ClosePlayerFrameBtn.TextColor3 = Color3.fromRGB(57, 255, 20)
ClosePlayerFrameBtn.Font = Enum.Font.SourceSansBold
ClosePlayerFrameBtn.TextSize = 18
ClosePlayerFrameBtn.Parent = PlayerFrame

----------------------------------------------------
-- FUNÇÃO DE CRIAR CAMPO DE CONFIGURAÇÃO
----------------------------------------------------
local function createInputRow(labelText, placeholder, positionY, onApply)
    local RowFrame = Instance.new("Frame")
    RowFrame.Size = UDim2.new(1, -30, 0, 45)
    RowFrame.Position = UDim2.new(0, 15, 0, positionY)
    RowFrame.BackgroundTransparency = 1
    RowFrame.Parent = PlayerFrame

    local Label = Instance.new("TextLabel")
    Label.Size = UDim2.new(0.5, -5, 1, 0)
    Label.BackgroundTransparency = 1
    Label.Text = labelText
    Label.TextColor3 = Color3.fromRGB(57, 255, 20)
    Label.Font = Enum.Font.SourceSansBold
    Label.TextSize = 14
    Label.TextXAlignment = Enum.TextXAlignment.Left
    Label.Parent = RowFrame

    local InputBox = Instance.new("TextBox")
    InputBox.Size = UDim2.new(0.5, 0, 1, 0)
    InputBox.Position = UDim2.new(0.5, 0, 0, 0)
    InputBox.BackgroundColor3 = Color3.fromRGB(10, 10, 10)
    InputBox.TextColor3 = Color3.fromRGB(57, 255, 20)
    InputBox.PlaceholderText = placeholder
    InputBox.PlaceholderColor3 = Color3.fromRGB(57, 180, 20)
    InputBox.Font = Enum.Font.SourceSansBold
    InputBox.TextSize = 14
    InputBox.Text = ""
    InputBox.ClearTextOnFocus = false
    InputBox.Parent = RowFrame
    Instance.new("UICorner", InputBox).CornerRadius = UDim.new(0, 6)
    
    local BoxStroke = Instance.new("UIStroke", InputBox)
    BoxStroke.Color = Color3.fromRGB(57, 255, 20)

    InputBox.FocusLost:Connect(function(enterPressed)
        if enterPressed then
            local val = tonumber(InputBox.Text)
            if val then
                onApply(val)
            end
        end
    end)
end

----------------------------------------------------
-- CAMPOS (1 A 100)
----------------------------------------------------
createInputRow("🏃 Velocidade (1-100):", "Ex: 16-100", 45, function(val)
    local valClamped = math.clamp(val, 1, 100)
    local char = LocalPlayer.Character
    if char and char:FindFirstChildOfClass("Humanoid") then
        char:FindFirstChildOfClass("Humanoid").WalkSpeed = valClamped
    end
end)

createInputRow("🦘 Tamanho do Pulo (1-100):", "Ex: 50-100", 100, function(val)
    local valClamped = math.clamp(val, 1, 100)
    local char = LocalPlayer.Character
    if char and char:FindFirstChildOfClass("Humanoid") then
        local hum = char:FindFirstChildOfClass("Humanoid")
        hum.UseJumpPower = true
        hum.JumpPower = valClamped
    end
end)

createInputRow("🏊 Velocidade de Nado (1-100):", "Ex: 16-100", 155, function(val)
    local valClamped = math.clamp(val, 1, 100)
    local char = LocalPlayer.Character
    if char and char:FindFirstChildOfClass("Humanoid") then
        char:FindFirstChildOfClass("Humanoid").WalkSpeed = valClamped
    end
end)

createInputRow("🌌 Gravidade (0-100):", "Ex: 0-100", 210, function(val)
    local valClamped = math.clamp(val, 0, 100)
    workspace.Gravity = valClamped
end)

----------------------------------------------------
-- AÇÕES DOS BOTÕES DE ABRIR/FECHAR
----------------------------------------------------
OpenPlayerBtn.MouseButton1Click:Connect(function()
    PlayerFrame.Visible = true
end)

ClosePlayerFrameBtn.MouseButton1Click:Connect(function()
    PlayerFrame.Visible = false
end)

ToggleButton.MouseButton1Click:Connect(function()
    MainFrame.Visible = not MainFrame.Visible
end)

CloseButton.MouseButton1Click:Connect(function()
    MainFrame.Visible = false
end)
