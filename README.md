# Cloud Computing for Data Science with Jupyter Notebooks

## Configuración de la instancia en DigitalOcean

- DigitalOcean dispone de una imagen denominada "Machine Learning and AI" que viene preinstalada con Python 3, R, Jupyter Notebook, TensorFlow, ScikitLearn y PyTorch.
<p align="center"><img src="https://i.imgur.com/LQvC8h8.png" width="50%"></p>

- Creemos un Droplet con una distribución como Ubuntu 16 LTS y seleccionemos la imagen "Machine Learning and AI".
- En tareas de análisis de datos, usualmente la cantidad de memoria RAM es el principal cuello de botella y ahí es donde una instancia cloud puede facilitar mucho el trabajo.
- Al conectarse a la instancia veremos que Jupyter Notebook ya se encuentra corriendo en el puerto 8888, así que basta ingresar a dicho puerto con la IP de la instancia en cualquier navegador acompañado del token de acceso y ya podemos empezar a usar Jupyter Notebook.

## Ejecutando Jupyter Lab en el puerto 8889

- La imagen de DigitalOcean también incluye [Jupyter Lab](https://github.com/jupyterlab/jupyterlab), la "evolución" de Jupyter Notebook, la cual cuenta con un completo rediseño de interfaz, ofreciendo una experiencia mucho más cercana a un IDE. Actualmente se encuentra en beta, veamos cómo usarlo en nuestra instancia.
- Habilitemos el puerto 8889 en el firewall: `sudo ufw allow 8889`.
- Para levantar el servicio en background podemos utilizar `screen`, con el fin de mantener el proceso corriendo aún después de terminar nuestra sesión.
- Una vez dentro de la sesión de screen, podemos utilizar el usuario _science_ creado por defecto para evitar ejecutar Jupyter Lab desde el usuario root: `su - science`.
- Para configurar una contraseña en lugar de seguir utilizando un token de acceso inicialicemos un archivo de configuración con `jupyter notebook --generate-config`.
- Una vez inicializado el archivo, podemos ejecutar `jupyter notebook password` para establecer la contraseña.
- Finalmente, para levantar Jupyter Lab ejecutemos `jupyter lab --no-browser --port=8889 --ip=0.0.0.0`.
- Listo! ahora solo basta entrar al puerto 8889 con la IP de nuestra instancia para acceder al entorno de Jupyter Lab.

## Explorando una competencia en Kaggle

- Kaggle es una de las plataformas de competencias de Data Science más grandes, con una gran variedad de competencias incluyendo data tanto estructurada como no estructurada y una comunidad bastante activa. Kaggle es un gran espacio para practicar y aprender sobre análisis de datos y modelamiento predictivo.
- La competencia recomendada para empezar es [Titanic: Machine Learning from Disaster](https://www.kaggle.com/c/titanic). Trabajaremos sobre este dataset para tener una mayor comprensión sobre parte de la secuencia de tareas realizadas en Data Science.
- El dataset puede ser descargado con mayor comodidad en nuestra instancia a través del [API oficial de Kaggle](https://github.com/Kaggle/kaggle-api): `kaggle competitions download -c titanic -w`.
- Para poder usar el API de Kaggle tenemos que registrar nuestras credenciales en el archivo: `~/.kaggle/kaggle.json`.
- Es bueno restringir el acceso a dicho archivo a solo el usuario actual: `chmod 600 ~/.kaggle/kaggle.json`.
