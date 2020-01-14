# angular

ng build --prod --aot --builder-optimizer --ouput-hashing=none

Una breve explicación:

--prod: Le pide al compilador utilizar la configuración para el entorno de Producción

--aot: Habilita la compilación Ahed Of Time, necesaria para ciertos motores de render como el futuro Ivy

--builder-optimizer: Espectacular optimizador de los archivos JavaScript, pero puede demorar muchos minutos en compilar un proyecto muy grande

--output-hashing=none: Elimina el número de identificación de los archivos JS y CSS. Suele ser útil en la mayoría de los casos, pero si estamos compilando en un server, y nos encontramos en constante compilado, puede ser recomendable no usarlo o utilizar --output-hashing=all para que el server no utilice los archivos en caché


import { ServiceService } from '@core/service';

¿Se ve mejor no? ¡Podemos hacerlo! Para eso necesitamos modificar un par de líneas del tsconfig.json:

"compilerOptions": {
    "baseUrl": "src",
    "paths": {
      "@core/service": ["app/core/service.service"]
    }
}

De la vereda de los estilos, cabe la posibilidad de hacerlo con nuestros archivos SCSS, LESS o Stylus. Para esto modificaremos el angular.json (que en versiones anteriores a las 6 estaba oculto como .angular-cli.json):

"stylePreprocessorOptions": {
    "includePaths": ["src", "src/ruta/a/estilos"]
}

Esto lo incluiremos en architect -> build -> options, dentro de nuestro angular.json. Deberemos reemplazar src/ruta/a/estilos por nuestra ruta donde se encuentran nuestros CSS globales (no usar el nombre globals.scss o tendremos un conflicto con dependencias de Angular). Y así ya podremos llamarlo, en cualquier archivo de CSS pre-procesado, de la siguiente forma:

@import 'mi-css-global'
