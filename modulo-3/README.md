<div align="center">

# ☁️ AWS S3 + IAM  
## 📦 Módulo #3 - Almacenamiento en la Nube

<img src="https://img.shields.io/badge/AWS-S3-orange?style=for-the-badge&logo=amazonaws" />
<img src="https://img.shields.io/badge/IAM-Security-blue?style=for-the-badge&logo=amazonaws" />
<img src="https://img.shields.io/badge/Status-Completed-brightgreen?style=for-the-badge" />

---

### 🚀 Implementación de bucket tipo objeto con versionado y acceso seguro

</div>

---

# 📚 Descripción

En esta práctica se configuró un sistema de almacenamiento en la nube utilizando **Amazon Web Services (AWS)**.

Se realizaron las siguientes tareas:

✅ Creación de bucket en Amazon S3  
✅ Activación del versionado  
✅ Carga de archivo de prueba  
✅ Creación de usuario IAM  
✅ Permisos de solo lectura para un bucket específico

---

# 🗂️ Arquitectura del Proyecto

```text
                ┌─────────────────────┐
                │     Usuario AWS     │
                └──────────┬──────────┘
                           │
                           ▼
                ┌─────────────────────┐
                │   AWS Management    │
                │      Console        │
                └──────────┬──────────┘
                           │
         ┌─────────────────┴─────────────────┐
         ▼                                   ▼
┌──────────────────┐               ┌──────────────────┐
│   Amazon S3      │               │      AWS IAM     │
│  Bucket Storage  │               │ User Permissions │
└──────────────────┘               └──────────────────┘
         │                                   │
         ▼                                   ▼
 File Uploads                        Read-Only Access
 Versioning Enabled                 Specific Bucket
```
# 🎯 Objetivos

| Objetivo | Estado |
|----------|--------|
| Crear bucket S3 | ✅ |
| Activar versionado | ✅ |
| Subir archivo de prueba | ✅ |
| Crear usuario IAM | ✅ |
| Asignar permisos de solo lectura | ✅ |

---

# 🧰 Servicios Utilizados

| Servicio | Función |
|----------|---------|
| Amazon S3 | Almacenamiento de objetos |
| AWS IAM | Gestión de usuarios y permisos |

---

# ⚙️ Paso 1 - Crear Bucket en S3

## 📍 Ruta

AWS Console > S3 > Create Bucket

## Configuración realizada

| Parámetro | Valor |
|----------|-------|
| Tipo de bucket | Uso general |
| Región | us-east-2 |
| ACL | Deshabilitadas |
| Acceso público | Bloqueado |

## Nombre del bucket

bucket-alec-modulo3

📸 Captura sugerida: Pantalla de creación del bucket.

---

# 🔄 Paso 2 - Activar Versionado

## 📍 Ruta

Bucket > Properties > Bucket Versioning

## Acción realizada

✅ Enable Versioning

## Beneficios

- Conserva versiones anteriores
- Recuperación de archivos
- Protección ante errores

📸 Captura sugerida: Versioning Enabled.

---

# 📤 Paso 3 - Subir Archivo de Prueba

## 📍 Ruta

Bucket > Upload

## Acción realizada

- Seleccionar archivo local
- Subir archivo
- Confirmar carga

📸 Captura sugerida: Archivo visible dentro del bucket.

---

# 👤 Paso 4 - Crear Usuario IAM

## 📍 Ruta

AWS Console > IAM > Users > Create User

## Usuario creado

alecuser

📸 Captura sugerida: Pantalla de creación del usuario.

---

# 🔐 Paso 5 - Política de Solo Lectura para el Bucket

## Política aplicada

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "ListBucket",
      "Effect": "Allow",
      "Action": ["s3:ListBucket"],
      "Resource": "arn:aws:s3:::bucket-alec-modulo3"
    },
    {
      "Sid": "ReadObjects",
      "Effect": "Allow",
      "Action": ["s3:GetObject"],
      "Resource": "arn:aws:s3:::bucket-alec-modulo3/*"
    }
  ]
}
```
