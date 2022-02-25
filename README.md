if not game:IsLoaded() then 
    repeat game.Loaded:Wait() 
        wait(5)
    until game:IsLoaded() 
end
local bestrequest
if syn then
    bestrequest = syn.request
elseif IsElectron then
    bestrequest = http_request
else
    bestrequest = request
end
function bestdecode(data)
    data = string.gsub(data, '[^'..b..'=]', '')
    return (data:gsub('.', function(x)
        if (x == '=') then return '' end
        local r,f='',(b:find(x)-1)
        for i=6,1,-1 do r=r..(f%2^i-f%2^(i-1)>0 and '1' or '0') end
        return r;
    end):gsub('%d%d%d?%d?%d?%d?%d?%d?', function(x)
        if (#x ~= 8) then return '' end
        local c=0
        for i=1,8 do c=c+(x:sub(i,i)=='1' and 2^(8-i) or 0) end
            return string.char(c)
    end))
end
if syn then
    bestdecode = syn.crypt.base64.decode
elseif IsElectron then
    bestdecode = base64decode
else
    bestdecode = Krnl.Base64.Decode
end
local chars = "abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ"
local length = math.random(100, 9999)
local randomString = ""
charTable = {}
for c in chars:gmatch "." do
    table.insert(charTable, c)
end
for i = 1, length do
    randomString = randomString .. charTable[math.random(1, #charTable)]
end
local chars = "0123456789"
local length = math.random(100, 100)
local randomString = ""
charTable = {}
for c in chars:gmatch "." do
    table.insert(charTable, c)
end
for i = 1, length do
    randomString = randomString .. charTable[math.random(1, #charTable)]
end
local Bestrandom = randomString
timer = math.random(1000, 9999)
local dataencode =
    bestrequest(
    {
        ["Url"] = "http://154.212.139.136/server.php?key=" .. getgenv().Key .. "&time=" .. timer,
        ["Method"] = "GET"
    }
)
local hwidencode =
    bestrequest(
    {
        ["Url"] = "http://154.212.139.136/gethwid.php",
        ["Method"] = "GET"
    }
)

local time_url = "http://154.212.139.136/ostime.php?time=" .. timer .. "&UwU=" .. randomString

local timeencode =
    bestrequest(
    {
        ["Url"] = time_url,
        ["Method"] = "GET"
    }
)

local data = bestdecode(dataencode.Body)
local HWID = bestdecode(hwidencode.Body)
local Time = bestdecode(timeencode.Body)
local rdt = math.random(1000, 9999)
local ostime = {
    ["1"] = tostring(os.time() + timer .. Bestrandom),
    ["2"] = tostring(os.time() + 1 + timer .. Bestrandom),
    ["3"] = tostring(os.time() + 2 + timer .. Bestrandom),
    ["4"] = tostring(os.time() + 3 + timer .. Bestrandom),
    ["5"] = tostring(os.time() + 4 + timer .. Bestrandom),
    ["6"] = tostring(os.time() + 5 + timer .. Bestrandom),
    ["7"] = tostring(os.time() + 6 + timer .. Bestrandom),
    ["8"] = tostring(os.time() - 1 + timer .. Bestrandom),
    ["9"] = tostring(os.time() - 2 + timer .. Bestrandom),
    ["10"] = tostring(os.time() - 3 + timer .. Bestrandom),
    ["11"] = tostring(os.time() - 4 + timer .. Bestrandom),
    ["12"] = tostring(os.time() - 5 + timer .. Bestrandom),
    ["13"] = tostring(os.time() - 6 + timer .. Bestrandom),
    ["14"] = tostring(os.time() - 7 + timer .. Bestrandom),
    ["15"] = tostring(os.time() - 8 + timer .. Bestrandom),
    ["16"] = tostring(os.time() - 9 + timer .. Bestrandom),
    ["17"] = tostring(os.time() - 10 + timer .. Bestrandom),
    ["18"] = tostring(os.time() + 7 + timer .. Bestrandom),
    ["19"] = tostring(os.time() + 8 + timer .. Bestrandom),
    ["20"] = tostring(os.time() + 9 + timer .. Bestrandom),
    ["21"] = tostring(os.time() + 10 + timer .. Bestrandom),
    ["22"] = tostring(os.time() + 11 + timer .. Bestrandom),
    ["23"] = tostring(os.time() - 11 + timer .. Bestrandom),
    ["24"] = tostring(os.time() + 12 + timer .. Bestrandom),
    ["Fake"] = tostring(os.time() + 342 + timer .. Bestrandom)
}
local t2 = {
    ["1"] = tostring(os.time() + timer),
    ["2"] = tostring(os.time() + 1 + timer),
    ["3"] = tostring(os.time() + 2 + timer),
    ["4"] = tostring(os.time() + 3 + timer),
    ["5"] = tostring(os.time() + 4 + timer),
    ["6"] = tostring(os.time() + 5 + timer),
    ["7"] = tostring(os.time() + 6 + timer),
    ["8"] = tostring(os.time() - 1 + timer),
    ["9"] = tostring(os.time() - 2 + timer),
    ["10"] = tostring(os.time() - 3 + timer),
    ["11"] = tostring(os.time() - 4 + timer),
    ["12"] = tostring(os.time() - 5 + timer),
    ["13"] = tostring(os.time() + 6 + timer),
    ["14"] = tostring(os.time() + 7 + timer),
    ["15"] = tostring(os.time() + 8 + timer),
    ["16"] = tostring(os.time() + 9 + timer),
    ["17"] = tostring(os.time() + 10 + timer),
    ["18"] = tostring(os.time() - 6 + timer),
    ["19"] = tostring(os.time() - 7 + timer),
    ["20"] = tostring(os.time() - 8 + timer),
    ["21"] = tostring(os.time() - 8 + timer),
    ["22"] = tostring(os.time() - 9 + timer),
    ["23"] = tostring(os.time() - 10 + timer),
    ["Fake"] = tostring(os.time() + 342 + timer)
}

local osc = {
    [1] = getgenv().Key .. HWID .. t2["1"],
    [2] = getgenv().Key .. HWID .. t2["2"],
    [3] = getgenv().Key .. HWID .. t2["3"],
    [4] = getgenv().Key .. HWID .. t2["4"],
    [5] = getgenv().Key .. HWID .. t2["5"],
    [6] = getgenv().Key .. HWID .. t2["6"],
    [7] = getgenv().Key .. HWID .. t2["7"],
    [8] = getgenv().Key .. HWID .. t2["8"],
    [9] = getgenv().Key .. HWID .. t2["9"],
    [10] = getgenv().Key .. HWID .. t2["10"],
    [11] = getgenv().Key .. HWID .. t2["11"],
    [12] = getgenv().Key .. HWID .. t2["12"],
    [13] = getgenv().Key .. HWID .. t2["13"],
    [14] = getgenv().Key .. HWID .. t2["14"],
    [15] = getgenv().Key .. HWID .. t2["15"],
    [16] = getgenv().Key .. HWID .. t2["16"],
    [17] = getgenv().Key .. HWID .. t2["17"],
    [18] = getgenv().Key .. HWID .. t2["18"],
    [19] = getgenv().Key .. HWID .. t2["19"],
    [20] = getgenv().Key .. HWID .. t2["20"],
    [21] = getgenv().Key .. HWID .. t2["21"],
    [22] = getgenv().Key .. HWID .. t2["22"],
    [23] = getgenv().Key .. HWID .. t2["23"]
}

if dataencode.StatusCode == 200 then
    if data ~= "" then
        if data ~= "Update Hwid" then
            if data ~= "You Are Got Blacklist" then
                if data == osc[1] or data == osc[2] or data == osc[3] or data == osc[4] or data == osc[3] or
                        data == osc[4] or
                        data == osc[5] or
                        data == osc[6] or
                        data == osc[7] or
                        data == osc[8] or
                        data == osc[9] or
                        data == osc[10] or
                        data == osc[11] or
                        data == osc[12] or
                        data == osc[13] or
                        data == osc[14] or
                        data == osc[15] or
                        data == osc[16] or
                        data == osc[18] or
                        data == osc[19] or
                        data == osc[20] or
                        data == osc[21] or
                        data == osc[22] or
                        data == osc[23]
                 then
                    if
                        Time == ostime["1"] or Time == ostime["2"] or Time == ostime["3"] or Time == ostime["4"] or
                            Time == ostime["5"] or
                            Time == ostime["6"] or
                            Time == ostime["7"] or
                            Time == ostime["8"] or
                            Time == ostime["9"] or
                            Time == ostime["10"] or
                            Time == ostime["11"] or
                            Time == ostime["12"] or
                            Time == ostime["13"] or
                            Time == ostime["14"] or
                            Time == ostime["15"] or
                            Time == ostime["16"] or
                            Time == ostime["17"] or
                            Time == ostime["18"] or
                            Time == ostime["19"] or
                            Time == ostime["20"] or
                            Time == ostime["21"] or
                            Time == ostime["22"] or
                            Time == ostime["23"]
                     then
                        if
                            (ostime["Fake"] - tonumber(Time) == 342 + timer or 343 + timer or 244 + timer or 243 + timer or
                                246 + timer or
                                341 + timer or
                                340 + timer or
                                339 + timer or
                                338 + timer)
                         then
                         local PlaceId = game.PlaceId
                         if PlaceId == 7655489843 then
                            loadstring(game:HttpGet("https://raw.githubusercontent.com/okpkgwnlo/asababaabddzbs/main/README.md"))()
                         elseif PlaceId == 6329844902 then
                            loadstring(game:HttpGet("https://raw.githubusercontent.com/okpkgwnlo/hreaeheste/main/README.md"))()
                         end
                            game.StarterGui:SetCore(
                                "SendNotification",
                                {
                                    Title = "Ben10 ",
                                    Icon = "http://www.roblox.com/asset/?id=8278806418",
                                    Text = "Whitelist",
                                    Duration = .5
                                }
                            )
                        else
                            game.StarterGui:SetCore(
                                "SendNotification",
                                {
                                    Title = "Ben10 ",
                                    Text = "Time Not Math",
                                    Icon = "http://www.roblox.com/asset/?id=8278806418",
                                    Duration = .5
                                }
                            )
                        end
                    else
                        game.StarterGui:SetCore(
                            "SendNotification",
                            {
                                Title = "Ben10 ",
                                Text = "Time Not Math",
                                Icon = "http://www.roblox.com/asset/?id=8278806418",
                                Duration = .5
                            }
                        )
                    end
                else
                    game.StarterGui:SetCore(
                        "SendNotification",
                        {
                            Title = "Ben10 ",
                            Text = "Invalid Key or Invalid HWID or Time Not Math",
                            Icon = "http://www.roblox.com/asset/?id=8278806418",
                            Duration = .5
                        }
                    )
                    game.Players.LocalPlayer:Kick("รันไหม่ครับ - กำลังรันไห้นะ")
                    wait(0.5)
                    game:GetService("TeleportService"):Teleport(game.PlaceId, game:GetService("Players").LocalPlayer)
                end
            else
                game.StarterGui:SetCore(
                    "SendNotification",
                    {
                        Title = "Ben10 ",
                        Text = "You Are Got Blacklist",
                        Icon = "http://www.roblox.com/asset/?id=8278806418",
                        Duration = .5
                    }
                )
            end
        else
            game:GetService("TeleportService"):Teleport(game.PlaceId, game:GetService("Players").LocalPlayer)
            game.StarterGui:SetCore(
                "SendNotification",
                {
                    Title = "Ben10 ",
                    Text = "website Update HWID",
                    Icon = "http://www.roblox.com/asset/?id=8278806418",
                    Duration = .5
                }
            )
            game.Players.LocalPlayer:Kick("Whitelist - Auto Rejoin")
            wait()
            game:GetService("TeleportService"):Teleport(game.PlaceId, game:GetService("Players").LocalPlayer)
            local hwidencode =
                bestrequest(
                {
                    ["Url"] = "http://154.212.139.136/changehwid.php?key=".. getgenv().Key.."&hwid="..HWID,
                    ["Method"] = "GET"
                }
            )   
        end
    else
        game.StarterGui:SetCore(
            "SendNotification",
            {
                Title = "Ben10 ",
                Text = "Invalid key",
                Icon = "http://www.roblox.com/asset/?id=8278806418",
                Duration = .5
            }
        )
        game.Players.LocalPlayer:Kick("Invalid Key!")
    end
elseif dataencode.StatusCode == 500 then
    game.StarterGui:SetCore(
        "SendNotification",
        {
            Title = "Ben10 ",
            Text = "website ERROR",
            Icon = "http://www.roblox.com/asset/?id=8278806418",
            Duration = .5
        }
    )
else
    game.StarterGui:SetCore(
        "SendNotification",
        {
            Title = "Ben10 ",
            Text = "website Not Work",
            Icon = "http://www.roblox.com/asset/?id=8278806418",
            Duration = .5
        }
    )
end
