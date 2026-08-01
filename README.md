# Visor de chutes - [NOMBRE DE LA MINERA]

Este repositorio contiene la configuracion de esta minera: sus chutes,
sus modelos 3D y su Firebase. El motor (la parte pesada del codigo) vive
en un repositorio compartido aparte: `visor-chutes-core`.

## Configuracion inicial (una sola vez)

1. El `index.html` ya viene configurado con el usuario `Dimarza-chile` -- no necesitas tocar esto.

2. Completa `js/firebase-config.js` con los datos de tu proyecto Firebase
   para esta minera (Firebase Console -> Configuracion del proyecto).

3. En Firebase, activa Realtime Database y en Reglas pon (para pruebas):
   ```json
   { "rules": { ".read": true, ".write": true } }
   ```

## Como abrir un chute

```
tudominio.github.io/visor-chutes-XXXXX/?chute=CV201
```

## Como agregar un chute nuevo

1. Exporta el `.glb` desde SolidWorks (Extended Reality Exporter) y subelo
   a la carpeta `/models`.

2. Abre `js/chutes-config.js` y agrega un bloque nuevo (hay un ejemplo
   comentado). Ajusta:
   - `nombre`, `ot`, `otNombre`
   - `modelo`: ruta al .glb que subiste
   - `categorias`: cada grupo de piezas, con su funcion `match` (lee el
     nombre de cada pieza) y sus estados/colores propios
   - `vistasReporte`: que fotos arma el informe PDF

No hace falta tocar nada mas.

## Sobre los nombres de las piezas en SolidWorks

No es necesario que cada pieza tenga un nombre unico e irrepetible (si hay
nombres repetidos, el exportador les agrega un sufijo automatico). Lo que
si hace falta es una convencion consistente que el `match` de cada
categoria pueda reconocer, por ejemplo `Pg-izq-...` para placas guia,
`Pm-...` para estructura, o la convencion que definas para tus chutes.
