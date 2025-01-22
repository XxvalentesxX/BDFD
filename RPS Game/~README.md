# Introducción
> Este sistema de RPS básico, consta de 2 comandos, un prefix. y una interacción. Puedes usarlo libremente, simplemente no lonhagas pasar por tuyo. Espero que les sirva, y muchas gracias.


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
        <td style="border: 1px solid black; padding: 8px;">rps</td>
        <td style="border: 1px solid black; padding: 8px;">{"game":false,"vs":null,"msg":null,"select":null}</td>
      </tr>
    </tbody>
  </table>
</div>

# Códigos
El sistema consta de **2 códigos** principales que se encargan de todo.

### [RPS Command](https://github.com/XxvalentesxX/BDFD/blob/main/RPS%20Game%2FRPS-Command.md)
- **Trigger:** Este es completamente personalizable. Ejemplo: `m!rps`.
- **Función:** Inicia un juego, ya sea con el propio bot, o contra un usuario.

### [RPS Interaction]()
- **Trigger:** Este debe ser `$onInteraction` sin [].
- **Función:** Maneja las interacciones del juego.
