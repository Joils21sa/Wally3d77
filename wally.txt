-- Decompiler will be improved soon!
-- Decompiled with Konstant V2.1, a fast Luau decompiler made in Luau by plusgiant5 (https://discord.gg/wyButjTMhM)
-- Decompiled on 2025-02-19 09:13:35
-- Luau version 6, Types version 3
-- Time taken: 0.038978 seconds

local module_2 = {}
local function new(arg1) -- Line 1
	local tbl_19_upvr = {}
	local UserInputService_upvr = game:GetService("UserInputService")
	local var4 = arg1
	if not var4 then
		var4 = {}
	end
	local var5_upvw = var4
	var4 = var5_upvw.ToggleKeybind
	local var6 = var4
	if not var6 then
		var6 = Enum.KeyCode.RightShift
	end
	var5_upvw.ToggleKeybind = var6
	local module_3_upvr = {
		count = 0;
		queue = {};
		callbacks = {};
		rainbowtable = {};
		toggled = true;
		binds = {};
	}
	local tbl_22_upvr = {}
	local mouse_upvr = game:GetService("Players").LocalPlayer:GetMouse()
	local Heartbeat_upvr = game:GetService("RunService").Heartbeat
	function tbl_22_upvr.new(arg1_2) -- Line 15
		--[[ Upvalues[4]:
			[1]: tbl_19_upvr (readonly)
			[2]: mouse_upvr (readonly)
			[3]: Heartbeat_upvr (readonly)
			[4]: UserInputService_upvr (readonly)
		]]
		local pcall_result1, pcall_result2 = pcall(function() -- Line 16
			--[[ Upvalues[1]:
				[1]: arg1_2 (readonly)
			]]
			return arg1_2.MouseEnter
		end)
		if pcall_result1 then
			arg1_2.Active = true
			table.insert(tbl_19_upvr, pcall_result2:connect(function() -- Line 23
				--[[ Upvalues[4]:
					[1]: arg1_2 (readonly)
					[2]: mouse_upvr (copied, readonly)
					[3]: Heartbeat_upvr (copied, readonly)
					[4]: UserInputService_upvr (copied, readonly)
				]]
				local any_connect_result1_upvr = arg1_2.InputBegan:connect(function(arg1_3) -- Line 24
					--[[ Upvalues[4]:
						[1]: mouse_upvr (copied, readonly)
						[2]: arg1_2 (copied, readonly)
						[3]: Heartbeat_upvr (copied, readonly)
						[4]: UserInputService_upvr (copied, readonly)
					]]
					if arg1_3.UserInputType == Enum.UserInputType.MouseButton1 then
						while Heartbeat_upvr:wait() and UserInputService_upvr:IsMouseButtonPressed(Enum.UserInputType.MouseButton1) do
							local vector2_5_upvr = Vector2.new(mouse_upvr.X - arg1_2.AbsolutePosition.X, mouse_upvr.Y - arg1_2.AbsolutePosition.Y)
							pcall(function() -- Line 28
								--[[ Upvalues[3]:
									[1]: arg1_2 (copied, readonly)
									[2]: mouse_upvr (copied, readonly)
									[3]: vector2_5_upvr (readonly)
								]]
								arg1_2:TweenPosition(UDim2.new(0, mouse_upvr.X - vector2_5_upvr.X + arg1_2.Size.X.Offset * arg1_2.AnchorPoint.X, 0, mouse_upvr.Y - vector2_5_upvr.Y + arg1_2.Size.Y.Offset * arg1_2.AnchorPoint.Y), "Out", "Linear", 0.1, true)
							end)
						end
					end
				end)
				local var20_upvw
				var20_upvw = arg1_2.MouseLeave:connect(function() -- Line 36
					--[[ Upvalues[2]:
						[1]: any_connect_result1_upvr (readonly)
						[2]: var20_upvw (read and write)
					]]
					any_connect_result1_upvr:disconnect()
					var20_upvw:disconnect()
				end)
			end))
		end
	end
	table.insert(tbl_19_upvr, UserInputService_upvr.InputBegan:connect(function(arg1_4, arg2) -- Line 44
		--[[ Upvalues[2]:
			[1]: var5_upvw (read and write)
			[2]: module_3_upvr (readonly)
		]]
		if not arg2 and arg1_4.KeyCode == var5_upvw.ToggleKeybind then
			module_3_upvr.toggled = not module_3_upvr.toggled
			module_3_upvr.container.Parent.Enabled = module_3_upvr.toggled
		end
	end))
	mouse_upvr = {}
	local var22_upvr = mouse_upvr
	var22_upvr.__index = var22_upvr
	function Heartbeat_upvr(arg1_5, arg2) -- Line 62, Named "window"
		--[[ Upvalues[3]:
			[1]: module_3_upvr (readonly)
			[2]: var22_upvr (readonly)
			[3]: tbl_19_upvr (readonly)
		]]
		module_3_upvr.count += 1
		local tbl_5 = {}
		tbl_5.Name = arg1_5
		tbl_5.Size = UDim2.new(0, 190, 0, 30)
		tbl_5.BackgroundColor3 = arg2.topcolor
		tbl_5.BorderSizePixel = 0
		tbl_5.Parent = module_3_upvr.container
		tbl_5.Position = UDim2.new(0, 15 + 200 * module_3_upvr.count - 200, 0, 0)
		tbl_5.ZIndex = 999999996
		local tbl_9 = {}
		tbl_9.Text = arg1_5
		tbl_9.Size = UDim2.new(1, -10, 1, 0)
		tbl_9.Position = UDim2.new(0, 5, 0, 0)
		tbl_9.BackgroundTransparency = 1
		tbl_9.Font = Enum.Font.Code
		tbl_9.TextSize = arg2.titlesize
		tbl_9.Font = arg2.titlefont
		tbl_9.TextColor3 = arg2.titletextcolor
		tbl_9.TextStrokeTransparency = module_3_upvr.options.titlestroke
		tbl_9.TextStrokeColor3 = module_3_upvr.options.titlestrokecolor
		tbl_9.ZIndex = 999999996
		local tbl_6 = {
			Name = "Underline";
			Size = UDim2.new(1, 0, 0, 2);
			Position = UDim2.new(0, 0, 1, -2);
		}
		local var27
		local function INLINED() -- Internal function, doesn't exist in bytecode
			var27 = arg2.underlinecolor
			return var27
		end
		if arg2.underlinecolor == "rainbow" or not INLINED() then
			var27 = Color3.new()
		end
		tbl_6.BackgroundColor3 = var27
		var27 = 0
		tbl_6.BorderSizePixel = var27
		var27 = 999999996
		tbl_6.ZIndex = var27
		var27 = {}
		var27.Name = "container"
		var27.Position = UDim2.new(0, 0, 1, 0)
		var27.Size = UDim2.new(1, 0, 0, 0)
		var27.BorderSizePixel = 0
		var27.BackgroundColor3 = arg2.bgcolor
		var27.ClipsDescendants = false
		var27[1] = module_3_upvr:Create("UIListLayout", {
			Name = "List";
			SortOrder = Enum.SortOrder.LayoutOrder;
		})
		tbl_5[1] = module_3_upvr:Create("TextLabel", tbl_9)
		tbl_5[2] = module_3_upvr:Create("TextButton", {
			Size = UDim2.new(0, 30, 0, 30);
			Position = UDim2.new(1, -35, 0, 0);
			BackgroundTransparency = 1;
			Text = '-';
			TextSize = arg2.titlesize;
			Font = arg2.titlefont;
			Name = "window_toggle";
			TextColor3 = arg2.titletextcolor;
			TextStrokeTransparency = module_3_upvr.options.titlestroke;
			TextStrokeColor3 = module_3_upvr.options.titlestrokecolor;
			ZIndex = 999999996;
		})
		tbl_5[3] = module_3_upvr:Create("Frame", tbl_6)
		tbl_5[4] = module_3_upvr:Create("Frame", var27)
		local any_Create_result1_upvr_9 = module_3_upvr:Create("Frame", tbl_5)
		if arg2.underlinecolor == "rainbow" then
			table.insert(module_3_upvr.rainbowtable, any_Create_result1_upvr_9:FindFirstChild("Underline"))
		end
		local setmetatable_result1_upvr = setmetatable({
			count = 0;
			object = any_Create_result1_upvr_9;
			container = any_Create_result1_upvr_9.container;
			toggled = true;
			flags = {};
		}, var22_upvr)
		table.insert(module_3_upvr.queue, {
			w = setmetatable_result1_upvr.object;
			p = setmetatable_result1_upvr.object.Position;
		})
		table.insert(tbl_19_upvr, any_Create_result1_upvr_9:FindFirstChild("window_toggle").MouseButton1Click:connect(function() -- Line 138
			--[[ Upvalues[2]:
				[1]: setmetatable_result1_upvr (readonly)
				[2]: any_Create_result1_upvr_9 (readonly)
			]]
			-- KONSTANTWARNING: Variable analysis failed. Output will have some incorrect variable assignments
			setmetatable_result1_upvr.toggled = not setmetatable_result1_upvr.toggled
			local var42
			if setmetatable_result1_upvr.toggled then
				var42 = '+'
			else
				var42 = '-'
			end
			any_Create_result1_upvr_9:FindFirstChild("window_toggle").Text = var42
			var42 = setmetatable_result1_upvr
			if not var42.toggled then
				var42 = setmetatable_result1_upvr
				var42 = true
				var42.container.ClipsDescendants = var42
			end
			wait()
			var42 = next
			for _, v in var42, setmetatable_result1_upvr.container:GetChildren() do
				if not v:IsA("UIListLayout") then
				end
			end
			local function INLINED_2() -- Internal function, doesn't exist in bytecode
				var42 = UDim2.new(1, 0, 0, 0 + v.AbsoluteSize.Y + 5)
				return var42
			end
			if not setmetatable_result1_upvr.toggled or not INLINED_2() then
				var42 = UDim2.new(1, 0, 0, 0)
			end
			if setmetatable_result1_upvr.toggled then
			else
			end
			setmetatable_result1_upvr.container:TweenSize(var42, "Out", "Quad", 0.15, true)
			wait(0.15)
			if setmetatable_result1_upvr.toggled then
				setmetatable_result1_upvr.container.ClipsDescendants = false
			end
		end))
		return setmetatable_result1_upvr
	end
	var22_upvr.window = Heartbeat_upvr
	function Heartbeat_upvr(arg1_6) -- Line 165, Named "Resize"
		local var51
		for _, v_2 in next, arg1_6.container:GetChildren() do
			if not v_2:IsA("UIListLayout") then
				var51 += v_2.AbsoluteSize.Y
			end
		end
		arg1_6.container.Size = UDim2.new(1, 0, 0, var51 + 5)
	end
	var22_upvr.Resize = Heartbeat_upvr
	function Heartbeat_upvr(arg1_7) -- Line 175, Named "GetOrder"
		local var58
		for _, v_3 in next, arg1_7.container:GetChildren() do
			if not v_3:IsA("UIListLayout") then
				var58 += 1
			end
		end
		return var58
	end
	var22_upvr.GetOrder = Heartbeat_upvr
	function Heartbeat_upvr(arg1_8, arg2) -- Line 185, Named "Label"
		--[[ Upvalues[1]:
			[1]: module_3_upvr (readonly)
		]]
		local tbl_2 = {
			Size = UDim2.new(1, 0, 0, game:GetService("TextService"):GetTextSize(arg2, 18, Enum.Font.SourceSans, Vector2.new(math.huge, math.huge)).Y + 5);
			BackgroundTransparency = 1;
		}
		local tbl_11 = {
			Size = UDim2.new(1, 0, 1, 0);
			Position = UDim2.new(0, 10, 0, 0);
			LayoutOrder = arg1_8:GetOrder();
		}
		tbl_11.Text = arg2
		tbl_11.TextSize = 18
		tbl_11.Font = Enum.Font.SourceSans
		tbl_11.TextColor3 = Color3.fromRGB(255, 255, 255)
		tbl_11.BackgroundTransparency = 1
		tbl_11.TextXAlignment = Enum.TextXAlignment.Left
		tbl_11.TextWrapped = true
		tbl_2[1] = module_3_upvr:Create("TextLabel", tbl_11)
		tbl_2.Parent = arg1_8.container
		arg1_8:Resize()
	end
	var22_upvr.Label = Heartbeat_upvr
	function Heartbeat_upvr(arg1_9, arg2, arg3, arg4) -- Line 208, Named "Toggle"
		--[[ Upvalues[2]:
			[1]: module_3_upvr (readonly)
			[2]: tbl_19_upvr (readonly)
		]]
		-- KONSTANTWARNING: Variable analysis failed. Output will have some incorrect variable assignments
		local location_upvr = arg3.location
		if not location_upvr then
			location_upvr = arg1_9.flags
		end
		local var62_upvr = arg3.flag or ""
		local var64_upvr = arg4
		if not var64_upvr then
			function var64_upvr() -- Line 212
			end
		end
		location_upvr[var62_upvr] = arg3.default or false
		local tbl_12 = {
			BackgroundTransparency = 1;
			Size = UDim2.new(1, 0, 0, 25);
			LayoutOrder = arg1_9:GetOrder();
		}
		local tbl_24 = {}
		tbl_24.Name = arg2
		tbl_24.Text = '\r'..arg2
		tbl_24.BackgroundTransparency = 1
		tbl_24.TextColor3 = module_3_upvr.options.textcolor
		tbl_24.Position = UDim2.new(0, 5, 0, 0)
		tbl_24.Size = UDim2.new(1, -5, 1, 0)
		tbl_24.TextXAlignment = Enum.TextXAlignment.Left
		tbl_24.Font = module_3_upvr.options.font
		tbl_24.TextSize = module_3_upvr.options.fontsize
		tbl_24.TextStrokeTransparency = module_3_upvr.options.textstroke
		tbl_24.TextStrokeColor3 = module_3_upvr.options.strokecolor
		local tbl_15 = {}
		if not location_upvr[var62_upvr] or not utf8.char(10003) then
		end
		tbl_15.Text = ""
		tbl_15.Font = module_3_upvr.options.font
		tbl_15.TextSize = module_3_upvr.options.fontsize
		tbl_15.Name = "Checkmark"
		tbl_15.Size = UDim2.new(0, 20, 0, 20)
		tbl_15.Position = UDim2.new(1, -25, 0, 4)
		tbl_15.TextColor3 = module_3_upvr.options.textcolor
		tbl_15.BackgroundColor3 = module_3_upvr.options.bgcolor
		tbl_15.BorderColor3 = module_3_upvr.options.bordercolor
		tbl_15.TextStrokeTransparency = module_3_upvr.options.textstroke
		tbl_15.TextStrokeColor3 = module_3_upvr.options.strokecolor
		tbl_24[1] = module_3_upvr:Create("TextButton", tbl_15)
		tbl_12[1] = module_3_upvr:Create("TextLabel", tbl_24)
		tbl_12.Parent = arg1_9.container
		local any_Create_result1_upvr_10 = module_3_upvr:Create("Frame", tbl_12)
		local function click(arg1_10) -- Line 249
			--[[ Upvalues[5]:
				[1]: location_upvr (readonly)
				[2]: var62_upvr (readonly)
				[3]: var64_upvr (readonly)
				[4]: any_Create_result1_upvr_10 (readonly)
				[5]: arg2 (readonly)
			]]
			location_upvr[var62_upvr] = not location_upvr[var62_upvr]
			var64_upvr(location_upvr[var62_upvr])
			local var69
			local function INLINED_3() -- Internal function, doesn't exist in bytecode
				var69 = utf8.char(10003)
				return var69
			end
			if not location_upvr[var62_upvr] or not INLINED_3() then
				var69 = ""
			end
			any_Create_result1_upvr_10:FindFirstChild(arg2).Checkmark.Text = var69
		end
		table.insert(tbl_19_upvr, any_Create_result1_upvr_10:FindFirstChild(arg2).Checkmark.MouseButton1Click:connect(click))
		module_3_upvr.callbacks[var62_upvr] = click
		if location_upvr[var62_upvr] == true then
			var64_upvr(location_upvr[var62_upvr])
		end
		arg1_9:Resize()
		local module = {}
		local function Set(arg1_11, arg2_2) -- Line 264
			--[[ Upvalues[5]:
				[1]: location_upvr (readonly)
				[2]: var62_upvr (readonly)
				[3]: var64_upvr (readonly)
				[4]: any_Create_result1_upvr_10 (readonly)
				[5]: arg2 (readonly)
			]]
			location_upvr[var62_upvr] = arg2_2
			var64_upvr(location_upvr[var62_upvr])
			local var71
			local function INLINED_4() -- Internal function, doesn't exist in bytecode
				var71 = utf8.char(10003)
				return var71
			end
			if not location_upvr[var62_upvr] or not INLINED_4() then
				var71 = ""
			end
			any_Create_result1_upvr_10:FindFirstChild(arg2).Checkmark.Text = var71
		end
		module.Set = Set
		return module
	end
	var22_upvr.Toggle = Heartbeat_upvr
	function Heartbeat_upvr(arg1_12, arg2, arg3) -- Line 272, Named "Button"
		--[[ Upvalues[2]:
			[1]: module_3_upvr (readonly)
			[2]: tbl_19_upvr (readonly)
		]]
		local var73 = arg3
		if not var73 then
			function var73() -- Line 273
			end
		end
		local var74_upvw = var73
		local tbl_10 = {
			BackgroundTransparency = 1;
			Size = UDim2.new(1, 0, 0, 25);
			LayoutOrder = arg1_12:GetOrder();
		}
		local tbl_16 = {}
		tbl_16.Name = arg2
		tbl_16.Text = arg2
		tbl_16.BackgroundColor3 = module_3_upvr.options.btncolor
		tbl_16.BorderColor3 = module_3_upvr.options.bordercolor
		tbl_16.TextStrokeTransparency = module_3_upvr.options.textstroke
		tbl_16.TextStrokeColor3 = module_3_upvr.options.strokecolor
		tbl_16.TextColor3 = module_3_upvr.options.textcolor
		tbl_16.Position = UDim2.new(0, 5, 0, 5)
		tbl_16.Size = UDim2.new(1, -10, 0, 20)
		tbl_16.Font = module_3_upvr.options.font
		tbl_16.TextSize = module_3_upvr.options.fontsize
		tbl_10[1] = module_3_upvr:Create("TextButton", tbl_16)
		tbl_10.Parent = arg1_12.container
		table.insert(tbl_19_upvr, module_3_upvr:Create("Frame", tbl_10):FindFirstChild(arg2).MouseButton1Click:connect(var74_upvw))
		arg1_12:Resize()
		return {
			Fire = function() -- Line 299, Named "Fire"
				--[[ Upvalues[1]:
					[1]: var74_upvw (read and write)
				]]
				var74_upvw()
			end;
		}
	end
	var22_upvr.Button = Heartbeat_upvr
	function Heartbeat_upvr(arg1_13, arg2, arg3, arg4) -- Line 305, Named "TextBox"
		--[[ Upvalues[2]:
			[1]: module_3_upvr (readonly)
			[2]: tbl_19_upvr (readonly)
		]]
		-- KONSTANTWARNING: Variable analysis failed. Output will have some incorrect variable assignments
		local var78_upvr = arg3.type or ""
		local var79_upvr
		if not var79_upvr then
			var79_upvr = arg1_13.flags
		end
		local var80_upvr = arg3.flag or ""
		if not arg4 then
			local function var81_upvr() -- Line 310
			end
		end
		local var82
		if var78_upvr == "number" and not tonumber(var82) then
			var79_upvr[var80_upvr] = var82
		else
			var79_upvr[var80_upvr] = ""
			var82 = ""
		end
		local tbl_26 = {
			BackgroundTransparency = 1;
			Size = UDim2.new(1, 0, 0, 25);
			LayoutOrder = arg1_13:GetOrder();
		}
		local tbl_23 = {}
		tbl_23.Name = arg2
		tbl_23.Text = '\r'..arg2
		tbl_23.BackgroundTransparency = 1
		tbl_23.TextColor3 = module_3_upvr.options.textcolor
		tbl_23.TextStrokeTransparency = module_3_upvr.options.textstroke
		tbl_23.TextStrokeColor3 = module_3_upvr.options.strokecolor
		tbl_23.Position = UDim2.new(0, 5, 0, 0)
		tbl_23.Size = UDim2.new(1, -5, 1, 0)
		tbl_23.TextXAlignment = Enum.TextXAlignment.Left
		tbl_23.Font = module_3_upvr.options.font
		tbl_23.TextSize = module_3_upvr.options.fontsize
		tbl_23[1] = module_3_upvr:Create("TextBox", {
			TextStrokeTransparency = module_3_upvr.options.textstroke;
			TextStrokeColor3 = module_3_upvr.options.strokecolor;
			Text = tostring(var82);
			Font = module_3_upvr.options.font;
			TextSize = module_3_upvr.options.fontsize;
			Name = "Box";
			Size = UDim2.new(0, 60, 0, 20);
			Position = UDim2.new(1, -65, 0, 3);
			TextColor3 = module_3_upvr.options.textcolor;
			TextWrapped = true;
			ClearTextOnFocus = not arg3.copyable;
			BackgroundColor3 = module_3_upvr.options.boxcolor;
			BorderColor3 = module_3_upvr.options.bordercolor;
			PlaceholderColor3 = module_3_upvr.options.placeholdercolor;
		})
		tbl_26[1] = module_3_upvr:Create("TextLabel", tbl_23)
		tbl_26.Parent = arg1_13.container
		local Box_upvr = module_3_upvr:Create("Frame", tbl_26):FindFirstChild(arg2):FindFirstChild("Box")
		local var88_upvr = arg3.min or 0
		local var89_upvr = arg3.max or 9000000000
		table.insert(tbl_19_upvr, Box_upvr.FocusLost:connect(function(arg1_14) -- Line 358
			--[[ Upvalues[7]:
				[1]: var79_upvr (readonly)
				[2]: var80_upvr (readonly)
				[3]: var78_upvr (readonly)
				[4]: Box_upvr (readonly)
				[5]: var88_upvr (readonly)
				[6]: var89_upvr (readonly)
				[7]: var81_upvr (readonly)
			]]
			if var78_upvr == "number" then
				local tonumber_result1_5 = tonumber(Box_upvr.Text)
				if not tonumber_result1_5 then
					Box_upvr.Text = tonumber(var79_upvr[var80_upvr])
				else
					var79_upvr[var80_upvr] = math.clamp(tonumber_result1_5, var88_upvr, var89_upvr)
					Box_upvr.Text = tonumber(var79_upvr[var80_upvr])
				end
			else
				var79_upvr[var80_upvr] = tostring(Box_upvr.Text)
			end
			var81_upvr(var79_upvr[var80_upvr], var79_upvr[var80_upvr], arg1_14)
		end))
		if var78_upvr == "number" then
			Box_upvr:GetPropertyChangedSignal("Text"):connect(function() -- Line 376
				--[[ Upvalues[1]:
					[1]: Box_upvr (readonly)
				]]
				Box_upvr.Text = string.gsub(Box_upvr.Text, "[%a+]", "")
			end)
		end
		arg1_13:Resize()
		return Box_upvr
	end
	var22_upvr.TextBox = Heartbeat_upvr
	function Heartbeat_upvr(arg1_15, arg2, arg3, arg4) -- Line 385, Named "Bind"
		--[[ Upvalues[3]:
			[1]: module_3_upvr (readonly)
			[2]: tbl_19_upvr (readonly)
			[3]: UserInputService_upvr (readonly)
		]]
		local var92_upvr
		if not var92_upvr then
			var92_upvr = arg1_15.flags
		end
		local var93_upvr = arg3.kbonly or false
		local var94_upvr = arg3.flag or ""
		local var96 = arg4
		if not var96 then
			function var96() -- Line 389
			end
		end
		local default_2 = arg3.default
		local var98
		if var93_upvr and tostring(default_2):find("MouseButton") then
			var98 = false
		end
		if var98 then
			var92_upvr[var94_upvr] = default_2
		end
		local tbl_27_upvr = {
			Escape = true;
			Return = true;
			Space = true;
			Tab = true;
			Unknown = true;
		}
		local tbl_3_upvr = {
			RightControl = "RightCtrl";
			LeftControl = "LeftCtrl";
			LeftShift = "LShift";
			RightShift = "RShift";
			MouseButton1 = "Mouse1";
			MouseButton2 = "Mouse2";
		}
		local tbl_20_upvr = {
			MouseButton1 = true;
		}
		local var102 = true
		tbl_20_upvr.MouseButton2 = var102
		local function INLINED_5() -- Internal function, doesn't exist in bytecode
			var102 = tbl_3_upvr[default_2.Name]
			return var102
		end
		local function INLINED_6() -- Internal function, doesn't exist in bytecode
			var102 = default_2.Name
			return var102
		end
		if not default_2 or not INLINED_5() and not INLINED_6() then
			var102 = "None"
		end
		local tbl_14 = {
			BackgroundTransparency = 1;
			Size = UDim2.new(1, 0, 0, 30);
			LayoutOrder = arg1_15:GetOrder();
		}
		local tbl_29 = {}
		tbl_29.Name = arg2
		tbl_29.Text = '\r'..arg2
		tbl_29.BackgroundTransparency = 1
		tbl_29.TextColor3 = module_3_upvr.options.textcolor
		tbl_29.Position = UDim2.new(0, 5, 0, 0)
		tbl_29.Size = UDim2.new(1, -5, 1, 0)
		tbl_29.TextXAlignment = Enum.TextXAlignment.Left
		tbl_29.Font = module_3_upvr.options.font
		tbl_29.TextSize = module_3_upvr.options.fontsize
		tbl_29.TextStrokeTransparency = module_3_upvr.options.textstroke
		tbl_29.TextStrokeColor3 = module_3_upvr.options.strokecolor
		tbl_29.BorderColor3 = module_3_upvr.options.bordercolor
		tbl_29.BorderSizePixel = 1
		tbl_29[1] = module_3_upvr:Create("TextButton", {
			Name = "Keybind";
			Text = var102;
			TextStrokeTransparency = module_3_upvr.options.textstroke;
			TextStrokeColor3 = module_3_upvr.options.strokecolor;
			Font = module_3_upvr.options.font;
			TextSize = module_3_upvr.options.fontsize;
			Size = UDim2.new(0, 60, 0, 20);
			Position = UDim2.new(1, -65, 0, 5);
			TextColor3 = module_3_upvr.options.textcolor;
			BackgroundColor3 = module_3_upvr.options.bgcolor;
			BorderColor3 = module_3_upvr.options.bordercolor;
			BorderSizePixel = 1;
		})
		tbl_14[1] = module_3_upvr:Create("TextLabel", tbl_29)
		tbl_14.Parent = arg1_15.container
		local Keybind_upvr = module_3_upvr:Create("Frame", tbl_14):FindFirstChild(arg2).Keybind
		table.insert(tbl_19_upvr, Keybind_upvr.MouseButton1Click:connect(function() -- Line 460
			--[[ Upvalues[9]:
				[1]: module_3_upvr (copied, readonly)
				[2]: Keybind_upvr (readonly)
				[3]: UserInputService_upvr (copied, readonly)
				[4]: tbl_20_upvr (readonly)
				[5]: var93_upvr (readonly)
				[6]: tbl_27_upvr (readonly)
				[7]: var92_upvr (readonly)
				[8]: var94_upvr (readonly)
				[9]: tbl_3_upvr (readonly)
			]]
			module_3_upvr.binding = true
			Keybind_upvr.Text = "..."
			local any_wait_result1, _ = UserInputService_upvr.InputBegan:wait()
			local var110
			local function INLINED_7() -- Internal function, doesn't exist in bytecode
				var110 = tbl_20_upvr[any_wait_result1.UserInputType.Name]
				return var110
			end
			local function INLINED_8() -- Internal function, doesn't exist in bytecode
				var110 = var93_upvr
				return var110
			end
			local function INLINED_9() -- Internal function, doesn't exist in bytecode
				var110 = any_wait_result1.KeyCode
				return var110
			end
			local function INLINED_10() -- Internal function, doesn't exist in bytecode
				var110 = tbl_27_upvr[any_wait_result1.KeyCode.Name]
				return var110
			end
			if var110 ~= Enum.UserInputType.Keyboard and INLINED_7() and not INLINED_8() or INLINED_9() and not INLINED_10() then
				local function INLINED_11() -- Internal function, doesn't exist in bytecode
					var110 = any_wait_result1.UserInputType.Name
					return var110
				end
				if any_wait_result1.UserInputType == Enum.UserInputType.Keyboard or not INLINED_11() then
					var110 = any_wait_result1.KeyCode.Name
				end
				var92_upvr[var94_upvr] = any_wait_result1
				Keybind_upvr.Text = tbl_3_upvr[var110] or var110
			else
				var110 = var92_upvr
				var110[var94_upvr] = nil
				var110 = Keybind_upvr
				var110.Text = "None"
			end
			wait(0.1)
			module_3_upvr.binding = false
		end))
		if var92_upvr[var94_upvr] then
			local var111 = tbl_3_upvr[tostring(var92_upvr[var94_upvr].Name)]
			if not var111 then
				var111 = tostring(var92_upvr[var94_upvr].Name)
			end
			Keybind_upvr.Text = var111
		end
		module_3_upvr.binds[var94_upvr] = {
			location = var92_upvr;
			callback = var96;
		}
		arg1_15:Resize()
	end
	var22_upvr.Bind = Heartbeat_upvr
	function Heartbeat_upvr(arg1_16, arg2) -- Line 504, Named "Section"
		--[[ Upvalues[1]:
			[1]: module_3_upvr (readonly)
		]]
		local any_GetOrder_result1 = arg1_16:GetOrder()
		local udim2_3 = UDim2.new(1, 0, 0, 25)
		local udim2 = UDim2.new(0, 0, 0, 4)
		local udim2_5 = UDim2.new(1, 0, 0, 20)
		if any_GetOrder_result1 == 0 then
			udim2_3 = UDim2.new(1, 0, 0, 21)
			udim2 = UDim2.new(0, 0, 0, -1)
			udim2_5 = nil
		end
		local tbl_8 = {
			Name = "Section";
			BackgroundTransparency = 1;
			Size = udim2_3;
			BackgroundColor3 = module_3_upvr.options.sectncolor;
			BorderSizePixel = 0;
			LayoutOrder = any_GetOrder_result1;
		}
		local tbl_25 = {
			Name = "section_lbl";
		}
		tbl_25.Text = arg2
		tbl_25.BackgroundTransparency = 0
		tbl_25.BorderSizePixel = 0
		tbl_25.BackgroundColor3 = module_3_upvr.options.sectncolor
		tbl_25.TextColor3 = module_3_upvr.options.textcolor
		tbl_25.Position = udim2
		local var119 = udim2_5
		if not var119 then
			var119 = UDim2.new(1, 0, 1, 0)
		end
		tbl_25.Size = var119
		tbl_25.Font = module_3_upvr.options.font
		tbl_25.TextSize = module_3_upvr.options.fontsize
		tbl_25.TextStrokeTransparency = module_3_upvr.options.textstroke
		tbl_25.TextStrokeColor3 = module_3_upvr.options.strokecolor
		tbl_8[1] = module_3_upvr:Create("TextLabel", tbl_25)
		tbl_8.Parent = arg1_16.container
		arg1_16:Resize()
	end
	var22_upvr.Section = Heartbeat_upvr
	function Heartbeat_upvr(arg1_17, arg2, arg3, arg4) -- Line 543, Named "Slider"
		--[[ Upvalues[3]:
			[1]: module_3_upvr (readonly)
			[2]: tbl_19_upvr (readonly)
			[3]: UserInputService_upvr (readonly)
		]]
		local default_3 = arg3.default
		if not default_3 then
			default_3 = arg3.min
		end
		local var121_upvr = arg3.min or 0
		local var122_upvr = arg3.max or 1
		local location_upvr_2 = arg3.location
		if not location_upvr_2 then
			location_upvr_2 = arg1_17.flags
		end
		local var124_upvr = arg3.float or false
		local var125_upvr = arg3.flag or ""
		local var127_upvr = arg4
		if not var127_upvr then
			function var127_upvr() -- Line 550
			end
		end
		location_upvr_2[var125_upvr] = default_3
		local tbl_17 = {
			BackgroundTransparency = 1;
			Size = UDim2.new(1, 0, 0, 25);
			LayoutOrder = arg1_17:GetOrder();
		}
		local tbl_4 = {}
		tbl_4.Name = arg2
		tbl_4.TextStrokeTransparency = module_3_upvr.options.textstroke
		tbl_4.TextStrokeColor3 = module_3_upvr.options.strokecolor
		tbl_4.Text = '\r'..arg2
		tbl_4.BackgroundTransparency = 1
		tbl_4.TextColor3 = module_3_upvr.options.textcolor
		tbl_4.Position = UDim2.new(0, 5, 0, 2)
		tbl_4.Size = UDim2.new(1, -5, 1, 0)
		tbl_4.TextXAlignment = Enum.TextXAlignment.Left
		tbl_4.Font = module_3_upvr.options.font
		tbl_4.TextSize = module_3_upvr.options.fontsize
		tbl_4[1] = module_3_upvr:Create("Frame", {
			Name = "Container";
			Size = UDim2.new(0, 60, 0, 20);
			Position = UDim2.new(1, -65, 0, 3);
			BackgroundTransparency = 1;
			BorderSizePixel = 0;
			
			module_3_upvr:Create("TextLabel", {
				Name = "ValueLabel";
				Text = default_3;
				BackgroundTransparency = 1;
				TextColor3 = module_3_upvr.options.textcolor;
				Position = UDim2.new(0, -10, 0, 0);
				Size = UDim2.new(0, 1, 1, 0);
				TextXAlignment = Enum.TextXAlignment.Right;
				Font = module_3_upvr.options.font;
				TextSize = module_3_upvr.options.fontsize;
				TextStrokeTransparency = module_3_upvr.options.textstroke;
				TextStrokeColor3 = module_3_upvr.options.strokecolor;
			}), module_3_upvr:Create("TextButton", {
				Name = "Button";
				Size = UDim2.new(0, 5, 1, -2);
				Position = UDim2.new(0, 0, 0, 1);
				AutoButtonColor = false;
				Text = "";
				BackgroundColor3 = Color3.fromRGB(20, 20, 20);
				BorderSizePixel = 0;
				ZIndex = 999999995;
				TextStrokeTransparency = module_3_upvr.options.textstroke;
				TextStrokeColor3 = module_3_upvr.options.strokecolor;
			}), module_3_upvr:Create("Frame", {
				Name = "Line";
				BackgroundTransparency = 0;
				Position = UDim2.new(0, 0, 0.5, 0);
				Size = UDim2.new(1, 0, 0, 1);
				BackgroundColor3 = Color3.fromRGB(255, 255, 255);
				BorderSizePixel = 0;
			})
		})
		tbl_17[1] = module_3_upvr:Create("TextLabel", tbl_4)
		tbl_17.Parent = arg1_17.container
		local any_Create_result1_upvr = module_3_upvr:Create("Frame", tbl_17)
		local SOME_upvr = any_Create_result1_upvr:FindFirstChild(arg2)
		local var137_upvw
		local var138_upvw
		local var139_upvw
		local var140_upvw
		local var141_upvw
		table.insert(tbl_19_upvr, any_Create_result1_upvr:FindFirstChild(arg2).Container.MouseEnter:connect(function() -- Line 624
			--[[ Upvalues[15]:
				[1]: var137_upvw (read and write)
				[2]: UserInputService_upvr (copied, readonly)
				[3]: SOME_upvr (readonly)
				[4]: var121_upvr (readonly)
				[5]: var122_upvr (readonly)
				[6]: var124_upvr (readonly)
				[7]: var127_upvr (readonly)
				[8]: location_upvr_2 (readonly)
				[9]: var125_upvr (readonly)
				[10]: var138_upvw (read and write)
				[11]: var139_upvw (read and write)
				[12]: var140_upvw (read and write)
				[13]: any_Create_result1_upvr (readonly)
				[14]: arg2 (readonly)
				[15]: var141_upvw (read and write)
			]]
			local function _() -- Line 646, Named "disconnect"
				--[[ Upvalues[4]:
					[1]: var137_upvw (copied, read and write)
					[2]: var138_upvw (copied, read and write)
					[3]: var139_upvw (copied, read and write)
					[4]: var140_upvw (copied, read and write)
				]]
				if var137_upvw then
					var137_upvw:disconnect()
				end
				if var138_upvw then
					var138_upvw:disconnect()
				end
				if var139_upvw then
					var139_upvw:disconnect()
				end
				if var140_upvw then
					var140_upvw:disconnect()
				end
			end
			var138_upvw = any_Create_result1_upvr:FindFirstChild(arg2).Container.InputBegan:connect(function(arg1_18) -- Line 654
				--[[ Upvalues[9]:
					[1]: var137_upvw (copied, read and write)
					[2]: UserInputService_upvr (copied, readonly)
					[3]: SOME_upvr (copied, readonly)
					[4]: var121_upvr (copied, readonly)
					[5]: var122_upvr (copied, readonly)
					[6]: var124_upvr (copied, readonly)
					[7]: var127_upvr (copied, readonly)
					[8]: location_upvr_2 (copied, readonly)
					[9]: var125_upvr (copied, readonly)
				]]
				if arg1_18.UserInputType == Enum.UserInputType.MouseButton1 then
					if var137_upvw then
						var137_upvw:disconnect()
					end
					var137_upvw = game:GetService("RunService").RenderStepped:connect(function() -- Line 629
						--[[ Upvalues[8]:
							[1]: UserInputService_upvr (copied, readonly)
							[2]: SOME_upvr (copied, readonly)
							[3]: var121_upvr (copied, readonly)
							[4]: var122_upvr (copied, readonly)
							[5]: var124_upvr (copied, readonly)
							[6]: var127_upvr (copied, readonly)
							[7]: location_upvr_2 (copied, readonly)
							[8]: var125_upvr (copied, readonly)
						]]
						local tonumber_result1_3 = tonumber(string.format("%.2f", math.clamp((UserInputService_upvr:GetMouseLocation().X - SOME_upvr.Container.AbsolutePosition.X) / SOME_upvr.Container.AbsoluteSize.X, 0, 1)))
						SOME_upvr.Container.Button.Position = UDim2.new(math.clamp(tonumber_result1_3, 0, 0.99), 0, 0, 1)
						local var149 = var121_upvr + (var122_upvr - var121_upvr) * tonumber_result1_3
						local var150
						local function INLINED_13() -- Internal function, doesn't exist in bytecode
							var150 = math.floor(var149 * var124_upvr) / var124_upvr
							return var150
						end
						if not var124_upvr or not INLINED_13() then
							var150 = math.floor(var149)
						end
						SOME_upvr.Container.ValueLabel.Text = var150
						var127_upvr(tonumber(var150))
						location_upvr_2[var125_upvr] = tonumber(var150)
					end)
				end
			end)
			var139_upvw = any_Create_result1_upvr:FindFirstChild(arg2).Container.InputEnded:connect(function(arg1_19) -- Line 660
				--[[ Upvalues[4]:
					[1]: var137_upvw (copied, read and write)
					[2]: var138_upvw (copied, read and write)
					[3]: var139_upvw (copied, read and write)
					[4]: var140_upvw (copied, read and write)
				]]
				if arg1_19.UserInputType == Enum.UserInputType.MouseButton1 then
					if var137_upvw then
						var137_upvw:disconnect()
					end
					if var138_upvw then
						var138_upvw:disconnect()
					end
					if var139_upvw then
						var139_upvw:disconnect()
					end
					if var140_upvw then
						var140_upvw:disconnect()
					end
				end
			end)
			var141_upvw = any_Create_result1_upvr:FindFirstChild(arg2).Container.Button.MouseButton1Down:connect(function() -- Line 625, Named "update"
				--[[ Upvalues[9]:
					[1]: var137_upvw (copied, read and write)
					[2]: UserInputService_upvr (copied, readonly)
					[3]: SOME_upvr (copied, readonly)
					[4]: var121_upvr (copied, readonly)
					[5]: var122_upvr (copied, readonly)
					[6]: var124_upvr (copied, readonly)
					[7]: var127_upvr (copied, readonly)
					[8]: location_upvr_2 (copied, readonly)
					[9]: var125_upvr (copied, readonly)
				]]
				if var137_upvw then
					var137_upvw:disconnect()
				end
				var137_upvw = game:GetService("RunService").RenderStepped:connect(function() -- Line 629
					--[[ Upvalues[8]:
						[1]: UserInputService_upvr (copied, readonly)
						[2]: SOME_upvr (copied, readonly)
						[3]: var121_upvr (copied, readonly)
						[4]: var122_upvr (copied, readonly)
						[5]: var124_upvr (copied, readonly)
						[6]: var127_upvr (copied, readonly)
						[7]: location_upvr_2 (copied, readonly)
						[8]: var125_upvr (copied, readonly)
					]]
					local tonumber_result1_4 = tonumber(string.format("%.2f", math.clamp((UserInputService_upvr:GetMouseLocation().X - SOME_upvr.Container.AbsolutePosition.X) / SOME_upvr.Container.AbsoluteSize.X, 0, 1)))
					SOME_upvr.Container.Button.Position = UDim2.new(math.clamp(tonumber_result1_4, 0, 0.99), 0, 0, 1)
					local var144 = var121_upvr + (var122_upvr - var121_upvr) * tonumber_result1_4
					local var145
					local function INLINED_12() -- Internal function, doesn't exist in bytecode
						var145 = math.floor(var144 * var124_upvr) / var124_upvr
						return var145
					end
					if not var124_upvr or not INLINED_12() then
						var145 = math.floor(var144)
					end
					SOME_upvr.Container.ValueLabel.Text = var145
					var127_upvr(tonumber(var145))
					location_upvr_2[var125_upvr] = tonumber(var145)
				end)
			end)
			var140_upvw = UserInputService_upvr.InputEnded:connect(function(arg1_20, arg2_3) -- Line 667
				--[[ Upvalues[5]:
					[1]: var141_upvw (copied, read and write)
					[2]: var137_upvw (copied, read and write)
					[3]: var138_upvw (copied, read and write)
					[4]: var139_upvw (copied, read and write)
					[5]: var140_upvw (copied, read and write)
				]]
				if arg1_20.UserInputType == Enum.UserInputType.MouseButton1 and var141_upvw.Connected then
					if var137_upvw then
						var137_upvw:disconnect()
					end
					if var138_upvw then
						var138_upvw:disconnect()
					end
					if var139_upvw then
						var139_upvw:disconnect()
					end
					if var140_upvw then
						var140_upvw:disconnect()
					end
				end
			end)
		end))
		if default_3 ~= var121_upvr then
			local tonumber_result1_2 = tonumber(string.format("%.2f", default_3))
			if not var124_upvr then
				tonumber_result1_2 = math.floor(tonumber_result1_2)
			end
			SOME_upvr.Container.Button.Position = UDim2.new(math.clamp(1 - (var122_upvr - default_3) / (var122_upvr - var121_upvr), 0, 0.99), 0, 0, 1)
			SOME_upvr.Container.ValueLabel.Text = tonumber_result1_2
		end
		arg1_17:Resize()
		return {
			Set = function(arg1_21, arg2_4) -- Line 689, Named "Set"
				--[[ Upvalues[7]:
					[1]: var122_upvr (readonly)
					[2]: var121_upvr (readonly)
					[3]: var124_upvr (readonly)
					[4]: SOME_upvr (readonly)
					[5]: location_upvr_2 (readonly)
					[6]: var125_upvr (readonly)
					[7]: var127_upvr (readonly)
				]]
				local tonumber_result1 = tonumber(string.format("%.2f", arg2_4))
				if not var124_upvr then
					tonumber_result1 = math.floor(tonumber_result1)
				end
				SOME_upvr.Container.Button.Position = UDim2.new(math.clamp(1 - (var122_upvr - arg2_4) / (var122_upvr - var121_upvr), 0, 0.99), 0, 0, 1)
				SOME_upvr.Container.ValueLabel.Text = tonumber_result1
				location_upvr_2[var125_upvr] = tonumber_result1
				var127_upvr(tonumber_result1)
			end;
		}
	end
	var22_upvr.Slider = Heartbeat_upvr
	function Heartbeat_upvr(arg1_22, arg2, arg3, arg4) -- Line 706, Named "SearchBox"
		--[[ Upvalues[2]:
			[1]: module_3_upvr (readonly)
			[2]: tbl_19_upvr (readonly)
		]]
		local list_upvw_2 = arg3.list
		if not list_upvw_2 then
			list_upvw_2 = {}
		end
		local location_upvr_3 = arg3.location
		if not location_upvr_3 then
			location_upvr_3 = arg1_22.flags
		end
		local var159_upvr = arg4
		if not var159_upvr then
			function var159_upvr() -- Line 710
			end
		end
		local var160_upvw = false
		local tbl_7 = {
			BackgroundTransparency = 1;
			Size = UDim2.new(1, 0, 0, 25);
			LayoutOrder = arg1_22:GetOrder();
		}
		local tbl_28 = {
			Text = "";
		}
		tbl_28.PlaceholderText = arg2
		tbl_28.PlaceholderColor3 = Color3.fromRGB(60, 60, 60)
		tbl_28.Font = module_3_upvr.options.font
		tbl_28.TextSize = module_3_upvr.options.fontsize
		tbl_28.Name = "Box"
		tbl_28.Size = UDim2.new(1, -10, 0, 20)
		tbl_28.Position = UDim2.new(0, 5, 0, 4)
		tbl_28.TextColor3 = module_3_upvr.options.textcolor
		tbl_28.BackgroundColor3 = module_3_upvr.options.dropcolor
		tbl_28.BorderColor3 = module_3_upvr.options.bordercolor
		tbl_28.TextStrokeTransparency = module_3_upvr.options.textstroke
		tbl_28.TextStrokeColor3 = module_3_upvr.options.strokecolor
		tbl_28[1] = module_3_upvr:Create("ScrollingFrame", {
			Position = UDim2.new(0, 0, 1, 1);
			Name = "Container";
			BackgroundColor3 = module_3_upvr.options.btncolor;
			ScrollBarThickness = 0;
			BorderSizePixel = 0;
			BorderColor3 = module_3_upvr.options.bordercolor;
			Size = UDim2.new(1, 0, 0, 0);
			ZIndex = 999999995;
			module_3_upvr:Create("UIListLayout", {
				Name = "ListLayout";
				SortOrder = Enum.SortOrder.LayoutOrder;
			})
		})
		tbl_7[1] = module_3_upvr:Create("TextBox", tbl_28)
		tbl_7.Parent = arg1_22.container
		local any_Create_result1_upvr_6 = module_3_upvr:Create("Frame", tbl_7)
		local var166_upvr = arg3.flag or ""
		local function rebuild_upvr(arg1_23) -- Line 749, Named "rebuild"
			--[[ Upvalues[7]:
				[1]: any_Create_result1_upvr_6 (readonly)
				[2]: list_upvw_2 (read and write)
				[3]: module_3_upvr (copied, readonly)
				[4]: var160_upvw (read and write)
				[5]: location_upvr_3 (readonly)
				[6]: var166_upvr (readonly)
				[7]: var159_upvr (readonly)
			]]
			any_Create_result1_upvr_6:FindFirstChild("Box").Container.ScrollBarThickness = 0
			for _, v_4 in next, any_Create_result1_upvr_6:FindFirstChild("Box").Container:GetChildren() do
				if not v_4:IsA("UIListLayout") then
					v_4:Destroy()
				end
			end
			if 0 < #arg1_23 then
				for i_5, v_5 in next, list_upvw_2 do
					if string.sub(string.lower(v_5), 1, string.len(arg1_23)) == string.lower(arg1_23) then
						local any_Create_result1_upvr_8 = module_3_upvr:Create("TextButton", {
							Text = v_5;
							Font = module_3_upvr.options.font;
							TextSize = module_3_upvr.options.fontsize;
							TextColor3 = module_3_upvr.options.textcolor;
							BorderColor3 = module_3_upvr.options.bordercolor;
							TextStrokeTransparency = module_3_upvr.options.textstroke;
							TextStrokeColor3 = module_3_upvr.options.strokecolor;
							Parent = any_Create_result1_upvr_6:FindFirstChild("Box").Container;
							Size = UDim2.new(1, 0, 0, 20);
							LayoutOrder = i_5;
							BackgroundColor3 = module_3_upvr.options.btncolor;
							ZIndex = 999999995;
						})
						any_Create_result1_upvr_8.MouseButton1Click:connect(function() -- Line 775
							--[[ Upvalues[6]:
								[1]: var160_upvw (copied, read and write)
								[2]: any_Create_result1_upvr_6 (copied, readonly)
								[3]: any_Create_result1_upvr_8 (readonly)
								[4]: location_upvr_3 (copied, readonly)
								[5]: var166_upvr (copied, readonly)
								[6]: var159_upvr (copied, readonly)
							]]
							var160_upvw = true
							any_Create_result1_upvr_6:FindFirstChild("Box").Text = any_Create_result1_upvr_8.Text
							wait()
							var160_upvw = false
							location_upvr_3[var166_upvr] = any_Create_result1_upvr_8.Text
							var159_upvr(location_upvr_3[var166_upvr])
							any_Create_result1_upvr_6:FindFirstChild("Box").Container.ScrollBarThickness = 0
							for _, v_6 in next, any_Create_result1_upvr_6:FindFirstChild("Box").Container:GetChildren() do
								if not v_6:IsA("UIListLayout") then
									v_6:Destroy()
								end
							end
							any_Create_result1_upvr_6:FindFirstChild("Box").Container:TweenSize(UDim2.new(1, 0, 0, 0), "Out", "Quad", 0.25, true)
						end)
					end
				end
			end
			local children_2 = any_Create_result1_upvr_6:FindFirstChild("Box").Container:GetChildren()
			any_Create_result1_upvr_8 = #children_2
			any_Create_result1_upvr_8 = 100
			if 100 < #children_2 * 20 - 20 then
				any_Create_result1_upvr_6:FindFirstChild("Box").Container.ScrollBarThickness = 5
			end
			any_Create_result1_upvr_8 = UDim2.new(1, 0, 0, math.clamp(any_Create_result1_upvr_8 * 20 - 20, 0, any_Create_result1_upvr_8))
			any_Create_result1_upvr_6:FindFirstChild("Box").Container:TweenSize(any_Create_result1_upvr_8, "Out", "Quad", 0.25, true)
			any_Create_result1_upvr_8 = 1
			any_Create_result1_upvr_6:FindFirstChild("Box").Container.CanvasSize = UDim2.new(any_Create_result1_upvr_8, 0, 0, #children_2 * 20 - 20)
		end
		table.insert(tbl_19_upvr, any_Create_result1_upvr_6:FindFirstChild("Box"):GetPropertyChangedSignal("Text"):connect(function() -- Line 808
			--[[ Upvalues[3]:
				[1]: var160_upvw (read and write)
				[2]: rebuild_upvr (readonly)
				[3]: any_Create_result1_upvr_6 (readonly)
			]]
			if not var160_upvw then
				rebuild_upvr(any_Create_result1_upvr_6:FindFirstChild("Box").Text)
			end
		end))
		local function reload(arg1_24) -- Line 814
			--[[ Upvalues[2]:
				[1]: list_upvw_2 (read and write)
				[2]: rebuild_upvr (readonly)
			]]
			list_upvw_2 = arg1_24
			rebuild_upvr("")
		end
		arg1_22:Resize()
		return reload, any_Create_result1_upvr_6:FindFirstChild("Box")
	end
	var22_upvr.SearchBox = Heartbeat_upvr
	function Heartbeat_upvr(arg1_25, arg2, arg3, arg4) -- Line 822, Named "Dropdown"
		--[[ Upvalues[3]:
			[1]: module_3_upvr (readonly)
			[2]: tbl_19_upvr (readonly)
			[3]: UserInputService_upvr (readonly)
		]]
		local location_upvr_4 = arg3.location
		if not location_upvr_4 then
			location_upvr_4 = arg1_25.flags
		end
		local var183_upvr = arg3.flag or ""
		local var185_upvr = arg4
		if not var185_upvr then
			function var185_upvr() -- Line 825
			end
		end
		local list_upvw = arg3.list
		if not list_upvw then
			list_upvw = {}
		end
		location_upvr_4[var183_upvr] = list_upvw[1]
		local any_Create_result1_upvr_2 = module_3_upvr:Create("Frame", {
			BackgroundTransparency = 1;
			Size = UDim2.new(1, 0, 0, 25);
			BackgroundColor3 = Color3.fromRGB(25, 25, 25);
			BorderSizePixel = 0;
			LayoutOrder = arg1_25:GetOrder();
			Parent = arg1_25.container;
			module_3_upvr:Create("Frame", {
				Name = "dropdown_lbl";
				BackgroundTransparency = 0;
				BackgroundColor3 = module_3_upvr.options.dropcolor;
				Position = UDim2.new(0, 5, 0, 4);
				BorderColor3 = module_3_upvr.options.bordercolor;
				Size = UDim2.new(1, -10, 0, 20);
				
				module_3_upvr:Create("TextLabel", {
					Name = "Selection";
					Size = UDim2.new(1, 0, 1, 0);
					Text = list_upvw[1];
					TextColor3 = module_3_upvr.options.textcolor;
					BackgroundTransparency = 1;
					Font = module_3_upvr.options.font;
					TextSize = module_3_upvr.options.fontsize;
					TextStrokeTransparency = module_3_upvr.options.textstroke;
					TextStrokeColor3 = module_3_upvr.options.strokecolor;
				}), module_3_upvr:Create("TextButton", {
					Name = "drop";
					BackgroundTransparency = 1;
					Size = UDim2.new(0, 20, 1, 0);
					Position = UDim2.new(1, -25, 0, 0);
					Text = 'v';
					TextColor3 = module_3_upvr.options.textcolor;
					Font = module_3_upvr.options.font;
					TextSize = module_3_upvr.options.fontsize;
					TextStrokeTransparency = module_3_upvr.options.textstroke;
					TextStrokeColor3 = module_3_upvr.options.strokecolor;
				})
			})
		})
		local var192_upvw
		table.insert(tbl_19_upvr, any_Create_result1_upvr_2:FindFirstChild("dropdown_lbl").drop.MouseButton1Click:connect(function() -- Line 872
			--[[ Upvalues[9]:
				[1]: var192_upvw (read and write)
				[2]: any_Create_result1_upvr_2 (readonly)
				[3]: arg2 (readonly)
				[4]: list_upvw (read and write)
				[5]: module_3_upvr (copied, readonly)
				[6]: location_upvr_4 (readonly)
				[7]: var183_upvr (readonly)
				[8]: var185_upvr (readonly)
				[9]: UserInputService_upvr (copied, readonly)
			]]
			-- KONSTANTWARNING: Variable analysis failed. Output will have some incorrect variable assignments
			local var247
			if var247 then
				var247 = var192_upvw.Connected
				if var247 then return end
			end
			var247 = any_Create_result1_upvr_2:FindFirstChild("dropdown_lbl"):WaitForChild("Selection")
			var247.TextColor3 = Color3.fromRGB(60, 60, 60)
			var247 = any_Create_result1_upvr_2:FindFirstChild("dropdown_lbl"):WaitForChild("Selection")
			var247.Text = arg2
			var247 = 0
			for _, _ in next, list_upvw do
				var247 += 20
			end
			local udim2_4 = UDim2.new(1, 0, 0, var247)
			local var249
			local var250 = 0
			if 100 < udim2_4.Y.Offset then
				var249 = UDim2.new(1, 0, 0, 100)
				var250 = 5
			end
			if var249 == nil or not var249 then
			end
			local any_Create_result1_upvr_5 = module_3_upvr:Create("ScrollingFrame", {
				TopImage = "rbxasset://textures/ui/Scroll/scroll-middle.png";
				BottomImage = "rbxasset://textures/ui/Scroll/scroll-middle.png";
				Name = "DropContainer";
				Parent = any_Create_result1_upvr_2:FindFirstChild("dropdown_lbl");
				Size = UDim2.new(1, 0, 0, 0);
				BackgroundColor3 = module_3_upvr.options.bgcolor;
				BorderColor3 = module_3_upvr.options.bordercolor;
				Position = UDim2.new(0, 0, 1, 0);
				ScrollBarThickness = var250;
				CanvasSize = UDim2.new(0, 0, 0, udim2_4.Y.Offset);
				ZIndex = 999999997;
				ClipsDescendants = true;
				
				module_3_upvr:Create("UIListLayout", {
					Name = "List";
					SortOrder = Enum.SortOrder.LayoutOrder;
				})
			})
			for i_8, v_8 in next, list_upvw do
				local any_Create_result1_upvr_4 = module_3_upvr:Create("TextButton", {
					Size = UDim2.new(1, 0, 0, 20);
					BackgroundColor3 = module_3_upvr.options.btncolor;
					BorderColor3 = module_3_upvr.options.bordercolor;
					Text = v_8;
					Font = module_3_upvr.options.font;
					TextSize = module_3_upvr.options.fontsize;
					LayoutOrder = i_8;
					Parent = any_Create_result1_upvr_5;
					ZIndex = 999999997;
					TextColor3 = module_3_upvr.options.textcolor;
					TextStrokeTransparency = module_3_upvr.options.textstroke;
					TextStrokeColor3 = module_3_upvr.options.strokecolor;
				})
				any_Create_result1_upvr_4.MouseButton1Click:connect(function() -- Line 929
					--[[ Upvalues[8]:
						[1]: any_Create_result1_upvr_2 (copied, readonly)
						[2]: module_3_upvr (copied, readonly)
						[3]: any_Create_result1_upvr_4 (readonly)
						[4]: location_upvr_4 (copied, readonly)
						[5]: var183_upvr (copied, readonly)
						[6]: var185_upvr (copied, readonly)
						[7]: any_Create_result1_upvr_5 (readonly)
						[8]: var192_upvw (copied, read and write)
					]]
					any_Create_result1_upvr_2:FindFirstChild("dropdown_lbl"):WaitForChild("Selection").TextColor3 = module_3_upvr.options.textcolor
					any_Create_result1_upvr_2:FindFirstChild("dropdown_lbl"):WaitForChild("Selection").Text = any_Create_result1_upvr_4.Text
					location_upvr_4[var183_upvr] = tostring(any_Create_result1_upvr_4.Text)
					var185_upvr(location_upvr_4[var183_upvr])
					game:GetService("Debris"):AddItem(any_Create_result1_upvr_5, 0)
					var192_upvw:disconnect()
				end)
				local var257_upvr
			end
			any_Create_result1_upvr_4 = 0.15
			var257_upvr:TweenSize(udim2_4, "Out", "Quad", any_Create_result1_upvr_4, true)
			local function isInGui_upvr(arg1_28) -- Line 943, Named "isInGui"
				--[[ Upvalues[1]:
					[1]: UserInputService_upvr (copied, readonly)
				]]
				local any_GetMouseLocation_result1_3 = UserInputService_upvr:GetMouseLocation()
				local vector2_4 = Vector2.new(any_GetMouseLocation_result1_3.X, any_GetMouseLocation_result1_3.Y - 36)
				local var260 = false
				if arg1_28.AbsolutePosition.X <= vector2_4.X then
					var260 = false
					if vector2_4.X <= arg1_28.AbsolutePosition.X + arg1_28.AbsoluteSize.X then
						var260 = false
						if arg1_28.AbsolutePosition.Y <= vector2_4.Y then
							if vector2_4.Y > arg1_28.AbsolutePosition.Y + arg1_28.AbsoluteSize.Y then
								var260 = false
							else
								var260 = true
							end
						end
					end
				end
				return var260
			end
			var192_upvw = UserInputService_upvr.InputBegan:connect(function(arg1_29) -- Line 953
				--[[ Upvalues[7]:
					[1]: isInGui_upvr (readonly)
					[2]: var257_upvr (readonly)
					[3]: any_Create_result1_upvr_2 (copied, readonly)
					[4]: module_3_upvr (copied, readonly)
					[5]: location_upvr_4 (copied, readonly)
					[6]: var183_upvr (copied, readonly)
					[7]: var192_upvw (copied, read and write)
				]]
				if arg1_29.UserInputType == Enum.UserInputType.MouseButton1 and not isInGui_upvr(var257_upvr) then
					any_Create_result1_upvr_2:FindFirstChild("dropdown_lbl"):WaitForChild("Selection").TextColor3 = module_3_upvr.options.textcolor
					any_Create_result1_upvr_2:FindFirstChild("dropdown_lbl"):WaitForChild("Selection").Text = location_upvr_4[var183_upvr]
					var257_upvr:TweenSize(UDim2.new(1, 0, 0, 0), "In", "Quad", 0.15, true)
					wait(0.15)
					game:GetService("Debris"):AddItem(var257_upvr, 0)
					var192_upvw:disconnect()
				end
			end)
		end))
		arg1_25:Resize()
		return {
			Refresh = function(arg1_30, arg2_5, arg3_2) -- Line 968, Named "reload"
				--[[ Upvalues[6]:
					[1]: list_upvw (read and write)
					[2]: location_upvr_4 (readonly)
					[3]: var183_upvr (readonly)
					[4]: var192_upvw (read and write)
					[5]: any_Create_result1_upvr_2 (readonly)
					[6]: module_3_upvr (copied, readonly)
				]]
				list_upvw = arg2_5
				local var262 = arg3_2
				if not var262 then
					var262 = arg2_5[1]
				end
				location_upvr_4[var183_upvr] = var262
				pcall(function() -- Line 971
					--[[ Upvalues[1]:
						[1]: var192_upvw (copied, read and write)
					]]
					var192_upvw:disconnect()
				end)
				any_Create_result1_upvr_2:WaitForChild("dropdown_lbl").Selection.Text = location_upvr_4[var183_upvr]
				any_Create_result1_upvr_2:FindFirstChild("dropdown_lbl"):WaitForChild("Selection").TextColor3 = module_3_upvr.options.textcolor
				game:GetService("Debris"):AddItem(container, 0)
			end;
			Set = function(arg1_31, arg2_6, arg3_3) -- Line 979, Named "set"
				--[[ Upvalues[4]:
					[1]: location_upvr_4 (readonly)
					[2]: var183_upvr (readonly)
					[3]: any_Create_result1_upvr_2 (readonly)
					[4]: var185_upvr (readonly)
				]]
				location_upvr_4[var183_upvr] = arg2_6
				any_Create_result1_upvr_2:WaitForChild("dropdown_lbl").Selection.Text = location_upvr_4[var183_upvr]
				if arg3_3 then
				else
					var185_upvr(location_upvr_4[var183_upvr])
				end
			end;
		}
	end
	var22_upvr.Dropdown = Heartbeat_upvr
	function Heartbeat_upvr(arg1_32, arg2, arg3) -- Line 993, Named "Create"
		local any = Instance.new(arg2)
		for i_9, v_9 in next, arg3 do
			if i_9 ~= "Parent" then
				if typeof(v_9) == "Instance" then
					v_9.Parent = any
				else
					any[i_9] = v_9
				end
			end
		end
		any.Parent = arg3.Parent
		return any
	end
	module_3_upvr.Create = Heartbeat_upvr
	function Heartbeat_upvr(arg1_33, arg2, arg3) -- Line 1010, Named "CreateWindow"
		--[[ Upvalues[3]:
			[1]: module_3_upvr (readonly)
			[2]: var22_upvr (readonly)
			[3]: tbl_22_upvr (readonly)
		]]
		local var268
		if not module_3_upvr.container then
			local tbl_18 = {arg1_33:Create("Frame", {
				Name = "Container";
				Size = UDim2.new(1, -30, 1, 0);
				Position = UDim2.new(0, 20, 0, 20);
				BackgroundTransparency = 1;
				Active = false;
			})}
			var268 = 999999998
			tbl_18.DisplayOrder = var268
			local function INLINED_14() -- Internal function, doesn't exist in bytecode
				var268 = gethui()
				return var268
			end
			if not gethui or not INLINED_14() then
				var268 = game:GetService("CoreGui")
			end
			tbl_18.Parent = var268
			module_3_upvr.container = arg1_33:Create("ScreenGui", tbl_18):FindFirstChild("Container")
		end
		if not module_3_upvr.options then
			local var271 = arg3
			if not var271 then
				var271 = {}
			end
			module_3_upvr.options = setmetatable(var271, {
				__index = nil;
			})
		end
		local any_window_result1 = var22_upvr.window(arg2, module_3_upvr.options)
		tbl_22_upvr.new(any_window_result1.object)
		return any_window_result1
	end
	module_3_upvr.CreateWindow = Heartbeat_upvr
	Heartbeat_upvr = {}
	local isreallypressed = Heartbeat_upvr
	isreallypressed.topcolor = Color3.fromRGB(30, 30, 30)
	isreallypressed.titlecolor = Color3.fromRGB(255, 255, 255)
	isreallypressed.underlinecolor = Color3.fromRGB(0, 255, 140)
	isreallypressed.bgcolor = Color3.fromRGB(35, 35, 35)
	isreallypressed.boxcolor = Color3.fromRGB(35, 35, 35)
	isreallypressed.btncolor = Color3.fromRGB(25, 25, 25)
	isreallypressed.dropcolor = Color3.fromRGB(25, 25, 25)
	isreallypressed.sectncolor = Color3.fromRGB(25, 25, 25)
	isreallypressed.bordercolor = Color3.fromRGB(60, 60, 60)
	isreallypressed.font = Enum.Font.SourceSans
	isreallypressed.titlefont = Enum.Font.Code
	isreallypressed.fontsize = 17
	isreallypressed.titlesize = 18
	isreallypressed.textstroke = 1
	isreallypressed.titlestroke = 1
	isreallypressed.strokecolor = Color3.fromRGB(0, 0, 0)
	isreallypressed.textcolor = Color3.fromRGB(255, 255, 255)
	isreallypressed.titletextcolor = Color3.fromRGB(255, 255, 255)
	isreallypressed.placeholdercolor = Color3.fromRGB(255, 255, 255)
	isreallypressed.titlestrokecolor = Color3.fromRGB(0, 0, 0)
	default = isreallypressed -- Setting global
	isreallypressed = setmetatable({}, {
		__index = default;
	})
	module_3_upvr.options = isreallypressed
	isreallypressed = spawn
	isreallypressed(function() -- Line 1066
		--[[ Upvalues[1]:
			[1]: module_3_upvr (readonly)
		]]
		while true do
			for i_10 = 0, 1, 0.0033333333333333335 do
				for _, v_10 in next, module_3_upvr.rainbowtable do
					v_10.BackgroundColor3 = Color3.fromHSV(i_10, 1, 1)
				end
				wait()
			end
		end
	end)
	function isreallypressed(arg1_34, arg2) -- Line 1077
		local var282
		if var282 == "Instance" then
			var282 = arg1_34.UserInputType
			if var282 == Enum.UserInputType.Keyboard then
				var282 = arg2.KeyCode
				if var282 == arg1_34.KeyCode then
					var282 = true
					return var282
				end
			end
			var282 = tostring(arg1_34.UserInputType):find("MouseButton")
			if var282 then
				var282 = arg2.UserInputType
				if var282 == arg1_34.UserInputType then
					var282 = true
					return var282
				end
			end
		end
		var282 = tostring(arg1_34):find("MouseButton1")
		if var282 then
			if arg1_34 ~= arg2.UserInputType then
				var282 = false
			else
				var282 = true
			end
			return var282
		end
		if arg1_34 ~= arg2.KeyCode then
			var282 = false
		else
			var282 = true
		end
		return var282
	end
	local var280_upvr = isreallypressed
	table.insert(tbl_19_upvr, UserInputService_upvr.InputBegan:connect(function(arg1_35) -- Line 1093
		--[[ Upvalues[2]:
			[1]: module_3_upvr (readonly)
			[2]: var280_upvr (readonly)
		]]
		if not module_3_upvr.binding then
			for i_12, v_11 in next, module_3_upvr.binds do
				local var286 = v_11.location[i_12]
				if var286 and var280_upvr(var286, arg1_35) then
					v_11.pressed = true
					v_11.callback(true)
				end
			end
		end
	end))
	table.insert(tbl_19_upvr, UserInputService_upvr.InputEnded:connect(function(arg1_36) -- Line 1105
		--[[ Upvalues[2]:
			[1]: module_3_upvr (readonly)
			[2]: var280_upvr (readonly)
		]]
		if not module_3_upvr.binding then
			for i_13, v_12 in next, module_3_upvr.binds do
				local var290 = v_12.location[i_13]
				if var290 and var280_upvr(var290, arg1_36) then
					v_12.pressed = false
					v_12.callback(false)
				end
			end
		end
	end))
	function tbl_22_upvr() -- Line 1118
		--[[ Upvalues[2]:
			[1]: tbl_19_upvr (readonly)
			[2]: module_3_upvr (readonly)
		]]
		for _, v_13 in next, tbl_19_upvr do
			v_13:Disconnect()
		end
		module_3_upvr.container:Destroy()
	end
	module_3_upvr.Unload = tbl_22_upvr
	return module_3_upvr
end
module_2.new = new
return module_2
