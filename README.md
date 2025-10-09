<p align="center">
  <img src="assets/qax-logo.png" alt="QAX Logo"/>
</p>

# Proyecto Modelo para realizar las entregas 

![QAX](https://img.shields.io/badge/QAX-Mentorias-orange?style=for-the-badge&logo=github)
![QA Pro Level](https://img.shields.io/badge/QA-ProLevel-blueviolet?style=for-the-badge&logo=target)

Repositorio **plantilla** para automatización de **API**. Diseñado para aprendices de **QAX** y pensado como **portafolio profesional** para entrevistas.

## 🎯 Propósito
- Facilitar un repositorio organizado para tus entregas por *Stage*.
- Mantener consistencia visual y de estructura entre API, Web y Mobile.
- Mostrar habilidades reales en tu GitHub.

## 🧱 Estructura base
```
.
├── Stage_1
│   ├── Quick_Tasks
│   │   └── README.md
│   ├── Challenge
│   │   └── README.md
│   └── Mission
│       └── README.md
├── Stage_2
│   ├── Quick_Tasks
│   ├── Challenge
│   └── Mission
├── README.md
├── .gitignore
└── assets/
```
> Agrega más *Stages* si tu plan lo requiere.

## 🚀 Cómo usar esta plantilla
1. **En GitHub**: entra a este repo → botón **Use this template** → crea tu repositorio.
2. **Con GitHub CLI**:
   ```bash
   gh repo create <tu-repo> --template <OWNER/REPO> --public --clone
   ```
3. Cambia el `README.md` con tu nombre y detalles de cada entrega.

## 🛠️ Tecnologías (sugeridas)
- REST APIs · (elige: Rest Assured + Postman, Karate, Robot Framework)
- Manejo de tokens, esquemas JSON, mocks
- Reportes HTML/JSON

> Personaliza este bloque con el stack exacto que uses.

## 🧪 Habilidades demostradas
- Diseño de casos y criterios de aceptación.
- Automatización modular, *fixtures* y datos de prueba.
- Buenas prácticas de versionamiento y documentación.
- Ejecución local y en CI (opcional).
- Reportes de resultados y trazabilidad.

## 📝 Convenciones mínimas
- **Commits**: `tipo(scope): mensaje` (ej. `test(login): agrega caso feliz`).  
- **Ramas**: `stageX/tipo/nombre` (ej. `stage1/retos/challenge-login-basico`).


---

> 👨‍🏫 **Este repositorio fue creado como parte de la mentoría QA Pro Level de QAX.**