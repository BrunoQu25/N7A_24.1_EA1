# Ejercicio de Aplicación

El siguiente ejercicio tiene como objetivo desarrollar una solución a un problema y documentar las decisiones de arquitectura utilizando Architecture Decision Records (ADR).

Los ADRs se utilizan para documentar **decisiones significativas de arquitectura**: _"architecturally significant decisions: those that affect the structure, non-functional characteristics, dependencies, interfaces, or construction techniques"._  Michael Nygard - November 15, 2011._

La letra del ejercicio la encuentra en [Indashboard] (<https://www.intedashboard.com/>)

En la carpeta __templates__ del repositorio encontrará dos subcarpetas, una con el template de ADR original simplificado y otra con uno mas elaborado. __Utilicé el que el docente le recomiende.__
  
- [Template de ADR Nygard](./templates/templateSimple/Template_ADR_Nygard_Simplificado.md)
- [Template de ADR con varias opciones](./templates/templateCompleto/Template_ADR_madr_Adaptado.md)


## Mecánica del ejercicio  
1. Para trabajar en su computadora debe clonar el repositorio, o  utilizar github codepsaces [Codespaces](instructions/img/Codespaces.png)
2. **No trabaje en main** (git checkout -b develop).
3. Cree una carpeta __solucion__ en la raíz del repositorio.
4. Los archivos con los ADRs que cree, agréguelos en una carpeta __./docs/architecture__ bajo **solucion**  
5. Al terminar el tiempo en clase __haga un commit para marcar lo hecho hasta el momento__. De esta forma si el docente permite que el ejercicio se termine fuera de clase queda registrado lo realizado en clase. 
6. Cuando termine completamente el ejercicio realice un pull request utilizando el template de revisión de ADRs. Marque los Items que correspondan en el PR y asígnelo a @gamousquesORT.

Como parte del ejercicio se espera que el equipo justifique sus decisiones. Recuerde almacenar los ADRs en una carpeta __./docs/architecture__ situada bajo la carpeta solución, y si utiliza diagramas en una carpeta img.

En la carpeta __templates__ se incluye el template en [formato word](./templates/templateCompleto/Template_ADR_madr_Adaptado.docx) **aunque es recomendable utilizar el formato markdown** [markdown cheat sheet](https://www.markdownguide.org/cheat-sheet/). VisualStudio Code es una buena herramienta para editar archivos markdown. También puede utilizar editores web como [dillinger.io](https://dillinger.io/)  

Tenga en cuenta que los ADRs pueden (y es recomendable) que incluyan diagramas. Para ello puede utilizar [draw.io](https://app.diagrams.net/), Astah, plantUML o cualquier otro software que le permita crear diagramas UML.

Recuerde que en los ADR es importante poner los nombres de los integrantes del equipo que están **presentes**.
