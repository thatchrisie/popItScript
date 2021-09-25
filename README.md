-- Gui to Lua
-- Version: 3.2

-- Instances:

local ScreenGui = Instance.new("ScreenGui")
local Frame = Instance.new("Frame")
local UICorner = Instance.new("UICorner")
local on = Instance.new("TextLabel")
local they = Instance.new("TextLabel")
local en = Instance.new("TextLabel")

--Properties:

ScreenGui.Parent = game.Players.LocalPlayer:WaitForChild("PlayerGui")
ScreenGui.ZIndexBehavior = Enum.ZIndexBehavior.Sibling

Frame.Parent = ScreenGui
Frame.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
Frame.Position = UDim2.new(0.0104166707, 0, 0.905277431, 0)
Frame.Size = UDim2.new(0.130729169, 0, 0.06901218, 0)

UICorner.Parent = Frame

on.Name = "on"
on.Parent = Frame
on.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
on.BackgroundTransparency = 1.000
on.Size = UDim2.new(0, 146, 0, 21)
on.Font = Enum.Font.PermanentMarker
on.Text = "On a board: true"
on.TextColor3 = Color3.fromRGB(0, 0, 0)
on.TextScaled = true
on.TextSize = 14.000
on.TextWrapped = true
on.TextXAlignment = Enum.TextXAlignment.Left

they.Name = "they"
they.Parent = Frame
they.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
they.BackgroundTransparency = 1.000
they.Position = UDim2.new(0, 0, 0.294117659, 0)
they.Size = UDim2.new(0, 146, 0, 21)
they.Font = Enum.Font.PermanentMarker
they.Text = "Other side accepted: true"
they.TextColor3 = Color3.fromRGB(0, 0, 0)
they.TextScaled = true
they.TextSize = 14.000
they.TextWrapped = true
they.TextXAlignment = Enum.TextXAlignment.Left

en.Name = "en"
en.Parent = Frame
en.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
en.BackgroundTransparency = 1.000
en.Position = UDim2.new(0, 0, 0.588235319, 0)
en.Size = UDim2.new(0, 212, 0, 21)
en.Font = Enum.Font.PermanentMarker
en.Text = "Scam is enabled: false (G to enable)"
en.TextColor3 = Color3.fromRGB(0, 0, 0)
en.TextScaled = true
en.TextSize = 14.000
en.TextWrapped = true
en.TextXAlignment = Enum.TextXAlignment.Left

--nav

local thatGui = ScreenGui

local Board = Instance.new("ObjectValue", thatGui.Frame)

local YourSide = Instance.new("ObjectValue", Board)

local TheirSide = Instance.new("ObjectValue", Board)

local onV = Instance.new("BoolValue", thatGui.Frame)

local enV = Instance.new("BoolValue", thatGui.Frame)

local theyV = Instance.new("BoolValue", thatGui.Frame)

Board.Name = "Board"

YourSide.Name = "YourSide"

TheirSide.Name = "TheirSide"

onV.Name = "onV"

enV.Name = "enV"

theyV.Name = "theyV"

onV.Value = true

theyV.Value = true

game:GetService("UserInputService").InputBegan:Connect(function(key, gameprocessed)
    if key.KeyCode == Enum.KeyCode.F and not gameprocessed then
        ScreenGui:Destroy()
        
        script:Destroy()
    end
end)

-- Scripts:

local function VRZN_fake_script() -- on.LocalScript
    local script = Instance.new("LocalScript", on)

    while true do
        wait()

        --local success, err = pcall(function()

        if script.Parent.Parent.onV.Value then
            script.Parent.Text = "On a board: " .. "true"
        else
            script.Parent.Text = "On a board: " .. "false"
        end
        --end)

        --print(success, err)
    end
end
coroutine.wrap(VRZN_fake_script)()
local function LWAIXV_fake_script() -- they.LocalScript
    local script = Instance.new("LocalScript", they)

    while true do
        wait()
        --local success, err = pcall(function()
        if script.Parent.Parent.theyV.Value then
            script.Parent.Text = "Other side accepted: " .. "true"
        else
            script.Parent.Text = "Other side accepted: " .. "false"
        end
        --end)
        --print(success, err)
    end
end
coroutine.wrap(LWAIXV_fake_script)()
local function TWYJPK_fake_script() -- en.LocalScript
    local script = Instance.new("LocalScript", en)

    while true do
        wait()

        --local success, err = pcall(function()

        if script.Parent.Parent.enV.Value then
            script.Parent.Text = "Scam is enabled: " .. "true" .. " (G to enable)"
        else
            script.Parent.Text = "Scam is enabled: " .. "false" .. " (G to enable)"
        end
        --end)
        --print(success, err)
    end
end
coroutine.wrap(TWYJPK_fake_script)()
local function UWUJSYO_fake_script() -- Frame.LocalScript
    local script = Instance.new("LocalScript", Frame)

    local UIS = game:GetService("UserInputService")

    UIS.InputBegan:Connect(
        function(key, gameprocessed)
            if key.KeyCode == Enum.KeyCode.G and not gameprocessed then
                script.Parent.enV.Value = not script.Parent.enV.Value
            end
        end
    )
