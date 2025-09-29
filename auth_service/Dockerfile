# Imagen base de Python
FROM python:3.11-slim

# Definir el directorio de trabajo dentro del contenedor
WORKDIR /app

# Instalar dependencias del sistema necesarias para compilar psycopg2
RUN apt-get update && apt-get install -y \
    build-essential \
    libpq-dev \
    && rm -rf /var/lib/apt/lists/*

# Copiar archivo de dependencias
COPY requirements.txt .

# Instalar dependencias de Python
RUN pip install --no-cache-dir -r requirements.txt

# Copiar el resto del código del microservicio
COPY . .

# Exponer el puerto que usará Django
EXPOSE 8000

# Comando por defecto al levantar el contenedor
CMD ["python", "manage.py", "runserver", "0.0.0.0:8000"]
