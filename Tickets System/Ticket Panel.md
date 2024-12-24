# m!panel
```js
$nomention
$jsonParse[$getUserVar[mvkproject-tickets;$botID]]
$onlyIf[$jsonExists[options]==true;:x: | Aún no está listo el panel. Empieza con m!config.]
$var[a;$json[options]]
$jsonClear $var[j;$replaceText[$getServerVar[mvkproject-tickets];null;]] $jsonParse[$var[j]]
$var[mvk;1]
$description[Bienvenido a nuestro panel de tickets. Recuerda que debes abrir un ticket solo si es necesario o podrías llevarte una sanción.]
$color[#4f5dcd]
$newSelectMenu[tickets;1;1]
$eval[$repeatMessage[$var[a];%{DOL}%if[%{DOL}%var[a\]>=%{DOL}%var[mvk\]\]
%{DOL}%addSelectMenuOption[tickets\;%{DOL}%json[p%{DOL}%var[mvk\]\;n\]\;p%{DOL}%var[mvk\]\;%{DOL}%json[p%{DOL}%var[mvk\]\;d\]\;no\;%{DOL}%json[p%{DOL}%var[mvk\]\;e\]\]
%{DOL}%endif
%{DOL}%var[mvk\;%{DOL}%sum[%{DOL}%var[mvk\]\;1\]\]
]]```
#
