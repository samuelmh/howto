# Cómo ver la pantalla de tu móvil en el ordenador (en Linux)

```
AUTOR: Samuel M.H.
FECHA: 29-Octubre-2020
LICENCIA: todos los derechos reservados.
```

En este tutorial explico la forma gratuita y más sencilla que he encontrado para poder ver en la pantalla de un PC con linux lo mismo que se vé en la de un teléfono móvil. Solo es para imagen, no para audio.

**Nota:** supongo que el usuario tiene nociones mínimas de cómo instalar paquetes. No obstante todo el tema de librerías está delegado en Docker.

**Motivación:** tuve que montar una video-conferencia por whatsapp y no era operativo estar varias personas con una pantalla diminuta.


## Activa el modo desarrollador en el móvil
1. Apps > Ajustes > Acerca del teléfono > Información de software.
2. Pincha 7 veces sobre "Número de compilación" para activar el modo desarrollador.
3. Apps > Ajustes > Opciones de desarrollador (este menú es nuevo).
4. Ponlo en Activado.
5. Activa depuración de USB.

## En Linux
Instala los siguiente paquetes.

* adb
* docker-engine

## Conexión móvil-PC
1. Enchufa el móvil al PC por USB
2. Cuando en el móvil pregunte "¿Permitir depuración por USB?", confirmar.
3. En una consola escribe `adb devices`. 
  * Se arrancará el servicio adb.
  * Tiene que aparecer el móvil en la lista.
4. En mi caso, para instalar Whatsapp.
  * Descargué Whatsapp de su [web](https://www.whatsapp.com)
  * Lo instalé con `adb install WhatsApp.apk`.
5. Como ya hemos verificado todo, cerramos el servidor adb `adb kill-server`
  * Este paso es muy importante porque utilizaremos otro servidor adb dentro del contenedor y solo puede haber uno controlando el móvil.

## Contenedor Docker
Para correr la aplicación [scrcpy](https://github.com/Genymobile/scrcpy), que es la encargada de hacer la magia, usaremos un [contenedor de Docker ya creado](https://github.com/pierlon/scrcpy-docker).

1. Con la siguiente orden, arrancamos el contenedor y se nos abre una consola.
  * Nota: sustituye intel por amd o nvidia según sea tu tarjeta gráfica.
```
docker run --rm -i -t --privileged \
    -v /dev/bus/usb:/dev/bus/usb \
    -v /tmp/.X11-unix:/tmp/.X11-unix \
    -e DISPLAY=$DISPLAY \
    pierlo1/scrcpy:intel
```
2. Arrancamos el servidor adb y verificamos que detecta el dispositivo.
```
adb devices
```
3. Arrancamos la aplicación scrcpy. Se nos abrirá una pantalla donde se vé la pantalla del móvil.
```
scrcpy
```

## Extra: grabar la sesión en vídeo

1. Al arrancar el contenedor Docker, le decimos dónde guardar el vídeo. En este caso en la carpeta `tmp/whatsapp` dentro de mi `home` de usuario.
```
docker run --rm -i -t --privileged \
    -v /dev/bus/usb:/dev/bus/usb \
    -v /tmp/.X11-unix:/tmp/.X11-unix \
    -v ~/tmp/whatsapp:/video \
    -e DISPLAY=$DISPLAY \
    pierlo1/scrcpy:intel
```
 2. Arrancamos el servidor adb y verificamos que detecta el dispositivo.
```
adb devices
```
3. Arrancamos scrcpy. En este caso, graba en horizontal y en el nombre del fichero de vídeo se guarda la hora.
```
scrcpy --lock-video-orientation 1 --record /video/video_`date +%F_%H-%M`.mp4
```


## Conclusiones
Todo este lío no hubiera sido necesario si se cumpliera alguna de estas premisas:
* La gente estuviera más concienciada con la usabilidad y favoreciera cualquier otra aplicación que funcione en un PC (zoom, meet, teams, skype, etc).
* Android tuviera de fábrica un streamer de audio/video. O yo hubiera encontrado una aplicación que lo hiciera.
* Whatsapp tuviera un cliente para Linux o funcionase su vídeo en la aplicación web.
* El protocolo de Whatsapp fuera abierto y no boicotearan cualquier intento de hacer un cliente libre.

Quick & dirty pero funciona. Gracias software libre! Otra vez.
