# Validación de una expresión regular

Otra característica útil de validación es el atributo pattern (en-US), que espera una expresión regular como valor. Una expresión regular (regex) es un patrón que se puede usar para establecer combinaciones de caracteres en cadenas de texto, por lo que las expresiones regulares son ideales para la validación de formularios y sirven para una gran variedad de otros usos en JavaScript.

Las expresiones regulares son bastante complejas y no vamos a exponerlas exhaustivamente en este artículo. A continuación hay algunos ejemplos para que te hagas una idea de cómo funcionan.

- a: coincide con un carácter que es a (ni b, ni aa, etc.).
- abc: coincide con a, seguido de b, seguido de c.
- ab?c: coincide con a, seguida opcionalmente de una sola b, seguida de c (ac o abc).
- ab\*c: coincide con a, seguido opcionalmente de cualquier número de b, seguido de c. (ac, abc, abbbbbc, etc.)
- a|b: coincide con un carácter que es a o b.
- abc|xyz: coincide exactamente con abc o xyz (pero no con abcxyz a o y, y así sucesivamente).

Hay muchas más posibilidades que no exponemos aquí. Para obtener una lista completa y muchos ejemplos, consulta nuestro documento de expresiones regulares.

Implementemos un ejemplo. Actualiza tu HTML para añadir un atributo pattern (en-US) como este:

```html
<form>
  <label for="choose">¿Prefieres un plátano o una cereza?</label>
  <input id="choose" name="i_like" required pattern="[Pp]látano|[Cc]ereza " />
  <button>Enviar</button>
</form>
```

> Nota: Puedes encontrar este ejemplo en vivo en GitHub como fruit-pattern.html (consulta también su código fuente).

En este ejemplo, el elemento <input> acepta uno de los cuatro valores posibles: las cadenas «plátano», «Plátano», «cereza» o «Cereza». Las expresiones regulares distinguen entre mayúsculas y minúsculas, pero hemos hecho que admita versiones en mayúsculas y minúsculas utilizando un patrón «Aa» adicional anidado dentro de corchetes.

En este punto, intenta cambiar el valor dentro del atributo pattern (en-US) para que se vean iguales que algunos de los ejemplos vistos anteriormente, y observa que esto afecta a los valores que puedes añadir para que el valor de entrada sea válido. Intenta escribir algo por tu cuenta y mira cómo va. ¡Haz que estén relacionadas con la fruta siempre que sea posible para que tus ejemplos tengan sentido!

Si un valor no vacío de <input> no coincide con el patrón de la expresión regular, input coincidirá con la pseudoclase :invalid.

> Nota: Algunos tipos de elementos <input> no necesitan validar una expresión regular con el atributo pattern (en-US). Especificar el tipo de correo electrónico (email), por ejemplo, valida el valor de las entradas con un patrón de dirección de correo electrónico bien formado o un patrón que coincida con una lista de direcciones de correo electrónico separadas por comas si tiene el atributo multiple.

> Nota: El elemento <textarea> no admite el atributo pattern (en-US).
