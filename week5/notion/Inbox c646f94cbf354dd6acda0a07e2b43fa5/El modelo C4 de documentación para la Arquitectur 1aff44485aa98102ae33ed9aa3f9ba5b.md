# El modelo C4 de documentación para la Arquitectura de Software | by Javier Vivanco | Medium

[https://medium.com/@javiervivanco/el-modelo-c4-de-documentaci%C3%B3n-para-la-arquitectura-de-software-424704528390](https://medium.com/@javiervivanco/el-modelo-c4-de-documentaci%C3%B3n-para-la-arquitectura-de-software-424704528390)

# El modelo C4 de documentación para la Arquitectura de Software

![](https://miro.medium.com/v2/resize:fill:88:88/0*a_DrxmG9y8UhzhlL.jpg)

[Javier Vivanco](https://medium.com/@javiervivanco?source=post_page---byline--424704528390---------------------------------------)

·

[Follow](https://medium.com/m/signin?actionUrl=https%3A%2F%2Fmedium.com%2F_%2Fsubscribe%2Fuser%2Fd9aa7f1544db&operation=register&redirect=https%3A%2F%2Fmedium.com%2F%40javiervivanco%2Fel-modelo-c4-de-documentaci%C3%B3n-para-la-arquitectura-de-software-424704528390&user=Javier+Vivanco&userId=d9aa7f1544db&source=post_page-d9aa7f1544db--byline--424704528390---------------------post_header------------------)

7 min read

·

Jun 5, 2019

> Traducido desde https://www.infoq.com/br/articles/C4-architecture-model/
> 
> 
> Sobre el autor
> 
> Simon Brown es un consultor independiente especializado en arquitectura de software y autor del libro “Software Architecture for Developers” (una guía amigable para desarrolladores de arquitectura de software, liderazgo técnico y equilibrio con agilidad). También es el creador del modelo de arquitectura de software C4, que es un enfoque simple para crear mapas de su código. Simon es un orador habitual en conferencias internacionales de desarrollo de software y viaja por el mundo para ayudar a las organizaciones a visualizar y documentar su arquitectura de software.
> 

**Puntos principales**

- La creación de diagramas de software se redujo como resultado del cambio en el uso de metodologías ágiles. Cuando se crean diagramas, a menudo son confusos y poco claros.
- El modelo C4 consiste en un conjunto jerárquico de diagramas de arquitectura de software para contexto, contenedores, componentes y código.
- La jerarquía de los diagramas C4 proporciona diferentes niveles de abstracción, cada uno de los cuales es relevante para una audiencia diferente.
- Evite la ambigüedad en sus diagramas incluyendo una cantidad suficiente de texto, así como una clave o leyenda para la notación utilizada

Los diagramas de arquitectura de software son una manera fantástica de comunicar cómo planea construir un sistema de software (diseño inicial) o cómo funciona un sistema de software existente (documentación retrospectiva, intercambio de conocimientos y aprendizaje).

Sin embargo, es muy probable que la mayoría de los diagramas de arquitectura de software que ha visto sean un lío confuso de cajas y líneas. Un desafortunado e involuntario efecto secundario del Manifiesto para el Desarrollo Ágil de Software es que muchos equipos han detenido o reducido sus esfuerzos de diagramación y documentación, incluyendo el uso de UML.

Ahora, estos mismos equipos tienden a confiar en diagramas ad hoc que dibujan en una pizarra o ensamblan utilizando herramientas de diagramación de propósito general, como Microsoft Visio. Ionut Balosin escribió el año pasado “The Art of Making Architectural Diagrams” (El arte de hacer diagramas arquitectónicos), que describe una serie de problemas comunes al hacerlo, relacionados con notaciones semánticas incomprensibles y poco claras.

Los diagramas ambiguos de arquitectura de software conducen a malentendidos, lo que puede ralentizar a un buen equipo. En nuestra industria, deberíamos esforzarnos por crear mejores diagramas de arquitectura de software. Después de años de crear software y trabajar con equipos de todo el mundo, he creado algo que llamo el “modelo C4”. C4 significa contexto, contenedores, componentes y código — un conjunto de diagramas jerárquicos que puede utilizar para describir la arquitectura de su software en diferentes niveles de zoom, cada uno útil para diferentes audiencias. Piensa en ello como Google Maps para tu código.

![](https://miro.medium.com/v2/resize:fit:700/1*zXKybal6qBCXOeKTArVbjg.jpeg)

Para crear estos mapas de su código, primero necesita un conjunto común de abstracciones para crear un lenguaje ubicuo que describa la estructura estática de un sistema de software. El modelo C4 considera las estructuras estáticas de un sistema de software en términos de contenedores (aplicaciones, almacenes de datos, microservicios, etc.), componentes y código. También considera a las personas que utilizan los sistemas de software que construimos.

![](https://miro.medium.com/v2/resize:fit:700/1*UoG-NUUBt_ympPD2Ix1iyA.jpeg)

# Nivel 1: El diagrama de contexto del sistema

El Nivel 1, un diagrama de contexto del sistema, muestra el sistema de software que está construyendo y cómo encaja en el mundo en términos de las personas que lo utilizan y los otros sistemas de software con los que interactúa. Aquí hay un ejemplo de un diagrama de contexto que describe un sistema de banca por Internet que usted puede estar construyendo:

![](https://miro.medium.com/v2/resize:fit:700/1*dbwsK7MqngVsTe55plkXpA.jpeg)

Sus clientes bancarios utilizan el sistema de banca por Internet para visualizar información sobre sus cuentas bancarias y realizar pagos. El sistema de banca por Internet utiliza el sistema del banco en el mainframe existente del banco para hacer esto y utiliza el sistema de correo electrónico existente del banco para enviar correo electrónico a los clientes. El código de color en el diagrama indica los sistemas de software que ya existen (las cajas grises) y los que se van a construir (azules).

# Nivel 2: El diagrama del contenedor

El nivel 2, un diagrama de contenedor, amplía el sistema de software y muestra los contenedores (aplicaciones, almacenamiento de datos, microservicios, etc.) que componen este sistema de software. Las decisiones tecnológicas son también una parte fundamental de este diagrama. El siguiente es un ejemplo de un diagrama de contenedor para el sistema de banca por Internet. Esto muestra que el sistema de banca por Internet (el cuadro punteado) consta de cinco contenedores: una aplicación web del lado del servidor, una aplicación de una sola página del lado del cliente, una aplicación móvil, una aplicación API del lado del servidor y una base de datos.

![](https://miro.medium.com/v2/resize:fit:700/1*TWUWldQW5vvDKOV0sQ-sbg.jpeg)

La Aplicación Web es un sistema Java/Spring MVC que simplemente muestra contenido estático (HTML, CSS y JavaScript), incluyendo el contenido que constituye la aplicación de una sola página. La aplicación de una sola página es una aplicación Angular que se ejecuta en el navegador web del cliente, proporcionando todas las características de la banca por Internet. Alternativamente, los clientes pueden utilizar una aplicación móvil integrada en Xamarin, plataforma cruzada, para acceder a un subconjunto de funcionalidades de banca por Internet. La aplicación de una sola página y la aplicación móvil utilizan una API JSON/HTTTPS, que proporciona otra aplicación Java/Spring MVC que se ejecuta en el lado del servidor. La aplicación en la API obtiene información de usuario de la base de datos (un esquema de base de datos relacional). La aplicación de la API también se comunica con el sistema bancario en el mainframe existente, utilizando una interfaz XML/HTTTPS propietaria, para obtener información sobre cuentas bancarias o realizar transacciones. La aplicación de la API también utiliza el sistema de correo electrónico existente si necesita enviar correo electrónico a los clientes.

# Nivel 3: El diagrama de componentes

El nivel 3, un diagrama de componentes, expande un contenedor individual para mostrar los componentes que contiene. Estos componentes deben asignarse a abstracciones reales (por ejemplo, una agrupación de códigos) en función de su código. A continuación se muestra un ejemplo de un diagrama de componentes para el sistema ficticio de banca por Internet que muestra algunos (en lugar de todos) de los componentes de la aplicación API.

![](https://miro.medium.com/v2/resize:fit:700/1*CCIKgdc_TAxCn6XlnnZMCw.jpeg)

Dos controladores MVC Spring en Rest proporcionan puntos de acceso a la API de JSON/HTTTPS, y cada controlador utiliza posteriormente otros componentes para acceder a los datos de la base de datos y del sistema bancario en el mainframe.

# Nivel 4: El código

Por último, si realmente lo desea o necesita, puede ampliar un componente individual para mostrar cómo se implementa este componente. Este es un diagrama de ejemplo (y parcial) de clases UML para el sistema ficticio de banca por Internet que muestra los elementos de código (interfaces y clases) que componen el componente MainframeBankingSystemFacade.

![](https://miro.medium.com/v2/resize:fit:700/1*UggQXl06gsCA5Xmprs6Bow.jpeg)

Este diagrama muestra que el componente consta de varias clases y que los detalles de implementación reflejan directamente el indicador. No recomendaría necesariamente la creación de diagramas a este nivel de detalle, especialmente cuando se pueden obtener bajo demanda de la mayoría de los IDEs.

# Una anotación

El modelo C4 no prescribe ninguna notación específica, y lo que usted ve en estos diagramas presentados es una notación simple que funciona bien en pizarras, papeles, notas adhesivas, fichas y una variedad de herramientas de diseño. También puede utilizar UML como notación, con el uso apropiado de paquetes, componentes y estereotipos.

Independientemente de la notación que utilice, le recomiendo que cada elemento incluya un nombre, el tipo de elemento (es decir, “Persona”, “Sistema de software”, “Contenedor” o “Componente”), una opción tecnológica (si procede) y algún texto descriptivo. Puede parecer inusual incluir tanto texto en un diagrama, pero este texto adicional elimina gran parte de la ambigüedad que se ve típicamente en los diagramas de arquitectura de software.

Asegúrese de tener una clave o leyenda para describir cualquier anotación que esté usando, incluso si es obvio para usted. Esto debe cubrir colores, formas, acrónimos, estilos de líneas, bordes, escalado, etc. Lo ideal es que su anotación sea coherente en todos los niveles de detalle. A continuación, presento la clave/leyenda del diagrama para el diagrama del contenedor que se muestra arriba.

![](https://miro.medium.com/v2/resize:fit:700/1*CKWYdqNAcjblEkzHmbfEtg.jpeg)

Para más información

El modelo C4 es una forma sencilla de comunicar la arquitectura del software en diferentes niveles de abstracción, de modo que se pueden contar diferentes historias a diferentes audiencias. También es una manera de introducir (a menudo reintroducir) algo de rigor y modelado ligero para los equipos de desarrollo de software. Visite c4model.com para obtener más información sobre el modelo C4, así como diagramas suplementarios (tiempo de ejecución e implementación), ejemplos, una lista de verificación de notación, preguntas frecuentes, vídeos de conferencias y opciones de herramientas.

Más información en [https://c4model.com/](https://c4model.com/)