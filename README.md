local Library = loadstring(game:HttpGet("https://raw.githubusercontent.com/bloodball/-back-ups-for-libs/main/cat"))() --you can go into the github link and copy all of it and modify it for yourself.
local Window = Library:CreateWindow("SloxicWare.cc | dont skid bitch .gg/6YePnPSb", Vector2.new(492, 598), Enum.KeyCode.RightControl) --you can change your UI keybind
local AIMLOCK = Window:CreateTab("Main") --you can rename this tab to whatever you want --you can also change the tabs code, for example "AimingTab" can be changed to "FunnyCoolTab" etc.






local aimlock = AIMLOCK:CreateSector("Main", "left")  --you can  change the section code, for example "testsection" can be changed to "FunnyCoolSection" etc.



local cool = AIMLOCK:CreateSector("Others", "Right")

local Player = AIMLOCK:CreateSector("Player", "Left")

aimlock:AddButton("Hood Modded Aimlock/key {Q}", function(IhateGayPeople)
 local Settings = { AimLock = { Enabled = true, Aimlockkey = "q", Prediction = 0.120, Aimpart = 'LowerTorso', Notifications = true }, Settings = { Thickness = 2.5, Transparency = 1, Color = Color3.fromRGB(190, 20, 190), FOV = false } } local CurrentCamera = game:GetService("Workspace").CurrentCamera local Inset = game:GetService("GuiService"):GetGuiInset().Y local RunService = game:GetService("RunService") local Mouse = game.Players.LocalPlayer:GetMouse() local LocalPlayer = game.Players.LocalPlayer local Line = Drawing.new("Line") local Circle = Drawing.new("Circle") local Plr = game.Players.LocalPlayer Mouse.KeyDown:Connect(function(KeyPressed) if KeyPressed == (Settings.AimLock.Aimlockkey) then if Settings.AimLock.Enabled == true then Settings.AimLock.Enabled = false if Settings.AimLock.Notifications == true then Plr = FindClosestPlayer() game.StarterGui:SetCore("SendNotification", { Title = "use sloxic skids | dont run dont trip", Text = "UNLOCKED" }) end else Plr = FindClosestPlayer() Settings.AimLock.Enabled = true if Settings.AimLock.Notifications == true then game.StarterGui:SetCore("SendNotification", { Title = "use sloxic skids | dont run dont trip", Text = "Locked On : " .. tostring(Plr.Character.Humanoid.DisplayName) }) end end end end) function FindClosestPlayer() local ClosestDistance, ClosestPlayer = math.huge, nil; for _, Player in next, game:GetService("Players"):GetPlayers() do if Player ~= LocalPlayer then local Character = Player.Character if Character and Character.Humanoid.Health > 1 then local Position, IsVisibleOnViewPort = CurrentCamera:WorldToViewportPoint(Character.HumanoidRootPart .Position) if IsVisibleOnViewPort then local Distance = (Vector2.new(Mouse.X, Mouse.Y) - Vector2.new(Position.X, Position.Y)).Magnitude if Distance < ClosestDistance then ClosestPlayer = Player ClosestDistance = Distance end end end end end return ClosestPlayer, ClosestDistance end RunService.Heartbeat:connect(function() if Settings.AimLock.Enabled == true then local Vector = CurrentCamera:WorldToViewportPoint(Plr.Character[Settings.AimLock.Aimpart].Position + (Plr.Character[Settings.AimLock.Aimpart].Velocity * Settings.AimLock.Prediction)) Line.Color = Settings.Settings.Color Line.Transparency = Settings.Settings .Transparency Line.Thickness = Settings.Settings .Thickness Line.From = Vector2.new(Mouse.X, Mouse.Y + Inset) Line.To = Vector2.new(Vector.X, Vector.Y) Line.Visible = true Circle.Position = Vector2.new(Mouse.X, Mouse.Y + Inset) Circle.Visible = Settings.Settings.FOV Circle.Thickness = 15.5 Circle.Thickness = 15 Circle.Radius = 450 Circle.Color = Settings.Settings.Color elseif Settings.AimLock.FOV == true then Circle.Visible = true else Circle.Visible = false Line.Visible = false end end) local mt = getrawmetatable(game) local old = mt.__namecall setreadonly(mt, false) mt.__namecall = newcclosure(function(...) local args = {...} if Settings.AimLock.Enabled and getnamecallmethod() == "FireServer" and args[2] == "MousePos" then args[3] = Plr.Character[Settings.AimLock.Aimpart].Position + (Plr.Character[Settings.AimLock.Aimpart].Velocity * Settings.AimLock.Prediction) return old(unpack(args)) end return old(...) end)
end)

