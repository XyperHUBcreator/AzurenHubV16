-- ============================================================
-- AZURENHUB - PIGGY 2X XP (RAYFIELD GEN2) - v16
-- Novidade: Aba Config com 10 Idiomas e Tradução em Tempo Real
-- ============================================================

-- [0] Limpeza
for _, obj in pairs(workspace:GetDescendants()) do
    for _, n in ipairs({"ESP_Highlight", "ESP_Billboard"}) do
        local f = obj:FindFirstChild(n); if f then f:Destroy() end
    end
end
pcall(function() if Drawing and Drawing.clear then Drawing.clear() end end)

-- [1] Streaming
pcall(function()
    if workspace.StreamingEnabled then
        workspace.StreamingTargetRadius = 100000
        workspace.StreamingMinRadius  = 100000
    end
end)

-- [2] Serviços e Rayfield
local Rayfield = loadstring(game:HttpGet("https://sirius.menu/gen2"))()
local Players = game:GetService("Players")
local RunService = game:GetService("RunService")
local LP = Players.LocalPlayer
local WS = workspace

-- [3] Tema Azul (Azuren)
local BlueTheme = {
    TextColor = Color3.fromRGB(255,255,255), Background = Color3.fromRGB(15,15,15),
    Topbar = Color3.fromRGB(10,50,100), Shadow = Color3.fromRGB(5,5,5),
    NotificationBackground = Color3.fromRGB(15,15,15), NotificationActionsBackground = Color3.fromRGB(50,50,50),
    TabBackground = Color3.fromRGB(20,60,120), TabStroke = Color3.fromRGB(0,150,255),
    TabBackgroundSelected = Color3.fromRGB(0,150,255), TabTextColor = Color3.fromRGB(255,255,255),
    SelectedTabTextColor = Color3.fromRGB(255,255,255), ElementBackground = Color3.fromRGB(20,40,60),
    ElementBackgroundHover = Color3.fromRGB(30,60,90), SecondaryElementBackground = Color3.fromRGB(15,30,45),
    ElementStroke = Color3.fromRGB(0,100,200), SecondaryElementStroke = Color3.fromRGB(0,50,100),
    SliderBackground = Color3.fromRGB(0,150,255), SliderProgress = Color3.fromRGB(0,150,255),
    SliderStroke = Color3.fromRGB(0,200,255), ToggleBackground = Color3.fromRGB(20,40,60),
    ToggleEnabled = Color3.fromRGB(0,150,255), ToggleDisabled = Color3.fromRGB(50,50,50),
    ToggleEnabledStroke = Color3.fromRGB(0,200,255), ToggleDisabledStroke = Color3.fromRGB(80,80,80),
    ToggleEnabledOuterStroke = Color3.fromRGB(0,100,200), ToggleDisabledOuterStroke = Color3.fromRGB(40,40,40),
    DropdownSelected = Color3.fromRGB(20,60,120), DropdownUnselected = Color3.fromRGB(20,40,60),
    InputBackground = Color3.fromRGB(20,40,60), InputStroke = Color3.fromRGB(0,150,255),
    PlaceholderColor = Color3.fromRGB(150,150,150),
}

-- ============================================================
-- [4] SISTEMA DE IDIOMAS (10 TRADUÇÕES)
-- ============================================================
local CurrentLanguage = "Português"

