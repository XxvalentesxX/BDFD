# Explicación
> Este sistema te permite gestionar tus tickets de manera personalizada. Es totalmente adaptable y puede ser utilizado en distintos servidores. Para que todo funcione correctamente, debes copiar y pegar todos los códigos proporcionados. Además, necesitarás crear una simple variable que gestionará todo el sistema.

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

# Límites
- Aunque es cierto que las variables en BDFD tienen un límite, este sistema no es la excepción. Cada tipo de variable tiene diferentes restricciones, pero hemos optimizado el uso para que este sistema tenga un límite más amplio. 
- Sin embargo, en casos extremos, podrías encontrar errores debido a estas limitaciones. Para solucionar este problema, estamos trabajando en la **V2**, que eliminará las restricciones relacionadas con embeds y otros aspectos visuales. 
- En la **V2**, los límites en los paneles seguirán existiendo, pero todo será altamente personalizable, incluyendo botones, textos, y más.

# Códigos
El sistema consta de **5 códigos** principales que se encargan de todo. **Nota:** A los triggers debes retirar las comillas (`""`) antes de usarlos.

### [Config System]()
- **Trigger:** Este es completamente personalizable. Ejemplo: `m!config`.
- **Función:** Abre el menú de configuración, donde podrás personalizar el sistema a tu gusto.

### [Ticket Panel]()
- **Trigger:** Este también es personalizable. Ejemplo: `m!panel`.
- **Función:** Envía el panel de tickets ya configurado.

### [Embed Tags]()
- **Trigger:** Personalizable. Ejemplo: `m!tags`.
- **Función:** Muestra las etiquetas disponibles que puedes usar para personalizar los mensajes.

### [Config Interactions]()
- **Trigger:** Este debe ser `"$onInteraction"`.
- **Función:** Gestiona las interacciones del menú de configuración.

### [Ticket Interactions]()
- **Trigger:** Este debe ser `"$onInteraction"`.
- **Función:** Gestiona las interacciones del panel de tickets, como crear, cerrar o responder un ticket.

