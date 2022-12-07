--idc if you look at my shit code your a fucking skid if you steal it so yeah fuck you shoutout my nigga nammeed veno

local Library = loadstring(game:HttpGet("https://raw.githubusercontent.com/xHeptc/Kavo-UI-Library/main/source.lua"))()
local Window = Library.CreateLib("NASA.EXE (veno on top) https://discord.gg/eeu2wWv2 - Beta", "Midnight")


--MAIN--


local AIMLOCKS = Window:NewTab("aimlock and silent aim")
local aimlock = AIMLOCKS:NewSection("AIMLCOK HERE!")


local MOVEMENT = Window:NewTab("movment")
local dad  = MOVEMENT:NewSection("MOVMENT/SPEED!")


local ESP = Window:NewTab("esp")
local esp = ESP:NewSection("ESP!")


local PLAYER = Window:NewTab("player")
local player = PLAYER:NewSection("PLAYER")


local EASY = Window:NewTab("more")
local easy = EASY:NewSection("MORE SUTFF HERE")






aimlock:NewButton("streamble silient aim", "makes the aimbot look streamble", function()
-- // Services
local Players = game:GetService("Players")

-- // Vars
local LocalPlayer = Players.LocalPlayer
local accomidationfactor = .1213

-- // Silent Aim Module
local SilentAim = loadstring(game:HttpGet("https://pastebin.com/raw/2f0mGbMP"))()
SilentAim.TeamCheck = false
-- // Metatable vars
local mt = getrawmetatable(game)
local backupindex = mt.__index
setreadonly(mt, false)

-- // Check if player is down
SilentAim.checkSilentAim = function()
    local checkA = (SilentAim.SilentAimEnabled == true and SilentAim.Selected ~= LocalPlayer)
    local playerCharacter = SilentAim.Selected.Character
    local daHood = (playerCharacter.BodyEffects["K.O"].Value == false or playerCharacter:FindFirstChild("GRABBING_CONSTRAINT") ~= nil)

    return (checkA and daHood)
end

-- // Hook
mt.__index = newcclosure(function(t, k)
    if (t:IsA("Mouse") and (k == "Hit")) then
        print(t, k)
        local CPlayer = SilentAim.Selected
        if (SilentAim.checkSilentAim()) then
            if (CPlayer.Character:FindFirstChild("HumanoidRootPart")) then
                return {p=(CPlayer.Character.HumanoidRootPart.CFrame.p+(CPlayer.Character.HumanoidRootPart.Velocity*accomidationfactor))}
            end
        end
    end
    return backupindex(t, k)
end)

-- // Revert
setreadonly(mt, true)
end)







aimlock:NewButton("AimLock", "gives you aimbot!:)", function()
local Settings = {
    rewrittenmain = {
        Enabled = true,
        Key = "q",
        DOT = true,
        AIRSHOT = true,
        NOTIF = true,
        AUTOPRED = false,
        FOV = math.huge,
        RESOVLER = false
    }
}
 
local SelectedPart = "LowerTorso"
local Prediction = true
local PredictionValue = .1208726
 
 
    local AnchorCount = 0
    local MaxAnchor = 6
 
    local CC = game:GetService"Workspace".CurrentCamera
    local Plr;
    local enabled = false
    local accomidationfactor = .1208726
    local mouse = game.Players.LocalPlayer:GetMouse()
    local placemarker = Instance.new("Part", game.Workspace)
 
    function makemarker(Parent, Adornee, Color, Size, Size2)
        local e = Instance.new("BillboardGui", Parent)
        e.Name = "PP"
        e.Adornee = Adornee
        e.Size = UDim2.new(Size, Size2, Size, Size2)
        e.AlwaysOnTop = Settings.rewrittenmain.DOT
        local a = Instance.new("Frame", e)
        if Settings.rewrittenmain.DOT == true then
        a.Size = UDim2.new(1, 0, 1, 0)
        else
        a.Size = UDim2.new(0, 0, 0, 0)
        end
        if Settings.rewrittenmain.DOT == true then
        a.Transparency = 0
        a.BackgroundTransparency = 0
        else
        a.Transparency = 1
        a.BackgroundTransparency = 1
        end
        a.BackgroundColor3 = Color
        local g = Instance.new("UICorner", a)
        if Settings.rewrittenmain.DOT == false then
        g.CornerRadius = UDim.new(0, 0)
        else
        g.CornerRadius = UDim.new(1, 1) 
        end
        return(e)
    end
 
 
    local data = game.Players:GetPlayers()
    function noob(player)
        local character
        repeat wait() until player.Character
        local handler = makemarker(guimain, player.Character:WaitForChild(SelectedPart), Color3.fromRGB(180, 125, 180), 0.3, 3)
        handler.Name = player.Name
        player.CharacterAdded:connect(function(Char) handler.Adornee = Char:WaitForChild(SelectedPart) end)
 
 
        spawn(function()
            while wait() do
                if player.Character then
                end
            end
        end)
    end
 
    for i = 1, #data do
        if data[i] ~= game.Players.LocalPlayer then
            noob(data[i])
        end
    end
 
    game.Players.PlayerAdded:connect(function(Player)
        noob(Player)
    end)
 
    spawn(function()
        placemarker.Anchored = true
        placemarker.CanCollide = false
        if Settings.rewrittenmain.DOT == true then
        placemarker.Size = Vector3.new(7, 7, 7)
        else
        placemarker.Size = Vector3.new(0, 0, 0)
        end
        placemarker.Transparency = 0.60
        if Settings.rewrittenmain.DOT then
        makemarker(placemarker, placemarker, Color3.fromRGB(180, 125, 180), 0.40, 0)
        end
    end)
 
    game.Players.LocalPlayer:GetMouse().KeyDown:Connect(function(k)
        if k == Settings.rewrittenmain.Key and Settings.rewrittenmain.Enabled then
            if enabled == true then
                enabled = false
                if Settings.rewrittenmain.NOTIF == true then
                    Plr = getClosestPlayerToCursor()
                game.StarterGui:SetCore("SendNotification", {
                    Title = "THANKS FOR USING NASA.EXE";
                    Text = "UNLOCKED",
                    Duration = 3
                })
            end
            else
                Plr = getClosestPlayerToCursor()
                enabled = true
                if Settings.rewrittenmain.NOTIF == true then
 
                    game.StarterGui:SetCore("SendNotification", {
                        Title = "THANKS FOR USING NASA.EXE";
                        Text = "Target: "..tostring(Plr.Character.Humanoid.DisplayName),
                        Duration = 3
                    })
 
                end
            end
        end
    end)
 
 
 
    function getClosestPlayerToCursor()
        local closestPlayer
        local shortestDistance = Settings.rewrittenmain.FOV
 
        for i, v in pairs(game.Players:GetPlayers()) do
            if v ~= game.Players.LocalPlayer and v.Character and v.Character:FindFirstChild("Humanoid") and v.Character.Humanoid.Health ~= 0 and v.Character:FindFirstChild("HumanoidRootPart") then
                local pos = CC:WorldToViewportPoint(v.Character.PrimaryPart.Position)
                local magnitude = (Vector2.new(pos.X, pos.Y) - Vector2.new(mouse.X, mouse.Y)).magnitude
                if magnitude < shortestDistance then
                    closestPlayer = v
                    shortestDistance = magnitude
                end
            end
        end
        return closestPlayer
    end
 
    local pingvalue = nil;
    local split = nil;
    local ping = nil;
 
    game:GetService"RunService".Stepped:connect(function()
        if enabled and Plr.Character ~= nil and Plr.Character:FindFirstChild("HumanoidRootPart") then
            placemarker.CFrame = CFrame.new(Plr.Character.HumanoidRootPart.Position+(Plr.Character.HumanoidRootPart.Velocity*accomidationfactor))
        else
            placemarker.CFrame = CFrame.new(0, 9999, 0)
        end
        if Settings.rewrittenmain.AUTOPRED == true then
             pingvalue = game:GetService("Stats").Network.ServerStatsItem["Data Ping"]:GetValueString()
             split = string.split(pingvalue,'(')
             ping = tonumber(split[1])
            if ping < 130 then
                PredictionValue = .1208726
            elseif ping < 125 then
                PredictionValue = .1208726
            elseif ping < 110 then
                PredictionValue = .1208726
            elseif ping < 105 then
                PredictionValue = .1208726
            elseif ping < 90 then
                PredictionValue = .1208726
            elseif ping < 80 then
                PredictionValue = .1208726
            elseif ping < 70 then
                PredictionValue = .1208726
            elseif ping < 60 then
                PredictionValue = .1208726
            elseif ping < 50 then
                PredictionValue = .1208726
            elseif ping < 40 then
                PredictionValue = .1208726
            end
        end
    end)
 
    local mt = getrawmetatable(game)
    local old = mt.__namecall
    setreadonly(mt, false)
    mt.__namecall = newcclosure(function(...)
        local args = {...}
        if enabled and getnamecallmethod() == "FireServer" and args[2] == "UpdateMousePos" and Settings.rewrittenmain.Enabled and Plr.Character ~= nil then
 
            -- args[3] = Plr.Character.HumanoidRootPart.Position+(Plr.Character.HumanoidRootPart.Velocity*accomidationfactor)
            --[[
            if Settings.rewrittenmain.AIRSHOT == true then
                if game.Workspace.Players[Plr.Name].Humanoid:GetState() == Enum.HumanoidStateType.Freefall then -- Plr.Character:WaitForChild("Humanoid"):GetState() == Enum.HumanoidStateType.Freefall
 
                    --// Airshot
                    args[3] = Plr.Character.LeftFoot.Position+(Plr.Character.LeftFoot.Velocity*PredictionValue)
 
                else
                    args[3] = Plr.Character.HumanoidRootPart.Position+(Plr.Character.HumanoidRootPart.Velocity*PredictionValue)
 
                end
            else
                    args[3] = Plr.Character.HumanoidRootPart.Position+(Plr.Character.HumanoidRootPart.Velocity*PredictionValue)
            end
            ]]
            if Prediction == true then
 
            args[3] = Plr.Character[SelectedPart].Position+(Plr.Character[SelectedPart].Velocity*PredictionValue)
 
            else
 
            args[3] = Plr.Character[SelectedPart].Position
 
            end
 
            return old(unpack(args))
        end
        return old(...)
    end)
 
    game:GetService("RunService").RenderStepped:Connect(function()
        if Settings.rewrittenmain.RESOVLER == true and Plr.Character ~= nil and enabled and Settings.rewrittenmain.Enabled then
        if Settings.rewrittenmain.AIRSHOT == true and enabled and Plr.Character ~= nil then
 
            if game.Workspace.Players[Plr.Name].Humanoid:GetState() == Enum.HumanoidStateType.Freefall then -- Plr.Character:WaitForChild("Humanoid"):GetState() == Enum.HumanoidStateType.Freefall
 
                --// Airshot
 
                --// Anchor Check
 
                if Plr.Character ~= nil and Plr.Character.HumanoidRootPart.Anchored == true then
                    AnchorCount = AnchorCount + 1
                    if AnchorCount >= MaxAnchor then
                        Prediction = false
                        wait(2)
                        AnchorCount = 0;
                    end
                else
                    Prediction = true
                    AnchorCount = 0;
                end
 
                SelectedPart = "LeftFoot"
 
            else
                --// Anchor Check
 
                if Plr.Character ~= nil and Plr.Character.HumanoidRootPart.Anchored == true then
                    AnchorCount = AnchorCount + 1
                    if AnchorCount >= MaxAnchor then
                        Prediction = false
                        wait(2)
                        AnchorCount = 0;
                    end
                else
                    Prediction = true
                    AnchorCount = 0;
                end
 
                SelectedPart = "HumanoidRootPart"
 
            end
            else
 
                --// Anchor Check
 
                if Plr.Character ~= nil and Plr.Character.HumanoidRootPart.Anchored == true then
                    AnchorCount = AnchorCount + 1
                    if AnchorCount >= MaxAnchor then
                        Prediction = false
                        wait(2)
                        AnchorCount = 0;
                    end
                else
                    Prediction = true
                    AnchorCount = 0;
                end
 
                SelectedPart = "HumanoidRootPart"
            end
 
        else
                SelectedPart = "HumanoidRootPart"
        end
    end)
    end)
    
    
    
    
    
    
    
    
    
    
    aimlock:NewButton("dhm aimlock OP!!", "THIS IS FOR HOOD MODDED!!!", function()
local Settings = { AimLock = { Enabled = true, Aimlockkey = "q", Prediction = 0.1318, Aimpart = 'LowerTorso', Notifications = true }, Settings = { Thickness = 8.5, Transparency = 1, Color = Color3.fromRGB(185, 0, 185), FOV = false } } local CurrentCamera = game:GetService("Workspace").CurrentCamera local Inset = game:GetService("GuiService"):GetGuiInset().Y local RunService = game:GetService("RunService") local Mouse = game.Players.LocalPlayer:GetMouse() local LocalPlayer = game.Players.LocalPlayer local Line = Drawing.new("Line") local Circle = Drawing.new("Circle") local Plr = game.Players.LocalPlayer Mouse.KeyDown:Connect(function(KeyPressed) if KeyPressed == (Settings.AimLock.Aimlockkey) then if Settings.AimLock.Enabled == true then Settings.AimLock.Enabled = false if Settings.AimLock.Notifications == true then Plr = FindClosestPlayer() game.StarterGui:SetCore("SendNotification", { Title = "THANKS FOR USING NASA.EXE", Text = "UNLOCKED" }) end else Plr = FindClosestPlayer() Settings.AimLock.Enabled = true if Settings.AimLock.Notifications == true then game.StarterGui:SetCore("SendNotification", { Title = "THANKS FOR USING NASA.EXE", Text = "Locked On : " .. tostring(Plr.Character.Humanoid.DisplayName) }) end end end end) function FindClosestPlayer() local ClosestDistance, ClosestPlayer = math.huge, nil; for _, Player in next, game:GetService("Players"):GetPlayers() do if Player ~= LocalPlayer then local Character = Player.Character if Character and Character.Humanoid.Health > 1 then local Position, IsVisibleOnViewPort = CurrentCamera:WorldToViewportPoint(Character.HumanoidRootPart .Position) if IsVisibleOnViewPort then local Distance = (Vector2.new(Mouse.X, Mouse.Y) - Vector2.new(Position.X, Position.Y)).Magnitude if Distance < ClosestDistance then ClosestPlayer = Player ClosestDistance = Distance end end end end end return ClosestPlayer, ClosestDistance end RunService.Heartbeat:connect(function() if Settings.AimLock.Enabled == true then local Vector = CurrentCamera:WorldToViewportPoint(Plr.Character[Settings.AimLock.Aimpart].Position + (Plr.Character[Settings.AimLock.Aimpart].Velocity * Settings.AimLock.Prediction)) Line.Color = Settings.Settings.Color Line.Transparency = Settings.Settings .Transparency Line.Thickness = Settings.Settings .Thickness Line.From = Vector2.new(Mouse.X, Mouse.Y + Inset) Line.To = Vector2.new(Vector.X, Vector.Y) Line.Visible = true Circle.Position = Vector2.new(Mouse.X, Mouse.Y + Inset) Circle.Visible = Settings.Settings.FOV Circle.Thickness = 15.5 Circle.Thickness = 15 Circle.Radius = 450 Circle.Color = Settings.Settings.Color elseif Settings.AimLock.FOV == true then Circle.Visible = true else Circle.Visible = false Line.Visible = false end end) local mt = getrawmetatable(game) local old = mt.__namecall setreadonly(mt, false) mt.__namecall = newcclosure(function(...) local args = {...} if Settings.AimLock.Enabled and getnamecallmethod() == "FireServer" and args[2] == "MousePos" then args[3] = Plr.Character[Settings.AimLock.Aimpart].Position + (Plr.Character[Settings.AimLock.Aimpart].Velocity * Settings.AimLock.Prediction) return old(unpack(args)) end return old(...) end)end)
    
    
    
    
    
    
    
    
    
    
    
    dad:NewButton("walkspeed", "gives the player walkspeed!", function()
--Skid this shut as much as u want lmao
local Player = game:GetService'Players'.LocalPlayer;
local UIS = game:GetService'UserInputService';
UIS.InputBegan:connect(function(UserInput)
        if UserInput.UserInputType == Enum.UserInputType.Keyboard and UserInput.KeyCode == Enum.KeyCode.LeftShift then
            _G.Running = true
                while wait(0.005) and _G.Running == true do
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame + game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame.lookVector * 1
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame + game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame.lookVector * 1
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame + game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame.lookVector * 1
end
        end
end)
UIS.InputEnded:connect(function(UserInput)
        if UserInput.UserInputType == Enum.UserInputType.Keyboard and UserInput.KeyCode == Enum.KeyCode.LeftShift then
                _G.Running = false
        end
end)
end)





dad:NewButton("fly / keybind T", "makes the player fly :)", function()
local plr = game.Players.LocalPlayer
local mouse = plr:GetMouse()
 
		localplayer = plr
 
		if workspace:FindFirstChild("Core") then
			workspace.Core:Destroy()
		end
 
		local Core = Instance.new("Part")
		Core.Name = "Core"
		Core.Size = Vector3.new(0.05, 0.05, 0.05)
 
		spawn(function()
			Core.Parent = workspace
			local Weld = Instance.new("Weld", Core)
			Weld.Part0 = Core
			Weld.Part1 = localplayer.Character.LowerTorso
			Weld.C0 = CFrame.new(0, 0, 0)
		end)
 
		workspace:WaitForChild("Core")
 
		local torso = workspace.Core
		flying = true
		local speed=10
		local keys={a=false,d=false,w=false,s=false} 
		local e1
		local e2
		local function start()
			local pos = Instance.new("BodyPosition",torso)
			local gyro = Instance.new("BodyGyro",torso)
			pos.Name="EPIXPOS"
			pos.maxForce = Vector3.new(math.huge, math.huge, math.huge)
			pos.position = torso.Position
			gyro.maxTorque = Vector3.new(9e9, 9e9, 9e9) 
			gyro.cframe = torso.CFrame
			repeat
				wait()
				localplayer.Character.Humanoid.PlatformStand=true
				local new=gyro.cframe - gyro.cframe.p + pos.position
				if not keys.w and not keys.s and not keys.a and not keys.d then
					speed=5
				end
				if keys.w then 
					new = new + workspace.CurrentCamera.CoordinateFrame.lookVector * speed
					speed=speed+0
				end
				if keys.s then 
					new = new - workspace.CurrentCamera.CoordinateFrame.lookVector * speed
					speed=speed+0
				end
				if keys.d then 
					new = new * CFrame.new(speed,0,0)
					speed=speed+0
				end
				if keys.a then 
					new = new * CFrame.new(-speed,0,0)
					speed=speed+0
				end
				if speed>10 then
					speed=5
				end
				pos.position=new.p
				if keys.w then
					gyro.cframe = workspace.CurrentCamera.CoordinateFrame*CFrame.Angles(-math.rad(speed*0),0,0)
				elseif keys.s then
					gyro.cframe = workspace.CurrentCamera.CoordinateFrame*CFrame.Angles(math.rad(speed*0),0,0)
				else
					gyro.cframe = workspace.CurrentCamera.CoordinateFrame
				end
			until flying == false
			if gyro then gyro:Destroy() end
			if pos then pos:Destroy() end
			flying=false
			localplayer.Character.Humanoid.PlatformStand=false
			speed=10
		end
		e1=mouse.KeyDown:connect(function(key)
			if not torso or not torso.Parent then flying=false e1:disconnect() e2:disconnect() return end
			if key=="w" then
				keys.w=true
			elseif key=="s" then
				keys.s=true
			elseif key=="a" then
				keys.a=true
			elseif key=="d" then
				keys.d=true
			elseif key=="t" then
				if flying==true then
					flying=false
				else
					flying=true
					start()
				end
			end
		end)
		e2=mouse.KeyUp:connect(function(key)
			if key=="w" then
				keys.w=false
			elseif key=="s" then
				keys.s=false
			elseif key=="a" then
				keys.a=false
			elseif key=="d" then
				keys.d=false
			end
		end)
		start()
		end)
		
		
		
		
		dad:NewButton("inf jump", "spam spacebar to jump ", function()
local Player = game:GetService'Players'.LocalPlayer;
local UIS = game:GetService'UserInputService';
 
_G.JumpHeight = 50;
 
function Action(Object, Function) if Object ~= nil then Function(Object); end end
 
UIS.InputBegan:connect(function(UserInput)
    if UserInput.UserInputType == Enum.UserInputType.Keyboard and UserInput.KeyCode == Enum.KeyCode.Space then
        Action(Player.Character.Humanoid, function(self)
            if self:GetState() == Enum.HumanoidStateType.Jumping or self:GetState() == Enum.HumanoidStateType.Freefall then
                Action(self.Parent.HumanoidRootPart, function(self)
                    self.Velocity = Vector3.new(0, _G.JumpHeight, 0);
                end)
            end
        end)
    end
end)
end)




easy:NewButton("Ambient", "MAKES THE GAME HAVE COLOR FOR RAGE MODE", function()
if not game:IsLoaded() then
	game.Loaded:Wait()
end
wait()

local executor = syn and "Synapse X" or KRNL_LOADED and "Krnl" or getexecutorname and getexecutorname() == "ScriptWare" or is_sirhurt_closure and "Sirhurt" or pebc_execute and "ProtoSmasher" or secure_load and "Sentinel" or SONA_LOADED and "Sona" or "Unknown Exploit"

--// instances
local cc = Instance.new("ColorCorrectionEffect")
local lighting = game:GetService("Lighting")
local sbox = Instance.new("Sky")
--// hd killer
local ihateu = {"DepthOfFieldEffect", "SunRaysEffect", "BloomEffect", "BlurEffect", "ColorCorrectionEffect", "Atmosphere"}
for i, v in pairs(lighting:GetChildren()) do
    for index, value in ipairs(ihateu) do
    	if v:IsA(value) then
    	   v:Destroy() 
    	end
    end
end
--// setup
cc.Parent = game.Lighting
cc.Saturation = -0.1
cc.Contrast = -0.1
lighting.GlobalShadows = false

if not executor == "ScriptWare" then
	setscriptable(lighting, "Technology", true) lighting.Technology = Enum.Technology.Compatibility
end
sethiddenproperty(lighting, "Technology", Enum.Technology.Compatibility) 

settings().Rendering.QualityLevel = 4

sbox.Parent = lighting
sbox.SkyboxBk = "http://www.roblox.com/asset/?id=271042516"
sbox.SkyboxDn = "http://www.roblox.com/asset/?id=271077243"
sbox.SkyboxFt = "http://www.roblox.com/asset/?id=271042556"
sbox.SkyboxLf = "http://www.roblox.com/asset/?id=271042310"
sbox.SkyboxRt = "http://www.roblox.com/asset/?id=271042467"
sbox.SkyboxUp = "http://www.roblox.com/asset/?id=271077958"
lighting.Ambient = Color3.fromRGB(185, 0, 185)
lighting.FogColor = Color3.fromRGB(185, 0, 185)
lighting.ClockTime = 2
lighting.FogEnd = 1000
for i, v in pairs(game:GetService("Workspace"):GetChildren()) do
    if v:IsA("BasePart") and v.Material == Enum.Material.Neon then
        v.Transparency = 0.1
        v.Color = Color3.fromRGB(185, 0, 185)
    end
end
end)






easy:NewButton("anit lock - keybind{V}", "ButtonInfo", function()
local Toggled = true
local KeyCode = 'v'
local hip = 2.00
local val = -55





function AA()
    local oldVelocity = game.Players.LocalPlayer.Character.HumanoidRootPart.Velocity
    game.Players.LocalPlayer.Character.HumanoidRootPart.Velocity = Vector3.new(oldVelocity.X, val, oldVelocity.Z)
    game.Players.LocalPlayer.Character.HumanoidRootPart.Velocity = Vector3.new(oldVelocity.X, oldVelocity.Y, oldVelocity.Z)
    game.Players.LocalPlayer.Character.HumanoidRootPart.Velocity = Vector3.new(oldVelocity.X, val, oldVelocity.Z)
    game.Players.LocalPlayer.Character.Humanoid.HipHeight = hip
end

game:GetService('UserInputService').InputBegan:Connect(function(Key)
    if Key.KeyCode == Enum.KeyCode[KeyCode:upper()] and not game:GetService('UserInputService'):GetFocusedTextBox() then
        if Toggled then
            Toggled = false
            game.Players.LocalPlayer.Character.Humanoid.HipHeight = hip

        elseif not Toggled then
            Toggled = true

            while Toggled do
                AA()
                task.wait()
            end
        end
    end
end)
end)









player:NewButton("headless/korblox -non FE", "makes you have headless and korblox", function()
local Main = Instance.new("ScreenGui")
local MainFrame = Instance.new("Frame")
local UICorner = Instance.new("UICorner")
local Korblox = Instance.new("TextButton")
local UICorner_2 = Instance.new("UICorner")
local Headless = Instance.new("TextButton")
local UICorner_3 = Instance.new("UICorner")

--Properties:

Main.Name = "Main"
Main.Parent = game.CoreGui
Main.ZIndexBehavior = Enum.ZIndexBehavior.Sibling

MainFrame.Name = "MainFrame"
MainFrame.Parent = Main
MainFrame.BackgroundColor3 = Color3.fromRGB(164, 12, 164)
MainFrame.Position = UDim2.new(0.0751346573, 0, 0.743494451, 0)
MainFrame.Size = UDim2.new(0, 163, 0, 109)
MainFrame.Active = true
MainFrame.Draggable = true

UICorner.Parent = MainFrame

Korblox.Name = "KORBLOX!"
Korblox.Parent = MainFrame
Korblox.BackgroundColor3 = Color3.fromRGB(285, 0, 285)
Korblox.Position = UDim2.new(0.0858895704, 0, 0.0825688019, 0)
Korblox.Size = UDim2.new(0, 134, 0, 42)
Korblox.Font = Enum.Font.GothamBlack
Korblox.Text = "KORBLOX!"
Korblox.TextColor3 = Color3.fromRGB(185, 185, 185)
Korblox.TextSize = 23.000
Korblox.TextWrapped = true
Korblox.MouseButton1Click:Connect(function()
	local ply = game.Players.LocalPlayer
	local chr = ply.Character
	chr.RightLowerLeg.MeshId = "902942093"
	chr.RightLowerLeg.Transparency = "1"
	chr.RightUpperLeg.MeshId = "http://www.roblox.com/asset/?id=902942096"
	chr.RightUpperLeg.TextureID = "http://roblox.com/asset/?id=902843398"
	chr.RightFoot.MeshId = "902942089"
	chr.RightFoot.Transparency = "1"
end)

UICorner_2.Parent = Korblox

Headless.Name = "HEADLESS!"
Headless.Parent = MainFrame
Headless.BackgroundColor3 = Color3.fromRGB(285, 0, 285)
Headless.Position = UDim2.new(0.0858895704, 0, 0.522935808, 0)
Headless.Size = UDim2.new(0, 134, 0, 42)
Headless.Font = Enum.Font.GothamBlack
Headless.Text = "HEADLESS!"
Headless.TextColor3 = Color3.fromRGB(185, 185, 185)
Headless.TextSize = 23.000
Headless.TextWrapped = true
Headless.MouseButton1Click:Connect(function()
	game.Players.LocalPlayer.Character.Head.Transparency = 1
	game.Players.LocalPlayer.Character.Head.Transparency = 1
	for i,v in pairs(game.Players.LocalPlayer.Character.Head:GetChildren()) do
		if (v:IsA("Decal")) then
			v.Transparency = 1
		end
	end
end)

UICorner_3.Parent = Headless
end)




player:NewButton("force/reset ", "when you on the ground press it and it will make you fall throiugh the map!", function()
-- made by tturley23
 
--[[ Thank you for choosing this noclip script!
    
    The noclip will be enabled automatically, please enter the values below - mode, hitpart according the the instructions.
    Want to disable the noclip? Type "noclip disable" in chat.
    Want to re-enable the noclip? Type "noclip enable" in chat.
 
    If you are going to share this etc please give credit :)
    
--]]
 
local plr = game.Players.LocalPlayer -- Player
 
local mode = "tempnoclip"
 
--[[ MODE:
    
    The mode is what mode the noclip script is on. You must enter one of these values. CASE SENSITIVE.
    
    tempnoclip - Will allow you to walk through touched objects for 3 seconds before making them solid again. While you can walk through them they are semi-transparent
    destroy - Will permanently destroy any touched objects
    noclip - Will Allow you to walk through any touched object permanently
    invis - Will make any touched object invisible.
    
--]]
 
local HitPart = ""
 
--[[ HITPART
    
    This Value is what part of your character will activate the noclip mode. You must enter one of the following values. CASE SENSITIVE.
    BE AWARE OF WETHER YOU ARE PLAYING R15 OR R6 ANIMATED GAMES.
    
    Head - R15/R6
    Torso - R6
    HumanoidRootPart - R15 Torso
    LeftLeg - R15
    LeftFoot - R15
    RightLeg - R15
    RightFoot - R15
    
--]]
 

 
 
local enabled = true
 
if (plr ~= nil) then
    
    print("Activating NoClip...")
    enabled = true
    
            
    if (mode ~= "TEMPNOCLIP" and mode ~= "tempnoclip" and mode ~= "DESTROY" and mode ~= "destroy" and mode ~= "NOCLIP" and mode ~= "noclip" and mode ~= "INVIS" and mode ~= "invis") then
        print ("Invalid mode! Setting to noclip by default!")
        mode = "noclip"
    else
        print("Succesfully Changed Mode! Mode: " ..mode)        
    end
    
    if (HitPart ~= "Head" and HitPart ~= "Torso" and HitPart ~= "HumanoidRootPart" and HitPart ~= "LeftHand" and HitPart ~= "LeftFoot" and HitPart ~= "RightFoot" and HitPart ~= "RightHand") then
        print ("Invalid Hit Object! Setting to head by default!")
        HitPart = "Head"
    else
        print ("Successfully Changed Hit Object! Object: " ..HitPart)
    end
    
    print("Noclip succesfully activated!")
    
end
 
plr.Chatted:connect(function(msg)
    
    if (msg == string.lower("noclip disable")) then
        print("Disabling noclip")
        enabled = false     
    end
    
    if (msg == string.lower("noclip enable")) then
        print("Enabling noclip")
        enabled = true
    end
end)
 
plr.Character[HitPart].Touched:connect(function(obj)
    
    if(obj:IsA("MeshPart") or obj:IsA("Part") or obj:IsA("WedgePart") or obj:IsA("UnionOperation")) then
        if(obj.CanCollide == true) then
            
            if (mode == "TEMPNOCLIP" or mode == "tempnoclip") then  
                
                if enabled == true then             
                    local ogtransp = obj.Transparency
                    
                    obj.CanCollide = false
                    obj.Transparency = 0.5
                    
                    wait(4)
                    
                    obj.CanCollide = true
                    obj.Transparency = ogtransp
                end
                
            end
            
            
            if (mode == "DESTROY" or mode == "destroy") then
                if enabled == true then
                    obj:remove()
                end
            end
            
            if (mode == "NOCLIP" or mode == "noclip") then
                if enabled == true then
                    obj.CanCollide = false
                end
            end
            
            if (mode == "INVIS" or mode == "invis") then
                if enabled == true then
                    obj.Transparency = 0.8
                    else
                end
            end
            
        end
        
    else
        print("Not Available obj")
    end
    
end)
end)


dad:NewButton("Animation Pack", "gives you the animation pack", function()
repeat
    wait()
until game:IsLoaded() and game.Players.LocalPlayer.Character:FindFirstChild("FULLY_LOADED_CHAR") and game.Players.LocalPlayer.PlayerGui.MainScreenGui:FindFirstChild("AnimationPack")

if game.ReplicatedStorage.ClientAnimations:FindFirstChild("Lean") then
    game.ReplicatedStorage.ClientAnimations.Lean:Destroy()
end

if game.ReplicatedStorage.ClientAnimations:FindFirstChild("Lay") then
    game.ReplicatedStorage.ClientAnimations.Lay:Destroy()
end

if game.ReplicatedStorage.ClientAnimations:FindFirstChild("Dance1") then
    game.ReplicatedStorage.ClientAnimations.Dance1:Destroy()
end

if game.ReplicatedStorage.ClientAnimations:FindFirstChild("Dance2") then
    game.ReplicatedStorage.ClientAnimations.Dance2:Destroy()
end

if game.ReplicatedStorage.ClientAnimations:FindFirstChild("Greet") then
    game.ReplicatedStorage.ClientAnimations.Greet:Destroy()
end

if game.ReplicatedStorage.ClientAnimations:FindFirstChild("Chest Pump") then
    game.ReplicatedStorage.ClientAnimations["Chest Pump"]:Destroy()
end

if game.ReplicatedStorage.ClientAnimations:FindFirstChild("Praying") then
    game.ReplicatedStorage.ClientAnimations.Praying:Destroy()
end

local Animations = game.ReplicatedStorage.ClientAnimations

local LeanAnimation = Instance.new("Animation", Animations)
LeanAnimation.Name = "Lean"
LeanAnimation.AnimationId = "rbxassetid://3152375249"

local LayAnimation = Instance.new("Animation", Animations)
LayAnimation.Name = "Lay"
LayAnimation.AnimationId = "rbxassetid://3152378852"

local Dance1Animation = Instance.new("Animation", Animations)
Dance1Animation.Name = "Dance1"
Dance1Animation.AnimationId = "rbxassetid://3189773368"

local Dance2Animation = Instance.new("Animation", Animations)
Dance2Animation.Name = "Dance2"
Dance2Animation.AnimationId = "rbxassetid://3189776546"

local GreetAnimation = Instance.new("Animation", Animations)
GreetAnimation.Name = "Greet"
GreetAnimation.AnimationId = "rbxassetid://3189777795"

local ChestPumpAnimation = Instance.new("Animation", Animations)
ChestPumpAnimation.Name = "Chest Pump"
ChestPumpAnimation.AnimationId = "rbxassetid://3189779152"

local PrayingAnimation = Instance.new("Animation", Animations)
PrayingAnimation.Name = "Praying"
PrayingAnimation.AnimationId = "rbxassetid://3487719500"

function AnimationPack(Character)
    Character:WaitForChild'Humanoid'
    repeat
        wait()
    until game.Players.LocalPlayer.Character:FindFirstChild("FULLY_LOADED_CHAR") and game.Players.LocalPlayer.PlayerGui.MainScreenGui:FindFirstChild("AnimationPack")

    local AnimationPack = game:GetService("Players").LocalPlayer.PlayerGui.MainScreenGui.AnimationPack
    local ScrollingFrame = AnimationPack.ScrollingFrame
    local CloseButton = AnimationPack.CloseButton

    local Lean = game:GetService("Players").LocalPlayer.Character.Humanoid:LoadAnimation(LeanAnimation)

    local Lay = game:GetService("Players").LocalPlayer.Character.Humanoid:LoadAnimation(LayAnimation)

    local Dance1 = game:GetService("Players").LocalPlayer.Character.Humanoid:LoadAnimation(Dance1Animation)

    local Dance2 = game:GetService("Players").LocalPlayer.Character.Humanoid:LoadAnimation(Dance2Animation)

    local Greet = game:GetService("Players").LocalPlayer.Character.Humanoid:LoadAnimation(GreetAnimation)

    local ChestPump = game:GetService("Players").LocalPlayer.Character.Humanoid:LoadAnimation(ChestPumpAnimation)

    local Praying = game:GetService("Players").LocalPlayer.Character.Humanoid:LoadAnimation(PrayingAnimation)

    AnimationPack.Visible = true

    AnimationPack.ScrollingFrame.UIListLayout.SortOrder = Enum.SortOrder.LayoutOrder

    for i,v in pairs(ScrollingFrame:GetChildren()) do
        if v.Name == "TextButton" then
            if v.Text == "Lean" then
                v.Name = "LeanButton"
            end
        end
    end

    for i,v in pairs(ScrollingFrame:GetChildren()) do
        if v.Name == "TextButton" then
            if v.Text == "Lay" then
                v.Name = "LayButton"
            end
        end
    end

    for i,v in pairs(ScrollingFrame:GetChildren()) do
        if v.Name == "TextButton" then
            if v.Text == "Dance1" then
                v.Name = "Dance1Button"
            end
        end
    end

    for i,v in pairs(ScrollingFrame:GetChildren()) do
        if v.Name == "TextButton" then
            if v.Text == "Dance2" then
                v.Name = "Dance2Button"
            end
        end
    end

    for i,v in pairs(ScrollingFrame:GetChildren()) do
        if v.Name == "TextButton" then
            if v.Text == "Greet" then
                v.Name = "GreetButton"
            end
        end
    end

    for i,v in pairs(ScrollingFrame:GetChildren()) do
        if v.Name == "TextButton" then
            if v.Text == "Chest Pump" then
                v.Name = "ChestPumpButton"
            end
        end
    end

    for i,v in pairs(ScrollingFrame:GetChildren()) do
        if v.Name == "TextButton" then
            if v.Text == "Praying" then
                v.Name = "PrayingButton"
            end
        end
    end

    function Stop()
        Lean:Stop()
        Lay:Stop()
        Dance1:Stop()
        Dance2:Stop()
        Greet:Stop()
        ChestPump:Stop()
        Praying:Stop()
    end

    local LeanTextButton = ScrollingFrame.LeanButton
    local LayTextButton = ScrollingFrame.LayButton
    local Dance1TextButton = ScrollingFrame.Dance1Button
    local Dance2TextButton = ScrollingFrame.Dance2Button
    local GreetTextButton = ScrollingFrame.GreetButton
    local ChestPumpTextButton = ScrollingFrame.ChestPumpButton
    local PrayingTextButton = ScrollingFrame.PrayingButton

    AnimationPack.MouseButton1Click:Connect(function()
        if ScrollingFrame.Visible == false then
            ScrollingFrame.Visible = true
            CloseButton.Visible = true
        end
    end)
    CloseButton.MouseButton1Click:Connect(function()
        if ScrollingFrame.Visible == true then
            ScrollingFrame.Visible = false
            CloseButton.Visible = false
        end
    end)
    LeanTextButton.MouseButton1Click:Connect(function()
        Stop()
        Lean:Play()
    end)
    LayTextButton.MouseButton1Click:Connect(function()
        Stop()
        Lay:Play()
    end)
    Dance1TextButton.MouseButton1Click:Connect(function()
        Stop()
        Dance1:Play()
    end)
    Dance2TextButton.MouseButton1Click:Connect(function()
        Stop()
        Dance2:Play()
    end)
    GreetTextButton.MouseButton1Click:Connect(function()
        Stop()
        Greet:Play()
    end)
    ChestPumpTextButton.MouseButton1Click:Connect(function()
        Stop()
        ChestPump:Play()
    end)
    PrayingTextButton.MouseButton1Click:Connect(function()
        Stop()
        Praying:Play()
    end)

    game:GetService("Players").LocalPlayer.Character.Humanoid.Running:Connect(function()
        Stop()
    end)

    game:GetService("Players").LocalPlayer.CharacterAdded:Connect(function()
        Stop()
    end)
end
AnimationPack(game.Players.LocalPlayer.Character)
game.Players.LocalPlayer.CharacterAdded:Connect(AnimationPack)
end)

