# Pauta I1

## Parte 1 (40%) - Preguntas Teóricas

1. Las diferencias principales son el scope y el comportamiento. El scope de `var` es de función, mientras que el scope de `const` es de bloque. Otra de las diferencias es que una variable definida con `var` puede cambiar su valor, mientras que usando `const` no se puede alterar el valor.

**Pauta:** 1 pt por explicar scope y 1pt por explicar el tema de cambio de valor.

2. Esto se puede hacer porque los objetos y los arreglos tienen la propiedad de "mutar", por eso funciona. Si crearamos un objeto nuevo (u otro valor) y tratáramos de asignárselo a `a` (no a una propiedad de `a`), fallaría igual que el otro caso.

**Pauta:** 1 pt por explicar que los objetos mutan y 1pt por el ejemplo en que `a` falla.

3. Los códigos de respuesta se utilizan para indicar como fue el resultado del request. Aquí hay varios ejemplos: los 2XX para éxito, los 3XX para redirección, los 4XX para error de cliente, los 5XX para error del servidor.

**Pauta:** 1 pt por explicar para que sirven y 1pt por el ejemplo.

4. El último termino impide que, si todos las casillas tienen el valor `null`, la condición sea `true` y gane el jugador.

**Pauta:** 2 pt por explicar para que sirve la condición de forma clara. 0 pt en otro caso.

5. La característica es herencia. También es válido indicar que los estilos se aplican en cascada (como indica el nombre).

**Pauta:** 2 pt por explicar la característica.

6. Una función que está definida como `async` implica que es una función asíncrona y que **siempre** retornará un promesa.

**Pauta:** 2 pt por explicar que la afirmación es falsa ya que tiene implicancias en el retorno por retornar una promesa.

7. Si se está trabajando en una *feature branch* y se deben hacer modificaciones a un modelo, al realizar la migración en esa rama implicará que la rama `master` u otra tendrá una definición de base de datos distinta.

**Pauta:** 1 pt por explicar que las migraciones permiten realizar modificaciones en la base  de datos y 1 pt por la explicación de cómo tener ambos esquemas.

8. HTML: Estructura, CSS: aspecto y JavaScript: comportamiento.

**Pauta:** 2 pt por tener todo bien, 1.2 pts por dos buenos y 0.6 pts con uno bueno.

9. Una vez que el request llega al servidor, pasa por una serie de *middlewares* hasta que llega al router (que es otro *middleware*). Ahí se busca el path para hacer match con una ruta y realizar lo que está descrito en el código, que generalmente es una operación que tiene operaciones a nivel de base de datos. Finalmente se procesa la vista y se envía la respuesta al cliente.

**Pauta:** 2 pt por tener todo bien. Se considerará bueno también que haya explicado que el request llega al router. 1 pt si falta algún paso de los anteriores. 0 pt si faltan 2 o más pasos.

10. Las redirecciones desde sitios HTTP a HTTPS se realizan con una redirección HTTP (código 3XX). Como ejemplo está la página web de ingeniería (vista en clases).

**Pauta:** 1 pt por el ejemplo y 1 pt por explicación.

## Parte 2 (60%) - Preguntas Prácticas

**Pauta General:** Considerar que no se espera que los alumnos tengan sintaxis perfecta en esta parte. La pauta, para cada pregunta, indica el máximo a obtener por distintos hitos cumplidos (y solicitados en el enunciado). Los descuentos deben hacerse sobre esos puntajes, para cada uno de los hitos.

Finalmente, existen varias formas de lograr el objetivo. Se debe considerar que existen soluciones adicionales a las planteadas.

### Parte A (60%): Funciones Sı́ncronas y Ası́ncronas

