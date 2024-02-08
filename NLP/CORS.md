## CORS

Nest hace uso de las dependencias del CORS de Express o Fastify. Estas dependencias permiten varias opciones para customizar dependiendo de los requerimientos.


## Formas de inicializar CORS

La primer forma de inicializar es mediante la función `enableCors()`.

La función toma como argumento la configuración de un objeto. Las propiedades de este objeto se describen en:


```javascript
const app = await NestFactory.create(AppModule);
app.enableCors();
await app.listen(3000);
```

Existe otra forma de inicializar el CORS. Esta es pasando el CORS como objeto en el método `NestFactory.create()`

```javascript
const app = await NestFactory.create(AppModule, { cors: true });
await app.listen(3000);

```


### Opciones extra
Existe otras opciones que se pueden configurar para el CORS.

Una es configurar los dominios por los cuales se accederan a al API.

```javascript
app.enableCors(
    { 
      origin: ['https://betterjavacode.com', 'https://www.google.com'],
    }
  );
```

De otra manera podemos definir los a usar en la API

```javascript
app.enableCors(
    { 
      origin: ['https://betterjavacode.com', 'https://www.google.com'],
      methods: ['POST', 'PUT', 'DELETE', 'GET']
    }
  );
```

Los parametros restantes son lo siguientes:

- origin:
  - Booleano: True, refleja el origen de la solicitud según lo definido por req.header('Origin'). False, CORS está deshabilitado.
  - Cadena: Se establece en un origen específico. Solo se permiten solicitudes del dominio de origen.
  - Expresión regular: Se establece en un patrón de expresión regular para    probar el origen de la solicitud.
  - Arreglo: Se establece en un arreglo de orígenes válidos, donde cada origen puede ser una cadena o una expresión regular.
  - Función: Se establece en una función personalizada que toma el origen de la solicitud como primer parámetro y un callback como segundo. El callback se llama como callback(err, origin).

- methods:
  - Configura el encabezado con los métodos a permitir para la API.['GET', 'PUT', 'POST', 'DELETE'].
  
- allowedHeaders:
  - Configura el encabezado  Access-Control-Allow-Headers CORS. Espera una cadena delimitada por comas o un arreglo. Si no se especifica, se reflejan los encabezados especificados en el encabezado Access-Control-Request-Headers de la solicitud.

- exposedHeaders:

  - Configura el encabezado CORS Access-Control-Expose-Headers. Espera una cadena delimitada por comas o un arreglo. Si no se especifica, no se exponen encabezados personalizados.
- credentials:

  - Configura el encabezado CORS Access-Control-Allow-Credentials. Se establece en true para incluir el encabezado; de lo contrario, se omite.
- maxAge:

  - Configura el encabezado CORS Access-Control-Max-Age. Se establece en un entero para incluir el encabezado; de lo contrario, se omite.
- preflightContinue:

  - Pasa la respuesta CORS al siguiente controlador.

- optionsSuccessStatus:

  - Proporciona un código de estado a utilizar para solicitudes OPTIONS exitosas. Se recomienda usar para navegadores viejos.

## Link

[https://betterjavacode.com/programming/how-to-use-cors-in-nestjs-application]

[https://docs.nestjs.com/security/cors]

[https://copyprogramming.com/howto/javascript-enable-cors-on-nestjs-to-specific-url]

[https://betterjavacode.com/programming/how-to-use-cors-in-nestjs-application]

[https://betterjavacode.com/programming/how-to-use-cors-in-nestjs-application]

[https://github.com/nestjs/nest/blob/master/packages/common/interfaces/external/cors-options.interface.ts]

[https://bipinparajuli.com.np/blog/how-to-use-cors-with-nestjs]

[https://bipinparajuli.com.np/blog/how-to-use-cors-with-nestjs]