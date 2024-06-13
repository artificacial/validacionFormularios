# Ejemplos de validación de formularios incorporados

En esta sección probaremos algunos de los atributos que hemos comentado antes.

## Archivo de inicio sencillo

Vamos a empezar con un ejemplo sencillo: una entrada que te permite elegir si prefieres un plátano o una cereza. Este ejemplo implica una simple entrada (<input>) de texto con una etiqueta (<label>) asociada y un botón de envío (<button>).

```html
<form>
  <label for="choose">¿Prefieres un plátano o una cereza?</label>
  <input id="choose" name="i_like" />
  <button>Enviar</button>
</form>
```

```css
input:invalid {
  border: 2px dashed red;
}

input:valid {
  border: 2px solid black;
}
```

## El atributo required

La característica de validación de HTML5 más simple es el atributo required (en-US). Añade este atributo al elemento para que una entrada sea obligatoria. Cuando se establece este atributo, el elemento coincide con la pseudoclase de la interfaz de usuario :required y el formulario no se envía; muestra un mensaje de error al enviarlo si la entrada está vacía. Si está vacía, la entrada también se considera inválida, coincidiendo con la pseudoclase de interfaz de usuario :invalid.

Añade un atributo required a tu entrada, como se muestra a continuación.

```html
<form>
  <label for="choose">¿Prefieres un plátano o una cereza? (requerido) </label>
  <input id="choose" name="i_like" required />
  <button>Enviar</button>
</form>
```

Ten en cuenta el CSS que en el archivo de ejemplo se ha incluido:

```css
input:invalid {
  border: 2px dashed red;
}

input:invalid:required {
  background-image: linear-gradient(to right, pink, lightgreen);
}

input:valid {
  border: 2px solid black;
}
```

Este CSS da un borde discontinuo rojo cuando la entrada no es válida, y un borde negro sólido más sutil cuando es válida. También añadimos un gradiente de fondo cuando la entrada es obligatoria y no válida.

Intenta enviar el formulario sin introducir ningún valor. Observa que la entrada no válida recibe el cursor, aparece un mensaje de error predeterminado («Complete este campo») y el formulario no se puede enviar.

La presencia del atributo required en cualquier elemento que admite este atributo significa que el elemento coincide con la pseudoclase :required, tenga o no un valor. Si en el elemento <input> no se ha introducido ningún valor, input coincidirá con la pseudoclase :invalid.

> Nota: Para una buena experiencia de usuario, indica al usuario que campos de formulario se requieren. No solo es una buena experiencia de usuario, sino que lo exigen las pautas de accesibilidad de WCAG. Además, solo requiere que los usuarios introduzcan los datos que realmente necesitas: Por ejemplo, ¿por qué realmente necesitas saber el género o el tratamiento de alguien?
