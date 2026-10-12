-- Panel Hub "7" - Versión para Delta Executor
local CoreGui = game:GetService("CoreGui")
local Players = game:GetService("Players")
local RunService = game:GetService("RunService")
local UserInputService = game:GetService("UserInputService")
local player = Players.LocalPlayer

local parentGui = game:GetService("CoreGui")
pcall(function()
    if not parentGui or not pcall(function() return parentGui.Name end) then
        parentGui = player:WaitForChild("PlayerGui")
    end
end)

if parentGui:FindFirstChild("PanelNumero7") then
    parentGui.PanelNumero7:Destroy()
end

local ScreenGui = Instance.new("ScreenGui")
ScreenGui.Name = "PanelNumero7"
ScreenGui.ResetOnSpawn = false
pcall(function() ScreenGui.Parent = parentGui end)

-- Botón Flotante Móvil "7"
local FloatingBtn = Instance.new("TextButton")
FloatingBtn.Name = "FloatingBtn"
FloatingBtn.Parent = ScreenGui
FloatingBtn.BackgroundColor3 = Color3.fromRGB(15, 20, 35)
FloatingBtn.Position = UDim2.new(0.05, 0, 0.2, 0)
FloatingBtn.Size = UDim2.new(0, 50, 0, 50)
FloatingBtn.Font = Enum.Font.SourceSansBold
FloatingBtn.Text = "7"
FloatingBtn.TextColor3 = Color3.fromRGB(0, 170, 255)
FloatingBtn.TextSize = 22
FloatingBtn.Active = true
FloatingBtn.Draggable = true

local BtnCorner = Instance.new("UICorner", FloatingBtn)
BtnCorner.CornerRadius = UDim.new(1, 0)

local BtnStroke = Instance.new("UIStroke", FloatingBtn)
BtnStroke.Color = Color3.fromRGB(0, 120, 255)
BtnStroke.Thickness = 2

-- Ventana Principal
local MainFrame = Instance.new("Frame")
MainFrame.Name = "MainFrame"
MainFrame.Parent = ScreenGui
MainFrame.BackgroundColor3 = Color3.fromRGB(12, 15, 25)
MainFrame.Position = UDim2.new(0.2, 0, 0.1, 0)
MainFrame.Size = UDim2.new(0, 360, 0, 440)
MainFrame.Active = true
MainFrame.Draggable = true
MainFrame.Visible = false

local MainCorner = Instance.new("UICorner", MainFrame)
MainCorner.CornerRadius = UDim.new(0, 8)

local MainStroke = Instance.new("UIStroke", MainFrame)
MainStroke.Color = Color3.fromRGB(0, 150, 255)
MainStroke.Thickness = 2

-- Título y Barra Superior
local TitleBar = Instance.new("Frame", MainFrame)
TitleBar.BackgroundColor3 = Color3.fromRGB(20, 30, 50)
TitleBar.Size = UDim2.new(1, 0, 0, 40)

local TitleCorner = Instance.new("UICorner", TitleBar)
TitleCorner.CornerRadius = UDim.new(0, 8)

local Title = Instance.new("TextLabel", TitleBar)
Title.BackgroundTransparency = 1
Title.Position = UDim2.new(0.05, 0, 0, 0)
Title.Size = UDim2.new(0.75, 0, 1, 0)
Title.Font = Enum.Font.SourceSansBold
Title.Text = "PANEL 7 // DELTA EXECUTOR"
Title.TextColor3 = Color3.fromRGB(100, 200, 255)
Title.TextSize = 15

local CloseBtn = Instance.new("TextButton", TitleBar)
CloseBtn.BackgroundColor3 = Color3.fromRGB(200, 40, 40)
CloseBtn.Position = UDim2.new(0.85, 0, 0.1, 0)
CloseBtn.Size = UDim2.new(0, 30, 0, 30)
CloseBtn.Font = Enum.Font.SourceSansBold
CloseBtn.Text = "X"
CloseBtn.TextColor3 = Color3.fromRGB(255, 255, 255)
CloseBtn.TextSize = 15

local CloseCorner = Instance.new("UICorner", CloseBtn)
CloseCorner.CornerRadius = UDim.new(0, 4)

CloseBtn.MouseButton1Click:Connect(function()
    MainFrame.Visible = false
end)

FloatingBtn.MouseButton1Click:Connect(function()
    MainFrame.Visible = not MainFrame.Visible
end)

-- Contenedor con Scroll Dinámico
local Scroll = Instance.new("ScrollingFrame", MainFrame)
Scroll.Name = "Scroll"
Scroll.BackgroundTransparency = 1
Scroll.Position = UDim2.new(0.03, 0, 0.12, 0)
Scroll.Size = UDim2.new(0.94, 0, 0.85, 0)
Scroll.CanvasSize = UDim2.new(0, 0, 0, 0)
Scroll.ScrollBarThickness = 6
Scroll.ScrollingEnabled = true

