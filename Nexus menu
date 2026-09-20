-- ===============================================
-- NEXUS SCRIPT - ULTIMATE SUPER VIP PACK
-- С умным детектором игр и авто-подгрузкой
-- Ключи: FREE2026, NEXUS2026
-- ===============================================

local Players = game:GetService("Players")
local LocalPlayer = Players.LocalPlayer
local RunService = game:GetService("RunService")
local UserInputService = game:GetService("UserInputService")
local VirtualUser = game:GetService("VirtualUser")
local Workspace = game:GetService("Workspace")
local MarketplaceService = game:GetService("MarketplaceService")

-- База данных известных игр и их бесплатных скриптов (можешь добавлять сюда свои)
local GameDatabase = {
   [3956818381] = {Name = "Ninja Legends", ScriptUrl = "https://raw.githubusercontent.com/example/ninjalegends/main/script.lua"},
   [286090429]  = {Name = "Arsenal", ScriptUrl = "https://raw.githubusercontent.com/example/arsenal/main/script.lua"},
   [6516141723] = {Name = "Doors", ScriptUrl = "https://raw.githubusercontent.com/example/doors/main/script.lua"},
}

local CurrentPlaceId = game.PlaceId
local DetectedGame = GameDatabase[CurrentPlaceId]

local GameName = "Неизвестная игра"
local ScriptStatus = "❌ Скрипт для этой игры не найден"

pcall(function()
   local placeInfo = MarketplaceService:GetProductInfo(CurrentPlaceId)
   GameName = placeInfo.Name
end)

if DetectedGame then
   ScriptStatus = "✅ Найден бесплатный скрипт для: " .. DetectedGame.Name
end

local Rayfield = loadstring(game:HttpGet('https://sirius.menu/rayfield'))()

local Window = Rayfield:CreateWindow({
   Name = "Nexus Script | Super VIP",
   LoadingTitle = "Загрузка Super VIP...",
   LoadingSubtitle = GameName,
   ConfigurationSaving = { Enabled = false },
   KeySystem = true,
   KeySettings = {
      Title = "Nexus Script | Key System",
      Subtitle = "Введите ключ доступа",
      Note = "Ключ: FREE2026",
      SaveKey = false,
      Key = {"FREE2026", "NEXUS2026"}
   }
})

-- Ссылка на канал в буфер
setclipboard("https://t.me/nexus_executor")

-- ВКЛАДКА 1: ДЕТЕКТОР ИГР И СЕКРЕТЫ
local MainTab = Window:CreateTab("Детектор & Читы ⚡", 4483345998)

MainTab:CreateSection("Умный детектор игр")

MainTab:CreateButton({
   Name = "🎮 Игра: " .. GameName,
   Callback = function()
      Rayfield:Notify({
         Title = "Game Detector",
         Content = "PlaceID: " .. CurrentPlaceId,
         Duration = 4
      })
   end,
})

MainTab:CreateButton({
   Name = ScriptStatus,
   Callback = function()
      if DetectedGame then
         Rayfield:Notify({
            Title = "Загрузка...",
            Content = "Подгружаем скрипт для игры...",
            Duration = 3
         })
         pcall(function()
            loadstring(game:HttpGet(DetectedGame.ScriptUrl))()
         end)
      else
         Rayfield:Notify({
            Title = "Внимание",
            Content = "Для этой новой или случайной игры скрипт не найден!",
            Duration = 4
         })
      end
   end,
})

MainTab:CreateSection("Уникальные механики")

-- Портальная пушка
MainTab:CreateButton({
   Name = "🌀 Загрузить Портальную пушку (Portal Gun)",
   Callback = function()
      pcall(function()
         loadstring(game:HttpGet("https://raw.githubusercontent.com/rickandmorty63753882/Iryexnpvi2/refs/heads/main/YaGul.lua"))()
      end)
      Rayfield:Notify({Title = "Portal Gun", Content = "Пушка загружена!", Duration = 3})
   end,
})

