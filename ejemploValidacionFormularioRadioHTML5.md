Claro, aquí tienes un ejemplo de un formulario simple en el que el usuario debe elegir entre dos opciones y luego presionar el botón de enviar. Además, se incluye el código CSS para aplicar estilos a los campos de formulario según su estado de validación:

```html
<!DOCTYPE html>
<html lang="es">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Formulario de Elección</title>
    <style>
      /* Estilos para los campos de formulario */
      input[type="radio"] {
        margin-right: 10px;
      }

      label {
        display: block;
        margin-bottom: 10px;
      }

      input[type="submit"] {
        background-color: #4caf50;
        color: white;
        padding: 10px 20px;
        border: none;
        cursor: pointer;
        border-radius: 5px;
      }

      /* Estilos para campos válidos e inválidos */
      input:valid {
        border: 2px solid green;
      }

      input:invalid {
        border: 2px solid red;
      }
    </style>
  </head>
  <body>
    <form>
      <label>
        <input type="radio" name="opcion" value="opcion1" required /> Opción 1
      </label>
      <label>
        <input type="radio" name="opcion" value="opcion2" required /> Opción 2
      </label>
      <input type="submit" value="Enviar" />
    </form>
  </body>
</html>
```

En este ejemplo, se utilizan dos botones de opción (`input type="radio"`) dentro de etiquetas `<label>`. Ambos botones de opción tienen el atributo `required`, lo que significa que el usuario debe seleccionar al menos una de las opciones antes de enviar el formulario. Además, se proporciona un botón de enviar (`input type="submit"`) que el usuario puede presionar una vez que haya hecho su elección.

En cuanto al estilo CSS, se definen estilos para los campos de formulario, como márgenes y rellenos para los botones de opción y el botón de enviar. Además, se aplican estilos específicos utilizando las pseudo-clases `:valid` e `:invalid` para cambiar el color del borde del campo de entrada dependiendo de si está válido o no. Cuando un campo es válido, se le aplica un borde verde (`border: 2px solid green`), y cuando es inválido, se le aplica un borde rojo (`border: 2px solid red`). Estos estilos ayudan a proporcionar retroalimentación visual instantánea al usuario sobre el estado de validación del formulario.
