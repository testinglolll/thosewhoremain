print("Carregando...")

-- Carrega a biblioteca Rayfield
local Rayfield = loadstring(game:HttpGet('https://sirius.menu/rayfield'))()

-- Agora podemos chamar Notify sem erro
task.wait(0.5) -- Pequeno delay para evitar erros
Rayfield:Notify({
    Title = "Loading...",
    Content = "Please wait...",
    Duration = 3.5,
    Image = 4483362458,
})

-- Criação da janela
local Window = Rayfield:CreateWindow({
    Name = "Ari´s HUB",
    Icon = 0, 
    LoadingTitle = "Ari´s HUB",
    LoadingSubtitle = "by Ari",
    Theme = "Default", 
 
    DisableRayfieldPrompts = false,
    DisableBuildWarnings = false, 
 
    ConfigurationSaving = {
       Enabled = true,
       FolderName = "Those Who Remain",
       FileName = "Ari Hub"
    },
 
    Discord = {
       Enabled = false,
       Invite = "noinvitelink",
       RememberJoins = true
    },
 
    KeySystem = true,
    KeySettings = {
       Title = "Key ari",
       Subtitle = "Key System",
       Note = "The key is: AriHB",
       FileName = "Key",
       SaveKey = true,
       GrabKeyFromSite = false,
       Key = {"AriHB"}
    }
})

Rayfield:Notify({
    Title = "Loaded!",
    Content = "Ari´s HUB is ready!",
    Duration = 4.5,
    Image = 4483362458,
})

-- Criando a aba corretamente
local MainTab = Window:CreateTab("Main", 4483362458)

-- Criando o botão corretamente
MainTab:CreateButton({
    Name = "Silent Aim",
    Callback = function()
        local function increaseHeadHitbox()
            local entitiesFolder = workspace:FindFirstChild("Entities")
            
            if entitiesFolder then
                local infectedFolder = entitiesFolder:FindFirstChild("Infected")
                
                if infectedFolder then
                    for _, model in pairs(infectedFolder:GetChildren()) do
                        if model:IsA("Model") then
                            local head = model:FindFirstChild("Head")
                            
                            if head and head:IsA("BasePart") then
                                head.Size = Vector3.new(40, 40, 40)  
                            end
                        end
                    end
                end
            end
        end

        task.spawn(function()
            while true do
                increaseHeadHitbox()
                task.wait(2)
                print("Silent Aim Enabled")
            end
        end)
    end
})

-- Criando parágrafos sem sobrescrever variáveis
MainTab:CreateParagraph({Title = "Best Experience", Content = "Use NoClip for the best experience."})
MainTab:CreateParagraph({Title = "Tutorial", Content = "Activate Silent Aim, use NoClip in InfiniteYield for each wave."})
