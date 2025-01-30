# m!rps
```js
$nomention
$jsonParse[$getUserVar[rps;$authorID]]
$var[user;$replaceText[$replaceText[$isSlash;true;$findUser[$message[usuario];no]];false;$findUser[$message;no]]]
$try
$onlyIf[$var[user]!=$authorID;:x: | No puedes jugar contigo mismo.] $endtry
$onlyIf[$json[game]!=true;:x: | Ya tienes un juego en [marcha\](https://discord.com/channels/$guildID/$json[msg]) en este servidor.]
$if[$var[user]!=]
$onlyIf[$or[$isBot[$var[user]]==false;$var[user]==$botID]==true;:x: | No puedes jugar con un bot.]
$onlyIf[$userExists[$var[user]]==true;:x: | El usuario proporcionado no existe.]
$jsonClear $jsonParse[$getUserVar[rps;$var[user]]]
$onlyIf[$json[game]!=true;:x: | El usuario al que intentas retar, ya tiene un juego en [marcha\](https://discord.com/channels/$json[msg]).]
$endif
$var[user;$replaceText[$replaceText[$checkCondition[$var[user]!=];true;$var[user];1];false;$botID;1]]

$if[$var[user]!=$botID]
$var[id;$sendEmbedMessage[$channelID;;$username vs esperando oponente...;;Debes esperar a que el usuario acepte la partida.;#2872ff;;;Garu and MVK Team... 📚;;;;;yes]]
$addButton[no;rpsaccept-$var[user]-$authorID;Aceptar;success;no;✅;$var[id]]
$addButton[no;rpsdeny-$var[user]-$authorID;Rechazar;danger;no;:x:;$var[id]]
$else
$var[id;$sendEmbedMessage[$channelID;;$username vs $username[$botID];;El bot está elegiendo.;#2872ff;;;Garu and MVK Team... 📚;;;;;yes]]
$async[a]
$replyIn[3s]
$editMessage[$channelID;$var[id];;$username vs $username[$botID];El bot ya eligió. Le toca a $username.
> Selecciona Piedra, Papel o Tijeras.;#2872ff;Garu and MVK Team... 📚]
$addButton[no;rock-$authorID-bot;Piedra;primary;no;:rock:;$var[id]]
$addButton[no;paper-$authorID-bot;Papel;primary;no;:roll_of_paper:;$var[id]]
$addButton[no;scissors-$authorID-bot;Tijeras;primary;no;:scissors:;$var[id]]
$endasync
$var[user;$botID]
$endif
$jsonSetString[game;true] $jsonSetString[vs;$var[user]] $jsonSetString[msg;$channelID/$var[id]] $jsonSetString[owner;true] $setUserVar[rps;$jsonStringify;$authorID]
$async[x] $replyIn[3m] $deleteMessage[$channelID;$var[id]] $resetUserVar[rps;$authorID] $resetUserVar[rps;$var[user]] $endasync
```
#