local Locales = {
    ["Português"] = {
        TabPlayer = "Jogador", TabESP = "ESP", TabESPConfig = "ESP Config", TabAutos = "Autos", TabSettings = "Config",
        WalkSpeed = "Velocidade", 
        ESPPlayers = "ESP Jogadores", ESPPiggy = "ESP Piggy", ESPItems = "ESP Itens / Chaves", ESPLocks = "ESP Cadeados / Portas",
        MaxDist = "Distância Máxima", Optimization = "Otimização Extrema", Tracer = "Tracer (Linhas)", ShowDist = "Mostrar Distância", RenderHighlight = "Renderizar Brilho (Trava Celular)",
        Nuke = "Auto Remover Piggys (Nuke)", SkinVeg = "Equipar Skin '3 Vegetables'", SkinCor = "Equipar Skin 'Cornélia'", AutoEscape = "Auto Escape",
        Language = "Idioma (Language)"
    },
    ["English"] = {
        TabPlayer = "Player", TabESP = "ESP", TabESPConfig = "ESP Settings", TabAutos = "Autos", TabSettings = "Config",
        WalkSpeed = "WalkSpeed", 
        ESPPlayers = "ESP Players", ESPPiggy = "ESP Piggy", ESPItems = "ESP Items / Keys", ESPLocks = "ESP Locks / Doors",
        MaxDist = "Max Distance", Optimization = "Extreme Optimization", Tracer = "Tracer (Lines)", ShowDist = "Show Distance", RenderHighlight = "Render Highlight (Lags Phone)",
        Nuke = "Auto Remove Piggys (Nuke)", SkinVeg = "Equip Skin '3 Vegetables'", SkinCor = "Equip Skin 'Cornelia'", AutoEscape = "Auto Escape",
        Language = "Language"
    },
    ["Español"] = {
        TabPlayer = "Jugador", TabESP = "ESP", TabESPConfig = "Ajustes ESP", TabAutos = "Autos", TabSettings = "Ajustes",
        WalkSpeed = "Velocidad", 
        ESPPlayers = "ESP Jugadores", ESPPiggy = "ESP Piggy", ESPItems = "ESP Objetos / Llaves", ESPLocks = "ESP Candados / Puertas",
        MaxDist = "Distancia Máxima", Optimization = "Optimización Extrema", Tracer = "Tracer (Líneas)", ShowDist = "Mostrar Distancia", RenderHighlight = "Renderizar Brillo (Laguea Celular)",
        Nuke = "Auto Eliminar Piggys (Nuke)", SkinVeg = "Equipar Skin '3 Vegetables'", SkinCor = "Equipar Skin 'Cornelia'", AutoEscape = "Auto Escape",
        Language = "Idioma"
    },
    ["Français"] = {
        TabPlayer = "Joueur", TabESP = "ESP", TabESPConfig = "Paramètres ESP", TabAutos = "Autos", TabSettings = "Paramètres",
        WalkSpeed = "Vitesse", 
        ESPPlayers = "ESP Joueurs", ESPPiggy = "ESP Piggy", ESPItems = "ESP Objets / Clés", ESPLocks = "ESP Cadenas / Portes",
        MaxDist = "Distance Max", Optimization = "Optimisation Extrême", Tracer = "Tracer (Lignes)", ShowDist = "Afficher Distance", RenderHighlight = "Afficher Surbrillance (Lag Tel)",
        Nuke = "Auto Supprimer Piggys (Nuke)", SkinVeg = "Équiper Skin '3 Vegetables'", SkinCor = "Équiper Skin 'Cornelia'", AutoEscape = "Auto Évasion",
        Language = "Langue"
    },
    ["Deutsch"] = {
        TabPlayer = "Spieler", TabESP = "ESP", TabESPConfig = "ESP Einstellungen", TabAutos = "Autos", TabSettings = "Einstellungen",
        WalkSpeed = "Geschwindigkeit", 
        ESPPlayers = "ESP Spieler", ESPPiggy = "ESP Piggy", ESPItems = "ESP Gegenstände / Schlüssel", ESPLocks = "ESP Schlösser / Türen",
        MaxDist = "Max Entfernung", Optimization = "Extreme Optimierung", Tracer = "Tracer (Linien)", ShowDist = "Entfernung Anzeigen", RenderHighlight = "Hervorhebung Anzeigen (Handy Lag)",
        Nuke = "Auto Entfernen Piggys (Nuke)", SkinVeg = "Skin '3 Vegetables' Ausrüsten", SkinCor = "Skin 'Cornelia' Ausrüsten", AutoEscape = "Auto Flucht",
        Language = "Sprache"
    },
    ["Italiano"] = {
        TabPlayer = "Giocatore", TabESP = "ESP", TabESPConfig = "Impostazioni ESP", TabAutos = "Autos", TabSettings = "Impostazioni",
        WalkSpeed = "Velocità", 
        ESPPlayers = "ESP Giocatori", ESPPiggy = "ESP Piggy", ESPItems = "ESP Oggetti / Chiavi", ESPLocks = "ESP Lucchetti / Porte",
        MaxDist = "Distanza Massima", Optimization = "Ottimizzazione Estrema", Tracer = "Tracer (Linee)", ShowDist = "Mostra Distanza", RenderHighlight = "Mostra Evidenziazione (Lag Cell)",
        Nuke = "Auto Rimuovi Piggys (Nuke)", SkinVeg = "Equipaggia Skin '3 Vegetables'", SkinCor = "Equipaggia Skin 'Cornelia'", AutoEscape = "Auto Fuga",
        Language = "Lingua"
    },
    ["Русский"] = {
        TabPlayer = "Игрок", TabESP = "ESP", TabESPConfig = "Настройки ESP", TabAutos = "Авто", TabSettings = "Настройки",
        WalkSpeed = "Скорость", 
        ESPPlayers = "ESP Игроки", ESPPiggy = "ESP Piggy", ESPItems = "ESP Предметы / Ключи", ESPLocks = "ESP Замки / Двери",
        MaxDist = "Макс Дистанция", Optimization = "Экстремальная Оптимизация", Tracer = "Трассер (Линии)", ShowDist = "Показать Дистанцию", RenderHighlight = "Показать Подсветку (Лагает)",
        Nuke = "Авто Удаление Piggys (Nuke)", SkinVeg = "Надеть Скин '3 Vegetables'", SkinCor = "Надеть Скин 'Cornelia'", AutoEscape = "Авто Побег",
        Language = "Язык"
    },
    ["日本語"] = {
        TabPlayer = "プレイヤー", TabESP = "ESP", TabESPConfig = "ESP設定", TabAutos = "自動", TabSettings = "設定",
        WalkSpeed = "速度", 
        ESPPlayers = "ESP プレイヤー", ESPPiggy = "ESP Piggy", ESPItems = "ESP アイテム / 鍵", ESPLocks = "ESP ロック / ドア",
        MaxDist = "最大距離", Optimization = "極限最適化", Tracer = "トレーサー (線)", ShowDist = "距離を表示", RenderHighlight = "ハイライトを表示 (重い)",
        Nuke = "Piggy自動削除 (Nuke)", SkinVeg = "スキン '3 Vegetables' を装備", SkinCor = "スキン 'Cornelia' を装備", AutoEscape = "自動脱出",
        Language = "言語"
    },
    ["中文"] = {
        TabPlayer = "玩家", TabESP = "ESP", TabESPConfig = "ESP设置", TabAutos = "自动", TabSettings = "设置",
        WalkSpeed = "速度", 
        ESPPlayers = "ESP 玩家", ESPPiggy = "ESP Piggy", ESPItems = "ESP 物品 / 钥匙", ESPLocks = "ESP 锁 / 门",
        MaxDist = "最大距离", Optimization = "极限优化", Tracer = "追踪线", ShowDist = "显示距离", RenderHighlight = "显示高亮 (卡顿)",
        Nuke = "自动移除Piggys (Nuke)", SkinVeg = "装备皮肤 '3 Vegetables'", SkinCor = "装备皮肤 'Cornelia'", AutoEscape = "自动逃脱",
        Language = "语言"
    },
    ["한국어"] = {
        TabPlayer = "플레이어", TabESP = "ESP", TabESPConfig = "ESP 설정", TabAutos = "자동", TabSettings = "설정",
        WalkSpeed = "속도", 
        ESPPlayers = "ESP 플레이어", ESPPiggy = "ESP Piggy", ESPItems = "ESP 아이템 / 열쇠", ESPLocks = "ESP 잠금장치 / 문",
        MaxDist = "최대 거리", Optimization = "극한 최적화", Tracer = "트레이서 (선)", ShowDist = "거리 표시", RenderHighlight = "하이라이트 표시 (렉)",
        Nuke = "Piggys 자동 제거 (Nuke)", SkinVeg = "스킨 '3 Vegetables' 장착", SkinCor = "스킨 'Cornelia' 장착", AutoEscape = "자동 탈출",
        Language = "언어"
    }
}