local UIListLayout = Instance.new("UIListLayout", Scroll)
UIListLayout.SortOrder = Enum.SortOrder.LayoutOrder
UIListLayout.Padding = UDim.new(0, 6)

-- Ajustar automáticamente el tamaño del scroll según los elementos
UIListLayout:GetPropertyChangedSignal("AbsoluteContentSize"):Connect(function()
    Scroll.CanvasSize = UDim2.new(0, 0, 0, UIListLayout.AbsoluteContentSize.Y + 20)
end)

local function AddHeader(text)
    local Header = Instance.new("TextLabel", Scroll)
    Header.Size = UDim2.new(1, 0, 0, 28)
    Header.BackgroundTransparency = 1
    Header.Font = Enum.Font.SourceSansBold
    Header.Text = "-- " .. text .. " --"
    Header.TextColor3 = Color3.fromRGB(0, 170, 255)
    Header.TextSize = 13
    Header.TextXAlignment = Enum.TextXAlignment.Left
    return Header
end

local function AddBtn(text, func)
    local Btn = Instance.new("TextButton", Scroll)
    Btn.Size = UDim2.new(1, 0, 0, 34)
    Btn.BackgroundColor3 = Color3.fromRGB(20, 25, 40)
    Btn.Font = Enum.Font.SourceSans
    Btn.Text = " " .. text
    Btn.TextColor3 = Color3.fromRGB(220, 240, 255)
    Btn.TextSize = 13
    Btn.TextXAlignment = Enum.TextXAlignment.Left
    
    local Corner = Instance.new("UICorner", Btn)
    Corner.CornerRadius = UDim.new(0, 4)
    
    Btn.MouseButton1Click:Connect(function()
        pcall(func)
    end)
    return Btn
end

----------------------------------------------------
-- OPCIONES COMPLETAS DEL PANEL
----------------------------------------------------

AddHeader("FOGATA Y CAMPAMENTO")

AddBtn("1. Subir Fogata al Máximo", function()
    local camp = workspace:FindFirstChild("Campfire") or workspace:FindFirstChild("Camp")
    if camp then
        for _, v in pairs(camp:GetDescendants()) do
            if v:IsA("Fire") then v.Size = 25 end
            if v:IsA("NumberValue") or v:IsA("IntValue") then v.Value = 9999 end
        end
    end
end)

AddBtn("2. Ampliar Luz de Fogata", function()
    local camp = workspace:FindFirstChild("Campfire") or workspace:FindFirstChild("Camp")
    if camp then
        local p = Instance.new("PointLight", camp:FindFirstChildWhichIsA("BasePart") or camp)
        p.Range = 80
        p.Brightness = 8
    end
end)

AddBtn("3. Generar Fogata Temporal", function()
    local char = player.Character
    if char and char:FindFirstChild("HumanoidRootPart") then
        local p = Instance.new("Part", workspace)
        p.Size = Vector3.new(3, 1, 3)
        p.Position = char.HumanoidRootPart.Position - Vector3.new(0, 2, 0)
        p.Anchored = true
        Instance.new("Fire", p).Size = 15
    end
end)

AddHeader("RECURSOS Y MATERIALES")

AddBtn("4. Teleportar Toda la Madera", function()
    local char = player.Character
    if char and char:FindFirstChild("HumanoidRootPart") then
        local root = char.HumanoidRootPart
        for _, obj in pairs(workspace:GetDescendants()) do
            if obj.Name:lower():find("wood") or obj.Name:lower():find("log") or obj.Name:lower():find("madera") then
                if obj:IsA("BasePart") then obj.CFrame = root.CFrame + Vector3.new(0, 2, 0) end
            end
        end
    end
end)

AddBtn("5. Teleportar Comida", function()
    local char = player.Character
    if char and char:FindFirstChild("HumanoidRootPart") then
        local root = char.HumanoidRootPart
        for _, obj in pairs(workspace:GetDescendants()) do
            if obj.Name:lower():find("food") or obj.Name:lower():find("meat") or obj.Name:lower():find("berry") then
                if obj:IsA("BasePart") then obj.CFrame = root.CFrame + Vector3.new(0, 2, 0) end
            end
        end
    end
end)

AddBtn("6. Teleportar Piedra y Minerales", function()
    local char = player.Character
    if char and char:FindFirstChild("HumanoidRootPart") then
        local root = char.HumanoidRootPart
        for _, obj in pairs(workspace:GetDescendants()) do
            if obj.Name:lower():find("stone") or obj.Name:lower():find("rock") or obj.Name:lower():find("metal") then
                if obj:IsA("BasePart") then obj.CFrame = root.CFrame + Vector3.new(0, 2, 0) end
            end
        end
    end
end)