-- Остановка времени
MainTab:CreateButton({
   Name = "⏳ Активировать остановку времени (Time Stop)",
   Callback = function()
      pcall(function()
         loadstring(game:HttpGet("https://raw.githubusercontent.com/rickandmorty63753882/Timestop/refs/heads/main/Iryex.lua"))()
      end)
      Rayfield:Notify({Title = "Time Stop", Content = "Время остановлено!", Duration = 3})
   end,
})

-- Гравитация на 1.5 минуты
MainTab:CreateButton({
   Name = "🪐 Гравитация на 1.5 мин (Low Gravity)",
   Callback = function()
      Workspace.Gravity = 50
      Rayfield:Notify({Title = "Гравитация", Content = "Снижена на 1.5 минуты!", Duration = 4})
      task.delay(90, function()
         Workspace.Gravity = 196.2
         Rayfield:Notify({Title = "Гравитация", Content = "Восстановлена.", Duration = 3})
      end)
   end,
})

MainTab:CreateSection("Передвижение")

-- Fly
local Flying = false
MainTab:CreateToggle({
   Name = "🛸 Полет (Fly)",
   CurrentValue = false,
   Flag = "FlyToggle",
   Callback = function(Value)
      Flying = Value
      local char = LocalPlayer.Character
      if char and char:FindFirstChild("HumanoidRootPart") then
         local rootPart = char.HumanoidRootPart
         if Flying then
            local bv = Instance.new("BodyVelocity")
            bv.Name = "NexusFly"
            bv.Parent = rootPart
            bv.MaxForce = Vector3.new(math.huge, math.huge, math.huge)
            bv.Velocity = Vector3.new(0, 0, 0)
            task.spawn(function()
               while Flying and char and rootPart do
                  bv.Velocity = Workspace.CurrentCamera.CFrame.LookVector * 50
                  task.wait()
               end
               if bv then bv:Destroy() end
            end)
         else
            if rootPart:FindFirstChild("NexusFly") then rootPart.NexusFly:Destroy() end
         end
      end
   end,
})

-- Noclip
local NoclipEnabled = false
MainTab:CreateToggle({
   Name = "👻 Проход сквозь стены (Noclip)",
   CurrentValue = false,
   Flag = "NoclipToggle",
   Callback = function(Value)
      NoclipEnabled = Value
   end,
})

RunService.Stepped:Connect(function()
   if NoclipEnabled and LocalPlayer.Character then
      for _, part in ipairs(LocalPlayer.Character:GetDescendants()) do
         if part:IsA("BasePart") then part.CanCollide = false end
      end
   end
end)

-- Анти-АФК
local AntiAfkEnabled = true
MainTab:CreateToggle({
   Name = "⏳ Анти-АФК (Anti-AFK)",
   CurrentValue = true,
   Flag = "AntiAfkToggle",
   Callback = function(Value)
      AntiAfkEnabled = Value
   end,
})

LocalPlayer.Idled:Connect(function()
   if AntiAfkEnabled then
      VirtualUser:Button2Down(Vector2.new(0,0), Workspace.CurrentCamera.CFrame)
      task.wait(1)
      VirtualUser:Button2Up(Vector2.new(0,0), Workspace.CurrentCamera.CFrame)
   end
end)


-- ВКЛАДКА 2: ВИЗУАЛ И ESP
local VisualTab = Window:CreateTab("Визуал & ESP 👁", 4483345998)

VisualTab:CreateSection("Настройка ESP")

VisualTab:CreateButton({
   Name = "🟢 Включить обычный ESP",
   Callback = function()
      for _, player in ipairs(Players:GetPlayers()) do
         if player ~= LocalPlayer and player.Character and not player.Character:FindFirstChild("NexusESP") then
            local hl = Instance.new("Highlight")
            hl.Name = "NexusESP"
            hl.Adornee = player.Character
            hl.FillColor = Color3.fromRGB(0, 255, 100)
            hl.Parent = player.Character
         end
      end
      Rayfield:Notify({Title = "ESP", Content = "Включен!", Duration = 3})
   end,
})

