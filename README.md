# Api Gateway httplog plugin

Plugin de métricas y datos sobre el uso de las API registradas en api-gateway.

También podés [ver el repositorio de api-gateway](https://github.com/datosgobar/api-gateway).

## Instalación

- Instalar `jsonlua`
- Clonar el repositorio
- Instalar con luarocks

```
[sudo] luarocks install json-lua
git clone git@github.com:datosgobar/api-gateway-httplog.git
cd api-gateway-httplog/
[sudo] luarocks make
```

## Uso

El plugin debe ser activado _por API_. El mismo require los siquirentes campos:

| Campo             | Requerido | Descripción                                 |
|-------------------|-----------|---------------------------------------------|
|name               | sí        | Nombre del plugin                           |
|token              | sí        | Token de acceso al "endpoint"               |
|endpoint           | sí        | "URL" a la cual registrar los datos         |
|api_data           | No        | Parámetro para relacionar datos con una API |
|token_header_name  | sí        | Nombre del header donde se envia el token de cliente |


Ejemplo:

```
curl -X POST http://localhost:8001/apis/mi-api-name/plugins \
    -d "name=api-gateway-httplog" \
    -d "token=mi-token-secreto" \
    -d "endpoint=http://midominio.com/endpoints/queries/"
```

El plugin debe estar entre los `custom_plugins` en el archivo `/etc/kong/kong.conf`. 

## Contacto

Te invitamos a [crearnos un issue](https://github.com/datosgobar/api-gateway/issues/new?title=Encontre%20un%20bug%20en%20api-gateway-httplog) en caso de que encuentres algún bug o tengas feedback de alguna parte de `api-gateway-httplog`.

Para todo lo demás, podés mandarnos tu comentario o consulta a [datos@modernizacion.gob.ar](mailto:datos@modernizacion.gob.ar).