aimlock:AddButton("aimolck | key {E}", function(IhateGayPeople)
--this is from sloxic dont skid fat bitch
local CC = game:GetService"Workspace".CurrentCamera
    local Plr
    local enabled = falseWD
    local accomidationfactor = .12027 --you can change this to wtv
    local mouse = game.Players.LocalPlayer:GetMouse()
    local placemarker = Instance.new("Part", game.Workspace)
 
    function makemarker(Parent, Adornee, Color, Size, Size2)
        local e = Instance.new("BillboardGui", Parent)
        e.Name = "sh!"
        e.Adornee = Adornee
        e.Size = UDim2.new(Size, Size2, Size, Size2)
        e.AlwaysOnTop = true
        local a = Instance.new("Frame", e)
        a.Size = UDim2.new(1, 0, 1, 0)
        a.BackgroundTransparency = 0
        a.BackgroundColor3 = Color
        local g = Instance.new("UICorner", a)
        g.CornerRadius = UDim.new(50, 50)
        return(e)
    end
 
 
 
 
 
 
         _G.Types = {
        Ball = Enum.PartType.Ball,
        Block = Enum.PartType.Block, 
        Cylinder = Enum.PartType.Cylinder
    }
    
    
    
    _G.Types = {
                Ball = Enum.PartType.Ball,
                Block = Enum.PartType.Block, 
                Cylinder = Enum.PartType.Cylinder
            }
                              
                           
                              
 
    --variables
    Tracer = Drawing.new("Tracer")                 
        local Tracer = Instance.new("Part", game.Workspace)
    Tracer.Name = "gay" 
    Tracer.Anchored = false      
    Tracer.CanCollide = false
    Tracer.Transparency = 0.8
    Tracer.Parent = game.Workspace  
    Tracer.Shape = _G.Types.Block
    Tracer.Size = Vector3.new(14,14,14)
    Tracer.Color = Color3.fromRGB(255,7,255)
    

 
    --
    local plr = game.Players.LocalPlayer
local mouse = plr:GetMouse()
local Runserv = game:GetService("RunService")
 
circle = Drawing.new("Circle")
circle.Color = Color3.fromRGB(190,20,190)
circle.Thickness = 0
circle.NumSides = 732
circle.Radius = 120
circle.Thickness = 0
circle.Transparency = 0.7 
circle.Visible = false
circle.Filled = false
 
Runserv.RenderStepped:Connect(function()
    circle.Position = Vector2.new(mouse.X,mouse.Y+35)
end)
 
 
 
      local Inset = game:GetService("GuiService"):GetGuiInset().Y
                local Line = Drawing.new("Line")
                    local Text = Drawing.new("Text")
        local guimain = Instance.new("Folder", game.CoreGui)
        local CC = game:GetService"Workspace".CurrentCamera
    local LocalMouse = game.Players.LocalPlayer:GetMouse()
        local Locking = false
 
 
    --
    if getgenv().valiansh == true then
                        game.StarterGui:SetCore("SendNotification", {
                   Title = "priv",
                   Text = "Already Loaded!",
                   Duration = 5
 
                   })
        return
    end
 
    getgenv().valiansh = true
 
        local UserInputService = game:GetService("UserInputService")
 
    UserInputService.InputBegan:Connect(function(keygo,ok)
           if (not ok) then
           if (keygo.KeyCode == getgenv().Key) then
               if getgenv().Target == true then
               Locking = not Locking
 
               if Locking then
               Plr =  getClosestPlayerToCursor()
                if getgenv().ChatMode then
        local A_1 = "Target: "..tostring(Plr.Character.Humanoid.DisplayName) local A_2 = "All" local Event = game:GetService("ReplicatedStorage").DefaultChatSystemChatEvents.SayMessageRequest Event:FireServer(A_1, A_2) 
            end 
               if getgenv().NotifMode then
                game.StarterGui:SetCore("SendNotification", {
        Title = "sh!";
        Text = "Target: "..tostring(Plr.Character.Humanoid.DisplayName);
 
    })
    end
    elseif not Locking then
         if getgenv().ChatMode then
        local A_1 = "Unlocked!" local A_2 = "All" local Event = game:GetService("ReplicatedStorage").DefaultChatSystemChatEvents.SayMessageRequest Event:FireServer(A_1, A_2) 
            end 
        if getgenv().NotifMode then
                        game.StarterGui:SetCore("SendNotification", {
                   Title = "sh!",
                   Text = "Unlocked",
                   Duration = 5
               })
           elseif getgenv().Target == false then
                        game.StarterGui:SetCore("SendNotification", {
                   Title = "sh!",
                   Text = "Target isn't enabled",
                   Duration = 5
 
                   })
 
               end
 
 
 end     end   
end
end
end)
 
    function getClosestPlayerToCursor()
        local closestPlayer
        local shortestDistance = circle.Radius
 
        for i, v in pairs(game.Players:GetPlayers()) do
            if v ~= game.Players.LocalPlayer and v.Character and v.Character:FindFirstChild("Humanoid") and v.Character.Humanoid.Health ~= 0 and v.Character:FindFirstChild("LowerTorso") then
                local pos = CC:WorldToViewportPoint(v.Character.PrimaryPart.Position)
                local magnitude = (Vector2.new(pos.X, pos.Y) - Vector2.new(LocalMouse.X, LocalMouse.Y)).magnitude
                if magnitude < shortestDistance then
                    closestPlayer = v
                    shortestDistance = magnitude
                end
            end
        end
        return closestPlayer
    end
--
if getgenv().PartMode then
    game:GetService"RunService".Stepped:connect(function()
        if Locking and Plr.Character and Plr.Character:FindFirstChild("LowerTorso") then
            Tracer.CFrame = CFrame.new(Plr.Character.LowerTorso.Position+(Plr.Character.LowerTorso.Velocity*Prediction))
        else
            Tracer.CFrame = CFrame.new(0, 9999, 0)
 
        end
    end)
end
 

 
 
 
       placemarker.Anchored = true
                   local placemarker = Instance.new("Part", game.Workspace)
                              placemarker.Shape = _G.Types.Block
                              placemarker.Material = "ForceField"
                              placemarker.Color = Color3.new(20, 190, 20)
                              placemarkertransparency = 50 
 
    local data = game.Players:GetPlayers()
    function noob(player)
        local character
        repeat wait() until player.Character
        local handler = makemarker(guimain, player.Character:WaitForChild("HumanoidRootPart"), Color3.fromRGB(190, 20, 190), 0.3, 3)
        handler.Name = player.Name
        player.CharacterAdded:connect(function(Char) handler.Adornee = Char:WaitForChild("HumanoidRootPart") end)
 
 
        spawn(function()
            while wait() do
                if player.Character then
                    TextLabel.Text = player.Name..tostring(player:WaitForChild("leaderstats").Wanted.Value).." | "..tostring(math.floor(player.Character:WaitForChild("Humanoid").Health))
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
        placemarker.Size = Vector3.new(7, 11, 7)
        placemarker.Transparency = 0.50
        makemarker(placemarker, placemarker, Color3.fromRGB(190, 20, 190), 0.40, 0)
    end)
    
        
 
mouse.KeyDown:Connect(function(k)
    if k ~= "e" then return end
    if enabled then
        enabled = false
        guimain[Plr.Name].Frame.BackgroundColor3 = Color3.fromRGB(190, 20, 190)
    else
        enabled = true 
        Plr = getClosestPlayerToCursor()
        guimain[Plr.Name].Frame.BackgroundColor3 = Color3.fromRGB(190, 20, 190)
    end    
end)
 
    function getClosestPlayerToCursor()
        local closestPlayer
        local shortestDistance = math.huge
 
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
 
    game:GetService"RunService".Stepped:connect(function()
        if enabled and Plr.Character and Plr.Character:FindFirstChild("HumanoidRootPart") then
            placemarker.CFrame = CFrame.new(Plr.Character.HumanoidRootPart.Position+(Plr.Character.HumanoidRootPart.Velocity*accomidationfactor))
        else
            placemarker.CFrame = CFrame.new(0, 9999, 0)
        end
    end)
 
    local mt = getrawmetatable(game)
    local old = mt.__namecall
    setreadonly(mt, false)
    mt.__namecall = newcclosure(function(...)
        local args = {...}
        if enabled and getnamecallmethod() == "FireServer" and args[2] == "UpdateMousePos" then
            args[3] = Plr.Character.HumanoidRootPart.Position+(Plr.Character.HumanoidRootPart.Velocity*accomidationfactor)
            return old(unpack(args))
        end
        return old(...)
    end)
end)

