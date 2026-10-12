-- [Obfuscated by UNC Luau Tool]
local _env = (getgenv and getgenv()) or shared
if _env._FencingLoaded then return end
_env._FencingLoaded = true

local _s,_u,_g,_w,_p = game:GetService, "Players", "Workspace", "ReplicatedStorage", "UserInputService"
local Players, Workspace, ReplicatedStorage, UserInputService = _s(_u), _s(_g), _s(_w), _s(_p)
local CoreGui = game:GetService("CoreGui")
local LocalPlayer = Players.LocalPlayer
local guiName, parentGui = "\x46\x65\x6e\x63\x69\x6e\x67\x53\x70\x72\x61\x79\x50\x61\x69\x6e\x74\x47\x55\x49", (gethui and gethui()) or CoreGui or LocalPlayer:WaitForChild("PlayerGui")

if parentGui:FindFirstChild(guiName) then parentGui[guiName]:Destroy() end

local ScreenGui = Instance.new("ScreenGui")
ScreenGui.Name, ScreenGui.Parent, ScreenGui.ResetOnSpawn, ScreenGui.ZIndexBehavior = guiName, parentGui, false, Enum.ZIndexBehavior.Sibling

local MainFrame = Instance.new("Frame")
MainFrame.Name, MainFrame.Parent, MainFrame.BackgroundColor3, MainFrame.BorderSizePixel = "MainFrame", ScreenGui, Color3.fromRGB(20, 20, 26), 0
MainFrame.Position, MainFrame.Size, MainFrame.Active, MainFrame.ZIndex = UDim2.new(0.5, -200, 0.5, -110), UDim2.new(0, 400, 0, 220), true, 1

local MainCorner = Instance.new("UICorner") MainCorner.CornerRadius = UDim.new(0, 10) MainCorner.Parent = MainFrame
local MainStroke = Instance.new("UIStroke") MainStroke.Parent = MainFrame MainStroke.Color = Color3.fromRGB(50, 50, 70) MainStroke.Thickness = 1 MainStroke.Transparency = 0.4

local TopBar = Instance.new("Frame")
TopBar.Name, TopBar.Parent, TopBar.BackgroundColor3, TopBar.BorderSizePixel, TopBar.Size, TopBar.ZIndex = "TopBar", MainFrame, Color3.fromRGB(28, 28, 36), 0, UDim2.new(1, 0, 0, 40), 3

local TopBarCorner = Instance.new("UICorner") TopBarCorner.CornerRadius = UDim.new(0, 10) TopBarCorner.Parent = TopBar
local TopBarCover = Instance.new("Frame") TopBarCover.Parent = TopBar TopBarCover.BackgroundColor3 = Color3.fromRGB(28, 28, 36) TopBarCover.BorderSizePixel = 0 TopBarCover.Position = UDim2.new(0, 0, 1, -5) TopBarCover.Size = UDim2.new(1, 0, 0, 5) TopBarCover.ZIndex = 3

local TitleLabel = Instance.new("TextLabel")
TitleLabel.Parent, TitleLabel.BackgroundTransparency, TitleLabel.Position, TitleLabel.Size = TopBar, true, UDim2.new(0, 15, 0, 0), UDim2.new(0, 300, 1, 0)
TitleLabel.Font, TitleLabel.Text, TitleLabel.TextColor3, TitleLabel.TextSize, TitleLabel.TextXAlignment, TitleLabel.ZIndex = Enum.Font.GothamBold, "FENCING MAP - LẤY PHUN SƠN", Color3.fromRGB(240, 240, 255), 13, Enum.TextXAlignment.Left, 4

local CloseButton = Instance.new("TextButton")
CloseButton.Parent, CloseButton.BackgroundColor3, CloseButton.BorderSizePixel, CloseButton.Position, CloseButton.Size = TopBar, Color3.fromRGB(235, 69, 95), 0, UDim2.new(1, -32, 0.5, -12), UDim2.new(0, 24, 0, 24)
CloseButton.Font, CloseButton.Text, CloseButton.TextColor3, CloseButton.TextSize, CloseButton.ZIndex = Enum.Font.GothamBold, "✕", Color3.fromRGB(255, 255, 255), 12, 4
local CloseCorner = Instance.new("UICorner") CloseCorner.CornerRadius = UDim.new(0, 6) CloseCorner.Parent = CloseButton
CloseButton.MouseButton1Click:Connect(function() ScreenGui:Destroy() _env._FencingLoaded = nil end)

local dragging, dragInput, dragStart, startPos
TopBar.InputBegan:Connect(function(input)
    if input.UserInputType == Enum.UserInputType.MouseButton1 or input.UserInputType == Enum.UserInputType.Touch then
        dragging, dragStart, startPos = true, input.Position, MainFrame.Position
        input.Changed:Connect(function() if input.UserInputState == Enum.UserInputState.End then dragging = false end end)
    end
end)
UserInputService.InputChanged:Connect(function(input)
    if input.UserInputType == Enum.UserInputType.MouseButton1 or input.UserInputType == Enum.UserInputType.Touch then dragInput = input end
end)
game:GetService("RunService").RenderStepped:Connect(function()
    if dragging and dragInput then
        local delta = dragInput.Position - dragStart
        MainFrame.Position = UDim2.new(startPos.X.Scale, startPos.X.Offset + delta.X, startPos.Y.Scale, startPos.Y.Offset + delta.Y)
    end
end)

