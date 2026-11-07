# Modelo Relacional de Bases de Datos 12



## Descripción



Este documento detalla el esquema y la estructura del modelo relacional de bases de datos para una red social, enfocado en el control de usuarios, relaciones de seguimiento, publicaciones, etiquetas, reacciones, comentarios y respuestas a comentarios.

---

## Estructura de Tablas y Atributos



### 1. Usuario



* **PK (Clave Primaria):** `id_username`


* **Atributos:**
* `fecha_alta`


* `correo_electronico`


* `biografia`


* `contraseña`





### 2. Seguimiento



* **PK (Clave Primaria Compuesta):** `id_seguidor`, `id_seguido`


* **Atributos:**
* `fecha_seguimiento`


* `estado_seguimiento`


* `notificaciones`




* **FK (Claves Foráneas):**
* `id_seguidor` (asociado a la tabla Usuario)


* `id_seguido` (asociado a la tabla Usuario)





### 3. Publicacion



* **PK (Clave Primaria):** `id_publicacion`


* **Atributos:**
* `url_imagen`


* `descripción`


* `fecha_publicación`




* **FK (Claves Foráneas):**
* `id_username` (asociado a la tabla Usuario)





### 4. Etiqueta



* **PK (Clave Primaria):** `id_etiqueta`


* **Atributos:**
* `categoria`


* `fecha_creacion`


* `nombre`


* `descripcion`





### 5. Publicacion-Etiqueta



* **FK (Claves Foráneas):**
* `id_publicación` (asociado a la tabla Publicacion)


* `id_etiqueta` (asociado a la tabla Etiqueta)





### 6. Reacción



* **FK (Claves Foráneas):**
* `id_username` (asociado a la tabla Usuario)


* `id_publicación` (asociado a la tabla Publicacion)




* **Atributos:**
* `tipo_de_reacción`





### 7. Comentario



* **PK (Clave Primaria):** `id_comentario`


* **Atributos:**
* `texto`


* `fecha_hora`




* **FK (Claves Foráneas):**
* `id_username` (asociado a la tabla Usuario)


* `id_publicación` (asociado a la tabla Publicacion)





### 8. Responde_comentarios



* **FK (Claves Foráneas):**
* `id_comentario` (asociado a la tabla Comentario)


* `id_username` (asociado a la tabla Usuario)


* `id_publicación` (asociado a la tabla Publicacion)





---

## Relaciones Principales



* **Usuario y Usuario (Seguimiento):** Permite gestionar la relación reflexiva de muchos a muchos entre seguidores y seguidos mediante la tabla intermedia `Seguimiento` (`id_seguidor` e `id_seguido`).


* **Usuario y Publicacion:** Un usuario puede crear múltiples publicaciones identificadas por su `id_username`.


* **Publicacion y Etiqueta (Publicacion-Etiqueta):** La relación de muchos a muchos entre publicaciones y etiquetas se administra a través de la tabla intermedia `Publicacion-Etiqueta`.


* **Usuario y Publicacion (Reacción):** Las reacciones de los usuarios a las publicaciones se registran vinculando `id_username` e `id_publicación`.


* **Publicacion y Comentario:** Las publicaciones reciben comentarios realizados por usuarios, los cuales se asocian mediante la tabla `Comentario`.


* **Comentario (Responde_comentarios):** Permite estructurar hilos o respuestas asociadas a los comentarios de las publicaciones mediante `id_comentario`.
