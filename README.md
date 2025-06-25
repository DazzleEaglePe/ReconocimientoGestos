
# Reconocimiento de Gestos con MediaPipe

Este proyecto tiene como objetivo el reconocimiento de gestos en tiempo real utilizando **MediaPipe** y **Flask** para el backend, junto con **MySQL** para almacenar los resultados. El proyecto captura imágenes en tiempo real desde la cámara, procesa los gestos (como **pulgar arriba** o **puño**) y los guarda en una base de datos.

## Requisitos

### 1. **Instalar dependencias**:

Para ejecutar este proyecto, necesitarás instalar las siguientes dependencias:

- Python 3.10 o superior
- `pip` para gestionar las dependencias

Puedes instalar las dependencias necesarias con:

```bash
pip install -r requirements.txt
```

El archivo **`requirements.txt`** incluye:

- Flask
- MediaPipe
- OpenCV
- mysql-connector-python

### 2. **Configurar la base de datos MySQL**:

El proyecto usa una base de datos **MySQL** para almacenar los gestos detectados. Sigue estos pasos para crear la base de datos y la tabla necesaria:

#### 2.1 Crear la base de datos

- Abre **phpMyAdmin** o usa un cliente MySQL como **MySQL Workbench**.
- Crea una base de datos llamada **`gestos_db`**.

```sql
CREATE DATABASE gestos_db;
```

#### 2.2 Crear la tabla de gestos

Ejecuta el siguiente script SQL para crear la tabla **`gestos`** dentro de la base de datos **`gestos_db`**:

```sql
CREATE TABLE gestos (
    id INT AUTO_INCREMENT PRIMARY KEY,
    usuario_id INT,
    gesto VARCHAR(100),
    confianza DECIMAL(5,2),
    timestamp DATETIME DEFAULT CURRENT_TIMESTAMP
);
```

#### 2.3 Configurar la conexión a la base de datos

En el archivo **`config.py`**, configura las credenciales de tu base de datos MySQL:

```python
DB_CONFIG = {
    'host': 'localhost',
    'user': 'root',           # tu usuario de MySQL
    'password': '',           # tu contraseña de MySQL
    'database': 'gestos_db'   # la base de datos que creaste
}
```

### 3. **Ejecutar el servidor Flask**:

Para ejecutar el servidor de Flask, sigue estos pasos:

1. Asegúrate de tener el entorno virtual activado:

```bash
.venv\Scriptsctivate
```

2. Ejecuta el servidor con el siguiente comando:

```bash
python app.py
```

Esto iniciará el servidor en **`http://127.0.0.1:5000/`**. Abre esta URL en tu navegador para acceder a la interfaz del proyecto.

### 4. **Usar el proyecto**:

1. El video se mostrará en tiempo real desde la cámara de tu dispositivo.
2. Los gestos (como **pulgar arriba** o **puño**) se detectarán y se enviarán automáticamente al backend.
3. Los gestos detectados se guardarán en la base de datos MySQL.
4. Los resultados se mostrarán en el área de **`#resultados`** de la página.

### 5. **Verificación y pruebas**:

- Puedes probar el funcionamiento del sistema interactuando con la página web.
- Si todo está bien configurado, los gestos detectados aparecerán en el área de **`#resultados`** en la página web.

### 6. **Problemas comunes**:

- **Error de conexión a la base de datos**: Verifica que MySQL esté en ejecución y que las credenciales en **`config.py`** sean correctas.
- **Error al ejecutar el servidor**: Asegúrate de tener las dependencias correctas instaladas con `pip install -r requirements.txt`.

---

### **Contribuciones**:

Si deseas contribuir a este proyecto, siéntete libre de hacer un **fork** y enviar un **pull request**. ¡Toda ayuda es bienvenida!

---

### **Licencia**:

Este proyecto está bajo la **Licencia MIT**. Si deseas usarlo en proyectos comerciales, por favor revisa la licencia.
