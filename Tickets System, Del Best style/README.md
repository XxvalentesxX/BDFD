# Explicación
> Es un sistema con el que podrás manejar tus tickets. Es totalmente personalizable, y se puede usar en distintos servidores. Para que todo sea posible, debes copiar y pegar todos los códigos que hay. También debes crear una simple variable que se encargará de todo.
# Variable
<div align="center">
  <table style="border: 2px solid black; border-collapse: collapse; width: 80%; text-align: left; border-radius: 10px; overflow: hidden;">
    <thead>
      <tr style="border: 2px solid black;">
        <th style="border: 1px solid black; padding: 8px;">Nombre</th>
        <th style="border: 1px solid black; padding: 8px;">Valor</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td style="border: 1px solid black; padding: 8px;">mvkproject-tickets</td>
        <td style="border: 1px solid black; padding: 8px;">{}</td>
      </tr>
    </tbody>
  </table>
</div>

# Limites
- Si bien es cierto que las variables en BDFD tienen un cierto límite, esta no es la excepción, sabiendo que cada tipo de variable tiene distintos límites, he aprovechado eso, y tiene un límite más amplio. Igualmente, eso no quita que en algún momento pueda dar un error. Para eso, estoy trabajando en la V2, y no tend´ra un límite en embeds ni nada por el estílo, pero si que seguirá habiendo un límite en paneles. Pero esto será todo customizable, hasta botones.

# Códigos
- Este sistema consta de 5 códigos que se encargan de todo. A los triggers, se les debe retirar las comillas ("").
> [Config System](), el trigger de este, es totalmente personalizable. Ejemplo: "m!config".
 - Con esto abrirás el menú de configuración, donde podrás customizar/personalzar tus sistemas.

> [Ticket Panel](), el trigger de este, también es personalizable. Ejemplo: "m!panel".
 - Envía el panel de tickets, ya configurado.

> [Embed Tags](), el trigger de este, es personalizable. Ejemplo: "m!tags"
 - Muestra las etiqutas disponibles para usar.

> [Config Interactions](), el trigger de este, debe ser: "$onInteraction".
 - Interacciones de la configuración.

> [Ticket Interactions](), el trigger de este, debe ser: "$onInteraction".
 - Interacciones del panel.
