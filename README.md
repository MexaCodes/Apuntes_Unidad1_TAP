# Interfaz gráfica de usuario

La **Interfaz Gráfica de Usuario** (GUI) representa la evolución de la interacción humano-computadora, sustituyendo las interfaces de texto (CLI) por un entorno visual intuitivo. Técnicamente, es una capa de abstracción que gestiona la comunicación entre el usuario y los recursos de hardware mediante elementos gráficos.

### Arquitectura y Procesamiento de Bajo Nivel
Una GUI no es una imagen estática, sino un sistema dinámico basado en un **Motor de Renderizado**. En el caso de Flet, se utiliza el motor de Flutter, el cual dibuja la interfaz directamente en la GPU (Unidad de Procesamiento Gráfico).

* **Bucle de Eventos (Event Loop):** Es el corazón de la GUI. El programa entra en un estado de espera infinita hasta que el usuario realiza una acción. En tu código de la **Calculadora Estática**, cuando se presiona un botón, se genera un evento que activa la función `presionar_boton(e)`, actualizando el estado visual sin cerrar el programa.
* **Gestión de Capas:** La GUI organiza los elementos en un árbol de componentes (Widget Tree). Cada cambio en un componente (como el display rojo de la calculadora) requiere que el motor calcule nuevamente la posición y el color de los píxeles afectados.



### Psicología y Usabilidad en la GUI
La GUI debe seguir principios de diseño para ser efectiva:
1.  **Visibilidad del estado:** El usuario siempre sabe qué número marcó en la calculadora porque el display se actualiza.
2.  **Consistencia:** El uso de un estilo único (`estilo_cuadrado`) para todos los botones numéricos permite que el usuario aprenda una sola vez cómo interactuar con ellos.



---

# 1.1 Creación de interfaz gráfica para usuarios

La **Creación de interfaz gráfica para usuarios** es el proceso de ingeniería que transforma los requerimientos de una aplicación en una experiencia interactiva funcional y segura. Este proceso combina la disposición espacial, la gestión de estados asíncronos y la integridad de los datos.

### Pilares Técnicos de la Creación de Interfaces

#### A. Estructuración Espacial (Layouts)
La creación comienza con la disposición jerárquica de los controles. Basándonos en el código de **Registro de Estudiantes**, la creación utiliza un modelo de "Cajas Flexibles":
* **Columnas (`ft.Column`):** Alineación vertical para formularios (Nombre, Control, Email).
* **Filas (`ft.Row`):** Alineación horizontal para optimizar espacio, como el caso de "Carrera" y "Semestre".
* **Alineación Interna:** El uso de `horizontal_alignment` y `vertical_alignment` asegura que la interfaz sea estéticamente equilibrada.



#### B. Programación Orientada a Objetos (POO) en la UI
Para crear interfaces escalables, como el **Sistema de Chat**, se emplea la creación basada en componentes personalizados.
* **Clases Reutilizables:** Al crear la clase `ChatMessage`, se encapsula la lógica del avatar y el texto. Esto permite que la creación sea modular: si necesitas cambiar el diseño de los mensajes, solo modificas la clase y se actualiza en toda la aplicación.
* **Modularidad:** La interfaz deja de ser un script plano y se convierte en un conjunto de objetos inteligentes que interactúan entre sí.



#### C. Lógica de Validación e Integridad (Data Handling)
Un aspecto crítico en la creación es la seguridad de la información. En el código de **Registro**, la creación incluye:
* **Validaciones Críticas:** Se implementan filtros que impiden que el usuario envíe formularios vacíos.
* **Uso de Regex:** Las expresiones regulares validan que el correo electrónico tenga una estructura real (`usuario@dominio.com`).
* **Controles de Selección:** En lugar de permitir escritura libre, la creación de `ft.Dropdown` y `ft.RadioGroup` limita al usuario a opciones válidas, eliminando errores de captura desde la fuente.



#### D. Sincronización de Estado y Comunicación Asíncrona (PubSub)
La creación de interfaces dinámicas, como el Chat, requiere que la GUI sea capaz de recibir datos de otros usuarios sin refrescar la página.
* **Suscripción:** La interfaz "escucha" cambios globales mediante `page.pubsub.subscribe`.
* **Actualización Reactiva:** El uso de `page.update()` es el comando que finaliza el ciclo de creación, permitiendo que nuevos mensajes aparezcan instantáneamente en la pantalla del receptor, manteniendo la fluidez de la comunicación.
