local Lib = loadstring(game:HttpGet("https://raw.githubusercontent.com/7yhx/kwargs_Ui_Library/main/source.lua"))()

local UI = Lib:Create{
    Theme = "Dark", -- ou qualquer outro tema
    Size = UDim2.new(0, 555, 0, 400) -- padrão
}

local Main = UI:Tab{
    Name = "Inicia"
}

local Divider = Main:Divider{
    Name = "Inicia shit"
}

local QuitDivider = Main:Divider{
    Name = "Sair"
}

-- Função para obter a lista de jogadores
local function getPlayerNames()
    local playerNames = {}
    for _, player in pairs(game.Players:GetPlayers()) do
        table.insert(playerNames, player.Name) -- Insere o nome do jogador na tabela
    end
    return playerNames
end

-- Adicionando um Dropdown para selecionar os jogadores
local Players = Divider:Dropdown{
    Name = "Lista de Jogadores",
    Options = getPlayerNames(), -- Preenche com a lista de jogadores
    Callback = function(Value)
        print("Jogador selecionado: " .. Value)
    end
}

-- Escolher a cor do ESP (Aqui você pode definir a cor desejada para o ESP)
Divider:ColorPicker{
    Name = "Cor do ESP",
    Default = Color3.fromRGB(255, 0, 0), -- Definindo a cor vermelha como padrão
    Callback = function(Value)
        print("Cor do ESP escolhida: ", Value)
    end
}

local Quit = QuitDivider:Button{
    Name = "Fechar a biblioteca UI.",
    Callback = function()
        UI:Quit{
            Message = "Saindo...", -- mensagem ao fechar
            Length = 1 -- segundos que a mensagem fica visível
        }
    end
}
