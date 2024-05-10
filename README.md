# Proof Of Concept GitLab 13.10.2 RCE (Unauthenticated)

## ¿Como y porque se acontece esta Vulnerabilidad?

Cuando un usuario carga una imagen con cualquiera de las  extensiones jpeg/jpg/tiff  , Gitlab Workhorse la envía a  Exiftool  para filtrar contenido malicioso según etiquetas predefinidas en la lista blanca. Exiftool intenta determinar la validez del tipo de archivo en función del contenido proporcionado. Entonces, si el usuario cambia el nombre del archivo, se puede cargar cualquier analizador en lugar de solo las extensiones mencionadas.

Debido a una validación inadecuada, si un actor malicioso con acceso de red al puerto 443 pasa una imagen con la  anotación DjVu  que incluye metadatos maliciosos, puede ejecutar comandos arbitrarios en el servidor, bajo el  usuario git  .

Para replicar este escenenario y visualizar la vulnerabilidad, replicar los comandos proporcionados en el Poc.txt
