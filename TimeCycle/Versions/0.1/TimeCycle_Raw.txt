--[[
	
	*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-
	TimeCycle Script By ImmaBeastX
	This script is open source, 
	however please place the below in the place's description.
	
		This Place Uses TimeCycle By ImmaBeastX	
			
	Thanks,
	~ImmaBeastX
	*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-
	
--]]

print ('TimeCycle By ImmaBeastX')
MissingLF = false
local LightingName = "LightingFake"         -- Name Of Game.(Lighting Object).TimeOfDay
local speed = "0.1"                       -- How Fast Do You want a minte to last in seconds?

function hint(m)
	wait(0.5)
	MH = Instance.new("Hint")
	MH.Parent = game.Workspace
	MH.Text = "[TimeCycle]:  "..m
	wait(3)
	if MH ~= nil then
		MH:remove()
	end
end

function printT(s)
	hint(s)
	print(s)
end

function getReq()
	Lchildren = game:GetChildren()
	findLighting = game:FindFirstChild(LightingName)
	if findLighting == nil then
		printT("[Warning]: Could Not Find Lighting Named: ("..LightingName..")!")
		for i = 1, #Lchildren do
			if MissingLF == false then
    			if (Lchildren[i].ClassName)=="Lighting" then
					OldLName = LightingName
					LightingName = Lchildren[i].Name
					printT("[Fixed]: Lighting Name ("..OldLName.."), to ("..LightingName..")!")
					MissingLF = true
				else
					print(Lchildren[i].Name)
				end
			end
		end
	end
	
end

function timeloop()
	hint('Script By ImmaBeastX Loaded,   Enjoy!)')
	print('TimeCycle Loaded Version: 1.0')
	Lighting = game:FindFirstChild(LightingName)
	X = 0
	while true do
		X = X+1
		CMinute = ("00:"..X..":00")
		if Lighting.TimeOfDay == "01:00:00" then
			printT("It Is Now Midnight!")
			Lighting.TimeOfDay = ("00:"..X..":01")
		end
		if Lighting.TimeOfDay == "12:00:00" then
			printT("It Is Now 12AM!")
			Lighting.TimeOfDay = ("00:"..X..":01")
		end
		Lighting.TimeOfDay = CMinute
		wait(speed)
	end
end
getReq()
repeat 
	wait(1)
until MissingLF == true
timeloop()