easy:NewButton("cash aura", "makes you auto pickup cash in da hood!", function()
while wait() do


local function getMoneyAroundMe() 
    for i, money in ipairs(game.Workspace.Ignored.Drop:GetChildren()) do
        if money.Name == "MoneyDrop" and (money.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).magnitude <= 20 then
            fireclickdetector(money.ClickDetector)
        end  
    end
end

 getMoneyAroundMe()
end
end)


dad:NewButton("cframe-fly key{X}", "cframe fly means no clipping while flying!", function()
local Settings = {
	
	Speed = 15,
	SprintSpeed = 15,
	ToggleKey = Enum.KeyCode.X,
	SprintKey = Enum.KeyCode.LeftControl,
	
	ForwardKey = Enum.KeyCode.W,
	LeftKey = Enum.KeyCode.A,
	BackwardKey = Enum.KeyCode.S,
	RightKey = Enum.KeyCode.D,

	
}

local Screen = Instance.new("ScreenGui",game.CoreGui)
local Distance = Instance.new("TextLabel",Screen)
Distance.BackgroundTransparency = 1
Distance.Size = UDim2.new(0,10,0,10)
Distance.ZIndex = 2
Distance.Text = "0"
Distance.TextStrokeTransparency = .5
Distance.TextSize = 20
Distance.TextStrokeColor3 = Color3.fromRGB(33, 33, 33)
Distance.Font = Enum.Font.Gotham
Distance.TextColor3 = Color3.new(1,1,1)
Distance.TextXAlignment = Enum.TextXAlignment.Left
Distance.TextYAlignment = Enum.TextYAlignment.Top


local Mouse = game.Players.LocalPlayer:GetMouse()
local Direction = Vector3.new(0,0,0)
local InterpolatedDir = Direction
local Tilt = 0
local InterpolatedTilt = Tilt
local RunService = game:GetService("RunService")
local Toggled = false
local Sprinting = false
local CameraPos = game.Workspace.CurrentCamera.CFrame.Position

pcall(function()
	game.Players.LocalPlayer.DevCameraOcclusionMode = Enum.DevCameraOcclusionMode.Invisicam	
end)

function Lerp(a, b, t)
    return a + (b - a) * t
end

local LastPos = nil

function KeyHandler(actionName, userInputState)
	if true and game.Players.LocalPlayer.Character and game.Players.LocalPlayer.Character:FindFirstChild("HumanoidRootPart") then
		if actionName == "Toggle" and userInputState == Enum.UserInputState.Begin then
			Toggled = not Toggled
			if Toggled then
				LastPos = game.Players.LocalPlayer.Character.HumanoidRootPart.Position
				--game.Players.LocalPlayer.Character.HumanoidRootPart.Anchored = true
				game.Players.LocalPlayer.Character.Humanoid.PlatformStand = true 
			else
				LastPos = nil
				game.Players.LocalPlayer.Character.Humanoid.PlatformStand = false
				--game.Players.LocalPlayer.Character.HumanoidRootPart.Anchored = false
			end
		elseif actionName == "Forward" then
			Tilt = userInputState == Enum.UserInputState.Begin and -20 or 0
			Direction = Vector3.new(Direction.x,Direction.y,userInputState == Enum.UserInputState.Begin and -1 or 0)
		elseif actionName == "Left" then
			Direction = Vector3.new(userInputState == Enum.UserInputState.Begin and -1 or 0,Direction.y,Direction.z)
		elseif actionName == "Backward" then
			Tilt = userInputState == Enum.UserInputState.Begin and 20 or 0
			Direction = Vector3.new(Direction.x,Direction.y,userInputState == Enum.UserInputState.Begin and 1 or 0)
		elseif actionName == "Right" then
			Direction = Vector3.new(userInputState == Enum.UserInputState.Begin and 1 or 0,Direction.y,Direction.z)
		elseif actionName == "Up" then
			Direction = Vector3.new(Direction.x,userInputState == Enum.UserInputState.Begin and 1 or 0,Direction.z)
		elseif actionName == "Down" then
			Direction = Vector3.new(Direction.x,userInputState == Enum.UserInputState.Begin and -1 or 0,Direction.z)
		elseif actionName == "Sprint" then
			Sprinting = userInputState == Enum.UserInputState.Begin
		end
	end
end



game:GetService("UserInputService").InputBegan:connect(function(inputObject, gameProcessedEvent)
	
	if inputObject.KeyCode == Settings.ToggleKey then
		KeyHandler("Toggle", Enum.UserInputState.Begin, inputObject)
	elseif inputObject.KeyCode == Settings.ForwardKey then
		KeyHandler("Forward", Enum.UserInputState.Begin, inputObject)
	elseif inputObject.KeyCode == Settings.LeftKey then
		KeyHandler("Left", Enum.UserInputState.Begin, inputObject)
	elseif inputObject.KeyCode == Settings.BackwardKey then
		KeyHandler("Backward", Enum.UserInputState.Begin, inputObject)
	elseif inputObject.KeyCode == Settings.RightKey then
		KeyHandler("Right", Enum.UserInputState.Begin, inputObject)
	elseif inputObject.KeyCode == Settings.UpKey then	
		KeyHandler("Up", Enum.UserInputState.Begin, inputObject)
	elseif inputObject.KeyCode == Settings.DownKey then
		KeyHandler("Down", Enum.UserInputState.Begin, inputObject)
	elseif inputObject.KeyCode == Settings.SprintKey then
		KeyHandler("Sprint", Enum.UserInputState.Begin, inputObject)
	end
	
	
end)


game:GetService("UserInputService").InputEnded:connect(function(inputObject, gameProcessedEvent)
	
	if inputObject.KeyCode == Settings.ToggleKey then
		KeyHandler("Toggle", Enum.UserInputState.End, inputObject)
	elseif inputObject.KeyCode == Settings.ForwardKey then
		KeyHandler("Forward", Enum.UserInputState.End, inputObject)
	elseif inputObject.KeyCode == Settings.LeftKey then
		KeyHandler("Left", Enum.UserInputState.End, inputObject)
	elseif inputObject.KeyCode == Settings.BackwardKey then
		KeyHandler("Backward", Enum.UserInputState.End, inputObject)
	elseif inputObject.KeyCode == Settings.RightKey then
		KeyHandler("Right", Enum.UserInputState.End, inputObject)
	elseif inputObject.KeyCode == Settings.UpKey then	
		KeyHandler("Up", Enum.UserInputState.End, inputObject)
	elseif inputObject.KeyCode == Settings.DownKey then
		KeyHandler("Down", Enum.UserInputState.End, inputObject)
	elseif inputObject.KeyCode == Settings.SprintKey then
		KeyHandler("Sprint", Enum.UserInputState.End, inputObject)
	end
	
	
end)


RunService.RenderStepped:Connect(function()
	if Toggled and game.Players.LocalPlayer.Character and game.Players.LocalPlayer.Character:FindFirstChild("HumanoidRootPart")  then
		for i,v in pairs(game.Players.LocalPlayer.Character:GetDescendants()) do
			if v:IsA("BasePart") then
				v.Velocity = Vector3.new(0,0,0)
			end
		end
		local RootPart = game.Players.LocalPlayer.Character.HumanoidRootPart
		if LastPos then
			Distance.Text = math.floor((LastPos-RootPart.Position).Magnitude+.5)
			if (LastPos-RootPart.Position).Magnitude >= 350 then
				Distance.TextColor3 = Color3.new(1,0,0)
			else
				Distance.TextColor3 = Color3.new(1,1,1)	
			end
		else
			Distance.TextColor3 = Color3.new(1,1,1)
			Distance.Text = 0
		end
		InterpolatedDir = InterpolatedDir:Lerp((Direction * (Sprinting and Settings.SprintSpeed or Settings.Speed)),.2)
		InterpolatedTilt = Lerp(InterpolatedTilt ,Tilt* (Sprinting and 2 or 1),Tilt == 0 and .2 or .1)
		RootPart.CFrame = RootPart.CFrame:Lerp(CFrame.new(RootPart.Position,RootPart.Position + Mouse.UnitRay.Direction) * CFrame.Angles(0,math.rad(00),0) * CFrame.new(InterpolatedDir)  * CFrame.Angles(math.rad(InterpolatedTilt),0,0),.2)
	else
		Distance.TextColor3 = Color3.new(1,1,1)
		Distance.Text = 0
	end	
end)
 
end)



