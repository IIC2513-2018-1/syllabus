# Pauta I2

## Parte 1 (20%) - Preguntas Teóricas

1. Esto es posible por las cookies. Las cuales se usan para que el servidor deje información en el cliente, quien después está obligado a enviarla al servidor dando la ilusión de tener estado.

**Pauta:** 1 pt por explicación.

2. La carga no se vería afectada, sin embargo, en la descarga tendría que enviarle un link al cliente que pase por nuestro servidor y ahí enviarle el archivo al usuario.

**Pauta:** 1 pt por explicación.

3. Principalmente porque un usuario podría modificar su cookie maliciosamente y colocar el id de otro usuario. Lo que generalente se hace es un token de sesión para cada usuario.

**Pauta:** 1 pt por explicación.

4. Porque el prototipo es entregado a cada uno de los objetos creados para la clase, por lo que siempre será el mismo.

**Pauta:** 1 pt por explicación.

5. Las clases creadas mediante `class` se traducen en funciones constructoras. La definición con `class` solo es *sintax sugar*.

**Pauta:** 1 pt por explicación.

6. En general, lo que se hace es una función que reciba el contexto (`ctx`) y información adicional. Dentro de esta función se pueden realizar operaciones pero finalmente se llama a la función `ctx.sendMail()` con el nombre del template a enviar, un objeto con los datos de a quién se envía, asunto, etc. Finalmente se agregan las variables necesarias para el template.

**Pauta:** 1 pt por explicación.


## Parte 2 (80%) - Preguntas Prácticas

**Pauta General:** Considerar que no se espera que los alumnos tengan sintaxis perfecta en esta parte. La pauta, para cada pregunta, indica el máximo a obtener por distintos hitos cumplidos (y solicitados en el enunciado). Los descuentos deben hacerse sobre esos puntajes, para cada uno de los hitos.

Finalmente, existen varias formas de lograr el objetivo. Se debe considerar que existen soluciones adicionales a las planteadas.

### Parte A (20%): Hoisting

```
Iniciando el programa
undefined
cuak!
cuak!
-- NOT DEFINED --
Testing... 7
Testing... 5
bark!
bark!
bark!
2
```
**Pauta:**
  * 6 pts por el correcto output
  * En caso de omisión de una salida se descuenta puntaje proporcional
  * En caso de agregar salidas que no corresponden, se descuenta una correcta por cada adicional

### Parte B (40%): Funciones Síncronas y Asíncronas

```javascript
router.post('orders.new', '/', async (ctx) => {
  try {
    const newOrder = ctx.orm.order.build(ctx.request.body.orderInfo);
    await newOrder.save();
    
    const productPromises = [];
    ctx.request.body.productsIds.each((productId) => {
      productPromises.push(
        ctx.orm.product.findById(productId)
          .then(product => newOrder.addProduct(product));
      );
    });

    await Promise.all(productPromises);
    ctx.messages.info = 'La orden se ha agregado con éxito';
    sendOrderAlertEmail(ctx, newOrder);
    ctx.redirect(ctx.router.url('orders.list'));
  } catch (error) {
    ctx.messages.error = 'Error';
    ctx.redirect(ctx.router.url('orders.list'));
  }
});
```
**Pauta:**
  * 4 pts por implementación
    * 1 pt por crear la orden
    * 3 pt por asociar los productos a la orden
  * 1 pt caso de éxito
  * 1 pt caso de error

### Parte C (40%): Javascript del lado del cliente

Cambios en `HTML`

```html
    <p>El sitio de películas para el curso de web</p>
  </header>

  <div>
    <select id="theme-selector">
      <option value="ubuntu">Ubuntu</option>
      <option value="rails">Rails</option>
      <option value="node">Node</option>
    </select>
  </div>

  <div id="most-viewed" class="most-viewed">
    [...]
  </div>
  <div id="testimony" class="testimony">
```

Cambios en `CSS`

```css
/* Archivo original */
#most-viewed .movie {
  display: inline-block;
  padding: 10px; 
  width: 250px;
}

.most-viewed .movie {
  border: 1px solid black;
}

#most-viewed h2{
}

.most-viewed h2{
  background-color: #FAE5D3;
}

#testimony h2{
}

.testimony h2{
  background-color: #F4ECF7;
}

/* Archivo ubuntu.css */

.ubuntu-most-viewed h2{
  background-color: #E95420;
  color: white;
}

.ubuntu-testimony h2{
  background-color: #E95420;
  color: white;
}

.ubuntu-most-viewed .movie {
  background-color: #f7f7f7;
  color: #667;
  border: 1px solid #cdcdcd;
}


/* Archivo rails.css */

.rails-most-viewed h2{
  background-color: #c52f24;
  color: white;
}

.rails-testimony h2{
  background-color: #fff9d8;
  color: black;
}

.rails-most-viewed .movie {
  background-color: #d5e9f6;
  color: black;
}

/* Archivo node.css */

.node-most-viewed h2{
  background-color: #eaf5e9;
  color: #026e00;
}

.node-testimony h2{
  background-color: #eaf5e9;
  color: #026e00;
}

.node-most-viewed .movie {
  background-color: #43853d;
  color: white;
}

```

Archivo `JS`

```javascript
$(function() {
  $('#theme-selector').change(function() {
    $('#most-viewed').removeClass().addClass(this.value + '-most-viewed');
    $('#testimony').removeClass().addClass(this.value + '-testimony');
  });
});
```

**Pauta:**
  * 1.5 pts HTML
  * 2 pts CSS
  * 2.5 pts JS