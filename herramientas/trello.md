# Trello
## 1. Introducción
Trello será nuestro medio oficial para la metodología Scrumban o [Kanban](https://es.atlassian.com/agile/kanban)

## 2. Funcionamiento
Un board de Trello existirá por desarrollo, sin discriminar entre distintas componentes del sistema.
Cada tarjeta tendrá la capacidad de unir servicios como GDrive, Github y campos personalizados.

Todo el contenido de las tarjetas es en inglés.

## 3 Campos

### 3.1 Estimate
Tamaño estimado de una tarea. Unidad de medida dependerá del proyecto.

## Labels

Dependerán del proyecto.

## 6. Columnas
Trabajaremos con 7 columnas, las cuales en todo momento deben estar ordenadas por prioridad.:

* To Do: contiene todas las tareas a realizar en la iteración actual.

* Next: contiene las tareas aprobadas para comenzar a realizarse. Tiene un límite de 2 tarjetas a la vez.

* Development: Son las tareas que están en desarrollo.  Solo pueden pasar tarjetas que vengan desde la columna Next.

* Testing: Tareas que estén en processo de Testing, ya  sean unitarios o de integración. Por defecto los proyectos de educalabs requieren que todas las funcionalidades esten testeadas antes de ser pasadas a producción.

* Documentation: Tareas Que se encuentran en proceso de documentación. Al igual que con los tests todo el código de educalabs debe estar apropiadamente documentado. Entre las 3 últimas columnas pueden haber a lo más 1.5n (redondeado hacia arriba) tarjetas donde n es el número de desarrolladores en el proyecto.

* Approval: Las tareas que estan esperando el proceso de QA y aprobación del equipo se encuentran en esta columna.

* Done: Las tareas completas y aprobadas del sprint llegan a esta columna.