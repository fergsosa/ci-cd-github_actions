# 🚀 GitHub Actions Boilerplate

## 📋 Tabla de Contenidos

- [Estructura del Proyecto](#-estructura-del-proyecto)
- [Índice de Workflows](#-índice-de-workflows)
- [Quick Start](#-quick-start)
- [Configuración](#-configuración)
- [Casos de Uso](#-casos-de-uso)
- [Best Practices](#-best-practices)
- [Recursos](#-recursos)

## 📁 Estructura del Proyecto

```
github-actions-boilerplate/
│
├── .github/
│   └── workflows/
│       ├── 01-basic-hello-world.yml
│       ├── 02-variables-and-secrets.yml
│       ├── 03-reusable-build.yml
│       ├── 04-reusable-test.yml
│       ├── 05-reusable-deploy.yml
│       ├── 06-orchestrator-pipeline.yml
│       └── 07-advanced-conditionals.yml
│
└── README.md
```

## 🗂️ Índice de Workflows

| #   | Workflow                                               | Descripción                        | Nivel         | Trigger          |
| --- | ------------------------------------------------------ | ---------------------------------- | ------------- | ---------------- |
| 00  | [orchestrator-pipeline.yml](#06-orchestrator-pipeline) | Pipeline CI/CD completo            | 🔴 Avanzado   | `push`           |
| 01  | [basic.yml](#01-basic-hello-world)                     | Introducción a GitHub Actions      | 🟢 Básico     | `push`           |
| 02  | [variables-and-secrets.yml](#02-variables-and-secrets) | Variables, secrets y condicionales | 🟡 Intermedio | `workflow_call`  |
| 03  | [reusable-build.yml](#03-reusable-build)               | Workflow reutilizable de build     | 🟡 Intermedio | `workflow_call`  |
| 04  | [reusable-test.yml](#04-reusable-test)                 | Workflow reutilizable de testing   | 🟡 Intermedio | `workflow_call`  |
| 05  | [reusable-deploy.yml](#05-reusable-deploy)             | Workflow reutilizable de deploy    | 🟡 Intermedio | `workflow_call`  |
| 06  | [conditionals.yml](#07-conditionals)                   | Lógica compleja y condicionales    | 🔴 Avanzado   | `push`, `manual` |

## 🚀 Quick Start

### 1. Clonar el Repositorio

```bash
git clone https://github.com/fergsosa/ci-cd-github_actions.git
cd ci-cd-github_actions
```

### 2. Configurar Secrets

Navega a: `Settings > Secrets and variables > Actions > New repository secret`

Secrets requeridos:

```
USERNAME_FER=tu_usuario
password_fer=tu_password
```

### 3. Configurar Variables

Navega a: `Settings > Secrets and variables > Actions > Variables`

Variables requeridas:

```
PROJECT_VERSION=1.0.0
ENVIRONMENT=development
```

### 4. Ejecutar tu Primer Workflow

```bash
# Hacer un commit y push para activar el workflow básico
git add .
git commit -m "Test: Activar workflow básico"
git push origin main
```

## ⚙️ Configuración

### Secrets Requeridos

| Secret         | Descripción                   | Ejemplo  |
| -------------- | ----------------------------- | -------- |
| `USERNAME_FER` | Usuario para autenticación    | `fer`    |
| `password_fer` | Contraseña para autenticación | `fer123` |

### Variables de Repositorio

| Variable          | Descripción          | Valor por defecto |
| ----------------- | -------------------- | ----------------- |
| `PROJECT_VERSION` | Versión del proyecto | `1.0.0`           |
| `ENVIRONMENT`     | Entorno de ejecución | `development`     |

### Variables de Entorno (en workflows)

```yaml
env:
  platform: aws
  region: us-east-1
  account: 9999-2222-1111
```

## 💡 Casos de Uso

### Caso 1: Pipeline CI/CD Completo

Usa el workflow `00-orchestrator-pipeline.yml` que ejecuta:

1. ⚓ Básicos
1. 📏 Variables
1. 🛠️ Build
1. 🧪 Tests automáticos
1. 🚀 Deploy a producción
1. ❓Condicionales
1. 📊 Validación final

### Caso 2: Workflows Reutilizables

Crea workflows modulares que pueden ser llamados desde otros:

```yaml
jobs:
  call-build:
    uses: ./.github/workflows/03-reusable-build.yml
```

### Caso 3: Ejecución Condicional

Ejecuta jobs solo cuando se cumplen condiciones específicas:

```yaml
if: ${{ env.platform == 'aws' && env.username == 'fer' }}
```

## ✨ Best Practices

### 1. Nomenclatura Clara

- Usa prefijos numéricos para orden de aprendizaje
- Nombres descriptivos que indiquen el propósito
- Formato consistente: `##-category-description.yml`

### 2. Seguridad

- ✅ Nunca hardcodees secrets en el código
- ✅ Usa `${{ secrets.NAME }}` para datos sensibles
- ✅ Limita permisos de GITHUB_TOKEN cuando sea posible

### 3. Reutilización

- 📦 Crea workflows reutilizables con `workflow_call`
- 🔄 Usa actions del marketplace cuando sea apropiado
- 🎯 Evita duplicación de código

### 4. Performance

- ⚡ Usa caché para dependencias
- 🎯 Ejecuta jobs en paralelo cuando sea posible
- 📊 Limita el uso de recursos innecesarios

### 5. Mantenibilidad

- 📝 Documenta cada workflow y sus parámetros
- 🏷️ Usa nombres claros para jobs y steps
- 🔍 Incluye logs informativos

## 📚 Recursos

### Documentación Oficial

- [GitHub Actions Documentation](https://docs.github.com/en/actions)
- [Workflow Syntax](https://docs.github.com/en/actions/using-workflows/workflow-syntax-for-github-actions)
- [GitHub Actions Marketplace](https://github.com/marketplace?type=actions)

### Herramientas Útiles

- [actionlint](https://github.com/rhysd/actionlint) - Linter para workflows
- [act](https://github.com/nektos/act) - Ejecuta workflows localmente
- [GitHub Actions VSCode Extension](https://marketplace.visualstudio.com/items?itemName=GitHub.vscode-github-actions)

## 👨‍💻 Autor

**Tu Nombre**

- GitHub: [@fergsosa](https://github.com/fergsosa)
- LinkedIn: [Fernando Sosa](https://www.linkedin.com/in/fercode)

---

<div align="center">
  
**¿Te resultó útil este proyecto? ¡Dale una ⭐ en GitHub!**

[⬆ Volver arriba](#-github-actions-boilerplate)

</div>
