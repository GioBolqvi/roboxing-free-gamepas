local ScreenGui = Instance.new("ScreenGui")
local Frame = Instance.new("Frame")
local UICorner = Instance.new("UICorner")
local UIStroke = Instance.new("UIStroke")
local ToggleButton = Instance.new("TextButton")
local InfoFrame = Instance.new("Frame")
local InfoText = Instance.new("TextLabel")

ScreenGui.Parent = game.CoreGui

Frame.Parent = ScreenGui
Frame.BackgroundColor3 = Color3.fromRGB(50, 50, 50)
Frame.Size = UDim2.new(0, 300, 0, 350)
Frame.Position = UDim2.new(0.5, -150, 0.5, -175)
Frame.Active = true
Frame.Draggable = true
Frame.Visible = true

UICorner.Parent = Frame
UICorner.CornerRadius = UDim.new(0, 10)

UIStroke.Parent = Frame
UIStroke.Color = Color3.fromRGB(0, 255, 255)
UIStroke.Thickness = 2

ToggleButton.Parent = ScreenGui
ToggleButton.BackgroundColor3 = Color3.fromRGB(70, 70, 70)
ToggleButton.Size = UDim2.new(0, 100, 0, 40)
ToggleButton.Position = UDim2.new(0, 20, 1, -60)
ToggleButton.Text = "Toggle GUI"
ToggleButton.TextColor3 = Color3.fromRGB(255, 255, 255)
ToggleButton.TextSize = 16
ToggleButton.Font = Enum.Font.SourceSansBold

local ToggleButtonCorner = Instance.new("UICorner", ToggleButton)
ToggleButtonCorner.CornerRadius = UDim.new(0, 10)

InfoFrame.Parent = Frame
InfoFrame.BackgroundColor3 = Color3.fromRGB(70, 70, 70)
InfoFrame.Size = UDim2.new(0, 260, 0, 50)
InfoFrame.Position = UDim2.new(0, 20, 1, -60)
InfoFrame.Active = true
InfoFrame.Draggable = true

local InfoFrameCorner = Instance.new("UICorner", InfoFrame)
InfoFrameCorner.CornerRadius = UDim.new(0, 10)

InfoText.Parent = InfoFrame
InfoText.BackgroundTransparency = 1
InfoText.Size = UDim2.new(1, 0, 1, 0)
InfoText.Text = "Free RO-BOXING animation gamepass by Gio"
InfoText.TextColor3 = Color3.fromRGB(255, 255, 255)
InfoText.TextSize = 14
InfoText.Font = Enum.Font.SourceSansBold
InfoText.TextWrapped = true

local function createButton(parent, position, text)
    local button = Instance.new("TextButton")
    button.Parent = parent
    button.BackgroundColor3 = Color3.fromRGB(70, 70, 70)
    button.Size = UDim2.new(0, 130, 0, 40)
    button.Position = position
    button.Text = text
    button.TextColor3 = Color3.fromRGB(255, 255, 255)
    button.TextSize = 14
    button.Font = Enum.Font.SourceSansBold

    local textStroke = Instance.new("UIStroke", button)
    textStroke.Thickness = 2
    textStroke.Color = Color3.fromRGB(0, 0, 0)

    local buttonCorner = Instance.new("UICorner", button)
    buttonCorner.CornerRadius = UDim.new(0, 10)

    return button
end

local buttons = {}
local animations = {
    {id = "3623649172", name = "Naruto Run"},
    {id = "3623496990", name = "Floss"},
    {id = "3622973244", name = "Dab"},
    {id = "3623529701", name = "T Pose Fly"},
    {id = "3622946649", name = "Fat Dab"},
    {id = "3623025151", name = "Jumping Jacks"},
    {id = "3623601385", name = "The Wiggler"},
    {id = "3623575587", name = "Laugh"},
}

for i, anim in ipairs(animations) do
    local row = math.floor((i - 1) / 2)
    local col = (i - 1) % 2
    local button = createButton(
        Frame,
        UDim2.new(0, 20 + col * 140, 0, 10 + row * 50),
        anim.name
    )
    buttons[anim.id] = button
end

local player = game.Players.LocalPlayer
local animator
local playingTrack

local function setupCharacter()
    local character = player.Character or player.CharacterAdded:Wait()
    local humanoid = character:WaitForChild("Humanoid")
    animator = humanoid:FindFirstChild("Animator") or humanoid:WaitForChild("Animator")
end

setupCharacter()

player.CharacterAdded:Connect(setupCharacter)

local function stopAllAnimations()
    for _, track in ipairs(animator:GetPlayingAnimationTracks()) do
        track:Stop()
    end
end

for id, button in pairs(buttons) do
    button.MouseButton1Click:Connect(function()
        if playingTrack and playingTrack.Animation.AnimationId == "rbxassetid://" .. id then
            playingTrack:Stop()
            playingTrack = nil
        else
            stopAllAnimations()
            local animation = Instance.new("Animation")
            animation.AnimationId = "rbxassetid://" .. id
            playingTrack = animator:LoadAnimation(animation)
            playingTrack.Priority = Enum.AnimationPriority.Action
            playingTrack:Play()
        end
    end)
end

ToggleButton.MouseButton1Click:Connect(function()
    Frame.Visible = not Frame.Visible
end)
