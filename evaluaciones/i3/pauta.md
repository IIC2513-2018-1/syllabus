# Pauta I2

## Parte 1 (20%) - Preguntas Teóricas

1. Al cambiar el estado, por medio de la función `this.setState()`, se gatillan otros procesos internos de `React` (por ejemplo un render). Esto no pasa al hacer el cambio directamente en el objeto.

**Pauta:** 1 pt por explicación.

2. Crear un test, escribir el código para el test pase y, una vez que el test pasa, mejorar el código escrito. Las ventajas es que siempre hay un test que prueba una funcionalidad, pero una de las desventajas es que, en algunos casos, se pierde el objetivo en el comportamiento de la feature más allá del test unitario.

**Pauta:** 1 pt por explicación.

3. Integración Continua. Si no sabe el nombre, puede explicar el proceso.

**Pauta:** 1 pt por explicación.

4. *dumb* component: sin estado y generalmente retorna `JSX` (escrito en forma de función).
*smart* component: con estado y con formato de clases. Generalmente se encarga de la obtención de la información en APIs.

**Pauta:** 1 pt por explicación.

5. Con técnicas de versionamiento, que permiten agregar funcionalidades sin romper los clientes que la implementan.

**Pauta:** 1 pt por explicación.

6. Layout líquido es aquel que se adapta a los cambios de tamaño del navegador (tal como el ejemplo visto en clases). Generalmente se escriben reglas de CSS con porcentajes. En algunos casos se deforman los contenidos o no quedan en la posición que uno quiere (ver ejemplo de clases), por lo que las *media queries* vienen al rescate.

**Pauta:** 1 pt por explicación.


## Parte 2 (80%) - Preguntas Prácticas

**Pauta General:** Considerar que no se espera que los alumnos tengan sintaxis perfecta en esta parte o recuerde todos los nombres de los métodos existentes. Sin embargo, se debe ser rígidos en la escritura correcta de funciones y utilización de variables. Además se espera que el alumno haya alcanzado el nivel de decidir qué solución es mejor que otra.

La pauta, para cada pregunta, indica el máximo a obtener por distintos hitos cumplidos (y solicitados en el enunciado). Los descuentos deben hacerse sobre esos puntajes, para cada uno de los hitos.

Finalmente, existen varias formas de lograr el objetivo. Se debe considerar que existen soluciones adicionales a las planteadas.

### Parte A (10%): CSS

```CSS
.topnav {
    background-color: #333;
}

.topnav a {
    display: 'inline-block';
    padding: 10px;
    color: #f2f2f2;
    text-decoration: none;
}

.topnav a:hover {
    background-color: #ddd;
    color: black;
}

@media screen and (max-width: 600px) {
  .topnav a {
    display: 'block';
    width: 100%;
  }
}
```
**Pauta:**
  * 6 pts por las reglas correctas. Podría haber más de una solución en este caso.

### Parte B (30%): API

**Pregunta 1** (1 pt):

Lo necesario es:
* Dos modelos, curso (`course`) y evaluación docente (`survey`). Cada uno de ellos con los parámetros indicados en el enunciado

* La relación entre ellos debería ser que un curso tiene muchas evaluaciones y que una evaluación es de un curso (1:N).

**Pregunta 2** (2 pts):

|Metodo|URL            |Descripción|
| -----|:-------------:| --------- |
|GET   |/courses/:id/surveys| Obtener todas las encuestas de un curso|
|GET   |/courses/:id/survey/:idSurvey| Obtener una encuesta docente de un curso|
|POST  |/courses/:id/survey/:idSurvey| Agregar una encuesta docente a un curso|
|PATCH |/courses/:id/survey/:idSurvey| Editar una encuesta docente de un curso|
|DELETE|/courses/:id/survey/:idSurvey| Eliminar una encuesta docente dea un curso|

**Pregunta 3** (3 pts):

