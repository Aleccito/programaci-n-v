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

### Imagen base ligera de Python
<img width="431" height="274" alt="image" src="https://github.com/user-attachments/assets/cf91e4c3-c85d-4980-90b8-2fa7f1f871eb" />


### Archivo `app.py` creado
<img width="413" height="57" alt="image" src="https://github.com/user-attachments/assets/269847a4-9e7c-4079-9dd6-3482304b15be" />

### Imagen construida con `docker build`
<img width="655" height="29" alt="image" src="https://github.com/user-attachments/assets/effc450f-5939-4b40-92ad-ec04dab1687a" />
<img width="707" height="80" alt="image" src="https://github.com/user-attachments/assets/33b1a88d-c6fb-430f-8e69-f0d97a217fa4" />

### Contenedor ejecutado con `docker run`
<img width="629" height="34" alt="image" src="https://github.com/user-attachments/assets/0c731040-f375-413a-980d-64fb375a7a59" />
<img width="328" height="27" alt="image" src="https://github.com/user-attachments/assets/c45b16fd-9d2c-415d-b4b7-bdce5465f6c7" />

### Imágenes listadas con `docker images`
<img width="764" height="35" alt="image" src="https://github.com/user-attachments/assets/26506fe4-bc37-408e-9132-696e4f0408e6" />

### Contenedores listados con `docker ps`