AddBtn("7. Romper Árboles Cercanos", function()
    local char = player.Character
    if char and char:FindFirstChild("HumanoidRootPart") then
        local root = char.HumanoidRootPart
        for _, obj in pairs(workspace:GetDescendants()) do
            if obj.Name:lower():find("tree") or obj.Name:lower():find("arbol") then
                if obj:IsA("Model") then obj:BreakJoints()
                elseif obj:IsA("BasePart") and (obj.Position - root.Position).Magnitude < 40 then obj:Destroy() end
            end
        end
    end
end)

AddHeader("COMBATE")

AddBtn("8. Aumentar Rango de Armas", function()
    local char = player.Character
    if char then
        for _, t in pairs(char:GetChildren()) do
            if t:IsA("Tool") and t:FindFirstChild("Handle") then
                t.Handle.Size = Vector3.new(8, 8, 8)
            end
        end
    end
end)

AddBtn("9. Quitar Retraso de Ataque", function()
    local char = player.Character
    if char then
        for _, t in pairs(char:GetChildren()) do
            if t:IsA("Tool") then t.ActivationThrottlingEnabled = false end
        end
    end
end)

AddBtn("10. Kill Aura Automático", function()
    task.spawn(function()
        while task.wait(0.3) do
            local char = player.Character
            if char and char:FindFirstChild("HumanoidRootPart") then
                for _, enemy in pairs(workspace:GetChildren()) do
                    if enemy:FindFirstChild("Humanoid") and enemy ~= char then
                        local root = enemy:FindFirstChild("HumanoidRootPart")
                        if root and (root.Position - char.HumanoidRootPart.Position).Magnitude < 18 then
                            enemy.Humanoid.Health = 0
                        end
                    end
                end
            end
        end
    end)
end)

AddHeader("TELEPORTS Y MAPA")

AddBtn("11. Teleport a la Fogata", function()
    local char = player.Character
    local camp = workspace:FindFirstChild("Campfire") or workspace:FindFirstChild("Camp")
    if char and camp then
        local pos = camp:IsA("Model") and camp:GetModelCFrame().Position or camp.Position
        char:MoveTo(pos + Vector3.new(0, 3, 0))
    end
end)

AddBtn("12. Visión Nocturna (FullBright)", function()
    game.Lighting.Brightness = 3
    game.Lighting.ClockTime = 14
    game.Lighting.GlobalShadows = false
end)

AddBtn("13. Eliminar Niebla", function()
    game.Lighting.FogEnd = 100000
end)

AddBtn("14. Ver Jugadores (ESP)", function()
    for _, p in pairs(Players:GetPlayers()) do
        if p ~= player and p.Character and not p.Character:FindFirstChild("Highlight") then
            Instance.new("Highlight", p.Character).FillColor = Color3.fromRGB(0, 170, 255)
        end
    end
end)

AddHeader("MOVIMIENTO Y UTILIDADES")

AddBtn("15. Super Velocidad (WalkSpeed 45)", function()
    if player.Character and player.Character:FindFirstChildOfClass("Humanoid") then
        player.Character:FindFirstChildOfClass("Humanoid").WalkSpeed = 45
    end
end)

AddBtn("16. Velocidad Normal (WalkSpeed 16)", function()
    if player.Character and player.Character:FindFirstChildOfClass("Humanoid") then
        player.Character:FindFirstChildOfClass("Humanoid").WalkSpeed = 16
    end
end)

AddBtn("17. Super Salto (JumpPower 100)", function()
    if player.Character and player.Character:FindFirstChildOfClass("Humanoid") then
        player.Character:FindFirstChildOfClass("Humanoid").JumpPower = 100
    end
end)

AddBtn("18. Salto Infinito", function()
    UserInputService.JumpRequest:Connect(function()
        if player.Character and player.Character:FindFirstChildOfClass("Humanoid") then
            player.Character:FindFirstChildOfClass("Humanoid"):ChangeState("Jumping")
        end
    end)
end)

AddBtn("19. Modo NoClip", function()
    RunService.Stepped:Connect(function()
        if player.Character then
            for _, p in pairs(player.Character:GetChildren()) do
                if p:IsA("BasePart") then p.CanCollide = false end
            end
        end
    end)
end)

AddBtn("20. Anti-AFK", function()
    local vu = game:GetService("VirtualUser")
    player.Idled:Connect(function()
        vu:CaptureController()
        vu:ClickButton2(Vector2.new())
    end)
end)
