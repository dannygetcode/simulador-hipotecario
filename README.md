# Simulador del crédito hipotecario en Colombia

Simulador web interactivo del modelo Logit de la monografía **«Determinantes del financiamiento de vivienda en Bogotá y algunas cabeceras departamentales de Colombia, 2019-2024»**, de Daniel Fernando Barragán Chía (Universidad Pedagógica y Tecnológica de Colombia, UPTC).

Se mueven las características de un hogar (edad e ingreso del jefe, educación, formalidad laboral, territorio y año) y una escena 3D muestra cómo cambia la probabilidad estimada de tener un crédito hipotecario activo: con probabilidad baja la casa aparece como un plano con reja (racionamiento de crédito); al subir, se construye y la familia llega a la puerta.

## Qué incluye

- Modelo Logit principal con selector de año (2019 / 2024) y prueba de robustez Probit.
- Hogar de referencia en las medias de cada territorio, con la tasa observada mostrada aparte.
- Efectos marginales promedio con su significancia.
- Curva de ciclo de vida (probabilidad vs. edad).
- Modo Retos, pestaña «Cómo leerlo» y tarjeta del paper con descarga del PDF.

## Cómo leer los resultados

- Todo es **asociación estadística**, no causalidad. Las comparaciones entre 2019 y 2024 son descriptivas.
- El ingreso **no es estadísticamente significativo** en el Logit (ni en 2019 ni en 2024): por eso el slider mueve poco el resultado.
- «Muestra de estudio» es Bogotá más las tres cabeceras analizadas; **no** es el promedio nacional.
- La probabilidad del hogar de referencia (en las medias) no tiene por qué coincidir con la tasa observada.
- Los territorios son cabeceras departamentales de la ECV (Boyacá, Tolima, Meta), no las ciudades capitales.

## Datos y modelo

- Fuente: DANE, Encuesta Nacional de Calidad de Vida (ECV) 2019 y 2024, con factor de expansión FEX_C.
- Todos los coeficientes y descriptivas están en [`model.json`](model.json); el simulador no usa otras cifras.
- Variable dependiente: hogar con vivienda en proceso de pago (crédito hipotecario activo).

## Ejecutar en local

El simulador carga `model.json` con `fetch`, que no funciona abriendo el archivo directamente. Desde la carpeta del proyecto:

```bash
python -m http.server 8000
```

y abrir <http://localhost:8000>.

## Estructura

```
index.html   # HTML + CSS + JS del simulador (sin build)
model.json   # coeficientes, errores estándar, efectos marginales y descriptivas
assets/      # PDF de la monografía
```

Three.js y GSAP se cargan por CDN (jsdelivr, versiones fijas); las fuentes, desde Google Fonts.

## Autor

Daniel Fernando Barragán Chía · UPTC
