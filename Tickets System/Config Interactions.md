# $onInteraction
```js
$nomention
$onlyIf[$or[$customID==close;$customID==claim;$customID==tickets]==true;]
$var[token;$getVar[token]]
$ephemeral
$removeAllComponents
$if[$customID==tickets]
$jsonParse[$getServerVar[mvkproject-tickets]]
$var[c;$json[$message;c]]
$jsonClear
$var[j;$replaceText[$getUserVar[mvkproject-tickets;$botID];null;]]
$jsonParse[$var[j]]
$var[ch;ticket-$replaceText[$replaceText[$replaceText[$username;-;-];_;];.;]]
$createChannel[$var[ch];text;$var[c]]
$var[cha;$findChannel[$var[ch]]]
$description[✅ • Tu ticket fue abierto correctamente.]
$color[#4f5dcd]
$addButton[no;https://discord.com/channels/$guildID/$var[cha];Ir;link;no]
$useChannel[$var[cha]]
$textSplit[m-t-th-f-fi-a-ai-i-c-d;-]
$var[best;1]
$var[own;$authorID]
$eval[$repeatMessage[10;
%{DOL}%var[%{DOL}%splitText[%{DOL}%var[best\]\]\;
%{DOL}%replaceText[%{DOL}%replaceText[%{DOL}%replaceText[%{DOL}%replaceText[%{DOL}%replaceText[%{DOL}%replaceText[%{DOL}%replaceText[%{DOL}%replaceText[%{DOL}%json[%{DOL}%message\;%{DOL}%splitText[%{DOL}%var[best\]\]\]\;{guild.icon}\;%{DOL}%serverIcon\]\;{guild.name}\;%{DOL}%serverName[%{DOL}%guildID\]\]\;{guild.id}\;%{DOL}%guildID\]\;{guild.owner}\;%{DOL}%serverOwner\]\;{owner.username}\;%{DOL}%username[%{DOL}%var[own\]\]\]\;{owner.nick}\;%{DOL}%nickname[%{DOL}%var[own\]\]\]\;{owner.mention}\;<@%{DOL}%var[own\]>\]\;{owner.id}\;%{DOL}%var[own\]\]\]
%{DOL}%var[best\;%{DOL}%sum[%{DOL}%var[best\]\;1\]\]]]

$var[id;$sendEmbedMessage[$var[cha];$var[m];$var[t];;$var[d];$var[c];$var[a];$var[ai];$var[f];$var[fi];$var[th];$var[i];yes;yes]]
$addButton[no;close;Cerrar Ticket;danger;no;;$var[id]]
$addButton[no;claim;Reclamar Ticket;primary;no;;$var[id]]
$jsonClear
$jsonParse[$getChannelVar[mvkproject-tickets;$var[cha]]]
$jsonSetString[owner;$authorID]
$setChannelVar[mvkproject-tickets;$jsonStringify;$var[cha]]
$stop
$endif
$if[$customID==close]
$jsonParse[$getUserVar[mvkproject-tickets;$botID]]
$description[La transcripción de esta creando. Esto puede tardar un rato.]
$color[#4f5dcd]
$httpAddHeader[Authorization;$var[token]]
$httpPost[https://api.erxproject.xyz/discord/transcript/$guildID/$channelID]
$editEmbedIn[2s;;Transcripción generada correctamente. Este ticket se cerrará en 5s.;;#4f5dcd]
$sendEmbedMessage[$json[log];;;;Transcripción Generada
Ticket: $channelName[$channelID]
Transcripción: $httpResult[url];#4f5dcd]
$async[b]
$replyIn[5s]
$deleteChannels[$channelID]
$endasync
$jsonClear
$jsonParse[$getChannelVar[mvkproject-tickets;$channelID]]
$elseif[$customID==claim]
$jsonParse[$getUserVar[mvkproject-tickets;$botID]]
$var[role;$json[role]]
$jsonClear
$jsonParse[$getChannelVar[mvkproject-tickets;$channelID]]
$onlyIf[$hasRole[$authorID;$var[role]]==true;:x: | Tú no eres staff. $var[role]]
$if[$json[claim]==$authorID]
$jsonUnset[claim]
$description[✅ • Este ticket ya no te pertenece, está libre y cualquiera lo puede reclamar.]
$color[#4f5dcd]
$else
$onlyIf[$json[claim]==;:x: | Este ticket ya fue reclamado.]
$description[✅ • Acabas de reclamar el ticket. Te comprometes a terminarlo.]
$color[#4f5dcd]
$jsonSetString[claim;$authorID]
$endif
$setChannelVar[mvkproject-tickets;$jsonStringify;$channelID]
$endif
```
#
