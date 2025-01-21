-- Função para prevenir tackles
function preventTackle(character)
    -- Desativar colisões entre jogadores
    character.HumanoidRootPart.CanCollide = false
end

-- Função para driblar automaticamente
function autoDribble(character)
    while character.Parent do
        -- Verifica se o personagem está em movimento
        if character.Humanoid.MoveDirection.Magnitude > 0 then
            -- Aqui você pode adicionar a lógica do drible
            -- Como alterar a posição do personagem para simular um drible
            character.HumanoidRootPart.CFrame = character.HumanoidRootPart.CFrame * CFrame.new(0, 0, -1)
        end
        wait(0.1) -- Intervalo de tempo para a lógica do drible
    end
end

-- Evento para quando um jogador entra no jogo
game.Players.PlayerAdded:Connect(function(player)
    -- Evento para quando o jogador respawnar
    player.CharacterAdded:Connect(function(character)
        -- Previne tackles no personagem do jogador
        preventTackle(character)

        -- Inicia o drible automático
        autoDribble(character)
    end)
end)
