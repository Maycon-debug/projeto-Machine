# 🚀 Como Enviar o Projeto para o GitHub

## 📋 Passo a Passo Completo

### 1️⃣ Criar Repositório no GitHub

1. Acesse [github.com](https://github.com) e faça login
2. Clique no botão **"+"** no canto superior direito
3. Selecione **"New repository"**
4. Preencha:
   - **Repository name:** `projeto-Machine` (ou outro nome de sua escolha)
   - **Description:** "Projeto Machine Learning - Predição de Desempenho de Estudantes"
   - **Visibility:** Escolha Public ou Private
   - **NÃO marque** "Initialize with README" (já temos um)
5. Clique em **"Create repository"**

### 2️⃣ Configurar Git (se ainda não fez)

```bash
git config --global user.name "Seu Nome"
git config --global user.email "seu.email@exemplo.com"
```

### 3️⃣ Adicionar Arquivos ao Git

```bash
# Adicionar todos os arquivos (exceto os ignorados pelo .gitignore)
git add .

# Verificar o que será commitado
git status
```

### 4️⃣ Fazer o Primeiro Commit

```bash
git commit -m "Initial commit: Projeto Machine Learning completo

- Etapa 1: EDA completa com relatório
- Etapa 2: Pré-processamento de dados
- Etapa 3: Modelo Baseline com guias completos
- Documentação completa em português"
```

### 5️⃣ Conectar com o Repositório Remoto

**Substitua `SEU_USUARIO` pelo seu usuário do GitHub:**

```bash
git remote add origin https://github.com/SEU_USUARIO/projeto-Machine.git
```

**OU se preferir usar SSH:**

```bash
git remote add origin git@github.com:SEU_USUARIO/projeto-Machine.git
```

### 6️⃣ Enviar para o GitHub

```bash
# Primeira vez (criar branch main)
git branch -M main
git push -u origin main
```

**Se pedir autenticação:**
- Use seu **token de acesso pessoal** (não sua senha)
- Para criar um token: GitHub → Settings → Developer settings → Personal access tokens → Generate new token

### 7️⃣ Verificar no GitHub

Acesse seu repositório no GitHub e verifique se todos os arquivos foram enviados!

---

## 🔄 Comandos para Atualizações Futuras

Quando fizer alterações no projeto:

```bash
# 1. Ver o que mudou
git status

# 2. Adicionar arquivos modificados
git add .

# 3. Fazer commit
git commit -m "Descrição das mudanças"

# 4. Enviar para GitHub
git push
```

---

## ⚠️ Arquivos que NÃO serão Enviados

O arquivo `.gitignore` está configurado para **NÃO enviar**:

- ✅ Arquivos Python compilados (`__pycache__/`, `*.pyc`)
- ✅ Checkpoints do Jupyter (`.ipynb_checkpoints/`)
- ✅ Ambientes virtuais (`venv/`, `env/`)
- ✅ Arquivos de IDE (`.vscode/`, `.idea/`)
- ✅ Arquivos temporários

**Nota:** Os dados (`data/*.csv`) e modelos (`models/*.pkl`) **SERÃO enviados** por padrão. Se preferir não enviar, descomente as linhas no `.gitignore`.

---

## 🐛 Problemas Comuns

### Erro: "remote origin already exists"

```bash
git remote remove origin
git remote add origin https://github.com/SEU_USUARIO/projeto-Machine.git
```

### Erro: "failed to push some refs"

```bash
git pull origin main --allow-unrelated-histories
git push -u origin main
```

### Esqueceu de adicionar arquivo

```bash
git add nome_do_arquivo
git commit -m "Adicionar arquivo esquecido"
git push
```

---

## 📝 Mensagens de Commit Sugeridas

Use mensagens descritivas:

```bash
# Adicionar nova etapa
git commit -m "feat: Adicionar Etapa 4 - Modelos Avançados"

# Corrigir bug
git commit -m "fix: Corrigir erro no cálculo de métricas"

# Atualizar documentação
git commit -m "docs: Atualizar README com novas informações"

# Melhorar código
git commit -m "refactor: Melhorar organização do código"
```

---

## ✅ Checklist Antes de Enviar

- [ ] Todos os arquivos importantes estão no projeto
- [ ] `.gitignore` está configurado corretamente
- [ ] README.md está atualizado
- [ ] Código está funcionando
- [ ] Não há informações sensíveis (senhas, tokens) no código
- [ ] Repositório foi criado no GitHub

---

**Pronto! Seu projeto está no GitHub!** 🎉