-- ============================================================
-- [5] VARIÁVEIS GLOBAIS E LÓGICA DO JOGO (Fora da UI)
-- ============================================================
local Config = { MaxDistance = 100, ShowDistance = true, Optimization = true, Tracer = false, RenderHighlights = false, WalkSpeed = 16 }
local espCfg = { player = {active=false}, piggy = {active=false}, item = {active=false}, lock = {active=false} }
local tracked = {}  
local nukeActive = false
local autoEscapeActive = false
local Window = nil

-- Funções de limpeza, nomes, cores, etc.
local function cleanName(rawName)
    local name = rawName:gsub("%d+", ""):gsub("_", " "):gsub("%-", " ")
    name = name:gsub("(%l)(%u)", "%1 %2"):gsub("%s+", " ")
    return name:match("^%s*(.-)%s*$")
end

local itemKeywords = {"key", "gear", "engrenagem", "wrench", "crowbar", "hammer", "pickup", "item", "collectable", "battery", "plank", "toy", "candle", "radio", "weapon", "flashlight", "medkit", "tool", "object", "prop", "sword", "gun", "melee", "quest", "scrap", "fuse", "wire"}

local function getRealItemName(obj)
    local name = obj.Name
    local n = name:lower()
    if n == "item" or n == "key" or n == "gear" or n == "tool" or n == "part" or n == "pickup" or n == "object" or n == "model" then
        for _, child in ipairs(obj:GetDescendants()) do
            local cName = child.Name:lower()
            for _, kw in ipairs(itemKeywords) do
                if cName:find(kw) then return cleanName(child.Name) end
            end
        end
    end
    if obj:IsA("Tool") and obj.ToolTip ~= "" then return cleanName(obj.ToolTip) end
    return cleanName(name)