-- Rainbow ESP
local RainbowEspActive = false
VisualTab:CreateToggle({
   Name = "🌈 Радужный ESP (Rainbow ESP)",
   CurrentValue = false,
   Flag = "RainbowEsp",
   Callback = function(Value)
      RainbowEspActive = Value
      task.spawn(function()
         while RainbowEspActive do
            local hue = tick() % 5 / 5
            local rainbowColor = Color3.fromHSV(hue, 1, 1)
            for _, player in ipairs(Players:GetPlayers()) do
               if player ~= LocalPlayer and player.Character then
                  local hl = player.Character:FindFirstChild("NexusESP")
                  if hl then hl.FillColor = rainbowColor end
               end
            end
            task.wait(0.1)
         end
      end)
   end,
})

VisualTab:CreateButton({
   Name = "🔴 Выключить ESP",
   Callback = function()
      RainbowEspActive = false
      for _, player in ipairs(Players:GetPlayers()) do
         if player.Character then
            local hl = player.Character:FindFirstChild("NexusESP")
            if hl then hl:Destroy() end
         end
      end
      Rayfield:Notify({Title = "ESP", Content = "Отключен.", Duration = 3})
   end,
})


-- ВКЛАДКА 3: НАСТРОЙКИ ИГРОКА И AIMBOT
local StatsTab = Window:CreateTab("Слайдеры & Aimbot ⚙️", 4483345998)

StatsTab:CreateSection("Параметры персонажа")

StatsTab:CreateSlider({
   Name = "⚡️ Скорость бега (WalkSpeed)",
   Range = {16, 300},
   Increment = 1,
   CurrentValue = 16,
   Callback = function(Value)
      if LocalPlayer.Character and LocalPlayer.Character:FindFirstChild("Humanoid") then
         LocalPlayer.Character.Humanoid.WalkSpeed = Value
      end
   end,
})

StatsTab:CreateSlider({
   Name = "🦘 Высота прыжка (JumpPower)",
   Range = {50, 400},
   Increment = 1,
   CurrentValue = 50,
   Callback = function(Value)
      if LocalPlayer.Character and LocalPlayer.Character:FindFirstChild("Humanoid") then
         LocalPlayer.Character.Humanoid.JumpPower = Value
      end
   end,
})

StatsTab:CreateSection("Прицел")

StatsTab:CreateToggle({
   Name = "🎯 Простой Aimbot",
   CurrentValue = false,
   Flag = "AimbotToggle",
   Callback = function(Value)
      _G.Aimbot = Value
      task.spawn(function()
         while _G.Aimbot do
            local closestPlayer = nil
            local shortestDist = math.huge
            for _, p in ipairs(Players:GetPlayers()) do
               if p ~= LocalPlayer and p.Character and p.Character:FindFirstChild("Head") then
                  local dist = (p.Character.Head.Position - LocalPlayer.Character.Head.Position).Magnitude
                  if dist < shortestDist then
                     shortestDist = dist
                     closestPlayer = p
                  end
               end
            end
            if closestPlayer and closestPlayer.Character:FindFirstChild("Head") then
               Workspace.CurrentCamera.CFrame = CFrame.new(Workspace.CurrentCamera.CFrame.Position, closestPlayer.Character.Head.Position)
            end
            task.wait()
         end
      end)
   end,
})


-- ВКЛАДКА 4: АДМИНКА
local AdminTab = Window:CreateTab("Секретная Админка 🛠", 4483345998)

AdminTab:CreateSection("Инструменты")

AdminTab:CreateButton({
   Name = "👑 Выдать инструмент",
   Callback = function()
      pcall(function()
         local tool = Instance.new("Tool")
         tool.Name = "Nexus Admin Wand"
         tool.Parent = LocalPlayer.Backpack
      end)
      Rayfield:Notify({Title = "Tools", Content = "Выдано!", Duration = 3})
   end,
})

AdminTab:CreateButton({
   Name = "📢 Скопировать наш Telegram",
   Callback = function()
      setclipboard("https://t.me/nexus_executor")
      Rayfield:Notify({Title = "Telegram", Content = "Ссылка скопирована!", Duration = 3})
   end,
})
