# 🚀 Módulo #2 - Implementación de Infraestructura en AWS

![AWS](https://img.shields.io/badge/AWS-Cloud-orange?style=for-the-badge&logo=amazonaws)
![EC2](https://img.shields.io/badge/EC2-Virtual%20Machine-blue?style=for-the-badge)
![VPC](https://img.shields.io/badge/VPC-Network-green?style=for-the-badge)
![Linux](https://img.shields.io/badge/Linux-Amazon%20Linux-yellow?style=for-the-badge&logo=linux)

---

## 📌 Descripción

En este laboratorio se desarrolló una infraestructura básica en la nube utilizando Amazon Web Services (AWS). Se creó una red privada virtual (VPC), una subred pública y una máquina virtual Linux mediante EC2. Finalmente, se configuró acceso remoto seguro mediante SSH restringido a una dirección IP específica.

---

## 🎯 Objetivos

✅ Crear una VPC personalizada  
✅ Configurar una subred pública  
✅ Lanzar una instancia Linux EC2  
✅ Asignar IP pública  
✅ Restringir acceso SSH solo a una IP autorizada  
✅ Verificar conectividad remota  
✅ Mostrar sistema operativo instalado

---

## 🏗️ Arquitectura Implementada

```text id="z3m8n7"
Internet
   │
   ▼
Public IP
   │
   ▼
Security Group (SSH Puerto 22 - Mi IP)
   │
   ▼
EC2 Amazon Linux
   │
   ▼
VPC (10.0.0.0/16)
   │
   ▼
Subred Pública
