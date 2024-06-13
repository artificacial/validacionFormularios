# Restringir los valores de tus entradas

Los atributos min y max (en-US) se pueden usar para proporcionar a los campos numéricos (es decir, <input type="number">) un rango de valores válidos. El campo no será válido si contiene un valor fuera de este rango.

Veamos otro ejemplo. Crea una nueva copia del archivo fruit-start.html.

Ahora elimina el contenido del elemento <body> y reemplázalo con lo siguiente:

```html
<form>
  <div>
    <label for="choose">¿Prefieres un plátano o una cereza?</label>
    <input
      type="text"
      id="choose"
      name="i_like"
      required
      minlength="6"
      maxlength="6"
    />
  </div>
  <div>
    <label for="number">¿Cuántos te gustaría comer?</label>
    <input type="number" id="number" name="amount" value="1" min="1" max="10" />
  </div>
  <div>
    <button>Enviar</button>
  </div>
</form>
```

Aquí verás que le hemos dado al campo de text unos valores minlength y maxlength de seis, que es la misma longitud que tienen el plátano y la cereza.
También le hemos dado al campo number un min de uno y un max de diez. Los números introducidos que queden fuera de este rango se mostrarán como no válidos; los usuarios no podrán usar las flechas de incremento/decremento para mover el valor fuera de este rango. Si el usuario introduce un número desde el teclado fuera de este rango, los datos no serán válidos. El número no es obligatorio, por lo que eliminar el valor aún dará como resultado un valor válido.

> Nota: Puedes encontrar este ejemplo en vivo en GitHub como fruit-length.html (consulta también su código fuente).

> Nota: <input type="number"> (y otros tipos, como range y date) también pueden tomar un atributo step (en-US), que especifica en qué incremento aumenta o disminuye el valor cuando se utilizan los controles de entrada (como el botones numéricos arriba y abajo). En el ejemplo anterior no hemos incluido un atributo step, por lo que el valor predeterminado es 1. Esto significa que los valores de coma flotante, como 3.2, también se mostrarán como no válidos.

## Ejemplo completo

Aquí hay un ejemplo completo que muestra el uso de las funciones de validación integradas en HTML. En primer lugar, un poco de HTML:

```html
<form>
  <p>
    <fieldset>
      <legend>¿Tienes carné de conducir?<abbr title="Este campo es obligatorio" aria-label="required">*</abbr></legend>
      <!-- Solo se puede seleccionar un botón de opción en un grupo con el mismo nombre,
           y, por lo tanto, solo un botón de opción en un grupo con el mismo nombre que tiene marcado el atributo «requerido»
           basta para hacer de una selección un requisito -->
      <input type="radio" required name="driver" id="r1" value="yes"><label for="r1">Sí</label>
      <input type="radio" required name="driver" id="r2" value="no"><label for="r2">No</label>
    </fieldset>
  </p>
  <p>
    <label for="n1">¿Qué edad tienes?</label>
    <!-- El atributo pattern puede actuar como una alternativa para los navegadores que
         no implementan el tipo de entrada de número, pero admiten el atributo pattern.
         Ten en cuenta que los navegadores que admiten el atributo pattern lo harán
         fallar silenciosamente cuando se use con un campo numérico.
         Su uso aquí solo actúa como una alternativa -->
     <input type="number" min="12" max="120" step="1" id="n1" name="age"
           pattern="\d+">
  </p>
  <p>
    <label for="t1">¿Cuál es tu fruta favorita?<abbr title="Este campo es obligatorio" aria-label="required">*</abbr></label>
    <input type="text" id="t1" name="fruit" list="l1" required
           pattern="[Bb]anana|[Cc]herry|[Aa]pple|[Ss]trawberry|[Ll]emon|[Oo]range ">
    <datalist id="l1">
      <option>Plátano</option>
      <option>Cereza</option>
      <option>Manzana</option>
      <option>Fresa</option>
      <option>Limón</option>
      <option>Naranja</option>
     </datalist>
  </p>
  <p>
    <label for="t2">¿Cuál es tu dirección de correo electrónico? </label>
    <input type="email" id="t2" name="email">
  </p>
  <p>
    <label for="t3">Deja un mensaje</label>
    <textarea id="t3" name="msg" maxlength="140" rows="5"></textarea>
  </p>
  <p>
    <button>Enviar</button>
  </p>
</form>
```

Y ahora, algo de CSS para añadir estilo al HTML:

```css
form {
  font: 1em sans-serif;
  max-width: 320px;
}

p > label {
  display: block;
}

input[type="text"],
input[type="email"],
input[type="number"],
textarea,
fieldset {
  width: 100%;
  border: 1px solid #333;
  box-sizing: border-box;
}

input:invalid {
  box-shadow: 0 0 5px 1px red;
}

input:focus:invalid {
  box-shadow: none;
}
```

Consulta Atributos relacionados con la validación para obtener una lista completa de los atributos que se pueden usar para restringir los valores de entrada y los tipos de entrada que los admiten.

> Nota: Puedes encontrar este ejemplo en vivo en GitHub como full-example.html (consulta también su código fuente).
