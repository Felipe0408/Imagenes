## Estructura de control

![](https://github.com/Felipe0408/Imagenes/blob/main/ControlFlujoImg)

### Control de flujo: **FOR**
El bucle for permite iterar/repetir sobre una serie de elementos de una cadena, lista, rangos, etc...
#### Sintaxis
```
for VARIABLE in LISTA_VALORES
do
	COMANDO1
	COMANDO2
  ...
done
```
#### Lista de valores
Puede ser un rango numérico:
- **for** VARIABLE **in** 1 2 3 4 5 6 7 8 9;
- **for** VARIABLE **in** {1..10};
- serie de valores
- **for** VARIABLE **in** file1 file2 file3;
#### Ejemplo
script.sh
```
#!/bin/bash
	for numero in {1..20..2};
	do
		echo "Este es el número: $numero
	done
```

### Control de flujo: **IF**
El control de flujo IF permite evaluar condiciones cuando se cumplan y no se cumplan a tarvés de condiciones numéricos o cadenas de textos.
#### Sintaxis
- Sobre un condicional:
```
if [[CONDICIÓN]];
then
	COMANDO1 si se comple la condición
fi
```
-  Si la condición no se comple:
```
if [[CONDICIÓN]];
then
	COMANDO1 si se comple la condición
else
	COMANDO2 si no se comple la condición
fi
```
- más condicones concatenando más if:
```
if [[CONDICIÓN1]];
then
	COMANDO1 si se comple la condición
elif [[CONDICIÓN2]];
then
	COMANDO2 si se comple la condición2
else
	COMANDO3 si no se comple la condición2
fi
```
#### Condicionales
- Numérico:
	- -it (menor que)
	- -gt (mayor que)
	- -le (menor o igual que)
	- -ge (mayor o igual que)
	- -eq (igual)
	- -ne (no igual)
- Cadenas de texto
	- = (igual)
	- != (no igual)
	- < (es menor que, en orden alfabético ASCII)
	- \> (es mayorque, en orden alfabético ASCII)
	- -z (la cadena está vacía)
	- -n (la cadena no está vacía)
#### Ejemplo
script.sh
```
#!/bin/bash
set -e
echo 'Adivina el valro númerio de la variable'
read variable #entrada de datos

if [ $variable = 1 ]; then
	echo 'Acertaste'
	exit 0
elif [ $variable = 2 ]; then
	echo 'casi'
else
	echo 'no acertaste'
fi

exit 0
```

### Control de flujo: **WHILE**
El ciclo until se ejecutará el ciclo hasta que se cumpla la condición
#### Sintaxis
```
until [ CONDICION ]
do
	COMANDS
done
```
#### Ejemplo
scrip.sh
```
i=10
until [ $i -lt 0 ]
do
	echo $i
	((i--))
done
```

## Uso de Cron y Crontab
**Cron** es un demonio (que es como se conoce a un proceso en segundo plano) que se ejecuta desde el mismo instante en el que arranca el sistema operativo. Cron se encargará de comprobar si existe alguna tarea (job) para ser ejecutada, de acuerdo a la hora configurada en el propio sistema operativo. 

**Crontab** es un archivo de texto, se trata de un archivo con un contenido especial y específicamente diseñado para que sea leído correctamente por Cron y proceder con la ejecución que nosotros hayamos programado. Crontab posee una lista con todos los scripts a ejecutar, generalmente cada usuario del sistema posee su propio fichero Crontab, de esta forma, cada usuario podría programar sus propias tareas repetitivas independientemente, sin necesidad de que siempre tengamos que acudir al usuario administrador.
![](https://github.com/Felipe0408/Imagenes/blob/main/Cron_Crontab)

### Estructura de CRONTAB
![](https://github.com/Felipe0408/Imagenes/blob/main/Estructura_Crontab)


### Ejemplo **CONTRAB**
1. Programe un cron para que se ejecute a las 5 AM Todos los días
```
0 5 * * * /scripts/job.sh
```
2. Programe un cron para que se ejecute dos veces al día a las 6 AM y a las 6 PM.
```
0 6,18 * * * /scripts/job.sh
```
3. Programe un cron para que se ejecute cada minuto
```
* * * * /scripts/job.sh
```
4. Programe un cron para que se ejecute en cada Monday a las 7 PM.
```
0 19 * * mon /scripts/job.sh
```
5. Programe un cron para que se ejecute cada 15 minutos.
```
*/10 * * * * /scripts/job.sh
```
6. Programe un cron para que se ejecute en los meses seleccionados
```
* * feb,jun,oct * /script/job.sh
```
7. Ejecute el script de shell /home/script/backup.sh el 4 de marzo a las 7:25 AM
```
25 7 4 3 * /home/script/backup.sh
```
