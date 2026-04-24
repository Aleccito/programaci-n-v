# Laboratorio Docker — Contenerización de aplicación Python

## Objetivo

Validar la creación, ejecución y administración de un contenedor básico en Docker sobre una instancia EC2 con Amazon Linux 2023.

---

## Entorno

| Campo | Valor |
|---|---|
| Plataforma | AWS EC2 — Amazon Linux 2023 |
| Acceso | SSH con clave `.pem` |
| Usuario | `ec2-user` |
| Directorio de trabajo | `~/docker-practica` |

---

## Pasos realizados

### 1. Conexión a la instancia EC2

```bash
ssh -i C:\Users\xxx\Downloads\xxx.pem ec2-user@xxx.xxx.xxx.xxx
```

---

### 2. Crear el directorio del proyecto

```bash
mkdir docker-practica
cd docker-practica
```

---

### 3. Crear `app.py`

```bash
vi app.py
```

**Contenido:**

```python
print("Hola desde Docker")
```

---

### 4. Crear el `Dockerfile`

```bash
vi Dockerfile
```

**Contenido:**

```dockerfile
FROM python:3.11-slim

WORKDIR /app

COPY app.py .

CMD ["python", "app.py"]
```

> `python:3.11-slim` es una imagen base ligera que reduce el tamaño final de la imagen.

---

### 5. Instalar e iniciar Docker

```bash
sudo yum install docker -y
sudo systemctl start docker
sudo systemctl enable docker
```

---

### 6. Construir la imagen

```bash
sudo docker build -t hola-python .
```

---

### 7. Listar imágenes

```bash
sudo docker images
```

**Salida:**

```
REPOSITORY    TAG       IMAGE ID       CREATED         SIZE
hola-python   latest    xxxxxxxxxxxx   xx seconds ago  124MB
```

---

### 8. Listar contenedores activos

```bash
sudo docker ps
```

**Salida:**

```
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES
```

> Sin contenedores activos antes de ejecutar, como se esperaba.

---

### 9. Ejecutar el contenedor

```bash
sudo docker run hola-python
```

**Salida:**

```
Hola desde Docker
```

---

## Estructura del proyecto

```
docker-practica/
├── app.py
└── Dockerfile
```

---

## Evidencia de cumplimiento

| Requisito | Estado |
|---|---|
| Imagen base ligera de Python | ✅ `python:3.11-slim` |
| Archivo `app.py` creado | ✅ Imprime "Hola desde Docker" |
| Imagen construida con `docker build` | ✅ `hola-python:latest` — 124 MB |
| Contenedor ejecutado con `docker run` | ✅ Salida correcta en terminal |
| Imágenes listadas con `docker images` | ✅ |
| Contenedores listados con `docker ps` | ✅ |
