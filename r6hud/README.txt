***** R6 CUSTOM HUD by B3RC1 HASZNÁLATI ÚTMUTATÓ *****

*** Működési elv ***
A program a map_players.txt adatbázis alapján automatikusan csapatokba rendezi a játékosokat, akiknek kezeli a képét és a live feedjét. Ha kiválasztunk valakit az X. spectate positionre, akkor a REFRESH HUD megnyomásakor a program az OBS számára az X. képre és forrásra ráteszi az adott játékosét. Az OBS figyeli a billentyűnyomásokat, így ha ingame megnyomjuk a "C" betűt (FPS nézetre váltás, akkor megjelenik a custom HUD), ha pedig megnyomjuk a 7-es számot, akkor a 7. játékos feedje fog megjelenni. 
(Előbb muszáj csapatot választani, csak utána lehet játékosokat.)

*** Megjegyzés ***
Ha valami gond van kör közben a custom huddal, akkor az INSERT gomb is kikapcsolja, így lehetővé téve, hogy fps nézetben legyen ugyan az observer, de ne látszódjon a custom hud (ne bindelj rá semmi mást a stream közben futó progikban, játékban).

*** Dual RTMP ***
Szükség van az NDI for OBS pluginra!
"A" feed: Ingame, OBS Studioból, pref: 15mbps, minimum: 10mbps
"B" feed: 10-men-picture, Streamlabs OBS-ből, pref: 15mbps, minimum: 8mbps

OBS Studioban a LOBBYVIEW jelenet ki van küldve egy dedikált NDI outputra (szűrőbeállítások). Ezt az NDI outputot kell megnyitni Streamlabs OBS-sel és kistreamelni (tulajdonságok: hardeveres gyorsítás be, késés: alacsony).

*** Lehetséges hibák, amire figyelni kell! ***
Ugyan a program egész sok kivételt tud kezelni és segít, ha baj van, de a legfontosabbak:
Az r6hud.exe fájllal egy mappában legyen az imgsrc mappa és a live_hud mappa, a map_players.txt és a scene-path. (továbbá a Newtonsoft.Json.dll és xml, r6hud.exe.config és az r6hud.pdb)
A map_players.txt fájlban minden sor a következőképp nézzen ki és ne legyen üres sor a fájl végén se:
csapatnév játékosnév feedCsatlakozásiLink feedMegtekintésiLink

Az imgsrc mappában minden egyes map_players.txt-ben szereplő játékoshoz kell tartozzon egy játékosnév.png kép, tehát, ha DogeFather van írva az adatbázisban, akkor a kép neve csak és kizárólag DogeFather.png lehet (dogefather.png sem, doge.png, doge father.png pláne nem).
Az imgsrc mappából a none.png-t törölni tilos.

A live_hud mappához hozzányúlni tilos, az OBS innen "nézi ki" a képeket, a pic0 forrásra rá van állítva a 0.png, pic1-re 1.png stb stb.

A scene-path.txt pontosan egyetlen sort kell, hogy tartalmazzon, mely a következőképpen néz ki pl.:
C:\Users\Berci\AppData\Roaming\obs-studio\basic\scenes\mn3br6.json
NEM A BEIMPORTÁLT FÁJL ELÉRÉSE KELL IDE, HANEM AZ APPDATA\ROAMING\OBS-STUDIO\BASIC\SCENES MAPPÁBAN TALÁLHATÓÉ!
Vigyázat! Az OBS preset JSON fájl neve nem egyezik meg a preset nevével.
(Pl.: preset neve: mn3b-r6, de a fájl neve: mn3br6.json)

Előfordulhat, hogy bizonyos rendszereken a program rendeltetésszerű működéséhez rendszergazdai jogosultsággal kell indítani. Ez akkor valószínú fokozottan, ha a rendszermeghajtóra van téve az r6hud.exe.

A REFRESH HUD gomb csak akkor működik, ha nem fut az OBS! Erre azért van szükség, mert az obs presetjén az r6hud.exe által eszközölt változtatások (JSON fájl) csak akkor lépnek életbe, ha az OBS  nem fut. Erre a játék is figyelmeztet.

Ha valaki kifagy, akkor át lehet ugyan a programon belül rendezni a játékosok listáját, de életbe csak akkor lép, ha  az OBS újraindul (CF megszakad) szóval ez annyira nem releváns, ilyenkor lehet tanácsosabb INSERT gombbal kikapcsolni a custom hudot és következő kör elején első FPS nézetbe váltáskor "C"-vel visszakapcsolni.

Az OBS bindelés előfordulhat, hogy csak magyar kiosztáson működik, ugyanis az "ö" betúre van bindelve a 10. játékos.

A program nem szól, ha ugyanaz a csapat vagy ugyanaz a játékos kétszer ki van választva, szükség lenne ennek implementálására?

***** Ha bármi nagyszabású probléma van, amire itt nincs válasz, akkor Bercit kell megkérdezni! *****

2021.
dinnyeTM