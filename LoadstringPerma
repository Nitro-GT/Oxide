--[[getgenv().OxideSettings = {
Refit = true,
noclip = true,
FlingEnabled = false,
ToolFling = false, -- false = holding, true = fling
AntiFling = false,
Legacy = false,
Scale = 1,
ClientHats = {},
CustomHats = false, -- Enable or disable custom rig feature (basically old oxide when false)
CH = {},
}]]
--[[ 
Oxide V3.7 
Anything below should NOT be changed
]]
if OxideSettings == nil then
	getgenv().OxideSettings = {}
end
if OxideSettings.CH == nil then 
	OxideSettings.CH = {}
end
for i,v in pairs(_G) do
	OxideSettings[i] = v
end

OxideSettings.TransparentRig = true
OxideSettings.ClickFling = true
OxideSettings.TeleportCharacter = true
OxideSettings.HatCollide = false
OxideSettings.HideCharacter = true
if OxideSettings.Legacy == nil then
	OxideSettings.Legacy = false 
end
if OxideSettings.ClientHats == nil then 
    OxideSettings.ClientHats = {}
end
if OxideSettings.Scale == nil then
	OxideSettings.Scale = 1
end
if OxideSettings.CH.Head == nil then 
	OxideSettings.CH.Head = {}
end
if OxideSettings.CH.Head.Name == nil then 
	OxideSettings.CH.Head.Name = "wtfgangimgonnakms!"
end
local str = game:GetService("SharedTableRegistry")
if not getgenv then 
	local getgenv = function()
		return _G
	end
end
local connect
local velocity
local removedl
local char
local function transparent() 
	for _, child in pairs(char:GetChildren()) do
		local v = child
		if child:IsA("BasePart") and not v:IsA("Model") and v.Name == "Torso" or  child:IsA("BasePart") and v.Name == "Right Arm" or  child:IsA("BasePart") and v.Name == "Left Arm" or  child:IsA("BasePart") and v.Name == "Right Leg" or  child:IsA("BasePart") and v.Name == "Left Leg" then
			if OxideSettings.TransparentRig == true then
				child.Transparency = .5
			else 
				child.Transparency = 1 
			end
		elseif child:IsA("Accessory") and v.Name ~= "Black" then
			if OxideSettings.TransparentRig == true then
				child.Handle.Transparency = .5
			else 
				child.Handle.Transparency = 1 
			end
		end
	end
end
local curcamcf
local function respawnfunc()
	curcamcf = workspace.CurrentCamera.CFrame
	replicatesignal(game:GetService("Players").LocalPlayer.ConnectDiedSignalBackend)
	task.wait(game:GetService("Players").RespawnTime)
	connect:Disconnect()
	velocity:Disconnect()
	removedl:Disconnect()
	transparent()
end
local flingpos = game:GetService("Players").LocalPlayer:GetMouse().Hit
local flingpart = game:GetService("Players").LocalPlayer:GetMouse().Target
local flingplr = nil
local sineee=os.clock()
local sine=os.clock()
local plr =game:GetService("Players").LocalPlayer
local lp = plr
local cf 
local lastcf = workspace.CurrentCamera.CFrame
local oldh = workspace.FallenPartsDestroyHeight
local tools = {}
local faketools = {}
local stopped = false
local moveloop
local respawnloop
OxideSettings.Stopped = false
OxideSettings.SBV4R = false
OxideSettings.R6Mode = false
OxideSettings.MiztCompat = true
OxideSettings.Fling = false
game:GetService("StarterGui"):SetCore("SendNotification", {
	Title = "Oxide Reanimation V3.7 ";
	Duration = 20;
	Text = "This script was made by Hemi"
})
local function cfAdd(a,b) return a+b end
pcall(function()
	task.spawn(function()
		game:GetService("CoreGui"):WaitForChild("TopBarApp"):WaitForChild("FullScreenFrame"):WaitForChild("HurtOverlay"):Destroy()
	end)
end)
local Hat = {
	Rename = function(HatID, NAME, oname)
		pcall(function()
			if oname == nil then oname = "Hat" end
			for i,v in pairs(game:GetService("Players").LocalPlayer.Character:GetChildren()) do
				if v:IsA("Accessory") then
					if game:GetService("Players").LocalPlayer.Character.Humanoid.RigType == Enum.HumanoidRigType.R6 then
						if v:WaitForChild("Handle"):FindFirstChildWhichIsA("SpecialMesh").TextureId == HatID then
							if oname == "Hat" then
								v.Name = NAME
							elseif oname == "LARM" then
								v.Name = "fooblet"
							elseif oname == "RARM" then
								v.Name = "gooblet"
							else
								v.Name = NAME
							end
						end
					elseif game:GetService("Players").LocalPlayer.Character.Humanoid.RigType == Enum.HumanoidRigType.R6 and v.Handle.TextureId == HatID  then
						if oname == "Hat" then
							v.Name = NAME
						elseif oname == "LARM" then
							v.Name = "fooblet"
						elseif oname == "RARM" then
							v.Name = "gooblet"
						else
							v.Name = NAME
						end
					elseif game:GetService("Players").LocalPlayer.Character.Humanoid.RigType == Enum.HumanoidRigType.R15 then
						if v.Handle.TextureID == HatID then
							if oname == "Hat" then
								v.Name = NAME
							elseif oname == "LARM" then
								v.Name = "fooblet"
							elseif oname == "RARM" then
								v.Name = "gooblet"
							else
								v.Name = NAME
							end
						end
					end
				end
			end
		end)
	end,
	Rename2 = function(HatID, NAME,rname, oname)
		pcall(function()
			if oname == nil then oname = "Hat" end
			for i,v in pairs(game:GetService("Players").LocalPlayer.Character:GetChildren()) do
				if v:IsA("Accessory") then
					if game:GetService("Players").LocalPlayer.Character.Humanoid.RigType == Enum.HumanoidRigType.R6 then
						if v:WaitForChild("Handle"):FindFirstChildWhichIsA("SpecialMesh").TextureId == HatID then
							if v.Name == rname then
								if oname == "Hat" then
									v.Name = NAME
								elseif oname == "LARM" then
									v.Name = "fooblet"
								elseif oname == "RARM" then
									v.Name = "gooblet"
								else
									v.Name = NAME
								end
							end
						end
					elseif game:GetService("Players").LocalPlayer.Character.Humanoid.RigType == Enum.HumanoidRigType.R6 and v.Handle.TextureId == HatID  then
						if v.Name == rname then
							if oname == "Hat" then
								v.Name = NAME
							elseif oname == "LARM" then
								v.Name = "fooblet"
							elseif oname == "RARM" then
								v.Name = "gooblet"
							else
								v.Name = NAME
							end
						end
					elseif game:GetService("Players").LocalPlayer.Character.Humanoid.RigType == Enum.HumanoidRigType.R15 then
						if v:WaitForChild("Handle").TextureID == HatID then
							if v.Name == rname then
								if oname == "Hat" then
									v.Name = NAME
								elseif oname == "LARM" then
									v.Name = "fooblet"
								elseif oname == "RARM" then
									v.Name = "gooblet"
								else
									v.Name = NAME
								end
							end
						end
					end
				end
			end
		end)
	end,}
