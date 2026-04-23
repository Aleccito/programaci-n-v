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
# 🔗 Paso 6 - Asignar Política al Usuario

## 📍 Ruta

AWS Console > IAM > Users > alecuser > Permissions

## Procedimiento

1. Ingresar al servicio IAM.  
2. Seleccionar el usuario **alecuser**.  
3. Ir a la pestaña **Permisos**.  
4. Hacer clic en **Agregar permisos**.  
5. Seleccionar **Adjuntar políticas directamente**.  
6. Buscar la política creada previamente.  
7. Marcar la política **SoloLecturaBucket**.  
8. Confirmar con **Agregar permisos**.  

## Resultado final

Usuario: alecuser  
Permiso asignado: SoloLecturaBucket

📸 Captura sugerida: Usuario mostrando la política asignada.

---

# 🧹 Paso 7 - Eliminar Permiso General (Opcional)

## 📍 Ruta

AWS Console > IAM > Users > alecuser > Permissions

## Procedimiento

1. Seleccionar la política **AmazonS3ReadOnlyAccess** si fue asignada antes.  
2. Hacer clic en **Eliminar**.  
3. Confirmar la eliminación.  

## Resultado esperado

El usuario conservará únicamente acceso al bucket específico.


# 🛡️ Seguridad Implementada

| Configuración | Estado |
|--------------|--------|
| Acceso público bloqueado | ✅ |
| ACL deshabilitadas | ✅ |
| Usuario IAM creado | ✅ |
| Permiso restringido al bucket | ✅ |
| Solo lectura aplicada | ✅ |

---

# 🧠 Aprendizajes Obtenidos

- Gestión de usuarios IAM  
- Aplicación de políticas personalizadas  
- Seguridad en AWS  
- Control de acceso por recursos  
- Principio de mínimo privilegio  

---

# 🏁 Conclusión

Se completó correctamente la asignación de permisos al usuario IAM, restringiendo el acceso únicamente al bucket creado.  

Con esta configuración se garantiza un entorno más seguro y una correcta administración de accesos dentro de AWS.

