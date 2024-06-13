---
title: Formulario con validación HTML 5.
publishDate: 9 Jun 2024.
description: Desarrollar un formulario web completo para la recogida de datos de registro de usuario, aplicando todas las medidas posibles de validación en el frontend.
---

### Enunciado del Ejercicio

**Objetivo:**

Desarrollar un formulario web completo para la recogida de datos de registro de usuario, aplicando todas las medidas posibles de validación en el frontend. Se deberán implementar las siguientes validaciones:

1. **Nombre de usuario (username):**

   - Obligatorio
   - Mínimo 3 caracteres, máximo 15
   - Solo caracteres alfanuméricos

2. **Correo electrónico (email):**

   - Obligatorio
   - Formato válido de correo electrónico

3. **Contraseña (password):**

   - Obligatorio
   - Mínimo 8 caracteres
   - Debe contener al menos una letra mayúscula, una minúscula, un número y un carácter especial

4. **Confirmación de contraseña (confirm password):**

   - Obligatorio
   - Debe coincidir con la contraseña

5. **Fecha de nacimiento (date of birth):**

   - Obligatorio
   - Formato válido de fecha (dd/mm/yyyy)
   - El usuario debe ser mayor de 18 años

6. **Número de teléfono (phone number):**

   - Obligatorio
   - Debe seguir el formato internacional (+1234567890)

7. **Dirección (address):**

   - Obligatorio
   - Mínimo 10 caracteres, máximo 100
   - No debe contener caracteres especiales

8. **Código postal (postal code):**

   - Obligatorio
   - Solo caracteres numéricos
   - Exactamente 5 dígitos

9. **Aceptación de términos y condiciones:**
   - Obligatorio

**Instrucciones:**

1. Crear un archivo HTML con el formulario.
2. Añadir las validaciones usando JavaScript en el frontend.
3. Utilizar elementos HTML5 y atributos de validación cuando sea posible.
4. Implementar mensajes de error personalizados para cada campo.

### Solución del Ejercicio

**HTML:**

