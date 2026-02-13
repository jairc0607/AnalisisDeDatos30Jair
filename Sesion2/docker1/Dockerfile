#Referenciar una imagen (Python)
FROM ubuntu:20.04
#Evitar que el SO evite las instalaciones manuales
ENV DEBIAN_FRONTEND=noninteractive

#Ejecutar algunas atualizaciones de sistemas y paquetes
RUN apt-get update && apt-get install -y \
    python3 \
    python3-pip \
    python3-dev \
    build-essential \
    wget && \
    apt-get clean

# Actualizar pip e instalar el JNotebook
RUN pip3 install --upgrade pip && \
    pip3 install notebook==6.5.6

#Definir el directorio del trabajo
WORKDIR /workspace

#Donde se guardará las configuraciones de Jupyter
RUN mkdir -p /root/.Jupyter

# Asignación de variables de configuración
RUN echo "c.NotebookApp.token =''" >> /root/.jupyter_notebook_config.py && \
    echo "c.NotebookApp.password =''" >> /root/.jupyter_notebook_config.py && \
    echo "c.NotebookApp.allow_root = True" >> /root/.jupyter_notebook_config.py && \
    echo "c.NotebookApp.open_browser = False" >> /root/.jupyter_notebook_config.py

# Exponer el puerto de la imagen
EXPOSE 8080

# COmando por defecto para iniciar el contenedor

CMD ["Jupiter", "notebok", "--ip=0.0.0.0", "--port=8888", "--no-open_browser", "allow_root"]