end
coroutine.wrap(UWUJSYO_fake_script)()
local function PVEOOI_fake_script() -- Frame.LocalScript
    local script = Instance.new("LocalScript", Frame)

    local player = game.Players.LocalPlayer

    while true do
        wait()

        local success, err =
            pcall(
            function()
                local yes = false

                for i, v in pairs(workspace.Boards:GetChildren()) do
                    --print(type(v.Player1.Value), type(v.Player2.Value))

                    if v:FindFirstChild("Player1") then
                        if v.Player1.Value == player or v.Player2.Value == player then
                            script.Parent.Board.Value = v

                            local your =
                                v.Player1.Value == player and v.Player1Action or
                                v.Player2.Value == player and v.Player2Action or
                                nil

                            local their =
                                v.Player1.Value ~= player and v.Player1Action or
                                v.Player2.Value ~= player and v.Player2Action

                            script.Parent.Board.YourSide.Value = your

                            script.Parent.Board.TheirSide.Value = their

                            script.Parent.onV.Value = true

                            yes = true

                            break
                        end
                    end

                    if not yes then
                        script.Parent.Board.Value = nil

                        script.Parent.Board.YourSide.Value = nil

                        script.Parent.Board.TheirSide.Value = nil

                        script.Parent.onV.Value = false
                    end
                end
            end
        )
        --print(success, err)
    end
end
coroutine.wrap(PVEOOI_fake_script)()
local function LBYI_fake_script() -- Frame.LocalScript
    local script = Instance.new("LocalScript", Frame)

    while true do
        wait()

        if script.Parent.Board.TheirSide.Value then
            --print(script.Parent.Board.YourSide.Value.Value, script.Parent.Board.TheirSide.Value.Value)

            if script.Parent.Board.TheirSide.Value.Value == "Done" then
                --print("tV")
                script.Parent.theyV.Value = true
            else
                --print("f")
                script.Parent.theyV.Value = false
            end
        else
            --print("f1")
            script.Parent.theyV.Value = false
        end
    end
end
coroutine.wrap(LBYI_fake_script)()
local function LFULR_fake_script() -- Frame.LocalScript
    local script = Instance.new("LocalScript", Frame)

    while true do
        wait()

        local success, err =
            pcall(
            function()
                print(script.Parent.onV.Value, script.Parent.enV.Value, script.Parent.theyV.Value)

                if script.Parent.onV.Value and script.Parent.enV.Value and script.Parent.theyV.Value then
                    print(123)

                    local yourSide

                    local controlNot

                    local helMag = math.huge

                    local bbb

                    for i, v in pairs(script.Parent.Board.Value:GetChildren()) do
                        if v.Name == "Controls" then
                            local mag =
                                (v.Done.Pad.Position -
                                TheirSide.Value.Parent[TheirSide.Value.Name:gsub("Action", "")].Value.Character.HumanoidRootPart.Position).Magnitude

                            if helMag == math.huge then
                                helMag = mag

                                bbb = v
                            elseif mag < helMag then
                                yourSide = bbb
                            else
                                yourSide = v
                            end
                        end
                    end

                    local toTp = yourSide.Done.Pad.CFrame

                    local char = game.Players.LocalPlayer.Character or game.Players.LocalPlayer.CharacterAdded:Wait()

                    char.HumanoidRootPart.CFrame = toTp + Vector3.new(0, 4, 0)

                    local hedermouth = false

                    local function bsf()
                        local n = false

                        for i, v2 in pairs(workspace.Dropped:GetChildren()) do
                            if
                                v2.Owner.Value == game.Players.LocalPlayer or
                                    v2.Owner.Value == game.Players.LocalPlayer.Character
                                    
                                    --print("take")
                             then
                                 print("take")
                                 
                                 for is, vs in pairs(game.Players.LocalPlayer.Character:GetChildren()) do
                                    if vs:IsA("MeshPart") or vs:IsA("BasePart") and v then
                                        print("1n1", v2, vs)
                                        
                                        firetouchinterest(vs, v2.Handle, 1)
                                        
                                        firetouchinterest(vs, v2.Handle, 0)
                                        
                                        --char.HumanoidRootPart.CFrame = v2.Handle.CFrame
                                        
                                        
                                        n = true
                                        
                                        print(2)
                                        
                                        break
                                    end
                                 end
                            
                            print(3)
                            end
                        end

                        if n then
                            wait()
                            
                            bsf()
                        end
                    end

                        bsf()

                        local p = false

                        spawn(function()
                                repeat
                                    game:GetService("ReplicatedStorage").RemoteEvents.Jumped:FireServer()
                                    
                                    print("jmjump")

                                    wait()
                                until p
                        end)

                        wait(3)

                        p = true

                        char.HumanoidRootPart.CFrame = script.Parent.Board.Value.MAIN.CFrame + Vector3.new(0, 4, 0)

                        script.Parent.enV.Value = false
 
                end
            end)

        print(success, err)
    end
end
coroutine.wrap(LFULR_fake_script)()