```html
<!DOCTYPE html>
<html lang="es">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Formulario de Registro</title>
    <style>
      body {
        font-family: Arial, sans-serif;
        background-color: #f4f4f4;
        display: flex;
        justify-content: center;
        align-items: center;
        height: 100vh;
        margin: 0;
      }
      .container {
        background-color: #fff;
        padding: 20px;
        border-radius: 8px;
        box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
        width: 400px;
      }
      h2 {
        text-align: center;
        margin-bottom: 20px;
        color: #333;
      }
      .form-group {
        margin-bottom: 15px;
      }
      label {
        display: block;
        margin-bottom: 5px;
        color: #333;
      }
      input[type="text"],
      input[type="email"],
      input[type="password"],
      input[type="date"],
      input[type="tel"],
      input[type="checkbox"] {
        width: calc(100% - 22px);
        padding: 10px;
        border: 1px solid #ddd;
        border-radius: 4px;
      }
      input[type="checkbox"] {
        width: auto;
        margin-right: 10px;
      }
      .error {
        color: red;
        display: none;
        font-size: 0.875em;
        margin-top: 5px;
      }
      button {
        width: 100%;
        padding: 10px;
        background-color: #5cb85c;
        border: none;
        border-radius: 4px;
        color: white;
        font-size: 16px;
        cursor: pointer;
      }
      button:hover {
        background-color: #4cae4c;
      }
    </style>
  </head>
  <body>
    <div class="container">
      <h2>Formulario de Registro</h2>
      <form id="registrationForm">
        <div class="form-group">
          <label for="username">Nombre de usuario:</label>
          <input
            type="text"
            id="username"
            name="username"
            required
            minlength="3"
            maxlength="15"
            pattern="[A-Za-z0-9]+"
          />
          <span class="error" id="usernameError"
            >Nombre de usuario inválido</span
          >
        </div>
        <div class="form-group">
          <label for="email">Correo electrónico:</label>
          <input type="email" id="email" name="email" required />
          <span class="error" id="emailError">Correo electrónico inválido</span>
        </div>
        <div class="form-group">
          <label for="password">Contraseña:</label>
          <input
            type="password"
            id="password"
            name="password"
            required
            minlength="8"
          />
          <span class="error" id="passwordError">Contraseña inválida</span>
        </div>
        <div class="form-group">
          <label for="confirmPassword">Confirmar contraseña:</label>
          <input
            type="password"
            id="confirmPassword"
            name="confirmPassword"
            required
          />
          <span class="error" id="confirmPasswordError"
            >Las contraseñas no coinciden</span
          >
        </div>
        <div class="form-group">
          <label for="dob">Fecha de nacimiento:</label>
          <input type="date" id="dob" name="dob" required />
          <span class="error" id="dobError">Debe ser mayor de 18 años</span>
        </div>
        <div class="form-group">
          <label for="phone">Número de teléfono:</label>
          <input
            type="tel"
            id="phone"
            name="phone"
            required
            pattern="\+?[0-9]{10,15}"
          />
          <span class="error" id="phoneError">Número de teléfono inválido</span>
        </div>
        <div class="form-group">
          <label for="address">Dirección:</label>
          <input
            type="text"
            id="address"
            name="address"
            required
            minlength="10"
            maxlength="100"
            pattern="[A-Za-z0-9\s]+"
          />
          <span class="error" id="addressError">Dirección inválida</span>
        </div>
        <div class="form-group">
          <label for="postalCode">Código postal:</label>
          <input
            type="text"
            id="postalCode"
            name="postalCode"
            required
            pattern="\d{5}"
          />
          <span class="error" id="postalCodeError">Código postal inválido</span>
        </div>
        <div class="form-group">
          <label>
            <input type="checkbox" id="terms" name="terms" required /> Acepto
            los términos y condiciones
          </label>
          <span class="error" id="termsError"
            >Debe aceptar los términos y condiciones</span
          >
        </div>
        <div class="form-group">
          <button type="submit">Registrarse</button>
        </div>
      </form>
    </div>

    <script>
      document
        .getElementById("registrationForm")
        .addEventListener("submit", function (event) {
          let valid = true;

          // Validación de nombre de usuario
          const username = document.getElementById("username");
          const usernameError = document.getElementById("usernameError");
          if (!username.checkValidity()) {
            usernameError.style.display = "block";
            valid = false;
          } else {
            usernameError.style.display = "none";
          }

          // Validación de correo electrónico
          const email = document.getElementById("email");
          const emailError = document.getElementById("emailError");
          if (!email.checkValidity()) {
            emailError.style.display = "block";
            valid = false;
          } else {
            emailError.style.display = "none";
          }

          // Validación de contraseña
          const password = document.getElementById("password");
          const passwordError = document.getElementById("passwordError");
          const passwordPattern =
            /^(?=.*[a-z])(?=.*[A-Z])(?=.*\d)(?=.*[@$!%*?&])[A-Za-z\d@$!%*?&]{8,}$/;
          if (!passwordPattern.test(password.value)) {
            passwordError.style.display = "block";
            valid = false;
          } else {
            passwordError.style.display = "none";
          }

          // Validación de confirmación de contraseña
          const confirmPassword = document.getElementById("confirmPassword");
          const confirmPasswordError = document.getElementById(
            "confirmPasswordError"
          );
          if (password.value !== confirmPassword.value) {
            confirmPasswordError.style.display = "block";
            valid = false;
          } else {
            confirmPasswordError.style.display = "none";
          }

          // Validación de fecha de nacimiento
          const dob = document.getElementById("dob");
          const dobError = document.getElementById("dobError");
          const today = new Date();
          const dobDate = new Date(dob.value);
          const age = today.getFullYear() - dobDate.getFullYear();
          const m = today.getMonth() - dobDate.getMonth();
          if (m < 0 || (m === 0 && today.getDate() < dobDate.getDate())) {
            age--;
          }
          if (age < 18) {
            dobError.style.display = "block";
            valid = false;
          } else {
            dobError.style.display = "none";
          }

          // Validación de número de teléfono
          const phone = document.getElementById("phone");
          const phoneError = document.getElementById("phoneError");
          if (!phone.checkValidity()) {
            phoneError.style.display = "block";
            valid = false;
          } else {
            phoneError.style.display = "none";
          }

          // Validación de dirección
          const address = document.getElementById("address");
          const addressError = document.getElementById("addressError");
          if (!address.checkValidity()) {
            addressError.style.display = "block";
            valid = false;
          } else {
            addressError.style.display = "none";
          }

          // Validación de código postal
          const postalCode = document.getElementById("postalCode");
          const postalCodeError = document.getElementById("postalCodeError");
          if (!postalCode.checkValidity()) {
            postalCodeError.style.display = "block";
            valid = false;
          } else {
            postalCodeError.style.display = "none";
          }

          // Validación de términos y condiciones
          const terms = document.getElementById("terms");
          const termsError = document.getElementById("termsError");
          if (!terms.checkValidity()) {
            termsError.style.display = "block";
            valid = false;
          } else {
            termsError.style.display = "none";
          }

          if (!valid) {
            event.preventDefault();
          }
        });
    </script>
  </body>
</html>
```

### Explicación

1. **HTML:**

   - Se crean los campos de entrada requeridos con sus respectivos atributos de validación HTML5 (`required`, `minlength`, `maxlength`, `pattern`).
   - Se añaden elementos `span` con la clase `error` para mostrar mensajes de error personalizados.

2. **CSS:**

   - Se define la clase `error` para mostrar mensajes en rojo y ocultarlos por defecto.

   ### Estructura General:

   - El body se centra en la pantalla con flexbox, y se le asigna un fondo gris claro (#f4f4f4).
   - Se crea una div contenedora con la clase container que se estiliza con un fondo blanco, bordes redondeados, y una sombra para darle un aspecto elevado.

   ### Encabezado:

   - El encabezado (h2) se centra y se le asigna un margen inferior para separarlo del formulario.

   ### Elementos del Formulario:

   - Cada div con la clase form-group agrupa los elementos de entrada y etiquetas.
   - Las etiquetas (label) se muestran como bloques con un margen inferior para separarlos del campo de entrada.
   - Los campos de entrada (input) tienen un ancho que se ajusta al contenedor, con un ligero padding y bordes redondeados.

   ### Errores:

   - Los mensajes de error (span.error) se muestran en rojo, con un tamaño de fuente más pequeño y un margen superior para separarlos del campo de entrada correspondiente.

   Botón de Envío:

   - El botón (button) tiene un color de fondo verde, bordes redondeados y cambia de color al pasar el cursor por encima (hover).

3. **JavaScript:**
   - Se agrega un evento de escucha al formulario para la validación personalizada.
   - Para cada campo, se verifica si es válido utilizando `checkValidity()` y patrones regulares (`RegExp`) cuando es necesario.
   - Se muestran u ocultan mensajes de error según corresponda.
   - Si alguna validación falla, se previene el envío del formulario usando `event.preventDefault()`.