local StatusLabel = Instance.new("TextLabel")
StatusLabel.Parent, StatusLabel.BackgroundTransparency, StatusLabel.Position, StatusLabel.Size = MainFrame, true, UDim2.new(0, 20, 0, 55), UDim2.new(0, 360, 0, 30)
StatusLabel.Font, StatusLabel.Text, StatusLabel.TextColor3, StatusLabel.TextSize, StatusLabel.TextXAlignment, StatusLabel.ZIndex = Enum.Font.GothamMedium, "Trạng thái: Sẵn sàng tìm kiếm bình phun sơn.", Color3.fromRGB(180, 180, 200), 12, Enum.TextXAlignment.Left, 3

local GetSprayBtn = Instance.new("TextButton")
GetSprayBtn.Name, GetSprayBtn.Parent, GetSprayBtn.BackgroundColor3, GetSprayBtn.BorderSizePixel = "GetSprayBtn", MainFrame, Color3.fromRGB(88, 101, 242), 0
GetSprayBtn.Position, GetSprayBtn.Size, GetSprayBtn.Font, GetSprayBtn.Text, GetSprayBtn.TextColor3, GetSprayBtn.TextSize, GetSprayBtn.ZIndex = UDim2.new(0, 20, 0, 100), UDim2.new(0, 360, 0, 42), Enum.Font.GothamBold, "LẤY BÌNH PHUN SƠN (SPRAY CAN)", Color3.fromRGB(255, 255, 255), 13, 3
local BtnCorner = Instance.new("UICorner") BtnCorner.CornerRadius = UDim.new(0, 8) BtnCorner.Parent = GetSprayBtn

local TeleportBtn = Instance.new("TextButton")
TeleportBtn.Name, TeleportBtn.Parent, TeleportBtn.BackgroundColor3, TeleportBtn.BorderSizePixel = "TeleportBtn", MainFrame, Color3.fromRGB(45, 45, 58), 0
TeleportBtn.Position, TeleportBtn.Size, TeleportBtn.Font, TeleportBtn.Text, TeleportBtn.TextColor3, TeleportBtn.TextSize, TeleportBtn.ZIndex = UDim2.new(0, 20, 0, 155), UDim2.new(0, 360, 0, 42), Enum.Font.GothamBold, "TELEPORT ĐẾN VỊ TRÍ BÌNH SƠN", Color3.fromRGB(220, 220, 230), 13, 3
local TeleCorner = Instance.new("UICorner") TeleCorner.CornerRadius = UDim.new(0, 8) TeleCorner.Parent = TeleportBtn

local function scanForSprayPaint()
    StatusLabel.Text = "Trạng thái: Đang quét Workspace và ReplicatedStorage..."
    for _, d in ipairs(ReplicatedStorage:GetDescendants()) do
        local nl = string.lower(d.Name)
        if (string.find(nl, "spray") or string.find(nl, "paint") or string.find(nl, "sơn") or string.find(nl, "phun")) and d:IsA("Tool") then
            return d
        end
    end
    for _, d in ipairs(Workspace:GetDescendants()) do
        local nl = string.lower(d.Name)
        if string.find(nl, "spray") or string.find(nl, "paint") or string.find(nl, "sơn") or string.find(nl, "phun") then
            return d
        end
    end
    return nil
end

GetSprayBtn.MouseButton1Click:Connect(function()
    local target = scanForSprayPaint()
    if target then
        pcall(function()
            if target:IsA("Tool") then
                target:Clone().Parent = LocalPlayer.Backpack
                StatusLabel.Text = "Trạng thái: Đã lấy Tool vào Backpack thành công!"
            elseif target:IsA("Model") and target:FindFirstChildOfClass("Tool") then
                target:FindFirstChildOfClass("Tool"):Clone().Parent = LocalPlayer.Backpack
                StatusLabel.Text = "Trạng thái: Đã lấy Tool từ Model thành công!"
            elseif target:IsA("BasePart") then
                local char = LocalPlayer.Character
                if char and char:FindFirstChild("HumanoidRootPart") then
                    char.HumanoidRootPart.CFrame = target.CFrame + Vector3.new(0, 3, 0)
                    StatusLabel.Text = "Trạng thái: Đã dịch chuyển đến vật phẩm!"
                end
            end
        end)
    else
        StatusLabel.Text = "Trạng thái: Tạo Custom Spray Tool dự phòng..."
        pcall(function()
            local tool = Instance.new("Tool") tool.Name = "SprayPaint (Custom)"
            local handle = Instance.new("Part") handle.Name = "Handle" handle.Size = Vector3.new(1, 2, 1) handle.BrickColor = BrickColor.new("Bright red") handle.Parent = tool
            tool.Parent = LocalPlayer.Backpack
            StatusLabel.Text = "Trạng thái: Đã tạo thành công Custom Spray Tool!"
        end)
    end
end)

TeleportBtn.MouseButton1Click:Connect(function()
    local target = scanForSprayPaint()
    if target then
        pcall(function()
            local p = target:IsA("BasePart") and target or (target:IsA("Model") and (target.PrimaryPart or target:FindFirstChildWhichIsA("BasePart"))) or (target:IsA("Tool") and target:FindFirstChild("Handle"))
            local hrp = LocalPlayer.Character and LocalPlayer.Character:FindFirstChild("HumanoidRootPart")
            if p and hrp then
                hrp.CFrame = p.CFrame + Vector3.new(0, 3, 0)
                StatusLabel.Text = "Trạng thái: Teleport thành công!"
            else
                StatusLabel.Text = "Trạng thái: Không tìm thấy tọa độ hợp lệ."
            end
        end)
    else
        StatusLabel.Text = "Trạng thái: Không tìm thấy đối tượng để tele."
    end
end)
