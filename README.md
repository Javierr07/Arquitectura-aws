# 🌍 Arquitectura de Alta Disponibilidad con Auto Scaling y Load Balancer  

*Descripción**  
Implementación de una infraestructura escalable y de alta disponibilidad en AWS utilizando EC2, ALB, Auto Scaling y RDS.  

## 📁 Servicios Utilizados  
- **VPC** → Redes públicas y privadas  
- **EC2** → Instancias en un Auto Scaling Group  
- **ALB (Application Load Balancer)** → Balanceo de carga  
- **Auto Scaling Group** → Escalabilidad automática  
- **RDS** → Base de datos en subredes privadas  

## 📜 Arquitectura  
![Arquitectura AWS](architecture.png)  

## ⚙️ Configuración  
1. **VPC y Subredes:** Configuración de redes públicas y privadas.  
2. **Auto Scaling:** Implementación de escalado basado en CPU.  
3. **Load Balancer:** Configuración de ALB con Target Groups.  
4. **RDS:** Creación de una base de datos en subredes privadas.  

## 🚀 Pasos para Implementar  
```bash
# Clonar el repositorio
git clone https://github.com/tu-usuario/aws-high-availability.git
cd aws-high-availability
