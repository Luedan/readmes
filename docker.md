# Que es el Dockerfile?
Un **Dockerfile** es un archivo de texto que contiene un conjunto de instrucciones para construir una imagen de Docker. Docker es una plataforma que permite desarrollar, enviar y ejecutar aplicaciones en contenedores, los cuales son entornos ligeros y portátiles que pueden ejecutar aplicaciones de manera aislada del sistema operativo subyacente.

### Función del Dockerfile

El **Dockerfile** especifica cómo se debe configurar y construir una imagen de Docker. Las imágenes de Docker son plantillas inmutables que se utilizan para crear contenedores. Al definir un Dockerfile, puedes automatizar el proceso de construcción de imágenes, asegurando que el entorno sea consistente y reproducible en cualquier lugar donde se despliegue.

### Componentes Clave de un Dockerfile

1. **FROM**: Especifica la imagen base que se va a utilizar. Por ejemplo, `FROM node:14` indica que se usará la imagen de Node.js versión 14 como base.
   
   ```dockerfile
   FROM node:14
   ```

2. **COPY** o **ADD**: Copia archivos y directorios desde el sistema de archivos del host al sistema de archivos del contenedor.

   ```dockerfile
   COPY . /app
   ```

3. **RUN**: Ejecuta comandos en el contenedor durante el proceso de construcción. Se utiliza para instalar dependencias, configurar el entorno, etc.

   ```dockerfile
   RUN npm install
   ```

4. **CMD** o **ENTRYPOINT**: Especifica el comando que se ejecutará cuando se inicie el contenedor. `CMD` se puede sobrescribir cuando se ejecuta el contenedor, mientras que `ENTRYPOINT` no.

   ```dockerfile
   CMD ["node", "app.js"]
   ```

5. **ENV**: Establece variables de entorno dentro del contenedor.

   ```dockerfile
   ENV PORT=3000
   ```

6. **EXPOSE**: Indica que el contenedor escuchará en los puertos especificados en tiempo de ejecución.

   ```dockerfile
   EXPOSE 3000
   ```

7. **WORKDIR**: Establece el directorio de trabajo dentro del contenedor. Es una buena práctica para mantener el entorno de trabajo organizado.

   ```dockerfile
   WORKDIR /app
   ```

### Ejemplo de Dockerfile

Aquí tienes un ejemplo de Dockerfile para una aplicación Node.js sencilla:

```dockerfile
# Utiliza la imagen base de Node.js 14
FROM node:14

# Establece el directorio de trabajo
WORKDIR /app

# Copia el package.json y package-lock.json
COPY package*.json ./

# Instala las dependencias
RUN npm install

# Copia el resto de los archivos de la aplicación
COPY . .

# Expone el puerto que usa la aplicación
EXPOSE 3000

# Define el comando por defecto para ejecutar la aplicación
CMD ["node", "app.js"]
```

### Uso del Dockerfile

Para construir una imagen de Docker usando un Dockerfile, navegas al directorio que contiene el Dockerfile y ejecutas:

```sh
docker build -t nombre-de-la-imagen .
```

Esto construirá la imagen siguiendo las instrucciones especificadas en el Dockerfile. Luego, puedes ejecutar un contenedor basado en esa imagen con:

```sh
docker run -p 3000:3000 nombre-de-la-imagen
```

Este comando iniciará un contenedor que ejecutará la aplicación en el puerto 3000.
