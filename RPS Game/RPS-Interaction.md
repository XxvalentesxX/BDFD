# $onInteraction
```js
$nomention
$textSplit[$customID;-] $var[bid;$splitText[1]]
$onlyIf[$or[$var[bid]==rpsaccept;$var[bid]==rpsdeny;$var[bid]==rock;$var[bid]==paper;$var[bid]==scissors]==true;]
$ephemeral
$removeAllComponents
$allowUserMentions[]
$var[dclink;https://discord.com]
$try $onlyIf[$splitText[2]==$authorID;] $catch $ephemeral Esta no es tu interacción. $stop $endtry
$jsonParse[$getUserVar[rps;$authorID]]
$if[$var[bid]==rpsaccept]
$try $onlyIf[$splitText[2]==$authorID;] $catch $ephemeral Esta no es tu interacción. $stop $endtry
$jsonSetString[game;true] $jsonSetString[vs;$splitText[3]] $jsonSetString[msg;$channelID/$messageID] $setUserVar[rps;$jsonStringify;$authorID]
$removeAllComponents[$messageID]
$editMessage[$channelID;$messageID;;$username[$json[vs]] vs $username;El usuario [@$nickname\]($var[dclink]/users/$authorID) aceptó. Hora de elegir. Primero elegirá: <@$json[vs]>
> Elige entre: Piedras, Papel o Tijeras.;#2872ff;Garu and MVK Team... 📚]
$var[tempm;<@$json[vs]>, el usuario $username aceptó tu partida en rps.
-# Este mensaje se eliminará en ]
$addButton[no;rock-$splitText[3];Piedra;primary;no;:rock:;$messageID]
$addButton[no;paper-$splitText[3];Papel;primary;no;:roll_of_paper:;$messageID]
$addButton[no;scissors-$splitText[3];Tijeras;primary;no;:scissors:;$messageID]
$var[temp;$sendMessage[$var[tempm]3s;yes]]
$async[a] $replyIn[1s] $editMessage[$channelID;$var[temp];$var[tempm]2s] $endasync
$async[b] $replyIn[2s] $editMessage[$channelID;$var[temp];$var[tempm]1s] $endasync
$async[c] $replyIn[3s] $editMessage[$channelID;$var[temp];$var[tempm]0] $endasync
$async[d] $replyIn[4s] $deleteMessage[$channelID;$var[temp]] $endasync
$stop
$elseif[$var[bid]==rpsdeny]
$try $onlyIf[$splitText[2]==$authorID;] $catch $ephemeral Esta no es tu interacción. $stop $endtry
$removeAllComponents[$messageID]
$resetUserVar[rps;$authorID]
$resetUserVar[rps;$splitText[3]]
$editMessage[$channelID;$messageID;;$username[$splitText[3]] gana;La victoria fue concedida a [@$nickname[$splitText[3]]\]($var[dclink]/users/$splitText[3])
> El oponente, $nickname, rechazó la partida. Por lo tanto, <@$splitText[3]>, gana.;#2872ff;Garu and MVK Team... 📚]
$var[temp;$sendMessage[<@$authorID> perdiste automáticamente por rechazar la partida.;yes]]
$async[j] $replyIn[3s] $deleteMessage[$channelID;$var[temp]] $endasync
$stop
$endif
$textSplit[$replaceText[$replaceText[$replaceText[$customID;rock;piedra];paper;papel];scissors;tijera];-]
$if[$or[$splitText[1]==piedra;$splitText[1]==papel;$splitText[1]==tijera]==true]
$removeAllComponents $removeAllComponents[$messageID]
$onlyIf[$or[$authorID==$splitText[2];$authorID==$splitText[3]]==true;no]
$jsonParse[$getUserVar[rps;$authorID]]
$jsonSetString[select;$toTitleCase[$splitText[1]]]
$setUserVar[rps;$jsonStringify;$authorID]
$ephemeral
✅ • Tu elección fue tomada correctamente.
$if[$and[$jsonExists[owner]==true;$splitText[3]==]==true]
$addButton[no;rock-$json[vs];Piedra;primary;no;:rock:;$messageID]
$addButton[no;paper-$json[vs];Papel;primary;no;:roll_of_paper:;$messageID]
$addButton[no;scissors-$json[vs];Tijeras;primary;no;:scissors:;$messageID]
$editMessage[$channelID;$messageID;;$username vs $username[$json[vs]];$nickname ya eligió. [$nickname[$json[vs]]\](https://discord.com/users/$json[vs]) te toca.
> Elige entre: Piedra, Papel o Tijeras.;#2872ff;Garu and MVK Team... 📚]
$else
$var[j2;$authorID] $var[2;$json[select]]
$if[$splitText[3]==bot]
$var[j1;$botID] $var[1;$randomText[Piedra;Papel;Tijera]]
$else
$var[j1;$json[vs]] $jsonParse[$getUserVar[rps;$json[vs]]] $var[1;$json[select]]
$endif
$if[$var[1]==$var[2]]
$var[win;nowin]
$elseif[$and[$var[1]==Piedra;$var[2]==Tijera]]
$var[win;$var[j1]] $var[select;$var[1]]
$var[loss;**$username[$var[j2]]:** $var[2]]
$elseif[$and[$var[1]==Tijera;$var[2]==Papel]]
$var[win;$var[j1]] $var[select;$var[1]]
$var[loss;**$username[$var[j2]]:** $var[2]]
$elseif[$and[$var[1]==Papel;$var[2]==Piedra]]
$var[win;$var[j1]] $var[select;$var[1]]
$var[loss;**$username[$var[j2]]:** $var[2]]
$else
$var[win;$var[j2]] $var[select;$var[2]]
$var[loss;**$username[$var[j1]]:** $var[1]]
$endif
$var[title;$username vs $username[$var[j1]]]
$var[fo;Garu and MVK Team... 📚]
$var[desc;Se está decidiendo el ganador.]
$var[1;#ff6776] $var[2;2872ff]
$editMessage[$channelID;$messageID;;$var[title];Ambos ya han elegido. $var[de]..;#2872ff;$var[fo]]
$async[m] $replyIn[1s] $editMessage[$channelID;$messageID;;$var[title];$var[desc];$var[1];$var[fo]] $endasync
$async[q] $replyIn[2s] $editMessage[$channelID;$messageID;;$var[title];$var[desc].;$var[2];$var[fo]] $endasync
$async[w] $replyIn[3s] $editMessage[$channelID;$messageID;;$var[title];$var[desc]..;$var[1];$var[fo]] $endasync
$async[v] $replyIn[4s] $editMessage[$channelID;$messageID;;$var[title];$var[desc];$var[2];$var[fo]] $endasync
$async[p] $replyIn[5s] $editMessage[$channelID;$messageID;;$var[title];$var[desc].;$var[1];$var[fo]] $endasync
$async[h] $replyIn[6s] $editMessage[$channelID;$messageID;;$var[title];$var[desc]..;$var[2];$var[fo]] $endasync
$if[$var[win]==nowin]
$async[ca] $replyIn[7s]
$editMessage[$channelID;$messageID;;Hubo un empate;Ninguno ganó. La elección de ambos fue la misma.;#2872ff;Garu and MVK Team... 📚]
$endasync
$else
$async[ca] $replyIn[7s]
$editMessage[$channelID;$messageID;;$username[$var[win]] ganó;El usuario [@$nickname[$var[win]]\](https://discord.com/users/$var[win]) salió ganador.
> **$username[$var[win]]:** $var[select]
> $var[loss];#2872ff;Garu and MVK Team... 📚]
$endasync
$endif
$resetUserVar[rps;$var[j1]]
$resetUserVar[rps;$var[j2]]
$endif
$endif
```
#
