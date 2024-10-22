#frontend #arquitectura

> **Tabla de contenidos:**
- [[#Title 1]]
- [[#Title 2]]
	- [[#Subtitle 1]]
	- [[#Subtitle 2]]
- [[#Title 3]]
-
*Arquitecturas de FrontEnd, prerenderizados, hidratación y resumability (csr - ssr - spa - mpa, etc...)
# ==🔨ARTICLE IN CONSTRUCTION ==

---

¡Buenas!, nos volvemos a reencontrar en esta ocasión para explicar brevemente diferentes **estrategias de renderizado** para tu aplicación web junto a las **tecnologías especializadas** en estos campos.
Esto es de suma importancia comprenderlo ya que te ayudara demasiado en como se debería maquetar un proyecto antes de codearlo según los requerimientos que exija así que... 

**¡Vamos a ello!.**

## ¿Qué es una estrategia de renderizado?

Tenemos que comprender que la renderización se trata de **diferentes maneras de servir el contenido HTML al navegador web** para que el usuario pueda verlo. 
Para esto, se han creado diversas estrategias para **solucionar este problema** y cada una tiene sus virtudes y defectos, como por ejemplo: 
- **==Static Site Generator (SSG):==** nos permite tener un buen **SEO** (Search Engine Optimization), (**Para resumir**: nos permite tener un mejor posicionamiento en los motores de búsqueda web utilizando los famosos **Web Crawlers**), pero a costo de tener un **Build-Time** demasiado costoso a medida que escale la aplicación.


## Tipos de renderizado

#### CSR (Client Side Rendering)