1.
```
Obteniendo la informacion
Distancia al sol: 1.5
Satelites: ['Moon']
{ name: 'Earth' }
```
No siempre es igual, ya que si las funciones asíncronas demoran más los mensajes estarán desordenados.

 **Pauta:** 0.5 pts por indicar que el output no siempre es igual por las funciones asíncronas y 0.5 pt por el *output*. Para esto último, el primer mensaje debe ser igual a esta respuesta y los otros pueden estar desordenados.

 2.
 ```javascript
 function getPlanetSummary (planet) {
     const planetSummary = { name: planet };
     return planetInfo.getDistanceFromSunPromise(planet)
        .then ((distance) => {
            planetSummary.distanceFromSun = distance;
            return planetInfo.getSatellitesNamesPromise(planet);
        })
        .then ((satellites) => {
            planetSummary.satellites = satellites.map(planetInfo.getSatelliteInfo);
            return planetSummary;
        });
 }
 ```

 **Pauta:** 1 pt por retornar correctamente el objeto. 1 pt por usar `then` correctamente (la función síncrona no tiene `then` ya que no es promesa) y 1 pt por retornar la promesa.

 3.
 ```javascript
 async function getPlanetSummary (planet) {
     const distance = await planetInfo.getDistanceFromSunPromise(planet);
     const satellites = await planetInfo.getSatellitesNamesPromise(planet);
     return {
         name: planet,
         distanceFromSun: distance,
         satellites: satellites.map(planetInfo.getSatelliteInfo),
     };
 }
 ```
 **Pauta:** 1 pt por usar correctamente `async/await`, no se debe ocupar `await` en la función síncrona. 1 pt por retornar lo pedido. Considerar correcto si en vez de usar la función `map` se usa un arreglo con `forEach` u otro mecanismo para obtener la información de los satélites.

### Parte B (40%): HTML + CSS

**Pauta:**
 * (1pt — 0.5pts HTML - 0.5 pts CSS) Header, contenedor y fondo
 * (3pts — 1 pt HTML - 2 pts CSS) Sección más vistas
 * (2pts — 1 pt HTML - 1 pt CSS) Sección testimonios

 #### HTML

 ```html
 <div id="container">
    <header>
        <h1>WebFlix</h1>
	    <p>El sitio de películas para el curso de web</p>
    </header>

    <div id="most-viewed">
        <h2>Más Vistas</h2>
	    <p>Las películas más vistas por los miembros del curso</p>
	    <div>
            <div class="movie">
                <h3>Kung Fu Panda</h3>
                <p>Película que trata de un oso que se convierte en maestro de kung fu</p>
                <p class="quantity">Vista por 20 personas</p>
            </div>
        
            <div class="movie">
                <h3>Buscando a Nemo</h3>
                <p>Un pez payaso intenta recuperar a su hijo que fue llevado por humanos</p>
                <p class="quantity">Vista por 18 personas</p>
            </div>

            <div class="movie">
                <h3>Cars</h3>
                <p>Un auto de carreras se pierde en un pueblo en donde aprende el significado de la amistad</p>
                <p class="quantity">Vista por 17 personas</p>
            </div>
	    </div>
    </div>

    <div id="testimony">
        <h2>Testimonios</h2>
	    <p class="phrase">Las películas que ven los alumnos son excelentes!</p>
	    <p class="author">Gabriel Vidal - IIC2513 - 2018</p>
    </div>
</div>
 ```

 #### CSS

 ```css
body {
  background-color: #2C3E50;
}

#container {
  margin: 0 auto;
  background-color: white;
  max-width: 900px;
  min-width: 600px;
  padding: 20px;
}

#most-viewed{
  text-align: center;
}

#most-viewed h2{
  background-color: #FAE5D3;
}

#most-viewed .movie {
  border: 1px solid black;
  display: inline-block;
  padding: 10px; 
  width: 250px;
}

.movie p {
  text-align: justify;
}

.movie .quantity {
  text-align: right;
}

#testimony {
  text-align: center;
}

#testimony h2{
  background-color: #F4ECF7;
}

#testimony .phrase {
  font-size: 24px;
  font-style: italic;
}

#testimony .author {
  text-align: right;
}
 ```
