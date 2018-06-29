# Pauta Examen

## Pregunta 1 (25%): Presencia en Internet

HTML (3pts)

`index.hmtl`
```html
<body>
  <div id="container">
    <header>
	    <div id="app-bar">
        <p>Iniciar sesión</p>
      </div>
      <h1>SnacksEats</h1>
	    <p>La red de venta de snacks saludables</p>
    </header>

    <div id="benefits">
      <h2>Beneficios</h2>
      <p>Dentro de los beneficios que pueden encontrar en nuestros productos estan:</p>
      <div>
        <div class="benefit">
          <h3>Sanos</h3>
          <img class="benefit-photo" src="https://www.uab.edu/news/images/eating_healthy_heart.jpg" alt="food" /> 
          <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Aliquam et elementum mauris. Ornare efficitur mauris.</p>
        </div>
        
        <div class="benefit">
          <h3>Naturales</h3>
          <img class="benefit-photo" src="https://www.uab.edu/news/images/eating_healthy_heart.jpg" alt="food" /> 
          <p>Nullam vulputate eros a efficitur tincidunt. Vivamus turpis purus, sagittis nec tellus non, ornare efficitur mauris.</p>
        </div>

        <div class="benefit">
          <h3>Sin Azúcar</h3>
          <img class="benefit-photo" src="https://www.uab.edu/news/images/eating_healthy_heart.jpg" alt="food" /> 
          <p>Nullam vulputate eros a efficitur tincidunt. Vivamus turpis purus, sagittis nec tellus non, ornare efficitur mauris.</p>
        </div>
      </div>
    </div>

    <div id="contact">
      <h2>Contacto</h2>
      <div id="form-container">
        <form action="/contact.php" method="POST">
          <div class="field">
            <label>
              Nombre:
              <input type="text" name="name" />
            </label>
          </div>

          <div class="field">
            <label>
              Email:
              <input type="text" name="email" />
            </label>
          </div>

          <div class="field">
            <label>
              Mensaje:
              <textarea name="email"></textarea>
            </label>
          </div>

          <div class="field">
            <input type="submit" value="Enviar" />
          </div>
        </form>
      </div>
    </div>
  </div>
</body>
```

CSS

`app.css`
```css
body {
  background-color: #2C3E50;
  font-family: 'Open Sans', sans-serif;
}

#container {
  margin: 0 auto;
  background-color: white;
  max-width: 900px;
  min-width: 600px;
  padding: 20px;
}

#app-bar {
  background-color: black;
  color: white;
  text-align: right;
}

#benefits{
  text-align: center;
}

#benefits h2{
  background-color: #FAE5D3;
}

#benefits .benefit {
  border: 1px solid black;
  display: inline-block;
  padding: 10px; 
  width: 250px;
}

.benefit-photo {
  width: 200px;
}

.benefit p {
  text-align: justify;
}

#contact {
  text-align: center;
}

#contact h2{
  background-color: #F4ECF7;
}

#form-container {
  background-color: wheat;
  padding: 20px;
}

#form-container .field {
  margin-bottom: 15px;
}
```

**HTML**: Debe esar bien formado, se debe evaluar estructura    
**CSS**: Debe estar bien formado, podría haber propiedades con nombres no exactos, pero debe entenderse o estar explicados correctamente. El sitio podría, o no, tener un contenedor con un tamaño limitado.

## Pregunta 2 (20%): Pedidos Online

### Pregunta 1 (1 pt)

Lo que se necesita es sólo un modelo de pedidos (`order`), que tenga todos los campos antes mencionados (N° de cliente, cantidad de *snacks* y cantidad de días para realizar el pedido). Además agregaremos otro atributo llamado `cancelled`, el cual por defecto es `false`, y será requerido en la ruta de anular.
Debemos agregar otro que es el `id` del pedido, para identificarlo.

### Pregunta 2 (1 pt)

|Metodo|URL            |Descripción|
| -----|:-------------:| --------- |
|POST  |/orders/       | Crear nueva orden |
|PATCH |/orders/:id    | Poder anular una orden |

### Pregunta 3 (4 pts)

Crear un pedido (2 pts)

```javascript
router.post('orders.create', '/orders/', async (ctx) => {
  const order = await ctx.orm.order.build(ctx.request.body);
  ctx.body = await order.save({ fields: ['customerNumber', 'quantity', 'arriveBeforeDays'] });
});
```

Cancelar un pedido  (2 pts)

```javascript
router.patch('orders.update', '/orders/:id', async (ctx) => {
  const order = await ctx.orm.order.findById(ctx.params.id);
  const { cancelled } = ctx.request.body;
  await order.update({ cancelled });
  ctx.status = 200;
});
```


## Pregunta 3 (35%): Contáctame (en React)

