# 🚀 Módulo #2 - Creación de Infraestructura en AWS

## 📌 Descripción del Proyecto

En este laboratorio se implementó una infraestructura básica en Amazon Web Services (AWS), creando una red virtual privada (VPC), una subred pública y una máquina virtual Linux (EC2). Además, se configuró acceso seguro por SSH restringido únicamente a una dirección IP específica.

---

## 🎯 Objetivos

- Crear una VPC personalizada.
- Configurar al menos una subred pública.
- Lanzar una instancia Linux en AWS EC2.
- Asignar una IP pública.
- Restringir acceso SSH solo a una IP autorizada.
- Conectarse remotamente mediante SSH.
- Verificar el sistema operativo instalado.

---

## 🛠️ Tecnologías Utilizadas

- Amazon Web Services (AWS)
- Amazon VPC
- Amazon EC2
- Amazon Linux 2023
- SSH
- PowerShell

---

## 🌐 Configuración de Red

### VPC creada

| Parámetro | Valor |
|--------|------|
| Nombre | MODULO2-vpc |
| CIDR | 10.0.0.0/16 |

### Subred Pública

| Parámetro | Valor |
|--------|------|
| Tipo | Pública |
| Zona de disponibilidad | us-east-2a |

---

## 💻 Instancia EC2

| Parámetro | Valor |
|--------|------|
| Nombre | LinuxUniversidad |
| Sistema Operativo | Amazon Linux 2023 |
| Tipo | t3.micro |
| IP Pública | Habilitada |

---

## 🔒 Seguridad Implementada

Se configuró un Security Group permitiendo únicamente acceso SSH desde la IP del administrador.

```text id="hclx2j"
Tipo: SSH
Puerto: 22
Origen: Mi IP (/32)
