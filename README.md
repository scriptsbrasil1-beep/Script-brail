-- Configuração
local TeleportPosition = workspace:WaitForChild("BaseLocation") -- Um objeto do tipo Part na posição da base
local player = game.Players.LocalPlayer

-- Verifica se tudo está certo
if not TeleportPosition then
    warn("BaseLocation não encontrada no workspace.")
    return
end

-- Função para teleportar o jogador
local function teleportToBase()
    local character = player.Character or player.CharacterAdded:Wait()
    if character and character:FindFirstChild("HumanoidRootPart") then
        character:MoveTo(TeleportPosition.Position)
    else
        warn("Personagem não encontrado ou HumanoidRootPart ausente.")
    end
end

-- Executa o teleporte
teleportToBase()
