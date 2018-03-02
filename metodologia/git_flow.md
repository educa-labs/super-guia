## Git Flow

Git flow es una convención mara el manejo de las branches en un repositorio de git. En educalabs tenemos nuestra propia convención basada en la original, la cual se conforma por las siguientes branches. En educalabs trabajamos con un sólo repositorio por proyecto.

### master

Esta es la rama principal del proyecto. Contiene el código que se encuentra actualmente en producción, está profundamente revisado y ~~prácticamente~~ libre de bugs. Cada merge a master implica un release del producto.

### staging

Esta es la rama cuyo código se encuentra deployado en nuestro servidor de prueba, en esta rama se evalúa el código y la integración antes de pasar a master. Las pruebas de QA se realizan en esta rama.

### development

Esta es la rama a partir de la cual se desarrolla. El código en development siempre debe poder montarse en local de tal manera que la aplicación en desarrollo pueda ser probada de forma integra en cualquier máquina. Cada vez que se quiera implementar una feature extraemos una rama a partir de development.

### feature

Las ramas de feature son aquellas en las que se programan las features. Una vez terminada y testeada una feature se hace el merge a development (ej: `f/login`).