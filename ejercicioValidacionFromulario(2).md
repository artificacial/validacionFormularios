---
title:
publishDate:
description:
---

¡Claro! A continuación te proporciono un segundo ejemplo de un formulario con validaciones y estilos. Este formulario estará enfocado en la recolección de datos para una solicitud de empleo.

### Enunciado del Ejercicio

**Objetivo:**

Desarrollar un formulario web para la solicitud de empleo, aplicando todas las medidas posibles de validación en el frontend. Se deberán implementar las siguientes validaciones:

1. **Nombre completo (full name):**

   - Obligatorio
   - Mínimo 5 caracteres, máximo 50

2. **Correo electrónico (email):**

   - Obligatorio
   - Formato válido de correo electrónico

3. **Número de teléfono (phone number):**

   - Obligatorio
   - Debe seguir el formato internacional (+1234567890)

4. **Dirección (address):**

   - Obligatorio
   - Mínimo 10 caracteres, máximo 100

5. **Fecha de disponibilidad (availability date):**

   - Obligatorio
   - Formato válido de fecha (dd/mm/yyyy)
   - No puede ser una fecha pasada

6. **Currículum (resume):**

   - Obligatorio
   - Solo formatos PDF o DOC/DOCX
   - Tamaño máximo 2MB

7. **Aceptación de términos y condiciones:**
   - Obligatorio

**Instrucciones:**

1. Crear un archivo HTML con el formulario.
2. Añadir las validaciones usando JavaScript en el frontend.
3. Utilizar elementos HTML5 y atributos de validación cuando sea posible.
4. Implementar mensajes de error personalizados para cada campo.
5. Aplicar estilos CSS para mejorar la apariencia del formulario.

### Solución del Ejercicio con Estilos

**HTML y CSS:**

```html
<!DOCTYPE html>
<html lang="es">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Solicitud de Empleo</title>
    <style>
      body {
        font-family: Arial, sans-serif;
        background-color: #e0e0e0;
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
        width: 500px;
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
      input[type="tel"],
      input[type="date"],
      input[type="file"],
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
        background-color: #007bff;
        border: none;
        border-radius: 4px;
        color: white;
        font-size: 16px;
        cursor: pointer;
      }
      button:hover {
        background-color: #0056b3;
      }
    </style>
  </head>
  <body>
    <div class="container">
      <h2>Solicitud de Empleo</h2>
      <form id="applicationForm">
        <div class="form-group">
          <label for="fullName">Nombre completo:</label>
          <input
            type="text"
            id="fullName"
            name="fullName"
            required
            minlength="5"
            maxlength="50"
          />
          <span class="error" id="fullNameError">Nombre completo inválido</span>
        </div>
        <div class="form-group">
          <label for="email">Correo electrónico:</label>
          <input type="email" id="email" name="email" required />
          <span class="error" id="emailError">Correo electrónico inválido</span>
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
          />
          <span class="error" id="addressError">Dirección inválida</span>
        </div>
        <div class="form-group">
          <label for="availabilityDate">Fecha de disponibilidad:</label>
          <input
            type="date"
            id="availabilityDate"
            name="availabilityDate"
            required
          />
          <span class="error" id="availabilityDateError"
            >Fecha de disponibilidad inválida</span
          >
        </div>
        <div class="form-group">
          <label for="resume">Currículum:</label>
          <input
            type="file"
            id="resume"
            name="resume"
            required
            accept=".pdf,.doc,.docx"
          />
          <span class="error" id="resumeError"
            >Currículum inválido (solo PDF o DOC, máximo 2MB)</span
          >
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
          <button type="submit">Enviar Solicitud</button>
        </div>
      </form>
    </div>

    <script>
      document
        .getElementById("applicationForm")
        .addEventListener("submit", function (event) {
          let valid = true;

          // Validación de nombre completo
          const fullName = document.getElementById("fullName");
          const fullNameError = document.getElementById("fullNameError");
          if (!fullName.checkValidity()) {
            fullNameError.style.display = "block";
            valid = false;
          } else {
            fullNameError.style.display = "none";
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

          // Validación de fecha de disponibilidad
          const availabilityDate = document.getElementById("availabilityDate");
          const availabilityDateError = document.getElementById(
            "availabilityDateError"
          );
          const today = new Date();
          const availabilityDateValue = new Date(availabilityDate.value);
          if (availabilityDateValue < today) {
            availabilityDateError.style.display = "block";
            valid = false;
          } else {
            availabilityDateError.style.display = "none";
          }

          // Validación de currículum
          const resume = document.getElementById("resume");
          const resumeError = document.getElementById("resumeError");
          const allowedExtensions = /(\.pdf|\.doc|\.docx)$/i;
          const maxSize = 2 * 1024 * 1024; // 2MB
          if (
            !allowedExtensions.exec(resume.value) ||
            resume.files[0].size > maxSize
          ) {
            resumeError.style.display = "block";
            valid = false;
          } else {
            resumeError.style.display = "none";
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

### Explicación de los Estilos CSS

1. **Estructura General:**
   - El `body` se centra en la pantalla con flexbox y tiene

un fondo gris claro (`#e0e0e0`).

- Se crea una `div` contenedora con la clase `container` que tiene un fondo blanco, bordes redondeados y una sombra para darle un aspecto de tarjeta.

2. **Encabezado:**

   - El encabezado (`h2`) se centra y tiene un margen inferior para separarlo del formulario.

3. **Elementos del Formulario:**

   - Cada `div` con la clase `form-group` agrupa los elementos de entrada y etiquetas.
   - Las etiquetas (`label`) se muestran como bloques con un margen inferior.
   - Los campos de entrada (`input`) tienen un ancho que se ajusta al contenedor, con un ligero padding y bordes redondeados.

4. **Errores:**

   - Los mensajes de error (`span.error`) se muestran en rojo, con un tamaño de fuente más pequeño y un margen superior para separarlos del campo de entrada correspondiente.

5. **Botón de Envío:**
   - El botón (`button`) tiene un color de fondo azul, bordes redondeados y cambia de color al pasar el cursor por encima (`hover`).