end

local function getColorFromName(name)
    local n = name:lower()
    if n:find("green") then return Color3.fromRGB(0, 255, 0) end
    if n:find("blue") then return Color3.fromRGB(0, 150, 255) end
    if n:find("cyan") then return Color3.fromRGB(0, 255, 255) end
    if n:find("red") then return Color3.fromRGB(255, 0, 0) end
    if n:find("yellow") then return Color3.fromRGB(255, 255, 0) end
    if n:find("purple") then return Color3.fromRGB(180, 0, 255) end
    if n:find("orange") then return Color3.fromRGB(255, 100, 0) end
    if n:find("pink") then return Color3.fromRGB(255, 105, 180) end
    return Color3.fromRGB(255, 255, 255)
end

local function getBestPart(obj)
    if obj:IsA("BasePart") then return obj end
    for _, v in ipairs(obj:GetChildren()) do
        if v:IsA("BasePart") and v.Transparency < 0.9 then return v end
    end
    return obj:FindFirstChildWhichIsA("BasePart") or obj.PrimaryPart
end

local function isPlayerChar(obj) return Players:GetPlayerFromCharacter(obj) ~= nil end
local function isHeldByMe(obj)
    if obj:IsDescendantOf(LP.Character) then return true end
    local bp = LP:FindFirstChild("Backpack")
    return bp and obj:IsDescendantOf(bp)
end
local function isJunk(name)
    local n = name:lower()
    return n:find("unlock") or n:find("button") or n:find("screen") or n:find("generator") or n:find("hitbox") or n:find("effect")
end
local function isPiggyModel(obj)
    return obj:IsA("Model") and not isPlayerChar(obj) and obj ~= LP.Character and not isJunk(obj.Name) and obj:FindFirstChildOfClass("Humanoid") ~= nil
end
local function isItemObject(obj)
    if isPlayerChar(obj) or isHeldByMe(obj) or isJunk(obj.Name) then return false end
    if obj:IsA("Tool") then return true end
    local n = obj.Name:lower()
    if n == "part" or n == "handle" or n == "main" or n == "" then return false end
    for _, kw in ipairs(itemKeywords) do if n:find(kw) then return true end end
    if obj:IsA("Model") or obj:IsA("BasePart") then
        for _, child in ipairs(obj:GetChildren()) do
            local cName = child.Name:lower()
            for _, kw in ipairs(itemKeywords) do if cName:find(kw) then return true end end
        end
    end
    if obj.Parent and obj.Parent ~= WS then
        local pName = obj.Parent.Name:lower()
        if pName:find("item") or pName:find("pickup") or pName:find("tool") or pName:find("drop") then return true end
    end
    return false
