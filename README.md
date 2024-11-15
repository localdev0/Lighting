## Get Stuff
```lua
local Halloween = Color3.fromRGB(255, 60, 1) --october
local Christmas = Color3.fromRGB(250, 0, 0) --chrtismas
local Regular = Color3.fromRGB(0, 85, 255) --Regular
local Regular = Color3.fromRGB(240, 240, 0) --regular

--replace the one that is a holiday with the one you want to use


local player = game:GetService("Players").LocalPlayer

local userInputService = game:GetService("UserInputService")

local Players = game:GetService("Players")
local RunService = game:GetService("RunService")
local LocalPlayer = Players.LocalPlayer
local Character = LocalPlayer.Character or LocalPlayer.CharacterAdded:Wait()
local config = { DefaultSpeed = 20, MaxSpeed = 100 }
local moveToUsing = {}
local walkspeedEnabled = false
local customWalkSpeed = config.DefaultSpeed


if not LPH_OBFUSCATED then
	getfenv().LPH_NO_VIRTUALIZE = function(f) return f end
	getfenv().LPH_JIT_MAX = function(f) return f end
end


local LightingLib = {}
local TS = game:GetService("TweenService")
local RS = game:GetService("RunService")
local UIS = game:GetService("UserInputService")

local function isPlayerOnMobile()
	
    return UIS.TouchEnabled and not UIS.KeyboardEnabled and not UIS.MouseEnabled

end
local Mouse = LocalPlayer:GetMouse()

local function CreateDrag(gui)
	local dragging = false
	local dragInput
	local dragStart
	local startPos

	local function update(input)
		local delta = input.Position - dragStart
		gui.Position = UDim2.new(
			startPos.X.Scale,
			startPos.X.Offset + delta.X,
			startPos.Y.Scale,
			startPos.Y.Offset + delta.Y
		)
	end

	gui.InputBegan:Connect(function(input)
		if input.UserInputType == Enum.UserInputType.MouseButton1 or input.UserInputType == Enum.UserInputType.Touch then
			dragging = true
			dragStart = input.Position
			startPos = gui.Position

			input.Changed:Connect(function()
				if input.UserInputState == Enum.UserInputState.End then
					dragging = false
				end
			end)
		end
	end)

	gui.InputChanged:Connect(function(input)
		if input.UserInputType == Enum.UserInputType.MouseMovement or input.UserInputType == Enum.UserInputType.Touch then
			dragInput = input
		end
	end)

	UIS.InputChanged:Connect(function(input)
		if input == dragInput and dragging then
			update(input)
		end
	end)
end

function LightingLib:newWindow(Title: string)
	local window = {
		CurrentTab = nil
	}

	local LightingUI = Instance.new('ScreenGui', RS:IsStudio() and game.Players.LocalPlayer.PlayerGui or game:GetService("CoreGui"))
	local MainFrame = Instance.new('Frame', LightingUI)
	local MainFrameCorner = Instance.new('UICorner', MainFrame)
	local Line = Instance.new('Frame', MainFrame)
	local Line2 = Instance.new('Frame', MainFrame)
	local Line3 = Instance.new('Frame', MainFrame)
	local UiTitle = Instance.new('TextLabel', MainFrame)
	local Logo = Instance.new('ImageLabel', MainFrame)
	local TabHolder = Instance.new('Frame', MainFrame)
	local UIListLayout = Instance.new('UIListLayout', TabHolder)
	local UIPadding = Instance.new('UIPadding', TabHolder)
	local Welcome = Instance.new('TextLabel', MainFrame)
	local SettingsIcon = Instance.new('ImageLabel', MainFrame)

	LightingUI.Name = "LightingUI"
	LightingUI.ZIndexBehavior = Enum.ZIndexBehavior.Sibling

	MainFrame.Name = "MainFrame"
	MainFrame.Position = UDim2.new(0.2242, 0, 0.2399, 0)
	MainFrame.Size = UDim2.new(0, 752, 0, 414)
	MainFrame.BackgroundColor3 = Color3.new(0.051, 0.051, 0.051)
	MainFrame.BorderSizePixel = 0

	Line.Name = "Line"
	Line.Position = UDim2.new(0, 0, 0.8696, 0)
	Line.Size = UDim2.new(0, 752, 0, 1)
	Line.BackgroundColor3 = Color3.new(0.1882, 0.1882, 0.1882)
	Line.BorderSizePixel = 0

	Line2.Name = "Line2"
	Line2.Position = UDim2.new(0, 0, 0.1304, 0)
	Line2.Size = UDim2.new(0, 752, 0, 1)
	Line2.BackgroundColor3 = Color3.new(0.1843, 0.1843, 0.1843)
	Line2.BorderSizePixel = 0

	Line3.Name = "Line3"
	Line3.Position = UDim2.new(0.254, 0, 0.1304, 0)
	Line3.Size = UDim2.new(0, 1, 0, 306)
	Line3.BackgroundColor3 = Color3.new(0.1843, 0.1843, 0.1843)
	Line3.BorderSizePixel = 0

	UiTitle.Name = "UiTitle"
	UiTitle.Position = UDim2.new(0.0811, 0, 0.0314, 0)
	UiTitle.Size = UDim2.new(0, 75, 0, 32)
	UiTitle.BackgroundColor3 = Color3.new(1, 1, 1)
	UiTitle.BackgroundTransparency = 1
	UiTitle.Text = Title
	UiTitle.TextColor3 = Color3.new(0.8196, 0.8196, 0.8196)
	UiTitle.Font = Enum.Font.SourceSans
	UiTitle.TextSize = 25

	Logo.Name = "Logo"
	Logo.Position = UDim2.new(0, 0, 0.0097, 0)
	Logo.Size = UDim2.new(0, 50, 0, 50)
	Logo.BackgroundColor3 = Color3.new(1, 1, 1)
	Logo.BackgroundTransparency = 1
	Logo.Image = "rbxassetid://85204852226269"

	TabHolder.Name = "TabHolder"
	TabHolder.Position = UDim2.new(0, 0, 0.1329, 0)
	TabHolder.Size = UDim2.new(0, 192, 0, 305)
	TabHolder.BackgroundColor3 = Color3.new(1, 1, 1)
	TabHolder.BackgroundTransparency = 1

	UIListLayout.SortOrder = Enum.SortOrder.LayoutOrder
	UIListLayout.Padding = UDim.new(0, 6)

	UIPadding.PaddingTop = UDim.new(0, 5)
	UIPadding.PaddingLeft = UDim.new(0, 10)

	Welcome.Name = "Welcome"
	Welcome.Position = UDim2.new(0.367, 0, 0.9106, 0)
	Welcome.Size = UDim2.new(0, 200, 0, 26)
	Welcome.BackgroundColor3 = Color3.new(1, 1, 1)
	Welcome.BackgroundTransparency = 1
	Welcome.Text = "Welcome, " .. LocalPlayer.Name
	Welcome.TextColor3 = Color3.new(0.7725, 0.7725, 0.7725)
	Welcome.Font = Enum.Font.SourceSans
	Welcome.TextSize = 17

	SettingsIcon.Name = "SettingsIcon"
	SettingsIcon.Position = UDim2.new(0.9455, 0, 0.0386, 0)
	SettingsIcon.Size = UDim2.new(0, 25, 0, 25)
	SettingsIcon.BackgroundColor3 = Color3.new(1, 1, 1)
	SettingsIcon.BackgroundTransparency = 1
	SettingsIcon.Image = "rbxassetid://127186588364408"

	CreateDrag(MainFrame)

	function window:newTab(Title: string)
		local tab = {
			Enabled = false
		}

		local ActiveTab = Instance.new('TextButton', TabHolder)
		local ActiveTabPadding = Instance.new('UIPadding', ActiveTab)
		local ActiveTabGradient = Instance.new('UIGradient', ActiveTab)
		local ActiveTabCorner = Instance.new('UICorner', ActiveTab)


		local CanvasHolder = Instance.new('Frame', MainFrame)
		local Canvas = Instance.new('ScrollingFrame', CanvasHolder)
		local UIListLayout = Instance.new('UIListLayout', Canvas)
		local UIPadding = Instance.new('UIPadding', Canvas)	
		
		

		ActiveTab.AutoButtonColor = false
		ActiveTab.Name = "ActiveTab"
		ActiveTab.Size = UDim2.new(0, 160, 0, 27)
		ActiveTab.BorderSizePixel = 0
		ActiveTab.Text = Title
		ActiveTab.TextColor3 = Color3.fromRGB(175, 175, 175)
		ActiveTab.Font = Enum.Font.SourceSans
		ActiveTab.TextSize = 16
		ActiveTab.TextXAlignment = Enum.TextXAlignment.Left
		ActiveTab.BackgroundTransparency = 1
		ActiveTab.BackgroundColor3 = Regular

		ActiveTabPadding.PaddingLeft = UDim.new(0, 8)

		ActiveTabGradient.Color = ColorSequence.new({
			ColorSequenceKeypoint.new(0, Color3.fromRGB(255, 255, 255)),
            ColorSequenceKeypoint.new(1, Color3.fromRGB(Regular))
		})
		ActiveTabGradient.Enabled = false

		ActiveTabCorner.CornerRadius = UDim.new(0, 5)



		CanvasHolder.Name = "CanvasHolder"
		CanvasHolder.Position = UDim2.new(0.2553,0,0.1304,0)
		CanvasHolder.Size = UDim2.new(0,560,0,500)
		CanvasHolder.BackgroundColor3 = Color3.new(0.9529,0.3137,1)
		CanvasHolder.BackgroundTransparency = 1
		CanvasHolder.BorderSizePixel = 0
		CanvasHolder.BorderColor3 = Color3.new(0,0,0)
		Canvas.Name = "Canvas"
		Canvas.Size = UDim2.new(0,560,0,306)
		Canvas.BackgroundColor3 = Color3.new(1,1,1)
		Canvas.BackgroundTransparency = 1
		Canvas.BorderSizePixel = 0
		Canvas.BorderColor3 = Color3.new(0,0,0)
		Canvas.ScrollBarThickness = 0
		Canvas.ScrollBarImageColor3 = Color3.new(0,0,0)
		Canvas.Visible = false
		Canvas.ClipsDescendants = true
		UIListLayout.SortOrder = Enum.SortOrder.LayoutOrder
		UIListLayout.Padding = UDim.new(0,5)
		UIPadding.PaddingTop = UDim.new(0,10)
		UIPadding.PaddingLeft = UDim.new(0,15)

		function tab:Enable()
			if not tab.Enabled then
				if window.CurrentTab then
					window.CurrentTab:Disable()
				end
				tab.Enabled = true
				ActiveTabGradient.Enabled = true
				ActiveTab.BackgroundTransparency = 0
				ActiveTab.TextColor3 = Color3.fromRGB(0, 0, 0)
				Canvas.Visible = true
				window.CurrentTab = tab

				for _, v in pairs(MainFrame:GetChildren()) do
					if v.Name == "DropDownOptions" then
						v.Visible = false
					end
				end
			end
		end

		function tab:Disable()
			if tab.Enabled then
				tab.Enabled = false
				ActiveTabGradient.Enabled = false
				ActiveTab.BackgroundTransparency = 1
				ActiveTab.TextColor3 = Color3.fromRGB(175, 175, 175)
				Canvas.Visible = false
			end
		end

		ActiveTab.MouseButton1Down:Connect(function()
			tab:Enable()
		end)

		if not window.CurrentTab then
			tab:Enable()
		end
		function tab:Dropdown(Title: string, Options: table)
			local Settings = {
				Default = Options.Default or "Select",
				Items = Options.Items or {},
				Callback = Options.Callback or function() end,
				Parent = Options.Parent or Canvas
			}
		
			local DropdownActive = Instance.new('Frame', Settings.Parent)
			local DropdownCorner = Instance.new('UICorner', DropdownActive)
			local DropdownButton = Instance.new('TextButton', DropdownActive)
			local DropdownTitle = Instance.new('TextLabel', DropdownActive)
			local DropdownList = Instance.new('Frame', Settings.Parent) 
		
			DropdownActive.Name = "DropdownActive"
			DropdownActive.Size = UDim2.new(0, 524, 0, 33)
			DropdownActive.BackgroundColor3 = Color3.new(0.0353, 0.0353, 0.0353)
			DropdownActive.BorderSizePixel = 0
			DropdownActive.BorderColor3 = Color3.new(0, 0, 0)
			DropdownActive.ZIndex = 100  
		
			DropdownCorner.CornerRadius = UDim.new(0, 6)
		
			DropdownButton.Name = "DropdownButton"
			DropdownButton.Size = UDim2.new(0, 524, 0, 33)
			DropdownButton.BackgroundColor3 = Color3.new(0.0353, 0.0353, 0.0353)
			DropdownButton.BorderSizePixel = 0
			DropdownButton.BorderColor3 = Color3.new(0, 0, 0)
			DropdownButton.Text = "" 
			DropdownButton.AutoButtonColor = false
			DropdownButton.ZIndex = 100
		
			DropdownTitle.Name = "DropdownTitle"
			DropdownTitle.Position = UDim2.new(0.5, -43, 0.5, -8.5) 
			DropdownTitle.Size = UDim2.new(0, 86, 0, 17)
			DropdownTitle.BackgroundColor3 = Color3.new(1, 1, 1)
			DropdownTitle.BackgroundTransparency = 1
			DropdownTitle.Text = Title
			DropdownTitle.TextColor3 = Color3.new(0.6353, 0.6353, 0.6353)
			DropdownTitle.Font = Enum.Font.SourceSans
			DropdownTitle.TextSize = 15
			DropdownTitle.TextXAlignment = Enum.TextXAlignment.Center
			DropdownTitle.ZIndex = 102  
		
			DropdownList.Name = "DropdownList"
			DropdownList.BackgroundColor3 = Color3.new(0.0353, 0.0353, 0.0353)
			DropdownList.BorderSizePixel = 0
			DropdownList.Size = UDim2.new(0.96, 0, 0, 0)
			DropdownList.Position = UDim2.new(0.5, -43, 1, 5)  -- Adjust position to be below DropdownActive
			DropdownList.Visible = false
			DropdownList.ClipsDescendants = false 
			DropdownList.ZIndex = 99 
		
			local function createOption(item, index)
				local OptionButton = Instance.new('TextButton', DropdownList)
				OptionButton.Name = "OptionButton"
				OptionButton.Size = UDim2.new(1, 0, 0, 24)  
				OptionButton.Position = UDim2.new(0, 0, 0, 24 * (index - 1)) 
				OptionButton.BackgroundColor3 = Color3.new(0.0353, 0.0353, 0.0353)
				OptionButton.BorderSizePixel = 0
				OptionButton.Text = item
				OptionButton.TextColor3 = Color3.new(0.6353, 0.6353, 0.6353)
				OptionButton.Font = Enum.Font.SourceSans
				OptionButton.TextSize = 15
				OptionButton.TextXAlignment = Enum.TextXAlignment.Center  
				OptionButton.ZIndex = 101  
		
				local OptionCorner = Instance.new('UICorner', OptionButton)
				OptionCorner.CornerRadius = UDim.new(0, 4)
		
				OptionButton.MouseEnter:Connect(function()
					OptionButton.BackgroundColor3 = Regular
				end)
		
				OptionButton.MouseLeave:Connect(function()
					OptionButton.BackgroundColor3 = Color3.new(0.0353, 0.0353, 0.0353)
				end)
		
				OptionButton.MouseButton1Click:Connect(function()
					DropdownTitle.Text = item  
					DropdownButton.Text = ""  
					DropdownList.Visible = false
					Settings.Callback(item)
				end)
			end
		
			for i, item in ipairs(Settings.Items) do
				createOption(item, i)
			end
		
			local DropdownOpen = false
			DropdownButton.MouseButton1Click:Connect(function()
				DropdownOpen = not DropdownOpen
				DropdownList.Visible = DropdownOpen
				if DropdownOpen then
					DropdownList.Size = UDim2.new(0.96, 0, 0, 24 * #Settings.Items)
				else
					DropdownList.Size = UDim2.new(0.96, 0, 0, 0)
				end
			end)
		
			-- Update DropdownList position on DropdownActive move
			DropdownActive:GetPropertyChangedSignal("Position"):Connect(function()
				DropdownList.Position = UDim2.new(0.5, -43, 1, 5)  -- Adjust accordingly
			end)
		
			return {
				DropdownButton = DropdownButton,
				DropdownList = DropdownList,
				SetValue = function(option)
					DropdownTitle.Text = option  
					DropdownButton.Text = ""  
					Settings.Callback(option)
				end
			}
		end
		
		
		

		function tab:NewToggle(Title: string, Options: table)
			local Settings = {
				Enabled = Options.Default or false,
				Parent = Options.Parent or Canvas,
				Callback = Options.Callback or function() end
			}

			local ToggleActive = Instance.new('ImageButton', Settings.Parent)
			local ToggleCorner = Instance.new('UICorner', ToggleActive)
			local Checkmark = Instance.new('Frame', ToggleActive)
			local CheckmarkStroke = Instance.new('UIStroke', Checkmark)
			local CheckmarkCorner = Instance.new('UICorner', Checkmark)
			local ToggleTitle = Instance.new('TextLabel', ToggleActive)

			ToggleActive.AutoButtonColor = false
			ToggleActive.Name = "ToggleActive"
			ToggleActive.Size = UDim2.new(0, 524, 0, 33)
			ToggleActive.BackgroundColor3 = Color3.new(0.0353, 0.0353, 0.0353)
			ToggleActive.BorderSizePixel = 0
			ToggleActive.BorderColor3 = Color3.new(0, 0, 0)

			ToggleCorner.CornerRadius = UDim.new(0, 6)

			Checkmark.Name = "Checkmark"
			Checkmark.Position = UDim2.new(0.0344, 0, 0.1818, 0)
			Checkmark.Size = UDim2.new(0, 20, 0, 20)
			Checkmark.BackgroundColor3 = Color3.new(0, 0, 0)
			Checkmark.BorderSizePixel = 0
			Checkmark.BorderColor3 = Color3.new(0, 0, 0)

			CheckmarkCorner.CornerRadius = UDim.new(0, 4)

			ToggleTitle.Name = "ToggleTitle"
			ToggleTitle.Position = UDim2.new(0.1069, 0, 0.2424, 0)
			ToggleTitle.Size = UDim2.new(0, 86, 0, 17)
			ToggleTitle.BackgroundColor3 = Color3.new(1, 1, 1)
			ToggleTitle.BackgroundTransparency = 1
			ToggleTitle.Text = Title
			ToggleTitle.TextColor3 = Color3.new(0.6353, 0.6353, 0.6353)
			ToggleTitle.Font = Enum.Font.SourceSans
			ToggleTitle.TextSize = 15
			ToggleTitle.TextXAlignment = Enum.TextXAlignment.Left

			local function Toggle(Value)
				if Value then
					TS:Create(Checkmark, TweenInfo.new(.2, Enum.EasingStyle.Quad), { BackgroundColor3 = Regular }):Play()
				else
					TS:Create(Checkmark, TweenInfo.new(.2, Enum.EasingStyle.Quad), { BackgroundColor3 = Color3.fromRGB(0, 0, 0) }):Play()
				end
				Settings.Enabled = Value
				Settings.Callback(Settings.Enabled)
			end

			Toggle(Settings.Enabled)

			ToggleActive.MouseButton1Down:Connect(function()
				Toggle(not Settings.Enabled)
			end)

			return Settings
		end
		
		
		
		
		LPH_NO_VIRTUALIZE(function()
		function tab:NewSlider(Title: string, Options: table)

			local Settings = {
				Connections = {},
				Value 		= Options.Default or 0,
				MinVal 		= Options.Min or 0,
				MaxVal 		= Options.Max or 100,
				Parent		= Options.Parent or Canvas,
				Callback 	= Options.Callback or function() end
			}
			

			local Slider = Instance.new('ImageButton', Canvas)
			local SliderCorner = Instance.new('UICorner', Slider)
			local SliderTitle = Instance.new('TextLabel', Slider)

			local Value = Instance.new('TextLabel', Slider)
			local SliderBack = Instance.new('Frame', Slider)
			local SliderBackCorner = Instance.new('UICorner', SliderBack)
			local SliderMain = Instance.new('Frame', SliderBack)
			local SliderMainCorner = Instance.new('UICorner', SliderMain)
			local SliderBackStroke = Instance.new('UIStroke', SliderBack)
			
			Slider.AutoButtonColor = false
			Slider.Name = "Slider"
			Slider.Size = UDim2.new(0,524,0,33)
			Slider.BackgroundColor3 = Color3.new(0.0353,0.0353,0.0353)
			Slider.BorderSizePixel = 0
			Slider.BorderColor3 = Color3.new(0,0,0)
			SliderCorner.CornerRadius = UDim.new(0,6)
			SliderTitle.Name = "SliderTitle"
			SliderTitle.Position = UDim2.new(0.1069,0,0.2424,0)
			SliderTitle.Size = UDim2.new(0,86,0,17)
			SliderTitle.BackgroundColor3 = Color3.new(1,1,1)
			SliderTitle.BackgroundTransparency = 1
			SliderTitle.BorderSizePixel = 0
			SliderTitle.BorderColor3 = Color3.new(0,0,0)
			SliderTitle.Text = Title
			SliderTitle.TextColor3 = Color3.new(0.6353,0.6353,0.6353)
			SliderTitle.Font = Enum.Font.SourceSans
			SliderTitle.TextSize = 14
			SliderTitle.TextXAlignment = Enum.TextXAlignment.Left

			Value.Name = "Value"
			Value.Position = UDim2.new(0.0134,0,0.2424,0)
			Value.Size = UDim2.new(0,41,0,17)
			Value.BackgroundColor3 = Color3.new(1,1,1)
			Value.BackgroundTransparency = 1
			Value.BorderSizePixel = 0
			Value.BorderColor3 = Color3.new(0,0,0)
			Value.Text = string.format(Options.Default or 0, Settings.MaxVal)
			Value.TextColor3 = Color3.new(0.5608,0.5608,0.5608)
			Value.Font = Enum.Font.SourceSans
			Value.TextSize = 14
			SliderBack.Name = "SliderBack"
			SliderBack.Position = UDim2.new(0.340,0,0.3636,0)
			SliderBack.Size = UDim2.new(0,342,0,9)
			SliderBack.BackgroundColor3 = Color3.new(0,0,0)
			SliderBack.BorderSizePixel = 0
			SliderBack.BorderColor3 = Color3.new(0,0,0)
			SliderBackCorner.CornerRadius = UDim.new(0,6)
			SliderMain.Name = "SliderMain"
			SliderMain.Size = UDim2.new(0,0,0,9)
			SliderMain.BackgroundColor3 = Regular
			SliderMain.BorderSizePixel = 0
			SliderMain.BorderColor3 = Color3.new(0,0,0)
			SliderMainCorner.CornerRadius = UDim.new(0,6)
			
			
			--canvas
			
			local function GetValue()
				return tonumber(Settings.Value)
			end

			function Settings:SetValue(v)
				local function roundToTwoDecimalPlaces(num)
					return math.floor(num * 100 + 0.5) / 100
				end
			
				if v == nil then
					local mouseX = UIS:GetMouseLocation().X
					local percentage = math.clamp((mouseX - SliderBack.AbsolutePosition.X) / (SliderBack.AbsoluteSize.X), 0, 1)
					local value = roundToTwoDecimalPlaces((((Settings.MaxVal - Settings.MinVal) * percentage) + Settings.MinVal))
					Value.Text = string.format("%.2f", value)
					SliderMain.Size = UDim2.fromScale(percentage, 1)
					Settings.Value = value
					Settings.Callback(value)
				else
					local value = roundToTwoDecimalPlaces(v)
					Value.Text = string.format("%.2f", value)
					SliderMain.Size = UDim2.fromScale(((value - Settings.MinVal) / (Settings.MaxVal - Settings.MinVal)), 1)
					Settings.Value = value
					Settings.Callback(value)
				end
			end
			

			local Connection;

			table.insert(Settings.Connections, UIS.InputEnded:Connect(function(input)
				if input.UserInputType == Enum.UserInputType.MouseButton1 or input.UserInputType == Enum.UserInputType.Touch then
					pcall(function()
						if Connection then
							Connection:Disconnect();
							Connection = nil;
						end
					end)
				end
			end))

			table.insert(Settings.Connections, Slider.MouseButton1Down:Connect(function()
				if(Connection) then
					Connection:Disconnect();
				end;

				Connection = RS.Heartbeat:Connect(function()
					Settings:SetValue()
				end)
			end))
			

			return Settings
		end
	end)()
		
		LPH_NO_VIRTUALIZE(function()
		function tab:NewSection(SectionTitle: string, Options: table)
			local Settings = {}

			local Section = Instance.new('Frame', Canvas)
			local STitle = Instance.new('TextLabel', Section)
			local UIPadding = Instance.new('UIPadding', Section)


			Section.Name = "Section"
			Section.Position = UDim2.new(0,0,0.2568,0)
			Section.Size = UDim2.new(0,524,0,12)
			Section.BackgroundColor3 = Color3.new(0.0353,0.0353,0.0353)
			Section.BackgroundTransparency = 1
			Section.BorderSizePixel = 0
			Section.BorderColor3 = Color3.new(0,0,0)
			STitle.Name = "SectionTitle"
			STitle.Position = UDim2.new(0.0344,0,-0.2576,0)
			STitle.Size = UDim2.new(0,86,0,17)
			STitle.BackgroundColor3 = Color3.new(1,1,1)
			STitle.BackgroundTransparency = 1
			STitle.BorderSizePixel = 0
			STitle.BorderColor3 = Color3.new(0,0,0)
			STitle.Text = SectionTitle
			STitle.TextColor3 = Color3.new(0.5137,0.5137,0.5137)
			STitle.Font = Enum.Font.SourceSans
			STitle.TextSize = 12
			STitle.TextXAlignment = Enum.TextXAlignment.Left
			UIPadding.PaddingRight = UDim.new(0,300)

		

			return Settings
		end
	end)()
		return tab
	end

	return window
end
```
## Create Title
```lua
local LightingUI = LightingLib:newWindow("Lightning.cc")
```
## Create Tab
```lua
local CatchingTab = LightingUI:newTab("Catching")
```
## Create Section
```lua
CatchingTab:NewSection("Velocity Powerered Magnets")
```
## Create Toggle
```lua
CatchingTab:NewToggle("Teleportation Magnets", {
    Default = false,
    Callback = function(size)
        
    end
})
```
## Create Slider
```lua
CatchingTab:NewSlider("Tween Duration Delay", {
    Default = 0,
    Max = 1,
    Min = 0,
    Callback = function(value)

   end
})
```
## Create Dropdown
```lua
CatchingTab:Dropdown("Magnets Mode:", {
    Items = {"Regular", "Blatant", "Legit", "League"},
    Default = "",
    Callback = function(selectedItem)

    end
})
```
