**Challenge 1 - Users** 

**Objetivo / Historia de usuario**

Usar variables y Scripts post response

**Scenarios-Criterios de aceptación**
1. GET /api/users debe devolver HTTP 200.
2. La lista de usuarios no debe estar vacía y cada usuario debe contener id, first_name, last_name y email.

**Ejecución (comandos o pasos)**

// Parseamos la respuesta
var jsonData = pm.response.json();

// Test 1: Validar código HTTP 200
pm.test("El código de estado es 200", function () {
    pm.response.to.have.status(200);
});

// Test 2: Validar que hay al menos un comentario
pm.test("La lista de comentarios no está vacía", function () {
    pm.expect(jsonData.data.length).to.be.above(0);
});

// Test 3: Validar estructura de cada comentario
pm.test("Cada comentario tiene  ,id, name, email  avatar", function () {
    jsonData.data.forEach(function(comment) {
        pm.expect(comment).to.have.all.keys( "id","email","first_name","last_name","avatar");
    });
});

**Resultados** 

<img width="659" height="578" alt="image" src="https://github.com/user-attachments/assets/4c3f9e36-dede-4b1c-9c8c-27b199a6fdc9" />

------------------------------------------------------

**Challenge 1- Register**

**Objetivo / Historia de usuario**

Usar variables y Scripts post response

**Scenarios-Criterios de aceptación**
1.POST /api/register con payload válido devuelve HTTP 200.
2.La respuesta debe incluir un id y un token

**Ejecución (comandos o pasos)**
{
  "username": "George",
  "email": "george.bluth@reqres.in",
  "password": "12345"
}

**Resultados** 

La  API tiene defecto 

<img width="748" height="629" alt="image" src="https://github.com/user-attachments/assets/b9ebadd8-3e3c-47d4-87c4-4e7fa50a32c9" />

---------------------------------------------------------------------------------------------
**Challenge 1- Login**

**Objetivo / Historia de usuario**

Usar variables y Scripts post response

**Scenarios-Criterios de aceptación**
1.POST /api/login con credenciales válidas devuelve HTTP 200.
2.La respuesta debe contener un token para autenticación.

**Ejecución (comandos o pasos)**
{
  "username": "George",
  "email": "george.bluth@reqres.in",
  "password": "12345"
}


**Resultados** 

<img width="657" height="571" alt="image" src="https://github.com/user-attachments/assets/f1e4630b-911f-4970-b615-21bc923d66b6" />

----------------------------------------------------------------------------------


**Challenge 2 - Users** 

**Objetivo / Historia de usuario**

Usar variables , Script pre - request y Scripts post response

**Scenarios-Criterios de aceptación**

Pre-test recomendado:

1.Validar que la URL esté definida correctamente.

Post-test recomendado:

1.Verificar que el código de estado HTTP sea 200.
2.Validar que la lista de usuarios no esté vacía.
3.Confirmar que cada usuario tenga los campos requeridos y tipos de datos correctos.
4.Validar que los id sean números positivos y que los emails contengan @.

**Ejecución (comandos o pasos)**

Pre- request


// Pre-Test: validar que la URL esté definida
  if (!pm.request.url.toString().includes("/users")) {
      throw new Error("La URL no contiene '/users'");
  }

  Post Response
  // Parseamos la respuesta
var jsonData = pm.response.json();

// Test 1: Validar código HTTP 200
pm.test("El código de estado es 200", function () {
    pm.response.to.have.status(200);
});

// Test 2: Validar que hay al menos un comentario
pm.test("La lista de comentarios no está vacía", function () {
    pm.expect(jsonData.data.length).to.be.above(0);
});

// Test 3: Validar estructura de cada comentario
pm.test("Cada comentario tiene  ,id, name, email  avatar", function () {
    jsonData.data.forEach(function(comment) {
        pm.expect(comment).to.have.all.keys( "id","email","first_name","last_name","avatar");
    });
});

// Test 4: Validar que los IDs son números positivos
pm.test("Los IDs de los comentarios son números positivos", function () {
    jsonData.data.forEach(function(comment) {
        pm.expect(comment.id).to.be.a("number").and.to.be.above(0);
    });
});
// Test 5: Validar que los emails contienen '@'
pm.test("Todos los emails contienen '@'", function () {
    jsonData.data.forEach(function(comment) {
        pm.expect(comment.email).to.include("@");
    });
});

**Resultados**

<img width="697" height="617" alt="image" src="https://github.com/user-attachments/assets/b92dfc05-dc7a-4cbd-9359-1f2933ff04e5" />


  

