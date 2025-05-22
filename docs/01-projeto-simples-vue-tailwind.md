# 🚀 Guia Completo: Projeto simples para fixar conceitos com **VueJS** + **TailwindCSS** + **ESLint**

Este guia apresenta um passo a passo completo para criar um projeto Vue.js com Tailwind CSS e ESLint, incluindo configuração de desenvolvimento e resolução de problemas comuns.

## 🎯 Objetivo do Projeto

Este projeto foi criado para fixar conceitos fundamentais do **Vue.js** como:

- v-bind, v-model
- computed properties
- methods
- manipulação de listas com v-for
- estilização com **TailwindCSS**

Perfeito para quem está começando com Vue e quer ver a mágica da reatividade em ação! 😄

## 🛠️ Pré-requisitos

- Node.js instalado
- npm ou yarn
- VSCode (recomendado)
- Git (para versionamento)

## 📁 Estrutura Final do Projeto

```
carrinho-vue/
├── src/
│   ├── input.css
│   └── components/
├── dist/
│   └── output.css
├── assets/
│   └── preview.png
├── index.html
├── app.js
├── package.json
├── tailwind.config.js
├── eslint.config.mjs
└── README.md
```

---

## 🚀 Passo a Passo: Configuração do Ambiente

### Passo 1: Criação do Projeto

1. **Crie e navegue até a pasta do projeto:**

```bash
mkdir carrinho-vue && cd carrinho-vue
```

2. **Inicialize o package.json:**

```bash
npm init -y
```

3. **Crie os arquivos básicos:**

- `index.html`
- `app.js`
- `README.md`

### Passo 2: Instalação do Tailwind CSS

⚠️ **Problema Comum:** O comando `npm install -D tailwindcss@latest` pode instalar versões de desenvolvimento (4.x) que causam problemas.

**Solução:**

1. **Se já instalou uma versão problemática, desinstale primeiro:**

```bash
npm uninstall tailwindcss
```

2. **Instale uma versão estável específica:**

```bash
npm install -D tailwindcss@3.4.1
```

3. **Inicialize a configuração do Tailwind:**

```bash
npx tailwindcss init
```

**Alternativa se o erro persistir:**

```bash
npx tailwindcss@3.4.1 init
```

### Passo 3: Configuração do ESLint

1. **Instale o ESLint:**

```bash
npm install -D eslint
```

2. **Inicialize a configuração:**

```bash
npx eslint --init
```

**Respostas Recomendadas Durante a Configuração:**

- **How would you like to use ESLint?**
  → `To check syntax, find problems, and enforce code style`
- **What type of modules does your project use?**
  → `JavaScript modules (import/export)`
- **Which framework does your project use?**
  → `Vue.js`
- **Does your project use TypeScript?**
  → `No` (ou conforme sua preferência)
- **Where does your code run?**
  → `Browser`
- **How would you like to define a style for your project?**
  → `Use a popular style guide`
- **Which style guide do you want to follow?**
  → `Standard` ou `Airbnb`
- **What format do you want your config file to be in?**
  → `JavaScript`
- **What do you want to lint?**
  → `JavaScript files`

### Passo 4: Correção do ESLint para Node.js

⚠️ **Problema:** "module is not defined" no `tailwind.config.js`

**Solução:** Atualize seu arquivo `eslint.config.mjs`:

```javascript
import js from "@eslint/js";
import globals from "globals";
import pluginVue from "eslint-plugin-vue";
import { defineConfig } from "eslint/config";

export default defineConfig([
  {
    files: ["**/*.{js,mjs,cjs,vue}"],
    plugins: { js },
    extends: ["js/recommended"],
  },
  // Adiciona o ambiente de navegador E node para todos os arquivos
  {
    files: ["**/*.{js,mjs,cjs,vue}"],
    languageOptions: {
      globals: {
        ...globals.browser,
        ...globals.node, // Adiciona globals do Node.js
      },
    },
  },
  // Configuração específica para arquivos config
  {
    files: ["**/tailwind.config.js", "**/postcss.config.js", "**/*.config.js"],
    languageOptions: {
      globals: globals.node,
    },
  },
  pluginVue.configs["flat/essential"],
]);
```

---

## ⚙️ Configurações dos Arquivos

### 1. Configuração do CSS Build

**Crie o arquivo `src/input.css`:**

```css
@tailwind base;
@tailwind components;
@tailwind utilities;
```

**Configure scripts no `package.json`:**

```json
{
  "name": "carrinho-vue",
  "version": "1.0.0",
  "description": "Mini Carrinho de Compras feito com Vue.js + TailwindCSS",
  "scripts": {
    "build:css": "tailwindcss -i ./src/input.css -o ./dist/output.css",
    "watch:css": "tailwindcss -i ./src/input.css -o ./dist/output.css --watch",
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "keywords": ["vue", "tailwind", "carrinho", "aprendizado"],
  "author": "Seu Nome",
  "license": "ISC",
  "devDependencies": {
    "eslint": "^9.x.x",
    "tailwindcss": "^3.4.1"
  }
}
```

