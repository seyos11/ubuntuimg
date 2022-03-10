# ubuntuimg

Este repositorio está basado en el repositorio de José Vírseda(josevirseda) y contiene un helm chart para ser empleado posteriormente, en nuestro caso, en OSM.


La primera tarea a realizar es la de generar una estructura adecuada para el Helm Chart. Por un lado tenemos un directorio (src/<nameOfOurChart>) donde se alojan los templates y el chart en sí. También encontramos bajo este directorio el archivo values.yaml donde se encuentran los valores que se envían a los templates de kubernetes, facilitándo así una mayor automatización del despliegue de kubernetes así como mayor capacidad a la hora de configurar dicho despliegue. 

Además de esta estrucutura se ha de tener un fichero index.yaml donde vienen metadatos correspondientes al helm chart y que son necesarios para la instalación. El siguiente paso es transformar el directorio src en un fichero comprimido tgz mediante el siguiente comando:
```
helm package src/<nameOfOurChart>
```
Una vez tenemos ya la esrtuctura completa y subida a github el último paso a realizar es el de generar una página web accesible desde el exterior que permita el acceso al chart. Para ello hacemos uso del servicio pages de github que nos proporcionará el enlace necesario para el comentado acceso.
  
Una vez se dispone de la url del repositorio del chart en github lo único que hay que hacer es una actualización del repositorio de Helm donde se esté trabajando:
  
```
helm repo add "<enlaceRepositorio>"
helm repo update
´´´
En el caso de OSM se disponen de dos opciones a la hora de realizar esta actualización de repositorio:
  
1. Uso del comando osm repo-add con el cual se añade el repositorio de helm chart en el apartado de k8s repos.
  
2. A través del cliente web proporcionado con OSM podemos añadirlo manualmente desde la sección de k8s repos. 
  
