# ✅ Guia de Merge de Branches com a Main (Fluxo Git)

Este guia explica como realizar o **merge de branches** com a `main` de forma **clara, segura** e seguindo as **boas práticas** de versionamento de código.

---

## ✅ 1. Garantir que está com a `main` atualizada

Antes de realizar o merge, é importante garantir que sua `main` está atualizada com o repositório remoto (GitHub):

```bash
git checkout main
git pull origin main
```

---

## ✅ 2. Fazer o merge da branch desejada

Por exemplo, para a branch `docs/guia-responsividade`:

```bash
git merge docs/guia-responsividade
```

Se **não houver conflitos**, o merge será realizado automaticamente.

Se houver **conflitos**, o Git irá avisar para você resolvê-los **manualmente**.

Depois de resolver os conflitos, finalize com:

```bash
git add .
git commit
```

---

## ✅ 3. Fazer o merge de outras branches (se houver)

Repita o mesmo processo para as demais branches:

```bash
git merge docs/construcao-html-carrinho-tailwindcss
```

---

## ✅ 4. Atualizar a `main` no repositório remoto

Depois de realizar todos os merges localmente, envie as mudanças para o repositório remoto (ex: GitHub):

```bash
git push origin main
```

---

## ✅ 5. Deletar branches (opcional)

Após o merge, se as branches **não forem mais necessárias**, é recomendado deletá-las para manter o repositório **limpo e organizado**.

### ➡️ Deletar branch localmente:

```bash
git branch -d docs/guia-responsividade
git branch -d docs/construcao-html-carrinho-tailwindcss
```

### ➡️ Deletar branch no remoto (GitHub):

```bash
git push origin --delete docs/guia-responsividade
git push origin --delete docs/construcao-html-carrinho-tailwindcss
```

⚠️ **Atenção**: só delete se tiver certeza de que não precisará mais dessas branches.

---

## ✅ 6. Fluxo visual do merge

```plaintext
docs/guia-responsividade
                         \
docs/construcao-html-carrinho-tailwindcss → main (merge final)
```

---

## ✅ 7. Alternativa: Merge via interface gráfica

- **No GitHub**:  
  → Clique em **“Compare & pull request”** → depois **“Merge pull request”**.

- **No VS Code**:  
  → Use o painel de **Source Control** → selecione a branch → clique em **“Merge...”**.

---

## ✅ Resumo rápido dos comandos principais:

```bash
git checkout main
git pull origin main

git merge <nome-da-branch>

git push origin main

# Opcional: deletar branch
git branch -d <nome-da-branch>
git push origin --delete <nome-da-branch>
```

---

## ✅ Boas práticas:

✅ Sempre atualize a `main` antes do merge.  
✅ Resolva conflitos com calma e clareza.  
✅ Deixe mensagens de commit informativas após resolver conflitos.  
✅ Delete branches que não serão mais usadas para evitar poluição no repositório.


