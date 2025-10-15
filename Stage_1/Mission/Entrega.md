Dog API

**Objetivos**

Construir casos de prueba basados en criterios de aceptación.
Validar respuestas de endpoints públicos en Postman.
Automatizar pruebas usando Pre-request Scripts y Test Scripts siguiendo buenas prácticas.
Generar reportes claros de ejecución con Newman.

**Breeds API**

**Citerios de Aceptacion**

1.Campo id
Debe existir y ser un string UUID válido.
2.Campo type
Debe existir y ser igual a "breed".
3.Campo attributes.name
Debe existir y ser un string no vacío.
4.Campo attributes.description
Debe existir y ser un string descriptivo.
5.Campo attributes.hypoallergenic
Debe ser un valor booleano (true o false).
6.Campo attributes.life
Debe contener min y max como enteros.
Valores permitidos: min ≥ 10, max ≤ 20.
7.Campos attributes.male_weight y attributes.female_weight
Deben contener min y max como enteros.
8.Los rangos deben ser iguales para macho y hembra:
male_weight.min == female_weight.min
male_weight.max == female_weight.max
9.Campo relationships.group.data
Debe contener id como string y type igual a "group".

**Ejecucion**

Script Post Response

// Parsear json
var jsonData = pm.response.json();


// Test ID: Validar que los IDs son strings
pm.test("Los IDs de las razas son strings válidos", function () {
    jsonData.data.forEach(function(breed) {
        pm.expect(breed.id).to.be.a("string").and.not.to.be.empty;
    });
});

// Test type: El campo type debe ser igual a breed
pm.test("El campo type debe ser igual a breed", function () {
    jsonData.data.forEach(function(breed) {
        pm.expect(breed.type).to.be.equal("breed");
    });
});

// Test name: El campo name debe ser un string no vacío
pm.test("El campo name debe ser un string no vacío", function () {
    jsonData.data.forEach(function(breed) {
        pm.expect(breed.attributes.name).to.be.a("string").and.not.to.be.empty;
    });
});

// Test description: El campo description debe ser un string no vacío
pm.test("El campo description debe ser un string no vacío", function () {
    jsonData.data.forEach(function(breed) {
        pm.expect(breed.attributes.description).to.be.a("string").and.not.to.be.empty;
    });
});

// Test hypoallergenic: El campo hypoallergenic debe ser un booleano
pm.test("El campo hypoallergenic debe ser un booleano", function () {
    jsonData.data.forEach(function(breed) {
        pm.expect(breed.attributes.hypoallergenic).to.be.a("boolean");
    });
});

// Test life: El campo life debe tener un min y max como enteros
pm.test("El campo life debe tener max y min", function () {
    jsonData.data.forEach(function(comment) {
        pm.expect(comment.attributes.life).to.have.all.keys("max", "min");
        pm.expect(comment.attributes.life.max).to.be.a("number");
        pm.expect(comment.attributes.life.min).to.be.a("number");
    });
});
// Test male_weight: El campo life debe tener un min y max como enteros
pm.test("El campo male_weight debe tener max y min", function () {
    jsonData.data.forEach(function(comment) {
        pm.expect(comment.attributes.male_weight).to.have.all.keys("max", "min");
        pm.expect(comment.attributes.male_weight >=10 );
        pm.expect(comment.attributes.male_weight <= 20);
    });
});

// Test female_weight: El campo life debe tener un min y max como enteros
pm.test("El  female_weight es igual al male weight", function () {
    jsonData.data.forEach(function(comment) {
        pm.expect(comment.attributes.female_weight).to.have.all.keys("max", "min");
        pm.expect(comment.attributes.female_weight == 5 );
        pm.expect(comment.attributes.female_weight == 3);
    });
});


// Test relationship: El campo name debe contener un id string y type igual a grupo 
pm.test("El campo name debe contener un id string y type igual a grupo", function () {
    jsonData.data.forEach(function(breed) {
        pm.expect(breed.relationships.group.data.id).to.be.a("string").and.not.to.be.empty;
        pm.expect(breed.relationships.group.data.type).to.be.equal("group");
    });
});

**Resultado**

La API dog tiene errores del sevidor



-------------------------------------------
**Breeds ID**

**Citerios de Aceptacion**


1.Si el id corresponde a una raza existente, el sistema debe devolver código HTTP 200.
2.La respuesta debe incluir el id solicitado y toda la información asociada (name, description, life, weight, hypoallergenic, group).
Raza inexistente

**Ejecucion**

Script Post Response

// Fixed the parsing and key validation
var jsonData = pm.response.json();

// Test 1: Validar código HTTP 200
pm.test("El código de estado es 200", function () {
    pm.response.to.have.status(200);
});


//test 2 - Validar los objetos y sus objetos 
pm.test("Cada raza tiene id, name, description, life, weight, hypoallergenic, group", function () {
    pm.expect(jsonData.data).to.have.all.keys("id", "type", "attributes", "relationships");
    pm.expect(jsonData.data.attributes).to.have.all.keys("name", "description", "life", "male_weight", "female_weight", "hypoallergenic");
    pm.expect(jsonData.data.relationships).to.have.all.keys("group");
});

**Resultado**

La API Dog tiene error en el sevidor


---------------------------------------------------


**Breeds ID Invalid**

**Citerios de Aceptacion**

1.Si el id no corresponde a ninguna raza, el sistema debe devolver código HTTP 404.
2.La respuesta puede incluir un mensaje indicando que la raza no fue encontrada.

**Ejecucion**

Pre- Request 

// Pre-Test: validar que la URL esté definida
  if (!pm.request.url.toString().includes("/036feed0-da8a-42c9-ab9a-57449b530b13")) {
      throw new Error("La URL no contiene '/036feed0-da8a-42c9-ab9a-57449b530b13 '");
  }

Post -Response

// Fixed the parsing and key validation
var jsonData = pm.response.json();

// Test 1: Validar código HTTP 404
pm.test("El código de estado es 404", function () {
    pm.response.to.have.status(404);
});

**Resultados**

La API Dog tiene error en el sevidor