```javascript
router.get('courses.surveys', '/courses/:id/surveys', async (ctx) => {
  try {
    const course = await ctx.orm.course.findById(ctx.params.id);

    if (!course) {
      ctx.body = {
        status: 'ERROR',
        error: 'Curso no encontrado',
      };
    } else {
      ctx.body = {
        id: course.id,
        name: course.name,
        surveys: await course.getSurveys(),
      };
    }
  } catch(err) {
    ctx.body = {
      status: 'ERROR',
      error: 'Ha ocurrido un error inesperado',
    };
  }
});
```

### Parte C (60%): React

```jsx
/* /src/assets/js/components/Movie.jsx  */

import React from 'react';
import PropTypes from 'prop-types';

export default function Movie(props) {
  return (
    <div>
      <h2>{props.name}</h2>
      <p>{props.description}</p>
      <p>Vista por {props.people} personas</p>
      <button onClick={() => props.onClick(props.id)}>Más información</button>
    </div>
  );
}

Movie.propTypes = {
  id: PropTypes.number.isRequired,
  name: PropTypes.string.isRequired,
  description: PropTypes.string.isRequired,
  people: PropTypes.number.isRequired,
  onClick: PropTypes.func.isRequired,
}
```

```jsx
/* /src/assets/js/components/MovieText.jsx  */

import React from 'react';
import PropTypes from 'prop-types';

export default function MovieText(props) {
  return (
    <div>
      <h2>{props.name}</h2>
      <p>{props.fullText}</p>
      <button onClick={props.onClick}>Volver</button>
    </div>
  );
}

MovieText.propTypes = {
  name: PropTypes.string.isRequired,
  fullText: PropTypes.string.isRequired,
  onClick: PropTypes.func.isRequired,
}
```

```jsx
/* /src/assets/js/containers/MostWatched.jsx  */

import React, { Component } from 'react';
import PropTypes from 'prop-types';

import MovieComponent from '../components/Movie';
import MovieTextComponent from '../components/MovieText';

export default class MostWatched extends Component {
  constructor(props) {
    super(props);
    this.state = {
      loading: true,
      displayText: false,
      currentMovieText = undefined,
      mostWatchesMovies: [],
    };

    this.showText = this.showText.bind(this);
    this.hideText = this.hideText.bind(this);
  }

  componentDidMount(){
    this.fetchMostWatchedMovies();
  }

  async fetchMostWatchedMovies() {
    this.setState({ loading: true });
    const mostWatchesMovies = await Promise.all(
      this.props.mostWatched.map(id => 
        fetch(`http://estecursoesbkn.cl/movies/${id}/summary`)
          .then(response => response.json()));
    );
    this.setState({ loading: false, mostWatchesMovies });
  }

  async fetchMovieText(id) {
    this.setState({ loading: true });
    const currentMovieText = await fetch(`http://estecursoesbkn.cl/movies/${id}/summary`)
                  .then(response => response.json()));
        
    );
    this.setState({ loading: false, currentMovieText });
  }

  async showText(movieId) {
    await this.fetchMovieText(movieId);
    this.setState({ displayText: true });
  }

  hideText() {
    this.setState({ displayText: false });
  }

  render() {
    let body = null;
    
    if (this.state.loading) {
      body = <p>Cargando...</p>;
    } else if (this.state.displayText) {
      const { name, fullText } = this.state.currentMovieText;
      body = <MovieTextComponent name={name} fulltext={fullText} onClick={this.hideText} />;
    } else {
      body = this.state.mostWatchesMovies.map(movie =>
        <MovieComponent {...movie} onClick={this.showText} />);
    }

    return (
      <div>
        <h1>Más Vistas</h2>
        {body}
      </div>
    );
  }
}

MostWatched.propTypes = {
  mostWatched: PropTypes.arrayOf(PropTypes.number).isRequired,
}
```



**Pauta:**
  * División de componente(s): 1 pt
  * Uso de patrón para componente(s): 1 pt
  * Código de componente(s): 4 pts
  * **Bonus:** (1 pt) Agregar estilo a el/los componente(s)