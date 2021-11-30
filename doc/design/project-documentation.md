# Tips para la documentación del proyecto

## SLIDES

- 11-12 diapositivas aprox
- Presentar objetivos
- Presentar aplicación
- TBD ¿Qué ha supuesto?
- Qué he cambiado
- Qué es necesario hacer
- Basarme en las conclusiones de la memoria, reutilizar capturas de commits github-despliegues heroku. Sacar un par de slides de las conclusiones
- Qué medidas he tomado
- Conclusiones:
  - ¿Difícil?
  - ¿Hay que tener cuidado?
  - CI/CD
  - Me ha ayudado
- Resumen de todo el trabajo
- TBD (reto)
- Proyecto como excusa para aplicar feature toggle
- Versión en producción actualizada en cada commit

### Demo

- Publicar un pending tweet bajo demanda, indicando que ha sido una de las features que he implementado
- Mostrar repositorio GitHub con los Pipelines de GitHub actions, commits verde verde, Heroku, actualización de la app
- Quizá menos slides y mas tiempo para darme una vuelta live para ejecutarlo

## MEMORIA

### Resumen

- Contar todo lo que he hecho, desde implementar una aplicación usando TBD con una serie de features, describir que se ha hecho utilizando la técnica de feature toggles y teniendo siempre una versión en producción que se iba actualizando después de cada commit, por tanto se ha seguido fielmente el modelo TBD.
- Extensión: media página o tres cuartos mejor que una página.
- Tiene que ser conciso porque después vienen los detalles.

### Objetivos

- ¿Qué quiero hacer? Desarrollar una aplicación de principio a fin utilizando la técnica de Trunk Based Development, apoyándome en los contenidos vistos en el Master CloudApps (feature toggles), manteniendo la aplicación en producción funcionando en Heroku en todo momento. 
- 4 o 5 puntos en una lista

### Introducción

- Se entra en los objetivos
- Introducción de los términos y explicación a nivel general, se habla del problema que se va a abordar:
   - TBD
   - Feature toggle
   - Branch by abstraction (usado?)
   - Introducir la app de TBD (aplicacion de la publicación de tweets y de las 2 features implementadas) en un párrafo sin entrar en detalles.

### Desarrollo del TFM

- PREPARACIÓN DEL DESARROLLO
  - Hablar de la infraestructura 
  - Repositorio con una serie de scripts de CI/CD
  - Aplicación desplegada en Heroku
  - Base de datos en Heroku
  - Indicar que se ha procedido a montar toda la infraestructura antes de comenzar con el desarrollo
  - Proyecto por defecto generado con Spring Initializr
- IMPLEMENTACIÓN DEL PROYECTO
  - Preparación de la aplicación
  - DDD
  - Diagrama de clases, adaptares y puertos, Spring
  - Arquitectura Hexagonal
- FEATURE TOGGLES
  - Para poder poner los features toggles, es importante tener un buen diseño arquitectónico ya que si el código no está bien organizado. TBD ayuda a poder desarrollar con feature toggles al tener un diseño limpio y estructurado.
  - Explicar por qué no me ha hecho falta usar Branch by abstraction
  - Capturas de pantalla de los commmits de github y despliegues en Heroku (al menos para una de ellas), suponen actualización de la aplicación en producción.

### Conclusiones

- Unas dos páginas y media
- Discutir qué me ha supuesto aplicar TBD
- ¿Más dificil de abordar?
- ¿Dudas a la hora de partir una feature para que realmente pueda mantenerse en todo momento la version funcionando en producción?
- ¿Ha sido fácil saber donde colocar los toogle para evitar que se ejecute esa funcionalidad que está en desarrollo y que no afecte a otras que tienen que estar funcionando? Hablar del repo de pruebas
- ¿Hasta qué punto me han ayudado los tests a no liarla?
- ¿He cambiado la forma de actuar por usar TBD a cómo lo habría hecho?
- ¿Retos?
- ¿Cómo he dividido las features?
- Si hay mucho que discutir en esta sección, incluir una sección anterior llamada **Discusión**, donde se mete lo que he aprendido de TBD y en las conclusiones, mostrar los temas mas relevantes. Comenzar poniendo sólo Conclusiones y si se ve que se va a dos páginas y media, sacar la sección de Discusión y dejar las Conclusiones en media página aprox.

### Trabajos futuros

- CQRS
- Almacenamiento de datos en la nube como AWS S3 o Google Cloud Storage

### Bibliografía

- No solamente páginas web
- Libros TBD, DDD, libro de spring, FlyWay, Github actions?
- Cuando menciono DDD, hacer referencia a la bibliografía

## DOCUMENTACIÓN TÉCNICA