end
local function isLockObject(obj)
    if isPlayerChar(obj) or isHeldByMe(obj) or isJunk(obj.Name) then return false end
    if obj:IsA("BasePart") and obj.Parent and obj.Parent:IsA("Model") then return false end
    local n = obj.Name:lower()
    if n == "main" or n == "door" or n:find("hinge") or n:find("frame") then return false end
    return (n:find("lock") or n:find("door")) and not n:find("unlock")
end

-- Funções do ESP
local function createESPs(obj, category)
    if tracked[obj] or obj:FindFirstChild("ESP_Billboard") then return end
    local realName = getRealItemName(obj)
    if realName == "" then return end 

    local color = getColorFromName(realName)
    local prefix = ""
    if category == "item" then prefix = "[ITEM] "; if color == Color3.fromRGB(255,255,255) then color = Color3.fromRGB(0, 255, 0) end
    elseif category == "lock" then prefix = "[LOCK] "; if color == Color3.fromRGB(255,255,255) then color = Color3.fromRGB(255, 165, 0) end
    elseif category == "piggy" then prefix = "[PIGGY] "; color = Color3.fromRGB(255, 0, 255)
    elseif category == "player" then prefix = "[PLAYER] "; color = Color3.fromRGB(255, 0, 0) end

    local bestPart = getBestPart(obj) or obj

    local bb = Instance.new("BillboardGui")
    bb.Name = "ESP_Billboard"
    bb.Adornee = bestPart 
    bb.Size = UDim2.new(0, 100, 0, 15)
    bb.StudsOffset = Vector3.new(0, 2, 0)
    bb.AlwaysOnTop = true
    bb.MaxDistance = math.huge
    bb.LightInfluence = 0
    bb.Parent = bestPart 

    local label = Instance.new("TextLabel")
    label.Name = "Label"
    label.Size = UDim2.new(1, 0, 1, 0)
    label.BackgroundTransparency = 1
    label.TextColor3 = color
    label.TextStrokeTransparency = 0.5 
    label.TextScaled = true
    label.Font = Enum.Font.GothamBold
    label.Text = prefix .. realName
    label.Parent = bb

    local tracer = nil
    if Drawing then
        tracer = Drawing.new("Line")
        tracer.Thickness = 1
        tracer.Color = color
        tracer.Visible = false
    end

    tracked[obj] = { highlight = nil, billboard = bb, category = category, part = bestPart, tracer = tracer, color = color }
end

local function removeESPs(obj)
    local d = tracked[obj]; if not d then return end
    if d.highlight then d.highlight:Destroy() end
    if d.billboard then d.billboard:Destroy() end
    if d.tracer then d.tracer:Remove() end
    tracked[obj] = nil
end

local function clearCategory(cat)
    for obj, d in pairs(tracked) do
        if d.category == cat then removeESPs(obj) end
    end
end

local function scanAndApply()
    for _, obj in pairs(WS:GetDescendants()) do
        if espCfg.player.active and obj:IsA("Model") and isPlayerChar(obj) and obj ~= LP.Character then createESPs(obj, "player")
        elseif espCfg.piggy.active and isPiggyModel(obj) then createESPs(obj, "piggy")
        elseif espCfg.item.active and isItemObject(obj) then createESPs(obj, "item")
        elseif espCfg.lock.active and isLockObject(obj) then createESPs(obj, "lock") end
    end
end

WS.DescendantAdded:Connect(function(obj)
    task.wait(0.1)
    if espCfg.player.active and obj:IsA("Model") and isPlayerChar(obj) then createESPs(obj, "player")
    elseif espCfg.piggy.active and isPiggyModel(obj) then createESPs(obj, "piggy")
    elseif espCfg.item.active and isItemObject(obj) then createESPs(obj, "item")
    elseif espCfg.lock.active and isLockObject(obj) then createESPs(obj, "lock") end
end)

