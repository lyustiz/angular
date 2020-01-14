# angular

ng build --prod --aot --builder-optimizer --ouput-hashing=none

Una breve explicación:

--prod: Le pide al compilador utilizar la configuración para el entorno de Producción

--aot: Habilita la compilación Ahed Of Time, necesaria para ciertos motores de render como el futuro Ivy

--builder-optimizer: Espectacular optimizador de los archivos JavaScript, pero puede demorar muchos minutos en compilar un proyecto muy grande

--output-hashing=none: Elimina el número de identificación de los archivos JS y CSS. Suele ser útil en la mayoría de los casos, pero si estamos compilando en un server, y nos encontramos en constante compilado, puede ser recomendable no usarlo o utilizar --output-hashing=all para que el server no utilice los archivos en caché
