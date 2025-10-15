**Ejercicio Java Script**


**Ejecución (comandos o pasos)**
// mi_ficha.js

// Declaración de variables
let nombre = "Cinthya"; // string
let edad = 40; // number
let estudiandoAutomatizacion = true; // boolean
let hobbies = ["Nadar", "Netflix", "Viajar"]; // array

// Mostrar información en pantalla
console.log("Nombre:", nombre);
console.log("Edad:", edad);
console.log("¿Estudiando automatización en APIs?:", estudiandoAutomatizacion);
console.log("Hobbies:", hobbies);

// Mostrar el tipo de cada variable usando typeof
console.log("Tipo de 'nombre':", typeof nombre);
console.log("Tipo de 'edad':", typeof edad);
console.log("Tipo de 'estudiandoAutomatizacion':", typeof estudiandoAutomatizacion);
console.log("Tipo de 'hobbies':", typeof hobbies);

let nuevoHobby = "leer"

// Agregar el nuevo hobby al array
hobbies.push(nuevoHobby);

// Mostrar el nuevo listado de hobbies
console.log("Tu lista actualizada de hobbies es:", hobbies);

// Mostrar cuántos hobbies hay en total
console.log("Número total de hobbies:", hobbies.length);

// Sumar 1 a la edad
edad = edad + 1;

// Mostrar la nueva edad
console.log("¡Feliz cumpleaños! Ahora tienes:", edad, "años");


**Evidencia**

<img width="1104" height="540" alt="image" src="https://github.com/user-attachments/assets/e90cc9b3-011d-498b-8813-2ea5478f42b6" />

-------------------------------------------------------------------------------------------------------------------

**Ejercicio de Postman** 

MiniDesafio_JS.

Crear un nuevo request 

Método: GET
URL: https://jsonplaceholder.typicode.com/posts/1

**Scenarios**

1.Que el código de estado de la respuesta sea 200.

2.Que la respuesta tenga la propiedad "id".

3.Que el campo "userId" sea un número.

**Post Response** 

//Test 1 - el codigo debe ser 200
pm.test("El código de estado es 200", function () {
    pm.response.to.have.status(200);
});

//Test 2 - validar la propiedad ID
pm.test("La respuesta tiene la propiedad id", function () {
    var jsonData = pm.response.json();
    pm.expect(jsonData).to.have.property("id");
});

//Test  - el ID es un numero 
pm.test("The ID is a number ", function () {
    var jsonData = pm.response.json();
    pm.expect(jsonData.id).to.be.a("Number")
})

**<img width="818" height="564" alt="image" src="https://github.com/user-attachments/assets/47bef1b4-2a3e-4ccd-875b-c73a98ba303b" />









 

