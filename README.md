--Main 
local Library = loadstring(game:HttpGet("https://raw.githubusercontent.com/xHeptc/Kavo-UI-Library/main/source.lua"))()

--Windows
local Window = Library.CreateLib("AimBot ByTokyto", "DarkTheme")

--Abas(tabs)
local Tab = Window:NewTab("Main")

Section:NewLabel("AimBot")

--Botão 
Section:NewButton("AimbotPlayer", "aimbot simples para players", function()
    print("

local Players = game:GetService("Players")
local LocalPlayer = Players.LocalPlayer
local Mouse = LocalPlayer:GetMouse()

-- Configuração do campo de visão
local FOV_RADIUS = 100

-- Função para obter o jogador inimigo mais próximo ao mouse
local function getClosestPlayer()
    local closestPlayer = nil
    local shortestDistance = FOV_RADIUS

    for _, player in pairs(Players:GetPlayers()) do
        if player ~= LocalPlayer and player.Character and player.Character:FindFirstChild("Head") then
            local screenPoint = workspace.CurrentCamera:WorldToScreenPoint(player.Character.Head.Position)
            local distance = (Vector2.new(screenPoint.X, screenPoint.Y) - Vector2.new(Mouse.X, Mouse.Y)).magnitude

            if distance < shortestDistance then
                closestPlayer = player
                shortestDistance = distance
            end
        end
    end

    return closestPlayer
end

game:GetService("RunService").RenderStepped:Connect(function()
    local target = getClosestPlayer()
    if target and target.Character and target.Character:FindFirstChild("Head") then
        print("Alvo detectado: " .. target.Name)
    end
end)")
end)
