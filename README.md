# radialmenu
### Depency
[Polyzonehelper](https://github.com/bashenga/polyzonehelper)

### It is not my own script. I don't know the author of the script, i just edited and set ready for QBFramework #######

You need [Polyzonehelper](https://github.com/nerohiro/nh-context) for interact with garage as I did in this video: https://streamable.com/ev3r03

### WARNING: There is no query whether the vehicle is outside or inside in the code below

save your current qb-garages\SharedConfig.lua first then change Garages table with this:
```
Garages = {
    ["motelgarage"] = {
        label = "Motel Parking",
        takeVehicle = vector3(273.43, -343.99, 44.91),
        spawnPoint = vector4(270.94, -342.96, 43.97, 161.5),
        putVehicle = vector3(276.69, -339.85, 44.91),
        isHouse = false,
        polyzone = vector3(281.57, -334.3, 45.05),
        polyzone1 = 28,
        polyzone2 = 38,
    },
    ["sapcounsel"] = {
        label = "San Andreas Parking",
        takeVehicle = vector3(-330.01, -780.33, 33.96),
        spawnPoint = vector4(-334.44, -780.75, 33.96, 137.5),
        putVehicle = vector3(-336.31, -774.93, 33.96),
        polyzone = vector3(-334.57, -779.09, 33.97),
        polyzone1 = 10,
        polyzone2 = 20,
        
    },
    ["spanishave"] = {
        label = "Spanish Ave Parking",
        takeVehicle = vector3(-1160.86, -741.41, 19.63),
        spawnPoint = vector4(-1163.88, -749.32, 18.42, 35.5),
        putVehicle = vector3(-1147.58, -738.11, 19.31),
        polyzone = vector3(-1136.49, -752.04, 19.46),
        polyzone1 = 13.8,
        polyzone2 = 31.8,
    },
    ["caears24"] = {
        label = "Caears 24 Parking",
        takeVehicle = vector3(69.84, 12.6, 68.96),
        spawnPoint = vector4(73.21, 10.72, 68.83, 163.5),
        putVehicle = vector3(65.43, 21.19, 69.47),
        polyzone = vector3(59.41, 18.12, 69.64),
        polyzone1 = 13.6,
        polyzone2 = 7.0,
    },
    ["caears242"] = {
        label = "Caears 24 Parking",
        takeVehicle = vector3(-475.31, -818.73, 30.46),
        spawnPoint = vector4(-472.03, -815.47, 30.5, 177.5),
        putVehicle = vector3(-453.6, -817.08, 30.61),
        polyzone = vector3(-460.74, -805.67, 30.54),
        polyzone1 = 26.6,
        polyzone2 = 40.2,
    },
    ["lagunapi"] = {
        label = "Laguna Parking",
        takeVehicle = vector3(364.37, 297.83, 103.49),
        spawnPoint = vector4(367.49, 297.71, 103.43, 340.5),
        putVehicle = vector3(363.04, 283.51, 103.38),
        polyzone = vector3(374.51, 279.85, 103.37),
        polyzone1 = 41.0, 
        polyzone2 = 35.0,
    },
    ["airportp"] = {
        label = "Airport Parking",
        takeVehicle = vector3(-796.86, -2024.85, 8.88),
        spawnPoint = vector4(-800.41, -2016.53, 9.32, 48.5),
        putVehicle = vector3(-804.84, -2023.21, 9.16),
        polyzone = vector3(-767.62, -2017.96, 8.88),
        polyzone1 = 7.2, 
        polyzone2 = 24.8,
    },
    ["beachp"] = {
        label = "Beach Parking",
        takeVehicle = vector3(-1183.1, -1511.11, 4.36),
        spawnPoint = vector4(-1181.0, -1505.98, 4.37, 214.5),
        putVehicle = vector3(-1176.81, -1498.63, 4.37),
        polyzone = vector3(-1191.59, -1486.91, 4.38),
        polyzone1 = 33.2, 
        polyzone2 = 25.6,
    },
    ["themotorhotel"] = {
        label = "The Motor Hotel Parking",
        takeVehicle = vector3(1137.77, 2663.54, 37.9),            
        spawnPoint = vector4(1137.69, 2673.61, 37.9, 359.5),      
        putVehicle = vector3(1137.75, 2652.95, 37.9),
        polyzone = vector3(1122.85, 2652.25, 38.0),
        polyzone1 = 15.8, 
        polyzone2 = 28.4,
    },
    ["shoreparking"] = {
        label = "Shore Parking",
        takeVehicle = vector3(1726.21, 3707.16, 34.17),
        spawnPoint = vector4(1730.31, 3711.07, 34.2, 20.5),
        putVehicle = vector3(1737.13, 3718.91, 34.04),
        polyzone = vector3(1724.79, 3715.02, 34.23),
        polyzone1 = 10,
        polyzone2 = 10,
    },
    ["haanparking"] = {
        label = "Bell Farms Parking",
        takeVehicle = vector3(78.34, 6418.74, 31.28),
        spawnPoint = vector4(70.71, 6425.16, 30.92, 68.5), 
        putVehicle = vector3(85.3, 6427.52, 31.33),
        polyzone = vector3(69.67, 6399.09, 31.23),
        polyzone1 = 26.0,
        polyzone2 = 20,
    },
    ["pillboxgarage"] = {
        label = "Pillbox Garage Parking",
        takeVehicle = vector3(215.9499, -809.698, 30.731),
        spawnPoint = vector4(234.1942, -787.066, 30.193, 159.6),
        putVehicle = vector3(218.0894, -781.370, 30.389),
        polyzone = vector3(229.4, -790.28, 30.64),
        polyzone1 = 50.0, 
        polyzone2 = 42.6,
    },
}
```

add this to your qb-garages\server\server.lua :

```
RegisterServerEvent("qb-garages:list_vehicles")
AddEventHandler("qb-garages:list_vehicles",function()
    local src = source
    local user = QBCore.Functions.GetPlayer(src)
    local cunt = user.PlayerData
    local citizenid = cunt.citizenid
    local vehicle = vehicle
    local name = name
    if not citizenid then return end
    exports.ghmattimysql:execute("SELECT * FROM player_vehicles WHERE citizenid = @citizenid", {['citizenid'] = citizenid}, function(vehcheck)
        if vehcheck ~= nil then        
            for i = 1, #vehcheck do
                local vehname = vehcheck[i].vehicle:upper()
                local plate = vehcheck[i].plate
                TriggerClientEvent('nh-context:sendMenu', src, {
                    {
                        id = i,
                        header = "Name: " ..vehname,
                        txt = "PLATE: " .. plate,
                        params = {
                            event = "qb-garages:takeoutveh",
                            args = {
                                vehicle = vehcheck[i]
                            }
                        }
                    },
                })
            end
        end
	end)
end)
```
and add these last things in your qb-garages\client\client.lua

```
RegisterNetEvent('qb-garages:putingarage')
AddEventHandler('qb-garages:putingarage', function()
    local ped = PlayerPedId()
    coordA = GetEntityCoords(ped, 1)
    coordB = GetOffsetFromEntityInWorldCoords(ped, 0.0, 100.0, 0.0)
    curVeh = getVehicleInDirection(coordA, coordB)
    local plate = GetVehicleNumberPlateText(curVeh)
    QBCore.Functions.TriggerCallback('qb-garage:server:checkVehicleOwner', function(owned)
        Citizen.Wait(1000)
        if owned then
            local bodyDamage = math.ceil(GetVehicleBodyHealth(curVeh))
            local engineDamage = math.ceil(GetVehicleEngineHealth(curVeh))
            local totalFuel = exports['LegacyFuel']:GetFuel(curVeh)
            local passenger = GetVehicleMaxNumberOfPassengers(curVeh)
            CheckPlayers(curVeh)
            TriggerServerEvent('qb-garage:server:updateVehicleStatus', totalFuel, engineDamage, bodyDamage, plate, k)
            TriggerServerEvent('qb-garage:server:updateVehicleState', 1, plate, k)
            QBCore.Functions.DeleteVehicle(curVeh)
            if plate ~= nil then
                OutsideVehicles[plate] = veh
                TriggerServerEvent('qb-garages:server:UpdateOutsideVehicles', OutsideVehicles)
            end
            QBCore.Functions.Notify("Vehicle Parked In", "primary", 4500)
        else
            QBCore.Functions.Notify("Nobody owns this vehicle", "error", 3500)
        end
    end, plate)
end)

RegisterNetEvent('qb-garages:takeout')
AddEventHandler('qb-garages:takeout', function()
    TriggerServerEvent('qb-garages:list_vehicles')
end)


RegisterNetEvent('qb-garages:takeoutveh')
AddEventHandler('qb-garages:takeoutveh', function(type)
    for k, v in pairs(type) do
        enginePercent = round(v.engine / 10, 0)
        bodyPercent = round(v.body / 10, 0)
        currentFuel = v.fuel
            
        local ped = PlayerPedId()
        local coords = GetEntityCoords(ped)
        local heading = GetEntityHeading(ped)
        local forward = GetEntityForwardVector(PlayerPedId())
        print(forward)
        local x, y, z = table.unpack(coords + forward)
        local spawnpoint = vector4(x, y, z, heading-85)
        Citizen.Wait(1000)
        QBCore.Functions.SpawnVehicle(v.vehicle, function(veh)
            QBCore.Functions.TriggerCallback('qb-garage:server:GetVehicleProperties', function(properties)
                if v.plate ~= nil then
                    OutsideVehicles[v.plate] = veh
                    TriggerServerEvent('qb-garages:server:UpdateOutsideVehicles', OutsideVehicles)
                end
                QBCore.Functions.SetVehicleProperties(veh, properties)
                SetVehicleNumberPlateText(veh, v.plate)
                --SetEntityHeading(veh, heading)
                exports['LegacyFuel']:SetFuel(veh, v.fuel)
                doCarDamage(veh, v)
                SetEntityAsMissionEntity(veh, true, true)
                TriggerServerEvent('qb-garage:server:updateVehicleState', 0, v.plate, v.garage)
                QBCore.Functions.Notify("Vehicle Off:Engine " .. enginePercent .. "% Body: " .. bodyPercent.. "% Fuel: "..currentFuel.. "%", "primary", 4500)
                TriggerEvent("vehiclekeys:client:SetOwner", GetVehicleNumberPlateText(veh))
                SetVehicleEngineOn(veh, false, false)
            end, v.plate)
        end, spawnpoint, true)
    end
end)

function getVehicleInDirection(coordFrom, coordTo)
	local offset = 0
	local rayHandle
	local vehicle
	for i = 0, 100 do
		rayHandle = CastRayPointToPoint(coordFrom.x, coordFrom.y, coordFrom.z, coordTo.x, coordTo.y, coordTo.z + offset, 10, PlayerPedId(), 0)	
		a, b, c, d, vehicle = GetRaycastResult(rayHandle)
		offset = offset - 1
		if vehicle ~= 0 then break end
	end
	local distance = Vdist2(coordFrom, GetEntityCoords(vehicle))
	if distance > 25 then vehicle = nil end
    return vehicle ~= nil and vehicle or 0
end
```

