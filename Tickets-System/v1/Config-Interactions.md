# $onInteraction
```js
$nomention
$textSplit[$customID;-]
$onlyIf[$or[$splitText[1]==options;$splitText[1]==optionss;$customID==select;$splitText[1]==set;$splitText[1]==sett;$message==back-$authorID]==true;]
$removeAllComponents
$jsonParse[$getUserVar[mvkproject-tickets;$botID]]
$ephemeral
$onlyIf[$isAdmin[$authorID]==true;Necesitas ser administrador para esto.]
$if[$splitText[1]==options]
$onlyIf[$splitText[2]==$authorID;:x: | Esta no es tu interacción.]
$newModal[optionss-$messageID;Establece Configuración Básica]
$addTextInput[optionss;short;Cantidad:;1;1;yes;$json[options];3]
$addTextInput[role;short;Staff Role;1;40;yes;$json[role];2773882777727222920]
$addTextInput[log;short;Log Channel;1;40;yes;$json[log];1294994994999376488]
$elseif[$splitText[1]==optionss]
$var[a;$input[optionss]]
$onlyIf[$isNumber[$var[a]]==true;:x: | No has proporcionado un número.]
$onlyIf[$var[a]<=5;:x: | El número es mayor a 5.]
$onlyIf[$roleExists[$input[role]]==true;:x: | El rol proporcionado no existe.]
$onlyIf[$channelExists[$input[log]]==true;:x: | El canal de logs proporcionado no existe.]
$removeAllComponents[$splitText[2]]
$jsonSetString[role;$input[role]]
$jsonSetString[options;$var[a]]
$jsonSetString[log;$input[log]]
$description[✅ • Todo ha ido bien, y estableciste la cantidad de opciones para tu panel.
-# Cantidad establecida en: $var[a]]
$color[#4f5dcd]
$newSelectMenu[select;1;1;;$splitText[2]]
$var[a;$json[options]]
$onlyIf[$var[a]!=;Al parecer no has seleccionado el número de opciones.]
$var[mvk;1]
$eval[$repeatMessage[$var[a];%{DOL}%if[%{DOL}%var[a\]>=%{DOL}%var[mvk\]\]
%{DOL}%addSelectMenuOption[select\;Panel %{DOL}%var[mvk\]\;panel-%{DOL}%var[mvk\]-%{DOL}%authorID-%{DOL}%messageID\; Configura el panel N°%{DOL}%var[mvk\]\;no\;\;%{DOL}%splitText[2\]\]
%{DOL}%endif
%{DOL}%var[mvk\;%{DOL}%sum[%{DOL}%var[mvk\]\;1\]\]]]
$elseif[$customID==select]
$textSplit[$message;-]
$onlyIf[$splitText[3]==$authorID;:x: | Esta no es tu interacción.]
$async[a]
$var[id;$messageID]
$endasync
$await[a]
$removeAllComponents
$removeAllComponents[$var[id]]
$newSelectMenu[sett-$splitText[2];1;1;;$var[id]]
$addSelectMenuOption[sett-$splitText[2];Embed;panel-$splitText[2]-1-$authorID;Título, Autor, Ícono de Autor, Thumbnail y Mensaje.;no;;$var[id]]
$addSelectMenuOption[sett-$splitText[2];Embed;panel-$splitText[2]-2-$authorID;Descripción, Color, Imagen, Footer e Icono del Footer.;no;;$var[id]]
$addSelectMenuOption[sett-$splitText[2];Embed;panel-$splitText[2]-3-$authorID;Configuración básica;no;;$var[id]]
$addSelectMenuOption[sett-$splitText[2];Volver;back-$authorID;Vuelve al menú de paneles.;no;;$var[id]]
$description[✅ • Ahora estás modificando el panel N°$splitText[2]]
$color[#4f5dcd]
$elseif[$splitText[1]==sett]
$textSplit[$message;-]
$if[$splitText[1]==panel]
$if[$splitText[3]==1]
$newModal[set-1-$splitText[2];Ajustes del Panel N°$splitText[2]]
$addTextInput[msg;short;Mensaje fuera del embed;1;140;no;$json[p$splitText[2];m];{user.mention} - <@&STAFF_ROLE_ID>]
$addTextInput[title;short;Título del Embed;1;40;no;$json[p$splitText[2];t];Bienvenid@ {username}!]
$addTextInput[author;short;Autor del Embed;1;45;no;$json[p$splitText[2];a];{guild.name}]
$addTextInput[authoricon;short;Ícono del author del embed;1;450;no;$json[p$splitText[2];ai];{guild.icon}]
$addTextInput[thumb;short;Thumbnail del Embed;1;450;no;$json[p$splitText[2];th];{user.icon}]
$elseif[$splitText[3]==2]
$newModal[set-2-$splitText[2];Ajustes del Panel N°$splitText[2]]
$addTextInput[desc;paragraph;Descripción del embed;1;2000;yes;$json[p$splitText[2];d];{user.username} Bienvenido al ticket.\nSe paciente y espera a que un staff te ayude.]
$addTextInput[color;short;Color del Embed;1;8;no;$json[p$splitText[2];c];#4f5dcd]
$addTextInput[img;short;Imágen del Embed;1;450;no;$json[p$splitText[2];i];https://cdn.mvkproject.xyz/mvkproject.png]
$addTextInput[foot;short;Footer del embed;1;35;no;$json[p$splitText[2];f];Created by: {user.id}]
$addTextInput[footi;short;Ícono del footer del Embed;1;450;no;$json[p$splitText[2];fi];{user.icon}]
$elseif[$splitText[3]==3]
$newModal[set-3-$splitText[2];Configuración Básica del Panel N°$splitText[2]]
$addTextInput[id;short;ID del Panel;1;40;yes;;suuport-1]
$addTextInput[category;short;Categoría;1;40;yes;;123456789123456789]
$addTextInput[name;short;Nombre de la opción;1;40;yes;; Categoría de Soporte]
$addTextInput[desc;short;Descripción de la Opción;1;120;yes;;Abre un ticket de tipo categoría soporte.]
$addTextInput[emoji;short;Emoji de la Opción;1;40;no;;🟢]
$endif
$elseif[$splitText[1]==back]
$removeAllComponents[$messageID]
$newSelectMenu[select;1;1;;$messageID]
$var[a;$json[options]]
$var[mvk;1]
$eval[$repeatMessage[$var[a];%{DOL}%if[%{DOL}%var[a\]>=%{DOL}%var[mvk\]\]
%{DOL}%addSelectMenuOption[select\;Panel %{DOL}%var[mvk\]\;panel-%{DOL}%var[mvk\]-%{DOL}%authorID-%{DOL}%messageID\; Configura el panel N°%{DOL}%var[mvk\]\;no\;\;%{DOL}%messageID\]
%{DOL}%endif
%{DOL}%var[mvk\;%{DOL}%sum[%{DOL}%var[mvk\]\;1\]\]]]
$description[✅ • Regresaste al menú de selección.]
$color[#4f5dcd]
$endif
$elseif[$splitText[1]==set]
$if[$splitText[2]==1]
$jsonSetString[p$splitText[3];m;
$replaceText[$replaceText[$checkCondition[$input[msg]!=];true;$input[msg];1];false;null;1]]
$jsonSetString[p$splitText[3];t;
$replaceText[$replaceText[$checkCondition[$input[title]!=];true;$input[title];1];false;null;1]]
$jsonSetString[p$splitText[3];a;
$replaceText[$replaceText[$checkCondition[$input[author]!=];true;$input[author];1];false;null;1]]
$jsonSetString[p$splitText[3];ai;
$replaceText[$replaceText[$checkCondition[$input[authoricon]!=];true;$input[authoricon];1];false;null;1]]
$jsonSetString[p$splitText[3];th;
$replaceText[$replaceText[$checkCondition[$input[thumb]!=];true;$input[thumb];1];false;null;1]]
$description[✅ • Todo salió correctamente, tu nuevo embed fue establecido.]
$color[#4f5dcd]
$elseif[$splitText[2]==2]
$jsonSetString[p$splitText[3];d;
$replaceText[$replaceText[$checkCondition[$input[desc]!=];true;$input[desc];1];false;null;1]]
$jsonSetString[p$splitText[3];c;
$replaceText[$replaceText[$checkCondition[$isValidHex[$input[color]]==true];true;$input[color];1];false;#4f5dcd;1]]
$jsonSetString[p$splitText[3];f;
$replaceText[$replaceText[$checkCondition[$input[footer]!=];true;$input[footer];1];false;null;1]]
$jsonSetString[p$splitText[3];fi;
$replaceText[$replaceText[$checkCondition[$input[footi]!=];true;$input[footi];1];false;null;1]]
$jsonSetString[p$splitText[3];i;
$replaceText[$replaceText[$checkCondition[$input[img]!=];true;$input[img];1];false;null;1]]
$description[✅ • Todo salió correctamente, tu nuevo embed fue establecido.]
$color[#4f5dcd]
$elseif[$splitText[2]==3]
$jsonClear
$jsonParse[$getServerVar[mvkproject-tickets]]
$onlyIf[$and[$channelExists[$input[category]]==true;$channelType[$input[category]]==category]==true;:x: | El id proporcionado, no fue encontrado en el servidor o no es una categoría.]
$jsonSetString[p$splitText[3];c;$input[category]]
$jsonSetString[p$splitText[3];n;$input[name]]
$jsonSetString[p$splitText[3];d;$input[desc]]
$jsonSetString[p$splitText[3];e;$input[emoji]]
$jsonSetString[p$splitText[3];id;$input[id]]
$description[✅ • Todo salió correctamente, tu nuevo panel fue establecido.]
$color[#4f5dcd]
$setServerVar[mvkproject-tickets;$jsonStringify]
$stop
$endif
$endif
$setUserVar[mvkproject-tickets;$jsonStringify;$botID]
```
#
