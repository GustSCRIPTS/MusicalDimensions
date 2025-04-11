# MusicalDimensions
local Players = game:GetService("Players")
local firstPlayerRewardGiven = false

-- Função para dar todos os passes e itens
local function giveAllRewards(player)
    -- Dá os passes pagos
    player.Passes:GivePass("2xXP")
    player.Passes:GivePass("2xMoney")
    player.Passes:GivePass("2xMaestria")
    player.Passes:GivePass("2xLevel")
    
    -- Dá todos os instrumentos
    player.Instruments:GiveAllInstruments()  -- Função fictícia para dar todos os instrumentos
    
    -- Dá itens exclusivos (se houver)
    player.Inventory:GiveExclusiveItems()  -- Função fictícia para dar itens exclusivos
    
    -- Dá uma quantidade inicial de XP e Coins
    player.leaderstats.XP.Value = 1000  -- Definir XP inicial
    player.leaderstats.Coins.Value = 500  -- Definir Coins iniciais
    
    -- Envia uma mensagem de boas-vindas
    player:SendMessage("Parabéns! Você recebeu todos os itens e passes do jogo por ser o primeiro a entrar!")
end

-- Conectar a função para o evento quando um jogador entra
Players.PlayerAdded:Connect(function(player)
    if not firstPlayerRewardGiven then
        firstPlayerRewardGiven = true
        -- Garantir que a primeira pessoa receba todas as recompensas
        giveAllRewards(player)
    end
end)