-- Loop de Renderização
task.spawn(function()
    while task.wait(0.1) do
        local char = LP.Character
        local hrp  = char and char:FindFirstChild("HumanoidRootPart")
        if not hrp then continue end
        local cam = workspace.CurrentCamera
        local screenCenter = Vector2.new(cam.ViewportSize.X / 2, cam.ViewportSize.Y)

        for obj, d in pairs(tracked) do
            if not obj or not obj.Parent or not d.part or not d.part.Parent then
                removeESPs(obj)
            else
                local dist = math.floor((hrp.Position - d.part.Position).Magnitude)
                if dist <= Config.MaxDistance then
                    d.billboard.Enabled = true
                    local prefix = ""
                    if d.category == "item" then prefix = "[ITEM] "
                    elseif d.category == "lock" then prefix = "[LOCK] "
                    elseif d.category == "piggy" then prefix = "[PIGGY] "
                    elseif d.category == "player" then prefix = "[PLAYER] " end
                    d.billboard.Label.Text = Config.ShowDistance and (prefix .. getRealItemName(obj) .. " [" .. dist .. "m]") or (prefix .. getRealItemName(obj))
                    if Config.Optimization then
                        d.billboard.Size = UDim2.new(0, 80, 0, 10)
                        d.billboard.StudsOffset = Vector3.new(0, 1, 0)
                    else
                        d.billboard.Size = UDim2.new(0, 150, 0, 20)
                        d.billboard.StudsOffset = Vector3.new(0, 2, 0)
                    end
                    if Config.Tracer and d.tracer then
                        local screenPos, onScreen = cam:WorldToViewportPoint(d.part.Position)
                        if onScreen then
                            d.tracer.From = screenCenter
                            d.tracer.To = Vector2.new(screenPos.X, screenPos.Y)
                            d.tracer.Visible = true
                        else d.tracer.Visible = false end
                    elseif d.tracer then d.tracer.Visible = false end
                    if Config.RenderHighlights then
                        if not d.highlight then
                            local hl = Instance.new("Highlight")
                            hl.FillColor = d.color
                            hl.OutlineColor = Color3.fromRGB(255,255,255)
                            hl.FillTransparency = 0.8
                            hl.OutlineTransparency = 0.2
                            hl.DepthMode = Enum.HighlightDepthMode.AlwaysOnTop
                            hl.Parent = obj
                            d.highlight = hl
                        end
                    else if d.highlight then d.highlight:Destroy(); d.highlight = nil end end
                else
                    d.billboard.Enabled = false
                    if d.tracer then d.tracer.Visible = false end
                    if d.highlight then d.highlight:Destroy(); d.highlight = nil end
                end
            end
        end
    end
end)

-- Loops de Autos
task.spawn(function()
    while task.wait(1) do
        if nukeActive then
            for _, obj in pairs(WS:GetDescendants()) do
                if isPiggyModel(obj) then obj:Destroy() end
            end
        end
        if autoEscapeActive then
            local hrp = LP.Character and LP.Character:FindFirstChild("HumanoidRootPart")
            if hrp then
                for _, obj in ipairs(WS:GetDescendants()) do
                    if obj:IsA("BasePart") and (obj.Name:lower():find("exit") or obj.Name:lower():find("helicopter")) then
                        hrp.CFrame = CFrame.new(obj.Position + Vector3.new(0, 5, 0))
                        break
                    end
                end
            end
        end
    end
end)

