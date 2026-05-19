# Kaito-hub
https://raw.githubusercontent.com/onepicesenpai/onepicesenpai/main/Kaitoonichan"))()
getgenv().MasterHupConfig = {
    KeySystem = false,
    SaveSettings = true,
    Discord = "không cần"
}

getgenv().MasterHup = {NoKey=true, AntiCrash=true, Version="4.2"}

-- Tải giao diện gốc
local lib=loadstring(game:HttpGet("https://raw.githubusercontent.com/onepicesenpai/onepicesenpai/main/Kaitoonichan"))()
local w=lib.CreateLib("MASTER HUP 2024 | FULL V4 + EVENT", "DarkTheme")

-- 🏠 TRANG CHÍNH
local Home=w:NewTab("🏠 Trang Chính")
Home:NewToggle("Chống AFK",false,function(v) getgenv().AntiAfk=v end)
Home:NewToggle("Đổi Server Tự Động",false,function(v) getgenv().AutoRejoin=v end)

-- 🚜 TAB FARM (đã có gom quái, click)
local Farm=w:NewTab("🚜 Auto Farm")
Farm:NewToggle("Bật Auto Farm",false,function(v) getgenv().Farm=v end)
Farm:NewSlider("Gom Quái (mét)",10,80,45,function(v) getgenv().BringRange=v end)
Farm:NewToggle("✅ Gom Quái",false,function(v) getgenv().BringMobs=v end)
Farm:NewToggle("✅ Auto Click",false,function(v) getgenv().AClick=v end)
Farm:NewSlider("✅ Tốc độ Click",1,12,7,function(v) getgenv().ClickSpeed=v end)
Farm:NewToggle("✅ Auto Mastery",false,function(v) getgenv().Mastery=v end)

-- ⚔️ TAB NÂNG TỘC V4 (ĐÃ THÊM MỚI)
local Race=w:NewTab("⚡ NÂNG TỘC V4")
Race:NewToggle("Tự làm Tộc V2 → V3 → V4",false,function(v) getgenv().FullV4=v end)
Race:NewDropdown("Chọn Tộc",{"Người","Thỏ","Cá","Quỷ","Người Máy","Rồng"},function(v) getgenv().RacePick=v end)
Race:NewToggle("Tự làm Thử Thách V4",false,function(v) getgenv().TrialV4=v end)
Race:NewToggle("Tự lấy Mảnh Vỡ",false,function(v) getgenv().FarmFrag=v end)
Race:NewSlider("Tốc độ làm V4",1,10,6,function(v) getgenv().V4Speed=v end)

-- 🎉 TAB SỰ KIỆN (ĐÃ THÊM MỚI)
local Event=w:NewTab("🎉 SỰ KIỆN")
Event:NewToggle("Tự làm Sự Kiện Biển Thú",false,function(v) getgenv().SeaBeast=v end)
Event:NewToggle("Tự làm Sự Kiện Cướp Biển",false,function(v) getgenv().PirateRaid=v end)
Event:NewToggle("Tự làm Sự Kiện Đảo Ảo",false,function(v) getgenv().Mirage=v end)
Event:NewToggle("Tự làm Boss Sự Kiện",false,function(v) getgenv().BossEvent=v end)
Event:NewToggle("Tự nhặt quà sự kiện",false,function(v) getgenv().GiftPick=v end)

-- 🍎 TRÁI + RAID + PvP
local Fruit=w:NewTab("🍎 Trái Cây")
Fruit:NewToggle("ESP + Tìm Trái",false,function(v) getgenv().FruitESP=v end)
Fruit:NewToggle("Tự lấy Trái",false,function(v) getgenv().GrabFruit=v end)

local Raid=w:NewTab("💥 Raid & Thức Tỉnh")
Raid:NewToggle("Auto Raid Tất Cả",false,function(v) getgenv().AutoRaid=v end)

local PvP=w:NewTab("🥊 Chiến Đấu")
PvP:NewToggle("Né Đòn Tự Động",false,function(v) getgenv().Dodge=v end)

-- 💧 HỆ THỐNG CHẠY CHỨC NĂNG
spawn(function()
    while task.wait(0.2)do
        -- Chống AFK
        if getgenv().AntiAfk then pcall(function() game.VirtualUser:Button2Down(Vector2.zero,workspace.Camera.CFrame)end)end
        -- Gom quái + Click
        if getgenv().BringMobs then pcall(function() for _,m in pairs(workspace.Enemies:GetChildren())do if m:FindFirstChild("Humanoid")and m.Humanoid.Health>0 then m:SetPrimaryPartCFrame(CFrame.new(game.Players.LocalPlayer.Character.HumanoidRootPart.Position+Vector3.new(0,3,0)))end end end)end
        if getgenv().AClick then task.wait(1/(getgenv().ClickSpeed or 7))pcall(function() game.ReplicatedStorage.Remotes.Click:FireServer()end)end
        -- TỰ LÀM V4
        if getgenv().FullV4 then pcall(function() getgenv().RaceSystem()end)end
        -- TỰ LÀM SỰ KIỆN
        if getgenv().SeaBeast then pcall(function() getgenv().FindSeaBeast()end)end
    end
end)
