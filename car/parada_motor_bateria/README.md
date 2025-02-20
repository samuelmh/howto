# Parada de motor


```
AUTOR: Samuel M.H.
FECHA: Febero-2025
LICENCIA: todos los derechos reservados.
```


## Descripción del problema

Contexto:
* Se me descargó la batería dedl coche. Poco uso y desplazamientos cortos.
* Entre que cargué la batería y la instalé, pasaron 24 horas en las que el coche no tuvo **nada** de corriente.

Al coger el coche de nuevo, el motor se paraba.
* En ralentí parecía que se ahogaba, caían las revoluciones por debajo de 500RPM y luego subían.
* Circulando, las revoluciones caían en picado al pisar el embrague hasta el punto de que el motor se calaba/paraba si no usaba el acelerador.



## Detección del fallo
Investigando un poco...

El fallo se produce porque al dejar el coche sin batería, se desprograma el ETM (Electronic Throttle Module)[https://www.matthewsvolvosite.com/volvos-electronic-throttle-module-fiasco/], el módulo que controla la admisión.


## Solución

Suponiendo que la batería está bien. Seguí el siguiente procedimiento:

* Arrancar el coche y dejarlo a ralentí hasta que se caliente el motor.
* Con el motor caliente, esperar al menos 10 minutos a ralentí.
* Lo mismo con el aire acondicionado encendido.

Es **muy importante** no tocar el acelerador durante el proceso, ya que el módulo de admisión se está reprogramando automáticamente. Si el coche se cala, volver a arrancar y esperar.

Una vez finalizado, hay que dar un paseo por carretera con el motor caliente para que siga reprogramándose (con y sin aire acondicionado).

Y así me funcionó.

El procedimiento no es único para este coche, posiblemente funcione en otras marcas y modelos (ver referencias).


## Referencias

* [Volvo 2002 S60 Keeps stalling @ Stops after battery change](https://www.matthewsvolvosite.com/forums/viewtopic.php?t=54186)
* [S40 V40: Poor idle after battery change](https://www.volvoforums.org.uk/showthread.php?t=266885)
* [Volvo’s Electronic Throttle Module (ETM)](https://www.matthewsvolvosite.com/volvos-electronic-throttle-module-fiasco/)
* [[Idle Relearn Procedure After Battery Replacement](https://www.youtube.com/watch?v=xJkQjVKy1yY)] - Es otro coche, pero el procedimiento es parecido.