-- ============================================================
-- [6] CONSTRUÇÃO DA INTERFACE (Reconstruída ao mudar idioma)
-- ============================================================
local function BuildUI()
    if Window then
        Window:Destroy()
    end
    
    local L = Locales[CurrentLanguage]
    
    Window = Rayfield:CreateWindow({
        name = "AzurenHub | Piggy 2x XP",
        subtitle = "v16 - " .. CurrentLanguage,
        theme = BlueTheme,
        configuration = { autoSave = false }, -- Desativado temporariamente para não bugar os idiomas
        keySystem = false
    })

    -- Jogador
    local PlayerTab = Window:CreateTab({ name = L.TabPlayer, icon = 4483362458 })
    PlayerTab:CreateSlider({
        name = L.WalkSpeed, range = {16,300}, increment = 1, suffix = "spd",
        value = Config.WalkSpeed, flag = "SpeedSlider",
        callback = function(v)
            Config.WalkSpeed = v
            if LP.Character and LP.Character:FindFirstChild("Humanoid") then
                LP.Character.Humanoid.WalkSpeed = v
            end
        end
    })

    -- ESP Categorias
    local ESPTab = Window:CreateTab({ name = L.TabESP, icon = 4483362458 })
    ESPTab:CreateToggle({
        name = L.ESPPlayers, value = espCfg.player.active,
        callback = function(v) espCfg.player.active = v; if v then scanAndApply() else clearCategory("player") end
    })
    ESPTab:CreateToggle({
        name = L.ESPPiggy, value = espCfg.piggy.active,
        callback = function(v) espCfg.piggy.active = v; if v then scanAndApply() else clearCategory("piggy") end
    })
    ESPTab:CreateToggle({
        name = L.ESPItems, value = espCfg.item.active,
        callback = function(v) espCfg.item.active = v; if v then scanAndApply() else clearCategory("item") end
    })
    ESPTab:CreateToggle({
        name = L.ESPLocks, value = espCfg.lock.active,
        callback = function(v) espCfg.lock.active = v; if v then scanAndApply() else clearCategory("lock") end
    })

    -- ESP Config
    local ConfigTab = Window:CreateTab({ name = L.TabESPConfig, icon = 4483362458 })
    ConfigTab:CreateSlider({
        name = L.MaxDist, range = {20, 300}, increment = 10, suffix = "m", value = Config.MaxDistance,
        callback = function(v) Config.MaxDistance = v end
    })
    ConfigTab:CreateToggle({
        name = L.Optimization, value = Config.Optimization,
        callback = function(v) Config.Optimization = v end
    })
    ConfigTab:CreateToggle({
        name = L.Tracer, value = Config.Tracer,
        callback = function(v) Config.Tracer = v end
    })
    ConfigTab:CreateToggle({
        name = L.ShowDist, value = Config.ShowDistance,
        callback = function(v) Config.ShowDistance = v end
    })
    ConfigTab:CreateToggle({
        name = L.RenderHighlight, value = Config.RenderHighlights,
        callback = function(v)
            Config.RenderHighlights = v
            if not v then for obj, d in pairs(tracked) do if d.highlight then d.highlight:Destroy(); d.highlight = nil end end end
        end
    })

    -- Autos
    local AutoTab = Window:CreateTab({ name = L.TabAutos, icon = 4483362458 })
    AutoTab:CreateToggle({
        name = L.Nuke, value = nukeActive,
        callback = function(v) nukeActive = v end
    })
    AutoTab:CreateButton({
        name = L.SkinVeg,
        callback = function()
            for _, gui in ipairs(LP.PlayerGui:GetDescendants()) do
                if (gui:IsA("TextButton") or gui:IsA("ImageButton")) and (gui.Name:lower():find("vegetable") or (gui.Text and gui.Text:lower():find("vegetable"))) then gui:Activate(); break end
            end
        end
    })
    AutoTab:CreateButton({
        name = L.SkinCor,
        callback = function()
            for _, gui in ipairs(LP.PlayerGui:GetDescendants()) do
                if (gui:IsA("TextButton") or gui:IsA("ImageButton")) and (gui.Name:lower():find("cornelia") or (gui.Text and gui.Text:lower():find("cornelia"))) then gui:Activate(); break end
            end
        end
    })
    AutoTab:CreateToggle({
        name = L.AutoEscape, value = autoEscapeActive,
        callback = function(v) autoEscapeActive = v end
    })

    -- Config (Idiomas)
    local SettingsTab = Window:CreateTab({ name = L.TabSettings, icon = 4483362458 })
    SettingsTab:CreateDropdown({
        name = L.Language,
        options = {"Português", "English", "Español", "Français", "Deutsch", "Italiano", "Русский", "日本語", "中文", "한국어"},
        currentOption = CurrentLanguage,
        multipleOptions = false,
        callback = function(option)
            if type(option) == "table" then
                CurrentLanguage = option[1]
            else
                CurrentLanguage = option
            end
            BuildUI() -- Reconstrói o painel no novo idioma
        end
    })
end

BuildUI() -- Inicia a UI
