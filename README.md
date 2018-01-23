--[[ ONE FOR ALL GOS
Script dùng để tổng hợp tất cả các script hiện tại của tool GOS.
Trang chủ GOS: gamingonsteroids.com
Script được viết bởi RN. Khi copy/di chuyển vui lòng để lại nguồn
--------------------------------------------------------------------------------]]
local function OneFile_Print(text)
PrintChat(string.format("<font color="#ff00ff">[Script TongHop]:<font color="#FFFFFF"> %s",tostring(text)))
end
local __require = require
local require = function(str) assert(FileExist(SCRIPT_PATH..str..".lua"), "\nKhong tim thay file '"..SCRIPT_PATH..str..".lua'\nVui long download script nay hoac chon script khac") __require(str) end

class "OneFile"
function OneFile:__init()
self:ChampSupported()
self:LoadMenu()
self:CheckUpdate()
self:LoadScriptChamp()
self:LoadUtility()
end

function OneFile:ChampSupported()
self.supported = {
["Aatrox"] = {"SeAIO","CSR Aatrox"},

    ["Akali"] = {"KMS Akali","CSR Akali"},
    ["Alistar"] = {"MeoMeo Support","CSR Alistar"},
    ["Annie"] = {"NEETSeries Annie", "PlatyAnnie"},
    ["Ashe"] = {"CS Ashe", "ADC Main Ashe"},
    
    ["Amumu"] = {"JungleBundle","CSR Amumu"},
    ["Blitzcrank"] = {"SxcSAIO Blitzcrank","MeoMeo Support","CSR Blitzcrank"},
    
    ["Brand"] = {"LB SERIES","[CS:R] Brand","NFSS Brand"},
    ["Caitlyn"] = {"ADC Main"},
	["Camille"] = {"CSR Camille"},
    ["Corki"] = {"SxcSAIO Corki", "ADC Main Corki"},
    ["Darius"] = {"Simple Darius"},
    ["Diana"] = {"KMS Diana","Moonwalker"},
    ["DrMundo"] = {"SxcSAIO Mundo"},
    
    ["Elise"] = {"Steroided Spider Elise", "QWER Elise"},
    ["Evelynn"] = {"Spooks Master Evelynn"},
    ["Ezreal"] = {"ADC Main Ezreal", "SxcSAIO Ezreal"},
    ["FiddleSticks"] = {"Fiddlesticks"},
    ["Fiora"] = {"Simple Fiora"},
    ["Fizz"] = {"Toxic Fizz"},
    ["Garen"] = {"Simple Garen", "SxcSAIO Garen","ES Garen"},
    ["Graves"] = {"ADC Main Graves"},
    ["Hecarim"] = {"Hecarim"},
    ["Illaoi"] = {"MvP Illaoi"},
    ["Jarvan IV"] = {"JarvanIVBae"},
	["Jayce"] = {"CSR Jayce"},
    ["Jax"] = {"Grandmaster Jax"},
    ["Jhin"] = {"High Noon Jhin","S7 Jhin"},
    ["Jinx"] = {"SxcSAIO Jinx"},
    ["Kalista"] = {"SxcSAIO Kalista", "ADC Main Kalista"},
    ["Karma"] = {"Karma Annoying Prick", "Meo Karma"},
    ["Karthus"] = {"Rx Karthus", "Simple Karthus"},
    ["Kassadin"] = {"Kassadin - The Void Walker"},
    ["Katarina"] = {"qwerKata","CSR Katarina"},
	["Khazix"] = {"Meo Khazix","Yard Zix"},
    ["Kayle"] = {"Royal Kayle", "Simple Kayle","Useless Kayle"},
    ["Kennen"] = {"KennenBae","ADC Main"},
    ["Kindred"] = {"|SL| Kindred","Eternal Kindred","QWER Kindred"},
    ["Kled"] = {"JungleBundle"},
    ["KogMaw"] = {"NEETSeries Kog'Maw", "SxcSAIO Kog'Maw","KogMaw"},
    ["LeBlanc"] = {"KMS LeBlanc","LB SERIES","S7 LeBlanc"},
    ["LeeSin"] = {"JungleBundle","CSR LeeSin"},
    ["Leona"] = {"SxcSAIO Leona"},
    ["Lissandra"] = {"KMS Lissandra"},
    ["Lucian"] = {"Lucian"},
    ["Lulu"] = {"LuluBae","ToXic Lulu"},
    ["Lux"] = {"SxcSAIO Lux","Lux - PentaKill"},
    ["Malphite"] = {"Eternal Malphite", "EternalAIO Malphite"},
    ["Malzahar"] = {"EvolvedMalzahar"},
    ["MasterYi"] = {"Alpha Strike MasterYi","[CS:R] Master Yi","Meo MasterYi"},
    ["MissFortune"] = {"ADC Main Miss Fortune"},
    ["Morgana"] = {"InnateSeries Morgana", "Meo Morgana","TroopMorg"},
    ["Nami"] = {"SxcSAIO Nami", "Meo Nami"},
    ["Nasus"] = {"Siphoning Strikes", "SxcSAIO Nasus", "SL Nasus"},
    ["Poppy"] = {"SxcSAIO Poppy","QWER Poppy"},
    ["Rengar"] = {"The Pridestalker Rengar", "Cloud Rengar"},
    ["Rumble"] = {"SxcSAIO Rumble"},
    ["Ryze"] = {"OpenPredict Ryze","Corrupt Ryze","qqwe Ryze"},
    ["Sona"] = {"Rx Sona"},
    ["Soraka"] = {"SxcSAIO Soraka", "SL Soraka"},
    ["Swain"] = {"SxcSAIO Swain","S7 Swain"},
    ["Tahm Kench"] = {"Tahm Kench","DamageLib"},
    ["Taliyah"] = {"Taliyah"},
    ["Teemo"] = {"OK Teemo","1 minute teemo"},
    ["Thresh"] = {"SxcSAIO Thresh"},
    ["Tristana"] = {"RK Tristana"},
    ["Tryndamere"] = {"Simple Tryndamere"},
    ["TwistedFate"] = {"KMS Twisted Fate","qwerTwistedFate "},
    ["Twitch"] = {"ADC Main Twitch","Insidious Twitch"},
    ["Varus"] = {"Piercing Arrow Varus","Insidious Varus"},
    ["Vayne"] = {"Simple Vayne", "SxcSAIO Vayne","CSR Vayne"},
    ["Veigar"] = {"Tiny Veigar"},
    ["Vi"] = {"The Heartbreaker Vi"},
    ["Viktor"] = {"KMS Viktor"},
    ["Vladimir"] = {"Simple Vladimir", "SL Vladimir"},
    ["Xerath"] = {"NEETSeries Xerath", "Simple Xerath","CSR Xerath"},
    ["XinZhao"] = {"Simple XinZhao","1 hour Xin Zhao"},
    ["Yasuo"] = {"Krystra Top Bundle", "Meo Yasuo"},
    ["Yorick"] = {"The Undefeated Yorick"},
    ["Zac"] = {"Elastic Slingshot Zac"},
    ["Zed"] = {"KMS Zed", "Zed Shadow","Zed Experimental"},
    ["Ziggs"] = {"EloBommer Ziggs"},
    ["Zilean"] = {"Rx Zilean","Meo Zilean"},
    ["Zyra"] = {"QWER Series"},
    ["Sivir"] = {"SL Sivir"},
    ["Velkoz"] = {"SL Velkoz"},
    ["Taliyah"] = {"Platy Taliyah"},
    ["Nautilus"] = {"Meo Nautilus"},
    ["Braum"] = {"Meo Braum"},
    ["Volibear"] = {"Volibear","Meo Volibear"},
    ["Jax"] = {"Grandmaster Jax"},
    ["Riven"] = {"Riven"},
    ["MonkeyKing"] = {"Sibyl WuKong", "Eternal WuKong"},
    ["Trundle"] = {"Eternal Trundle"},
    ["Irelia"] = {"QWER Irelia", "Frosted Booty Irelia"},
    ["Nidalee"] = {"QWER Nidalee"},
    ["Nocturne"] = {"|SL| Nocturne"},
    ["Pantheon"] = {"Pantheon"},
    ["Cassiopeia"] = {"SalamiSeries Cassiopeia"},
    ["Talon"] = {"LB Talon","S7 Talon"},
    ["Gangplank"] = {"Cloud Gangplank"},
    ["Ekko"] = {"Bored Ekko"},
    ["Shyvana"] = {"Noddy Shyvana"},
    ["TahmKench"] = {"Cloud TahmKench"},
    ["Mordekaiser"] = {"Zeyx Mordekaiser"},
    ["Singed"] = {"QWER Singed"},
    ["Taric"] = {"Taric Bae"},
    ["Janna"] = {"Meo Janna"},
    ["Udyr"] = {"Cloud Udyr"},
    ["Urgot"] = {"Urgot"},
	["Orianna"] = {"[KMS] Orianna"," Clock Orianna"},
	["Tryndamere"] = {"Useless Tryndamere"},
	--["Syndra"] = {"Syndra_LBSeries_ALPHA"}
}
end

function OneFile:LoadMenu()
self.cfg = MenuConfig("OneFile", "Script Tong Hop")
self.cfg:Info("if3", "Scipts Edit By Ka")
self.cfg:Menu("c", "Chon script cho "..myHero.charName)
if self.supported[myHero.charName] ~= nil then
self.cfg.c:DropDown("p", "Chon script:", 1, self.supported[myHero.charName], function() self:PrintScriptChange() end)
else
self.cfg.c:Info("info", "Tuong nay hien khong co script nao ho tro")
end
self.cfg:Menu("u", "Utility Scripts")
self.cfg.u:Info("if1", "Day la nhung scripts ho tro")
self.cfg.u:Info("if2", "Co the dung cho tat ca tuong")
self.cfg.u:Boolean("e1", "Load Ho Tro Farm Hoi Lag", false, function() self:PrintUtility(self.cfg.u.e1:Value(), "ho tro Farm") end)
self.cfg.u:Boolean("e2", "Load Auto Uti be da co", false, function() self:PrintUtility(self.cfg.u.e2:Value(), "Auto Uti be da co") end)
self.cfg.u:Boolean("e6", "Load Ne Skill (Like)", false, function() self:PrintUtility(self.cfg.u.e6:Value(), "Ne Skill (Like)") end)
self.cfg.u:Boolean("e3", "Load Ne Skill (Ok)", false, function() self:PrintUtility(self.cfg.u.e3:Value(), "Ne Skill (Ok)") end)
self.cfg.u:Boolean("e8", "Load Ne Skill (No FPS Drops )", false, function() self:PrintUtility(self.cfg.u.e8:Value(), "Ne Skill (No FPS Drops )") end)
self.cfg.u:Boolean("e4", "Load SL-Utility", false, function() self:PrintUtility(self.cfg.u.e4:Value(), "SL-Utility") end)
self.cfg.u:Boolean("e5", "Load Mod Skin", false, function() self:PrintUtility(self.cfg.u.e5:Value(), "Better SkinChanger") end)
self.cfg.u:Boolean("e7", "Load Auto Smite", false, function() self:PrintUtility(self.cfg.u.e7:Value(), "Auto Smite") end)
self.cfg.u:Boolean("e9", "Load Tat Vong", false, function() self:PrintUtility(self.cfg.u.e7:Value(), "Tat Vong") end)
self.cfg.u:Boolean("e10", "Load Auto + Skill ", false, function() self:PrintUtility(self.cfg.u.e7:Value(), "Auto + Chieu") end)
end

function OneFile:LoadScriptChamp()
local n, v = myHero.charName, self.cfg.c.p and self.cfg.c.p:Value()
if n == "Aatrox" then
if v == 1 then
require('SeAIO')
elseif v == 2 then
require('ChallengerSeriesReborn')
end
elseif n == "Ahri" then
if v == 1 then
require('ChallengerSeriesReborn')
end
elseif n == "Akali" then
if v == 1 then
require('BetaKms')
elseif v == 2 then
require('ChallengerSeriesReborn')
end
elseif n == "Alistar" then
if v == 1 then
require('Support Bundle')
elseif v == 2 then
require('ChallengerSeriesReborn')
end
elseif n == "Annie" then
if v == 1 then
require('NEETSeries')
elseif v == 2 then
require('annie')
end
elseif n == "Ashe" then
if v == 1 then
require('ChallengerSeriesReborn')
elseif v == 2 then
require('ADC Main')
end
elseif n == "Azir" then
if v == 1 then
require('ChallengerSeriesReborn')
end
elseif n == "Amumu" then
if v == 1 then
require('JungleBundle')
elseif v == 2 then
require('ChallengerSeriesReborn')
end
elseif n == "Bard" then
if v == 1 then
require('bardBae')
end
elseif n == "Brand" then
if v == 1 then
require('Brand_LBSeries')
elseif v==2 then
require('ChallengerSeriesReborn')
elseif v==3 then
require('Brand_NFSS')
end
elseif n == "Blitzcrank" then
if v == 1 then
require('SxcSAIO')
elseif v == 2 then
require('Support Bundle')
elseif v == 3 then
require('ChallengerSeriesReborn')
end
elseif n == "Caitlyn" then
if v == 1 then
require('ADC Main')
end
elseif n == "Camille" then
if v == 1 then
require('ChallengerSeriesReborn')
end
elseif n == "Corki" then
if v == 1 then
require('SxcSAIO')
elseif v == 2 then
require('ADC Main')
end
elseif n == "Draven" then
if v == 1 then
require('ChallengerSeriesReborn')
elseif v == 2 then
require('EternalDraven')
end
elseif n == "Darius" then
if v == 1 then
require('simple darius')
end
elseif n == "Diana" then
if v == 1 then
require('BetaKms')
elseif v == 2 then
require('Diana')
end
elseif n == "DrMundo" then
if v == 1 then
require('SxcSAIO')
end
elseif n == "Elise" then
if v == 1 then
require('Elise')
elseif v == 2 then
require('QWER Series')
end
elseif n == "Ezreal" then
if v == 1 then
require('ADC Main')
elseif v == 2 then
require('SxcSAIO')
end
elseif n == "FiddleSticks" then
if v == 1 then
require('Fiddle')
end
elseif n == "Fiora" then
if v == 1 then
require('simple fiora')
end
elseif n == "Fizz" then
if v == 1 then
require('Toxic fizz')
end
elseif n == "Garen" then
if v == 1 then
require('simple garen')
elseif v == 2 then
require('SxcSAIO')
elseif v == 3 then
require('Garen')
end
elseif n == "Graves" then
if v == 1 then
require('Graves')
end
elseif n == "Hecarim" then
if v == 1 then
require('Hecarim')
end
elseif n == "Illaoi" then
if v == 1 then
require('IllaoiGod')
end
elseif n == "Jarvan IV" then
if v == 1 then
require('jarvanivBae')
end
elseif n == "Jayce" then
if v == 1 then
require('ChallengerSeriesReborn')
end
elseif n == "Jax" then
if v == 1 then
require('Jax')
end
elseif n == "Jhin" then
if v == 1 then
require('Jhin')
elseif v == 2 then
require('Jhin')
end
elseif n == "Jinx" then
if v == 1 then
require('SxcSAIO')
end
elseif n == "Kalista" then
if v == 1 then
require('SxcSAIO')
elseif v == 2 then
require('ADC Main')
end
elseif n == "Karma" then
if v == 1 then
require('Karma')
elseif v == 2 then
require('Support Bundle')
end
elseif n == "Karthus" then
if v == 1 then
require('Karthus')
elseif v == 2 then
require('simple karthus')
end
elseif n == "Kassadin" then
if v == 1 then
require('Kassadin')
end
elseif n == "Katarina" then
if v == 1 then
require('qwerKata')
elseif v == 2 then
require('ChallengerSeriesReborn')
end
elseif n == "Khazix" then
if v == 1 then
require('JungleBundle')
elseif v == 2 then
require('GraveYard-Zix')
end
elseif n == "Kayle" then
if v == 1 then
require('RoyalKayle')
elseif v == 2 then
require('simple kayle')
elseif v == 3 then
require('UselessKayle')
end
elseif n == "Kennen" then
if v == 1 then
require('kennenBae')
elseif v == 2 then
require('ADC Main')
end
elseif n == "Kindred" then
if v == 1 then
require('SL-Series')
elseif v == 2 then
require('EternalKindred')
elseif v == 3 then
require('QWER Series')
end
elseif n == "Kled" then
if v == 1 then
require('JungleBundle')
end
elseif n == "KogMaw" then
if v == 1 then
require('NEETSeries')
elseif v == 2 then
require('SxcSAIO')
elseif v == 3 then
require('KogMaw')
end
elseif n == "LeBlanc" then
if v == 1 then
require('BetaKms')
elseif v == 2 then
require('LeBlanc_LBSeries')
elseif v == 3 then
require('LeBlanc')
end
elseif n == "LeeSin" then
if v == 1 then
require('JungleBundle')
elseif v == 2 then
require('ChallengerSeriesReborn')
end
elseif n == "Leona" then
if v == 1 then
require('SxcSAIO')
end
elseif n == "Lissandra" then
if v == 1 then
require('BetaKms')
end
elseif n == "Lucian" then
if v == 1 then
require('Lucian')
end
elseif n == "Lulu" then
if v == 1 then
require('luluBae')
elseif v == 2 then
require('Toxic Lulu')
end
elseif n == "Lux" then
if v == 1 then
require('SxcSAIO')
elseif v == 2 then
require('Lux')
end
elseif n == "Malphite" then
if v == 1 then
require('CustomMalphite')
elseif v == 2 then
require('EternalAIO')
end
elseif n == "Malzahar" then
if v == 1 then
require('EvolvedMalzahar')
end
elseif n == "MasterYi" then
if v == 1 then
require('MasterYi')
elseif v == 2 then
require('ChallengerSeriesReborn')
elseif v == 3 then
require('JungleBundle')
end
elseif n == "MissFortune" then
if v == 1 then
require('MissFortune')
end
elseif n == "Morgana" then
if v == 1 then
require('IS_morgana')
elseif v == 2 then
require('Support Bundle')
elseif v == 3 then
require('TroopMorg')
end
elseif n == "Nami" then
if v == 1 then
require('SxcSAIO')
elseif v == 2 then
require('Support Bundle')
end
elseif n == "Nasus" then
if v == 1 then
require('Nasus')
elseif v == 2 then
require('SxcSAIO')
elseif v == 3 then
require('SL-Series')
end
elseif n == "Poppy" then
if v == 1 then
require('SxcSAIO')
elseif v==2 then
require('QWER Series')
end
elseif n == "Rengar" then
if v == 1 then
require('Rengar - the Pridestalker')
elseif v == 2 then
require('Rengar')
end
elseif n == "Rumble" then
if v == 1 then
require('SxcSAIO')
end
elseif n == "Ryze" then
if v == 1 then
require('IcyRyze')
elseif v == 2 then
require('CorruptRyze')
elseif v == 3 then
require('Ryze')
end
elseif n == "Sona" then
if v == 1 then
require('SonaNDe')
end
elseif n == "Soraka" then
if v == 1 then
require('SxcSAIO')
elseif v == 2 then
require('SL-Series')
end
elseif n == "Swain" then
if v == 1 then
require('SxcSAIO')
elseif v == 2 then
require('Swain')
end
elseif n == "Tahm Kench" then
if v == 1 then
require('Kench')
elseif v == 2 then
require('DamageLib')
end
elseif n == "Taliyah" then
if v == 1 then
require('Taliyah')
end
elseif n == "Teemo" then
if v == 1 then
require('Teemo')
elseif v == 2 then
require('1 minute teemo')
end
elseif n == "Thresh" then
if v == 1 then
require('SxcSAIO')
end
elseif n == "Tristana" then
if v == 1 then
require('RKTristana')
end
elseif n == "Tryndamere" then
if v == 1 then
require('simple tryndamere')
end
elseif n == "TwistedFate" then
if v == 1 then
require('BetaKms')
end
if v == 2 then
require('qwerTF')
end
elseif n == "Twitch" then
if v == 1 then
require('ADC Main')
elseif v == 2 then
require('InsidiousTwitch')
end
elseif n == "Varus" then
if v == 1 then
require('Varus')
elseif v == 2 then
require('InsidiousVarus')
end
elseif n == "Vayne" then
if v == 1 then
require('simple vayne')
elseif v == 2 then
require('SxcSAIO')
elseif v == 3 then
require('ChallengerSeriesReborn')
end
elseif n == "Veigar" then
if v == 1 then
require('Veigar')
end
elseif n == "Vi" then
if v == 1 then
require('Vi')
end
elseif n == "Viktor" then
if v == 1 then
require('BetaKms')
end
elseif n == "Vladimir" then
if v == 1 then
require('simple vladimir')
elseif v == 2 then
require('SL-Series')
end
elseif n == "Xerath" then
if v == 1 then
require('NEETSeries')
elseif v == 2 then
require('simple xerath')
elseif v == 3 then
require('ChallengerSeriesReborn')
end
elseif n == "XinZhao" then
if v == 1 then
require('simple xinZhao')
elseif v == 2 then
require('xin')
end
elseif n == "Yasuo" then
if v == 1 then
require('KrystraTopBundle')
elseif v == 2 then
require('Project Yasuo')
end
elseif n == "Yorick" then
if v == 1 then
require('yorick')
end
elseif n == "Zac" then
if v == 1 then
require('Zac')
end
elseif n == "Zed" then
if v == 1 then
require('BetaKms')
elseif v == 2 then
require('Zed')
elseif v == 3 then
require('ZedExperimental')
end
elseif n == "Ziggs" then
if v == 1 then
require('Ziggs')
end
elseif n == "Zilean" then
if v == 1 then
require('RxZilean')
elseif v == 2 then
require('Support Bundle')
end
elseif n == "Zyra" then
if v == 1 then
require('QWER Series')
end
elseif n == "Gangplank" then
if v == 1 then
require('Gangplank')
end
elseif n == "TahmKench" then
if v == 1 then
require('Kench')
end
elseif n == "Udyr" then
if v == 1 then
require('Udyr')
end
elseif n == "Urgot" then
if v == 1 then
require('Urgot')
end
elseif n == "Velkoz" then
if v == 1 then
require('SL-Series')
end
elseif n == "Sivir" then
if v == 1 then
require('SL-Series')
end
elseif n == "Nautilus" then
if v == 1 then
require('Support Bundle')
end
elseif n == "Janna" then
if v == 1 then
require('Support Bundle')
end
elseif n == "Volibear" then
if v == 1 then
require('Volibear')
elseif v==2 then
require('Support Bundle')
end
elseif n == "Taliyah" then
if v == 1 then
require('Taliyah')
end
elseif n == "Braum" then
if v == 1 then
require('Support Bundle')
end
elseif n == "Jax" then
if v == 1 then
require('Jax')
end
elseif n == "Riven" then
if v == 1 then
require('riven')
end
elseif n == "MonkeyKing" then
if v == 1 then
require('Wukong')
elseif v == 2 then
require('EternalWukong')
end
elseif n == "Trundle" then
if v == 1 then
require('EternalTrundle')
end
elseif n == "Irelia" then
if v == 1 then
require('FrostedBootyBlade')
elseif v == 2 then
require('QWER Series')
end
elseif n == "Nidalee" then
if v == 1 then
require('QWER Series')
end
elseif n == "Nocturne" then
if v == 1 then
require('SL-Series')
end
elseif n == "Pantheon" then
if v == 1 then
require('Pantheon')
end
elseif n == "Cassiopeia" then
if v == 1 then
require('SalamiSeries-Cassiopeia')
end
elseif n == "Talon" then
if v == 1 then
require('Talon_LBSeries')
elseif v == 2 then
require('Talon')

  end
elseif n == "Ekko" then
  if v == 1 then
    require('Ekko')
  end
elseif n == "Shyvana" then
  if v == 1 then
    require('qwerShyv')
  end
elseif n == "Mordekaiser" then
  if v == 1 then
    require('Mordekaiser')
  end
elseif n == "Bard" then
  if v == 1 then
    require('bardBae')
  end
elseif n == "Taric" then
  if v == 1 then
    require('TaricBae')
  end
 elseif n == "Orianna" then
  if v == 1 then
    require('BetaKms')
  elseif v==2 then
    require('ClockworkOrianna')
  end
  elseif n == "Syndra" then
  if v == 1 then
    require('Syndra_LBSeries_ALPHA')
  end
  elseif n == "Singed" then
  if v == 1 then
    require('QWER Series')
  end
   elseif n == "Tryndamere" then
  if v == 1 then
    require('UselessTryndamere')
  end
  
end
end

function OneFile:LoadUtility()
if self.cfg.u.e1:Value() then require("Deftsu's Auto Carry Reborn") end
if self.cfg.u.e2:Value() then require('RecallUlt') end
if self.cfg.u.e3:Value() then require('SL-Evade') end
if self.cfg.u.e6:Value() then require('ChallengerEvade') end
if self.cfg.u.e4:Value() then require("SL-Utility") end
if self.cfg.u.e5:Value() then require("Better SkinChanger") end
if self.cfg.u.e7:Value() then require("SmiteGod") end
if self.cfg.u.e8:Value() then require("Evade") end
if self.cfg.u.e9:Value() then require("OffDrawEditByKA") end
if self.cfg.u.e10:Value() then require("AutoLVL") end

end

function OneFile:PrintScriptChange()
if self.supported[myHero.charName] == nil then return end
OneFile_Print("Da chuyen sang su dung script "..self.supported[myHero.charName][self.cfg.c.p:Value()]..". Nhan F6 x2 de thay doi.")
end

function OneFile:PrintUtility(boolean, text)
local current = boolean == true and "Bat" or "Tat"
OneFile_Print("F6 x2 de "..current.." '"..text.."'")
end

function OneFile:CheckUpdate()
self.Update = {}
self.Update.ScriptVersion = 0.029
self.Update.UseHttps = true
self.Update.Host = "raw.githubusercontent.com"
self.Update.VersionPath = "/solotanktank/Script/master/ScriptTongHop.version"
self.Update.ScriptPath = "/solotanktank/Script/master/1%20Key%20To%20Champion.lua"
self.Update.SavePath = SCRIPT_PATH.."1 Key To Champion.lua"
self.Update.CallbackUpdate = function(NewVersion) OneFile_Print("Da cap nhat len phien ban "..NewVersion..". F6 x2 de tai lai script.") end
self.Update.CallbackNoUpdate = function(NewVersion) OneFile_Print("Bạn đã sử dụng phiên bản mới nhất ("..NewVersion..")") self:Hello() end
self.Update.CallbackNewVersion = function(NewVersion) OneFile_Print("Da tim thay phien ban moi ("..NewVersion.."). Vui long doi cap nhat...") end
self.Update.CallbackError = function() OneFile_Print("Da co loi xay ra khi kiem tra cap nhat. Vui long kiem tra lai Internet") end
AutoUpdater(self.Update.ScriptVersion, self.Update.UseHttps, self.Update.Host, self.Update.VersionPath, self.Update.ScriptPath, self.Update.SavePath, self.Update.CallbackUpdate, self.Update.CallbackNoUpdate, self.Update.CallbackNewVersion, self.Update.CallbackError)
end

function OneFile:Hello()
if self.supported[myHero.charName] ~= nil then
PrintChat(string.format("<font color="#ff00ff">[Script TongHop]:<font color="#FFFFFF"> Script tướng đang dùng: %s",self.supported[myHero.charName][self.cfg.c.p:Value()]))
else
PrintChat(string.format("<font color="#ff00ff">[Script TongHop]:<font color="#FFFFFF"> Tướng bạn đang chơi hiện chưa có scipts nào hổ trợ."))
end
PrintChat(string.format("<font color="#ff00ff">[Script TongHop]:<font color="#FFFFFF"> Script Được Viết Bởi RN."))
PrintChat(string.format("<font color="#80ff00"> HTTP://ToolLienMinhMienPhi.BlogSpot.Com/"))
end

OneFile()
