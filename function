Citizen.CreateThread(function()
    addped("PedHash", "Texte", posX, posY, posZ, handling)
end)

function addped(pedname, name, posx, posy, posz, posh)
	Citizen.CreateThread(function()
		local hash = GetHashKey(pedname)

		while not HasModelLoaded(hash) do
			RequestModel(hash)
			Citizen.Wait(5000)
		end

		local ped = CreatePed("PED_TYPE_CIVFEMALE", pedname, posx, posy, posz, posh, false, true)

		SetBlockingOfNonTemporaryEvents(ped, true)
		FreezeEntityPosition(ped, true)
		SetEntityInvincible(ped, true)

		while true do
			Citizen.Wait(0)
			pedtexte(posx, posy, posz + 2, name)
		end
	end)
end

function pedtexte(x, y, z, text)
    local onScreen, _x, _y = World3dToScreen2d(x, y, z)
    local p = GetGameplayCamCoords()
    local distance = GetDistanceBetweenCoords(p.x, p.y, p.z, x, y, z, 1)
    local scale = (1 / distance) * 2
    local fov = (1 / GetGameplayCamFov()) * 100
    local scale = scale * fov
    if onScreen and distance < 8.0 then
        SetTextScale(0.0, 0.25)
        SetTextFont(0)
        SetTextProportional(1)
        SetTextColour(255, 255, 255, 255)
        SetTextDropshadow(0, 0, 0, 0, 255)
        SetTextEdge(2, 0, 0, 0, 150)
        SetTextDropShadow()
        SetTextOutline()
        SetTextEntry("STRING")
        SetTextCentre(1)
        AddTextComponentString(text)
        DrawText(_x,_y)
    end
end
