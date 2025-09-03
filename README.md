# 🚀 DevOps-projekt

Detta arkiv innehåller grundläggande struktur och verktyg för att implementera ett modernt, automatiserat och skalbart DevOps-flöde.

## 📦 Innehåll

- terraform/
- ansible/
- pipeline/
- scripts/

## 🎯 Syfte

Projektets syfte är att visa hur man integrerar viktiga DevOps-verktyg för att uppnå:

- Automatiserade och säkra distributioner
- Reproducerbar infrastruktur
- Centraliserad konfiguration
- Effektiv övervakning och underhåll

## 🛠️ Tekniker som används

- Terraform
- Ansible
- GitHub Actions
- AWS EC2 / S3 / IAM
- Docker (valfritt)
- Bash / Python

## 📖 Kom igång

1. Klona arkivet:
   git clone https://github.com/AlexB1974/devops-proyecto.git
   cd devops-proyecto

2. Konfigurera dina AWS-uppgifter.

3. Distribuera infrastrukturen med Terraform:
   cd terraform
   terraform init
   terraform apply

4. Kör Ansible för att konfigurera servrarna:
   cd ../ansible
   ansible-playbook playbook.yml -i inventario

## 📄 Licens

Detta projekt är licensierat under MIT.
