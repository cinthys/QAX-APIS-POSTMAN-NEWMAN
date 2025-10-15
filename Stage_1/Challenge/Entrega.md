README.md por cada entrega con:
Challenge 1 - Users 

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