**Configure o `tailwind.config.js`:**

```javascript
module.exports = {
  content: ["./*.html", "./src/**/*.{html,js,vue}"],
  theme: {
    extend: {},
  },
  plugins: [],
};
```

### 2. Estrutura do HTML

**Opção A: Desenvolvimento Rápido (CDN)**

```html
<!DOCTYPE html>
<html lang="pt-br">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Mini Carrinho Vue</title>

    <script src="https://cdn.jsdelivr.net/npm/vue@3"></script>
    <link
      href="https://cdn.jsdelivr.net/npm/tailwindcss@2.2.19/dist/tailwind.min.css"
      rel="stylesheet"
    />
  </head>
  <body>
    <!-- Seu conteúdo aqui -->
    <script src="./app.js"></script>
  </body>
</html>
```

**Opção B: Produção (Build Local)**

```html
<!DOCTYPE html>
<html lang="pt-br">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Mini Carrinho Vue</title>

    <script src="https://cdn.jsdelivr.net/npm/vue@3"></script>
    <!-- Use o arquivo CSS local -->
    <link href="./dist/output.css" rel="stylesheet" />
  </head>
  <body>
    <!-- Seu conteúdo aqui -->
    <script src="./app.js"></script>
  </body>
</html>
```

---

## 🎨 README.md Profissional

```markdown
# 🛒 Mini Carrinho de Compras feito com Vue.js + TailwindCSS

Este é um projeto simples desenvolvido para fixar conceitos fundamentais do **Vue.js** como v-bind, v-model, computed, methods, e manipulação de listas com v-for e também com **HTML** e **TailwindCSS**.

É perfeito para quem está começando com Vue e quer ver a mágica da reatividade em ação! 😄

## 🔧 Tecnologias Usadas

- Vue.js 3 (via CDN)
- TailwindCSS
- HTML5
- ESLint (para qualidade de código)

## ✨ Funcionalidades

- ➕ Aumentar e diminuir quantidade de produtos
- 🗑️ Remover item do carrinho
- 💰 Cálculo automático do total
- 📱 Layout responsivo

## 🧠 Conceitos Praticados

- Computed properties
- Manipulação de dados reativos
- Interação com métodos (`add`, `remove`, etc.)
- Estilização responsiva com Tailwind
- Configuração de ambiente de desenvolvimento

## 🚀 Como Rodar

### Opção 1: Desenvolvimento Rápido

1. Clone o repositório ou baixe os arquivos
2. Abra o `index.html` em seu navegador
3. Pronto! Seu carrinho está funcionando 😎

### Opção 2: Ambiente Completo

1. Clone o repositório
2. Execute `npm install`
3. Execute `npm run watch:css` (para desenvolvimento)
4. Abra o `index.html` em seu navegador

## 📷 Preview

![preview](assets/preview.png)

---

Feito com 💚 para aprendizado
```

---

## 🛠️ Comandos de Desenvolvimento

- **Build CSS uma vez:**

  ```bash
  npm run build:css
  ```

- **Watch CSS (rebuilda automaticamente):**

  ```bash
  npm run watch:css
  ```

- **Lint do código:**

  ```bash
  npx eslint .
  ```

---

## 🐙 Versionamento com Git

1. **Inicie o Git e faça o primeiro commit:**

```bash
git init
git add .
git commit -m "🚀 Primeira versão do carrinho Vue"
```

2. **Crie um repositório no GitHub e conecte:**

```bash
git remote add origin https://github.com/seu-usuario/carrinho-vue.git
git branch -M main
git push -u origin main
```

---

## 🔧 Troubleshooting

### Cache do npm

Se enfrentar problemas persistentes de instalação:

```bash
npm cache clean --force
```

### Verificar versões instaladas

```bash
npm list tailwindcss
npm list eslint
```

### Reset completo (último recurso)

```bash
rm -rf node_modules package-lock.json
npm install
```

### Erro "could not determine executable to run"

- Certifique-se de usar `tailwindcss@3.4.1` em vez da versão 4.x
- Use `npx tailwindcss@3.4.1 init` se necessário

---

## 🎯 Extensões VSCode Recomendadas

- ESLint
- Vetur (para Vue.js)
- Tailwind CSS IntelliSense
- Vue Language Features (Volar)

---

## 📋 Checklist Final

- [ ] Node.js e npm instalados
- [ ] Projeto inicializado com `npm init -y`
- [ ] Tailwind CSS 3.4.1 instalado e configurado
- [ ] ESLint instalado e configurado
- [ ] Arquivos HTML e JS criados
- [ ] Build CSS funcionando
- [ ] Git inicializado
- [ ] README.md criado

## 📷 Preview do Projeto

![preview](..\assets\preview.png)