local function redo()
	local gay = true -- dont edit >:(
	hmode = nil
	if gay == true then
		hmode = "norm" 
	else
		hmode = "alsoo3" -- hate this guy
	end
	--game:GetService("Workspace")["Error_30363"].EyesOfTheEverWorld.Name = "Puffer Vest"
	loadstring(game:HttpGet("https://raw.githubusercontent.com/Nitro-GT/OxideReanim/main/stuff2"))()
	local c = game:GetService("Players").LocalPlayer.Character
	if not workspace:FindFirstChild("non") then
		if OxideSettings.Legacy == false then 
			char = game:GetObjects("rbxassetid://140589790135981")[1]
		else
			char = game:GetService("Players"):CreateHumanoidModelFromDescription(game:GetService("Players"):GetHumanoidDescriptionFromUserId(game:GetService("Players").LocalPlayer.UserId),Enum.HumanoidRigType.R6)
			for i,v in pairs(char:GetChildren()) do
				if v:IsA("Accessory") then
					v:Destroy()
				end
			end
			for i,v in pairs(char:GetDescendants()) do
				if v:IsA("BasePart") then
					v.Transparency = 1
				elseif v:IsA("Decal") then
					v.Transparency = 1
				end
			end
		end
	else
		char = workspace.non
	end

	_G.OxideFakeChar = char 
	getgenv().OxideFakeChar = char
	getgenv().OxideRealChar = c
	local hum = char:FindFirstChildOfClass("Humanoid")
	hum.DisplayDistanceType = 2
	if OxideSettings.MiztCompat == false then
		char.Name = c.Name.." (Dummy)"
	else
		char.Name = "non"
	end
	zz = Instance.new("Highlight",char)
	zz.FillTransparency = 1
	zz.DepthMode = Enum.HighlightDepthMode.Occluded
	zz.Enabled = false
	if not workspace:FindFirstChild("non") then
		char:SetPrimaryPartCFrame(c.HumanoidRootPart.CFrame *CFrame.new(0,0,2))
	end
	c["Body Colors"]:Clone().Parent = char
	game:GetService("Players").LocalPlayer.Character.PrimaryPart = c.Head
	char.HumanoidRootPart.Anchored = false
	for i,v in pairs(c:GetChildren()) do
		if v:IsA("Accessory") and v.Name == "Pants" then
			v:Destroy()
		end
	end
	char.Parent = workspace
	c.Parent = char
	for i,v in pairs(OxideSettings.ClientHats) do 
		local hat = game:GetService("InsertService"):LoadLocalAsset("rbxassetid://"..v)
		hat.Parent = char
		hat.Handle.CanCollide = false
		OxideSettings.ClientHats[i] = hat.Name
		w = Instance.new("Weld",hat.Handle)
		w.C0 = w.Parent:FindFirstChildOfClass("Attachment").CFrame
		w.Name = "AccessoryWeld"
		w.Part0 = hat.Handle
		a  = w.Parent:FindFirstChildOfClass("Attachment")
		if string.find(a.Name,"Left") then
			if string.find(a.Name,"Shoulder") then
				w.Part1 = char["Left Arm"]
				w.C1 =  char["Left Arm"].LeftShoulderAttachment.CFrame
			end
		elseif string.find(a.Name,"Right") then
			if string.find(a.Name,"Shoulder") then
				w.Part1 = char["Right Arm"]
				w.C1 =  char["Right Arm"].RightShoulderAttachment.CFrame;
			end
		elseif string.find(a.Name,"Left") then
			if string.find(a.Name,"Foot") then
				w.Part1 = char["Left Leg"]
				w.C1 =  char["Left Leg"].LeftFootAttachment.CFrame
			end
		elseif string.find(a.Name,"Right") then
			if string.find(a.Name,"Foot") then
				w.Part1 = char["Right Leg"]
				w.C1 =  char["Right Leg"].RightFootAttachment.CFrame
			end
		elseif string.find(a.Name,"Waist") then
			if string.find(a.Name,"Back") then
				w.Part1 = char["Torso"]
				w.C1 =  char["Torso"].WaistBackAttachment.CFrame
			end    
		elseif string.find(a.Name,"Body") then
			if string.find(a.Name,"Back") then
				w.Part1 = char["Torso"]
				w.C1 =  char["Torso"].BodyBackAttachment.CFrame
			elseif  string.find(a.Name,"Front") then
				w.Part1 = char["Torso"]
				w.C1 =  char["Torso"].BodyFrontAttachment.CFrame
			end    
		elseif string.find(a.Name,"Hat") then
			w.Part1 = char["Head"]
			w.C1 =  char["Head"].HatAttachment.CFrame 
		elseif string.find(a.Name,"FaceFront") then
			w.Part1 = char["Head"]
			w.C1 =  char["Head"].FaceFrontAttachment.CFrame 
		elseif string.find(a.Name,"FaceCenter") then
			w.Part1 = char["Head"]
			w.C1 =  char["Head"].FaceCenterAttachment.CFrame 
		elseif string.find(a.Name,"Neck") then
			w.Part1 = char["Torso"]
			w.C1 =  char["Torso"].NeckAttachment.CFrame 
		elseif string.find(a.Name,"Hair") then
			w.Part1 = char["Head"]
			w.C1 =  char["Head"].HairAttachment.CFrame 
		end
	end
	task.spawn(function()
		wait(game:GetService("Players").RespawnTime)
		if OxideSettings.ReanimatedAnimations == true then
			pcall(function()
				c.Animate.Disabled = true
				c.Animate.Disabled = false
				char.Animate:Destroy()
				c.Animate.Parent = char
				char.Animate.Disabled = true
				--char.Animate.Disabled = false
			end)
			c.Humanoid.Animator.Parent = char.Humanoid
		else 
			char.Animate:Destroy()
			c.Animate.Disabled = true
			c.Animate.Parent = char
			char.Animate.Disabled = true
			c.Humanoid.Animator.Parent = char.Humanoid
		end
		local Char = char
		local Hum = Char:FindFirstChildOfClass("Humanoid") or Char:FindFirstChildOfClass("AnimationController")
		for i,v in next, Hum:GetPlayingAnimationTracks() do
			v:Stop()
		end
	end)
end
local function redo2()
	wait(.001)
	local gay = true -- dont edit >:(
	hmode = nil
	if gay == true then
		hmode = "norm" 
	else
		hmode = "alsoo3" -- hate this guy
	end
	local c = game:GetService("Players").LocalPlayer.Character
	--game:GetService("Workspace")["Error_30363"].EyesOfTheEverWorld.Name = "Puffer Vest"
	if OxideSettings.CustomHats == false then
		Hat.Rename("rbxassetid://17374768001","","LARM")
		Hat.Rename("rbxassetid://17374768001","","RARM")
		Hat.Rename("rbxassetid://14251599953", "Tor")
		Hat.Rename("rbxassetid://18640914168","","LARM")
		Hat.Rename("rbxassetid://18640914168","","RARM")
		Hat.Rename("rbxassetid://14255544465","","LARM")
		Hat.Rename("rbxassetid://14255544465","","RARM")
		Hat.Rename("rbxassetid://13415110780", "Tor")	
		Hat.Rename("http://www.roblox.com/asset/?id=83269599235494", "Tor")
		Hat.Rename("rbxassetid://18640899481", "Tor")
		Hat.Rename("rbxassetid://89183204903931", "Tor")
		Hat.Rename("rbxassetid://14255543546","","LARM")
		Hat.Rename("rbxassetid://14255543546","","RARM")
		Hat.Rename("rbxassetid://14768664565", "Tor")
		Hat.Rename("rbxassetid://14768683674","","LARM")
		Hat.Rename("rbxassetid://14768683674","","RARM")
		Hat.Rename("rbxassetid://125975972015302", "Tor")
		Hat.Rename("rbxassetid://135650240593878","","LARM")
		Hat.Rename("rbxassetid://135650240593878","","RARM")
		pcall(function()
			c["Accessory (RLeg)"].Name = "Accessory (rightleg)"
		end)
		pcall(function()
			c["Accessory (LLegNoob)"].Name = "Accessory (LLeg)"
		end)
		pcall(function()
			c["Accessory (RLegNoob)"].Name = "Accessory (rightleg)"
		end)
		pcall(function()
			c["Accessory (LArm)"].Name = "gooblet"
		end)
		pcall(function()
			c["Accessory (RArm)"].Name = "fooblet"
		end)
		Hat.Rename("rbxassetid://79186624401216","fooblet")
		Hat.Rename("rbxassetid://70661572547971", "Tor")
		Hat.Rename("rbxassetid://136752500636691","","LARM")
		Hat.Rename("rbxassetid://136752500636691","","RARM")
		pcall(function()
			c.gooblet.Name = "fooblet"
		end)
		pcall(function()
			c.gooblet.Name = "fooblet"
		end)
		pcall(function()
			c["Accessory (LARM)"].Name = "gooblet"
		end)
		pcall(function()
			c["Accessory (RARM)"].Name = "RARM"
		end)
		pcall(function()
			c["RARM"].Name = "fooblet"
		end)
		pcall(function()
			if not c:FindFirstChild("Accessory (rightleg)") then
				c.gooblet.Name = "Accessory (rightleg)"
			end
		end)
		pcall(function()
			if not c:FindFirstChild("Accessory (LLeg)") then
				c.gooblet.Name = "Accessory (LLeg)"
			end
		end)
		pcall(function()
			c.fooblet.Name = "gooblet"
		end)
		pcall(function()
			if not c:FindFirstChild("Tor") then 
				c.ExtraNoobTorso.Name = "Tor"
			end
		end)
	else
		pcall(function()
			Hat.Rename2("rbxassetid://"..OxideSettings.CH.Torso.TextureId, "Tor",OxideSettings.CH.Torso.Name)
			Hat.Rename2("rbxassetid://"..OxideSettings.CH.LeftArm.TextureId,"gooblet",OxideSettings.CH.LeftArm.Name)
			Hat.Rename2("rbxassetid://"..OxideSettings.CH.RightArm.TextureId,"fooblet",OxideSettings.CH.RightArm.Name)
			Hat.Rename2("rbxassetid://"..OxideSettings.CH.LeftLeg.TextureId,"Accessory (LLeg)",OxideSettings.CH.LeftLeg.Name)
			Hat.Rename2("rbxassetid://"..OxideSettings.CH.RightLeg.TextureId,"Accessory (rightleg)",OxideSettings.CH.RightLeg.Name)	
			Hat.Rename2("http://www.roblox.com/asset/?id="..OxideSettings.CH.Torso.TextureId, "Tor",OxideSettings.CH.Torso.Name)
			Hat.Rename2("http://www.roblox.com/asset/?id="..OxideSettings.CH.LeftArm.TextureId,"gooblet",OxideSettings.CH.LeftArm.Name)
			Hat.Rename2("http://www.roblox.com/asset/?id="..OxideSettings.CH.RightArm.TextureId,"fooblet",OxideSettings.CH.RightArm.Name)
			Hat.Rename2("http://www.roblox.com/asset/?id="..OxideSettings.CH.LeftLeg.TextureId,"Accessory (LLeg)",OxideSettings.CH.LeftLeg.Name)
			Hat.Rename2("http://www.roblox.com/asset/?id="..OxideSettings.CH.RightLeg.TextureId,"Accessory (rightleg)",OxideSettings.CH.RightLeg.Name)	
		end)
	end

	local nria = false 
	local nlia = false 
	pcall(function()
		if c.Humanoid.RigType == Enum.HumanoidRigType.R6 then
			if c:FindFirstChild("fooblet").Handle:FindFirstChildOfClass("SpecialMesh").TextureId == "rbxassetid://18640914168" then 
				nria = true 
			end 
		elseif c.Humanoid.RigType == Enum.HumanoidRigType.R15 then
			if c:FindFirstChild("fooblet").Handle.TextureID == "rbxassetid://18640914168" then 
				nria = true 
			end 
		end 
	end)
	pcall(function()
		if c.Humanoid.RigType == Enum.HumanoidRigType.R6 then
			if c:FindFirstChild("gooblet").Handle:FindFirstChildOfClass("SpecialMesh").TextureId == "rbxassetid://18640914168" then 
				nlia = true 
			end 
		elseif c.Humanoid.RigType == Enum.HumanoidRigType.R15 then
			if c:FindFirstChild("gooblet").Handle.TextureID == "rbxassetid://18640914168" then 
				nlia = true 
			end 
		end 
	end)
	pcall(function()
		loadstring(game:HttpGet("https://raw.githubusercontent.com/Nitro-GT/OxideReanim/main/renameclones3"))()
	end)
	pcall(function()
		c["gooblet-1"].Name = "fooblet"
	end)
	local flingloop
	function waitForChild(parent, childName)
		local child = parent:findFirstChild(childName)
		if child then return child end
		while true do
			child = parent.ChildAdded:wait()
			if child.Name==childName then return child end
		end
	end
	if not workspace:FindFirstChild("non") then
		char =  workspace.Terrain.non
	else
		char = workspace.non
	end
	local oldrootcf = char.HumanoidRootPart.CFrame 
	char.HumanoidRootPart.Anchored = true 
	if c ~= char then
		_G.OxideRealChar = c
	else 
		_G.OxideRealChar = workspace[lp.Name]
	end
	speaker = game:GetService("Players").LocalPlayer
	Clip = false
	local function NoclipLoop()
		for _, child in pairs(c:GetChildren()) do
			if child:IsA("BasePart") then
				child.CanCollide = false
			end
		end
	end
	for i,v in pairs(c:GetChildren()) do
		if v:IsA("Accessory") and v.Name == "Pants" then
			v:Destroy()
		end
	end

	char.Parent = workspace
	c.Parent = char
	OxideSettings.Flinging = false
	local swordbigvel = false
	function getRoot(char)
		local rootPart = char:FindFirstChild('HumanoidRootPart') or char:FindFirstChild('Torso') 
		return rootPart
	end
	local character = game:GetService("Players").LocalPlayer.Character
	local humanoid = character:FindFirstChildOfClass("Humanoid")
	if humanoid and humanoid.SeatPart then
		humanoid.Sit = false
		wait(0.1)
	end
	local hipHeight = humanoid and humanoid.HipHeight > 0 and (humanoid.HipHeight + 1)
	local rootPart = getRoot(character)
	for i,v in pairs(c:GetChildren()) do
		if v:IsA("BasePart") then
			v.AssemblyAngularVelocity = Vector3.new(0,0,0)
			v.AssemblyLinearVelocity = Vector3.new(0,-9e9,9e9)
		end
	end
	speaker = game:GetService("Players").LocalPlayer
	for _, child in pairs(c:GetChildren()) do
		if child:IsA("Part") then
			child.Anchored = false
		elseif child:IsA("Accessory") then
			child.Handle.Anchored = true
		end
	end
	for _, v in pairs(char:GetChildren()) do
		if v:IsA("Part") then
			pcall(function()
				v.CollisionGroup = c.Head.CollisionGroup
			end)
		end
	end	
	if c.Humanoid.RigType == Enum.HumanoidRigType.R6 then
		for _,v in pairs(c:GetChildren()) do
			if v:IsA("Accessory")  and v.Name ~= "gooblet"  and v.Name ~= "Accessory (RARM)" and v.Name ~= "Accessory (LARM)" and v.Name ~= "fooblet" and v.Name ~= "Accessory (rightleg)"   and not string.find(v.Name,"Accessory (Noob") and v.Name ~= "Accessory (NoobLeftArm)"  and v.Name ~= "Accessory (NoobTorso)"  and v.Name ~= "Accessory (NoobRightArm)"  and v.Name ~= "Accessory (LLeg)" and v.Name ~= "Accessory (LARM)"  and v.Name ~= "Rarm" and v.Name ~= "funnihead"  and v.Name ~= "Larm" and v.Name ~= "RectangleFace" and v.Name ~= "BlueRobotArm" and v.Name ~= "GreyRobotArm"   and v.Name ~= "Tor" and v.Name ~= "PurpleRobotArm" and v.Name ~= "RobotArmTest"  and v.Name ~= "RectangleHead-2"  and v.Name ~= "Tor" and v.Name ~= "Accessory (LLeg)" and v.Name ~= "RARM"  and v.Name ~="Unloaded head" then
				if not char:FindFirstChild(v.Name) then
					local a = v:Clone()
					a.Handle.AccessoryWeld.Part1 = char[a.Handle.AccessoryWeld.Part1.Name]
					Accessory = v
					Handle = Accessory.Handle
					a.Parent = char
					a.Handle.Anchored = false
					a.Handle.Transparency = 1
					if a.Handle:FindFirstChild("Sparkles") then 
						a.Handle:FindFirstChild("Sparkles"):Destroy()
					end
				end
			end
		end
	else
		for _,v in pairs(c:GetChildren()) do
			if v:IsA("Accessory") and v.Name ~= "Pouch" and v.Name ~= "Scooper"    and v.Name ~= "gooblet" and v.Name ~= "fooblet" and v.Name ~= "Accessory (rightleg)"  and not string.find(v.Name,"Accessory (Noob") and v.Name ~= "Accessory (NoobLeftArm)"  and v.Name ~= "Accessory (NoobTorso)"  and v.Name ~= "Accessory (NoobRightArm)"and v.Name ~= "Accessory (LARM)"  and v.Name ~= "Rarm" and v.Name ~= "funnihead"  and v.Name ~= "Larm" and v.Name ~= "RectangleFace" and v.Name ~= "Tor" and v.Name ~= "RectangleHead-2"  and v.Name ~= "BlueRobotArm" and v.Name ~= "GreyRobotArm"   and v.Name ~= "Tor" and v.Name ~= "PurpleRobotArm" and v.Name ~= "RobotArmTest"  and v.Name ~= "Accessory (LLeg)" and v.Name ~= "RARM"  and v.Name ~="Unloaded head"  then
				if not char:FindFirstChild(v.Name) then
					local a = v:Clone()
					if a.Handle:FindFirstChild("Sparkles") then 
						a.Handle:FindFirstChild("Sparkles"):Destroy()
					end
					a.Handle:BreakJoints()
					Accessory = v
					Handle = Accessory.Handle
					z = a
					a.Parent = char
					a.Handle.Anchored = false
					a.Handle.Transparency = 1
					a.Handle.CFrame = char.HumanoidRootPart.CFrame
					a.Handle.Velocity = Vector3.new(0,0,0)
					a.Handle.Massless = true
					w = Instance.new("Weld",z.Handle)
					w.C0 = w.Parent:FindFirstChildOfClass("Attachment").CFrame
					w.Name = "AccessoryWeld"
					w.Part0 = z.Handle
					a  = w.Parent:FindFirstChildOfClass("Attachment")
					if string.find(a.Name,"Left") then
						if string.find(a.Name,"Shoulder") then
							w.Part1 = char["Left Arm"]
							w.C1 =  char["Left Arm"].LeftShoulderAttachment.CFrame
						end
					elseif string.find(a.Name,"Right") then
						if string.find(a.Name,"Shoulder") then
							w.Part1 = char["Right Arm"]
							w.C1 =  char["Right Arm"].RightShoulderAttachment.CFrame
						end
					elseif string.find(a.Name,"Left") then
						if string.find(a.Name,"Foot") then
							w.Part1 = char["Left Leg"]
							w.C1 =  char["Left Leg"].LeftFootAttachment.CFrame
						end
					elseif string.find(a.Name,"Right") then
						if string.find(a.Name,"Foot") then
							w.Part1 = char["Right Leg"]
							w.C1 =  char["Right Leg"].RightFootAttachment.CFrame
						end
					elseif string.find(a.Name,"Waist") then
						if string.find(a.Name,"Back") then
							w.Part1 = char["Torso"]
							w.C1 =  char["Torso"].WaistBackAttachment.CFrame
						elseif string.find(a.Name,"Center") then 
							w.Part1 = char["Torso"]
							w.C1 =  char["Torso"].WaistCenterAttachment.CFrame
						end    
					elseif string.find(a.Name,"Body") then
						if string.find(a.Name,"Back") then
							w.Part1 = char["Torso"]
							w.C1 =  char["Torso"].BodyBackAttachment.CFrame
						elseif  string.find(a.Name,"Front") then
							w.Part1 = char["Torso"]
							w.C1 =  char["Torso"].BodyFrontAttachment.CFrame
						end    
					elseif string.find(a.Name,"Hat") then
						w.Part1 = char["Head"]
						w.C1 =  char["Head"].HatAttachment.CFrame 
					elseif string.find(a.Name,"FaceFront") then
						w.Part1 = char["Head"]
						w.C1 =  char["Head"].FaceFrontAttachment.CFrame 
					elseif string.find(a.Name,"FaceCenter") then
						w.Part1 = char["Head"]
						w.C1 =  char["Head"].FaceCenterAttachment.CFrame 
					elseif string.find(a.Name,"Neck") then
						w.Part1 = char["Torso"]
						w.C1 =  char["Torso"].NeckAttachment.CFrame 
					elseif string.find(a.Name,"Hair") then
						w.Part1 = char["Head"]
						w.C1 =  char["Head"].HairAttachment.CFrame 
					end
				end
			end
		end
	end
	for _,v in pairs(c:GetChildren()) do
		if v:IsA("Accessory") and v.Name ~= "RectangleHead" and v.Name ~= "RectangleHead-1"  and v.Name ~= "RectangleHead-3"  and v.Name ~= "funnihead" and v.Name ~= "RectangleFace-1" and v.Name ~= "RectangleFace" and v.Name ~= "RectangleFace-2" and v.Name ~= "RectangleHead-2"     then
			v.Handle:BreakJoints()
		end
	end 
	for _,v in pairs(c:GetChildren()) do
		if v:IsA("Accessory") and v.Name == "RectangleHead" and v.Name =="Puffer Vest" and v.Name == "RectangleFace" and v.Name == "RectangleFace-2" and v.Name == "RectangleHead-2"     then
			v.Handle:BreakJoints()
		end
	end 
	if OxideSettings.Legacy == false then 
		for _, child in pairs(char:GetChildren()) do
			if child:IsA("BasePart") then
				child.Transparency = 1
			elseif child:IsA("Accessory") then
				child.Handle.Transparency = 1
			end
		end
	else	
		for _, child in pairs(char:GetChildren()) do
			if child:IsA("BasePart") and child.Name ~= "HumanoidRootPart" and child.Name ~= "Head" then
				child.Transparency = 0
			elseif child:IsA("Accessory") then
				child.Handle.Transparency = 0
			end
		end
		for _, child in pairs(c:GetDescendants()) do
			if child:IsA("BasePart") and child.Name ~= "HumanoidRootPart" then
				child.Transparency = 1
			end
		end
	end
	for i,v in tools do
		table.remove(tools,table.find(tools,v))
	end
	for i,v in pairs(lp.Backpack:GetChildren()) do 
		if v:IsA("Tool") and not string.find(v.Name,"FAKE")  then 
			pcall(function()
				v.Handle.CanCollide = false
			end)
			table.insert(tools,v)
		end 
	end
	for i,v in tools do
		pcall(function()
			v.Parent = c 
			v.Parent = lp.Backpack
			v.Parent = c 
			v.Parent = lp.Backpack
			if not char:FindFirstChild("FAKE"..v.Name) then 
				local fv = v:Clone()
				task.wait(.001)
				fv.Parent = lp.Backpack 
				local oldn = fv.Name 
				fv.Name = "FAKE"..oldn
				table.insert(faketools,fv)
				pcall(function()
					fv.Handle.Transparency = 1 
				end)
			end
			v.Handle.CFrame = char.HumanoidRootPart.CFrame *CFrame.new(0,-25,5)
		end)
	end
	pcall(function()
		c.HumanoidRootPart.Transparency = 0
	end)
	local exploit = "shitsploit"
	pcall(function()
		exploit = getexecutorname()
	end)
	task.spawn(function()
		task.wait(.01)
		for i,v in tools do
			v.Parent = c
		end
		for i,v in tools do
			v.Parent = lp.Backpack
		end
		c:BreakJoints()
		if exploit ~= "CaetSploit" then
			replicatesignal(c:FindFirstChildOfClass("Humanoid").ServerBreakJoints)
		else
			replicatesignal2(c:FindFirstChildOfClass("Humanoid"),"ServerBreakJoints")
		end
		for i,v in tools do
			v.Parent = c
		end
	end)
	local curcamcf = workspace.CurrentCamera.CFrame
	task.spawn(function()	
		task.wait(.02)
		game:GetService("Players").LocalPlayer.Character=char 
		pcall(function()
			moveloop:Disconnect()
		end)
		task.wait(.01)
		workspace.CurrentCamera.CFrame = curcamcf
	end)
	local burgermeat = false 
	local clock = os.clock
	local rad, cos, sin, random = math.rad, math.cos, math.sin, math.random
	local sin=math.sin
	local plrs = game:GetService("Players")
	if OxideSettings.ToolFling == false then
		velocity = game:GetService("RunService").Heartbeat:Connect(function()
			plrs.LocalPlayer.SimulationRadius = #plrs:GetChildren()*1000
			for i,v in pairs(c:GetChildren()) do
				if v:IsA("Accessory") or v:IsA("Tool") then
					v.Handle.AssemblyLinearVelocity = Vector3.new(char.Torso.AssemblyLinearVelocity.X*15 -(10*math.cos(os.clock()*1000))   , 28.5312+math.sin(os.clock()*1000), char.Torso.AssemblyLinearVelocity.Z*15+(3*math.sin(os.clock()*12000))) 
					v.Handle.AssemblyAngularVelocity = Vector3.new(0, sin(clock()*10), 0) + char.Torso.AssemblyAngularVelocity * 2
					v.Handle.CanCollide = false
				end
			end
		end)
	else 
		velocity = game:GetService("RunService").Heartbeat:Connect(function()
			for i,v in pairs(c:GetChildren()) do
				if v:IsA("Accessory")  then
					v.Handle.AssemblyLinearVelocity = Vector3.new(char.Torso.AssemblyLinearVelocity.X*15 -10*math.clamp(math.sin(os.clock()*1000),0.5,1)   ,30.499+math.sin(os.clock()*10000), char.Torso.AssemblyLinearVelocity.Z*15 +6) 
					v.Handle.AssemblyAngularVelocity = char.Torso.AssemblyAngularVelocity * 10
				elseif v:IsA("Tool") then 
					if burgermeat == true then
						pcall(function()
							v.Handle.AssemblyLinearVelocity = Vector3.new(9e9 -9e7, 9e9) 
							v.Handle.AssemblyAngularVelocity = Vector3.new(9e9 -9e7, 9e9) 
							v.Handle.CanCollide = false
						end)
					else 
						v.Handle.AssemblyLinearVelocity = Vector3.new(char.Torso.AssemblyLinearVelocity.X*15 -5   , 35.499+math.sin(os.clock()*100), char.Torso.AssemblyLinearVelocity.Z*15 +5) 
						v.Handle.AssemblyAngularVelocity = char.Torso.AssemblyAngularVelocity
					end
				end
			end
		end)
	end
	pcall(function()
		char["Accessory (sapphireTophatAccessory)"].Handle.AccessoryWeld.C0 = CFrame.new(0,0,0) 
		char["Accessory (sapphireTophatAccessory)"].Handle.AccessoryWeld.C1 = CFrame.new(0,0,0)*  CFrame.Angles(0,math.rad(-90),math.rad(90))
	end)
	pcall(function()
		char["SpringPixie_150381051_LC"].Handle.AccessoryWeld.Part1 = char["Torso"]
		char["SpringPixie_150381051_LC"].Handle.AccessoryWeld.C0 = CFrame.new(-0.5,0.1,0) 
		char["SpringPixie_150381051_LC"].Handle.AccessoryWeld.C1 = CFrame.new(0,0,0)*  CFrame.Angles(0,math.rad(-90),math.rad(90))
		workspace.non["SpringPixie_150381051_LC"].Handle.AccessoryWeld.C0  = workspace.non["SpringPixie_150381051_LC"].Handle.AccessoryWeld.C0* CFrame.Angles(math.rad(180),0,0)
	end)

	--wait(game:GetService("Players").RespawnTime + 0.25)  
	local removinghealth = false
	local sin = math.sin
	local plrs = game:GetService("Players")
	local antisleepMultiplier=Vector3.new(.005,.005,.005)
	OxideSettings.HeadAngle = CFrame.Angles(0,0,0)
	local hum = char:FindFirstChildOfClass("Humanoid")

	if OxideSettings.CustomHats == false then
		connect = game:GetService("RunService").Heartbeat:Connect(function(set)
			sine=os.clock
			flingpart = OxideSettings.flingpart
			pcall(function()
				if flingpart ~= nil and flingpart.Parent.Parent ~= nil then
					if flingpart.Parent:FindFirstChildOfClass("Humanoid") then
						if flingpart.Name ~= "Torso" or flingpart.Name ~= "HumanoidRootPart" or flingpart.Name ~= "Handle" then
							if flingpart.Parent:FindFirstChildOfClass("Humanoid") then
								flingpart = flingpart.Parent.HumanoidRootPart
							end
						end
					end 
				else 
					flingpart = nil
				end
			end)
			local antisleep=Vector3.new(0.005*sin(sine()*8),0.0045*sin(sine()*6),0.005*math.cos(sine()*7))
			pcall(function()
				workspace.CurrentCamera.CameraSubject = char:FindFirstChildOfClass("Humanoid")
				workspace.FallenPartsDestroyHeight = oldh 
			end)
			if c:FindFirstChild("Tor") then
				c["Tor"].Handle.CFrame = char["Torso"].CFrame   + antisleep
			end
			if c:FindFirstChild("gooblet") then
				if nlia == false then 
					c["gooblet"].Handle.CFrame = char["Left Arm"].CFrame * CFrame.Angles(math.rad(0),math.rad(0),math.rad(90))  +antisleep
				else 
					c["gooblet"].Handle.CFrame = char["Left Arm"].CFrame * CFrame.Angles(math.rad(0),math.rad(90),math.rad(0))  +antisleep
				end
			end
			if c:FindFirstChild("fooblet") then
				if nria == false then 
					c["fooblet"].Handle.CFrame = char["Right Arm"].CFrame * CFrame.Angles(math.rad(0),math.rad(0),math.rad(90))+antisleep
				else 
					c["fooblet"].Handle.CFrame = char["Right Arm"].CFrame * CFrame.Angles(math.rad(0),math.rad(90),math.rad(0))+antisleep
				end
			end
			if c:FindFirstChild("Accessory (rightleg)") then
				c["Accessory (rightleg)"].Handle.CFrame = char["Right Leg"].CFrame  * CFrame.Angles(math.rad(0),math.rad(0),math.rad(90))  +antisleep
			end
			if c:FindFirstChild("Accessory (LLeg)") then
				c["Accessory (LLeg)"].Handle.CFrame = char["Left Leg"].CFrame  * CFrame.Angles(math.rad(0),math.rad(0),math.rad(90))  +antisleep
			end

			pcall(function()
				for _,v in pairs(c:GetChildren()) do
					if v:IsA("Accessory") and v.Name ~= "gooblet"  and v.Name ~= "fooblet"  and v.Name ~= "BlueRobotArm" and not string.find(v.Name,"Accessory (Noob") and v.Name ~= "Accessory (NoobLeftArm)"  and v.Name ~= "Accessory (NoobTorso)"  and v.Name ~= "Accessory (NoobRightArm)" and v.Name ~= "GreyRobotArm"   and v.Name ~= "Tor" and v.Name ~= "PurpleRobotArm" and v.Name ~= "RobotArmTest"  and v.Name ~= "LARM" and v.Name ~= "RARM" and v.Name ~= "Accessory (rightleg)" and v.Name ~= "Accessory (LLeg)" then  
						v.Handle.CFrame = char[v.Name].Handle.CFrame +antisleep
						v.Handle.CanTouch = false
					end
				end
			end)
			pcall(function()
				for _,v in pairs(char:GetChildren()) do
					if v:IsA("Accessory") and v.Name ~= "gooblet" and not string.find(v.Name, "gooblet") and not table.find(OxideSettings.ClientHats,v.Name) and v.Name ~= "fooblet" and v.Name ~= "Black"  and v.Name ~= "Tor"  and v.Name ~= "BlueRobotArm" and v.Name ~= "GreyRobotArm"   and v.Name ~= "Tor" and v.Name ~= "PurpleRobotArm" and v.Name ~= "RobotArmTest"  and v.Name ~= "LARM" and v.Name ~= "RARM" and v.Name ~= "Accessory (rightleg)" and v.Name ~= "Accessory (LLeg)" then  
						if not c:FindFirstChild(v.Name) then 
							v.Handle.Transparency = 0.5
						end
					end
				end
				if not c:FindFirstChild("gooblet") then 
					char["Left Arm"].Transparency = 0.5
				end 
				if not c:FindFirstChild("fooblet") then 
					pcall(function()
						char["Right Arm"].Transparency = 0.5
					end)
				end 
				if not c:FindFirstChild("Accessory (rightleg)") then 
					char["Right Leg"].Transparency = 0.5
				end 
				if not c:FindFirstChild("Accessory (LLeg)") then 
					char["Left Leg"].Transparency = 0.5
				end 
				if not c:FindFirstChild("Tor") then 
					char["Torso"].Transparency = 0.5
				end 
			end)
			for _,v in pairs(c:GetChildren()) do
				if v:IsA("Accessory")   then
					v.Handle.CanCollide = false
					v.Handle:ApplyImpulseAtPosition(Vector3.one,Vector3.zero)
				end
			end

			for i,v in pairs(c:GetChildren()) do
				if v:IsA("Tool")  then
					pcall(function()
						if not char:FindFirstChild("FAKE"..v.Name) then
							v.Handle.CFrame =  CFrame.new(char.HumanoidRootPart.CFrame.X,workspace.FallenPartsDestroyHeight + 450,char.HumanoidRootPart.CFrame.Z)
						else 
							if OxideSettings.ToolFling == true then
								v.Handle.CFrame = cfAdd(flingpart.CFrame,flingpart.AssemblyLinearVelocity*(sin(sine()*15)+1))
							else 
								v.Handle.CFrame = char:FindFirstChild("FAKE"..v.Name).Handle.CFrame + antisleep  
							end
						end
					end)
				end
			end
			settings().Physics.AllowSleep = false
		end)
	else 
		connect = game:GetService("RunService").Heartbeat:Connect(function(set)
			sine=os.clock
			flingpart = OxideSettings.flingpart
			pcall(function()
				if flingpart ~= nil and flingpart.Parent.Parent ~= nil then
					if flingpart.Parent:FindFirstChildOfClass("Humanoid") then
						if flingpart.Name ~= "Torso" or flingpart.Name ~= "HumanoidRootPart" or flingpart.Name ~= "Handle" then
							if flingpart.Parent:FindFirstChildOfClass("Humanoid") then
								flingpart = flingpart.Parent.HumanoidRootPart
							end
						end
					end 
				else 
					flingpart = nil
				end
			end)
			local antisleep=Vector3.new(0.005*sin(sine()*10),0.005*sin(sine()*9),0.005*math.cos(sine()*7))
			pcall(function()
				workspace.CurrentCamera.CameraSubject = char:FindFirstChildOfClass("Humanoid")
				workspace.FallenPartsDestroyHeight = oldh 
			end)
			if c:FindFirstChild("Tor") then
				if char["Torso"]:FindFirstChildOfClass("SpecialMesh") then 
					c["Tor"].Handle.CFrame = char["Torso"].CFrame  * OxideSettings.CH.Torso.Orientation  +antisleep+ char["Torso"]:FindFirstChildOfClass("SpecialMesh").Offset
				else
					c["Tor"].Handle.CFrame = char["Torso"].CFrame  * OxideSettings.CH.Torso.Orientation  +antisleep
				end
			end
			if c:FindFirstChild("gooblet") then
				if char["Left Arm"]:FindFirstChildOfClass("SpecialMesh") then 
					c["gooblet"].Handle.CFrame = char["Left Arm"].CFrame  * OxideSettings.CH.LeftArm.Orientation  +antisleep+ char["Left Arm"]:FindFirstChildOfClass("SpecialMesh").Offset
				else
					c["gooblet"].Handle.CFrame = char["Left Arm"].CFrame  * OxideSettings.CH.LeftArm.Orientation  +antisleep
				end
			end
			if c:FindFirstChild("fooblet") then
				if char["Right Arm"]:FindFirstChildOfClass("SpecialMesh") then 
					c["fooblet"].Handle.CFrame = char["Right Arm"].CFrame  * OxideSettings.CH.RightArm.Orientation  +antisleep+ char["Right Arm"]:FindFirstChildOfClass("SpecialMesh").Offset
				else
					c["fooblet"].Handle.CFrame = char["Right Arm"].CFrame  * OxideSettings.CH.RightArm.Orientation  +antisleep
				end
			end
			if c:FindFirstChild("Accessory (rightleg)") then
				if char["Right Leg"]:FindFirstChildOfClass("SpecialMesh") then 
					c["Accessory (rightleg)"].Handle.CFrame = char["Right Leg"].CFrame  * OxideSettings.CH.RightLeg.Orientation  +antisleep+ char["Right Leg"]:FindFirstChildOfClass("SpecialMesh").Offset
				else
					c["Accessory (rightleg)"].Handle.CFrame = char["Right Leg"].CFrame  * OxideSettings.CH.RightLeg.Orientation  +antisleep
				end
			end
			if c:FindFirstChild("Accessory (LLeg)") then
				if char["Left Leg"]:FindFirstChildOfClass("SpecialMesh") then 
					c["Accessory (LLeg)"].Handle.CFrame = char["Left Leg"].CFrame  * OxideSettings.CH.LeftLeg.Orientation  +antisleep+ char["Left Leg"]:FindFirstChildOfClass("SpecialMesh").Offset
				else
					c["Accessory (LLeg)"].Handle.CFrame = char["Left Leg"].CFrame  * OxideSettings.CH.LeftLeg.Orientation  +antisleep
				end
			end
			if c:FindFirstChild(OxideSettings.CH.Head.Name) then
				if char["Head"]:FindFirstChildOfClass("SpecialMesh") then 
					c[OxideSettings.CH.Head.Name].Handle.CFrame = char["Head"].CFrame  * OxideSettings.CH.Head.Orientation  +antisleep+ char["Head"]:FindFirstChildOfClass("SpecialMesh").Offset 
				else
					c[OxideSettings.CH.Head.Name].Handle.CFrame = char["Head"].CFrame * OxideSettings.CH.Head.Orientation +antisleep
				end
			end

			pcall(function()
				for _,v in pairs(c:GetChildren()) do
					if v:IsA("Accessory") and v.Name ~= "gooblet" and v.Name ~= "fooblet"  and v.Name ~= "BlueRobotArm"  and v.Name ~= OxideSettings.CH.Head.Name  and not string.find(v.Name,"Accessory (Noob") and v.Name ~= "Accessory (NoobLeftArm)"  and v.Name ~= "Accessory (NoobTorso)"  and v.Name ~= "Accessory (NoobRightArm)" and v.Name ~= "GreyRobotArm"   and v.Name ~= "Tor" and v.Name ~= "PurpleRobotArm" and v.Name ~= "RobotArmTest"  and v.Name ~= "LARM" and v.Name ~= "RARM" and v.Name ~= "Accessory (rightleg)" and v.Name ~= "Accessory (LLeg)" then  
						if char[v.Name].Handle:FindFirstChildOfClass("SpecialMesh") then 
							v.Handle.CFrame = char[v.Name].Handle.CFrame +antisleep + char[v.Name].Handle:FindFirstChildOfClass("SpecialMesh").Offset
						else
							v.Handle.CFrame = char[v.Name].Handle.CFrame +antisleep
						end
						v.Handle.CanTouch = false
					end
				end
			end)
			pcall(function()
				for _,v in pairs(char:GetChildren()) do
					if v:IsA("Accessory") and v.Name ~= "gooblet" and not string.find(v.Name, "gooblet") and not table.find(OxideSettings.ClientHats,v.Name) and v.Name ~= "fooblet" and v.Name ~= "Black"  and v.Name ~= "Tor"  and v.Name ~= "BlueRobotArm" and v.Name ~= "GreyRobotArm"   and v.Name ~= "Tor" and v.Name ~= "PurpleRobotArm" and v.Name ~= "RobotArmTest"  and v.Name ~= "LARM" and v.Name ~= "RARM" and v.Name ~= "Accessory (rightleg)" and v.Name ~= "Accessory (LLeg)" then  
						if not c:FindFirstChild(v.Name) then 
							v.Handle.Transparency = 0.5
						end
					end
				end
				if not c:FindFirstChild("gooblet") then 
					char["Left Arm"].Transparency = 0.5
				end 
				if not c:FindFirstChild("fooblet") then 
					pcall(function()
						char["Right Arm"].Transparency = 0.5
					end)
				end 
				if not c:FindFirstChild("Accessory (rightleg)") then 
					char["Right Leg"].Transparency = 0.5
				end 
				if not c:FindFirstChild("Accessory (LLeg)") then 
					char["Left Leg"].Transparency = 0.5
				end 
				if not c:FindFirstChild("Tor") then 
					char["Torso"].Transparency = 0.5
				end 
			end)
			for _,v in pairs(c:GetChildren()) do
				if v:IsA("Accessory")   then
					v.Handle.CanCollide = false
					v.Handle:ApplyImpulseAtPosition(Vector3.one,Vector3.zero)
				end
			end
			for i,v in pairs(c:GetChildren()) do
				if v:IsA("Tool")  then
					pcall(function()
						if not char:FindFirstChild("FAKE"..v.Name) then
							v.Handle.CFrame =  CFrame.new(char.HumanoidRootPart.CFrame.X,workspace.FallenPartsDestroyHeight + 450,char.HumanoidRootPart.CFrame.Z)
						else 
							if OxideSettings.ToolFling == true then
								v.Handle.CFrame = cfAdd(flingpart.CFrame,flingpart.AssemblyLinearVelocity*(sin(sine()*15)+1))
							else 
								v.Handle.CFrame = char:FindFirstChild("FAKE"..v.Name).Handle.CFrame + antisleep  
							end
						end
					end)
				end
			end
			settings().Physics.AllowSleep = false
		end)
	end
	local qr = 0
	task.spawn(function()
		task.wait(.05)
		qr = qr + .05
	end)
	char:FindFirstChildOfClass("Humanoid").Died:Connect(function()
		stopped = true
		OxideSettings.Stopped = true
		respawnloop:Disconnect()
		for i,v in pairs(char:GetChildren()) do 
			if v:IsA("Accessory") then
				v.Handle.CanCollide = true
				v.Handle:ApplyImpulse(v.Handle.CFrame.LookVector * 5)
			end 
		end
		replicatesignal(game:GetService("Players").LocalPlayer.ConnectDiedSignalBackend)
		task.wait(game:GetService("Players").RespawnTime - qr)
		connect:Disconnect()
		char:Destroy()
		velocity:Disconnect()
	end)
	settings().Physics.AllowSleep = false
	for _, child in pairs(c:GetChildren()) do
		if child:IsA("Part") then
			child.Anchored = false
		elseif child:IsA("Accessory") then
			child.Handle.Anchored = false
		end
	end
	local n = 0
	task.spawn(function()
		task.wait(1.5)
		burgermeat = true 
	end)
	local haslosthat = false
	removedl = c.ChildRemoved:Connect(function(v)
		if OxideSettings.Refit == true then
			if v:IsA("Accessory") and haslosthat == false then
				haslosthat = true
				respawnfunc()
			end
		end
	end)
	char.HumanoidRootPart.Anchored = false 
	task.wait(.25)
	char.HumanoidRootPart.CFrame= oldrootcf 
	char.HumanoidRootPart.Velocity = Vector3.zero 
end
redo()
replicatesignal(game:GetService("Players").LocalPlayer.ConnectDiedSignalBackend)
task.wait(game:GetService("Players").RespawnTime)
plr.Character:WaitForChild("HumanoidRootPart").CFrame =CFrame.new( workspace.non.HumanoidRootPart.CFrame.X + 2 , workspace.FallenPartsDestroyHeight + 300, workspace.non.HumanoidRootPart.CFrame.Z  ) 
task.wait(.05)
redo2()
game:GetService("StarterGui"):SetCore("SendNotification", {
	Title = "Oxide Reanimation V3.7  - Respawn Time";
	Duration = 20;
	Text = "Refit will take roughly "..(game:GetService("Players").RespawnTime*2).." seconds."
})
local sin=math.sin
local oldh = workspace.FallenPartsDestroyHeight
local seatdebounce = 3 
local cansit = true 
char:FindFirstChild("Left Leg").Touched:Connect(function(p)
	if p:IsA("Seat") and cansit == true then 
		local sw = Instance.new("Weld",p)
		sw.Name = "SeatWeld"
		sw.Part0 = p 
		sw.Part1 = char:FindFirstChild("HumanoidRootPart")
		sw.C0 = CFrame.new(0, 0.2, 0, 1, 0, -0, 0, 0, 1, 0, -1, 0)
		sw.C1 = CFrame.new(0, -1.5, 0, 1, 0, -0, 0, 0, 1, 0, -1, 0)
		char:FindFirstChildOfClass("Humanoid").Sit = true
		char:FindFirstChildOfClass("Humanoid").Jumping:Wait()
		sw:Destroy()
		char:FindFirstChildOfClass("Humanoid").Sit = false 
		cansit = false
		task.spawn(function()
			task.wait(seatdebounce)
			cansit = true 
		end)
	end
end)
respawnloop = plr.CharacterAdded:Connect(function(re)
	if re ~= char then
		if OxideSettings.HatCollide == false then 
			repeat wait() until re:FindFirstChildOfClass("Humanoid")
			moveloop = game:GetService("RunService").Heartbeat:Connect(function()
				char:FindFirstChildOfClass("Humanoid"):Move(re:FindFirstChildOfClass("Humanoid").MoveDirection)   
			end)
		end
		task.wait(.01)
		pcall(function()
			workspace.CurrentCamera.CFrame = curcamcf
		end)
		replicatesignal(game:GetService("Players").LocalPlayer.ConnectDiedSignalBackend)
		task.wait(game:GetService("Players").RespawnTime)
		if  OxideSettings.ToolFling == true then 
			OxideSettings.Fling = false 
		end
		for i,v in pairs(lp.Backpack:GetDescendants()) do 
			if v:IsA("Sound") and v:FindFirstAncestorOfClass("Tool") then 
				v.Volume = 0 
			end 
		end
		if OxideSettings.HatCollide == false then
			repeat wait() until plr.Character:FindFirstChild("Head")
			workspace.CurrentCamera.CameraSubject = workspace.non:FindFirstChild("Humanoid")
			repeat wait() until plr.Character:FindFirstChildOfClass("Accessory")
		end
		if OxideSettings.HideCharacter == false then
			if plr.Character.Name ~= "non" then
				if workspace:FindFirstChild("non") then
					workspace.CurrentCamera.CameraSubject = workspace.non:FindFirstChild("Humanoid")
					if plr.Character.Name ~= "non" then
						plr.Character.HumanoidRootPart.CFrame = CFrame.new( workspace.non.HumanoidRootPart.CFrame.X +5 , workspace.non.HumanoidRootPart.CFrame.Y, workspace.non.HumanoidRootPart.CFrame.Z +5) 
					end
					task.wait(.005)
					redo2()
				else
					workspace.CurrentCamera.CameraSubject = workspace.Terrain.non:FindFirstChildOfClass("Humanoid")
					if plr.Character.Name ~= "non" then
						plr.Character.HumanoidRootPart.CFrame = CFrame.new( workspace.Terrain.non.HumanoidRootPart.CFrame.X +5 , workspace.Terrain.non.HumanoidRootPart.CFrame.Y, workspace.Terrain.non.HumanoidRootPart.CFrame.Z +5) 
					end
					task.wait(.005)
					redo2()
				end
			end
		else
			workspace.CurrentCamera.CameraSubject = workspace.non:FindFirstChild("Humanoid")
			local flingloop
			local c = re
			if OxideSettings.FlingEnabled == true and OxideSettings.ToolFling == false and OxideSettings.HatCollide == false then 
				if OxideSettings.Fling == true  and OxideSettings.ToolFling == false then
					local flingpart = OxideSettings.flingpart
					local sineee=os.clock()
					if flingpart ~= nil then
						if flingpart.Parent:FindFirstChildOfClass("Humanoid") or flingpart:FindFirstChildOfClass("Humanoid") then
							c.Humanoid:ChangeState(16)
							if flingpart.Name ~= "Torso" or flingpart.Name ~= "HumanoidRootPart" or flingpart.Name ~= "Handle" then
								if flingpart.Parent:FindFirstChildOfClass("Humanoid") then
									flingpart = flingpart.Parent.HumanoidRootPart
								elseif flingpart:IsA("Model") then
									flingpart = flingpart.HumanoidRootPart
									OxideSettings.flingplr = tostring(flingpart:FindFirstChildOfClass("Humanoid").DisplayName.." (@"..flingpart.Parent.Name..")")
								end
							end
							flingloop = game:GetService("RunService").Heartbeat:Connect(function()
								sineee=os.clock()
								pcall(function()
									if flingpart:IsA("Part") then 
										c.HumanoidRootPart.CFrame = cfAdd(flingpart.CFrame,flingpart.AssemblyLinearVelocity*(sin(sineee*15)+1))
									end
									c.HumanoidRootPart.Velocity = Vector3.new(9e9,-9e7,9e9)
								end)
							end)
							local n = 0
							workspace.FallenPartsDestroyHeight = 0/0
							repeat 
								wait(.05)
								n=n+.05
							until  flingpart.AssemblyLinearVelocity.X <= 3500 and n >= .5 or n >= 1
							game:GetService("StarterGui"):SetCore("SendNotification", {
								Title = "Oxide Reanimation V3.7  - Fling:";
								Duration = 5;
								Text = "Successfully flung: "..OxideSettings.flingplr.." in: "..n.." seconds!"
							})
							flingloop:Disconnect()
							workspace.FallenPartsDestroyHeight = oldh
							for i,v in pairs(c:GetDescendants()) do
								if v:IsA("BasePart") then
									v.AssemblyAngularVelocity = Vector3.new(0,0,0)
									v.AssemblyLinearVelocity = Vector3.new(0,0,0)
								end
							end
						end
					end
					OxideSettings.Fling =false
				end
			end
			for i,v in pairs(c:GetDescendants()) do
				if v:IsA("BasePart") then
					v.AssemblyAngularVelocity = Vector3.new(0,0,0)
					v.AssemblyLinearVelocity = Vector3.new(0,0,0)
				end
			end
		end
		if plr.Character.Name ~= "non" then
			if plr.Character.Name ~= "non" then
				if OxideSettings.TeleportCharacter == true then
					if OxideSettings.HatCollide == false then
						plr.Character:WaitForChild("HumanoidRootPart").CFrame =CFrame.new( workspace.non.HumanoidRootPart.CFrame.X + 45 , workspace.FallenPartsDestroyHeight + 300, workspace.non.HumanoidRootPart.CFrame.Z  ) 
					else 
						plr.Character:WaitForChild("HumanoidRootPart").CFrame =CFrame.new( workspace.non.HumanoidRootPart.CFrame.X + 45 , workspace.FallenPartsDestroyHeight + 300, workspace.non.HumanoidRootPart.CFrame.Z  ) 
					end
				end
				local c =plr.Character
				if c.Name ~= "non" then
					if OxideSettings.HatCollide == true then
						c:BreakJoints()
						c:WaitForChild("Humanoid").Health = 0		
						repeat task.wait() until c:FindFirstChildOfClass("Accessory") or not c:IsDescendantOf(workspace)
					end
				end
				if OxideSettings.HatCollide == false then
					task.wait(.005)
				else 
					task.wait(.0025)
				end
				workspace.CurrentCamera.CameraSubject = workspace.non:FindFirstChild("Humanoid")
				redo2()
				task.wait(game:GetService("Players").RespawnTime/3)
				if lp.Character ~= workspace.non then 
					moveloop:Disconnect()
					lp.Character:BreakJoints()
					task.wait(.15)
					lp.Character = workspace.non
				end
			end
		end
	end
end)
local flingtable= {}
getgenv().attackuno= function(part)
	task.spawn(function()
		if OxideSettings.FlingEnabled == true and stopped == false then
			flingpos = game:GetService("Players").LocalPlayer:GetMouse().Hit
			flingpart = part
			OxideSettings.flingplr = nil
			if flingpart.Parent ~= char then
				if flingpart.Parent:FindFirstChildOfClass("Humanoid") then
					OxideSettings.flingpart = flingpart
					OxideSettings.flingplr = tostring(flingpart.Parent:FindFirstChildOfClass("Humanoid").DisplayName.." (@"..flingpart.Parent.Name..")")
					game:GetService("StarterGui"):SetCore("SendNotification", {
						Title = "Oxide Reanimation V3.7  - Fling:";
						Duration = 3;
						Text = "Locked onto player: "..flingpart.Parent:FindFirstChildOfClass("Humanoid").DisplayName.." (@"..flingpart.Parent.Name..")"
					})
					if OxideSettings.ToolFling == true then
						OxideSettings.Fling = false
						if faketools[1] ~= nil then 
							faketools[1].Parent = char
						end
						task.wait(2.5)
						if faketools[1] ~= nil then 
							faketools[1].Parent = game:GetService("Players").LocalPlayer.Backpack
						end
						OxideSettings.Fling = false 
					else 
						OxideSettings.Fling = true
					end
				elseif flingpart:FindFirstChildOfClass("Humanoid") then 
					if not table.find(flingtable,flingpart) then
						table.insert(flingtable,flingpart)
						OxideSettings.flingpart = flingpart:FindFirstChild("HumanoidRootPart")
						OxideSettings.flingplr = tostring(flingpart:FindFirstChildOfClass("Humanoid").DisplayName.." (@"..flingpart.Name..")")
						game:GetService("StarterGui"):SetCore("SendNotification", {
							Title = "Oxide Reanimation V3.7  - Fling:";
							Duration = 3;
							Text = "Locked onto player: "..flingpart:FindFirstChildOfClass("Humanoid").DisplayName.." (@"..flingpart.Name..")"
						})
						OxideSettings.Fling = true
						if OxideSettings.ToolFling == true then
							q=next(flingtable)
							if q then
								for i,v in next,table.clone(flingtable) do
									OxideSettings.flingpart = v:FindFirstChild("HumanoidRootPart")
									print(OxideSettings.flingpart)
									OxideSettings.Fling = false
									if faketools[1] ~= nil then 
										faketools[1].Parent = char
									end
									task.wait(2.5)
									OxideSettings.Fling = false
									flingtable[i] = nil
								end
								if faketools[1] ~= nil then 
									faketools[1].Parent = game:GetService("Players").LocalPlayer.Backpack
								end
							end
						else 
							OxideSettings.Fling = true
						end
					end
				else
					print("not a player")
					OxideSettings.Fling = false
				end
			end
		end
	end)
	print(OxideSettings.Fling)
end
if OxideSettings.AntiFling == true then 
	local speaker = game:GetService("Players").LocalPlayer
	local Players = game:GetService("Players")
	local RunService = game:GetService("RunService")
	antifling = RunService.Stepped:Connect(function()
		for _, player in pairs(Players:GetPlayers()) do
			if player ~= speaker and player.Character then
				for _, v in pairs(player.Character:GetDescendants()) do
					if v:IsA("BasePart") then
						v.CanCollide = false
					end
				end
			end
		end
	end)
end
if OxideSettings.noclip == true then 
	local speaker = game:GetService("Players").LocalPlayer
	local Players = game:GetService("Players")
	local RunService = game:GetService("RunService")
	noclip = RunService.Stepped:Connect(function()
		for _, v in pairs(char:GetChildren()) do
			if v:IsA("BasePart") then
				v.CanCollide = false
			end
		end
	end)
end
local Mouse = game:GetService("Players").LocalPlayer:GetMouse()
Mouse.Button1Down:Connect(function()
	if OxideSettings.FlingEnabled == true and stopped == false and OxideSettings.ClickFling == true then
		attackuno(Mouse.Target)
	end
end)
local uis = game:GetService("UserInputService")
uis.InputBegan:Connect(function(k,chatting)
	if chatting then return end
	if k.KeyCode == Enum.KeyCode.Minus then 
		respawnfunc()
	end
end) 
OxideFakeChar:ScaleTo(OxideSettings.Scale)
OxideRealChar:ScaleTo(1)
