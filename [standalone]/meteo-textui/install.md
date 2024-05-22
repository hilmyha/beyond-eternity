- Go to qb-core/client/drawtext.lua
- replace the all thing with above code.
- image example - https://media.discordapp.net/attachments/1092459678614700195/1198535688010858506/image.png

local function hideText()
    exports['meteo-textui']:Close()
end

local function drawText(text, position)
    exports['meteo-textui']:Show(text)
end

local function changeText(text, position)
    if type(position) ~= "string" then position = "left" end

    SendNUIMessage({
        action = 'CHANGE_TEXT',
        data = {
            text = text,
            position = position
        }
    })
end

local function keyPressed()
    exports['meteo-textui']:Close()
end

RegisterNetEvent('qb-core:client:DrawText', function(text, position)
    drawText(text, position)
end)

RegisterNetEvent('qb-core:client:ChangeText', function(text, position)
    changeText(text, position)
end)

RegisterNetEvent('qb-core:client:HideText', function()
    hideText()
end)

RegisterNetEvent('qb-core:client:KeyPressed', function()
    keyPressed()
end)

exports('DrawText', drawText)
exports('ChangeText', changeText)
exports('HideText', hideText)
exports('KeyPressed', keyPressed)