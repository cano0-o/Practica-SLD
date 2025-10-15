# LegalMente - Resolución SLD en Python

Este proyecto implementa un motor de inferencia basado en **Resolución SLD (Selective Linear Definite-clause resolution)** en Python. El objetivo es simular el razonamiento de un sistema experto capaz de responder consultas sobre una base de conocimiento definida mediante cláusulas de Horn.

## Descripción del Proyecto

El script `sld_practice.py` toma un programa lógico (una lista de hechos y reglas) y una consulta (query), y utiliza el algoritmo de Resolución SLD para encontrar todas las sustituciones de variables que satisfacen dicha consulta. Además, para facilitar la comprensión del proceso, el script imprime la ruta de derivación detallada paso a paso, mostrando cómo el sistema llega a una conclusión.

El proyecto utiliza una pequeña sección de la base de conocimientos del sistema experto "LegalMente", enfocado en trámites vehiculares en Ensenada.

## Estructura del Repositorio

* `sld_practice.py`: El script principal que contiene el motor de Resolución SLD.
* `base_conocimiento.txt`: Un archivo de texto que describe los hechos y reglas utilizados en la demostración.
* `README.md`: Este archivo.

## Base de Conocimiento Utilizada

Para la demostración, hemos seleccionado un subconjunto de reglas y hechos relacionados con la **expedición de la licencia de conducir**.

### Hechos:

Representan conocimiento fundamental y verdadero en nuestro sistema.

* `requerimiento('expedicion_licencia', 'identificacion_oficial').`
    * Significa: Para la expedición de licencia se requiere una identificación oficial.
* `requerimiento('expedicion_licencia', 'comprobante_domicilio').`
    * Significa: Para la expedición de licencia se requiere un comprobante de domicilio.
* `requerimiento('expedicion_licencia', 'certificado_medico').`
    * Significa: Para la expedición de licencia se requiere un certificado médico.
* `costo('expedicion_licencia', 3, 1077.80).`
    * Significa: El costo de la expedición de licencia por 3 años es de $1077.80.
* `lugar('expedicion_licencia', 'Secretaria de Hacienda de Ensenada').`
    * Significa: El trámite de expedición de licencia se realiza en la Secretaría de Hacienda de Ensenada.

### Reglas (Cláusulas de Horn):

Permiten al sistema inferir nuevo conocimiento a partir de los hechos.

1.  **Regla 1: `puede_tramitar(Persona, Tramite)`**
    * `puede_tramitar(Persona, Tramite) :- cumple_requisitos(Persona, Tramite).`
    * Significado: Una `Persona` puede realizar un `Tramite` si cumple con todos los requisitos para ese trámite.

2.  **Regla 2: `cumple_requisitos(Persona, Tramite)`**
    * `cumple_requisitos(Persona, Tramite) :- tiene(Persona, 'identificacion_oficial'), tiene(Persona, 'comprobante_domicilio'), tiene(Persona, 'certificado_medico').`
    * Significado: Una `Persona` cumple los requisitos para un `Tramite` si tiene los tres documentos necesarios. (Para este ejemplo, asumimos que los requisitos son fijos).

## ¿Cómo Ejecutar el Script?

1.  Asegúrate de tener Python 3 instalado.
2.  Coloca los archivos `sld_practice.py` y `base_conocimiento.txt` en el mismo directorio.
3.  Abre una terminal en ese directorio y ejecuta el siguiente comando:

```bash
python sld_practice.py