esp:NewButton("ESP - DROPS FPS BY A LITTLE", "makes you see all players!!!", function()
local OxJJCEO11=('Identitys Lua, https://discord.gg/GnzUUPd3FQ')return(function(Ox1UC1EJ2,OxCLAJE13,...)local OxCLAJE13=getfenv or function(...)return(_ENV)end;local OxE2UEJL4,OxE2UEJL4,OxLDD2HV5={},"",(OxCLAJE13())local OxCOL2AC6=((OxLDD2HV5[""..Ox1UC1EJ2[0x17E3EE27].."\105"..Ox1UC1EJ2[0x1FA51563]..Ox1UC1EJ2[0x14AA09D6].."\50"])or(OxLDD2HV5["\98\105"..Ox1UC1EJ2[0x1FA51563]])or({}))local OxJCDONH7=(((OxCOL2AC6)and(OxCOL2AC6["\98"..Ox1UC1EJ2['ch2PM7'].."\111\114"]))or(function(OxJJCEO11,Ox1UC1EJ2)local OxCLAJE13,OxE2UEJL4=0x1,0;while((OxJJCEO11>0)and(Ox1UC1EJ2>0))do local OxLDD2HV5,OxCOL2AC6=OxJJCEO11%0x2,Ox1UC1EJ2%0x2;if OxLDD2HV5~=OxCOL2AC6 then OxE2UEJL4=OxE2UEJL4+OxCLAJE13 end;OxJJCEO11,Ox1UC1EJ2,OxCLAJE13=(OxJJCEO11-OxLDD2HV5)/0x2,(Ox1UC1EJ2-OxCOL2AC6)/0x2,OxCLAJE13*0x2 end;if OxJJCEO11<Ox1UC1EJ2 then OxJJCEO11=Ox1UC1EJ2 end;while OxJJCEO11>0 do local Ox1UC1EJ2=OxJJCEO11%0x2;if Ox1UC1EJ2>0 then OxE2UEJL4=OxE2UEJL4+OxCLAJE13 end;OxJJCEO11,OxCLAJE13=(OxJJCEO11-Ox1UC1EJ2)/0x2,OxCLAJE13*0x2 end;return(OxE2UEJL4)end))local OxBUDJ2V8=(0x2^0x20)local OxBUDJ2V8=(OxBUDJ2V8-0x1)local Ox1O2VOB9,OxHBNUCE10,OxSULBCD11;local Ox2NJSBL12=(OxE2UEJL4[""..Ox1UC1EJ2[0x20304762]..Ox1UC1EJ2[0xF6FF715]..Ox1UC1EJ2.o5ITi..Ox1UC1EJ2[0x17E3EE27]])local OxNOFS2113=(OxE2UEJL4["\98"..Ox1UC1EJ2.dJE8e.."\116\101"])local OxSAVNLC14=(OxE2UEJL4["\109\97"..Ox1UC1EJ2[0x1FA51563]..Ox1UC1EJ2[0x28733ADE].."\104"])local OxH22UAV15=(OxE2UEJL4[""..Ox1UC1EJ2[0x28733ADE].."\104"..Ox1UC1EJ2[0x630BB2E].."\114"])local OxE2UEJL4=(OxE2UEJL4["\115\117\98"])local OxONHHAN16=(OxLDD2HV5[""..Ox1UC1EJ2[0x1FA51563].."\121"..Ox1UC1EJ2[0x28552064].."\101"])local OxONHHAN16=(OxLDD2HV5["\112\97\105\114\115"])local OxFDEESB17=(OxLDD2HV5[""..Ox1UC1EJ2[0xF6FF715].."\101"..Ox1UC1EJ2[0x15C3D2F6]..Ox1UC1EJ2["Vot08VN"]..Ox1UC1EJ2[0x28733ADE].."\116"])local OxVVBBHF18=((OxLDD2HV5["\109\97\116"..Ox1UC1EJ2[0x23A5B0F0]][""..Ox1UC1EJ2[0x15C3D2F6]..Ox1UC1EJ2['aPpIZlBvh'].."\101"..Ox1UC1EJ2["ch2PM7"].."\112"])or(function(OxJJCEO11,Ox1UC1EJ2,...)return((OxJJCEO11*0x2)^Ox1UC1EJ2)end))local OxCHEEAN19=(OxLDD2HV5["\114\97"..Ox1UC1EJ2[0x1660770].."\115"..Ox1UC1EJ2.Vot08VN.."\116"])local OxCHEEAN19=(OxLDD2HV5[""..Ox1UC1EJ2[0xF6FF715]..Ox1UC1EJ2['Vot08VN']..Ox1UC1EJ2[0x1FA51563].."\109"..Ox1UC1EJ2["Vot08VN"]..Ox1UC1EJ2[0x1FA51563].."\97\116\97"..Ox1UC1EJ2[0x17E3EE27]..Ox1UC1EJ2[0x15C3D2F6]..Ox1UC1EJ2['Vot08VN']])local function OxF2SBFV20(...)local OxJJCEO11,OxJJCEO11=...local OxJJCEO11=OxSAVNLC14(OxJJCEO11,':(%d*):')return OxJJCEO11 end;local OxSAVNLC14=(OxLDD2HV5["\112"..Ox1UC1EJ2[0x28733ADE]..Ox1UC1EJ2[0x630BB2E]..Ox1UC1EJ2[0x15C3D2F6].."\108"])local OxSAVNLC14=((OxLDD2HV5["\117\110"..Ox1UC1EJ2[0x28552064].."\97"..Ox1UC1EJ2[0x28733ADE].."\107"])or(OxLDD2HV5[""..Ox1UC1EJ2[0x1FA51563]..Ox1UC1EJ2[0x630BB2E]..Ox1UC1EJ2[0x17E3EE27]..Ox1UC1EJ2[0x15C3D2F6].."\101"][""..Ox1UC1EJ2.o5ITi..Ox1UC1EJ2[0x1B445014].."\112"..Ox1UC1EJ2[0x630BB2E].."\99"..Ox1UC1EJ2[0x1FCEE392]]))local OxF2SBFV20=(OxLDD2HV5["\116\111\110"..Ox1UC1EJ2["o5ITi"]..Ox1UC1EJ2[0x22902A95].."\98\101"..Ox1UC1EJ2[0x36FFAC03]])local OxCFL11U21=(OxLDD2HV5["\109"..Ox1UC1EJ2[0x630BB2E]..Ox1UC1EJ2[0x1FA51563].."\104"]["\102\108\111\111"..Ox1UC1EJ2[0x36FFAC03]])local OxFEL21F22=(OxCOL2AC6[""..Ox1UC1EJ2[0x17E3EE27].."\111"..Ox1UC1EJ2[0x36FFAC03]])or(function(OxJJCEO11,Ox1UC1EJ2,...)return(OxBUDJ2V8-OxSULBCD11(OxBUDJ2V8-OxJJCEO11,OxBUDJ2V8-Ox1UC1EJ2))end)OxSULBCD11=(OxCOL2AC6["\98\97"..Ox1UC1EJ2[0x1B445014]..Ox1UC1EJ2['aPpIZlBvh']])or(function(OxJJCEO11,Ox1UC1EJ2,...)return(((OxJJCEO11+Ox1UC1EJ2)-OxJCDONH7(OxJJCEO11,Ox1UC1EJ2))/0x2)end)local OxBUDJ2V8=(OxCOL2AC6[""..Ox1UC1EJ2[0x17E3EE27].."\110"..Ox1UC1EJ2.fToXmpErQ.."\116"])or(function(OxJJCEO11,...)return(OxBUDJ2V8-OxJJCEO11)end)OxHBNUCE10=((OxCOL2AC6["\114\115"..Ox1UC1EJ2[0x23A5B0F0].."\105"..Ox1UC1EJ2['ofLQcv00L'].."\116"])or(function(OxJJCEO11,Ox1UC1EJ2,...)if(Ox1UC1EJ2<0)then return(Ox1O2VOB9(OxJJCEO11,-(Ox1UC1EJ2)))end;return(OxCFL11U21(OxJJCEO11%0x2^0x20/0x2^Ox1UC1EJ2))end))Ox1O2VOB9=((OxCOL2AC6["\108\115\104"..Ox1UC1EJ2[0x327E37C3].."\102\116"])or(function(OxJJCEO11,Ox1UC1EJ2,...)if(Ox1UC1EJ2<0)then return(OxHBNUCE10(OxJJCEO11,-(Ox1UC1EJ2)))end;return((OxJJCEO11*0x2^Ox1UC1EJ2)%0x2^0x20)end))if((not(OxLDD2HV5["\98\105\116"..Ox1UC1EJ2[0x14AA09D6]..Ox1UC1EJ2[0x30CDB6B8]]))and(not(OxLDD2HV5["\98\105\116"])))then OxCOL2AC6[""..Ox1UC1EJ2[0x17E3EE27].."\120\111\114"]=OxJCDONH7;OxCOL2AC6["\114\115\104"..Ox1UC1EJ2[0x327E37C3]..Ox1UC1EJ2.ofLQcv00L..Ox1UC1EJ2[0x1FA51563]]=OxHBNUCE10;OxCOL2AC6[""..Ox1UC1EJ2[0x17E3EE27].."\111\114"]=OxFEL21F22;OxCOL2AC6[""..Ox1UC1EJ2[0x15C3D2F6]..Ox1UC1EJ2[0xF6FF715]..Ox1UC1EJ2[0x23A5B0F0]..Ox1UC1EJ2[0x327E37C3].."\102"..Ox1UC1EJ2[0x1FA51563]]=Ox1O2VOB9;OxCOL2AC6[""..Ox1UC1EJ2[0x17E3EE27]..Ox1UC1EJ2[0x1B445014]..Ox1UC1EJ2['fToXmpErQ'].."\116"]=OxBUDJ2V8;OxCOL2AC6[""..Ox1UC1EJ2[0x17E3EE27]..Ox1UC1EJ2[0x630BB2E]..Ox1UC1EJ2[0x1B445014].."\100"]=OxSULBCD11 end;local OxBUDJ2V8=(OxLDD2HV5[""..Ox1UC1EJ2[0x1FA51563]..Ox1UC1EJ2[0x630BB2E].."\98\108"..Ox1UC1EJ2['Vot08VN']][""..Ox1UC1EJ2[0x36FFAC03].."\101"..Ox1UC1EJ2[0x22902A95].."\111"..Ox1UC1EJ2[0x1702BD6B]..Ox1UC1EJ2.Vot08VN])local OxBUDJ2V8=(OxLDD2HV5["\116\97"..Ox1UC1EJ2[0x17E3EE27].."\108"..Ox1UC1EJ2["Vot08VN"]]["\105\110"..Ox1UC1EJ2[0xF6FF715].."\101"..Ox1UC1EJ2[0x36FFAC03].."\116"])local OxBUDJ2V8=(OxLDD2HV5["\116\97"..Ox1UC1EJ2[0x17E3EE27]..Ox1UC1EJ2[0x15C3D2F6].."\101"]["\99\111\110"..Ox1UC1EJ2[0x28733ADE]..Ox1UC1EJ2[0x630BB2E]..Ox1UC1EJ2[0x1FA51563]])local Ox1O2VOB9=(((OxLDD2HV5["\116"..Ox1UC1EJ2[0x630BB2E]..Ox1UC1EJ2[0x17E3EE27].."\108\101"]["\99\114"..Ox1UC1EJ2['Vot08VN'].."\97"..Ox1UC1EJ2[0x1FA51563].."\101"]))or((function(OxJJCEO11,...)return({OxSAVNLC14({},0,OxJJCEO11)})end)))OxLDD2HV5["\98\105"..Ox1UC1EJ2[0x1FA51563].."\51"..Ox1UC1EJ2[0x30CDB6B8]]=OxCOL2AC6;local Ox1UC1EJ2=(0xA8)local OxLDD2HV5=0x100;local OxCOL2AC6,OxHBNUCE10={},{}for OxJJCEO11=0,OxLDD2HV5-0x1 do local Ox1UC1EJ2=OxH22UAV15(OxJJCEO11)OxCOL2AC6[OxJJCEO11]=Ox1UC1EJ2;OxHBNUCE10[OxJJCEO11]=Ox1UC1EJ2;OxHBNUCE10[Ox1UC1EJ2]=OxJJCEO11 end;local function OxSULBCD11(OxJJCEO11)OxJJCEO11=Ox2NJSBL12(OxJJCEO11,'\73\100\101\110\76\117\97','\85\80\83')local OxCLAJE13,OxJCDONH7,Ox1O2VOB9=OxNOFS2113(OxJJCEO11,0x1,0x3)if((OxCLAJE13+OxJCDONH7+Ox1O2VOB9)~=0xF8)then Ox1UC1EJ2=Ox1UC1EJ2+0x7F;OxLDD2HV5=OxLDD2HV5+0x55 end;OxJJCEO11=OxE2UEJL4(OxJJCEO11,0x5)OxJJCEO11=Ox2NJSBL12(OxJJCEO11,"..",{["ٶ"]="0";["ٷ"]="1";["ٸ"]="2";["ٺ"]="3";["ٻ"]="4";["ټ"]="5";["ٽ"]="6";["پ"]="7";["ٿ"]="8";["ڀ"]="9";["ځ"]="A";["ڂ"]="B";["ڃ"]="C";["ڄ"]="D";["څ"]="E";["چ"]="F";["ڇ"]="G";["ڈ"]="H";["ډ"]="I";["ڊ"]="J";["ڋ"]="K";["ڌ"]="L";["ڍ"]="M";["ڎ"]="N";["ڏ"]="O";["ڐ"]="P";["ڑ"]="Q";["ڒ"]="R";["ݐ"]="S";["ݑ"]="T";["ݒ"]="U";["ݓ"]="V";["ݔ"]="W";["ݕ"]="X";["ݖ"]="Y";["ݗ"]="Z";["ݘ"]="a";["ݙ"]="b";["ݚ"]="c";["ݛ"]="d";["ݜ"]="e";["ݝ"]="f";["ݞ"]="g";["ݟ"]="h";["ݠ"]="i";["ݡ"]="j";["ݢ"]="k";["ݣ"]="l";["ݤ"]="m";["ݥ"]="n";["ݦ"]="o";["ݧ"]="p";["ݨ"]="q";["ݩ"]="r";["ݪ"]="s";["ݫ"]="t";["ݬ"]="u";["ݭ"]="v";["ݮ"]="w";["ݯ"]="x";["ݰ"]="y";["ݱ"]="z"})local Ox1UC1EJ2,OxCLAJE13,OxJCDONH7=(""),(""),({})local Ox1O2VOB9=0x1;local function OxSULBCD11()local Ox1UC1EJ2=OxF2SBFV20(OxE2UEJL4(OxJJCEO11,Ox1O2VOB9,Ox1O2VOB9),0x24)Ox1O2VOB9=Ox1O2VOB9+0x1;local OxJJCEO11=OxF2SBFV20(OxE2UEJL4(OxJJCEO11,Ox1O2VOB9,Ox1O2VOB9+Ox1UC1EJ2-0x1),0x24)Ox1O2VOB9=Ox1O2VOB9+Ox1UC1EJ2;return(OxJJCEO11)end;Ox1UC1EJ2=OxHBNUCE10[OxSULBCD11()]OxJCDONH7[0x1]=Ox1UC1EJ2;while(Ox1O2VOB9<#OxJJCEO11)do local OxJJCEO11=OxSULBCD11()if OxCOL2AC6[OxJJCEO11]then OxCLAJE13=OxCOL2AC6[OxJJCEO11]else OxCLAJE13=Ox1UC1EJ2..OxE2UEJL4(Ox1UC1EJ2,0x1,0x1)end;OxCOL2AC6[OxLDD2HV5]=Ox1UC1EJ2..OxE2UEJL4(OxCLAJE13,0x1,0x1)OxJCDONH7[#OxJCDONH7+0x1],Ox1UC1EJ2,OxLDD2HV5=OxCLAJE13,OxCLAJE13,OxLDD2HV5+0x1 end;return(OxBUDJ2V8(OxJCDONH7))end;local OxLDD2HV5,OxCOL2AC6=OxSULBCD11([=[IdenLua|ٸٻݔٷڏٷٶٸپٽٸپپٸپٿٷٻٷٻٸپٽٷٷٷٺٷٸٸپٿٷٶٷٷٷݖٷݖٷٷٸپٿٷٷٷݨٷڑٸپڌٸپپٷٷٷݣٷݢٸپڇٷٸٸپݝٷٺٷٺٸپڇٸپڇٸپݰٸپݚٸپݜٸٿٷٷݚٷݝٸپݟٸپݨٸپݪٸپݒٸپٿٸپݮٸٿٶٸپپٸپځٸٿٺٸپچٸپݤٷݙٷݙٷٷٸٿڄٸپݟٷٽٷٽٸپڑٸپڃٸپݫٸپݭٸٿډٸپپٸٿٸٷٶٷݬٷݒٸٿٶٸٷݪٸٸڍٸڀٶٸٿٶٸٿݗٸپڇٸٽڏٸټڒٷݕٸڀٻٸپڄٸٿݭٸپٽٷݠٷڍٷٽٸپݮٸٿݠٸڀݝٷپٷٺٷٷٸپڑٸٺݔٸٻݐٷݯٷٷٷݟٷݟٸپڀٸپݙٷٶٸڀڐٸڀݩٸڀݫٸپڃٷٷٷټٷټٸپٽٷݯٷڀٸٷٿٸڀݮٸځټٷڀٸٷڀٷټٸڀݥٸپٽٸٺڏٸٻݛٷݫٷٻٷڀٷڀٸپٽٸځٺٷٿٷٿٸپݚٸٷٽٸٷٻٸپݖٸپݜٷٸٸڀڎٸٿݧٸپٽٸپځٷݕٸٷٺٷٶٸٿݧٷٽٸݘٷٷپٷپٸڀݥٸݘٺٸݙٶٷٷٸݙٽٷپٸځټٸٷٿٷݝٸڀډٸپݚٷݥٷڎٸݙڂٸڂݛٸپڈٷݥٷݤٸݙٸٸڂٻٷٶٷٺٸٿٽٸݙݪٸپݱٷٶٸٺڏٸٻڂٷݓٷٶٷڊٷڊٸݘٷٷݠٷډٸڂݠٸڂڐٸݘڅٸڀݕٸڀݨٷٷٷݪٷݪٸپٿٷڋٸٿݙٸځٽٸځٿٸپٿٸڀݰٷٷٸݙݡٸݘݰٷٻٷݤٸݙݧٸپڈٸݘڒٸݘݑٸپݮٸݙٿٸځٻٷٶٸځݱٸٷٺٷٺٸځٺٸڃݯٷݕٸݙچٸڂڈٸڂڎٸڂݧٸݘٺٸپٽٸݙݑٸٿپٸڃٸٸپڃٷٽٷٻٸݙݮٸٿݐٸٿڂٸپپٸځݦٷٸٷڅٷݚٸڀڅٷڋٸݙݩٸٺپٷپٷٽٷݩٷپٷڀٸٺڀٷݬٸݛڏٷٶٸٺپٷݤٷڈٷݧٷٿٷݟٷݣٸݜٿٷٺٷݜٷڀٸٺڂٷڈٸݙݔٸٺپٷٽٷݥٸٺݞٸڀٻٸپپٸڀٿٸڀځٸٿڅٸڀٽٸپپٸٺڋٸټݒٷݠٸٸݘٷݨٸݘݧٷٶٸٸݥٷٶٸٷڏٷڃٷٷٷڄٷٸٷݣٸٸݬٷݤٸڀݮٸٸڒٷݙٷڀٷݡٸٸڏٸݚٽٸڀݜٸٸݞٸٸٸٸپٽٸٺݨٸٸٸٸٷټٸٽݝٷݓٸٸټٸٷݑٸٷڋٸٻځٸٻݪٸٽݞٸٷݩٸټڄٸٷݯٸټځٸٽݦٷݙٸټټٷݗٸٻڄٸٸڄٸٽݬٸٽٽٸٸݒٸټݘٸٽټٸټڍٸٸٽٸٻݨٸټݒٸٸݩٸٺݣٸٻڑٸٸݢٸٷݥٸٽݟٸټٻٷٶٸٺٿٸٸݔٸٺݤٸٽڅٸٽݐٸٸݞٸٺݠٸٺݱٸٸݪٸٽݝٸٸپٷݭٸټپٸٸٺٸټݯٸٺٷٸٻݪٸٷݩٸٺڋٸٺݑٸٺڒٸٽڐٸٷݟٸٺݔٸټڒٸٽݕٷݐٸټٽٸٺݫٸٺٷٸټڏٷٸٸٻڒٷڒٸٷٷٸٻݘٸټٻٷݦٷݘٸپٽٸݜݰٸٷپٷڒٷݐٸݛݑٸڄݓٷڀٸٺڄٸڅݢٷٶٸٽٿٸٺݗٸٷݙٸٺݙٸٷڊٸٿڈٸپڇٷݠٷݩٷٿٸڀݥٸٿڀٷݧٷڑٸڀڄٷٷٷڐٷݩٸڂݮٸڀډٸٷٸٷݮٸݘڀٷٶٷݟٸٷݞٸٷٸٷٺٷݘٷݘٸپݘٷٸٸډڊٷٻٸڃڀٸډݥٸݠڐٸٿݧٸپݘٷٷٸݚݨٸپݛٸډݟٸٷٸٸٷٸٸݛٽٸݠٽٷݘٸڄݟٷٶٷݯٷٺٸݡڄٸپݰٸڂٽٸݠڅٷݐٸݠڌٸڀچٸځٸٸٿڇٷٶٸڀݝٷٸٷٽٸٿݢٸڀڅٷڍٷٺٸڀݣٸڂݔٸٺڎٸٻݝٷڐٷټٸݚݨٸپٽٸݘٶٸڂڎٷݓٷڀٸٿݯٸڃڍٷݪٷځٸځڏٸپڃٸٷپٷݱٸځݣٸپݩٷݔٸٷٷٷٻٸځڏٸݘݢٷٷٸݢډٸݘڊٷڀٸݘݦٸٺݥٸٻڋٷݰٷټٸڋٻٸݚڎٸڊڏٷݤٸځٸٸڋڃٸݢݖٸݡڑٸځڋٸڀݜٷݩٷڅٸڂݤٸځټٷٺٸٷٷٸڂڃٸپݔٸڀچٷڃٷٿٸݢٿٷݩٷڊٸڋڇٸݡݑٷݜٸݡځٸݡݯٸٻچٷڋٷٿٸٷݞٸٷݞٸپٽٷݓٸݚٶٸڊݚٸٷٶٷڀٷݚٸٿڋٸپݰٸځٽٸٷٶٷڃٸݤټٸݙڀٷݖٷݝٸڍټٷڃٸپݖٸݚݤٷڒٷݛٸݛڀٸݙݥٷݦٷݜٸٿݥٸݚڍٷڐٷݝٸڂٽٸݙݠٷٽٷݞٸپڍٷݥٷپٷڈٸݡݐٸڂݥٷٻٷډٸݤݔٸݡٸٷڏٷچٸݚټٸپڃٷݠٷݐٷچٸپݘٷچٷݝٸݚڍٸݤݨٸڍݦٸݙݥٸݤݬٸځݕٸڍݕٷډٸڍټٸڂډٷټٷڊٸڎڋٸپݟٷڍٷپٷݞٸڄݛٸپݟٷݠٷٺٷڇٸپځٷݞٷڇٸڊٸٷڐٷݜٸڎݗٸݥټٷݑٷݜٸپځٷڅٷݜٸڍڌٸڎݙٸٿڀٷڄٷڀٷټٷڄٷڄٸڎځٸڋݪٸٷڂٷٿٸݣݓٸپٽٸٷݟٸٷݟٸڄݜٷٸٸݚݕٸݛݠٸپڇٸڃڇٸٿݤٸڊݙٸٿٶٸڋٿٸٿٻٸپٿٸڄڂٸٿٿٸݦݒٸٿݚٸڀݛٸپݞٸݡݥٸڀڃٸپݞٷٷٸٿݢٸٿڍٸٿډٷٷٸٿݧٸٿڒٸپݟٸٿݫٸڐٽٸٿٷٸڂݔٸڅڐٸݜݣٸڀڀٸڈݯٸپٽٸڀٸٸݧݩٸپٽٸڅڐٸڐݘٸپٿٸڀچٸڀݟٸݧݖٸݥڑٸځݒٸپٽٸڀݧٷݖٷٸٸڋٻٸݚݦٸݨٻٸٻݐٸڑٽٸڋٻٸݚݔٸځݘٸݚڊٸٿٿٸݘٽٸݘڃٸډڀٷٷٸݘڇٸځݠٸڌٻٷٶٸݘݥٸڅݮٷٷٸڃݑٸپݰٸڃݓٸڐݞٸڂڒٸڃݗٸݙݨٸٿڑٸډڀٸڊڈٸݘٸٷټٸڂݘٸڂݚٸڀڎٸݛٻٸݙݞٸݨݭٸڃڍٸݙݢٸݥڅٸڃݤٸݙڐٸݥݟٸݧٺٸٿݯٸݙݰٸݚٶٸڎݫٸڀڎٸڎٻٸڄپٸڐٻٸڃݘٸݨٽٸݚݛٸݚچٸڃݟٸݘپٸڀݔٸڀݥٸݨټٷٸٸݢݕٸپݘٸݢٸٸڃݪٸځݪٸڑݒٸځݓٸڒٺٸڃݦٸڂٶٸݛٷٸځٺٸݩپٸڄټٸڒݘٸݙݦٸڑݧٸڃݕٸڐٺٸڒݣٸڄݝٸڊݙٸٿݘٸپڇٸڄݣٸڄڎٸڀڅٸݛݱٸپٽٸڅٸٸڅٻٸڅٽٸڅٿٷڌٸݜݘٸڅݚٸچپٸپٽٸچڀٸݝڂٸٺٶٸݧݩٸٸڀٷݟٸڀٺٸپٿٸڈݗٸٷڂٸݫٿٸڀټٸڐڒٸڀٿٸٷڀٸڅݭٸڈڏٸڅݗٸݝٷٸݝٺٸݝټٸچڅٸڊڏٸڈݤٸݫډٸݟڑٸݟݐٸݛݒٸݛݮٸٺڀٸٸݜٸٷݮٸپٽٸٻݤٸٻڃٷݚٸٷچٸٻݞٸٽٽٸٷٽٸټڇٷݑٸٸݬٸٷݩٸٷݮٸٸڎٸٻݗٸٻڊٸٸݬٸٽٶٸٻݪٸٸپٸٽډٷݰٸٸٿٸٸݮٸټٽٸٻݢٸپٷٸٺݣٸٽݠٸټڏٸټٿٸټݨٸٽݚٸٺݭٸٷݚٸٷݔٸٺٿٸٻݔٸٷݜٸٽݠٸٽݡٸٺڂٸٺڄٷڎٸٺڃٸٽݤٷڂٷٻٷڊٸٽٸٸٺݫٷݕٸٺݢٸٸݐٷݔٸټڎٸټݞٸٷݯٸٻݨٸٽݩٸٺݬٸݠٸٸٷڃٸٻڀٸٸݚٸٺڒٸٸټٸټڐٸټټٸݜڅٸݐݪٸݜڈٸٺٻٸڄڑٸݪݪٸڈݫٸڄݔٸٸٿٸݠٺٸپڈٸݧٷٸپپٸډٽٸډٿٸپڍٸډڂٸډڄٸݠݝٸݠڈٸپݮٸݠݓٸپٿٸډݖٷٺٸځݦٸډݑٸډݓٸډݕٸډݦٷٺٸݡٶٸݠݔٸݡٺٸٿݯٸݠݒٸݡپٸٿݥٸڊڀٷٺٸڍݔٸݡݛٸݡݝٸڀڍٸڀݥٷݧٸݡݡٸڑٷٸڊڍٸڀݔٸڊݧٷٽٸٿݕٸڀݝٸݡݓٸݤݞٸݡݰٸڋٶٸݐٸٸڑڄٷݥٸڋٽٸݢٿٷݥٸݢݘٸݣٷٷٷٸڋݜٸݣݢٸپݟٸݢݦٸڋڌٷڀٸݢݥٸڋݡٸځݢٸݢڒٸڋݫٸڋݭٸڀݬٷٶٸڋݯٸݡڌٷټٸڎݜٸݕڀٸݨݦٸډٽٸڌپٸݔݱٸݣځٸݙݚٸډڒٸڌڅٷٿٸڍڇٷٷٸڌډٸݕݩٸڀچٸݣڍٸݯݜٸڌڐٸڌݩٸݣݑٷٶٸݦݥٸݣݕٸڌݱٸٿݢٸڂڀٷڀٸݤٻٸݤټٸپݔٷݕٸݤٿٸڍݘٸݪݙٷݥٸڍݜٸݖݠٷݥٸݤډٸڍڋٷݥٸڍڍٸݩڄٷݥٸݤݨٸݤݪٸݤݬٸݥٶٷڎٸݤݖٸڎٶٷڍٸݥٸٸڒݥٷٷٸݥٽٸڎٿٷٻٸݥݘٸݥݚٷڇٸݱڅٸݥڇٸݙڒٸڃڍٸݤݖٸݥݦٸڃݤٸڎݤٺٷٶٸٸڎڑٸݥݪٸݚٺٸݥݒٸڎݮٸݥݰٸݦٶٷݤٸڏٸٸڏٻٸݥݒٸݦٽٸڏٿٸݦݘٸݗڃٸݦݚٸپڃٸݦݜٸݦڇٸڏډٷݝٸڏڋٸݦݤٸݣݮٸڏڐٸݦڒٸݦݑٸݧڊٸڄݡٸپٽٸݦݔٷٸٸڏݖٸڐڍٸݠٻٸݧٸٸڂݬٸڃڀٸݐݤٸڐڌٸٿݜٸݚݖٸݩݔٸݮٽٸپڃٸݧڄٸݤڋٸݧڈٸپݤٸڐڋٸپپٸٿݥٸٿݔٸڐݥٸڐݬٸٿݰٸݫڅٸڐݨٸڀٷٸݫڃٸݧݕٸݔپٸڀڇٸݪٽٸݡݑٸڀڌٸڃݢٸٻݪٷݔٸݠڍٸݰٸٸڑڀٸڃݘٺٷٸٸٸݨݛٸݐپٸڊڃٸݩݓٸپٽٸݱٷٸݘڂٸځݛٸڐݜٸڑݤٸڋݧٸݘݤٷټٸݕݦٸݨݫٸځݒٸݘݮٸݨݯٷٻٸڂٶٸݨݱٸڑݭٸݩٸٸڂڀٸٷٺٸݙڌٷپٸݱٷٸݐݛٸڀݠٸڒڂٸڂڌٸݚپٸݙݨٸݛݘٸݙݒٸڒډٸڂݱٸڃٷٺٷٶٿٸڒڍٸݝݜٸݩݜٸݩڐٸڀݧٺٷٸٸٸݩݪٸپپٸݚڇٸݨݝٸڀݔٸپݮٺٷٺݞٸݰٺٷڎٸڃڏٸݐٸٸݨݪٸݐٻٺٷٸڎٺٷٸڀٸݚݱٸݐݘٷټٺٷٸݗٸڒڀٺٷٺٷٸݐݝٸݤݞٸݐݠٺٷٺڂٸݪݢٺٷٷډٺٷٶݰٷٶٸݐڏٸڅٶٷݠٸݑݟٸڅݕٸݑݡٸݝٸٸݝٻٸٸݰٺٷٷڏٷډٸݓݗٸڅٷٸݔٷٸڄݯٸݭݭٷٶٸٽݔٸٷݛٸٸڅٸٺݕٺٷٻݨٸڅݞٸڅډٸڈݯٸݫݘٸٸݘٸݫڎٷݠٸݑڐٺٷٻچٸݫݩٺٷٻݦٸڄݖٸݜٶٸݐݫٸڅټٸݜپٸڅڀٸݜڂٸٺچٸݧڒٷٿٸٸٶٸٸݘٸݑٶٷٶٸݑٸٷݡٸݫٻٸڀپٸټڒٷٿٸݮٻٺٷٷݬٸڌټٸډٿٸݕݦٸݔݙٸݮځٸݠݞٺٷٸݚٸݔݝٸډڋٸݔݟٸݔڏٸݙٽٸݮݣٸډڋٸݔݥٸݠڐٸݚݦٸݡٸٸڋݗٸݮݑٸݡٽٸڊٿٷڒٸݡځٸٿݥٸݯٶٸځݫٸݠڒٸݡډٸڊڋٸݢݗٺٷٸݝٸڊݑٸڊݨٸڍݞٸݕڃٷپٸݤݮٸݯݝٸڋٷٸݚڒٸݕݠٸݯڋٸڂݔٸڋڀٸݢݙٸݨݩٸݯڑٸپڍٸݕݫٷٿٸڋݤٸݢݦٸݕݰٷٿٸݢݪٸڋݒٸڋݔٺٷٺڑٸݢݖٸݘٸٸڎڈٸݕڀٸݕڂٸݣٽٺٷٸݰٸٿډٸڊݛٸڌڂٺٷٽټٸݤݰٷڍٸݣݝٸݥٶٸݰݢٸݨٷٸڌݤٺٷٽݭٸݖڐٸڌݪٸݣݬٸݣݮٷݕٸݣݰٸڍٶٸٿݢٷڂٸڍٺٸݤݘٸځݢٸݱٸٸڍڀٸڍټٸݧݛٸݱٽٸڍݝٸݚݯٸڃݤٸݱځٸڐݝٺٷٶݢٸݗڅٸݱڇٸپݩٸݤݑٸڍݓٷݙٸݙډٸݱݣٺٷٿݐٸڎڐٸݱݦٺٷٺݛٸݱݩٸڎڀٸݥڂٸݱچٸݱݮٸݙڍٸڃݤٸݱݰٺٷٿݑٸڎݡٸڅٶٺٷٶٺٸݥڎٺٷڀڀٺٷٶٽٸڒڌٸڎݓٸڎݯٷٻٸڎݱٸݦٷٸڏٺٸڍݩٺٷٶݞٸڏپٷٻٸݦڀٸڏݙٺٷٷپٺٷٶڎٸڏڈٸڏڊٸٻڋٸڏڌٸݰݑٺٷٶݬٸٿڏٸݦݪٺٷٻٿٸݦݓٷڋٸݦݕٺٷٷݘٸڄݘٺٷپٷٺٷٷڄٸݙݐٺٷٷٽٸٿڀٺٷٷݡٺٷٽٶٺٷځټٸݧڀٺٷݘٿٸݧݚٸٿݣٺٷٷݞٸٿݨٺٷݘٷٺٷٷڀٺٷٷݤٸڐݭٸڐݬٸݧݑٺٷټڐٸݜڎٸݑݛٺٷٷٻٺٷٷݓٸڀڈٸڃڀٸڀݢٸڑٺٸݩڑٸݨپٺٷٸٻٺٷٷݙٸڑݘٸݨݚٸݰٸٸݨڅٺٷٸځٸڑڇٸݘݘٸݨݡٸپݨٺٷٸڈٸڑݦٸݨݨٸݘݨٺٷٺݒٸڑݭٸݥݟٸڑݖٸݙٺٸݙټٸݙپٸݩٺٸڒټٸڎڅٸڒٿٸݛٽٺٷٺٸٸݱݜٸݩچٸݙڒٸڒݟٸݙݔٸڒݡٺٷٺݘٸݚٻٺٷٺڄٸݐݝٸݚڀٸڒݰٺٷٺݠٺٷٶݗٸڒݬٺٷݙڀٺٷݙٶٸݪٶٸݚݧٸݚڒٺٷٺݑٸڃݬٸݪٽٸݤݞٺٷٺݕٸݛٸٸݙݜٺٷٻٷٺٷٺٻٺٷٻٻٸݙݒٸݐڊٸڄڇٺٷځݣٸڄݢٷٿٸڄݤٺٷٻݚٺٷٻݜٸݜݰٸݝٶٺٷٻڈٸݝټٺٷټٻٸڈڐٸڈڒٺٷٻڏٸݟݮٺٷځڒٺٷٻݱٸډٶٸٸځٸݐݩٸڅٷٸݜٺٺٷټݙٸݪݔٸݪݰٸٺڂٷڌٸݙݤٷٿٸٺݓٸٷݗٸٸٽٷڐٸټڅٸٺپٸٷݦٸڐݩٷݪٸٸڋٸٸځٺٷٻݔٸݓݕٺٷټٸٺٷټݢٺٷټڍٸٸݦٺٷٻڍٸڄݐٸݑݫٸݟݭٺٷٷݦٸٷڊٺٷټݐٺٷځٿٸݮٿٷٷٸݧڀٺٷټݕٸپݩٸݮڄٺٷٽٶٸډݬٺٷٽٸٸپپٸݮډٸڀݥٺٷٽٽٸډݮٸپݨٸݔݠٺٷٽځٸݔݪٸݡټٸݮݭٸڀݡٺٷٽڇٸډڑٸݟݥٸڊڃٸݡݜٸځݑٸݢڍٸݯٻٺٷٽڎٸݘٸٸݤݮٺٷپݢٸݙݮٺٷٽݑٸٿݥٺٷٽݮٸݯڈٺٷݙٽٸݯڊٸݢپٺٷپٷٸݕݤٺٷپٺٸڋݛٸڋچٺٷپٽٸݢڊٸݕݬٸݕݔٸڋڐٸݕݗٺٷپڅٸݰٸٸݰٻٺٷٽڏٸݣٷٸݕڀٺٷٽݪٺٷپݤٸݠڒٸڌڀٺٷپڑٸݙݚٸݖڇٸڍݢٺٷپݔٺٷٷݭٸݣڍٺٷݝٿٺٷٿٶٸݰݩٸݰݑٺٷٿٻٸݰݓٷڂٺٷٸݛٸݰݗٷڃٸٿڐٺٷٿݚٸڍݘٸݚݓٺٷٿݞٸݗٿٺٷٿݢٸڂݠٸݱݛٺٷڀٻٺٷڀٸٸݱڈٺٷٿڒٺٷڀپٸݗݤٺٷٿݯٸݥټٸݥپٺٷڀٶٸݱݓٸݱݯٷݟٸݥڈٺٷٶٶٺٷڀٿٸݥݣٺٷڀڂٸپݚٺٷڀݛٺٷٺݙٺٷڀݝٺٷٶڂٺٷڀڊٺٷٶچٸݱݨٺٷٶݟٺٷڀڏٺٷٶڊٸڍڍٺٷڀݩٸݦݝٺٷڀݫٺٷٶݨٺٷڀݓٺٷٶݐٸݦڏٸݦڑٺٷڀݱٺٷٶݔٺٷٷٿٺٷٺڊٺٷݘٺٸٿڒٺٷځݯٺٷڄݟٸپٽٸٸݫٷݙٷچٸݪݰٷٷٸٸڏٺٷٷݚٸݧپٷٷٸٷڀٸٷڀٸڐډٸډڎٸٷٶٸڐݠٺٷݟݫٺٷٽٶٺٷݘٻٺٷځټٸݧٶٸڐپٸݧٺٺٷٷپٺٷݘݚٷٶٺٷٷڌٸٿٶٺٷݘچٺٷډپٺٷٷچٸݧچٺٷٷڈٸپڒٺٷډݥٺٷݠڐٸݙݭٺٷځڏٸݜڏٺٷݘڐٸݑݚٸݧݧٺٷݘݪٺٷټݑٸݢݰٸڀݟٸݮݮٸڑٸٺٷٸٶٺٷٸپٺٷݙٸٸڊڎٺٷٺڏٺٷٸٿٸݤڇٸݚډٸڒݮٷٷٸڑݠٺٷٸݝٸڀڎٺٷݙڄٸڋݞٺٷݙݝٸݪٺٺٷݚݝٺٷٸڏٸݐٿٸݙٷٸݙٺٸڑݢٺٷٸݬٸڒٻٺٷٸݮٸڒٽٺٷڊݢٺٷٺٶٸډڀٸݙݡٺٷٺٺٸڒݦٸڒݞٺٷٺپٺٷݙݖٺٷٺڀٸݩݣٸݱݨٺٷڃٸٸڃٿٸڀڏٺٷٸٷٷٶٺٷݚٽٷٶٺٷٺݢٺٷڂٿٺٷڊݡٺٷٺڏٺٷݚڂٺٷٺݐٺٷٸݤٸڑݓٺٷڃڈٺٷٸݨٸڄٶٸݛٸٸݪݚٺٷٻٷٺٷڋٻٸڄٿٸݪݟٺٷݚݦٺٷٻٽٺٷݚݨٺٷݠݔٺٷٻڀٺٷٻݙٺٷݡٶٸپپٸݫݘٺٷݡٺٸپٽٷݰٸٸݨٺٷڄݒٸڅچٸڅڈٸڅݡٸٿڅٸڀچٸچٿٸچځٸچڃٺٷڅٷٺٷڄٻٺٷٷڑٸٷڀٺٷݛځٺٷټݘٸݪݓٺٷټݛٸݜݚٺٷڃݔٺٷٻݞٸݫݣٸٸݒٷڒٸݢڇٸٷݣٷڀٸٽݩٸټݯٸٽڅٸټݕٸټݚٸٺݥٸٺݫٸپٷٺٷټٸٺٷڄٷٷٶٺٷټٽٺٷݜٺٸݮٺٺٷݘݬٺٷټݬٺٷڋٽٸډݜٸݠݚٺٷټݰٸݮݜٺٷݜݞٸډڌٸݮݠٸٿݢٺٷڅݣٺٷٽٿٸݮݡٷٿٸڊٷٺٷݜڑٺٷٸڃٺٷٽڅٸݔݮٺٷݜݒٺٷݡݟٺٷݜݰٸپݰٸڊٷٺٷچٷٸݕٽٷټٸݕڂٷݤٸݡݨٸڑٷٸڊݭٸڎݟٺٷچڀٺٷٽݖٺٷݝڂٺٷپٶٸڂݠٸݯݥٺٷپٻٺٷݝډٸڋڈٺٷچڋٺٷپٿٸݯݭٺٷپځٸݢݨٺٷپݚٸݰٶٺٷپݝٸݡݑٸݘٸٺٷݝݕٸڌٸٷٽٸݰڀٺٷپݤٺٷڎٻٺٷݝݗٸݣݛٺٷپݫٷٿٺٷڈٸٺٷݞٺٸݣڌٷځٺٷڎݞٺٷڇپٺٷٿٸٸݘټٺٷٿټٸٿڋٺٷݞݞٸݖݖٸڍݘٸڒپٸݗٺٸݤټٸڐݟٺٷݞݢٺٷٿډٸݱڀٸݤڊٺٷٿݣٺٷڇڏٸڍڐٺٷڀݣٸݙݠٸݗډٺٷٿݓٺٷڈٺٺٷڇݬٸݥٺٺٷٿݰٺٷڇݕٸݱݫٺٷڀٷٸݥݛٺٷڇݧٺٷڀٽٸݥډٺٷٶٸٷڎٺٷٶٻٺٷڀݚٸڎݩٺٷڀݜٺٷٶځٺٷڀݟٺٷٶڃٺٷٶݜٺٷڀڌٺٷݟڅٺٷڀڎٺٷڀڐٺٷٶݢٺٷݟݡٺٷٶݦٺٷڀݬٺٷڀݔٺٷٶݫٺٷڈݨٸݧڇٺٷݘٶٺٷݣټٺٷݘٸٸڃڀٸݩݧٸډٽٸڋڇٸٺٿٷڈٷٻٷڃٷڅٷݙٷڄٷٽٷٿٸٺٺٺٷݠٽٸݧݙٺٷډڀٺٷډݙٸٷڇٺٷډݛٺٷڃڒٺٷݠݞٺٷٷٷٺٷځټٺٷډݱٸݔټٺٷݠڋٺٷځځٸڐټٺٷٷݢٸݧپٸڀݭٺٷݤݡٸپڈٺٷݠݫٸڄݜٺٷݘݢٺٷڑٶٺٷځݤٺٷݘٽٺٷݣٿٺٷڊٻٺٷٷڏٸڐݦٸپپٺٷځڑٺٷڑڒٸݠټٺٷٷݔٸڑٷٸڀڌٺٷݚٻٸݚڂٸݨٿٺٷڂٺٸݚځٸڀݗٺٷڂٽٺٷٸڀٺٷڊډٺٷٽٶٺٷڊڌٸڀڎٸپݮٺٷڊݦٺٷٸڊٺٷٸڌٺٷڂݟٸݪٽٺٷڂݡٺٷݢݬٺٷٸݐٸݐٽٺٷڊݖٺٷڂݧٺٷپݥٺٷݙڒٸڀݠٸځݭٺٷڋټٺٷڂݒٺٷٺټٺٷݘڀٸٿپٺٷٺٿٸڒڋٺٷٺݙٺٷڋڄٺٷٺٻٺٷݩݟٸڀݩٺٷݢݡٺٷڋڌٺٷݩݧٺٷډݦٷٸٸݚڌٺٷڋڐٺٷڃݛٺٷڋݩٺٷݚڇٸݚݕٺٷݚݠٸځٺٺٷٻٶٺٷݐپٺٷݐٿٺٷݣٶٺٷٺٽٸݛڃٺٷݣٺٸݪݣٺٷډڎٺٷݣپٸڊݦٺٷݣݦٺٷڅٺٺٷټٿٸݪݐٺٷڄڃٺٷݣݬٸݪݯٸڅݙٸٺݙٺٷڄݖٺٷݣݤٺٷټڏٺٷݣڀٸډٶٺٷݣڂٷٶٸݫݝٺٷټٸٺٷٻݨٸٽݔٸٺݧٸٸچٸٷݢٺٷڄݓٷݥٸٺٻٺٷڌݯٺٷڃݖٺٷݣݗٺٷݤݜٺٷݤڇٸڈݒٺٷڄټٺٷݘݫٸپٿٺٷټڈٸݠٸٺٷڑݰٺٷڅڀٺٷٷپٺٷݜݚٸپڃٺٷڅݜٺٷݪݦٺٷݤڑٺٷٽٺٸډݧٸځڋٺٷݤݒٺٷݜݥٸݔڏٸݔڋٸݔݩٺٷٽڃٺٷڅݩٺٷٽݝٸڊݘٸپٿٺٷٽڊٸݪټٺٷٽڍٺٷݥڀٺٷڏٶٺٷݝټٸڊݑٸݡݭٸݡڎٺٷڎڈٸڋٺٺٷڎڊٺٷچڄٺٷڎڌٺٷچݞٸپڈٺٷپټٺٷݥڐٸݢڋٺٷڎڒٺٷݝڍٺٷپݙٺٷپڄٸݖٷٸپٽٺٷچݩٸڒٺٸڃݕٸݕڀٺٷپڊٺٷپݤٺٷݬݬٸݖݛٸݙݚٷپٸݰݞٸڐڀٺٷڏݙٸݢݖٸݣݤٺٷݭٺٺٷݦچٸݖݐٺٷٿٺٺٷݦډٸݭٿٺٷٸݨٺٷݦݣٺٷٿݜٺٷٿٿٺٷڏڏٷݚٸڊٷٺٷڏڒٸݙډٺٷڇڍٸݙڎٺٷݦݮٸڂڎٺٷٿݦٺٷڏݱٺٷݞݪٸݥډٺٷڐٺٸݱڐٺٷٿݱٺٷݧپٺٷڇݗٺٷڐځٺٷݟٷٸݱݗٸݗڋٺٷڈٻٸڂݥٺٷڐݝٺٷݟپٺٷݧݟٺٷڈڀٺٷڐڊٺٷڀݠٺٷٶݛٺٷڀڋٸݦټٺٷݧڐٺٷݟڈٺٷٶݣٸپݟٺٷڀݐٺٷٶڐٺٷٶݩٺٷڀݯٺٷڐݯٸڀݟٺٷڈݪٺٷډݥٸڏݮٸٿݩٸڊݥٺٷٻݣٸݙڒٸٷݓٸٷٿٸپݖٷݫٸٷݑٷݯٺٷٻݨٸٸڑٷڄٷݥٸٸݒٺٷڌڑٺٷٻڑٸٺٸٷݙٷډٸٺڄٷڅٺٷݨݰٺٷډٿٺٷݠݘٸپݤٸڍڀٺٷٷٷٺٷݝڅٸݐݕٸڐݰٸݤݜٸݠݣٸڊڄٸٷٸٸپݘٸڄݞٷٺٸݰټٺٷݡڀٸݡݨٺٷݡڀٸݡݓٸڍڋٷݤٷݡٷٻٸݰپٺٷٽڏٸݤڋٸڎݪٸڏݐٺٷٸݝٺٷډݚٸݠڀٸڃݭٺٷݑٽٸډٿٺٷڑڏٺٷډݠٺٷݘپٺٷڑݪٸٿپٺٷډݤٺٷٻڀٺٷݠݰٺٷڑݕٺٷݩݚٸٿڊٺٷݘډٺٷݠݒٺٷڒٸٺٷݨݒٺٷݘݛٸڐٸٺٷٷڎٺٷݡٷٺٷٷݐٺٷٷڑٺٷݡټٺٷڅٿٺٷٷݔٺٷݡڀٺٷٷݗٸپپٺٷڊݝٺٷݡݛٸڀݮٺٷݱݮٸݘٷٺٷڊڈٺٷٸݙٸݨڈٺٷٸڅٸݨݢٺٷڒݬٸݐݞٺٷݩݮٺٷڊݐٸݨݮٺٷڊݒٸݨݱٺٷݡݯٺٷڂڎٺٷٸݓٺٷٸݕٺٷݢݕٺٷٺٷٸڀڎٺٷݪڀٺٷݞڐٺٷݙݓٺٷݫٸٺٷڑݨٺٷڂݗٺٷݢڃٸݱڐٺٷڃٺٺٷڋݞٺٷٺݟٸݚڅٺٷڈݒٺٷٺݣٸځٷٺٷݢݦٺٷپڇٸݪٷٺٷݐݪٺٷڒݯٺٷڂپٺٷݐݔٺٷٸݝٺٷݪٽٸݪٽٺٷٺݜٺٷݚڎٺٷݫٺٸڄڅٺٷݣٻٺٷݗݡٺٷٻݘٺٷݚݫٸݪݧٸݡڏٸݫݥٺٷݩڀٸݮپٺٷڈݰٷٶٸٸڋٸٽڋٸٺټٸٽݞٸݜځٸټٸٸٺڋٺٷݫݠٸݫٺٺٷڄڒٸٸݢٺٷݫڎٸݜݤٺٷڄپٸٷݙٺٷݛڀٺٷټڀٺٷݑڄٺٷټڃٺٷݫݝٸݜڃٺٷݒٸٺٷڄٺٺٷݫځٺٷݫݔٸݓݰٸݛڒٺٷټپٺٷݫݱٸݑڋٸچٻٸٷݭٺٷڅپٸڐپٺٷݜڀٸڒڄٺٷݒݛٸپڈٺٷݬݝٸډډٺٷڅڈٸݢٺٺٷݒڎٺٷݤݯٷٻٺٷݤݨٺٷݤݭٺٷݤݫٺٷݒݧٸڊٻٺٷڎٶٺٷݜݐٸڌټٸݡځٺٷڏٶٺٷݒݓٸځݫٺٷݒݯٺٷٷݓٸځٸٺٷݘݕٺٷڎݚٺٷݙݣٸڋݖٸݯݛٸڃݯٺٷݭٻٺٷٸٺٸݙډٺٷڎݢٸڂݥٺٷݥݤٺٷچڈٸݯڒٺٷݝݤٺٷݝݣٺٷڎݫٺٷݝڏٺٷݭݠٺٷٺݧٺٷڎݰٺٷٶݮٸݕڀٺٷڎٸٸݣپٺٸٺٽٺٷݭڒٸڄݔٷڀٸݰݞٸݰݠٺٷݓݔٸݰڍٷݘٸݰڏٸݣݨٺٷٿٷٺٷݮٷٺٷݦݟٺٷݞڂٸݖݯٺٷݞݜٸځݗٺٷݮڀٸݗټٸݗپٺٷݦݐٺٷݮڅٸݦݙٺٷٿݥٺٷݦݰٸݥݝٺٷݔݢٺٷݧٸٺٷڐٷٸݗڎٺٷݧٻٺٷݞݔٸݗݪٸݱݬٺٷڀٸٺٷڈٶٺٷڈٸٺٷݔݒٺٷݧڄٺٷݮݯٸڎݧٺٷݮݱٸݥټٺٷݯٷٺٷڐݣٺٷݕٻٺٷڀڍٺٷٶډٺٷڀڑٸڏڄٺٷڈݢٺٷݯݙٺٷڈݥٺٷݕڄٺٷٶݭٺٷڑڍٺٷݢݢٺٷڈݭٸپپٸݥڈٺٸٷݢٸݑݝٺٷݕݱٺٷݰٷٸٸݑٺٷٻݤٺٷݕڎٺٷݯڐٺٷݕڒٺٸٷڍٺٷݕݒٷڎٷݒٷچٸځٻٸٺٽٸݧݩٸټݐٸٽڎٺٷځݐٺٷڌڀٸٽپٸٷڄٺٷݰٻٺٷݱݜٸپݩٺٷڑݠٺٷݰٿٷڃٺٷݖځٸڂݠٺٷݰݚٸݮپٺٷݖڅٺٷٽډٷٺٺٷݖڈٸݡٷٸݱڑٺٷٽݦٸݨٷٸݡڑٺٷݕݢٸݡݬٷپٸڐڀٺٷݰڒٺٷݰݑٸڂݤٸݖټٸݖݠٺٷݖݕٸݪڂٸڀݐٺٷڑڋٸڊٻٺٷݱٸٺٷݣٽٺٷݱٻٺٷٷٸٺٷݱݣٺٷڑݖٺٷݠݣٺٷځݙٺٷݗڂٺٷݨݮٸٿݝٺٷݨݞٺٷݗچٸݧݜٺٷݩٷٺٷݠڅٺٷډݯٺٷډݢٺٷݗݤٺٷݒٽٸپٿٺٷݩڂٺٷڒپٺٷݬݘٺٷݗݐٸڀݡٺٷݡݘٺٷݱݓٺٷڋڈٺٷڒڊٺٷݡڅٺٸٿٸٺٷڒݥٺٸٶٷٸݨݞٸڒپٺٸٶٻٸݠڀٺٸٶٽٺٷݡݨٺٷڃڅٺٷݒݔٺٸٶځٺٷٷݙٺٷٸڒٺٷݡݮٸݩٷٺٸٶڅٺٷݡݗٺٸٶݞٺٷڋٸٺٷݢݖٺٸٶݡٸݩݚٺٸٶڌٺٷݪݙٺٷڂݯٸځچٺٷݢڂٺٷݐݞٺٸٶݩٺٷݢچٸݨځٺٸٶݒٸݩݫٺٸٶݕٸٿٿٺٸٶݱٺٷٺݩٺٸٷٸٺٸٶڀٺٷڋݑٸݐڀٺٷڋݮٺٸٿݦٺٸٶݠٺٸٷڀٺٷڌٷٺٸٷݙٸٿڏٺٸٷݛٺٷٶݕٸݪݥٺٸٷݞٸݜٶٺٸٷݢٺٷڄݪٺٷڌݙٺٷڌځٺٷݣڑٺٸٸڇٺٷݚݱٸٸݬٺٸٷڍٸٸٺٸټڂٸٻډٸٷݗٸٺݛٸٽڍٸٸݧٸٽݫٺٷݣݪٺٸٸټٺٷݛڅٺٷݑڇٺٸٸݚٺٸٸڀٸݫݐٸݟݬٸٺڀٺٷݫڀٺٸݘڂٺٷݛݕٺٷڌڌٺٸٷݮٸٿݜٺٷڅٽٺٷݬݘٸډپٺٷٸڀٺٷڍݤٸݔݚٺٷټݗٺٷݬڇٸݔݞٺٷݜݠٺٷٽٻٺٸٽݖٺٸٸݔٸݮڍٺٷݬݤٸݠݧٺٷڎٽٺٸٺٶٺٷٽݛٺٸٺٺٸݡڏٺٷݜݒٸݣٷٺٸٺپٺٷٽڌٺٷݥٿٺٸٺݘٷټٺٷچٻٺٸٺڄٺٸٺݚٺٷݖڐٸٿډٺٸٺݠٺٷٽݗٺٷݭپٺٸٺڍٺٷݓڀٸݯݧٺٷݥݦٸپݚٺٷپپٺٷپڀٸݯݯٺٷݥݒٺٷݭݟٺٷڎݯٺٷپݟٷټٸݖڀٺٸٺݛٺٷݕݢٺٷپݤٺٸڂټٺٸٻٸٸٿڐٺٷݞٷٸڐݝٺٸٻپٷݤٺٷڇټٺٸݙچٺٷݔٶٺٷڇڀٺٷݔٺٺٷݞݛٸݤݘٸځټٺٷݔڀٺٷݞڊٺٸٻݣٺٷݮݛٺٷڏݬٺٷݞڎٸݤݥٺٷݞݧٺٷݮډٺٸٻڒٸݱݡٺٷٿݬٺٷڈپٺٷڇݓٸڎݬٺٷڐٽٺٸٻݗٺٷڐڀٺٷݔڊٺٸټٸٺٷٶٷٺٷڀڀٺٷݧڅٺٷڈٽٺٸټٽٺٷٶپٺٸټٿٺٷڀݞٺٷݕٸٺٷڐݤٺٷݕټٺٸټݛٺٷڐڒٺٸټچٺٷڐݫٺٷݟڍٺٷݧݭٺٷڈݧٺٸټڋٺٷݩٺٺٷݟݒٺٷڑٸٺٷݕڋٺٸټݪٷډٸٸݕٺٷٻڋٺٸټݭٺٷݕݦٷٺٺٷݕݨٷݕٺٸٷݤٸٺٺٸپݧٷڏٸݖٽٷݙٸٸݔٷݛٺٷݰټٺٸٽݞٸپڒٷݡٷݞٺٷٷݯٸݙڎٺٸٽڌٸڌټٷݛٺٸٸݔٺٷپڏٺٸٽݧٺٷݰډٺٸٺݔٺٸٺڃٸݡݨٺٸڂڄٺٷڂݥٸپڃٷݓٷݨٺٸپٷٸپڃٸݙݐٸݧݝٺٸپپٺٷݠڄٺٷݬݔٺٷݗٺٺٷݠݟٺٷٷځٺٷډڊٸٿټٺٷݱڀٺٸپڈٸٿݬٺٷݘڅٺٸپڌٸپݩٺٷڒٶٸٿݦٺٷݗډٺٸڀݡٺٷݩٻٺٷڑڑٺٸٷݢٺٷڒٽٸپٽٺٸٸٶٺٷݗڏٺٸپݕٺٷځݔٸپڑٺٷځݰٺٷڊݙٺٸٺڊٺٸپݢٺٸڀٶٺٸچݥٺٷڂپٺٷݐݥٺٷٸݛٺٷݙݙٺٷݩݑٸځڈٺٷٸډٺٸٶپٸݨݩٺٷݪݑٺٷݡݫٺٸٿڈٺٷݡݓٸٿڐٺٷٸݫٺٸٿݣٺٷݪٻٺٷݐݰٺٷݐپٺٷڂݫٺٸٿݪٺٷڋٿٺٷݐڄٺٷݢݘٺٷݐݝٺٷڃٷٺٷݪݠٺٸٶݫٺٷڋډٺٸٶݓٺٷݚپٺٸڀٺٺٷٺڎٺٷݢݟٺٷݐݩٺٷڂݞٺٸڀٿٺٷݪݭٺٷݢݒٺٷٺݰٺٸڇٿٺٷٻٸٺٷݑٷٺٷݐݚٺٷݚٶٺٸڀݟٺٷݑټٺٸپݙٺٷݚݬٸڄڐٺٸٸݜٺٷݑݘٺٸݘٻٸݐݒٺٸٸٽٺٷݛݝٺٸݘچٸݫٷٺٷڌݤٸٸڏٺٷݑݔٺٷڌݠٺٸپݫٸپٽٺٷڄݐٸڅݒٸݜݮٺٷڃݯٺٸٸڈٷݣٺٷٻݡٺٷټݧٸٷڀٺٸٷڍٸټٿٸٽݠٸٸݟٸٽݰٷڋٸټݱٷٷٸٷٷٺٸݘڀٺٷڌݧٸݑڀٸډٶٺٷݬڀٺٸٽڅٺٷݤݢٺٷݒڃٺٷڍݥٺٷڅݛٺٸݘڐٺٸٸݩٺٷڍݩٸݮڏٸݠڒٺٷݬݣٺٸٸݑٸډڐٺٷپݩٺٷٽڂٺٸٺٷٺٷݠڏٺٷݥٷٺٷݜݑٺٷݬݑٸپپٺٸٺپٸڍݚٺٸڂٿٺٸٺݔٺٷٽݪٺٸٺݛٺٸݙݙٸݡݭٸڌٷٺٸݙڇٺٷݓٽٸݯݣٺٸٺݥٺٷݓځٺٸڂݤٸݯݪٺٷڎڑٺٸݙڐٺٷچڎٺٷڎݭٺٷݝڐٺٷݓݡٺٷپڇٺٷݖݣٺٸپݱٸݣٺٸڋڇٸݰݘٸڌٿٺٷݜݯٺٷݝݗٸپځٸݖڇٸݕݦٺٸڃټٸڌݤٺٸډݱٺٸݚڀٺٷݔٸٺٷݞݙٸځڏٺٷٿڀٺٷݦڐٷٽٺٷڇݟٸڍټٸځڏٸڍݛٺٷٿڈٺٸݚډٸݱڂٺٷݮݞٸݗݭٺٷڇڒٺٸݚڐٸݤݱٺٸٻݬٺٸڃݐٸݗڑٺٸڃݬٺٷڐٿٺٷڀٺٺٸڃݯٺٷݮݑٺٸڃݗٺٷڈټٺٷٶټٺٸټپٺٷٶڀٺٸڄٽٺٸټځٺٷڈڄٷݠٺٷݟچٺٷݧڑٺٷڈݠٺٸݛݚٺٷݟݣٺٷݕڃٺٷڐݮٺٸݛڈٺٸٷݜٺٷݯډٺٸچڏٺٷݑٿٺٷݯݤٺٸݛڒٺٸڄݑٺٸڄڍٺٸټݬٸݙڒٸٺٿٷٽٷڊٸڊݨٷݥٺٷݫݢٸڐݧٺٸٽڃٺٸڅٺٺٷݰپٸپڒٺٷݖڀٸݯڌٺٸڅݘٺٸڂٺٺٸݜݚٺٷݭڑٺٸٽڑٺٷڅݤٸݰټٺٷݥڂٸݡڑٺٷݥڂٸݡݓٸڋٿٺٸپٶٺٷݖݬٸݘٸٸڋٿٺٸپټٺٷݰݗٺٸپٿٺٸݞڀٺٸݜݮٺٷݗټٺٸڅݖٺٷݗپٺٸݝٶٸݩڐٺٷݠݝٺٷݐݦٺٸچٻٺٷݰټٺٸچپٸڑݔٺٸپڐٺٸپݠٺٷٷٺٺٷٷڐٺٷڄٽٺٸݝݟٺٷݬٽٺٷڊٽٸݧݗٸڀڄٺٷݘݰٸٿݥٸݩݖٺٸٿٺٺٷݱݖٸڑڂٺٷڂٷٺٸٶٶٸݛٺٺٸٶٸٺٸٿڀٺٷݙݙٺٷݡݥٺٸچݔٺٷݙݜٺٷٸݢٺٸچݗٺٸٷٺٺٸٿڇٺٷݙݢٸڐݟٺٸٿݢٸڃݮٺٷݐٻٺٸٶݟٸݪݜٺٸٿݩٺٷٺٻٺٸݞڃٺٸٶݦٺٸٿݮٺٸݞݞٸڒݦٺٷݩڈٸݩݩٺٸڇݢٺٸټڍٺٸڀٺٸݩݕٺٸݤݖٺٸڇڐٺٷݡڒٺٸٿچٺٸڀڀٺٷݢݭٺٸپٽٺٸٷپٺٷڋݱٸݪݞٺٸٶݥٺٷڃݧٺٸڈٷٺٸڀݢٺٸڈٺٺٸݤڍٺٸڈݟٺٷݢݠٺٷݛݫٺٸݟپٺٷڄڄٺٷڌݭٺٷټچٺٸڈڑٺٸݟݙٺٷټݣٺٸݟݛٺٸٸݚٺٸݘݛٸݑݒٺٸٷݤٸٸݜٸٸݨٸٺڀٸٽݡٸٽڍٸٺڈٸٺݙٸٸڋٺٸډٷٺٷݜٺٺٷݬټٸپٽٺٷټٶٺٸڀݐٸݫڌٺٸٸݡٺٸځڋٺٷݱٻٸڐݝٺٸٸݦٸډݜٺٸݠݙٺٷٽٷٺٸډݛٺٷݒݡٷڀٺٸݠݞٸډڍٸݮڏٺٸٸݗٺٸݠڋٺٸڂٷٺٷݒݪٸڊݓٸڂݤٺٸٺپٸݐݙٺٸډݫٺٸݙݒٺٸٽݒٷٽٺٷݒݱٺٸٽݯٸٿݯٺٸݡٶٺٸٺݢٺٸݙډٺٷپٸٸݕڏٺٷݭݙٺٸڂݥٺٸڊپٺٷݥݪٺٸݙݨٺٸٺݫٺٸڂݫٸݰټٺٸٽݮٸڊڑٺٷچݫٺٷپڍٺٷڂڑٺٸݚٷٷٽٸݖݞٸݣڈٸڌڊٺٷپݯٸݣݥٸپٽٸڊݖٺٸٻڂٺٷݞٿٺٸݡݫٺٷٿٽٸڍٸٺٷݮٽٸݝٷٺٷڊݢٺٷݮڀٸݤݚٺٷݮݚٸڍڈٺٸڃݡٺٷݮݝٺٸݚݣٺٷڏݕٺٸݢٿٺٷڐٷٺٷݔݒٺٷݔݤٺٷݧټٺٸٻݰٺٸݢݝٺٸټٷٺٸݢݠٺٷݔݭٺٷڀݘٺٸݢڌٺٸݛٻٺٸڋڎٺٷݟݙٺٷݕٺٺٸݢݨٺٸݢݪٺٷݕپٺٷݧݪٺٸڋݮٺٸټډٺٸڋݖٺٷݟݩٺٸټݣٸڏݔٸڐٷٸٿݯٺٸݤڀٺٸپݝٺٷݨݑٺٸچځٺٷݨݓٺٸڍچٺٸݠٽٺٷݨݱٺٷݗݞٺٸپݦٺٸټݣٺٷډݖٸٿݕٺٸچڄٺٸڏݙٺٸپݬٺٸٷݱٺٷٷڒٺٸݐٻٺٸݤݩٺٷݱݫٸݡݙٺٷݱݗٺٸݣٸٺٸݪݢٺٸچڒٺٸڎٸٺٷݡݢٺٸٿځٺٸݥټٸڑڎٺٷݡݧٺٸݥٿٺٸڇڑٺٸٿچٺٷڒݗٺٸٿډٺٸڎݛٸڀڎٺٷݪٺٺٷݢٶٸݩٸٺٸڏٺٺٸٿݨٺٷݤݣٸݪݝٺٸݥڌٺٷݪݜٺٸݞݱٺٷٺڃٺٸڇڈٺٸݝڐٺٷݐڌٺٷݚٿٺٷݢݥٺٸڇڏٺٸٷٶٺٷڃݚٺٸݪݓٺٷٺݓٺٸݦٶٺٷٺݰٺٸڎݟٺٸٷٿٺٷٻٺٺٸڀݝٺٸݑځٺٷٻپٺٸݛݠٸپٽٺٷݑپٷݠٺٸڏݝٺٷݑڅٺٷݛچٺٸٷݓٺٷݣڎٺٸڈټٺٷݬٻٺٷݱݧٺٷڒٿٸڐڒٷڇٸٸٿٺٷټݡٸڀݔٸٽݒٸٻݥٸٻڋٸٷپٸټݚٺٸٸٷٺٷڌݝٸݭݔٺٷݑݕٺٸݦݗٺٸݘڂٺٸڐٻٸݝٻٸٸݒٸݑڎٺٸځڊٺٸݪڇٺٸځݣٸݔݘٺٸډڀٺٷݒݜٺٸݧݚٺٷݬڈٺٸځݪٺٸݧچٺٸݧڈٸݔډٺٸډݝٺٸݙٶٺٷݒݩٺٷݥٸٺٷٽݟٺٸڅڅٸݕٷٸډڀٺٸݧݪٺٸڑڂٸݯٿٺٸٺڄٺٷݖݒٺٸڌݯٸݣڏٸݯڇٺٷڎډٺٸݨٶٺٸڊٸٺٸݙݢٺٸݨٻٺٸڊٽٺٷݓڄٺٸݡٿٺٷݭڇٺٷڎݮٺٷݝݨٺٸݡݛٺٷٽݦٺٸݙݙٸݡݨٺٷݭݦٸڌپٺٸٽڏٺٷݝݱٸځڏٺٸڑݡٺٷپٷٺٸݡݧٺٸݨݥٷٶٺٸݨڐٸݖݨٺٷݦݞٸݖݬٺٸڑݑٸڊݜٺٸݨݓٸڍپٺٷٿݛٸݤݙٸڀݤٺٸݩٶٺٷٿݡٺٸݩٸٺٸٻݦٺٸڃݤٺٸٻݨٺٷڀټٺٸٻݐٺٸڒٿٺٸݢݙٺٸٻݔٺٸݚݑٺٸڒڂٺٷݮڑٺٸڋݟٺٷڀپٺٸټٻٺٸݛٸٸݡٸٺٸڋڍٸݗݨٺٸټڀٺٷڈڃٺٷڐݥٺٸڋݩٺٷݕٽٺٸټݜٺٷٶݤٺٸټڇٺٷڐݬٺٷڈڏٷٶٺٷڀݖٺٷݧݰٺٷݕڇٺٷٻڀٺٷٷٶٺٸپݛٺٷݘݥٺٸݐٻٺٸپڇٺٸٷݜٺٷݗڃٺٸڌٸٺٷڊٽٺٷځݟٺٸپݥٺٸݝٿٺٸݤݡٺٸݝٺٺٸپݜٺٸݐݚٺٸچݝٺٸݐݝٸپݞٺٸݝڄٺٷݩڂٺٸݤڑٺٷڒݜٺٷٷݓٺٷݩݞٺٷڋڇٺٷݩڍٺٷݗݛٸڃڌٺٷݡݞٺٸڎٷٸڑڇٺٸݝݑٺٷٸچٺٸچݭٺٸݪݐٺٷڒݓٺٸݥڀٺٸٶڀٺٸݐݕٺٸݞٺٺٷݡٿٺٸݫٶٺٸݞٽٺٸݑٸٺٷݐټٺٷٺٶٺٷݞݡٺٸڎڊٺٷڋپٺٷݙݔٺٷݢڀٺٸٿݭٺٸڇچٸٿٿٺٸٿݖٺٷٺچٸݚݙٺٸݑڅٺٸݞݤٺٷݪڐٸڃݙٺٸݥݕٺٸٿڅٺٸݑݣٺٸڇݪٺٸڀځٺٷݐݯٷٸٺٸٷپٺٷڇݡٺٸڇݯٺٷٻټٺٸٷݚٺٸڏٿٺٷݒپٺٸڀڌٸݐڑٺٸٸٻٺٸڈٿٺٸݘٽٷڀٺٸڏډٺٷݑڌٺٸٸٸٺٸݒݣٸݛݮٺٸݧٷٺٸݯݱٸٷڀٺٸٷݡٺٷٻݢٺٸٸݚٺٸݒٷٺٸݣچٺٸݑݓٺٷټݠٺٸݒڎٸݝټٺٷٻڑٸٸݠٷپٸٻټٸٽٸٺٸݦݦٷڀٺٷݤډٺٸݒݪٸݮڀٺٷݜݛٺٸݒݭٺٸٸݧٺٸݒݕٺٸځڒٺٸډڈٸځݬٺٸݭٷٸݮݦٺٷݒݢٺٸݭٻٺٸٺٸٺٸڐݥٸݖݚٸݕٷٸڊڈٺٸݓڂٺٷٽݦٺٸډݭٺٸڅڊٺٸچڋٺٸڐݕٺٸݭڈٺٷٽݕٺٷݭټٺٸݓݢٺٷݝݜٺٸڊٺٺٸڂڌٺٸٺݧٺٸݙݦٺٸڑپٺٸݡڀٺٸݙݪٺٸݓݫٺٸٺݮٺٸڑݚٺٸݧݓٺٷڅݮٺٸݡݠٸݖڃٺٷݝݗٺٸݚٸٺٷڏٿٺٸڑݢٸݖڌٺٸݚٽٺٸݮٽٺٸݮٿٺٸٻݚٺٸݚݘٺٷݞݙٺٸݨݒٺٷݞڅٺٸڊݓٺٸݨݖٺٸݮډٺٸݚڈٺٸڒٷٺٸڋټٺٸݩٻٺٷݔݟٺٸݮڏٺٷٿڑٺٸݢڀٺٸڒڀٺٸٻݯٺٷڇݰٺٸټٶٺٷݮڒٺٸݚݖٺٸڒچٺٸڄٷٺٸڒݟٺٷڐݠٺٸڋڏٺٸݕټٺٸݛڀٺٷڈڇٺٸݕڀٺٷݯڀٺٸݯݙٺٸݛݜٺٸݯݛٺٸݕچٺٷݯچٺٸݩݬٺٷځٺٷݘٺٷٿݓٺٸݫݕٸڅٶٸٸݚٸٷٸٷڊٷچٷݫٷٺٷݟٷڊٷڎٺٷڑݙٷڑٸٸݱٺٷڐݜٸپٽٺٸټݔٺٸݛݐٸٸݦٺٷټݢٸټٻٸٺݐٸٻڏٷݗٸٻڐٺٷٻڅٸٸٿٸٷڒٷݪٷݨٷݑٷݑٸٿڑٸٺݞٺٸٷݤٸٷݕٸٷپٺٷډٸٸݜݙٷٷٸٺڅٺٷݕݖٸݙݮٺٷݖٶٷݠٺٸݣٿٺٺٺݟٺٸڌټٸٷݑٺٷڌڒٺٷڌڊٺٸٷݤٸٸٽٸٷڂٸݣݝٷݮٸڊݒٸٷݬٺٷٻڑٸٷځٷݪٸٺݬٸٻݭٺٷپڇٺٸݯݩٺٸڅٻٺٷݒڅٺٸډڀٺٷݩݐٸٷٸٸݛٶٸݨٷٸڃݖٸڍڋٸٷپٸٷټٸݪڌٺٸݙٿٸݔڌٷݯٺٷٽݧٺٷݦٷٺٷݦٶٸݯڐٸٷݙٺٷٶݮٸݠڎٷݕٺٷݖڊٸځٺٺٺټݞٺٸڅڇٺٸڂٺٷݚٸݖٽٺٸڐݧٷٺٸٷٺٸݛٸٺٺٷݨٺٷٽڒٺٷݓݤٺٸٽݯٺٸډݭٸݣݝٸݰݠٷݤٷݠٺٸݪݬٺٸڐݠٺٺټڈٸݚݮٸٷڄٷݥٷݖٸڀݔٺٸڋٷٷݮٷݱٺٷݖݘٸپݘٺٷݱٶٸځڋٺٸپݘٸپڇٸݢڍٺٸڍٿٸٿݜٺٸڅݱٺٷٷټٺٸݝٷٺٸݯݦٺٸپݡٺٷٸټٺٸݕݩٺٸݤڈٺٷݠݓٺٺٽڐٺٸڍݣٺٸݖٸٺٸݐڅٺٸٽڀٸپٿٸݧݔٺٷݗݩٺٸݝݡٺٷٷݖٺٷݘݗٺٸݤݓٺٷݱݕٺٷڂٻٺٸڍݱٸٿٿٺٸٿپٺٷݰچٺٸٿځٸځچٺٸڎٽٺٸݐݫٺٸٶٿٺٸݐݮٺٷٸڐٺٸݪݰٸݗݱٸݙڌٺٸڎݝٺٸݖڒٺٷڃݢٺٷݙݪٺٸٶڋٺٸݥڋٺٸݖݕٺٸݞڄٺٸݖݗٺٸݫځٺٷݪݟٺٸڎڐٺٷݢڇٺٸڎݩٺٸڀٸٺٷݢݤٺٷٸٶٸݨٽٺٸݱڀٺٸݞٶٺٷٺݔٺٸڇݑٺٷݚݡٸݡڃٺٷٺٶٺٷڃݤٺٸݑݩٺٸݦپٺٸټڌٺٷݫپٺٸݐݙٺٷݩڀٺٷټٶٺٸݑݰٺٸݟڀٺٷݑڇٺٺٶچٺٸݱݖٷٶٸٷٸٸٸݬٺٸݬډٸڅٷٸݓݯٷڐٺٷٿݓٸټٺٸٷݯٸټݦٷٶٸپٶٸٷڏٸٺݔٸٸݖٷڋٸٸڑٸٽٿٸٻݚٺٸݗݮٸڄݯٺٸݬٷٸٸݦٺٺٶٿٺٸڈݧٸپٿٺٷݑڐٸپپٺٸݬڒٺٸݤڑٺٸݘݣٸݤݢٺٸݧځٺٸٸڑٺٸڐڄٺٷݒډٺٸڐڏٺٺٶݩٺٸݭٶٺٺٶݬٺٸݠڍٺٸݙٸٸݮݕٸٿݯٺٸٺپٺٸݢٷٺٺٷٶٸځٸٺٸݧݬٺٸݜݢٺٷڏٶٺٸݧݱٸڋټٺٸݨٷٺٷچچٺٸڑٺٺٸݡټٺٸٺݨٺٷݭݜٺٸٺݐٺٸڊݘٺٸٺݒٺٷݭڋٺٸڂݘٺٺٺٷٺٸٺڄٺٸݭݖٸڊݮٺٷچݖٸݙڃٸݘٺٸݖڇٺٺټݚٺٸݮټٺٺځٻٺٸڊݐٺٸٻڅٺٷٿٽٸډݩٺٸڊݮٺٷݔݘٺٷٸݨٺٷݔڀٺٷٽڌٺٸݔڊٺٷݦݫٺٺٸپٺٸٻڐٺٸڒٽٺٷݞݫٺٸݮݪٺٷݮݥٺٸݢݜٺٸݮݔٺٸٻڒٺٺٸݠٺٸݮݱٺٺٸݣٺٷݕٶٺٺٸڎٺٸڒݣٺٸݯٽٺٸڒݥٺٺٸڒٸݝٸٺٺٸݑٺٸڋݯٺٸݛڇٺٸڒݑٺٸݫݒٺٸټݤٸݡڍٺٷݩټٺٷݱٽٺٸݩݱٺٺٽڏٺٸݐٷٺٷݱݢٸٿڅٺٷډݩٸݧڂٺٺٽݫٺٸݝڀٺٸڍڄٺٸݪڀٺٸپݐٺٸݖٷٺٷڊٸٺٸݒټٺٸݝډٸڊٿٺٸٿٶٺٸچݧٺٸݤݔٺٺݚڅٺٸٿٽٺٸݖݛٺٷڊڊٺٷݩڒٺٸٿݙٺٺپچٺٸݰݡٺٸݫݢٺٷڂݠٺٺپڊٺٸݖڎٺٸٶڄٺٺپڎٺٸٿݥٺٸݫٻٺٸݞځٺٺپݪٺٸٶݥٺٸݑڀٺٸٶݨٺٷݢڅٺٸݗٺٺٸڀٷٺٸٶݮٺٺٿٸٺٸڀٻٺٸݫڈٺٸڀٽٺٺڃڏٺٷݐݒٺٷݡݬٺٸݑڎٺٸڀڃٸݐݜٺٸݱډٺٷڌٸٺٸݗڋٺٺٿݝٺٸݗݥٸڊݦٺٷٻڅٷټٸٻݩٸٸٿٸٺڇٸٸݑٸٽٺٸٷڐٸٷٸٸٷݟٺٺٿݢٺٸݗڒٸٺݙٺٺٶٿٺٸݒݧٸپپٺٸټڑٸټڒٸٷڀٺٺٶٺٺٸځڇٺٷټڎٸݧݩٷݔٸٸڏٸٸځٺٺڀڀٺٺٿݦٺٸݝڅٺٷټٶٺٺٶݝٺٺٶڈٺٺڀڊٸډٿٺٸډٿٺٸݘڏٺٷڍڐٺٺٶڏٺٸڐݠٸډڐٺٷݒݦٺٸٸݯٺٸځݕٺٺٶڑٺٺڀݫٸݮݒٺٺٶݮٺٷٿݭٺٸٺپٸݧڈٺٺځٶٺٸݙݓٺٸڊݟٺٸٺڄٺٸڐݮٺٷݭٸٸڀݔٺٺځټٸݚݤٺٸٺݣٺٸڑٸٺٷݥݥٺٺٷݛٺٸڑٽٺٷݓݝٺٸݙݩٺٸݭݪٺٸڊڃٺٸٺݮٺٸݣݒٸڂڒٸݣټٸݖݙٺٺڅݔٺٸٻٸٺٺځݦٺٷڏٿٺٷݭݓٺٸݨڌٺٷڇٻٸډݪٺٺݝټٺٺݘݫٺٸݮݙٺٸٸݗٺٺځݯٸݙٽٺٸݡݗٺٺݘݖٺٸڋٸٺٷڇڌٺٸݔڌٺٷٿڍٺٸݔڎٺٺݙٽٺٷݔݣٺٺڂٿٺٸڒځٺٺٸچٺٸڃݔٺٺڂݚٺٸڒڅٺٺڂڅٺٷڐݞٺٸݩډٺٸݕٺٺٺڂڈٺٸݛٿٺٸټڃٺٺٸݨٺٸݛݙٺٸݕݘٺٸݛڄٺٺݙݦٺٸݯڅٺٷݯڅٺٷڐݗٺٸڌٶٺٷݘٺٺٺٽڋٸڏݱٺٸڍځٺٺٽڎٺٸڍڃٺٸپڑٺٸݐٺٺٺٽݐٺٸݪٽٺٸݯݒٺٸݐٿٺٸپݩٺٸچݜٺٷݫݦٺٸݖٶٺٺپٶٺٺݚڀٺٺݚڂٺٷݩݝٸݕٸٸݨݘٺٸݖڀٺٸݐݣٺٷڒډٺٺݚڈٺٸݱٽٺٺݚڋٺٸݖڈٺٸچݕٺٸٿݛٺٺٿٽٺٸݰݤٺٷݪٷٺٸݖڐٺٺڃݑٸݣڃٺٸݱݝٺٸݰݑٺٷݐٿٺٸݖݭٺٷٺݜٺٸݫٿٺٸڇڅٺٺپݮٺٸݱٸٺٷݪڊٸݚڃٺٸݥݪٺٷݪݤٺٸٶٸٺٸڇݥٸڀݩٺٺٿټٺٸݥݘٺٸݑڍٸݛٸٺٸݞݓٺٸݱڈٺٸݦټٺٸݞݖٺٺٿڅٺٺݙڒٺٺٿݞٺٸݬٽٸپݞٷڏٸٸڇٺٸڀڐٺٷݛٿٺٸݘٿٺٷݜݮٺٷڄٸٺٸݘݘٸݑݒٺٷٻݤٸپٷٸټڍٸٸݒٸٷٶٸٷݤٸٸڋٸڊٸٺٺڅټٺٺٶټٺٺݟڀٸݫڇٺٸݟڌٺٷݣݰٺٸݒڏٺٺݛݭٺٷݣݓٸٺݙٺٷټٸٺٺݜݝٺٸٸݢٸډټٺٸݘݣٸݨڏٺٸݘڎٺٷڍڏٺٷݜݝٺٺڅڍٸݮݠٺٷݰډٺٸځݓٺٷٽپٺٺڅݩٺٷݒڏٺٸݧݣٺٸݓټٺٸډڏٸݮݖٺٺچݤٸݯٷٺٺڅݰٸݕټٺٸݙڀٺٸڐݬٺٷݰڏٸڂڃٺٸݨڏٸݡݱٺٺٷپٺٸݝڑٺٷݝݚٺٸݭݣٺٺځڀٺٺݝڂٺٸݭݧٺٺٷچٺٸݓڒٺٸڊݙٺٸٺݭٺٸڂݒٺٸݧݔٺٺټݬٺٺݝڋٺٷٽݒٺٺݝڍٺٷچݗٸپݖٸݰݞٸڒڄٺٸݔټٸݥڅٺٺٷݮٺٸݨݩٺٺځݒٸٿݢٺٺݝݗٺٸڑݭٺٷݦݥٺٸݮݞٸڊݟٺٺڂٸٺٸٻݥٺٺݞټٺٸڒټٺٷٿڐٺٷڐٶٺٺڂپٺٸݚݩٺٸݮݑٺٸݢݛٺٸݮݓٺٺٸڇٺٸݔݯٺٷݧݚٺٸݛٶٺٸټټٺٸݯٷٺٺݞݟٺٷݟݘٺٷڐݢٺٺٸݦٺٺڇڌٺٸݢݑٺٷݕٿٺٺڂݤٺٺڇڐٺٸݩڒٺٺڂݧٺٸݕݞٺٺٸݖٺٸݜݯٺٺٽݣٺٺڇݖٸٿݔٺٸݪٶٺٺڃټٺٺٽڑٺٷݩڋٺٺݟٺٺٸݕݫٺٸݤݠٺٺڈٽٺٺٽݮٺٺڃځٸپڇٺٸپݓٺٺڈݙٺٺڈݛٺٸݰٽٺٺپټٺٸݤݰٺٺݚچٺٷڂٶٺٸݖݚٺٸݥݬٺٸݪڐٺٸݥٻٸڑڌٺٺݚڍٺٸچݰٺٺڄڀٺٸݞٷٺٸڎݚٸڒٶٺٺݟݑٺٷݙݦٺٸݰݩٺٸݫڏٺٷݢٻٺٺݟݗٺٸݑپٺٺپݫٺٸڎڍٺٸݱٶٺٸݑڂٺٺپݖٺٺپٿٺٸݗټٺٺڄټٺٸڎݓٺٺٿٻٺٸݑډٺٷڋݨٺٺݠݛٺٸݱݚٺٸݦٷٺٸٷٽٺٷڋٺٺٸٶڊٺٺڄچٺٸڀڇٸڐݞٺٸڀډٺٸڍڄٺٸݫݮٺٷٻڑٸٺݩٸٸݪٸٸݓٸٻٽٺٺڀݛٺٸݬݟٺٺڀڀٸٺڀٺٸݟݝٺٷڌڑٺٺڀݙٺٺڊڄٺٸٸپٸٺڂٺٺٿݥٺٷټڇٺٷټݠٺٺٶٷٺٸځݠٺٺڊډٺٷݰڄٸݠٿٺٸٸݥٺٺٶڌٺٸݧݙٺٺڅڌٺٸٸݐٺٺݜݥٸݘݑٺٺڀݩٸݕٸٺٷݤݰٺٷݬݨٺٺٶݓٺٸݓٽٺٷݤݔٸڌڀٺٺݢٷٸٿݨٺٺڅݱٺٸݓݔٺٷݡٿٺٷݭٷٷپٸݖڏٺٸݭډٺٺٷٿٺٺݘٽٺٺݢݛٺٺچځٺٷݝݡٺٺݢڇٺٺݝݛٺٸڑڀٺٺٷډٺٺݢڌٺٺٷڍٺٸٺݛٺٷݰڄٸݣپٺٸݚٶٺٸڊڌٺٷپݪٺٺټݖٺٷٿݠٺٸݔټٺٸٻځٺٸݮڀٺٸٻݛٺٺچݮٷڂٺٸٻݞٺٷٿݘٷڀٺٺڇٶٺٸٻݢٺٸݢٺٺٺٸٽٺٷݦݓٺٺٸٿٺٸڋپٺٺݣځٺٸݔڑٺٸڃڑٺٷٿݔٺٺڌڅٺٷݮݦٺٸڃݭٺٸڋݞٺٺڇݛٺٸݮݰٺٺڌڋٺٸݕٶٺٷڈٿٺٸݛټٺٸݩݢٺٺݞݢٺٷݧڏٺٸݛݘٺٸݢݒٺٺݞݦٺٸݩڑٺٸݛݝٺٺڇڒٺٸڋݗٺٺڂݖٺٺݙݪٺٺڇݮٺٸݤڌٺٷڊٽٺٸݕڎٺٺڑݩٺٸݕڐٺٺٽݩٺٷځڇٺٺݚٺٺٸݯݓٺٸچݙٺٸݪݘٺٺډݥٺٺڀچٺٺݟݘٸݧݪٺٷٷݫٺٺپٸٺٸڅٿٺٸچڌٺٸٿٷٺٷڊݚٺٸݰځٺٸٿټٺٸݥٶٺٺݟڌٺٸٿݘٺٺڈݥٺٸݥپٺٺپݟٺٷٺݭٺٺݟڒٸڂٺٺٸڇټٺٺݟݒٸݙٽٺٺݠڇٺٺݟݰٺٸݑٽٺٸٶݤٺٸݞݖٺٺڃݗٺٸٿݕٺٺݛٷٺٷݩݟٺٺڄٺٺٸڇڌٺٺڄټٺٸݞݥٺٷٸٸٺٺݠڃٺٸڇݩٺٺݛڂٺٺډݝٺٺڈݮٺٷٻٷٺٺݠݟٺٸٷځٺٸݑݐٺٺڎݨٺٷݱٺٷٸٷڀٺٺٺٷٺٺڄݰٺٺݡڇٺٸݬٺٸݑݬٺٺڏٶٷݡٸپڑٷٸٷݞٺٺڀݙٺٸٸڃٺٺݦټٸݐݖٺٸݱݫٺٸپݔٺٸݟݟٸݑݘٺٸݠټٺٺݜڈٺٷڍݣٺٺڀڍٺٺٶݥٺٺڏڋٸݔݠٺٸݘݱٺٺݜݨٺٺٶڐٺٷڅݧٺٺݦݨٺٺڀݒٺٸݧڎٺٸٽݦٸݯٷٺٸڐڒٺٺڋٺٺٸٺݮٺٸڂݮٸݡݨٺٺݝٺٷپٺٸڊڒٺٺݧٺٺٺݢݙٺٺݝٿٺٺݘٿٺٺڐپٺٷݭݚٺٸٺݩٺٸڑٿٺٺځڅٺٸڑݘٺٷٽڏٺٸڅݠٸݛچٸݯٿٺٷپݤٺٸݔٶٸڂڃٺٺٷڑٸݣݝٺٸݡݦٺٺݝڒٺٷڏڃٺٸڊڒٺٸݨݨٺٸݮځٺٷݞځٺٷٿٽٺٸݡݓٺٸڑݭٺٺٸٸٺٸݮݞٺٸݢٷٺٺڌٽٺٺݞٻٺٸݢٽٺٷݞݨٺٺڑٺٺٺٸڃٺٺݞڀٺٺٸڅٺٷݮڐٺٺݣݟٺٺݨݙٺٺڌݡٺٸݢڋٺٺڇݞٺٺٸݤٺٺݨݟٺٸټڂٺٺݨڊٺٺڇݤٺٺڑݣٺٺٸݐٺٺڌݓٺٺݨݦٺٺٸݮٺٺݞݑٺٺݨݩٸݦݔٷݜٸٿپٸڊڏٺٸڌپٺٺݐڑٸپٽٸٺٺٸٺټٺٷٻڋٺٸٷڍٸٷݮٸڊڄٷپٷڋٷڐٷڏٺٷݕݕٺٺٺٺٺٺٺټٺٺٺپٺٺٺڀٺٺٺݙٺٺٺڄٸٸݱٺٷٻڍٸٸݙٺٺٺټٷٶٷݝٷݟٸٸݰٺٺٿݓٸپٽٸٷݮٸݫڇٷپٷݣٷݝٺٷݨݚٺٺٻڌٷٺٸٷݒٺٺٺݞٷٶٺٺٺݠٷݑٺٸڈݜٸڂݔٸټݣٸٸٺٸٸٶٸٽٶٺٷٻڍٸٻچٸټݡٸٺڈٸٷٶٷݯٸٸڍٸٸݦٺٸڀݩٸݜݔٺٺٺݐٺٺٺݬٺٺٺݔٺٺٺݖٺٺٻٶٺٺٻٸٺٷډٺٸٺݘٺٸݛݨٺٸټݯٷݯٺٷٻڅٸٷݑٸݝڊٸٺݝٸٺٻٸټݮٸٷݚٷݔٸٸݣٸݣݔٺٺٻݬٺٸݣڊٺٺٻݮٺٸڅݪٸݠݒٺٺټٶٺٷٷݓٸڃݖٸڏڀٸݢݛٺٺټټٸݮځٺٺݢٺٺٸڇٻٸٷٸٺٺټڀٺٺݬٷٺٺڊڌٸٷپٺٺټڅٺٷٽٺٺٺټݟٸݰݮٸݢݓٸٷݞٺٺټݟٸڎݦٸډݒٺٺټڀٺٷݰݤٺٷڑڄٺٷپٻٺٺݰپٺٸݘݐٺٺټݟٸپݰٺٷݪݯٺٺݖٸٺٷڎݘٺٷچٽٺٸڂݚٸٿڀٺٺݖٽٺٺټݝٺٺݰڃٷٻٸݛٸٷټٸډٽٺٺټڎٸݦڈٸݣڀٺٺټڒٺٺٷٸٺٺٷڌٺٺڐٶٺٸݧݔٸڌݝٺٺټڃٺٺٽٶٺٺٽٸٺٺټݢٸڂٽٸځٺٺٺٽٽٺٺٽٿٸݠݑٸځݓٺٺٽڂٺٺٽݛٷٻٺٷݗٶٺٸݞٻٸݘݓٺٷݠݥٺٺٽڊٺٸݯڋٺٺݙݒٺٺڑݓٺٺݤٻٺٺڈٷٺٷٷځٺٺڃٷٺٸپݤٺٷݘڊٺٺڒٸٺٸݪٸٺٸݯݕٺٺݜٷٺٺٽݗٺٺڅٶٺٺݟڃٺٸݪڇٺٸݖټٺٺپٻٺٺډټٺٺݤݣٺٸݖڂٺٺݟݢٺٺݪٻٺٸݗݝٺٺڒڊٷٸٺٸٿݚٺٺٽٸٺٸݗݘٺٺڃݧٺٸٶڂٺٺݩڐٺٷݐٸٺٸݖڑٺٷٸݕٺٺڒݑٺٺݚݮٺٸݖݔٺٺݚݖٺٺݠٸٺٺڄٶٺٸݑݚٺٷڒݣٺٺډٽٺٺٿٷٺٸچݐٺٸݗپٺٺډݙٺٺڎچٺٸڀپٺٸݥݱٺٺݥډٺٸݞݒٺٺݪݙٺٷݪݗٺٸڀݜٺٸڏٽٺٷݫٻٺٺݛݠٺٸݦݘٺٸٷڋٺٷڌݛٺٷݑݥٺٺڅݛٺٷڄٿٺٺݪݮٺٺٿݤٺٺݪݥٸڄݕٺٷڍٷٸپٽٸٺٻٸټݑٸٺڋٷٷٸټڑٸٷڋٷݙٸٷپٷڊٸٽݓٺٸٸڃٺٺݪڌٺٻٶٽٺٸݟڑٺٺڀڂٺٺڀڀٺٺڅݞٺٷڅٿٺٸځڌٸݢٿٺٺݑټٺٺڏڊٺٸڐݜٺٺڊݱٺٺݦڎٺٸډݡٺٷڍݗٺٺݫڅٺٺݦݐٸڊݥٺٸݙٽٷݘٺٸٺڀٺٸݜڈٺٺٷٻٺٷݰڎٺٸپݗٸڊݓٸݨݦٺٺݝٽٺٺڋڃٺٺٷݘٺٸݭݤٺٺݘݘٺٺٷݜٺٺݧځٺٺݑݖٺٺݧݚٸݰټٺٷچݑٺٸٺڄٺٷچݭٸڌپٺٻٸڌٺٸݨڈٸݖݞٺٺݡڌٺٸݔټٺٻٸݬٺٺچݓٺٺݒچٸٿڋٺٷٿڂٺٸڑݓٺٸڃݜٺٸݔڇٸڋڍٺٺݒڍٺٺݙٻٺٺڇٽٺٺݒݨٺٸݩپٺٺݨټٸڎٷٺٺڑپٺٺڂݘٺٺݒݭٺٸݔݧٺٺݙݛٺٺݨݛٺٺڂچٺٺݨݞٺٺڌݧٺٺڂډٺٺٸݧٺٺݣݪٺٸڒڐٺٸټݟٺٺݭٿٺٺڇݐٺٸݕڈٺٷݨٷٺٷݱټٺٸݩݕٺٺݤٷٺٺݙݔٺٺڈٶٺٸݤڋٺٺݱݕٺٸچټٺٷٷڅٺٺݟٻٺٺݤݘٺٺݙڒٺٺڃٽٺٺڈٿٺٻٻݧٺٺڍچٺٺݟڀٺٷݗڑٺٸٸڌٺٸپݖٺٺپٻٺٸݝڍٺٻٶڃٺٺݩݞٺٺپݘٺٺݚډٸځٷٺٺڃڋٺٸݪݩٺٺڈݦٺٻٶڋٺٺڈݨٺٺݚݨٺٸٶڃٺٸݥڅٺٺڍݗٺٺڃݒٺٺݥݣٺٻٶݫٺٺډٶٺٺڎټٺٺڒݰٺٸڎݦٺٷٺڅٺٺݪٷٺٸڇݡٺٻٷٷٺٸݪݦٺٸڀټٺٷٷݙٺٺڎݞٺٺݐٿٺٸݞٸٺٺڄݚٺٺݚݭٺٸݫݨٺٻٷڄٺٺڄڈٺٺݠݣٺٺݛݡٺٺڅٷٺٺݡڀٸݫݠٺٷݬٶٺٸݒڏٺٷڍݛٺٺډݒٺٷݤݝٺٸٸݘٺٸݘڂٺٺڀڂٺٺٶچٺٷݫڂٺٷݛݙٺٸݱڑٺٸڏڈٺٸݛݧٸڂڒٸټݙٸٷݯٸټڈٸټݭٸٽݕٸٷٿٸٷٺٺٸݬݟٺٺڏٸٺٺݠڏٸٸڇٺٺݑٸٺٻٸڀٸݠٿٺٷڈٸٺٻٸڃٺٺڊݦٺٺݑپٸݔڏٺٺݑڀٺٸݘݮٺٺٶݧٺٷڅݢٺٺݜݑٺٸډݥٺٸٺٻٸݐځٺٺݦݒٺٺݦڍٸݠݔٺٺݜݗٺٷݖݬٺٸڊڇٺٺݧٶٸپٿٺٻٸݓٺٺݑݪٺٺٷڂٺٸݭݥٺٺݘڂٺٸݭݨٺٺچڅٺٺݢڊٺٺݘݞٺٺݖݟٺٸڑݜٸڌپٺٷڏټٸݖڅٷځٸݰݞٸپڍٺٸݔټٺٻپڇٺٻٺچٺٷݮٺٸݘݘٺٷݞڅٸٿݢٺٺڇٶٸݙݠٺٺٸټٺٸݔڋٺٻٺݦٺٺڌڀٺٷݮݡٺٺݬݩٺٺڌڄٺٺݙڀٺٺݣڇٺٺݞڃٺٻٺݯٺٺڇݜٺٻٺݱٺٺݒݗٺٺڂݞٺٺݭٷٺٸڒڍٺٸݯٿٺٺڇڎٺٺݭٽٺٺݨݥٺٺٸݭٺٻٻڀٺٺݣݱٺٺڑݑٺٸݕݕٺٺݱݒٺٺڂݯٺٺڍټٺٺڈٸٺٺڒٶٺٻٻݣٺٺٽݒٺٺڑݯٺٺݟپٺٸݯݖٺٺڒٿٺٺڍڄٺٺݚٿٺٺݚڂٺٸٺݚٸڀݣٺٸڍݬٺٺڍڋٺٺپپٺٺݤڍٺٻٶݜٺٷݪڎٺٷڂځٺٺټݘٺٻٶڊٺٺݩڍٺٻٶڍٺٸڇٸٸڑݗٺٷڂݤٺٺݩڒٺٸڐڐٺٺٿݙٸݙڎٺٺݥٺٺٺݩݔٺٸٿݒٸڂݕٺٸڎݥٺٸݱٷٺٺݐٶٺٺپݱٷٸٺٺڎݙٺٻڀډٺٷڃځٺٻٷټٺٺڍݒٺٺٿپٺٸݱݛٸڄٺٺٻڀݫٺٻٷݚٺٺډڊٺٻٷڅٺٻټݰٺٻٷڇٺٷٻڋٺٷټڋٸٷٸٸٽݦٸٻڈٸٻݥٸټݜٺٺڏٶٺٻٷڍٸݪݱٺٺݜټٺٺڀݚٺٺݡځٺٻٽٺٺٸݟڏٺٸٸٷٺٷݫݥٺٸݬٿٺٺٿݐٺٷٻݕٺٸڈڇٸڐڐٸٷڀٺٻٽڂٺٸݒݨٺٺڏڄٺٸٽݤٸݠٿٺٻٸݙٺٺڏڈٺٺڀڎٺٸݬݖٺٺٶڐٸپݔٺٺڏڎٸځٺٺٺݦݧٺٸډڌٺٺڅݒٺٺڏݪٺٸٻٷٸݯٷٺٷڎپٺٺݑݡٺٸݧݑٺٷٷݭٺٸݓݯٸڂڒٺٷٽݫٺٻٺݜٺٺݫݨٺٸݙݟٺٺڐٽٺٸٺݦٺٺݧٿٺٺݑݮٺٺٷڇٺٺچݝٺٺݢڋٸݰټٺٺڏݖٺٷݘݕٺٷݝݔٺٷݜݮٺٷپڐٸݙڃٺٸݔٸٺٷڏٿٺٻٺݚٺٺݒځٺٷݭݯٷݘٺٻٺڅٺٺݬڄٺٺڐݨٺٻٺݞٸݝځٺٺݧݓٺٸڑݭٺٺچݗٺٷݔڀٺٻٺڍٺٻٿپٺٺݙٺٺٺݨٶٺٺݙټٺٻٺݨٺٺݣݚٺٺڑٽٺٻٿڅٺٺڇڂٺٺڑځٺٻٿڈٺٺݨݚٺٺݬݰٺٷݮݖٺٺݣڎٺٸݕٻٺٻٻٺٺٺڌݩٺٸڒݦٺٸڋݭٺٻٻپٺٻٿݪٺٺݨڑٺٸݤڄٺٸݯݡٺٷݨݧٺٺٽݤٺٺݤٺٺٻٿݰٺٺݱݮٺٺڃٶٺٻٻڊٺٸݪټٺٺݤڀٺٻڀٺٺٻٿݱٺٻٶٺٺٻڀٿٺٷݩځٺٻٷݡٺٸݦڂٺٸݖٻٸڑٶٺٺݤݠٺٻڀݛٺٷݙټٺٺݩݝٺٻݜٷٺٻټٶٺٺݤݦٺٻټٺٺٺڍݩٺٸݰډٺٺڍݫٺٸڎݖٺٺڒڎٺٻټٿٺٸٿڊٺٺڍݖٺٸٶݝٺٷݢٷٺٻټݒٺٻڀݭٺٸٿݑٺٸݖݰٺٻڀݖٺٺݥپٺٺپݯٺٻټڊٺٻځٸٺٻݘٻٺٻټڎٺٸݥݮٺٻݘپٺٻڅځٺٷݢݪٺٻٷٿٺٸڀݙٺٻټݒٺٺڎڎٺٺݪݝٺٸݱݣٺٷڃݪٺٸڏځٷډٺٷٻڑٷݔٸٸڎٸټݕٸټٻٺٺڎݖٺٷݣݡٺٻݘڑٺٷݑݟٺٻݘݐٺٻٽټٸݫڑٺٻٽٿٺٸݱݕٺٻݘݕٺٺڏڀٺٸݐڅٺٺڅٺٺٷݣڇٺٷݫݯٺٺݡڈٺٸݧپٺٸݠڌٺٺݡڍٺٸډݘٺٻٸڄٺٺڀݧٸݮݨٺٺݑݘٺٺڏݣٺٻپٻٺٺݡݔٺٺڏڒٺٺڊݰٺٺٶݯٺٻپځٺٻٸڏٺٸڂݬٺٺݰڈٺٸݓچٺٸٻٺٺٺڋٿٺٻݙݮٺٸݡٷٺٻٸݕٺٺڋݜٺٻڃٶٺٺځݚٺٺݫݯٺٺٷڈٺٺچڇٺٸݙݬٺٺݱټٺٺݧݞٺٺݢڐٺٺݘݤٸڂٽٸݖچٺٻڃݛٸڋݞٸݖݡٺٻݚچٺٸٻٿٺٻݚډٺٺڐڐٺٺٷݰٺٷٿٽٺٻٺډٺٺٸٷٷٿٺٺݞٶٺٻݚݩٺٺڐݰٺٻٿٿٺٻݚݬٺٻٺݧٺٻٿݙٺٻٺݩٺٸݢݘٺٻٿڄٺٺڇݘٺٺݬݒٺٻٿڇٺٷٿڑٺٻٺݖٺٻݛٻٺٸڄٺٺٺݭٶٺٻٻٸٺٺݨډٺٸݕپٺٺڑڋٺٺڌݑٺٷݯځٺٸݕڃٺٸټڊٺٺݙݨٺٺݞݬٷٷٺٺݭݛٸڀݜٺٺݭڍٺٺݓݦٺٺݓڑٺٺݓݪٺٺݯڂٺٸڄݐٺٷݕڒٺٷڄځٸٸٷٸٷݘٸݕݓٷݫٷݥٸٷڄٸٷݟٷݡٷݣٸݨپٸٸݬٺٷݯݱٸٺٻٸٽݖٸټݒٸٷݡٷݓٺٺٻپٸپٽٺٺٻڀٸٸݫٺٺٺڒٺٺٺݑٺٺٺݭٺٺٺݕٷٷٸٺݞٺٷٻݤٸٽݭٸٸݮٸټݛٸٽٽٸٽڀٸٷݚٸٷݓٺٷڄځٺٺٺٻٺٺٺٽٺٺٺٿٺٺٺݘٺٺٺݚٷݛٺٺٺݜٺٷټڋٸٸٸٸٽݕٸٻډٸټٷٸټٸٺٺݯپٺٺٻٺٸݯݭٸٺځٺٻٷݨٷٶٸٸٶٸٷڀٷٻٷڄٷڏٷݐٸٷڀٺٺٻڍٺٺݔݡٺٺݔڌٺٺڊپٺٸݟݠٺٸٶݭٺٺݕڏٺٷݠڅٺٷڅݚٺٺٻݖٺٺݕݫٸݡݫٸݚݰٺٸݨٺٺٺݯݖٺٷڅݛٺٺݖٶٸڀڈٺٺݖڐٺٺݒٷٺٺټݚٺٺݖݬٺٺݰٿٺٸپٷٺٺټݡٺٺݖݔٸݤݮٺٺݱݞٺٸݜڄٺٺټٿٺٷٺݗٺٸݡݝٸݯݘٺٷپٷٺٻڋݟٺٺݰڌٸڀݔٺٺځݦٷݩٺٺټݥٸڃڀٸڊݛٺٺݱٻٷټٺٺټݫٷٽٺٸݠݓٺٸٺڇٸڊݫٺٺڐڌٺٷڈپٺٺٽٷٸݣٷٺٺټڋٸڏݟٺٺݗݝٺٺٽپٸڋݧٺٷڀڐٺٺݱݢٺٸځݱٺٷݗٶٸݗٶٺٺݱڐٺٷٻڀٺٺݱڒٺٻݛڈٺٺڍٸٺٸٶڎٺٷݗݘٺٸݯݔٺٻڄڍٺٸڍݞٺٻڀٸٺٺڃٻٺٻڄݣٺٺݙݬٺٻٶٻٺٻٶپٺٻڀڀٺٻٶٿٺٻڄݰٺٺپٻٺٻݜٶٺٺپڀٺٷٸټٺٺپٽٺٺݩݟٺٺݥݚٺٺݤݧٺٷڊݤٺٻڅپٺٻټټٺٻڀݤٺٷݩݰٺٻݜڃٺٸݐݗٺٺپڍٺٻټݙٺٻڅݞٺٻټݛٺٺپݩٺٻٶݬٺٺڒݕٺٻٶݔٺٺڒݱٺٻٶݰٺٷڃټٺٺݠپٺٸݑچٺٸٶݖٺٻݜݐٺٺݛٿٺٻڅݬٺٺݛݘٺٻټݪٺٻݜݕٺٻݤݦٺٻݜݗٺٺݠڋٺٸٷڅٺٺډڍٺٻٸټٺٻځݪٺٻچڃٺٷݑݨٺٻچݥٺٻݙٸٺٷݖݛٸڋݞٸٷݤٸٸڃٸٻٸٸٽݗٸچݔٸٸݓٸٽٷٸٻݫٸٽݧٸڐݩٺٷݣݛٺٸڈݢٺٻٽٸٺٸݟݥٸٸݬٺٻٽݙٺٺݜݙٺٸٸٷٺٻٽݑٺٸٸݣٺٺڀݢٺٸݧڀٺٻݙڂٺٺݫٽٺٻٸݜٺٸݭٺٺٻچݕٸݔݠٺٺڊݓٺٻٸݠٺٻݙڋٺٺݡݰٸݨݦٺٸٺپٺٸݭځٺٻڂڐٺٸپٺٺٺټݓٸڊڑٺٸډݯٺٸڊݡٺٻپڈٺٺݘپٺٻپڊٺٻٸݗٺٺݝݚٺٺځڄٺٻڇݠٺٻݚٻٺٷٽڏٺٺݝډٺٺݘڋٺٻڏڅٺٸٻٸٺٸڊڍٺٷݦٿٺٻپݯٺٻڇݒٺٺٷݬٺٻپݗٺٻݚݡٺٻݞݰٸݔݗٺٻݚڏٷپٺٻٿټٸڂڎٺٻڃݪٺٺݣپٺٺݬݦٺٸڃݥٺٸݮڐٺٻٿݚٺٻڃݰٺٻݟݛٺٺڑڀٺٸݩڄٺٻڄٺٺٷݔݔٺٺݨݜٺٸݯٸٺٺݣݦٺٸݛپٺٺݓٸٺٻݟڎٺٺݭٻٺٻݟݧٺٺݙݥٺٺݣݔٺٺڑڐٺٻڈݫٺٺݭݙٺٷݘٺٺٸڒݔٺٺݗݐٺٷݨڑٺٻٿݯٺٻٻݞٺٻݣݬٺٷݠݨٺٻݛڎٺٸݯݪٺٻٶٶٺٺݤݙٺٻڄݐٺٸݤڏٺٻڍٺٺٺݐݱٺٻݛݕٺٺڃݚٺٸݰپٺٺڈڇٸڀݐٺٻڀݝٺٻٶڄٺٻڍڂٺٻځټٺٺڃݢٺٺپݜٺٻݜٿٺٺݟڐٺٸݥځٺٺڒڏٺٷݟٸٺٻݤݣٺٻڅچٺٷݙڑٺٻځݚٺٻݤڐٺٻټݝٺٻٶݭٺٺپݭٺٻٶݕٺٺڎڀٺٻٶݗٺٻݜڑٺٷݚڀٺٷݪݨٺٻݜݫٺٻٶڌٺٻڎٸٺٸٷټٺٺپݧٸݗڂٺٻڎٽٺٻځݝٺٻݥٿٺٻټݗٸݧݩٺٺډݧٺٻڎݫٺٷٻݝٺٻځݭٸݝٽٺٺݡٽٺٷݣݨٺٷٻڍٸٷٺٸٻݣٸٺݰٸٷٷٸٺڂٸټݢٸٺڏٺٺݐݭٺٸݱݧٺٸݦݞٺٺڏٽٺٺݦٿٺٷݣݡٺٺݦݙٺٸݱݒٺٺڅځٺٻٽٽٺٷݬٺٸݔٸٺٻݙپٺٷڍڋٺٻٽݔٺٻݦٻٺٻچݬٺٸݒݗٺٻٸݝٺٺڊݐٺٷݜݤٺٻپٺٺٷݜځٺٻپټٺٺڀݭٺٷڅݬٺٸݨڇٸݯٷٸݚݭٺٺݜݗٺٻٺټٺٺݫݤٺٺݧݜٺٸݭݞٺٻڇݘٺٺڋݘٺٻڂݕٺٻݞݛٺٺݑݒٺٸݨټٺٺڐڀٺٻݦݐٺٻڃٺٺٺځڇٺٺݫݣٺٺݒٸٺٺݢڏٺٸݨݞٺٷݝݱٺٺݝݦٸݣݝٺٺٷݪٺٸݨڍٺٸݧݰٺٻٿٶٺٺٷݱٺٸݮݛٺٷݞݜٺٻٺڋٸݤݘٺٸڑݱٺٻڐݛٺٺݒڎٺٺݨٷٺٺݒڐٺٻڈڀٺٻݚݕٺٻٺݫٺٻݚݗٺٻݟݜٺٻڄٷٺٻڈڇٺٻٿݠٺٻݟډٺٺݣڍٺٻڈݢٺٻڐݐٺٻٿݥٺٻڈݦٺٻٻٽٺٻڈڒٺٸڒݐٺٺݣݰٺٺݙݩٺٻݛݞٺٺݙݓٺٸݯڍٺٺݱݭٺٻٻڈٺٻݣݓٺٸݪٻٺٻڑݙٺٷݗڈٺٻٶٷٺٺݙݗٺٻݤٶٺٻڍٸٺٸݯݗٺٻٶټٺٷڌٿٺٻڑݠٺٻڀڂٺٺڍݡٺٻݜٺٺٻݤڀٺٻڀݜٺٻݨڐٺٸٶٸٺٻڀڊٸݚڀٺٻڀݣٺٸݰڋٺٺپݠٺٻٶڎٺٻݨݯٺٸݑٷٺٷٸݕٺٻڒڇٺٷٿݣٺٻݜݠٺٺݠٷٺٻڒټٺٻڍݑٺٻڒپٺٻڍݭٺٻټݤٺٻݩݘٺٻڍݱٺٻټݧٺٻٷٽٺٸݱݙٺٺݪڀٺٷڊݟٺٻݩٷٺٻڒݠٺٻټݕٺٻڒڋٺٻݘڈٺٷڌݡٺٺڅٻٸپٽٸٻپٸٽډٸټٸٷݞٸټݣٺٻچڃٺٻڂټٺٻٸٻٺٺڒٽٺٻٽٷٺٻݩڐٺٻݥݭٺٻڎݖٸپݞٺٻݘݗٺٺٶٻٺٻݥݗٺٻݐڅٺٸݙٺٺٻڂڀٺٷپٷٺٻٽݕٺٸݘڑٺٻٽݱٺٺڅڏٺٸٸݓٺٻݦٿٺٸݘݫٺٻڂݠٺٸݧڍٺٻٸݢٸڀݮٺٻٸڍٺٻڇټٸݰټٺٸݧݬٺٻݦڌٺٷڏڅٺٻݞڂٺٺٷڀٺٷݓٿٺٻڇݜٺٺݑݭٺٻݞݞٺٻݚٸٺٻپڏٺٸݓݒٺٷݭڌٺٷٽڑٺٺڏݱٺٸݙٺٺٻٺٿٺٻݮݬٺٸٻٸٸݩڍٺٷݦٿٺٷݦݘٺٻڐٺٸڌڍٺٷڏڅٺٻݧٽٺٸڑݐٺٷڏڊٺٸݡݖٺٸݨݭٺٷٿݙٺٷݔڀٺٷݦݨٺٻݫڒٺٻٿڀٺٺٸڀٺٺڇپٺٸٻݫٺٻڈڃٺٺݒݫٺٻݧڌٺٺٸݟٺٻݬٸٺٻڐڏٺٻٻٶٺٸݩݡٺٻݟݣٺٻڐݑٺٺڂݢٺٻٿݧٺٺݣݬٺٻٿݩٺٻݟݐٺٻݒݚٺٻڈݬٷݛٺٷٻݚٺٻݠٸٷݑٸٷݪٷݔٺٻݡټٺٺݭݓٺٻڊٿٺٺݭݰٺٻڊݙٸٸݗٺٷټڋٸٽݱٸٽڂٸټٷٷٸٸټڀٺٸڌپٺٷٻݤٸٺٺٸٺݐٸٺݒٸٷٻٸٺٺٸټݔٸٽڋٺٻݖݡٸٷݓٸٷڂٺٷڌݨٺٻݡڊٺٺݕڀٺٻڊݥٺٻڊڐٺٻݡڒٺٻݡݫٸٷٽٷٺٷݡٸٷݐٺٻډڒٺٺݕٻٺٻډݬٸٺٻٺٻٽݞٺٺٻݚٺٸټݯٺٺٻݝٺٻݬݢٺٺٻݭٺٸٸݧٺٺٻݕٸٿݤٺٺٻݱٸݡݙٸڀچٺٷٷݙٸڒݮٺٺټٻٺٺټٽٺٺݢٺٺٺݖݦٺٺݰٺٺٻٸݨٺٻݕڃٺٺټڄٺٺݰݭٺٺټڈٸځݢٺٻڋڋٺٺټݟٸݰپٺٻݢݰٺٺځݟٺٺݱٺٸݛٸٺٺڋݐٺٺݘڊٺٻݙݑٺٸٽݯٺٺݗٿٷٿٺٺݱݘٺٻݣݙٸݜݮٺٺټݢٺٺݰݖٺٺݗٶٺټٶݡٺٷݜݯٺٻݣٸٺټٶݤٺٻݪݯٺٺݧٶٺٷپݡٺٷڏٿٺټٶݪٺٺݱݚٺٺݰݔٺٷٸݡٺٻڋݥٸڀݥٺٷٽڌٺٻڌݡٷٺٺٺٽݜٺٸپٿٸݛݣٺٻݣڎٺٺٽݠٸݕݓٷݡٸݝڅٺٷݨٻٸپٽٸٷڋٸپٶٸٺݦٷݚٸټݰٸٷٶٸٷٸٸٷڐٷڇٸٻڎٺٷٻݤٸٸݚٸٷڎٸݘݧٸݝځٺٷݛڇٸݙݤٸٷݨٸٽڀٸٸݬٸٽݒٸڍٶٸټٸٺٻݗپٸڂڒٸٸݝٸٷڑٷپٺٺٺٶٷڏٸٸݑٸݑݔٸپٽٸټݨٸٺݢٷݚٸٷݡٸٻڊٸٻپٸٷڒٸټݞٸٷݪٸٺڀٸٷټٷݫٷڍٸټڀٸټݘٸٺڅٸټݟٸټپٸٸڇٸٽݢٸٷݞٺٸڀݱٸټٸٸٻݣٸٽݝٸٻٶٸٽڀٸټݖٸٽڅٸٺݥٸٽݞٸٺݫٸٺٽٸٷݣٸٸݪٸٻڑٸٷټٸټڄٸٽݜٸٺپٸٺٶٷٽٸٺٺٸٽݕٸٷݫٸٸڎٷٸٸټݦٸٺݖٸٺݚٸټڋٸٺٽٷݱٸٻٻٸٺݨٸٸٷٸٻډٸٽݪٸټڎٺٷڇݝٸٷٸٸٻݜٷݜٸٽݛٸٺٿٸٽٷٸٽٶٺٸٷڍٸٸٶٸٷڏٸݚݰٸٷݡٷݖٷݟٺٸڀݬٸݙڍٸټڋٸٽݢٸٸٸٸٽݮٷډٸټݚٷٶٸٸڅٺٸٷݤٸٷٶٸٻڌٸٻݡٸٸڎٸٺݞٸٽڈٸٸݖٸٻٶٺٸٷݤٸٺٷٸٺڋٸٸٶٸٸټٷڎٸټڎٸٺٽٸٸݚٺٻڊڎٸٺٽٸٺݛٸٻٽٸٽݒٸٸڌٸٻډٸٸټٸٽٸٸټݘٸٻݭٺٺݮٿٷٶٸٽڒٸٸݔٸټݰٷپٸٽݟٸٷݝٸٺݣٸٺٶٸٷݞٸٺٿٸٽݙٸټڏٺٸٷڍٷڏٸٸټٸٺڄٸٽݙٸټڑٸٸݱٸٺٿٷڃٺٷٻڑٸټڀٸٷٺٸٸڄٸٽټٸݝڇٸپٽٸٽڍٸٸݜٸٷټٸٽݙٸݡݡٸٸݚٸٷݢٸټݡٸټڂٸپٸٸٸݒٸٺݐٸٸٺٸٻݡٸٽڋٷڍٸٻݬٸٷݞٸٻڂٸٷݭٸٽڀٸټڒٸٸݰٸټݙٸټݡٸٽٺٸٷݕٸٻݔٸٺݪٸٷځٸٺݕٸٻڏٷݒٸٺݘٸٽچٸټپٷٶٸٺݡٸٺٸٸٺڌٸٽݡٸٽݐٷݩٸٺݞٸټݚٸٸݭٸٽڄٸٷݱٸٸݟٸٽڂٸٸٽٸټݖٸٷچٸٽچٸٷݠٸٻݛٸټݖٸټݠٸٽݪٸٷݨٸٻݛٸٻٺٸټپٷڇٸٻݰٸٺݖٸٷٿٸٻپٷٺٸٻݪٷݑٸٷݧٸٻٺٸٽټٺٷټݢٸٸݓٷٽٸڌچٸݜݛٸݙݔٸٻݘٸٺݐٸٷݐٸٷݪٺٷټٻٸٺٶٸݜݘٷټٸڍݑٺٷݑݘٺٻݡڎٸٸټٷڏٸٽݭٸٽٷٸٽݞٸٽٽٸټݧٸٺڐٸٺڌٸٽݚٸٸݦٺٷڑݖٸݠݒٸٷٶٺٺڊڊٸډٿٺٷٶݝٸډٽٺٷݞݚٺٺݯݮٸڊڃٷٿٸٷپٸڀݠٺٺݖڏٺٺݡݫٺٸٺݔٺٺݗٸٺٷݭݘٸٷځٸݠڌٷٷٷݓٷݐٷٸٸݧڀٸڀݫٺٷډڅٸڏݮٺٷݰݛٺٷݞڃٺټڀݢٺٷڅݬٺټڀڎٷݯٷٿٺٻݱݠٺٺݖڎٺٷٺݗٺٺݖݧٺٺݰڈٸݧڀٺٻݢݬٺٸڅڍٺٺٺٿٸݰډٷڈٷݠٸݠڄٷݢٷڎٸڀݛٺټځݚٺٻݗݠٸڀݥٸݨݒٺٺݖڐٺٺݝډٺٷٶٸٺټݘݢٸڎڐٷݢٺٻپٿٺټڀݦٺٻڊڑٸڍڃٺٻݱݰٷݖٺٻݑݙٺٸٺݝٺٺݫݦٺٷپٻٸٷٿٺٺݝݡٸپڈٷڀٸڍݥٸپٿٸݛݬٷݣٸݖڈٺٷٿݠٸپݣٸڃݭٷځٸݥٿٺٸݙټٷٿٺټݙٽٸݯٸٸݠݬٺټݙڀٺټٷٻٸݡݭٸڑݛٸٷپٺټݙݜٸپڍٺټݙڈٺٸڊݡٺټڂڋٷٿٸݩڄٺټݙڏٸځݓٺټݙݨٺٷݭڄٸځټٺټݙݫٺٷݖڊٺٺٻݰٺټڂڀٺٻٺټٸڊݭٸڎݘٸݢݛٺټڃٸٸپڒٺټڃٻٺټڂݡٷڒٺټݙڌٺٺڊݣٺټݚڀٷٷٺټݚݙٺټڂݐٺټݙݒٺټݚݞٺٺݱٽٺټڂڂٺٺټٺٺټڃݤٸپݚٺټݚڏٺٸټݦٺټڃڑٷٿٸݥٶٺټڃݫٺټݚݓٸݜݔٺټځڃٺټڃݕٺټݙٿٺټٿڐٺٷٻݚٺٸٽݯٸڒڄٺټݚٷٺټڂچٷٷٺټڄٻٸپٽٺټڃٽٺټڀݓٸݘݜٺټݙڐٺټݙڒٺټݛݙٺټڃڅٺټݙپٺټڂݮٷٽٺټڀڎٺٷٽݫٺٷڈٸٺټڄݡٺټڃٺٺټڂډٺټݛټٺټڂݣٺټݚݢٸݧٻٺټݛݩٺټݚڃٺټݙټٺټڃݝٺټݛݜٺټڀݢٺٸٽݕٸڎٶٺټڅٷٺټڃݥٺټڅٺٺټڄڎٺټڄٽٺٷٸٿٺٷݪڏٺټڃݬٺټڄݐٺټݚڄٺټݛݛٺټڄݮٸڒݥٺٷٽݑٺٻݢڇٺټڄٸٺټڂڇٺټݜݠٸݙٸٺټݛٽٺٷڋݚٺټݜڍٺټݛݘٺټڅڐٺټݜݙٺټݛݔٺٷڋݣٺٷٽݑٸپڍٺټݜڇٺټڄٺٺټڅݯٺټݚٽٸڅٿٸځٷٺټݝٷٺټݜݦٺټڅݘٺټݛݓٸٷٸٺټݙڀٸݪٸٺٻݙݬٺٻݞݐٺټچڀٺټݜݮٺټڃټٺټݛٽٸڋݕٺټݛڑٺټݚݘٺټݝڇٺٸݤݛٸڌٻ]=]),(0x1)local function OxBUDJ2V8(OxJJCEO11,Ox1UC1EJ2,...)if(OxJJCEO11==0x1BBE6E6D)then return(OxJCDONH7(OxJCDONH7(OxJCDONH7(OxJCDONH7(Ox1UC1EJ2,0x83DE7),0xD88CA),0x43DEA),0xC80))elseif(OxJJCEO11==0x273E8146)then return((OxJCDONH7((OxJCDONH7(OxJCDONH7(Ox1UC1EJ2,0x1C6AD),0x36661))-0x1D2B1,0xE13A))-0x246D1)elseif(OxJJCEO11==0x2DF1368A)then return(OxJCDONH7((OxJCDONH7(((Ox1UC1EJ2)-0x483C6)-0x7CEE8,0x6E586))-0x4F41E,0x379AF))elseif(OxJJCEO11==0xA6402FC)then return(OxJCDONH7(OxJCDONH7((Ox1UC1EJ2)-0x383FB,0xB578),0x4A34A))elseif(OxJJCEO11==0x12E91D28)then return(OxJCDONH7(((OxJCDONH7(OxJCDONH7(Ox1UC1EJ2,0x28D45),0xE27BD))-0x2C842)-0x2DC83,0xC8548))elseif(OxJJCEO11==0x263B4784)then return((OxJCDONH7(((Ox1UC1EJ2)-0x91404)-0xECF07,0x2FA92))-0x8B475)elseif(OxJJCEO11==0x1431F3B0)then return((OxJCDONH7((((Ox1UC1EJ2)-0x10954)-0xF1B2B)-0x483A1,0xD3DB6))-0x4B743)elseif(OxJJCEO11==0x1171C90F)then return((OxJCDONH7((OxJCDONH7(Ox1UC1EJ2,0x2E8CF))-0x56115,0x8F8AD))-0x40CCA)elseif(OxJJCEO11==0x2611D638)then return(((OxJCDONH7(OxJCDONH7((Ox1UC1EJ2)-0x918F2,0x6D117),0x10D5D))-0xB4540)-0x36F52)elseif(OxJJCEO11==0x2410A969)then return((((Ox1UC1EJ2)-0xEDEEB)-0x3ECD4)-0x991C7)elseif(OxJJCEO11==0x16C9805D)then return(((OxJCDONH7(OxJCDONH7((Ox1UC1EJ2)-0x1540D,0x7C491),0xAAF71))-0x51069)-0xB198B)elseif(OxJJCEO11==0x393940A9)then return(OxJCDONH7(OxJCDONH7(OxJCDONH7(OxJCDONH7(Ox1UC1EJ2,0xDD457),0x59417),0x3BB0D),0xC6EB2))elseif(OxJJCEO11==0x234E35FC)then return((((OxJCDONH7(Ox1UC1EJ2,0xEEA08))-0x5DA07)-0x40E60)-0x6154F)elseif(OxJJCEO11==0x27533BB0)then return(OxJCDONH7(OxJCDONH7((((Ox1UC1EJ2)-0xBC1B5)-0x8A5C6)-0xD6A,0x11703),0xE72BB))else end end;local function OxBUDJ2V8()local OxJJCEO11,OxCLAJE13,OxE2UEJL4,OxLDD2HV5=OxNOFS2113(OxLDD2HV5,OxCOL2AC6,OxCOL2AC6+0x3)OxJJCEO11=OxJCDONH7(OxJJCEO11,Ox1UC1EJ2)Ox1UC1EJ2=OxJJCEO11%0x100;OxCLAJE13=OxJCDONH7(OxCLAJE13,Ox1UC1EJ2)Ox1UC1EJ2=OxCLAJE13%0x100;OxE2UEJL4=OxJCDONH7(OxE2UEJL4,Ox1UC1EJ2)Ox1UC1EJ2=OxE2UEJL4%0x100;OxLDD2HV5=OxJCDONH7(OxLDD2HV5,Ox1UC1EJ2)Ox1UC1EJ2=OxLDD2HV5%0x100;OxCOL2AC6=OxCOL2AC6+0x4;return((OxLDD2HV5*0x1000000)+(OxE2UEJL4*0x10000)+(OxCLAJE13*0x100)+OxJJCEO11)end;local function OxSULBCD11()local OxJJCEO11,OxCLAJE13=OxNOFS2113(OxLDD2HV5,OxCOL2AC6,OxCOL2AC6+0x2)OxJJCEO11=OxJCDONH7(OxJJCEO11,Ox1UC1EJ2)Ox1UC1EJ2=OxJJCEO11%0x100;OxCLAJE13=OxJCDONH7(OxCLAJE13,Ox1UC1EJ2)Ox1UC1EJ2=OxCLAJE13%0x100;OxCOL2AC6=OxCOL2AC6+0x2;return((OxCLAJE13*0x100)+OxJJCEO11)end;local function Ox2NJSBL12()local OxJJCEO11=OxJCDONH7(OxNOFS2113(OxLDD2HV5,OxCOL2AC6,OxCOL2AC6),Ox1UC1EJ2)Ox1UC1EJ2=OxJJCEO11%0x100;OxCOL2AC6=(OxCOL2AC6+0x1)return(OxJJCEO11)end;local function OxH22UAV15(OxJJCEO11,Ox1UC1EJ2,OxCLAJE13)if(OxCLAJE13)then local OxJJCEO11=(OxJJCEO11/0x2^(Ox1UC1EJ2-0x1))%0x2^((OxCLAJE13-0x1)-(Ox1UC1EJ2-0x1)+0x1)return(OxJJCEO11-(OxJJCEO11%0x1))else local Ox1UC1EJ2=0x2^(Ox1UC1EJ2-0x1)return(((OxJJCEO11%(Ox1UC1EJ2+Ox1UC1EJ2)>=Ox1UC1EJ2)and(0x1))or(0))end end;local OxF2SBFV20="\35"local function OxCFL11U21(...)return({...}),OxFDEESB17(OxF2SBFV20,...)end;local function OxFEL21F22(...)local OxJJCEO11=({})local OxCLAJE13=({})local Ox1O2VOB9=({})for OxJJCEO11=0,OxBUDJ2V8(Ox1UC1EJ2)-0x1,0x1 do OxCLAJE13[OxJJCEO11]=OxFEL21F22()end;for OxJJCEO11=0,OxBUDJ2V8(Ox1UC1EJ2)-0x1,0x1 do local OxCLAJE13=Ox2NJSBL12(Ox1UC1EJ2)if(OxCLAJE13==0x36)then local Ox1UC1EJ2=Ox2NJSBL12(Ox1UC1EJ2)Ox1O2VOB9[OxJJCEO11]=(Ox1UC1EJ2~=0)elseif(OxCLAJE13==0x12)then while true do local OxCLAJE13=OxBUDJ2V8(Ox1UC1EJ2)if(OxCLAJE13==0)then Ox1O2VOB9[OxJJCEO11]=('')break end;if(OxCLAJE13>0x1388)then local OxLDD2HV5,OxBUDJ2V8=(''),(OxE2UEJL4(OxLDD2HV5,OxCOL2AC6,OxCOL2AC6+OxCLAJE13-0x1))OxCOL2AC6=OxCOL2AC6+OxCLAJE13;for OxJJCEO11=0x1,#OxBUDJ2V8,0x1 do local OxJJCEO11=OxJCDONH7(OxNOFS2113(OxE2UEJL4(OxBUDJ2V8,OxJJCEO11,OxJJCEO11)),Ox1UC1EJ2)Ox1UC1EJ2=OxJJCEO11%0x100;OxLDD2HV5=OxLDD2HV5..OxHBNUCE10[OxJJCEO11]end;Ox1O2VOB9[OxJJCEO11]=OxLDD2HV5 else local OxE2UEJL4,OxLDD2HV5=(''),({OxNOFS2113(OxLDD2HV5,OxCOL2AC6,OxCOL2AC6+OxCLAJE13-0x1)})OxCOL2AC6=OxCOL2AC6+OxCLAJE13;for OxJJCEO11,OxJJCEO11 in OxONHHAN16(OxLDD2HV5)do local OxJJCEO11=OxJCDONH7(OxJJCEO11,Ox1UC1EJ2)Ox1UC1EJ2=OxJJCEO11%0x100;OxE2UEJL4=OxE2UEJL4..OxHBNUCE10[OxJJCEO11]end;Ox1O2VOB9[OxJJCEO11]=OxE2UEJL4 end;break end elseif(OxCLAJE13==0x1E)then while(true)do local OxCLAJE13=OxBUDJ2V8(Ox1UC1EJ2)local Ox1UC1EJ2=OxBUDJ2V8(Ox1UC1EJ2)local OxE2UEJL4=0x1;local OxCLAJE13=(OxH22UAV15(Ox1UC1EJ2,0x1,0x14)*(0x2^0x20))+OxCLAJE13;local OxLDD2HV5=OxH22UAV15(Ox1UC1EJ2,0x15,0x1F)local Ox1UC1EJ2=((-0x1)^OxH22UAV15(Ox1UC1EJ2,0x20))if(OxLDD2HV5==0)then if(OxCLAJE13==0)then Ox1O2VOB9[OxJJCEO11]=(Ox1UC1EJ2*0)break else OxLDD2HV5=0x1;OxE2UEJL4=0 end elseif(OxLDD2HV5==0x7FF)then Ox1O2VOB9[OxJJCEO11]=(OxCLAJE13==0)and(Ox1UC1EJ2*(0x1/0))or(Ox1UC1EJ2*(0/0))break end;Ox1O2VOB9[OxJJCEO11]=OxVVBBHF18(Ox1UC1EJ2,OxLDD2HV5-0x3FF)*(OxE2UEJL4+(OxCLAJE13/(0x2^0x34)))break end elseif(OxCLAJE13==0xD)then while(true)do local Ox1UC1EJ2=OxBUDJ2V8(Ox1UC1EJ2)Ox1O2VOB9[OxJJCEO11]=OxE2UEJL4(OxLDD2HV5,OxCOL2AC6,OxCOL2AC6+Ox1UC1EJ2-0x1)OxCOL2AC6=OxCOL2AC6+Ox1UC1EJ2;break end else Ox1O2VOB9[OxJJCEO11]=nil end end;local OxE2UEJL4=OxBUDJ2V8(Ox1UC1EJ2)for Ox1UC1EJ2=0,OxE2UEJL4-0x1,0x1 do OxJJCEO11[Ox1UC1EJ2]=({})end;for OxCLAJE13=0,OxE2UEJL4-0x1,0x1 do local OxE2UEJL4=Ox2NJSBL12(Ox1UC1EJ2)if(OxE2UEJL4~=0)then OxE2UEJL4=OxE2UEJL4-0x1;local OxLDD2HV5,OxCOL2AC6,OxJCDONH7,OxHBNUCE10,OxNOFS2113,OxSAVNLC14=0,0,0,0,0,0;local OxONHHAN16=OxH22UAV15(OxE2UEJL4,0x1,0x3)if(OxONHHAN16==0x6)then elseif(OxONHHAN16==0x3)then OxLDD2HV5=(Ox2NJSBL12(Ox1UC1EJ2))OxHBNUCE10=(OxSULBCD11(Ox1UC1EJ2))OxNOFS2113=OxJJCEO11[(OxBUDJ2V8(Ox1UC1EJ2))]OxCOL2AC6=(OxSULBCD11(Ox1UC1EJ2))elseif(OxONHHAN16==0x1)then OxLDD2HV5=(Ox2NJSBL12(Ox1UC1EJ2))OxHBNUCE10=(OxSULBCD11(Ox1UC1EJ2))OxNOFS2113=(OxBUDJ2V8(Ox1UC1EJ2))elseif(OxONHHAN16==0)then OxLDD2HV5=(Ox2NJSBL12(Ox1UC1EJ2))OxHBNUCE10=(OxSULBCD11(Ox1UC1EJ2))OxNOFS2113=(OxSULBCD11(Ox1UC1EJ2))OxCOL2AC6=(OxSULBCD11(Ox1UC1EJ2))elseif(OxONHHAN16==0x5)then OxLDD2HV5=(Ox2NJSBL12(Ox1UC1EJ2))OxHBNUCE10=(OxSULBCD11(Ox1UC1EJ2))OxNOFS2113=(OxBUDJ2V8(Ox1UC1EJ2))OxCOL2AC6=(OxSULBCD11(Ox1UC1EJ2))OxJCDONH7=({})for OxJJCEO11=0x1,OxCOL2AC6,0x1 do OxJCDONH7[OxJJCEO11]=({[0]=Ox2NJSBL12(Ox1UC1EJ2),[0x1]=OxSULBCD11(Ox1UC1EJ2)})end elseif(OxONHHAN16==0x2)then OxLDD2HV5=(Ox2NJSBL12(Ox1UC1EJ2))OxHBNUCE10=(OxSULBCD11(Ox1UC1EJ2))OxNOFS2113=OxJJCEO11[(OxBUDJ2V8(Ox1UC1EJ2))]end;if(OxH22UAV15(OxE2UEJL4,0x8,0x8)==0x1)then OxSAVNLC14=OxJJCEO11[OxBUDJ2V8(Ox1UC1EJ2)]else OxSAVNLC14=OxJJCEO11[OxCLAJE13+0x1]end;if(OxH22UAV15(OxE2UEJL4,0x4,0x4)==0x1)then OxHBNUCE10=Ox1O2VOB9[OxHBNUCE10]end;if(OxH22UAV15(OxE2UEJL4,0x5,0x5)==0x1)then OxNOFS2113=Ox1O2VOB9[OxNOFS2113]end;if(OxH22UAV15(OxE2UEJL4,0x6,0x6)==0x1)then OxCOL2AC6=Ox1O2VOB9[OxCOL2AC6]end;if(OxH22UAV15(OxE2UEJL4,0x7,0x7)==0x1)then OxJCDONH7=({})for OxJJCEO11=0x1,Ox2NJSBL12(),0x1 do OxJCDONH7[OxJJCEO11]=OxBUDJ2V8()end end;local OxJJCEO11=OxJJCEO11[OxCLAJE13]OxJJCEO11[0x3A368]=OxLDD2HV5;OxJJCEO11['RJx5YJV']=OxNOFS2113;OxJJCEO11["fc2WFOpTr"]=OxCOL2AC6;OxJJCEO11["HAND8DQ"]=OxHBNUCE10;OxJJCEO11['XgWFuG']=OxJCDONH7;OxJJCEO11[98630.44431832733]=OxSAVNLC14 end end;local OxE2UEJL4=OxSULBCD11(Ox1UC1EJ2)local Ox1UC1EJ2=Ox2NJSBL12(Ox1UC1EJ2)return({[-0x1AC2F]=Ox1O2VOB9;['g0Wo2']=OxE2UEJL4;[-123846.76397547068]=OxJJCEO11;[-0x91BA8]=Ox1UC1EJ2;['nJE1IMw']=0;[905130.5631713972]=OxCLAJE13})end;local function Ox1UC1EJ2(OxCLAJE13,OxE2UEJL4,OxLDD2HV5,...)local OxCOL2AC6=OxCLAJE13[-0x1AC2F]local OxCOL2AC6=OxCLAJE13[-0x91BA8]local OxJCDONH7=OxCLAJE13[-123846.76397547068]local OxBUDJ2V8=OxCLAJE13[905130.5631713972]local OxHBNUCE10=0;local OxCLAJE13=OxCLAJE13['g0Wo2']return(function(...)local OxSULBCD11=0x3A368;local Ox2NJSBL12=({})if#OxJJCEO11~=0x2C then while''do end end;local OxJJCEO11=(0x23E4293E)local OxJJCEO11=-(0x1)local OxNOFS2113=(true)local OxJCDONH7=OxJCDONH7[OxHBNUCE10]local OxHBNUCE10='HAND8DQ'local OxNOFS2113='XgWFuG'local OxH22UAV15=98630.44431832733;local OxONHHAN16='RJx5YJV'local OxVVBBHF18='fc2WFOpTr'local OxFDEESB17=(OxFDEESB17(OxF2SBFV20,...)-0x1)local OxF2SBFV20={}local OxFEL21F22={}local OxBLAUSL23={...}for OxJJCEO11=0,OxFDEESB17,0x1 do if(OxJJCEO11>=OxCOL2AC6)then OxF2SBFV20[OxJJCEO11-OxCOL2AC6]=OxBLAUSL23[OxJJCEO11+0x1]else OxFEL21F22[OxJJCEO11]=OxBLAUSL23[OxJJCEO11+0x1]end end;local OxCOL2AC6=OxFDEESB17-OxCOL2AC6+0x1;while(true)do local OxFDEESB17=OxJCDONH7;local OxSULBCD11=OxFDEESB17[OxSULBCD11]OxJCDONH7=OxFDEESB17[OxH22UAV15]if(OxSULBCD11<=0x15)then if(OxSULBCD11<=0xA)then if(OxSULBCD11<=0x4)then if(OxSULBCD11<=0x1)then if(OxSULBCD11==0)then OxFEL21F22[OxFDEESB17[OxHBNUCE10]]=OxFEL21F22[OxFDEESB17[OxONHHAN16]]-OxFEL21F22[OxFDEESB17[OxVVBBHF18]]elseif(OxSULBCD11<=0x1)then local Ox1UC1EJ2=OxFDEESB17[OxHBNUCE10]local OxCLAJE13=OxFEL21F22[Ox1UC1EJ2]local OxE2UEJL4,OxLDD2HV5=0,0x32*(OxFDEESB17[OxVVBBHF18]-0x1)for OxJJCEO11=Ox1UC1EJ2+0x1,OxJJCEO11,0x1 do OxCLAJE13[OxLDD2HV5+OxE2UEJL4+0x1]=OxFEL21F22[OxJJCEO11]OxE2UEJL4=OxE2UEJL4+0x1 end end elseif(OxSULBCD11<=0x2)then elseif(OxSULBCD11>0x3)then OxFEL21F22[OxFDEESB17[OxHBNUCE10]]=OxFDEESB17[OxONHHAN16]elseif(OxSULBCD11<0x4)then OxFEL21F22[OxFDEESB17[OxHBNUCE10]]=OxFEL21F22[OxFDEESB17[OxONHHAN16]]+OxFDEESB17[OxVVBBHF18]end elseif(OxSULBCD11<=0x7)then if(OxSULBCD11<=0x5)then OxFEL21F22[OxFDEESB17[OxHBNUCE10]]=OxFEL21F22[OxFDEESB17[OxONHHAN16]]-OxFDEESB17[OxVVBBHF18]elseif(OxSULBCD11>0x6)then do return(OxFEL21F22[OxFDEESB17[OxHBNUCE10]])end elseif(OxSULBCD11<0x7)then OxFEL21F22[OxFDEESB17[OxHBNUCE10]]=OxFEL21F22[OxFDEESB17[OxONHHAN16]]/OxFDEESB17[OxVVBBHF18]end elseif(OxSULBCD11<=0x8)then OxFEL21F22[OxFDEESB17[OxHBNUCE10]]=(OxFDEESB17[OxONHHAN16]~=0)elseif(OxSULBCD11==0x9)then OxFEL21F22[OxFDEESB17[OxHBNUCE10]]=OxLDD2HV5[OxFDEESB17[OxONHHAN16]]elseif(OxSULBCD11<=0xA)then local OxJJCEO11=OxFDEESB17[OxHBNUCE10]local Ox1UC1EJ2=OxFDEESB17[OxONHHAN16]for Ox1UC1EJ2=0x1,Ox1UC1EJ2,0x1 do OxFEL21F22[OxJJCEO11+Ox1UC1EJ2-0x1]=OxF2SBFV20[Ox1UC1EJ2-0x1]end end elseif(OxSULBCD11<=0xF)then if(OxSULBCD11<=0xC)then if(OxSULBCD11>0xB)then local OxJJCEO11=OxFDEESB17[OxONHHAN16]local Ox1UC1EJ2=OxFEL21F22[OxJJCEO11]for OxJJCEO11=OxJJCEO11+0x1,OxFDEESB17[OxVVBBHF18]do Ox1UC1EJ2=Ox1UC1EJ2..OxFEL21F22[OxJJCEO11]end;OxFEL21F22[OxFDEESB17[OxHBNUCE10]]=Ox1UC1EJ2 elseif(OxSULBCD11<0xC)then local OxJJCEO11=OxFDEESB17[OxHBNUCE10]OxFEL21F22[OxJJCEO11](OxSAVNLC14(OxFEL21F22,OxJJCEO11+0x1,OxFDEESB17[OxONHHAN16]))for OxJJCEO11=OxJJCEO11+0x1,OxCLAJE13 do OxFEL21F22[OxJJCEO11]=nil end end elseif(OxSULBCD11<=0xD)then OxFEL21F22[OxFDEESB17[OxHBNUCE10]]=OxFEL21F22[OxFDEESB17[OxONHHAN16]]*OxFDEESB17[OxVVBBHF18]elseif(OxSULBCD11>0xE)then OxJCDONH7=OxFDEESB17[OxONHHAN16]elseif(OxSULBCD11<0xF)then OxFEL21F22[OxFDEESB17[OxHBNUCE10]]=Ox1O2VOB9(OxFDEESB17[OxONHHAN16])end elseif(OxSULBCD11<=0x12)then if(OxSULBCD11<=0x10)then local Ox1UC1EJ2=OxFDEESB17[OxHBNUCE10]OxFEL21F22[Ox1UC1EJ2]=OxFEL21F22[Ox1UC1EJ2](OxSAVNLC14(OxFEL21F22,Ox1UC1EJ2+0x1,OxJJCEO11))for OxJJCEO11=Ox1UC1EJ2+0x1,OxJJCEO11 do OxFEL21F22[OxJJCEO11]=nil end elseif(OxSULBCD11>0x11)then OxFEL21F22[OxFDEESB17[OxHBNUCE10]]=({(nil)})elseif(OxSULBCD11<0x12)then local OxJJCEO11=OxFDEESB17[OxHBNUCE10]local Ox1UC1EJ2=OxFDEESB17[OxONHHAN16]local OxCLAJE13=0x32*(OxFDEESB17[OxVVBBHF18]-0x1)local OxE2UEJL4=OxFEL21F22[OxJJCEO11]local OxLDD2HV5=0;for Ox1UC1EJ2=OxJJCEO11+0x1,Ox1UC1EJ2 do OxE2UEJL4[OxCLAJE13+OxLDD2HV5+0x1]=OxFEL21F22[OxJJCEO11+(Ox1UC1EJ2-OxJJCEO11)]OxLDD2HV5=OxLDD2HV5+0x1 end end elseif(OxSULBCD11<=0x13)then OxFEL21F22[OxFDEESB17[OxHBNUCE10]]=OxFEL21F22[OxFDEESB17[OxONHHAN16]][OxFEL21F22[OxFDEESB17[OxVVBBHF18]]]elseif(OxSULBCD11==0x14)then do return end elseif(OxSULBCD11<=0x15)then local OxJJCEO11=OxFDEESB17[OxHBNUCE10]OxFEL21F22[OxJJCEO11]=OxFEL21F22[OxJJCEO11]()end elseif(OxSULBCD11<=0x20)then if(OxSULBCD11<=0x1A)then if(OxSULBCD11<=0x17)then if(OxSULBCD11==0x16)then OxFEL21F22[OxFDEESB17[OxHBNUCE10]]=OxFEL21F22[OxFDEESB17[OxONHHAN16]]elseif(OxSULBCD11<=0x17)then local OxJJCEO11=OxFDEESB17[OxHBNUCE10]OxFEL21F22[OxJJCEO11]=OxFEL21F22[OxJJCEO11](OxSAVNLC14(OxFEL21F22,OxJJCEO11+0x1,OxFDEESB17[OxONHHAN16]))for OxJJCEO11=OxJJCEO11+0x1,OxCLAJE13 do OxFEL21F22[OxJJCEO11]=nil end end elseif(OxSULBCD11<=0x18)then OxFEL21F22[OxFDEESB17[OxHBNUCE10]]=Ox1O2VOB9(0x100)elseif(OxSULBCD11>0x19)then OxFEL21F22[OxFDEESB17[OxHBNUCE10]]=#OxFEL21F22[OxFDEESB17[OxONHHAN16]]elseif(OxSULBCD11<0x1A)then if(OxFEL21F22[OxFDEESB17[OxHBNUCE10]]==OxFEL21F22[OxFDEESB17[OxVVBBHF18]])then OxJCDONH7=OxFDEESB17[OxONHHAN16]end end elseif(OxSULBCD11<=0x1D)then if(OxSULBCD11<=0x1B)then local Ox1UC1EJ2=OxFDEESB17[OxHBNUCE10]do return OxSAVNLC14(OxFEL21F22,Ox1UC1EJ2,OxJJCEO11)end elseif(OxSULBCD11==0x1C)then local OxJJCEO11=OxFDEESB17[OxHBNUCE10]OxFEL21F22[OxJJCEO11]=0+(OxFEL21F22[OxJJCEO11])OxFEL21F22[OxJJCEO11+0x1]=0+(OxFEL21F22[OxJJCEO11+0x1])OxFEL21F22[OxJJCEO11+0x2]=0+(OxFEL21F22[OxJJCEO11+0x2])local Ox1UC1EJ2=OxFEL21F22[OxJJCEO11]local OxCLAJE13=OxFEL21F22[OxJJCEO11+0x2]if(OxCLAJE13>0)then if(Ox1UC1EJ2>OxFEL21F22[OxJJCEO11+0x1])then OxJCDONH7=OxFDEESB17[OxONHHAN16]else OxFEL21F22[OxJJCEO11+0x3]=Ox1UC1EJ2 end elseif(Ox1UC1EJ2<OxFEL21F22[OxJJCEO11+0x1])then OxJCDONH7=OxFDEESB17[OxONHHAN16]else OxFEL21F22[OxJJCEO11+0x3]=Ox1UC1EJ2 end elseif(OxSULBCD11<=0x1D)then local OxJJCEO11=OxBUDJ2V8[OxFDEESB17[OxONHHAN16]]local OxCLAJE13=OxFDEESB17[OxNOFS2113]local OxCOL2AC6={}local OxJCDONH7=OxCHEEAN19({},{__index=function(OxJJCEO11,OxJJCEO11)local OxJJCEO11=OxCOL2AC6[OxJJCEO11]return(OxJJCEO11[0x1][OxJJCEO11[0x2]])end,__newindex=function(OxJJCEO11,OxJJCEO11,Ox1UC1EJ2)local OxJJCEO11=OxCOL2AC6[OxJJCEO11]OxJJCEO11[0x1][OxJJCEO11[0x2]]=Ox1UC1EJ2 end})for OxJJCEO11=0x1,OxFDEESB17[OxVVBBHF18],0x1 do local Ox1UC1EJ2=OxCLAJE13[OxJJCEO11]if(Ox1UC1EJ2[0]==0)then OxCOL2AC6[OxJJCEO11-0x1]=({OxFEL21F22,Ox1UC1EJ2[0x1]})else OxCOL2AC6[OxJJCEO11-0x1]=({OxE2UEJL4,Ox1UC1EJ2[0x1]})end;Ox2NJSBL12[#Ox2NJSBL12+0x1]=OxCOL2AC6 end;OxFEL21F22[OxFDEESB17[OxHBNUCE10]]=Ox1UC1EJ2(OxJJCEO11,OxJCDONH7,OxLDD2HV5)end elseif(OxSULBCD11<=0x1E)then local Ox1UC1EJ2=OxFDEESB17[OxHBNUCE10]local OxCLAJE13,OxE2UEJL4=OxCFL11U21(OxFEL21F22[Ox1UC1EJ2](OxSAVNLC14(OxFEL21F22,Ox1UC1EJ2+0x1,OxFDEESB17[OxONHHAN16])))OxJJCEO11=OxE2UEJL4+Ox1UC1EJ2-0x1;local OxE2UEJL4=0;for OxJJCEO11=Ox1UC1EJ2,OxJJCEO11 do OxE2UEJL4=OxE2UEJL4+0x1;OxFEL21F22[OxJJCEO11]=OxCLAJE13[OxE2UEJL4]end elseif(OxSULBCD11==0x1F)then if(OxFEL21F22[OxFDEESB17[OxHBNUCE10]]>=OxFEL21F22[OxFDEESB17[OxVVBBHF18]])then OxJCDONH7=OxFDEESB17[OxONHHAN16]end elseif(OxSULBCD11<=0x20)then if(OxFDEESB17[OxHBNUCE10]>=OxFEL21F22[OxFDEESB17[OxVVBBHF18]])then OxJCDONH7=OxFDEESB17[OxONHHAN16]end end elseif(OxSULBCD11<=0x26)then if(OxSULBCD11<=0x23)then if(OxSULBCD11<=0x21)then OxFEL21F22[OxFDEESB17[OxHBNUCE10]][OxFEL21F22[OxFDEESB17[OxONHHAN16]]]=OxFEL21F22[OxFDEESB17[OxVVBBHF18]]elseif(OxSULBCD11==0x22)then OxFEL21F22[OxFDEESB17[OxHBNUCE10]]=OxFEL21F22[OxFDEESB17[OxONHHAN16]][OxFDEESB17[OxVVBBHF18]]elseif(OxSULBCD11<=0x23)then local Ox1UC1EJ2=OxFDEESB17[OxHBNUCE10]OxJJCEO11=Ox1UC1EJ2+OxCOL2AC6-0x1;for OxJJCEO11=0,OxCOL2AC6 do OxFEL21F22[Ox1UC1EJ2+OxJJCEO11]=OxF2SBFV20[OxJJCEO11]end;for OxJJCEO11=OxJJCEO11+0x1,OxCLAJE13 do OxFEL21F22[OxJJCEO11]=nil end end elseif(OxSULBCD11<=0x24)then OxFEL21F22[OxFDEESB17[OxHBNUCE10]]=Ox1UC1EJ2(OxBUDJ2V8[OxFDEESB17[OxONHHAN16]],(nil),OxLDD2HV5)elseif(OxSULBCD11==0x25)then OxFEL21F22[OxFDEESB17[OxHBNUCE10]][OxFDEESB17[OxONHHAN16]]=OxFEL21F22[OxFDEESB17[OxVVBBHF18]]elseif(OxSULBCD11<=0x26)then OxFEL21F22[OxFDEESB17[OxHBNUCE10]][OxFDEESB17[OxONHHAN16]]=OxFDEESB17[OxVVBBHF18]end elseif(OxSULBCD11<=0x29)then if(OxSULBCD11<=0x27)then local OxJJCEO11=OxFDEESB17[OxHBNUCE10]local Ox1UC1EJ2=OxFEL21F22[OxJJCEO11+0x2]local OxCLAJE13=OxFEL21F22[OxJJCEO11]+Ox1UC1EJ2;OxFEL21F22[OxJJCEO11]=OxCLAJE13;if(Ox1UC1EJ2>0)then if(OxCLAJE13<=OxFEL21F22[OxJJCEO11+0x1])then OxJCDONH7=OxFDEESB17[OxONHHAN16]OxFEL21F22[OxJJCEO11+0x3]=OxCLAJE13 end elseif(OxCLAJE13>=OxFEL21F22[OxJJCEO11+0x1])then OxJCDONH7=OxFDEESB17[OxONHHAN16]OxFEL21F22[OxJJCEO11+0x3]=OxCLAJE13 end elseif(OxSULBCD11==0x28)then OxFEL21F22[OxFDEESB17[OxHBNUCE10]]=OxFEL21F22[OxFDEESB17[OxONHHAN16]]%OxFDEESB17[OxVVBBHF18]elseif(OxSULBCD11<=0x29)then local OxJJCEO11=OxFDEESB17[OxHBNUCE10]local Ox1UC1EJ2=OxFEL21F22[OxFDEESB17[OxONHHAN16]]OxFEL21F22[OxJJCEO11+0x1]=Ox1UC1EJ2;OxFEL21F22[OxJJCEO11]=Ox1UC1EJ2[OxFDEESB17[OxVVBBHF18]]end elseif(OxSULBCD11<=0x2A)then local OxJJCEO11=OxFDEESB17[OxHBNUCE10]OxFEL21F22[OxJJCEO11]=OxFEL21F22[OxJJCEO11](OxFEL21F22[OxJJCEO11+0x1])for OxJJCEO11=OxJJCEO11+0x1,OxCLAJE13 do OxFEL21F22[OxJJCEO11]=nil end elseif(OxSULBCD11==0x2B)then OxFEL21F22[OxFDEESB17[OxHBNUCE10]]=OxFEL21F22[OxFDEESB17[OxONHHAN16]]+OxFEL21F22[OxFDEESB17[OxVVBBHF18]]elseif(OxSULBCD11<=0x2C)then OxFEL21F22[OxFDEESB17[OxHBNUCE10]]=OxE2UEJL4[OxFDEESB17[OxONHHAN16]]end end end)end;return Ox1UC1EJ2(OxFEL21F22(),{},OxCLAJE13())(...)end)({[0x14AA09D6]=("\51");[0x30CDB6B8]=("\50");['o5ITi']=("\117");[0x1FA51563]=("\116");['dJE8e']=("\121");[0x36FFAC03]=("\114");ofLQcv00L=("\102");[0x15C3D2F6]=("\108");["fToXmpErQ"]=("\111");[0x23A5B0F0]=("\104");['ch2PM7']=("\120");[0x28552064]=("\112");[0x1702BD6B]=("\118");[0x28733ADE]=("\99");["aPpIZlBvh"]=("\100");[0x20304762]=("\103");["Vot08VN"]=("\101");[0x17E3EE27]=("\98");[0x1B445014]=("\110");[0x22902A95]=("\109");[0x630BB2E]=("\97");[0x327E37C3]=("\105");[0xF6FF715]=("\115");[0x1FCEE392]=("\107");[0x1660770]=("\119")})
end)


easy:NewButton("chat spy", "makes you see evreyones chat in game!", function()
enabled = true
spyOnMyself = true
public = false
publicItalics = true
privateProperties = {
	Color = Color3.fromRGB(0,255,255); 
	Font = Enum.Font.SourceSansBold;
	TextSize = 18;
}
local StarterGui = game:GetService("StarterGui")
local Players = game:GetService("Players")
local player = Players.LocalPlayer
local saymsg = game:GetService("ReplicatedStorage"):WaitForChild("DefaultChatSystemChatEvents"):WaitForChild("SayMessageRequest")
local getmsg = game:GetService("ReplicatedStorage"):WaitForChild("DefaultChatSystemChatEvents"):WaitForChild("OnMessageDoneFiltering")
local instance = (_G.chatSpyInstance or 0) + 1
_G.chatSpyInstance = instance

local function onChatted(p,msg)
	if _G.chatSpyInstance == instance then
		if p==player and msg:lower():sub(1,6)=="/e spy" then
			enabled = not enabled
			wait(0.3)
			privateProperties.Text = "{SPY "..(enabled and "EN" or "DIS").."ABLED}"
			StarterGui:SetCore("ChatMakeSystemMessage",privateProperties)
		elseif enabled and (spyOnMyself==true or p~=player) then
			msg = msg:gsub("[\n\r]",''):gsub("\t",' '):gsub("[ ]+",' ')
			local hidden = true
			local conn = getmsg.OnClientEvent:Connect(function(packet,channel)
				if packet.SpeakerUserId==p.UserId and packet.Message==msg:sub(#msg-#packet.Message+1) and (channel=="All" or (channel=="Team" and public==false and Players[packet.FromSpeaker].Team==player.Team)) then
					hidden = false
				end
			end)
			wait(1)
			conn:Disconnect()
			if hidden and enabled then
				if public then
					saymsg:FireServer((publicItalics and "/me " or '').."{SPY} [".. p.Name .."]: "..msg,"All")
				else
					privateProperties.Text = "{SPY} [".. p.Name .."]: "..msg
					StarterGui:SetCore("ChatMakeSystemMessage",privateProperties)
				end
			end
		end
	end
end

for _,p in ipairs(Players:GetPlayers()) do
	p.Chatted:Connect(function(msg) onChatted(p,msg) end)
end
Players.PlayerAdded:Connect(function(p)
	p.Chatted:Connect(function(msg) onChatted(p,msg) end)
end)
privateProperties.Text = "{SPY "..(enabled and "EN" or "DIS").."ABLED}"
StarterGui:SetCore("ChatMakeSystemMessage",privateProperties)
local chatFrame = player.PlayerGui.Chat.Frame
chatFrame.ChatChannelParentFrame.Visible = true
chatFrame.ChatBarParentFrame.Position = chatFrame.ChatChannelParentFrame.Position+UDim2.new(UDim.new(),chatFrame.ChatChannelParentFrame.Size.Y)
end)


easy:NewKeybind("toggle ui", "makes the ui go away", Enum.KeyCode.LeftAlt, function()
	Library:ToggleUI(LeftAlt)
end)






local keys = {
    
    "58729375275t8g77fg7F57FD5DFSHUIEFYSG7Tge6g85328rfd",
    "H8YHG765F87GHIOUh865tgh8IGT875FG7ufg576fG7RF7f78G78e",
    "gh76ttght679G876E67E5FUT645WErr56fDF67DTF7JHIEHIFGEWHGH",
    "j89g3h093h894gh6GT76F57R3E65727058347837H7gf7fiusgf78gfe7sivb",
    "D544E7RF54R7F88YYHGIUHGGFES6GYWGD67ARDR7W245564fe3w7",
    "LOJ8FH3UJ75ttg63w4h6f85sguyhNFYSE7GFH0UEGWI7GWHG",
    "HG8379HG46EG9g765fgf43EDF765df6rfghnuilh8765r5463f7g6",
    "gh76ttght679G876E67E5FUT645WErr56fDF67DTF7JHIEHIFGEWHGH7fr5g654ed",
    "G7TGIYH875RFg7g67eghfhe67gyfsh7hgft6tfrtweyh76r54ge7tfg7",
    "H7TR67GWTGF6A77TG76FG7GFR67WGFW65f7fgsyef6s5rf6afw6arf",
   
}

local counter = 1
local keyCheck
for i,v in pairs(keys) do
    if counter == #keys then
    --not whitelisted!
    keys = ""
    game.Players.LocalPlayer:Kick("Not a valid key!")
    else
        if v == _G.Key then
            --Whitelisted!
            print("Successfully whitelisted!")
            keyCheck = _G.Key
            keys = ""
        else
            counter = counter +1
        end
    end
end

while true do
    if _G.Key == keyCheck then
        --Not spoofed
    else
        game.Players.LocalPlayer:Kick("DONT SPOOF YOUR FUCKING KEY WEAKLING")
    end
    wait()
end







local GetService = setmetatable({}, {
    __index = function(self, key)
        return game:GetService(key)
    end
})

local Library = loadstring(game:HttpGet("https://raw.githubusercontent.com/bloodball/-back-ups-for-libs/main/cat"))()
local NotifyLibrary = loadstring(game:HttpGet("https://raw.githubusercontent.com/Kinlei/Dynissimo/main/Scripts/AkaliNotif.lua"))()
local Notify = NotifyLibrary.Notify
Library.theme.accentcolor = Color3.new(0.37483344, 0.99383, 2)

local RunService = GetService.RunService
local Players = GetService.Players
local LocalPlayer = Players.LocalPlayer
local Mouse = LocalPlayer:GetMouse()
local CurrentCamera = workspace.CurrentCamera
local UserInputService = GetService.UserInputService
local Unpack = table.unpack
local GuiInset = GetService.GuiService:GetGuiInset()
local AimbotFOV = Drawing.new("Circle")
AimbotFOV.Thickness = 1
local SilentAimFOV = Drawing.new("Circle")
SilentAimFOV.Thickness = 1
local Insert = table.insert
local Network = GetService.NetworkClient
local PuppywareFolder = Instance.new("Folder", workspace)
PuppywareFolder.Name = "venoware on top fym-Folder"
local StarterGui = GetService.StarterGui
local ReplicatedStorage = GetService.ReplicatedStorage

local AnimationModule = {
    Astronaut = {
        "rbxassetid://891621366",
        "rbxassetid://891633237",
        "rbxassetid://891667138",
        "rbxassetid://891636393",
        "rbxassetid://891627522",
        "rbxassetid://891609353",
        "rbxassetid://891617961"
    },
    Bubbly = {
        "rbxassetid://910004836",
        "rbxassetid://910009958",
        "rbxassetid://910034870",
        "rbxassetid://910025107",
        "rbxassetid://910016857",
        "rbxassetid://910001910",
        "rbxassetid://910030921",
        "rbxassetid://910028158"
    },
    Cartoony = {
        "rbxassetid://742637544",
        "rbxassetid://742638445",
        "rbxassetid://742640026",
        "rbxassetid://742638842",
        "rbxassetid://742637942",
        "rbxassetid://742636889",
        "rbxassetid://742637151"
    },
    Confindent = {
        "rbxassetid://1069977950",
        "rbxassetid://1069987858",
        "rbxassetid://1070017263",
        "rbxassetid://1070001516",
        "rbxassetid://1069984524",
        "rbxassetid://1069946257",
        "rbxassetid://1069973677"
    },
    Cowboy = {
        "rbxassetid://1014390418",
        "rbxassetid://1014398616",
        "rbxassetid://1014421541",
        "rbxassetid://1014401683",
        "rbxassetid://1014394726",
        "rbxassetid://1014380606",
        "rbxassetid://1014384571"
    },
    Default = {
        "http://www.roblox.com/asset/?id=507766666",
        "http://www.roblox.com/asset/?id=507766951",
        "http://www.roblox.com/asset/?id=507777826",
        "http://www.roblox.com/asset/?id=507767714",
        "http://www.roblox.com/asset/?id=507765000",
        "http://www.roblox.com/asset/?id=507765644",
        "http://www.roblox.com/asset/?id=507767968"
    },
    Elder = {
        "rbxassetid://845397899",
        "rbxassetid://845400520",
        "rbxassetid://845403856",
        "rbxassetid://845386501",
        "rbxassetid://845398858",
        "rbxassetid://845392038",
        "rbxassetid://845396048" 
    },
    Ghost = {
        "rbxassetid://616006778",
        "rbxassetid://616008087",
        "rbxassetid://616013216",
        "rbxassetid://616013216",
        "rbxassetid://616008936",
        "rbxassetid://616005863",
        "rbxassetid://616012453",
        "rbxassetid://616011509"
    },
    Knight = {
        "rbxassetid://657595757",
        "rbxassetid://657568135",
        "rbxassetid://657552124",
        "rbxassetid://657564596",
        "rbxassetid://658409194",
        "rbxassetid://658360781",
        "rbxassetid://657600338"
    },
    Levitation = {
        "rbxassetid://616006778",
        "rbxassetid://616008087",
        "rbxassetid://616013216",
        "rbxassetid://616010382",
        "rbxassetid://616008936",
        "rbxassetid://616003713",
        "rbxassetid://616005863"
    },
    Mage = {
        "rbxassetid://707742142",
        "rbxassetid://707855907",
        "rbxassetid://707897309",
        "rbxassetid://707861613",
        "rbxassetid://707853694",
        "rbxassetid://707826056",
        "rbxassetid://707829716"
    },
    Ninja = {
        "rbxassetid://656117400",
        "rbxassetid://656118341",
        "rbxassetid://656121766",
        "rbxassetid://656118852",
        "rbxassetid://656117878",
        "rbxassetid://656114359",
        "rbxassetid://656115606"
    },
    OldSchool = {
        "rbxassetid://5319828216",
        "rbxassetid://5319831086",
        "rbxassetid://5319847204",
        "rbxassetid://5319844329",
        "rbxassetid://5319841935",
        "rbxassetid://5319839762",
        "rbxassetid://5319852613",
        "rbxassetid://5319850266"
    },
    Patrol = {
        "rbxassetid://1149612882",
        "rbxassetid://1150842221",
        "rbxassetid://1151231493",
        "rbxassetid://1150967949",
        "rbxassetid://1148811837",
        "rbxassetid://1148811837",
        "rbxassetid://1148863382"
    },
    Pirtate = {
        "rbxassetid://750781874",
        "rbxassetid://750782770",
        "rbxassetid://750785693",
        "rbxassetid://750783738",
        "rbxassetid://750782230",
        "rbxassetid://750779899",
        "rbxassetid://750780242"
    },
    Popstar = {
        "rbxassetid://1212900985",
        "rbxassetid://1150842221",
        "rbxassetid://1212980338",
        "rbxassetid://1212980348",
        "rbxassetid://1212954642",
        "rbxassetid://1213044953",
        "rbxassetid://1212900995"
    },
    Princess = {
        "rbxassetid://941003647",
        "rbxassetid://941013098",
        "rbxassetid://941028902",
        "rbxassetid://941015281",
        "rbxassetid://941008832",
        "rbxassetid://940996062",
        "rbxassetid://941000007"
    },
    Robot = {
        "rbxassetid://616088211",
        "rbxassetid://616089559",
        "rbxassetid://616095330",
        "rbxassetid://616091570",
        "rbxassetid://616090535",
        "rbxassetid://616086039",
        "rbxassetid://616087089"
    },
    Rthro = {
        "rbxassetid://2510196951",
        "rbxassetid://2510197257",
        "rbxassetid://2510202577",
        "rbxassetid://2510198475",
        "rbxassetid://2510197830",
        "rbxassetid://2510195892",
        "rbxassetid://02510201162",
        "rbxassetid://2510199791",
        "rbxassetid://2510192778"
    },
    Sneaky = {
        "rbxassetid://1132473842",
        "rbxassetid://1132477671",
        "rbxassetid://1132510133",
        "rbxassetid://1132494274",
        "rbxassetid://1132489853",
        "rbxassetid://1132461372",
        "rbxassetid://1132469004"
    },
    Stylish = {
        "rbxassetid://616136790",
        "rbxassetid://616138447",
        "rbxassetid://616146177",
        "rbxassetid://616140816",
        "rbxassetid://616139451",
        "rbxassetid://616133594",
        "rbxassetid://616134815"
    },
    Superhero = {
        "rbxassetid://782841498",
        "rbxassetid://782845736",
        "rbxassetid://782843345",
        "rbxassetid://782842708",
        "rbxassetid://782847020",
        "rbxassetid://782843869",
        "rbxassetid://782846423"
    },
    Toy = {
        "rbxassetid://782841498",
        "rbxassetid://782845736",
        "rbxassetid://782843345",
        "rbxassetid://782842708",
        "rbxassetid://782847020",
        "rbxassetid://782843869",
        "rbxassetid://782846423"
    },
    Vampire = {
        "rbxassetid://1083445855",
        "rbxassetid://1083450166",
        "rbxassetid://1083473930",
        "rbxassetid://1083462077",
        "rbxassetid://1083455352",
        "rbxassetid://1083439238",
        "rbxassetid://1083443587"
    },
    Werewolf = {
        "rbxassetid://1083195517",
        "rbxassetid://1083214717",
        "rbxassetid://1083178339",
        "rbxassetid://1083216690",
        "rbxassetid://1083218792",
        "rbxassetid://1083182000",
        "rbxassetid://1083189019"
    },
    Zombie = {
        "rbxassetid://616158929",
        "rbxassetid://616160636",
        "rbxassetid://616168032",
        "rbxassetid://616163682",
        "rbxassetid://616161997",
        "rbxassetid://616156119",
        "rbxassetid://616157476"
    }
}

local AnimationsName = {
    "Astronaut",
    "Bubbly",
    "Cartoony",
    "Confindent",
    "Cowboy",
    "Default",
    "Elder",
    "Ghost",
    "Knight",
    "Levitation",
    "Mage",
    "Ninja",
    "OldSchool",
    "Patrol",
    "Pirate",
    "Popstar",
    "Princess",
    "Robot",
    "Rthro",
    'Sneaky',
    "Stylish",
    "Superhero",
    "Toy",
    "Vampire",
    "Werewolf",
    "Zombie"
}

local AnimationState = {
    Idle = "Default",
    Walk = "Default",
    Run = "Default",
    Jump = "Default",
    Climb = "Default",
    Fall = "Default",
}

local PuppywareSettings = {
    Aiming = {
        Aimbot = {
            Enabled = false,
            AimAssist = false,
            IsAiming = false,
            ShowFOV = false,
            FOVColor = Color3.new(0.603921, 0.011764, 1),
            UseNearestDistance = false,
            WallCheck = false,
            KnockedOutCheck = false,
            GrabbedCheck = false,
            Hitboxes = {"Head"}
        },
        TriggerBot = {
            Enabled = false,
            Delay = false,
            DelayAmount = 0
        },
        SilentAim = {
            Enabled = false,
            ShowFOV = false,
            FOVColor = Color3.new(0.603921, 0.011764, 1),
            WallCheck = false,
            KnockedOutCheck = false,
            UseNearestDistance = false,
            GrabbedCheck = false,
            Hitboxes = {"Head"}
        },
        TargetAim = {
            Enabled = false,
            ShowFOV = false,
            FOVColor = Color3.new(0.603921, 0.011764, 1),
            WallCheck = false,
            KnockedOutCheck = false,
            UseNearestDistance = false,
            GrabbedCheck = false,
            Hitboxes = {"Head"},
            Target = nil
        },
        AimbotSettings = {
            AimAssistType = "Camera",
            MovementPrediction = false,
            MovementPredictionAmount = 0.165 * 1,
            SmoothingTracing = false,
            SmoothingTracingAmount = 5
        },
        SilentAimSettings = {
            MovementPrediction = false,
            MovementPredictionAmount = 0.165 * 1,
            HitChance = false,
            HitChanceAmount = {
                HitPercent = 100,
                NotHitPercent = 0
            }
        },
        TargetAimSettings = {
            MovementPrediction = false,
            MovementPredictionAmount = 0.165 * 1,
            HitChance = false,
            HitChanceAmount = {
                HitPercent = 100,
                NotHitPercent = 0
            },
            UnlockTargetKnocked = false,
            NotificationAlert = false,
        },
        FOV = {
            FOVFilled = false,
            AimAssistSize = 100,
            SilentAimSize = 100,
            TargetAimSize = 100
        },
        Whitelist = {
            Players = {},
            Friends = {},
            Holder = "",
            Enabled = false,
            CrewEnabled = false,
            FriendsWhitelist = false
        },
    },
    Blatant = {
        BlatantAA = {
            Enabled = false,
            NoAutoRotate = false,
            UndergroundWallbang = false,
            Underground = false,
            AntiAimType = "Jitter",
            AntiAimSpeed = 100,
            JitterAngle = 180
        },
        LegitAA = {
            Enabled = false,
            AntiAimAt = false,
            AntiAimAtDistance = 20
        },
        FakeLag = {
            Enabled = false,
            TriggerAmount = 5
        },
        Movement = {
            SpeedEnabled = false,
            SpeedType = "Default",
            SpeedRender = "Default",
            SpeedAmount = 5
        },
        Reaching = {
            FistReach = false,
            MeleeReach = false
        },
        Character = {
            AntiGrab = false,
            AntiStomp = false,
            AntiStompType = "Nil Char",
            AntiBag = false,
            AutoArmor = false,
            AutoLettuce = false,
            AutoReload = false
        },
        Farming = {
            ATMFarm = false,
            ShoeFarm = false,
            MuscleFarm = false,
            MuscleFarmingType = "Normal",
            BoxFarm = false,
            HospitalFarm = false,
            ATMPick = false
        },
        Cash = {
            AutoDrop = false,
            AutoDropAmount = 5000,
            AutoPickCash = false
        }
    },
    Teleport = {
        TeleportReturn = false,
        ReturnDelay = false,
        AutoPurchase = false,
        AmmoPurchaseAmount = 1
    }
}

local PuppywareModule = {
    Old = {
        CFrame,
    },
    God = {
        MeleeAlive = false,
        GodMelee = false,
        GodBullet = false,
        AntiRagdoll = false
    },
    LagTick = 0,
    Ignores = {
        "UpperTorso",
        "LowerTorso",
        "Head",
        "LeftHand",
        "LeftUpperArm",
        "LeftLowerArm",
        "RightHand",
        "RightUpperArm",
        "RightLowerArm"
    },
    PingBasedPrediction = 0.165,
    Instance = {},
    Teleport = {
        Players = {},
        Food = {
            "Cranberry",
            "Donut",
            "Pizza",
            "Chicken",
            "Popcorn",
            "Hamburger",
            "Taco",
            "Starblox Latte",
            "Lettuce",
            "Lemonade"
        },
        Location = {
            "Bank",
            "Boxing Place",
            "Police Station",
            "Admin Base",
            "Sewers",
            "Shoe Store",
            "Hospital",
            "Phone Store",
            "Taco Shack",
            "Casino",
            "UFO",
            "Fire Station",
            "Church",
            "Downhill Shop",
            "Uphill Shop"
        },
        Gun = {
            "Glock",
            "SMG",
            "Silencer",
            "TacticalShotgun",
            "P90",
            "AUG",
            "Shotgun",
            "RPG",
            "AR",
            "Double-Barrel SG",
            "Flamethrower",
            "Revolver",
            "LMG",
            "AK47",
            "DrumGun",
            "Silencer",
            "GrenadeLauncher",
            "Taser",
            "SilencerAR",
            "Grenade"
        },
        Armor = {
            "High-Medium Armor",
            "Medium Armor"
        },
        Mask = {
            "Surgeon Mask",
            "Riot Mask",
            "Pitchfork",
            "Hockey Mask",
            "Breathing Mask",
            "Pumpkin Mask",
            "Skull Mask",
            "Paintball Mask",
            "Ninja Mask"
        },
        Weight = {
            "Weights",
            "HeavyWeights"
        },
        Melee = {
            "Shovel",
            "Bat",
            "Pencil",
            "StopSign",
            "Knife",
            "Pitchfork"
        },
        Phone = {
            "iPhone",
            "iPhoneB",
            "iPhoneG",
            "iPhoneP",
            "Old Phone",
            "Orange Phone",
            "Original Phone",
        },
        Bike = {
            "DuoBike",
            "Solo Bike",
        },
        Extra = {
            "PepperSpray",
            "LockPicker",
            "Flashlight",
            "Flowers",
            "Money Gun",
            "Brown Bag",
            "Anti Bodies",
            "Firework"
        }
    }
}

local Window = Library:CreateWindow("w venoware", Vector2.new(492, 598), Enum.KeyCode.RightControl)
local AimingTab = Window:CreateTab("Aiming")

-- Aimbot Setion --

local LegitSection = AimingTab:CreateSector("AIMLOCK", "left")
LegitSection:AddToggle('Enabled', false, function(Boolean)
    PuppywareSettings.Aiming.Aimbot.Enabled = Boolean
end)

local AimAssistToggle = LegitSection:AddToggle('AIM ASSIST', false, function(Boolean)
    PuppywareSettings.Aiming.Aimbot.AimAssist = Boolean
end)

AimAssistToggle:AddKeybind()

local AimbotFOVToggle = LegitSection:AddToggle('SHOW FOV ', false, function(Boolean)
    PuppywareSettings.Aiming.Aimbot.ShowFOV = Boolean
end)

AimbotFOVToggle:AddColorpicker(PuppywareSettings.Aiming.Aimbot.FOVColor, function(Color)
    PuppywareSettings.Aiming.Aimbot.FOVColor = Color
end)

LegitSection:AddToggle('Use CLOSE DISTANCE', false, function(Boolean)
    PuppywareSettings.Aiming.Aimbot.UseNearestDistance = Boolean
end)

LegitSection:AddToggle('WALL CHECK ', false, function(Boolean)
    PuppywareSettings.Aiming.Aimbot.WallCheck = Boolean
end)

LegitSection:AddToggle('Knock Out Check', false, function(Boolean)
    PuppywareSettings.Aiming.Aimbot.KnockedOutCheck = Boolean
end)

LegitSection:AddToggle('Grabbed Check', false, function(Boolean)
    PuppywareSettings.Aiming.Aimbot.GrabbedCheck = Boolean
end)

LegitSection:AddDropdown('HITBOX', {"Head", "HumanoidRootPart"}, {"Head"}, true, function(Value)
    PuppywareSettings.Aiming.Aimbot.Hitboxes = Value
end)



local RageSection = AimingTab:CreateSector("SILIENT AIM ", "left")
local SilentAimToggle = RageSection:AddToggle('Silent Aim Enabled', false, function(Boolean)
    PuppywareSettings.Aiming.SilentAim.Enabled = Boolean
end)

SilentAimToggle:AddKeybind()

local SilentAimFOVToggle = RageSection:AddToggle('Show FOV', false, function(Boolean)
    PuppywareSettings.Aiming.SilentAim.ShowFOV = Boolean
end)

SilentAimFOVToggle:AddColorpicker(Color3.new(0.4839555, 0.011764, 1), function(Color)
    PuppywareSettings.Aiming.SilentAim.FOVColor = Color
end)

RageSection:AddToggle('Use Nearest Distance', false, function(Boolean)
    PuppywareSettings.Aiming.SilentAim.NearestDistance = Boolean
end)

RageSection:AddToggle('Wall Check', false, function(Boolean)
    PuppywareSettings.Aiming.SilentAim.WallCheck = Boolean
end)

RageSection:AddToggle('Knock Out Check', false, function(Boolean)
    PuppywareSettings.Aiming.SilentAim.KnockedOutCheck = Boolean
end)

RageSection:AddToggle('Grabbed Check', false, function(Boolean)
    PuppywareSettings.Aiming.SilentAim.GrabbedCheck = Boolean
end)

RageSection:AddDropdown('Hitboxes', {"Head", "HumanoidRootPart"}, {"Head"}, true, function(Value)
    PuppywareSettings.Aiming.SilentAim.Hitboxes = Value
end)

-- Target Aim Setion --

local RageSection = AimingTab:CreateSector("Target Aim", "left")
local TargetAimToggle = RageSection:AddToggle('Target Aim Enabled', false, function(Boolean)
    PuppywareSettings.Aiming.TargetAim.Enabled = Boolean
end)

TargetAimToggle:AddKeybind()

local SilentAimFOVToggle = RageSection:AddToggle('Show FOV', false, function(Boolean)
    PuppywareSettings.Aiming.TargetAim.ShowFOV = Boolean
end)

SilentAimFOVToggle:AddColorpicker(Color3.new(0.603921, 0.011764, 1), function(Color)
    PuppywareSettings.Aiming.TargetAim.FOVColor = Color
end)

RageSection:AddToggle('WALL CHECK ', false, function(Boolean)
    PuppywareSettings.Aiming.TargetAim.WallCheck = Boolean
end)

RageSection:AddToggle('Knock Out Check', false, function(Boolean)
    PuppywareSettings.Aiming.TargetAim.KnockedOutCheck = Boolean
end)

RageSection:AddToggle('Grabbed Check', false, function(Boolean)
    PuppywareSettings.Aiming.TargetAim.GrabbedCheck = Boolean
end)

RageSection:AddDropdown('Hitboxes', {"Head", "HumanoidRootPart"}, {"Head"}, true, function(Value)
    PuppywareSettings.Aiming.TargetAim.Hitboxes = Value
end)

-- Aim Assist FOV Section --




-- Trigger Bot Section -- 

local TriggerbotSection = AimingTab:CreateSector("Trigger Bot", "left")

local TriggerBotToggle = TriggerbotSection:AddToggle('Trigger Bot Enabled', false, function(State)
    PuppywareSettings.Aiming.TriggerBot.Enabled = State
end)

TriggerBotToggle:AddKeybind()

local TValue = TriggerbotSection:AddToggle('Trigger Bot Delay (ms)', false, function(State)
    PuppywareSettings.Aiming.TriggerBot.Delay = State
end)

TValue:AddSlider(1, 0, 60, 1, function(Value)
    PuppywareSettings.Aiming.TriggerBot.DelayAmount = Value
end)

-- Aimbot Settings Section --

local AimbotSettings = AimingTab:CreateSector("Aimbot Settings", "right")

AimbotSettings:AddDropdown('Aim Assist Type', {"Camera", "Mouse"}, "Camera", false, function(Option)
    PuppywareSettings.Aiming.AimbotSettings.AimAssistType = Option
end)

local MovementPredToggle = AimbotSettings:AddToggle('Movement Prediction', false, function(Boolean)
    PuppywareSettings.Aiming.AimbotSettings.MovementPrediction = Boolean
end)

MovementPredToggle:AddSlider(1, 1, 5, 1, function(Value)
    PuppywareSettings.Aiming.AimbotSettings.MovementPredictionAmount = 0.165 * tonumber("1." ..Value)
end)

local SmoothingTracing = AimbotSettings:AddToggle('Smoothing Tracing', false, function(Boolean)
    PuppywareSettings.Aiming.AimbotSettings.SmoothingTracing = Boolean
end)

SmoothingTracing:AddSlider(2, 5, 10, 1, function(Value)
    PuppywareSettings.Aiming.AimbotSettings.SmoothingTracingAmount = Value
end)

-- Silent Aim Settings Section --

local SilentAimSettings = AimingTab:CreateSector("Silent Aim Settings", "right")

local MovementPredToggle2 = SilentAimSettings:AddToggle('Movement Prediction', false, function(Boolean)
    PuppywareSettings.Aiming.SilentAimSettings.MovementPrediction = Boolean
end)

MovementPredToggle2:AddSlider(1, 1, 5, 1, function(Value)
    PuppywareSettings.Aiming.SilentAimSettings.MovementPredictionAmount = 0.165 * tonumber("1." ..Value)
end)

local HitChanceToggle2 = SilentAimSettings:AddToggle('Hit Chance', false, function(Boolean)
    PuppywareSettings.Aiming.SilentAimSettings.HitChance = Boolean
end)

HitChanceToggle2:AddSlider(0, 100, 100, 1, function(Value)
    PuppywareSettings.Aiming.SilentAimSettings.HitChanceAmount.HitPercent = tonumber(Value)
    PuppywareSettings.Aiming.SilentAimSettings.HitChanceAmount.NotHitPercent = tonumber(100 - PuppywareSettings.Aiming.SilentAimSettings.HitChanceAmount.HitPercent)
end)

-- Target Aim Settings Section --

local TargetAimSettings = AimingTab:CreateSector("Target Aim Settings", "right")

local TargetBind = TargetAimSettings:AddKeybind("Bind", false, function()
    
end, function()
    if PuppywareSettings.Aiming.TargetAim.Enabled then
        local NearestTarget, NearestDistance = NearestMouse()
        if NearestTarget and Visible(NearestTarget.Character.HumanoidRootPart, LocalPlayer.Character.HumanoidRootPart) then
            PuppywareSettings.Aiming.TargetAim.Target = NearestTarget.Name
            if PuppywareSettings.Aiming.TargetAimSettings.NotificationAlert then
                Notify({
                    Title = "Puppyware ðŸ˜³",
                    Description = "Target: " .. NearestTarget.Name,
                    Duration = 3
                })
            end
        end
    end
end)

TargetAimSettings:AddToggle('Unlock Target Knocked', false, function(State)
    PuppywareSettings.Aiming.TargetAimSettings.UnlockTargetKnocked = State
end)

TargetAimSettings:AddToggle('Notification Alert', false, function(State)
    PuppywareSettings.Aiming.TargetAimSettings.NotificationAlert = State
end)

local MovementPredToggle3 = TargetAimSettings:AddToggle('Movement Prediction', false, function(State)
    PuppywareSettings.Aiming.TargetAimSettings.MovementPrediction = State
end)

MovementPredToggle3:AddSlider(1, 1, 5, 1, function(Value)
    PuppywareSettings.Aiming.TargetAimSettings.MovementPredictionAmount = 0.165 * tonumber("1." ..Value)
end)

local HitChanceToggle3 = TargetAimSettings:AddToggle('Hit Chance', false, function(State)
    PuppywareSettings.Aiming.TargetAimSettings.HitChance = State
end)

HitChanceToggle3:AddSlider(0, 100, 100, 1, function(Value)
    PuppywareSettings.Aiming.TargetAimSettings.HitChanceAmount.HitPercent = tonumber(Value)
    PuppywareSettings.Aiming.TargetAimSettings.HitChanceAmount.NotHitPercent = tonumber(100 - PuppywareSettings.Aiming.TargetAimSettings.HitChanceAmount.HitPercent)
end)

local WhitelistSection = AimingTab:CreateSector("Whitelist", "right")

WhitelistSection:AddToggle('Whitelist Enabled', false, function(State)
    PuppywareSettings.Aiming.Whitelist.Enabled = State
end)

WhitelistSection:AddTextbox("Username", nil, function(Text)
    if Text ~= nil and Find(Text) ~= nil and Players:FindFirstChild(Find(Text)) then
        PuppywareSettings.Aiming.Whitelist.Holder = Find(Text)
    else
        Notify({
            Title = "VENO WARE ON TOP",
            Description = "Player is not found.",
            Duration = 3
        })
    end
end)

WhitelistSection:AddButton('Add', function(State)
    if PuppywareSettings.Aiming.Whitelist.Holder ~= nil and Players:FindFirstChild(PuppywareSettings.Aiming.Whitelist.Holder) then
        if table.find(PuppywareSettings.Aiming.Whitelist.Players, PuppywareSettings.Aiming.Whitelist.Holder) then
            Notify({
                Title = "VENO WARE ON TOP",
                Description = PuppywareSettings.Aiming.Whitelist.Holder .. " is whitelisted.",
                Duration = 3
            })
        else
            Insert(PuppywareSettings.Aiming.Whitelist.Players, PuppywareSettings.Aiming.Whitelist.Holder)
            Notify({
                Title = "VENO WARE ON TOP",
                Description = "Whitelisted " .. PuppywareSettings.Aiming.Whitelist.Holder,
                Duration = 3
            })
        end
    else
        Notify({
            Title = "VENO WARE ON TOP",
            Description = "Player is not found.",
            Duration = 3
        })
    end
end)

WhitelistSection:AddButton('Remove', function()
    if PuppywareSettings.Aiming.Whitelist.Holder ~= nil and Players:FindFirstChild(PuppywareSettings.Aiming.Whitelist.Holder) then
        if table.find(PuppywareSettings.Aiming.Whitelist.Players, PuppywareSettings.Aiming.Whitelist.Holder) then
            Remove(PuppywareSettings.Aiming.Whitelist.Players, PuppywareSettings.Aiming.Whitelist.Holder)
            Notify({
                Title = "VENO WARE ON TOP",
                Description = "Removed " .. PuppywareSettings.Aiming.Whitelist.Holder,
                Duration = 5
            })
        else
            Notify({
                Title = "VENO WARE ON TOP",
                Description = PuppywareSettings.Aiming.Whitelist.Holder .. " is not whitelisted.",
                Duration = 5
            })
        end
    else
        Notify({
            Title = "VENO WARE ON TOP",
            Description = "Player is not found.",
            Duration = 3
        })
    end
end)

WhitelistSection:AddToggle('Crew Whitelist', false, function(State)
    PuppywareSettings.Aiming.Whitelist.CrewEnabled = State
end)

WhitelistSection:AddToggle('Friends Whitelist', false, function(State)
    PuppywareSettings.Aiming.Whitelist.FriendsWhitelist = State
end)

-- Visuals Window --

    
local VisualsTab = Window:CreateTab("Visuals")
local ESPSection = VisualsTab:CreateSector("ESP", "left")

local ESPToggle = ESPSection:AddToggle('ESP Enabled', false, function(Boolean)
    
end)

ESPToggle:AddKeybind()

ESPSection:AddToggle('Box ESP', false, function(Boolean)
    
end)

ESPSection:AddToggle('Tracer ESP', false, function(Boolean)
    
end)

ESPSection:AddToggle('Name ESP', false, function(Boolean)
    
end)

ESPSection:AddToggle('Health Bar', false, function(Boolean)
    
end)

ESPSection:AddToggle('Armor Bar', false, function(Boolean)
    
end)

ESPSection:AddToggle("Wall Check", false, function()

end)

local LocalSection = VisualsTab:CreateSector("Local", "left")

local FOVToggle = LocalSection:AddToggle('FOV Changer', false, function(State)

end)

FOVToggle:AddSlider(70, 90, 120, 1, function(Value)
    
end)

local SelfChamToggle = LocalSection:AddToggle('Self Cham', false, function(State)

end)

SelfChamToggle:AddColorpicker(Color3.fromRGB(255, 255, 255), function()

end)

SelfChamToggle:AddDropdown({}, "Ghost", false, function(Option)
    
end)

local FakeLagChamToggle = LocalSection:AddToggle('Fake Lag Cham', false, function(State)

end)

FakeLagChamToggle:AddColorpicker(Color3.fromRGB(255, 255, 255), function()

end)

local CrosshairSection = VisualsTab:CreateSector("Drawing Crosshair", "left")

local DrawingCrosshairToggle = CrosshairSection:AddToggle("Crosshair Enabled", false, function()

end)

DrawingCrosshairToggle:AddColorpicker(Color3.fromRGB(255, 255, 255), function()

end)

CrosshairSection:AddSlider("Gap", 0, 1, 5, 1, function(Value)
    
end)

CrosshairSection:AddSlider("Size", 0, 3, 10, 1, function(Value)
    
end)

local MiscSection = VisualsTab:CreateSector("Misc", "left")

MiscSection:AddToggle("No Flashbag", false, function()

end)

MiscSection:AddToggle("No Recoil", false, function()

end)

local WorldSection = VisualsTab:CreateSector("World", "right")

WorldSection:AddToggle("Better Shadow", false, function()

end)

WorldSection:AddToggle("FullBright", false, function()

end)

local GridiantToggle = WorldSection:AddToggle("Gradiant", false, function()

end)

GridiantToggle:AddColorpicker(Color3.fromRGB(255, 255, 255), function()

end)

GridiantToggle:AddColorpicker(Color3.fromRGB(255, 255, 255), function()

end)

local SaturationToggle = WorldSection:AddToggle("Saturation", false, function()

end)

SaturationToggle:AddSlider(-10, 0, 10, 1, function(Value)
    
end)

local BrightnessToggle = WorldSection:AddToggle("Brightness", false, function()

end)

BrightnessToggle:AddSlider(-10, 0, 10, 1, function(Value)
    
end)

local ContrastToggle = WorldSection:AddToggle("Contrast", false, function()

end)

ContrastToggle:AddSlider(-10, 0, 10, 1, function(Value)
    
end)

local ESPSettings = VisualsTab:CreateSector("ESP Settings", "right")

ESPSettings:AddDropdown('Font', {}, "Plex", false, function(Option)
    
end)

ESPSettings:AddDropdown('Text Case', {"Normal", "Uppercase", "Lowercase"}, "Lowercase", false, function(Option)
    
end)

ESPSettings:AddToggle("Unlock Tracers", false, function()

end)

ESPSettings:AddSlider("Text Size", 5, 14, 20, 1, function(Value)
    
end)

-- Blatant Tab --

local BlatantTab = Window:CreateTab("Blatant")

local MovementSector = BlatantTab:CreateSector("Movement", "right")

local BlatantAntiAimSector = BlatantTab:CreateSector("Blatant Anti Aim", "left")

local SpeedToggle = MovementSector:AddToggle('Speed Enabled', false, function(State)
    PuppywareSettings.Blatant.Movement.SpeedEnabled = State
end)

SpeedToggle:AddKeybind()

SpeedToggle:AddSlider(0, 5, 10, 1, function(Value)
    PuppywareSettings.Blatant.Movement.SpeedAmount = Value
end)

MovementSector:AddDropdown("Speed Type", {"CFrame"}, "CFrame", false, function(Value)
    PuppywareSettings.Blatant.Movement.SpeedType = Value
end)

MovementSector:AddDropdown("Speed Render Type", {"Default", "Fast"}, "Default", false, function(Value)
    PuppywareSettings.Blatant.Movement.SpeedRenderType = Value
end)

local AntiAimToggle = BlatantAntiAimSector:AddToggle('Blatant AA Enabled', false, function(State)
    PuppywareSettings.Blatant.BlatantAA.Enabled = State
end)

AntiAimToggle:AddKeybind()

BlatantAntiAimSector:AddToggle('No Auto Rotate', false, function(State)
    PuppywareSettings.Blatant.BlatantAA.NoAutoRotate = State
end)

BlatantAntiAimSector:AddToggle('Underground', false, function(State)
    PuppywareSettings.Blatant.BlatantAA.Underground = State
end)

BlatantAntiAimSector:AddDropdown("Anti Aim Type", {"Jitter", "Spin"}, "Jitter", false, function(Value)
    PuppywareSettings.Blatant.BlatantAA.AntiAimType = Value
end)

BlatantAntiAimSector:AddSlider("Anti Aim Speed", 0, 100, 300, 1, function(Value)
    PuppywareSettings.Blatant.BlatantAA.AntiAimSpeed = Value
end)

BlatantAntiAimSector:AddSlider("Jitter Angle", 0, 180, 360, 1, function(Value)
    PuppywareSettings.Blatant.BlatantAA.JitterAngle = Value
end)

local LegitAntiAimSector = BlatantTab:CreateSector("Legit Anti Aim", "left")

local LegitAntiAimToggle = LegitAntiAimSector:AddToggle('Legit AA Enabled', false, function(State)
    PuppywareSettings.Blatant.LegitAA.Enabled = Value
end)

LegitAntiAimSector:AddToggle('Anti Aim At', false, function(State)
    PuppywareSettings.Blatant.LegitAA.AntiAimAt = State
end)

LegitAntiAimSector:AddSlider("Anti Aim At Distance", 2.5, 20, 100, 1, function(Value)
    PuppywareSettings.Blatant.LegitAA.AntiAimAtDistance = Value
end)

local FakeLagSector = BlatantTab:CreateSector("Fake Lag", "left")

local FakeLagToggle = FakeLagSector:AddToggle('Fake Lag Enabled', false, function(State)
    PuppywareSettings.Blatant.FakeLag.Enabled = State
end)

FakeLagToggle:AddKeybind()

FakeLagToggle:AddSlider(1, 5, 10, 1, function(Value)
    PuppywareSettings.Blatant.FakeLag.TriggerAmount = Value
end)

local MiscSector = BlatantTab:CreateSector("Misc", "left")

MiscSector:AddButton('Invisible', function(State)
    Invisible()
end)

MiscSector:AddButton('Nil Char', function(State)
    NilBody()
end)


    MiscSector:AddButton('Unjail', function(State)

    end)

local NilCharBind = MiscSector:AddKeybind("Nil Char Bind", false, function()
    
end, function()
    NilBody()
end)

local GodModeSector = BlatantTab:CreateSector("God Mode", "left")

GodModeSector:AddButton("Gun Only", function()
    PuppywareModule.God.GodBullet = true
    NilBody()
end)

GodModeSector:AddButton("Melee Only", function()
    PuppywareModule.God.GodMelee = true
    NilBody()
end)

GodModeSector:AddButton("Anti Ragdoll", function()
    PuppywareModule.God.AntiRagdoll = true
    NilBody()
end)

GodModeSector:AddButton("God Block", function()
    pcall(function()
        LocalPlayer.Character.BodyEffects.Defense.CurrentTimeBlock:Destroy()
    end)
end)

local ReachingSector = BlatantTab:CreateSector("Reaching", "right")

local FistReachToggle = ReachingSector:AddToggle('Fist Reach', false, function(State)
    PuppywareSettings.Blatant.Reaching.FistReach = State
end)

FistReachToggle:AddKeybind()

local MeleeReachToggle = ReachingSector:AddToggle('Melee Reach', false, function(State)
    PuppywareSettings.Blatant.Reaching.MeleeReach = State
end)

MeleeReachToggle:AddKeybind()

local CharacterSector = BlatantTab:CreateSector("Character", "right")

CharacterSector:AddToggle('Anti Stomp', false, function(State)
    PuppywareSettings.Blatant.Character.AntiStomp = State
end)

CharacterSector:AddDropdown("Anti Stomp Type", {"Show Body", "Nil Char"}, "Nil Char", false, function(State)
    PuppywareSettings.Blatant.Character.AntiStompType = State
end)

CharacterSector:AddToggle('Anti Bag', false, function(State)
    PuppywareSettings.Blatant.Character.AntiBag = State
end)

CharacterSector:AddToggle('Anti Grab', false, function(State)
    PuppywareSettings.Blatant.Character.AntiGrab = State
end)

CharacterSector:AddToggle('Auto Lettuce', false, function(State)
    PuppywareSettings.Blatant.Character.AutoLettuce = State
end)

CharacterSector:AddToggle('Auto Armor', false, function(State)
    PuppywareSettings.Blatant.Character.AutoArmor = State
end)

CharacterSector:AddToggle('Auto Reload', false, function(State)
    PuppywareSettings.Blatant.Character.AutoReload = State
end)

local FarmingSector = BlatantTab:CreateSector("Farming", "right")

FarmingSector:AddToggle('Shoe Farm', false, function(State)
    PuppywareSettings.Blatant.Farming.ShoeFarm = State
end)

FarmingSector:AddToggle('ATM Farm', false, function(State)
    PuppywareSettings.Blatant.Farming.ATMFarm = State
end)

FarmingSector:AddToggle('Hospital Farm', false, function(State)
    PuppywareSettings.Blatant.Farming.HospitalFarm = State
end)

local BoxFarmToggle = FarmingSector:AddToggle('Box Farm', false, function(State)
    PuppywareSettings.Blatant.Farming.BoxFarm = State
end)

BoxFarmToggle:AddKeybind()

FarmingSector:AddDropdown("Muscle Farming Type", {"Normal", "Heavy"}, "Normal", false, function(State)
    PuppywareSettings.Blatant.Farming.MuscleFarmingType = State
end)

FarmingSector:AddToggle('Muscle Farm', false, function(State)
    PuppywareSettings.Blatant.Farming.MuscleFarm = State
end)

local CashSector = BlatantTab:CreateSector("Cash", "right")

local AutoDropToggle = CashSector:AddToggle("Auto Drop", false, function(State)
    PuppywareSettings.Blatant.Cash.AutoDrop = State
end)

AutoDropToggle:AddSlider(1000, 5000, 10000, 1, function(Value)
    PuppywareSettings.Blatant.Cash.AutoDropAmount = Value
end)

CashSector:AddToggle("Auto Pick Cash", false, function(State)
    PuppywareSettings.Blatant.Cash.AutoPickCash = State
end)

-- Auto Buy Tab --

local TeleportTab = Window:CreateTab("Teleport")

local TeleportModule = {
    Food = PuppywareModule.Teleport.Food[1],
    Gun = PuppywareModule.Teleport.Gun[1],
    Location = PuppywareModule.Teleport.Location[1],
    Armor = PuppywareModule.Teleport.Armor[1],
    Melee = PuppywareModule.Teleport.Melee[1],
    Extra = PuppywareModule.Teleport.Extra[1],
    Bike = PuppywareModule.Teleport.Bike[1],
    Mask = PuppywareModule.Teleport.Mask[1],
    Phone = PuppywareModule.Teleport.Phone[1],
    Weight = PuppywareModule.Teleport.Weight[1],
    AutoSet = {
        Tools = {}
    }
}

local FoodSector = TeleportTab:CreateSector("Food Teleport", "left")
FoodSector:AddDropdown("Food Selection", PuppywareModule.Teleport.Food, PuppywareModule.Teleport.Food[1], false, function(Value)
    TeleportModule.Food = Value
end)

FoodSector:AddButton("Teleport", function()
    TeleportBuy(ToolName(TeleportModule.Food))
end)

local GunSector = TeleportTab:CreateSector("Gun Teleport", "left")
GunSector:AddDropdown("Gun Selection", PuppywareModule.Teleport.Gun, PuppywareModule.Teleport.Gun[1], false, function(Value)
    TeleportModule.Gun = Value
end)

GunSector:AddButton("Teleport", function()
    TeleportBuy(ToolName(TeleportModule.Gun))
    spawn(function()
        for i = 1, PuppywareSettings.Teleport.AmmoPurchaseAmount do
            TeleportBuy(ToolAmmo(TeleportModule.Gun))
            wait(1)
        end
    end)
end)

local LocationSector = TeleportTab:CreateSector("Location Teleport", "left")
LocationSector:AddDropdown("Location Selection", PuppywareModule.Teleport.Location, PuppywareModule.Teleport.Location[1], false, function(Value)
    TeleportModule.Location = Value
end)

LocationSector:AddButton("Teleport", function()
    TeleportBuy(ToolName(TeleportModule.Location))
end)

local ArmorSector = TeleportTab:CreateSector("Armor Teleport", "left")
ArmorSector:AddDropdown("Armor Selection", PuppywareModule.Teleport.Armor, PuppywareModule.Teleport.Armor[1], false, function(Value)
    TeleportModule.Armor = Value
end)

ArmorSector:AddButton("Teleport", function()
    TeleportBuy(ToolName(TeleportModule.Armor))
end)

local MeleeSector = TeleportTab:CreateSector("Melee Teleport", "left")
MeleeSector:AddDropdown("Melee Selection", PuppywareModule.Teleport.Melee, PuppywareModule.Teleport.Melee[1], false, function(Value)
    TeleportModule.Melee = Value
end)

MeleeSector:AddButton("Teleport", function()
    TeleportBuy(ToolName(TeleportModule.Melee))
end)

local ExtraSector = TeleportTab:CreateSector("Extra Teleport", "left")
ExtraSector:AddDropdown("Extra Selection", PuppywareModule.Teleport.Extra, PuppywareModule.Teleport.Extra[1], false, function(Value)
    TeleportModule.Extra = Value
end)

ExtraSector:AddButton("Teleport", function()
    TeleportBuy(ToolName(TeleportModule.Extra))
end)

local BikeSector = TeleportTab:CreateSector("Bike Teleport", "left")
BikeSector:AddDropdown("Bike Selection", PuppywareModule.Teleport.Bike, PuppywareModule.Teleport.Bike[1], false, function(Value)
    TeleportModule.Bike = Value
end)

BikeSector:AddButton("Teleport", function()
    TeleportBuy(ToolName(TeleportModule.Bike))
end)

local MaskSector = TeleportTab:CreateSector("Mask Teleport", "left")
MaskSector:AddDropdown("Mask Selection", PuppywareModule.Teleport.Mask, PuppywareModule.Teleport.Mask[1], false, function(Value)
    TeleportModule.Mask = Value
end)

MaskSector:AddButton("Teleport", function()
    TeleportBuy(ToolName(TeleportModule.Mask))
end)

local PhoneSector = TeleportTab:CreateSector("Phone Teleport", "left")
PhoneSector:AddDropdown("Phone Selection", PuppywareModule.Teleport.Phone, PuppywareModule.Teleport.Phone[1], false, function(Value)
    TeleportModule.Phone = Value
end)

PhoneSector:AddButton("Teleport", function()
    TeleportBuy(ToolName(TeleportModule.Phone))
end)

local WeightSector = TeleportTab:CreateSector("Weight Teleport", "left")
WeightSector:AddDropdown("Weight Selection", PuppywareModule.Teleport.Weight, PuppywareModule.Teleport.Weight[1], false, function(Value)
    TeleportModule.Weight = Value
end)

WeightSector:AddButton("Teleport", function()
    TeleportBuy(ToolName(TeleportModule.Weight))
end)

local TeleportSettings = TeleportTab:CreateSector("Teleport Settings", "right")
TeleportSettings:AddToggle("Teleport Return", false, function(State)
    PuppywareSettings.Teleport.TeleportReturn = State
end)

TeleportSettings:AddSlider("Return Delay", 0, 1, 100, 1, function(Value)
    PuppywareSettings.Teleport.ReturnDelay = Value
end)

TeleportSettings:AddToggle("Auto Purchase", false, function(State)
    PuppywareSettings.Teleport.AutoPurchase = State
end)

TeleportSettings:AddSlider("Ammo Purchase Amount", 0, 1, 100, 1, function(Value)
    PuppywareSettings.Teleport.AmmoPurchaseAmount = Value
end)

local AutoSetTab = TeleportTab:CreateSector("Auto Set", "right")
for i, v in pairs(PuppywareModule.Teleport.Armor) do
    AutoSetTab:AddToggle(v, false, function(State)
        if State then
            if not table.find(TeleportModule.AutoSet.Tools, v) then
                table.insert(TeleportModule.AutoSet.Tools, v)
            end
        else
            Remove(TeleportModule.AutoSet.Tools, v)
        end
    end)
end

for i, v in pairs(PuppywareModule.Teleport.Gun) do
    AutoSetTab:AddToggle(v, false, function(State)
        if State then
            if not table.find(TeleportModule.AutoSet.Tools, v) then
                table.insert(TeleportModule.AutoSet.Tools, v)
            end
        else
            Remove(TeleportModule.AutoSet.Tools, v)
        end
    end)
end

AutoSetTab:AddButton("Teleport", function()
    if Alive(LocalPlayer) then
        for i, v in pairs(TeleportModule.AutoSet.Tools) do
            if string.find(v:lower(), "armor") then
                if PuppywareSettings.Teleport.ArmorValueCheck and LocalPlayer.Character.BodyEffects.Armor.Value < 0 then
                    TeleportBuy(ToolName(v, true))
                else
                    TeleportBuy(ToolName(v, true))
                end
            else
                TeleportBuy(ToolName(v, true))
                spawn(function()
                    for i = 1, PuppywareSettings.Teleport.AmmoPurchaseAmount do
                        TeleportBuy(ToolAmmo(v), true)
                        wait(1)
                    end
                end)
            end
        end
    end
end)

-- Miscellaneous Window --
local MiscellaneousTab = Window:CreateTab("Miscellaneous")

LocalPlayer.CharacterAdded:Connect(function()
    wait(0.5)
    PuppywareModule.God.GodMeleeAlive = false
    if LocalPlayer.Character:FindFirstChild("BodyEffects") then
        if PuppywareModule.God.GodBullet then
            GodFunction(PuppywareModule.God.GodBullet)
            LocalPlayer.Character.BodyEffects.BreakingParts:Destroy()
        end
        if PuppywareModule.God.GodMelee then
            GodFunction(PuppywareModule.God.GodMelee)
            PuppywareModule.God.GodMeleeAlive = true
            LocalPlayer.Character.BodyEffects.Armor:Destroy()
            LocalPlayer.Character.BodyEffects.Defense:Destroy()
        end
        if PuppywareModule.God.AntiRagdoll then
            GodFunction(PuppywareModule.God.AntiRagdoll)
        end
    end
    wait(0.5)
    if PuppywareSettings.Blatant.BlatantAA.Underground then
        Underground(true)
    end
    wait(0.4)
    if PuppywareSettings.Blatant.BlatantAA.UndergroundWallbang then
        Float = Instance.new("BodyVelocity")
        Float.Parent = LocalPlayer.Character.HumanoidRootPart
        Float.MaxForce = Vector3.new(100000, 100000, 100000)
        Float.Velocity = Vector3.new(0, 0, 0)
        wait(0.25)
        LocalPlayer.Character.HumanoidRootPart.CFrame = LocalPlayer.Character.HumanoidRootPart.CFrame * CFrame.new(0, -11.5, 0)
        Cham(LocalPlayer, true)
        PuppywareSettings.Blatant.BlatantAA.UndergroundWallbang = true
    end
    LocalPlayer.Character.Animate.idle.Animation1.AnimationId = AnimationModule[AnimationState.Idle][1]
    LocalPlayer.Character.Animate.idle.Animation2.AnimationId = AnimationModule[AnimationState.Idle][2]
    LocalPlayer.Character.Animate.walk.WalkAnim.AnimationId = AnimationModule[AnimationState.Walk][3]
    LocalPlayer.Character.Animate.run.RunAnim.AnimationId = AnimationModule[AnimationState.Run][4]
    LocalPlayer.Character.Animate.jump.JumpAnim.AnimationId = AnimationModule[AnimationState.Jump][5]
    LocalPlayer.Character.Animate.climb.ClimbAnim.AnimationId = AnimationModule[AnimationState.Climb][6]
    LocalPlayer.Character.Animate.fall.FallAnim.AnimationId = AnimationModule[AnimationState.Fall][7]
    for i, v in pairs(AnimationState) do
        print(i, v)
    end
end)

local AnimationSector = MiscellaneousTab:CreateSector("Animation", "left")
AnimationSector:AddDropdown("Idle", AnimationsName, "Default", false, function(State)
    if Alive(LocalPlayer) then
        LocalPlayer.Character.Animate.idle.Animation1.AnimationId = AnimationModule[State][1]
        LocalPlayer.Character.Animate.idle.Animation2.AnimationId = AnimationModule[State][2]
        AnimationState.Idle = State
    end
end)

AnimationSector:AddDropdown("Walk", AnimationsName, "Default", false, function(State)
    if Alive(LocalPlayer) then
        LocalPlayer.Character.Animate.walk.WalkAnim.AnimationId = AnimationModule[State][3]
        AnimationState.Walk = State
    end
end)

AnimationSector:AddDropdown("Run", AnimationsName, "Default", false, function(State)
    if Alive(LocalPlayer) then
        LocalPlayer.Character.Animate.run.RunAnim.AnimationId = AnimationModule[State][4]
        AnimationState.Run = State
    end
end)

AnimationSector:AddDropdown("Jump", AnimationsName, "Default", false, function(State)
    if Alive(LocalPlayer) then
        LocalPlayer.Character.Animate.jump.JumpAnim.AnimationId = AnimationModule[State][5]
        AnimationState.Jump = State
    end
end)

AnimationSector:AddDropdown("Climb", AnimationsName, "Default", false, function(State)
    if Alive(LocalPlayer) then
        LocalPlayer.Character.Animate.climb.ClimbAnim.AnimationId = AnimationModule[State][6]
        AnimationState.Climb = State
    end
end)

AnimationSector:AddDropdown("Fall", AnimationsName, "Default", false, function(State)
    if Alive(LocalPlayer) then
        LocalPlayer.Character.Animate.fall.FallAnim.AnimationId = AnimationModule[State][7]
        AnimationState.Fall = State
    end
end)


local RadioSector = MiscellaneousTab:CreateSector("Radio Playlist", "left")

RadioSector:AddDropdown("Playlist", {}, "", false, function()

end)

RadioSector:AddLabel("Current Song: ")

RadioSector:AddButton("Add", function()

end)

RadioSector:AddButton("Remove", function()

end)

RadioSector:AddButton("Play", function()

end)

RadioSector:AddButton("Stop", function()

end)

local KillInsultsSector = MiscellaneousTab:CreateSector("Kill Insults", "right")

KillInsultsSector:AddToggle("Kill Insults Enabled", false, function()

end)

KillInsultsSector:AddToggle("Custom Message", false, function()

end)

KillInsultsSector:AddSlider("Delay (ms)", 0, 0, 5, 1, function(Value)
    
end)

KillInsultsSector:AddDropdown("Messages", {}, "", false, function()

end)

KillInsultsSector:AddTextbox("Message", "@Username is bad.", function(Text)
    
end)

KillInsultsSector:AddButton("Add", function()

end)

KillInsultsSector:AddButton("Remove", function()

end)

local CustomModelSector = MiscellaneousTab:CreateSector("Custom Model", "right")

CustomModelSector:AddToggle("Custom Model Enabled", false, function()

end)

CustomModelSector:AddDropdown("Models", {"Among Us", "19$ Fortnite Card"}, "Among Us", false, function()

end)

CustomModelSector:AddToggle("Edit Mode", false, function()

end)

CustomModelSector:AddSlider("Position X", 0, 0, 360, 1, function(Value)
    
end)

CustomModelSector:AddSlider("Position Y", 0, 0, 360, 1, function(Value)
    
end)

CustomModelSector:AddSlider("Position Z", 0, 0, 360, 1, function(Value)
    
end)

CustomModelSector:AddSlider("Position Rotation", 0, 0, 360, 1, function(Value)
    
end)

local ServerSector = MiscellaneousTab:CreateSector("Server", "left")

ServerSector:AddLabel("Crashing Rate: 0%")

ServerSector:AddToggle("Server Crash", false, function()

end)

ServerSector:AddButton("Rejoin", function()

end)

ServerSector:AddButton("Server Hop", function()

end)

local PanicSector = MiscellaneousTab:CreateSector("Panic", "right")

PanicSector:AddDropdown("Panic Type", {"Da Hood Moderator", "Player Joined"}, "Da Hood Moderator", false, function()

end)

PanicSector:AddToggle("Panic Enabled", false, function()

end)

-- Settings Window --

local SettingsTab = Window:CreateTab("Settings")

SettingsTab:CreateConfigSystem("left")

-- Init --

for _, v in next, Players:GetPlayers() do
    if v ~= LocalPlayer and v:IsFriendsWith(LocalPlayer.UserId) then
        Insert(PuppywareSettings.Aiming.Whitelist.Friends, v.Name)
    end
end

Players.PlayerAdded:Connect(function(_Player)
    if _Player ~= LocalPlayer and _Player:IsFriendsWith(LocalPlayer.UserId) then
        Insert(PuppywareSettings.Aiming.Whitelist.Friends, _Player.Name)
    end
end)

Players.PlayerRemoving:Connect(function(_Player)
    if _Player ~= LocalPlayer and _Player:IsFriendsWith(LocalPlayer.UserId) then
        Module.Functions.TableRemove(PuppywareSettings.Aiming.Whitelist.Friends, _Player.Name)
    end
end)

function NoSpace(Data)
    return Data:gsub("%s+", "") or Data
end
    
function Find(Data)
    local Target = nil
    
    for i, v in next, Players:GetPlayers() do
        if v.Name ~= LocalPlayer.Name and v.Name:lower():match('^'.. NoSpace(Data):lower()) then
            Target = v.Name
        end
    end
    
    return Target
end

function Alive(Player)
    if Player and Player.Character and Player.Character:FindFirstChild("HumanoidRootPart") ~= nil and Player.Character:FindFirstChild("Humanoid") ~= nil and Player.Character:FindFirstChild("Head") ~= nil then
        return true
    end
    return false
end

function Knocked(Player)
    if Alive(Player) then
        if Player.Character.BodyEffects["K.O"].Value then
            return true
        end
        return false
    end
    return false
end

function Grabbing(Player)
    if Alive(Player) then
        if Player.Character:FindFirstChild("GRABBING_CONSTRAINT") then
            return true
        end
        return false
    end
    return false
end

function NearestDistance()
    local Target = nil
    local Distance = math.huge
    
    for i, v in next, Players:GetPlayers() do
        if v ~= LocalPlayer and Alive(LocalPlayer) and Alive(v) then
            local DistanceFromPlayer = (v.Character.HumanoidRootPart.Position - LocalPlayer.Character.HumanoidRootPart.Position).Magnitude
            if Distance > DistanceFromPlayer then
                if (not PuppywareSettings.Aiming.Whitelist.FriendsWhitelist or not table.find(PuppywareSettings.Aiming.Whitelist.Friends, v.Name)) and (not PuppywareSettings.Aiming.Whitelist.CrewEnabled or v:FindFirstChild("DataFolder") and v.DataFolder.Information:FindFirstChild("Crew") and not tonumber(v.DataFolder.Information.Crew.Value) == tonumber(LocalPlayer.DataFolder.Information.Crew.Value)) and (not PuppywareSettings.Aiming.Whitelist.Enabled or not table.find(PuppywareSettings.Aiming.Whitelist.Players, v.Name)) then
                    Target = v
                    Distance = DistanceFromPlayer
                end
            end
        end
    end

    return Target, Distance
end

function NearestMouse()
    local Target = nil
    local Distance = math.huge

    for i, v in next, Players:GetPlayers() do
        if v ~= LocalPlayer and Alive(LocalPlayer) and Alive(v) then
            local RootPosition, RootVisible = CurrentCamera:WorldToViewportPoint(v.Character.HumanoidRootPart.Position)
            local DistanceFromMouse = (Vector2.new(RootPosition.X, RootPosition.Y) - Vector2.new(Mouse.X, Mouse.Y)).Magnitude
            if RootVisible and Distance > DistanceFromMouse then
                if (not PuppywareSettings.Aiming.Whitelist.FriendsWhitelist or not table.find(PuppywareSettings.Aiming.Whitelist.Friends, v.Name)) and (not PuppywareSettings.Aiming.Whitelist.CrewEnabled or v:FindFirstChild("DataFolder") and v.DataFolder.Information:FindFirstChild("Crew") and not tonumber(v.DataFolder.Information.Crew.Value) == tonumber(LocalPlayer.DataFolder.Information.Crew.Value)) and (not PuppywareSettings.Aiming.Whitelist.Enabled or not table.find(PuppywareSettings.Aiming.Whitelist.Players, v.Name)) then
                    Target = v
                    Distance = DistanceFromMouse
                end
            end
        end
    end

    return Target, Distance
end

function NearestType(Type)
    if Type == "Distance" then
        return NearestDistance()
    elseif Type == "Mouse" then
        return NearestMouse()
    end
end

function Jitter(Speed, Angle)
    if Alive(LocalPlayer) then
        local Jit = Speed or math.random(30, 90)
        LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(LocalPlayer.Character.HumanoidRootPart.CFrame.Position) * CFrame.Angles(0, math.rad(Angle) + math.rad((math.random(1, 2) == 1 and Jit or -Jit)), 0) 
    end
end

function TableLowerFind(Table, CurrentName)
    local TableName
    for i, v in pairs(Table) do
        if string.find(CurrentName:gsub("%[", ""):gsub("%]", ""):lower(), v:lower()) then
            TableName = v
        end
    end
    return TableName
end
    
function Spin(Speed)
    if Alive(LocalPlayer) then
        LocalPlayer.Character.HumanoidRootPart.CFrame = LocalPlayer.Character.HumanoidRootPart.CFrame * CFrame.Angles(0, math.rad(Speed), 0)
    end
end

function TeleportBuy(Target, AutoSetDelay)
    if workspace.Ignored.Shop:FindFirstChild(Target) and Alive(LocalPlayer) then
        PuppywareModule.Old.CFrame = LocalPlayer.Character.HumanoidRootPart.CFrame
        wait(0.05)
        LocalPlayer.Character.HumanoidRootPart.CFrame = Workspace.Ignored.Shop[Target].Head.CFrame * CFrame.new(0, 3, 0)
        wait(0.15)
        if PuppywareSettings.Teleport.AutoPurchase then
            for i = 1, 10 do
                fireclickdetector(Workspace.Ignored.Shop[Target].ClickDetector)
            end
        end
        if PuppywareSettings.Teleport.TeleportReturn then
            wait(PuppywareSettings.Teleport.ReturnDelay)
            LocalPlayer.Character.HumanoidRootPart.CFrame = PuppywareModule.Old.CFrame  
        end
        if AutoSetDelay then
            wait(1)
        end
    end
end

function Buy(Target, Delay, LagBack)
    if workspace.Ignored.Shop:FindFirstChild(Target) and Alive(LocalPlayer) then
        PuppywareModule.Old.CFrame = LocalPlayer.Character.HumanoidRootPart.CFrame
        wait(0.05)
        LocalPlayer.Character.HumanoidRootPart.CFrame = Workspace.Ignored.Shop[Target].Head.CFrame * CFrame.new(0, 3, 0)
        wait(0.15)
        for i = 1, 3 do
            fireclickdetector(Workspace.Ignored.Shop[Target].ClickDetector)
        end
        if LagBack then
            wait(1)
            LocalPlayer.Character.HumanoidRootPart.CFrame = PuppywareModule.Old.CFrame  
        end
        if Delay ~= nil then
            wait(Delay)
        end
    end
end

function Visible(OriginPart, Part)
    if Alive(LocalPlayer) then
        local IgnoreList = {CurrentCamera, LocalPlayer.Character, OriginPart.Parent}
        local Parts = CurrentCamera:GetPartsObscuringTarget({OriginPart.Position, Part.Position}, IgnoreList)
    
        for i, v in pairs(Parts) do
            if v.Transparency >= 0.3 then
                PuppywareModule.Instance[#PuppywareModule.Instance + 1] = v
            end
    
            if v.Material == Enum.Material.Glass then
                PuppywareModule.Instance[#PuppywareModule.Instance + 1] = v
            end
        end
    
        return #Parts == 0
    end
    return true
end

function ToolName(Name)
    for Check = 1, 100000 do
        if Workspace.Ignored.Shop:FindFirstChild("[" .. Name .. "] - $" .. Check) then
            return tostring("[" .. Name .. "] - $" .. Check)
        end
    end
end

function ToolAmmo(Name)
    for Check1 = 1, 250 do
        for Check2 = 1, 250 do
            if Workspace.Ignored.Shop:FindFirstChild(Check1 .. " [" .. Name .. " Ammo] - $" .. Check2) then
                return tostring(Check1 .. " [" .. Name .. " Ammo] - $" .. Check2)
            end
        end
    end
end

function Invisible()
    if Alive(LocalPlayer) then
        PuppywareModule.Old.CFrame = LocalPlayer.Character.HumanoidRootPart.CFrame
        print(PuppywareModule.Old.CFrame)
        wait(0.1)
        LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(0, 96995694596945934234234234, 0)
        wait(0.1)
        LocalPlayer.Character.LowerTorso.Root:Destroy()
        for _, v in pairs(LocalPlayer.Character:GetChildren()) do
            if v:IsA("MeshPart") and not table.find(PuppywareModule.Ignores, v.Name) then
                v:Destroy()
            end
        end
        wait(0.1)
        LocalPlayer.Character.HumanoidRootPart.CFrame = PuppywareModule.Old.CFrame
    end
end

function NilBody()
    if Alive(LocalPlayer) then
        for i, v in pairs(LocalPlayer.Character:GetChildren()) do
            if v:IsA("BasePart") or v:IsA("Part") or v:IsA("MeshPart") then
                if v.Name ~= "HumanoidRootPart" then
                    v:Destroy()
                end
            end
        end
    end
end

function ChanceTable(Table)
    local Chance = 0
    for i, v in pairs(Table) do
        Chance = Chance + v
    end
    Chance = math.random(0, Chance)
    for i, v in pairs(Table) do
        Chance = Chance - v
        if Chance <= 0 then
            return i
        end
    end	
end

function RandomTable(Table)
    local Values = 0
    for i, v in pairs(Table) do
        Values = i
    end
    
    return Table[math.random(1, Values)]
end

function Remove(Data, Data2)
    for i, v in pairs(Data) do
        if v == Data2 then
            table.remove(Data, i)
        end
    end
end

function GodFunction(Variable)
    LocalPlayer.Character.RagdollConstraints:Destroy()
    local Folder = Instance.new("Folder", LocalPlayer.Character)
    Folder.Name = "FULLY_LOADED_CHAR"
    wait()
    StarterGui:SetCoreGuiEnabled(Enum.CoreGuiType.Backpack, true)
    Variable = false
end

function Cham(Data, State)
    local BoxVar = nil
    local GlowVar = nil
    if State then
        for _, v in pairs(Data.Character:GetChildren()) do
            if v:IsA("BasePart") and v.Transparency ~= 1 then
                if not v:FindFirstChild("Box") then
                    BoxVar = Instance.new("BoxHandleAdornment", v)
                    BoxVar.Name = "Box"
                    BoxVar.AlwaysOnTop = true
                    BoxVar.ZIndex = 4
                    BoxVar.Adornee = v
                    BoxVar.Color3 = Color3.fromRGB(0, 153, 153)
                    BoxVar.Transparency = 0.5
                    BoxVar.Size = v.Size + Vector3.new(0.02, 0.02, 0.02)
                end
            end
        end
    else
        for i, v in pairs(Data.Character:GetChildren()) do
            if v:IsA("BasePart") and v.Transparency ~= 1 then
                if v:FindFirstChild("Box") then
                    v["Box"]:Destroy()
                end
            end
        end
        
        return BoxVar, GlowVar
    end
end

UserInputService.InputBegan:Connect(function(Key, Event)
    if Key.UserInputType == Enum.UserInputType.MouseButton2 and not Event then
        PuppywareSettings.Aiming.Aimbot.IsAiming = true
    end
end)

UserInputService.InputEnded:Connect(function(Key, Event)
    if Key.UserInputType == Enum.UserInputType.MouseButton2 and not Event then
        PuppywareSettings.Aiming.Aimbot.IsAiming = false
    end
end)

RunService.Heartbeat:Connect(function()
    if Alive(LocalPlayer) then
        if PuppywareSettings.Blatant.Movement.SpeedEnabled and PuppywareSettings.Blatant.Movement.SpeedType == "CFrame" then
            if PuppywareSettings.Blatant.Movement.SpeedRenderType == "Default" then
                if LocalPlayer.Character.Humanoid.MoveDirection.Magnitude > 0 then
                    for i = 1, PuppywareSettings.Blatant.Movement.SpeedAmount do
                        LocalPlayer.Character:TranslateBy(LocalPlayer.Character.Humanoid.MoveDirection)
                    end
                end
            end
        end
        if PuppywareSettings.Blatant.Character.AntiStomp then
            if Knocked(LocalPlayer) then
                if PuppywareSettings.Blatant.Character.AntiStompType == "Nil Char" then
                    NilBody()
                end
                if PuppywareSettings.Blatant.Character.AntiStompType == "Show Body" then
                    pcall(function()
                        LocalPlayer.Character.Humanoid:Destroy()
                    end)
                end
            end
        end
        if PuppywareSettings.Blatant.Character.AntiBag then
            if LocalPlayer.Character:FindFirstChild("Christmas_Sock") then
                LocalPlayer.Character:FindFirstChild("Christmas_Sock"):Destroy()
            end
        end
        if PuppywareSettings.Blatant.Character.AntiGrab and LocalPlayer.Character:FindFirstChild("GRABBING_CONSTRAINT") then
            LocalPlayer.Character["GRABBING_CONSTRAINT"]:Destroy()
        end
    end
end)

RunService.Stepped:Connect(function()
	if PuppywareSettings.Blatant.BlatantAA.UndergroundWallbang then
		for i, v in pairs(LocalPlayer.Character:GetDescendants()) do
			if v:IsA("BasePart") and v.CanCollide == true then
				v.CanCollide = false
			end
		end
	end
end)

spawn(function()
    while wait() do
        if Alive(LocalPlayer) then
            if PuppywareSettings.Blatant.Character.AutoLettuce then
                pcall(function()
                    Buy("[Lettuce] - $5", 1)
                    if LocalPlayer.Backpack:FindFirstChild("[Lettuce]") then
                        LocalPlayer.Character.Humanoid:EquipTool(LocalPlayer.Backpack["[Lettuce]"])
                    end
                    wait(0.5)
                    LocalPlayer.Character["[Lettuce]"]:Activate()
                end)
            end
            if PuppywareSettings.Blatant.Character.AutoReload then
                local Gun = LocalPlayer.Character:FindFirstChildOfClass("Tool")
                if Gun ~= nil and Gun:FindFirstChild("MaxAmmo") then
                    if Gun.Ammo.Value == 0 then
                        ReplicatedStorage.MainEvent:FireServer("Reload", Gun)
                    end
                end
            end
            if PuppywareSettings.Blatant.Character.AutoArmor then
                if LocalPlayer.Character.BodyEffects.Armor.Value == 0 then
                    Buy("[High-Medium Armor] - $2300", 0.5, true)
                end
            end
            if PuppywareSettings.Blatant.Farming.MuscleFarm then
                pcall(function()
                    if PuppywareSettings.Blatant.Farming.MuscleFarmingType == "Normal" then
                        if not LocalPlayer.Backpack:FindFirstChild("[Weights]") then
                            Buy("[Weights] - $120", 1)
                        end
                        if LocalPlayer.Backpack:FindFirstChild("[Weights]") then
                            LocalPlayer.Character.Humanoid:EquipTool(LocalPlayer.Backpack["[Weights]"])
                        end
                        LocalPlayer.Character["[Weights]"]:Activate()
                    end
                    if PuppywareSettings.Blatant.Farming.MuscleFarmingType == "Heavy" then
                        if not LocalPlayer.Backpack:FindFirstChild("[HeavyWeights]") then
                            Buy("[HeavyWeights] - $250", 1)
                        end
                        if LocalPlayer.Backpack:FindFirstChild("[HeavyWeights]") then
                            LocalPlayer.Character.Humanoid:EquipTool(LocalPlayer.Backpack["[HeavyWeights]"])
                        end
                        LocalPlayer.Character["[HeavyWeights]"]:Activate()
                    end
                end)
            end
            if PuppywareSettings.Blatant.Farming.ShoeFarm then
                pcall(function()
                    for i, v in pairs(Workspace.Ignored.Drop:GetChildren()) do
                        if v.Name == "MeshPart" then
                            LocalPlayer.Character.HumanoidRootPart.CFrame = v.CFrame * CFrame.new(0, 2, 0)
                            local ShoeDistance = (v.Position - LocalPlayer.Character.HumanoidRootPart.Position).Magnitude
                            if ShoeDistance < 25 then
                                fireclickdetector(v.ClickDetector)
                            end
                        else
                            fireclickdetector(Workspace.Ignored["Clean the shoes on the floor and come to me for cash"].ClickDetector)
                        end
                    end
                end)
            end
            if PuppywareSettings.Blatant.Farming.HospitalFarm then
                LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(116, 23, -479)
                for _, v in pairs(Workspace.Ignored.HospitalJob:GetChildren()) do
                    if v.Name == "Can I get the Green bottle" then
                        fireclickdetector(v.Parent.Green.ClickDetector)
                        wait(1)
                        fireclickdetector(v.ClickDetector)
                    end
                    if v.Name == "Can I get the Blue bottle" then
                        fireclickdetector(v.Parent.Blue.ClickDetector)
                        wait(1)
                        fireclickdetector(v.ClickDetector)
                    end
                    if v.Name == "Can I get the Red bottle" then
                        fireclickdetector(v.Parent.Red.ClickDetector)
                        wait(1)
                        fireclickdetector(v.ClickDetector)
                    end
                end
            end
            if PuppywareSettings.Blatant.Farming.BoxFarm then
                pcall(function()
                    LocalPlayer.Character.HumanoidRootPart.CFrame = Workspace.MAP.Map.ArenaBOX.PunchingBagInGame["pretty ransom"].CFrame * CFrame.new(0, -1, 3)
                    if LocalPlayer.Backpack:FindFirstChild("Combat") then
                        LocalPlayer.Backpack.Combat.Parent = LocalPlayer.Character
                    end
                end)
                mouse1click()
            end
        end
    end
end)

spawn(function()
    while wait() do
        if PuppywareSettings.Blatant.Farming.ATMFarm then
            for _, v in pairs(Workspace.Cashiers:GetChildren()) do
                if v:FindFirstChild("Head") and v:FindFirstChild("Humanoid") and v.Humanoid.Health > 0 then
                    repeat
                        PuppywareSettings.Blatant.Farming.ATMPick = false
                        wait()
                        if PuppywareSettings.Blatant.Farming.ATMFarm then
                            if Alive(LocalPlayer) then
                                LocalPlayer.Character.HumanoidRootPart.CFrame = v.Head.CFrame * CFrame.new(0, -1, 2.5)
                                if LocalPlayer.Backpack:FindFirstChild("Combat") then
                                    LocalPlayer.Backpack.Combat.Parent = LocalPlayer.Character
                                end
                                --if LocalPlayer.Character:FindFirstChild("Combat") then
                                    LocalPlayer.Character["Combat"]:Activate()
                                --end
                            end
                        end
                    until v.Humanoid.Health <= 0 or not PuppywareSettings.Blatant.Farming.ATMFarm
                    pcall(function()
                        LocalPlayer.Character:FindFirstChildOfClass("Tool").Parent = LocalPlayer.Backpack
                    end)
                    PuppywareSettings.Blatant.Farming.ATMPick = true
                    wait(5)
                end
            end
        end
    end
end)

RunService.RenderStepped:Connect(function()
    if Alive(LocalPlayer) then
        if PuppywareSettings.Blatant.Cash.AutoDrop then
            ReplicatedStorage.MainEvent:FireServer("DropMoney", tostring(PuppywareSettings.Blatant.Cash.AutoDropAmount))
        end
        if PuppywareSettings.Blatant.Cash.AutoPickCash then
            pcall(function()
                for _, v in pairs(Workspace.Ignored.Drop:GetChildren()) do
                    if v.Name == "MoneyDrop" then
                        local MoneyMagnitude = (v.Position - LocalPlayer.Character.HumanoidRootPart.Position).magnitude
                        if MoneyMagnitude < 25 then
                            fireclickdetector(v.ClickDetector)
                        end 
                    end
                end
            end)
        end
        if PuppywareSettings.Blatant.Farming.ATMPick then
            pcall(function()
                for _, v in pairs(Workspace.Ignored.Drop:GetChildren()) do
                    if v.Name == "MoneyDrop" then
                        local MoneyMagnitude = (v.Position - LocalPlayer.Character.HumanoidRootPart.Position).Magnitude
                        if MoneyMagnitude < 25 then
                            fireclickdetector(v.ClickDetector)
                        end 
                    end
                end
            end)
        end
        if PuppywareSettings.Blatant.Movement.SpeedEnabled and PuppywareSettings.Blatant.Movement.SpeedType == "CFrame" then
            if PuppywareSettings.Blatant.Movement.SpeedRenderType == "Fast" and Alive(LocalPlayer) then
                if LocalPlayer.Character.Humanoid.MoveDirection.Magnitude > 0 then
                    for i = 1, PuppywareSettings.Blatant.Movement.SpeedAmount do
                        LocalPlayer.Character:TranslateBy(LocalPlayer.Character.Humanoid.MoveDirection)
                    end
                end
            end
        end
        if PuppywareSettings.Blatant.Reaching.FistReach and LocalPlayer.Character.LeftHand.Transparency ~= 0.5 then
            LocalPlayer.Character.LeftHand.Size = Vector3.new(45, 45, 45)
            LocalPlayer.Character.RightHand.Size = Vector3.new(45, 45, 45)
            LocalPlayer.Character.RightHand.Massless = true
            LocalPlayer.Character.LeftHand.Massless = true
            LocalPlayer.Character.RightHand.Transparency = 0.5
            LocalPlayer.Character.LeftHand.Transparency = 0.5
        end
        if PuppywareSettings.Blatant.Reaching.MeleeReach then
            local Tool = LocalPlayer.Character:FindFirstChildOfClass("Tool")
            if Tool ~= nil and not Tool:FindFirstChild("Ammo") and TableLowerFind(PuppywareModule.Teleport.Melee, Tool.Name) ~= nil and Tool:FindFirstChild("Handle") then
                if Tool.Handle.Transparency ~= 0.5 then
                    Tool.Handle.Size = Vector3.new(100, 100, 100)
                    Tool.Handle.Transparency = 0.5
                end
            end
        else
            local Tool = LocalPlayer.Character:FindFirstChildOfClass("Tool")
            if Tool ~= nil and not Tool:FindFirstChild("Ammo") and TableLowerFind(PuppywareModule.Teleport.Melee, Tool.Name) ~= nil and Tool:FindFirstChild("Handle") then
                if Tool.Handle.Transparency == 0.5 then
                    if Tool.Name == "knife" then
                        Tool.Handle.Size = Vector3.new(2.19574, 0.449288, 0.102495)
                    end
                    if Tool.Name == "bat" then
                        Tool.Handle.Size = Vector3.new(0.559523, 4.68133, 0.559523)
                    end
                    if Tool.Name == "pencil" then
                        Tool.Handle.Size = Vector3.new(0.375586, 1.9, 0.375587)
                    end
                    if Tool.Name == "pitchfork" then
                        Tool.Handle.Size = Vector3.new(1.0553, 5.86135, 0.316619)
                    end
                    if Tool.Name == "shovel" then
                        Tool.Handle.Size = Vector3.new(1.68383, 5.903, 0.337731)
                    end
                    Tool.Handle.Transparency = 0
                end
            end
        end
        if PuppywareSettings.Blatant.LegitAA.Enabled then
            if PuppywareSettings.Blatant.LegitAA.AntiPointAt then
                for i, v in next, Players:GetPlayers() do
                    if v ~= LocalPlayer and Alive(v) and Alive(LocalPlayer) then
                        local BodyEffects = v.Character:FindFirstChild("BodyEffects")
                        local MousePos = BodyEffects:FindFirstChild("MousePos")
                        if BodyEffects ~= nil and MousePos ~= nil then
                            local EnemyMouseMagnitude = (LocalPlayer.Character.HumanoidRootPart.Position - MousePos.Value).Magnitude
                            if PuppywareSettings.Blatant.LegitAA.AntiAimAtDistance > EnemyMouseMagnitude then
                                Root.CFrame = Root.CFrame * CFrame.new(math.random(1, 2) == 1 and 2 or -2, 0, 0)
                            end
                        end
                    end
                end
            end
        end
        if PuppywareSettings.Blatant.BlatantAA.Enabled then
                if PuppywareSettings.Blatant.BlatantAA.AntiAimType == "Jitter" then
                    Jitter(PuppywareSettings.Blatant.BlatantAA.AntiAimSpeed, PuppywareSettings.Blatant.BlatantAA.JitterAngle)
                else
                    Spin(PuppywareSettings.Blatant.BlatantAA.AntiAimSpeed)
                end
                if PuppywareSettings.Blatant.BlatantAA.NoAutoRotate then
                    LocalPlayer.Character.Humanoid.AutoRotate = false
                else
                    LocalPlayer.Character.Humanoid.AutoRotate = true
                end
        else
            LocalPlayer.Character.Humanoid.AutoRotate = true
        end
    end
    if PuppywareSettings.Aiming.TargetAimSettings.UnlockTargetKnocked then
        if PuppywareSettings.Aiming.TargetAimSettings.Target ~= nil and Players:FindFirstChild(PuppywareSettings.Aiming.TargetAimSettings.Target) then
            if Knocked(Players:FindFirstChild(PuppywareSettings.Aiming.TargetAimSettings.Target)) then
                PuppywareSettings.Aiming.TargetAimSettings.Target = nil
            end
        end
    end
    if PuppywareSettings.Aiming.SilentAim.ShowFOV then
        SilentAimFOV.Visible = true
        SilentAimFOV.Radius = PuppywareSettings.Aiming.FOV.SilentAimSize
        SilentAimFOV.Filled = PuppywareSettings.Aiming.FOV.FOVFilled
        SilentAimFOV.Transparency = PuppywareSettings.Aiming.FOV.Transparency
        SilentAimFOV.NumSides = 100
        SilentAimFOV.Color = PuppywareSettings.Aiming.SilentAim.FOVColor
        SilentAimFOV.Position = Vector2.new(Mouse.X, Mouse.Y + GuiInset.Y)
    else
        SilentAimFOV.Visible = false
    end
    if PuppywareSettings.Aiming.Aimbot.Enabled then
        if PuppywareSettings.Aiming.Aimbot.ShowFOV then
            AimbotFOV.Visible = true
            AimbotFOV.Radius = PuppywareSettings.Aiming.FOV.AimAssistSize
            AimbotFOV.Filled = PuppywareSettings.Aiming.FOV.FOVFilled
            AimbotFOV.Transparency = PuppywareSettings.Aiming.FOV.Transparency
            AimbotFOV.NumSides = 100
            AimbotFOV.Color = PuppywareSettings.Aiming.Aimbot.FOVColor
            AimbotFOV.Position = Vector2.new(Mouse.X, Mouse.Y + GuiInset.Y)
        else
            AimbotFOV.Visible = false
        end
        if PuppywareSettings.Aiming.Aimbot.AimAssist and PuppywareSettings.Aiming.Aimbot.IsAiming then
            local NearestTarget, NearestDistance = NearestType(Unpack({PuppywareSettings.Aiming.Aimbot.UseNearestDistance and "Distance" or "Mouse"}))

            if NearestTarget and (not PuppywareSettings.Aiming.Aimbot.GrabbedCheck or not Grabbing(NearestTarget)) and (not PuppywareSettings.Aiming.Aimbot.KnockedOutCheck or not Knocked(NearestTarget)) and (not PuppywareSettings.Aiming.Aimbot.ShowFOV or PuppywareSettings.Aiming.FOV.AimAssistSize > NearestDistance) and (not PuppywareSettings.Aiming.Aimbot.WallCheck or Visible(NearestTarget.Character.HumanoidRootPart, LocalPlayer.Character.HumanoidRootPart)) then
                local TargetPart = Unpack({NearestTarget.Character.Humanoid:GetState() == Enum.HumanoidStateType.Freefall and NearestTarget.Character.LeftFoot or NearestTarget.Character[RandomTable(PuppywareSettings.Aiming.Aimbot.Hitboxes)]})
                local Prediction = Unpack({PuppywareSettings.Aiming.AimbotSettings.MovementPrediction and TargetPart.CFrame + (TargetPart.Velocity * PuppywareSettings.Aiming.AimbotSettings.MovementPredictionAmount) or TargetPart.CFrame})
                
                if PuppywareSettings.Aiming.AimbotSettings.AimAssistType == "Mouse" then
                    local NearestPosition, NearestVisible = CurrentCamera:WorldToScreenPoint(Prediction.Position)
                    local MouseLocation = CurrentCamera:WorldToScreenPoint(Mouse.Hit.Position)
                    local EndPosition = Unpack({PuppywareSettings.Aiming.AimbotSettings.SmoothingTracing and Vector2.new((NearestPosition.X - MouseLocation.X) / PuppywareSettings.Aiming.AimbotSettings.SmoothingTracingAmount, (NearestPosition.Y - MouseLocation.Y) / PuppywareSettings.Aiming.AimbotSettings.SmoothingTracingAmount) or Vector2.new((NearestPosition.X - MouseLocation.X) / 1.4, (NearestPosition.Y - MouseLocation.Y) / 1.4)})

                    if NearestVisible then
                        mousemoverel(EndPosition.X, EndPosition.Y)
                    end
                elseif PuppywareSettings.Aiming.AimbotSettings.AimAssistType == "Camera" then
                    CurrentCamera.CFrame = CFrame.lookAt(CurrentCamera.CFrame.Position, Prediction.Position)
                end
            end
        end
    else
        AimbotFOV.Visible = false
    end
end)

spawn(function()
    while wait(1 / 16) do
        LagTick = math.clamp(PuppywareModule.LagTick + 1, 0, PuppywareSettings.Blatant.FakeLag.TriggerAmount)
        if Alive(Player) and PuppywareSettings.Blatant.FakeLag.Enabled then
            if LagTick == math.random(1, PuppywareSettings.Blatant.FakeLag.TriggerAmount) then
                Network:SetOutgoingKBPSLimit(9e9)
                PuppywareFolder:ClearAllChildren()
                LagTick = 0
                
                    if Settings.Visuals.PlayerESP.FakeLag.Cham then
                        for i, v in pairs(Player.Character:GetChildren()) do
                            if v:IsA("BasePart") and v.Name ~= "HumanoidRootPart" then
                                local ShadowPart = Instance.new("Part")
                                ShadowPart.CFrame = v.CFrame
                                ShadowPart.Anchored = true
                                ShadowPart.CanCollide = false
                                ShadowPart.Material = Enum.Material.ForceField
                                ShadowPart.Color = Settings.Visuals.PlayerESP.FakeLag.Color
                                ShadowPart.Name = v.Name
                                ShadowPart.Transparency = 0
                                ShadowPart.Size = v.Size
                                ShadowPart.Parent = FakeLagFolder
                            end
                        end
                    end
                
            else
                if PuppywareSettings.Blatant.FakeLag.Enabled then
                    Network:SetOutgoingKBPSLimit(1)
                end
            end
        else
            PuppywareFolder:ClearAllChildren()
            Network:SetOutgoingKBPSLimit(9e9)
        end
    end
end)

local __namecall -- cock ;)
__namecall = hookmetamethod(game, "__namecall", function(self, ...)
    local Args = {...}
    local Method = getnamecallmethod()

    if tostring(self.Name) == "MainEvent" and tostring(Method) == "FireServer" then
        if Args[1] == "TeleportDetect" or Args[1] == "CHECKER_1" or Args[1] == "OneMoreTime" then
            return
        end
    end

    return __namecall(self, ...)
end)

local __index -- <3
__index = hookmetamethod(game, "__index", function(self, key)
    if self == Mouse and (tostring(key) == "Hit" or tostring(key) == "Target") then
        if PuppywareSettings.Aiming.TargetAim.Enabled then
            if PuppywareSettings.Aiming.TargetAim.Target ~= nil and ChanceTable(PuppywareSettings.Aiming.TargetAimSettings.HitChanceAmount) == "HitPercent" then
                if Players:FindFirstChild(PuppywareSettings.Aiming.TargetAim.Target) ~= nil and (not PuppywareSettings.Aiming.TargetAim.GrabbedCheck or not Grabbing(Players[PuppywareSettings.Aiming.TargetAim.Target])) and (not PuppywareSettings.Aiming.TargetAim.KnockedOutCheck or not Knocked(Players[PuppywareSettings.Aiming.TargetAim.Target])) and (not PuppywareSettings.Aiming.TargetAim.ShowFOV or PuppywareSettings.Aiming.FOV.TargetAimSize > (LocalPlayer.Character.Head.Position - Players[PuppywareSettings.Aiming.TargetAim.Target].Character.Head.Position).Magnitude) and (not PuppywareSettings.Aiming.TargetAim.WallCheck or Visible(Players[PuppywareSettings.Aiming.TargetAim.Target].Character.HumanoidRootPart, LocalPlayer.Character.HumanoidRootPart)) then
                    local TargetPart = Unpack({Players[PuppywareSettings.Aiming.TargetAim.Target].Character.Humanoid:GetState() == Enum.HumanoidStateType.Freefall and Players[PuppywareSettings.Aiming.TargetAim.Target].Character.LeftFoot or Players[PuppywareSettings.Aiming.TargetAim.Target].Character[RandomTable(PuppywareSettings.Aiming.TargetAim.Hitboxes)]})
                    local Prediction = Unpack({PuppywareSettings.Aiming.TargetAimSettings.MovementPrediction and TargetPart.CFrame + (TargetPart.Velocity * PuppywareSettings.Aiming.TargetAimSettings.MovementPredictionAmount) or TargetPart.CFrame})

                    return (tostring(key) == "Hit" and Prediction or tostring(key) == "Target" and TargetPart)
                end
            end
        else    
            if PuppywareSettings.Aiming.SilentAim.Enabled and ChanceTable(PuppywareSettings.Aiming.SilentAimSettings.HitChanceAmount) == "HitPercent" then
                local NearestTarget, NearestDistance = NearestType(Unpack({PuppywareSettings.Aiming.SilentAim.UseNearestDistance and "Distance" or "Mouse"}))
    
                if NearestTarget and (not PuppywareSettings.Aiming.SilentAim.GrabbedCheck or not Grabbing(NearestTarget)) and (not PuppywareSettings.Aiming.SilentAim.KnockedOutCheck or not Knocked(NearestTarget)) and (not PuppywareSettings.Aiming.SilentAim.ShowFOV or PuppywareSettings.Aiming.FOV.SilentAimSize > NearestDistance) and (not PuppywareSettings.Aiming.SilentAim.WallCheck or Visible(NearestTarget.Character.HumanoidRootPart, LocalPlayer.Character.HumanoidRootPart)) then
                    local TargetPart = Unpack({NearestTarget.Character.Humanoid:GetState() == Enum.HumanoidStateType.Freefall and NearestTarget.Character.LeftFoot or NearestTarget.Character[RandomTable(PuppywareSettings.Aiming.SilentAim.Hitboxes)]})
                    local Prediction = Unpack({PuppywareSettings.Aiming.SilentAimSettings.MovementPrediction and TargetPart.CFrame + (TargetPart.Velocity * PuppywareSettings.Aiming.SilentAimSettings.MovementPredictionAmount) or TargetPart.CFrame})
    
                    return (tostring(key) == "Hit" and Prediction or tostring(key) == "Target" and TargetPart)
                end
            end
        end
        
    end

    return __index(self, key)
end)

while wait() do
    if PuppywareSettings.Aiming.TriggerBot.Enabled then
        for i, v in next, Players:GetPlayers() do 
            if Alive(v) then 
                if Mouse.Target:IsDescendantOf(v.Character) then 
                    mouse1press()
                    wait()
                    mouse1release()
                    if PuppywareSettings.Aiming.TriggerBot.Delay then
                        wait(PuppywareSettings.Aiming.TriggerBot.DelayAmount)
                    end
                end 
            end
        end
    end
end





local Settings = {
    rewrittenmain = {
        Enabled = true,
        Key = "q",
        DOT = true,
        AIRSHOT = true,
        NOTIF = true,
        AUTOPRED = false,
        FOV = math.huge,
        RESOVLER = false
    }
}
 
local SelectedPart = "LowerTorso"
local Prediction = true
local PredictionValue = .1208726
 
 
    local AnchorCount = 0
    local MaxAnchor = 6
 
    local CC = game:GetService"Workspace".CurrentCamera
    local Plr;
    local enabled = false
    local accomidationfactor = .1208726
    local mouse = game.Players.LocalPlayer:GetMouse()
    local placemarker = Instance.new("Part", game.Workspace)
 
    function makemarker(Parent, Adornee, Color, Size, Size2)
        local e = Instance.new("BillboardGui", Parent)
        e.Name = "PP"
        e.Adornee = Adornee
        e.Size = UDim2.new(Size, Size2, Size, Size2)
        e.AlwaysOnTop = Settings.rewrittenmain.DOT
        local a = Instance.new("Frame", e)
        if Settings.rewrittenmain.DOT == true then
        a.Size = UDim2.new(1, 0, 1, 0)
        else
        a.Size = UDim2.new(0, 0, 0, 0)
        end
        if Settings.rewrittenmain.DOT == true then
        a.Transparency = 0
        a.BackgroundTransparency = 0
        else
        a.Transparency = 1
        a.BackgroundTransparency = 1
        end
        a.BackgroundColor3 = Color
        local g = Instance.new("UICorner", a)
        if Settings.rewrittenmain.DOT == false then
        g.CornerRadius = UDim.new(0, 0)
        else
        g.CornerRadius = UDim.new(1, 1) 
        end
        return(e)
    end
 
 
    local data = game.Players:GetPlayers()
    function noob(player)
        local character
        repeat wait() until player.Character
        local handler = makemarker(guimain, player.Character:WaitForChild(SelectedPart), Color3.fromRGB(180, 125, 180), 0.3, 3)
        handler.Name = player.Name
        player.CharacterAdded:connect(function(Char) handler.Adornee = Char:WaitForChild(SelectedPart) end)
 
 
        spawn(function()
            while wait() do
                if player.Character then
                end
            end
        end)
    end
 
    for i = 1, #data do
        if data[i] ~= game.Players.LocalPlayer then
            noob(data[i])
        end
    end
 
    game.Players.PlayerAdded:connect(function(Player)
        noob(Player)
    end)
 
    spawn(function()
        placemarker.Anchored = true
        placemarker.CanCollide = false
        if Settings.rewrittenmain.DOT == true then
        placemarker.Size = Vector3.new(7, 7, 7)
        else
        placemarker.Size = Vector3.new(0, 0, 0)
        end
        placemarker.Transparency = 0.60
        if Settings.rewrittenmain.DOT then
        makemarker(placemarker, placemarker, Color3.fromRGB(180, 125, 180), 0.40, 0)
        end
    end)
 
    game.Players.LocalPlayer:GetMouse().KeyDown:Connect(function(k)
        if k == Settings.rewrittenmain.Key and Settings.rewrittenmain.Enabled then
            if enabled == true then
                enabled = false
                if Settings.rewrittenmain.NOTIF == true then
                    Plr = getClosestPlayerToCursor()
                game.StarterGui:SetCore("SendNotification", {
                    Title = "THANKS FOR USING NASA.EXE";
                    Text = "UNLOCKED",
                    Duration = 3
                })
            end
            else
                Plr = getClosestPlayerToCursor()
                enabled = true
                if Settings.rewrittenmain.NOTIF == true then
 
                    game.StarterGui:SetCore("SendNotification", {
                        Title = "THANKS FOR USING NASA.EXE";
                        Text = "Target: "..tostring(Plr.Character.Humanoid.DisplayName),
                        Duration = 3
                    })
 
                end
            end
        end
    end)
 
 
 
    function getClosestPlayerToCursor()
        local closestPlayer
        local shortestDistance = Settings.rewrittenmain.FOV
 
        for i, v in pairs(game.Players:GetPlayers()) do
            if v ~= game.Players.LocalPlayer and v.Character and v.Character:FindFirstChild("Humanoid") and v.Character.Humanoid.Health ~= 0 and v.Character:FindFirstChild("HumanoidRootPart") then
                local pos = CC:WorldToViewportPoint(v.Character.PrimaryPart.Position)
                local magnitude = (Vector2.new(pos.X, pos.Y) - Vector2.new(mouse.X, mouse.Y)).magnitude
                if magnitude < shortestDistance then
                    closestPlayer = v
                    shortestDistance = magnitude
                end
            end
        end
        return closestPlayer
    end
 
    local pingvalue = nil;
    local split = nil;
    local ping = nil;
 
    game:GetService"RunService".Stepped:connect(function()
        if enabled and Plr.Character ~= nil and Plr.Character:FindFirstChild("HumanoidRootPart") then
            placemarker.CFrame = CFrame.new(Plr.Character.HumanoidRootPart.Position+(Plr.Character.HumanoidRootPart.Velocity*accomidationfactor))
        else
            placemarker.CFrame = CFrame.new(0, 9999, 0)
        end
        if Settings.rewrittenmain.AUTOPRED == true then
             pingvalue = game:GetService("Stats").Network.ServerStatsItem["Data Ping"]:GetValueString()
             split = string.split(pingvalue,'(')
             ping = tonumber(split[1])
            if ping < 130 then
                PredictionValue = .1208726
            elseif ping < 125 then
                PredictionValue = .1208726
            elseif ping < 110 then
                PredictionValue = .1208726
            elseif ping < 105 then
                PredictionValue = .1208726
            elseif ping < 90 then
                PredictionValue = .1208726
            elseif ping < 80 then
                PredictionValue = .1208726
            elseif ping < 70 then
                PredictionValue = .1208726
            elseif ping < 60 then
                PredictionValue = .1208726
            elseif ping < 50 then
                PredictionValue = .1208726
            elseif ping < 40 then
                PredictionValue = .1208726
            end
        end
    end)
 
    local mt = getrawmetatable(game)
    local old = mt.__namecall
    setreadonly(mt, false)
    mt.__namecall = newcclosure(function(...)
        local args = {...}
        if enabled and getnamecallmethod() == "FireServer" and args[2] == "UpdateMousePos" and Settings.rewrittenmain.Enabled and Plr.Character ~= nil then
 
            -- args[3] = Plr.Character.HumanoidRootPart.Position+(Plr.Character.HumanoidRootPart.Velocity*accomidationfactor)
            --[[
            if Settings.rewrittenmain.AIRSHOT == true then
                if game.Workspace.Players[Plr.Name].Humanoid:GetState() == Enum.HumanoidStateType.Freefall then -- Plr.Character:WaitForChild("Humanoid"):GetState() == Enum.HumanoidStateType.Freefall
 
                    --// Airshot
                    args[3] = Plr.Character.LeftFoot.Position+(Plr.Character.LeftFoot.Velocity*PredictionValue)
 
                else
                    args[3] = Plr.Character.HumanoidRootPart.Position+(Plr.Character.HumanoidRootPart.Velocity*PredictionValue)
 
                end
            else
                    args[3] = Plr.Character.HumanoidRootPart.Position+(Plr.Character.HumanoidRootPart.Velocity*PredictionValue)
            end
            ]]
            if Prediction == true then
 
            args[3] = Plr.Character[SelectedPart].Position+(Plr.Character[SelectedPart].Velocity*PredictionValue)
 
            else
 
            args[3] = Plr.Character[SelectedPart].Position
 
            end
 
            return old(unpack(args))
        end
        return old(...)
    end)
 
    game:GetService("RunService").RenderStepped:Connect(function()
        if Settings.rewrittenmain.RESOVLER == true and Plr.Character ~= nil and enabled and Settings.rewrittenmain.Enabled then
        if Settings.rewrittenmain.AIRSHOT == true and enabled and Plr.Character ~= nil then
 
            if game.Workspace.Players[Plr.Name].Humanoid:GetState() == Enum.HumanoidStateType.Freefall then -- Plr.Character:WaitForChild("Humanoid"):GetState() == Enum.HumanoidStateType.Freefall
 
                --// Airshot
 
                --// Anchor Check
 
                if Plr.Character ~= nil and Plr.Character.HumanoidRootPart.Anchored == true then
                    AnchorCount = AnchorCount + 1
                    if AnchorCount >= MaxAnchor then
                        Prediction = false
                        wait(2)
                        AnchorCount = 0;
                    end
                else
                    Prediction = true
                    AnchorCount = 0;
                end
 
                SelectedPart = "LeftFoot"
 
            else
                --// Anchor Check
 
                if Plr.Character ~= nil and Plr.Character.HumanoidRootPart.Anchored == true then
                    AnchorCount = AnchorCount + 1
                    if AnchorCount >= MaxAnchor then
                        Prediction = false
                        wait(2)
                        AnchorCount = 0;
                    end
                else
                    Prediction = true
                    AnchorCount = 0;
                end
 
                SelectedPart = "HumanoidRootPart"
 
            end
            else
 
                --// Anchor Check
 
                if Plr.Character ~= nil and Plr.Character.HumanoidRootPart.Anchored == true then
                    AnchorCount = AnchorCount + 1
                    if AnchorCount >= MaxAnchor then
                        Prediction = false
                        wait(2)
                        AnchorCount = 0;
                    end
                else
                    Prediction = true
                    AnchorCount = 0;
                end
 
                SelectedPart = "HumanoidRootPart"
            end
 
        else
                SelectedPart = "HumanoidRootPart"
        end
    end)
