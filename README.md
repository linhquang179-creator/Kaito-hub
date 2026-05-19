# Kaito-hub
https://raw.githubusercontent.com/onepicesenpai/onepicesenpai/main/onichanokaka
getgenv().MasterHupConfig = {
    KeySystem = false,
    SaveSettings = true,
    Discord = "không cần"
}

local Window = loadstring(game:HttpGet("https://raw.githubusercontent.com/onepicesenpai/onepicesenpai/main/onichanokaka"))()
local Lib = Window.CreateLib("MASTER HUP 2024", "DarkTheme")

-- TAB CHÍNH
local MainTab = Lib:NewTab("🏠 Trang Chính")
MainTab:NewToggle("Chống AFK", false, function(v) getgenv().AntiAfk = v end)
MainTab:NewToggle("Đổi Server Tự Động", false, function(v) getgenv().AutoRejoin = v end)

-- TAB FARM (ĐÚNG NHƯ BẠN MUỐN)
local FarmTab = Lib:NewTab("🚜 Auto Farm")
FarmTab:NewToggle("Bật Auto Farm", false, function(v) getgenv().AutoFarm = v end)
FarmTab:NewDropdown("Chọn Khu Vực Farm", {"Marine", "Desert", "Fountain", "Snow", "Magma", "Third Sea"}, function(v) getgenv().FarmZone = v end)
FarmTab:NewSlider("Gom Quái (mét)", 10, 80, 40, function(v) getgenv().MobRadius = v end)
FarmTab:NewToggle("✅ Gom Quái", false, function(v) getgenv().BringMobs = v end)
FarmTab:NewToggle("✅ Auto Click", false, function(v) getgenv().AutoClick = v end)
FarmTab:NewSlider("✅ Tốc Độ Click", 1, 12, 7, function(v) getgenv().ClickSpeed = v end)
FarmTab:NewToggle("✅ Fast Attack", false, function(v) getgenv().FastAttack = v end)
FarmTab:NewToggle("Auto Thành Thạo", false, function(v) getgenv().AutoMastery = v end)

-- TAB TRÁI CÂY
local FruitTab = Lib:NewTab("🍎 Trái Cây")
FruitTab:NewToggle("ESP Trái Cây", false, function(v) getgenv().FruitESP = v end)
FruitTab:NewToggle("Tự Lấy Trái", false, function(v) getgenv().AutoPickFruit = v end)

-- TAB RAID & THỨC TỈNH
local RaidTab = Lib:NewTab("⚔️ Raid & V4")
RaidTab:NewToggle("Auto Raid", false, function(v) getgenv().AutoRaid = v end)
RaidTab:NewToggle("Mở Chủng V4", false, function(v) getgenv().RaceV4 = v end)

-- TAB PVP
local PvpTab = Lib:NewTab("🥊 PvP")
PvpTab:NewToggle("Né Đòn Tự Động", false, function(v) getgenv().AutoDodge = v end)
PvpTab:NewToggle("Tăng Tốc Chạy", false, function(v) getgenv().Speed = v end)

-- CHỨC NĂNG HOẠT ĐỘNG
spawn(function()
    while task.wait(0.1) do
        if getgenv().AntiAfk then
            pcall(function() game:GetService("VirtualUser"):Button2Down(Vector2.new(0,0),workspace.CurrentCamera.CFrame) end)
        end
        if getgenv().AutoClick and getgenv().ClickSpeed then
            task.wait(1/getgenv().ClickSpeed)
            pcall(function() game:GetService("ReplicatedStorage").remotes.click:FireServer() end)
        end
    end
end)