aimlock:AddButton("Cframe | key {C}", function(IhateGayPeople)
--cframe made from sloxic
 local Player = game:GetService'Players'.LocalPlayer;
 local UIS = game:GetService'UserInputService';
 UIS.InputBegan:connect(function(UserInput)
         if UserInput.UserInputType == Enum.UserInputType.Keyboard and UserInput.KeyCode == Enum.KeyCode.C then
             _G.Running = true
                 while wait(0.005) and _G.Running == true do
 game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame + game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame.lookVector * 1
 game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame + game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame.lookVector * 1
 game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame + game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame.lookVector * 1
 end
         end
 end)
 UIS.InputEnded:connect(function(UserInput)
         if UserInput.UserInputType == Enum.UserInputType.Keyboard and UserInput.KeyCode == Enum.KeyCode.C then
                 _G.Running = false
         end
 end)
end)


aimlock:AddButton("Fly | key {X}", function(IhateGayPeople)
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

cool:AddButton("Cframe fly | key {T}", function(IhateGayPeople)
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

Player:AddButton("FreeFist | Key {B}", function(IhateGayPeople)
local localPlayer       = game:GetService("Players").LocalPlayer
local localCharacter    = localPlayer.Character
local Mouse             = localPlayer:GetMouse()
local FistControl       = false
local LeftFist          = localCharacter.LeftHand
local RightFist         = localCharacter.RightHand

-- // Services
local uis = game:GetService("UserInputService")

-- // Coroutine Loop + Functions
local loopFunction = function()
    LeftFist.CFrame  = CFrame.new(Mouse.Hit.p)
    RightFist.CFrame = CFrame.new(Mouse.Hit.p)
end

local Loop

local Start = function()
    Loop = game:GetService("RunService").Heartbeat:Connect(loopFunction)
end

local Pause = function()
    Loop:Disconnect()
end

-- // Hotkeys
uis.InputBegan:connect(function(Key)
    if (Key.KeyCode == Enum.KeyCode.B) then
        if (FistControl == false) then
            FistControl = true
            Start()
            pcall(function()
                localCharacter.RightHand.RightWrist:Remove()
                localCharacter.LeftHand.LeftWrist:Remove()
            end)
        elseif (FistControl == true) then
            FistControl = false
            Pause()
            local rightwrist  = Instance.new("Motor6D")
            rightwrist.Name   = "RightWrist"
            rightwrist.Parent = localCharacter.RightHand
            rightwrist.C0     = CFrame.new(1.18422506e-07, -0.5009287, -6.81715525e-18, 1, 0, 0, 0, 1, 0, 0, 0, 1)
            rightwrist.C1     = CFrame.new(3.55267503e-07, 0.125045404, 5.92112528e-08, 1, 0, 0, 0, 1, 0, 0, 0, 1)
            rightwrist.Part0  = localCharacter.RightLowerArm
            rightwrist.Part1  = localCharacter.RightHand

            local leftwrist   = Instance.new("Motor6D")
            leftwrist.Name    = "LeftWrist"
            leftwrist.Parent  = localCharacter.LeftHand
            leftwrist.C0      = CFrame.new(0.000475466368, -0.5009287, 7.59417072e-20, 1, 0, 0, 0, 1, 0, 0, 0, 1)
            leftwrist.C1      = CFrame.new(0.000475821638, 0.125045404, 5.92112528e-08, 1, 0, 0, 0, 1, 0, 0, 0, 1)
            leftwrist.Part0   = localCharacter.LeftLowerArm
            leftwrist.Part1   = localCharacter.LeftHand
        end
    end
end)
end)









cool:AddButton("Headless & Korblox | Non Fe", function(IhateGayPeople)
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





cool:AddButton("no Jump CoolDown", function(IhateGayPeople)
 if not game.IsLoaded(game) then 
            game.Loaded.Wait(game.Loaded);
        end
    
        local IsA = game.IsA;
        local newindex = nil 
    
        newindex = hookmetamethod(game, "__newindex", function(self, Index, Value)
            if not checkcaller() and IsA(self, "Humanoid") and Index == "JumpPower" then 
                return
            end
    
            return newindex(self, Index, Value);
        end)
end)









Player:AddButton("TryHard Animations", function(IhateGayPeople)
while true do
            local Animate = game.Players.LocalPlayer.Character.Animate
            Animate.idle.Animation1.AnimationId = "http://www.roblox.com/asset/?id=782841498"
            Animate.idle.Animation2.AnimationId = "http://www.roblox.com/asset/?id=782841498"
            Animate.walk.WalkAnim.AnimationId = "http://www.roblox.com/asset/?id=616168032"
            Animate.run.RunAnim.AnimationId = "http://www.roblox.com/asset/?id=616163682"
            Animate.jump.JumpAnim.AnimationId = "http://www.roblox.com/asset/?id=1083218792"
            Animate.climb.ClimbAnim.AnimationId = "http://www.roblox.com/asset/?id=1083439238"
            Animate.fall.FallAnim.AnimationId = "http://www.roblox.com/asset/?id=707829716"
            game.Players.LocalPlayer.Character.Humanoid.Jump = false
            wait(1)
            end
end)



cool:AddButton("RGB | higher FPS", function(IhateGayPeople)
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
 sbox.SkyboxBk = "https://cdn.nekos.life/lewd/lewd_neko_195.jpeg"
 sbox.SkyboxDn = "https://cdn.nekos.life/lewd/lewd_neko_195.jpeg"
 sbox.SkyboxFt = "https://cdn.nekos.life/lewd/lewd_neko_195.jpeg"
 sbox.SkyboxLf = "https://cdn.nekos.life/lewd/lewd_neko_195.jpeg"
 sbox.SkyboxRt = "https://cdn.nekos.life/lewd/lewd_neko_195.jpeg"
 sbox.SkyboxUp = "https://cdn.nekos.life/lewd/lewd_neko_195.jpeg"
 lighting.Ambient = Color3.fromRGB(185, 0, 185)
 lighting.FogColor = Color3.fromRGB(185, 0, 185)
 lighting.ClockTime = 3
 lighting.FogEnd = 2000
 for i, v in pairs(game:GetService("Workspace"):GetChildren()) do
     if v:IsA("BasePart") and v.Material == Enum.Material.Grass then
         v.Transparency = 0.60
         v.Color = Color3.fromRGB(185, 0, 185)
     end
 end
end)



Player:AddButton("AntiLock | Key {V}", function(IhateGayPeople)
getgenv().Underground = true
  getgenv().UndergroundAmount = -999
  local OK = false
  local toggle = false
   
  local function Notify(text)
          game:GetService("StarterGui"):SetCore("SendNotification",
          {
              Title = "VUX LOVES YOU",
              Text = text,
              Duration = 1,
              Button1 = ""
          }
          )
      end
   
  game:GetService("RunService").heartbeat:Connect(function()
      if OK == true then
      if getgenv().Underground ~= false then 
      local vel = game.Players.LocalPlayer.Character.HumanoidRootPart.Velocity
      game.Players.LocalPlayer.Character.HumanoidRootPart.Velocity = Vector3.new(-999,-         getgenv().UndergroundAmount,-999) 
      game:GetService("RunService").RenderStepped:Wait()
      game.Players.LocalPlayer.Character.HumanoidRootPart.Velocity = vel
      end
      end
  end)
   
  game.Players.LocalPlayer:GetMouse().KeyDown:Connect(function(KeyPressed)
   if KeyPressed == "v" then
       if toggle == false then
  toggle = true
              OK = true
  Notify('anti on >:)')
  else
  toggle = false
          OK = false
  Notify('anti  off >:(')
  end
  end
  end)
end)


Player:AddButton("Dh force Reset | Key {K}", function(IhateGayPeople)
game.Players.LocalPlayer:GetMouse().KeyDown:Connect(function(KeyPressed)
 if KeyPressed == "k" then
	for L_170_forvar0, L_171_forvar1 in pairs(game.Players.LocalPlayer.Character:GetDescendants()) do
		if L_171_forvar1:IsA("BasePart") then
			L_171_forvar1:Destroy()
		end
	end
	end
end)
end)




cool:AddButton("GodMode | No Key", function(IhateGayPeople)
local localPlayer = game:GetService('Players').LocalPlayer;
                local localCharacter = localPlayer.Character;
                localCharacter:FindFirstChildOfClass('Humanoid').Health = 0;
                local newCharacter = localPlayer.CharacterAdded:Wait();
                local spoofFolder = Instance.new('Folder');
                spoofFolder.Name = 'FULLY_LOADED_CHAR';
                spoofFolder.Parent = newCharacter;
                newCharacter:WaitForChild('RagdollConstraints'):Destroy();
                local spoofValue = Instance.new('BoolValue', newCharacter);
                spoofValue.Name = 'RagdollConstraints';
                local name = game.Players.LocalPlayer.Name
                local lol =    game.Workspace:WaitForChild(name)
                local money = Instance.new("Folder",game.Players.LocalPlayer.Character);money.Name = "FULLY_LOADED_CHAR"
                lol.Parent = game.Workspace.Players
                game.Players.LocalPlayer.Character:WaitForChild("BodyEffects")
                game.Players.LocalPlayer.Character.BodyEffects.BreakingParts:Destroy()
end)



cool:AddButton("No Slow Down | No Key}", function(IhateGayPeople)
   game:GetService('RunService'):BindToRenderStep("Anti-Slow", 0 , function()
            if game.Players.LocalPlayer.Character.BodyEffects.Movement:FindFirstChild("NoWalkSpeed") then game.Players.LocalPlayer.Character.BodyEffects.Movement:FindFirstChild("NoWalkSpeed"):Destroy() end
            if game.Players.LocalPlayer.Character.BodyEffects.Movement:FindFirstChild("ReduceWalk") then game.Players.LocalPlayer.Character.BodyEffects.Movement:FindFirstChild("ReduceWalk"):Destroy() end
            if game.Players.LocalPlayer.Character.BodyEffects.Movement:FindFirstChild("NoJumping") then game.Players.LocalPlayer.Character.BodyEffects.Movement:FindFirstChild("NoJumping"):Destroy() end
            if game.Players.LocalPlayer.Character.BodyEffects.Reload.Value == true then game.Players.LocalPlayer.Character.BodyEffects.Reload.Value = false
            end
            end)        
end)




cool:AddButton("Reach | No Key", function(IhateGayPeople)
game:GetService('RunService'):BindToRenderStep("Reach", 0 , function(value)
            local success, err = pcall(function()
                if game.Players.LocalPlayer.Character.BodyEffects.Attacking.Value == true then
                    for i,v in pairs(game:GetService('Players'):GetChildren()) do
                        if (v.Character.HumanoidRootPart.Position - game.Players.LocalPlayer.Character.LeftHand.Position).Magnitude <= 50 then
                            if game.Players.LocalPlayer.Character:FindFirstChildOfClass("Tool") then
                                if game.Players.LocalPlayer.Character:FindFirstChildOfClass("Tool"):FindFirstChild('Handle') then
                                    firetouchinterest(game.Players.LocalPlayer.Character:FindFirstChildOfClass("Tool").Handle, v.Character.UpperTorso, 0)
                                else
                                    firetouchinterest(game.Players.LocalPlayer.Character['RightHand'], v.Character.UpperTorso, 0)
                                    firetouchinterest(game.Players.LocalPlayer.Character['LeftHand'], v.Character.UpperTorso, 0)
                                    firetouchinterest(game.Players.LocalPlayer.Character['RightFoot'], v.Character.UpperTorso, 0)
                                    firetouchinterest(game.Players.LocalPlayer.Character['LeftFoot'], v.Character.UpperTorso, 0)
                                    firetouchinterest(game.Players.LocalPlayer.Character['RightLowerLeg'], v.Character.UpperTorso, 0)
                                    firetouchinterest(game.Players.LocalPlayer.Character['LeftLowerLeg'], v.Character.UpperTorso, 0)
                                end
                            end
                        end
                    end
                end
                end)
            end)
end)






cool:AddButton("Auto Farm | No Key", function(IhateGayPeople)
local humanoid = game.Players.LocalPlayer.Character.Humanoid
        local tool = game.Players.LocalPlayer.Backpack.Combat
        
        local function getMoneyAroundMe() 
            wait(0.6)
            for i, money in ipairs(game.Workspace.Ignored.Drop:GetChildren()) do
                if money.Name == "MoneyDrop" and (money.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).magnitude <= 18 then
                    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = money.CFrame
                    fireclickdetector(money.ClickDetector)
                   wait(0.6)
                end  
            end
        end
        
        
        local function startAutoFarm() 
            humanoid:EquipTool(tool)
        
            for i, v in ipairs(game.Workspace.Cashiers:GetChildren()) do
                game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = v.Open.CFrame * CFrame.new(0, 0, 2)
        
                for i = 0, 15 do
                    wait(0.5)
                    tool:Activate()
                end
        
                getMoneyAroundMe()
        
            end
        
        
        
            wait(0.6)
         
        end
        
        startAutoFarm()
end)


player:AddButton("ESP | No key", function(IhateGayPeople)
local settings = {
   defaultcolor = Color3.fromRGB(190,20,190),
   teamcheck = false
};
 
-- services
local runService = game:GetService("RunService");
local players = game:GetService("Players");
 
-- variables
local localPlayer = players.LocalPlayer;
local camera = workspace.CurrentCamera;
 
-- functions
local newVector2, newColor3, newDrawing = Vector2.new, Color3.new, Drawing.new;
local tan, rad = math.tan, math.rad;
local round = function(...) local a = {}; for i,v in next, table.pack(...) do a[i] = math.round(v); end return unpack(a); end;
local wtvp = function(...) local a, b = camera.WorldToViewportPoint(camera, ...) return newVector2(a.X, a.Y), b, a.Z end;
 
local espCache = {};
local function createEsp(player)
   local drawings = {};
 
   drawings.box = newDrawing("Square");
   drawings.box.Thickness = 1;
   drawings.box.Filled = false;
   drawings.box.Color = settings.defaultcolor;
   drawings.box.Visible = false;
   drawings.box.ZIndex = 2;
 
   drawings.boxoutline = newDrawing("Square");
   drawings.boxoutline.Thickness = 3;
   drawings.boxoutline.Filled = false;
   drawings.boxoutline.Color = newColor3();
   drawings.boxoutline.Visible = false;
   drawings.boxoutline.ZIndex = 1;
 
   espCache[player] = drawings;
end
 
local function removeEsp(player)
   if rawget(espCache, player) then
       for _, drawing in next, espCache[player] do
           drawing:Remove();
       end
       espCache[player] = nil;
   end
end
 
local function updateEsp(player, esp)
   local character = player and player.Character;
   if character then
       local cframe = character:GetModelCFrame();
       local position, visible, depth = wtvp(cframe.Position);
       esp.box.Visible = visible;
       esp.boxoutline.Visible = visible;
 
       if cframe and visible then
           local scaleFactor = 1 / (depth * tan(rad(camera.FieldOfView / 2)) * 2) * 1000;
           local width, height = round(4 * scaleFactor, 5 * scaleFactor);
           local x, y = round(position.X, position.Y);
 
           esp.box.Size = newVector2(width, height);
           esp.box.Position = newVector2(round(x - width / 2, y - height / 2));
           esp.box.Color = settings.teamcolor and player.TeamColor.Color or settings.defaultcolor;
 
           esp.boxoutline.Size = esp.box.Size;
           esp.boxoutline.Position = esp.box.Position;
       end
   else
       esp.box.Visible = false;
       esp.boxoutline.Visible = false;
   end
end
 
-- main
for _, player in next, players:GetPlayers() do
   if player ~= localPlayer then
       createEsp(player);
   end
end
 
players.PlayerAdded:Connect(function(player)
   createEsp(player);
end);
 
players.PlayerRemoving:Connect(function(player)
   removeEsp(player);
end)
 
runService:BindToRenderStep("esp", Enum.RenderPriority.Camera.Value, function()
   for player, drawings in next, espCache do
       if settings.teamcheck and player.Team == localPlayer.Team then
           continue;
       end
 
       if drawings and player ~= localPlayer then
           updateEsp(player, drawings);
       end
   end
end)
end)

ColorToggle:AddColorpicker(Color3.fromRGB(75, 0,130), function(ztx)
   
end)

local ToggleBind = testSection:AddToggle("Keybind w/Toggle", false, function(e)

end)

ToggleBind:AddKeybind(RightShift)

AimingTab:CreateConfigSystem("right") --this is the config system