```jsx
/* /src/assets/js/components/ContactForm.jsx */

import React from 'react';
import PropTypes from 'prop-types';

export default function ContactForm(props) {
  return (
    <div>
        <h2>Contact Us</h2>
        <p>{props.formMessage}</p>
        <form onSubmit={props.handleSubmit}>
          <div>
            <label>
              Name:
              <input 
                type="text"
                name="name"
                value={props.nameInputValue}
                onChange={props.handleInputChange}
              />
            </label>
          </div>

          <div>
            <label>
              Email:
              <input
                type="text"
                name="email"
                value={props.emailInputValue}
                onChange={props.handleInputChange}
              />
            </label>
          </div>

          <div>
            <label>
              Message:
              <textarea
                name="message"
                value={props.messageInputValue}
                onChange={props.handleInputChange} />
          </div>

          <input type="submit" name="Send" />
        </form>
    </div>
  );
}

ContactForm.propTypes = {
  nameInputValue: PropTypes.string.isRequired,
  emailInputValue: PropTypes.string.isRequired,
  messageInputValue: PropTypes.string.isRequired,
  formMessage: PropTypes.string.isRequired,
  handleSubmit: PropTypes.func.isRequired,
  handleInputChange: PropTypes.func.isRequired,
};
```

```jsx
/* /src/assets/js/containers/ContactForm.jsx */

import React, { Component } from 'react';
import PropTypes from 'prop-types';
import { validateEmail } from 'iic2513-validators';
import ContactFormComponent from '../components/ContactForm';

export default class ContactForm extends Component {
  constructor(props) {
    super(props);
    this.state = {
      name: '',
      email: '',
      message: '',
      formMessage: '',
    };

    this.handleSubmit = this.handleSubmit.bind(this);
    this.handleInputChange = this.handleInputChange.bind(this);
  }

  handleInputChange(event) {
    const { name, value } = event.target;
    this.setState({ [name]: value });
  }

  isFormCorrect() {
    if (!this.state.name || !this.state.email || !this.state.message) {
      this.setState({ formMessage: 'Complete all fields' });
      return false;
    } else if (!validateEmail(this.state.email)) {
      this.setState({ formMessage: 'Email must be valid' });
      return false;
    } else {
      return true;
    }
  }

  handleSubmit(event) {
    event.preventDefault();

    if (!this.isFormCorrect()) {
      return;
    }

    const { name, email, message } = this.state;
    const data = {
      name,
      email,
      message, 
    };

    return fetch('/contact.php', {
      body: JSON.stringify(data),
      headers: {
        'content-type': 'application/json'
      },
      method: 'POST',
    })
      .then(() => this.setState({ formMessage: 'Your message has been sent successfully'}))
      .catch((err) => this.setState({ formMessage: 'Ops! Something went wrong!'}));
  }

  render() {
    return(
      <ContactFormComponent
        nameInputValue={this.state.name}
        emailInputValue={this.state.email}
        messageInputValue={this.state.message}
        formMessage={this.state.formMessage}
        handleSubmit={this.handleSubmit}
        handleInputChange={this.handleInputChange}
      />
    );
  }
}
```

Pauta:
* 1 pt por dividir componentes *dumb* y *smart*
* 1 pt por validación (Puede ser una validación de todo o parcial)
* 0.5 pt por enviar el formulario (Evaluar que el formulario no puede ser enviado si contiene errores)
* 0.5 pt cor actualizar estado correctamente al cambiar un campo (si no usa `this.setState`= 0 pts)
* 1 pt por *dumb* component (o render en un componente) - Mostar los campos y error
* 2 pts por *smart* component - Manejo de estado, estructura en general y hacer render del *dumb* component


## Pregunta 4 (20%): Preguntas generales

1. (1 pt) Se puede incorporar Websockets en cualquier actividad de tiempo real, por ejemplo, en una lista que contenga los pedidos que falta por procesar y que, cuando se vayan completando, se pueden sacar de la lista sin refrescar el sitio web.

2. (1 pt) Redux nos permite tener un estado general de la aplicación. Por ejemplo, se podría agregar los datos de usuario que ingresó al sistema, ya que son datos que podrían querer ser conocidos por toda la aplicación.

3. (1 pt) En esta pregunta debe mencionar al menos: un dominio, un DNS y un servidor con la aplicación. Así se podría ingresar a algo como api.dominio.tld.

4. (1 pt) Por ejemplo un microservicio podría ser el de los pedidos, otro de los usuarios y otro de los pagos. Lo importante es que se indiquen que deben ser servicios independientes y que se relacionan entre sí debido a una API u otro microservicio. El diagrama es el típico de microservicios y puede ser visto [aquí](http://microservices.io/patterns/microservices.html).

5. (0.5 pts) Según lo explicado por Johanna, los Pull Request aportaban calidad al código y además era una forma de aprender nuevas formas de hacer ciertos algoritmos.

6. (0.5 pts) Que un lider técnico no tenga conocimientos suficientes, en el caso de Johanna, implicó que muchas prácticas llevaran al caos. (push directos a master, pérdida de código, etc.).

7. (0.5 pts) Dos aspectos son el manejo del tiempo y la responsabilidad. Se puede colocar otro que vaya en esa línea.

8. (0.5 pts) Debido a que el equipo no está en un mismo lugar, al usar un sistema de mensajería la comunicación no verbal se pierde en las conversaciones. Por este motivo, se puede malinterpretar ciertos mensajes. Las llamadas o las video conferencias son una muy buena manera de poder rescatar esta parte de la comunicación.