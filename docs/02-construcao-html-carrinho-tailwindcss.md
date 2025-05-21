# 🧱 Construção do HTML do Carrinho com TailwindCSS

### ✅ Explicando cada classe:

| Classe      | Por quê usar?                                                        |
| ----------- | -------------------------------------------------------------------- |
| `max-w-2xl` | Limita a largura para deixar o conteúdo compacto e mais fácil de ler |
| `mx-auto`   | Centraliza horizontalmente o bloco no meio da tela                   |
| `mt-10`     | Dá espaço no topo da página                                          |
| `bg-white`  | Fundo branco para contraste                                          |
| `p-6`       | Padding interno: espaçamento dentro do card                          |
| `rounded`   | Deixa os cantos arredondados (visual mais amigável)                  |
| `shadow`    | Adiciona uma sombra leve para destacar o card                        |

---

## 🛍️ Título do Carrinho

```html
<h1 class="text-xl sm:text-2xl font-semibold text-center mb-6">
  Carrinho de compra
</h1>
```

### ✅ Decisões:

- `text-xl` para mobile e `sm:text-2xl` para telas maiores

- `text-center` para centralizar

- `font-semibold` para deixar em seminegrito

- `mb-6` para separar do conteúdo abaixo

---

## 📦 Bloco de Produto

### 🔧 Estrutura com Responsividade

```html
<div class="flex flex-col sm:flex-row sm:items-center sm:justify-between border-t py-4 gap-4">
  <!-- Lado esquerdo: imagem + info -->
  <div class="flex items-center gap-4">
    <div class="w-16 h-16 bg-gray-200 rounded-full flex items-center justify-center text-sm text-gray-500">72x72</div>
    <div>
      <p class="font-medium">Produto A</p>
      <p class="text-sm text-gray-500">#12345</p>
    </div>
  </div>

  <!-- Lado direito: quantidade, preço, remover -->
  <div class="flex flex-wrap sm:flex-nowrap items-center gap-2 sm:gap-4">
    <button class="border px-2 rounded">-</button>
    <span class="w-8 text-center">1</span>
    <button class="border px-2 rounded">+</button>
    <span class="font-semibold">R$10.50</span>
    <button class="text-red-600 font-bold text-xl">✕</button>
  </div>
</div>
```

---

### ✅ Explicações por parte

#### 📐 Layout geral:

| Classe                      | Motivo                                                              |
| --------------------------- | ------------------------------------------------------------------- |
| `flex flex-col sm:flex-row` | Empilha no mobile, organiza lado a lado no desktop                  |
| `sm:items-center`           | Centraliza verticalmente os conteúdos no layout horizontal          |
| `sm:justify-between`        | Distribui os dois blocos (esquerda e direita) com espaço entre eles |
| `gap-4`                     | Dá espaçamento entre elementos no eixo principal                    |

#### 🖼️ Imagem + Informações:

| Classe                             | Motivo                                  |
| ---------------------------------- | --------------------------------------- |
| `w-16 h-16`                        | Tamanho fixo de 64x64px                 |
| `bg-gray-200`                      | Cor de fundo neutra para simular imagem |
| `rounded-full`                     | Deixa o bloco da imagem redondo         |
| `flex items-center justify-center` | Centraliza o texto no “círculo”         |

#### ➕➖ Quantidade e Preço:

| Classe                     | Motivo                                               |
| -------------------------- | ---------------------------------------------------- |
| `flex-wrap sm:flex-nowrap` | Permite quebra de linha no mobile, impede no desktop |
| `border px-2 rounded`      | Estilo simples nos botões                            |
| `text-red-600`             | Cor vermelha no botão de remover                     |
| `font-semibold`            | Destaque no preço                                    |

---

## 🔻 Rodapé

```html
<div class="flex justify-between items-center mt-6">
  <a href="#" class="text-blue-600 hover:underline">Continuar comprando</a>
  <p class="text-lg font-semibold">Total: R$200.20</p>
</div>
```

### ✅ Detalhes:

- `flex justify-between`: distribui os elementos horizontalmente

- `text-blue-600`: cor azul no link

- `hover:underline`: efeito visual ao passar o mouse

- `text-lg font-semibold`: destaque no total final

---

## 💡 Conclusão

Com esse layout, seu carrinho:

- Fica lindo no desktop ✅

- Funciona perfeitamente em celulares ✅

- Tem código claro e organizado ✅

Essa estrutura serve como base para conectar com Vue.js e deixar o carrinho dinâmico com reatividade.
