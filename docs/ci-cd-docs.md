# Documentation CI/CD Pipeline

## Призначення
Документація в проєкті є частиною Definition of Done і повинна автоматично перевірятися та збиратися в CI/CD.

## Артефакти документації
Автоматичній генерації або перевірці підлягають:
- OpenAPI-специфікація (`docs/api/openapi.yaml`)
- Swagger UI
- Storybook
- загальний сайт документації з MkDocs

## Тригери pipeline
- push у feature-гілку
- pull request у `main`
- merge у `main`

## Послідовність кроків pipeline

### 1. Validate OpenAPI
- перевірити синтаксис `openapi.yaml`
- перевірити наявність `info`, `paths`, `components`, `responses`, `security`

### 2. Build Swagger UI
- згенерувати інтерактивну API-документацію зі специфікації

### 3. Build Storybook
- зібрати візуальну документацію UI-компонентів

### 4. Build MkDocs site
- згенерувати загальний статичний сайт документації

### 5. Publish
- опублікувати документацію на GitHub Pages

## Місце публікації
Документація публікується на GitHub Pages.

### Приклад URL
- `https://username.github.io/project-name/`
- `https://username.github.io/project-name/swagger/`
- `https://username.github.io/project-name/storybook/`

## Versioning
Версія документації повинна відповідати версії продукту.

### Правила
- `v1.0` — початкова стабільна документація
- зміни без breaking changes збільшують minor-версію
- breaking API changes вимагають нової major-версії документації

## Приклад GitHub Actions pipeline

```yaml
name: Docs Pipeline

on:
  push:
    branches:
      - main
      - 'feature/**'
  pull_request:
    branches:
      - main

jobs:
  docs:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout repository
        uses: actions/checkout@v4

      - name: Setup Node.js
        uses: actions/setup-node@v4
        with:
          node-version: 20

      - name: Setup Python
        uses: actions/setup-python@v5
        with:
          python-version: '3.11'

      - name: Install MkDocs
        run: pip install mkdocs

      - name: Validate OpenAPI file
        run: echo "OpenAPI validation step"

      - name: Build Swagger UI
        run: echo "Swagger UI build step"

      - name: Build Storybook
        run: echo "Storybook build step"

      - name: Build MkDocs site
        run: mkdocs build

      - name: Publish docs
        run: echo "Deploy to GitHub Pages"