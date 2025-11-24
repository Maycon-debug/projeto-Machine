# ⚙️ Como Configurar Nome e Email no Git

## 📋 Verificar Configuração Atual

Para ver qual nome e email estão configurados:

```bash
# Ver nome
git config --global user.name

# Ver email
git config --global user.email
```

## 🔧 Configurar Nome e Email

### Opção 1: Configuração Global (Recomendado)

Configura para **todos os projetos** no seu computador:

```bash
# Configurar nome
git config --global user.name "Seu Nome Completo"

# Configurar email
git config --global user.email "seu.email@exemplo.com"
```

**Exemplo:**
```bash
git config --global user.name "Maycon Silva"
git config --global user.email "mayconykarus@gmail.com"
```

### Opção 2: Configuração Apenas para Este Projeto

Se quiser usar um nome/email diferente apenas para este projeto:

```bash
# Remover --global para configurar apenas este projeto
git config user.name "Seu Nome"
git config user.email "seu.email@exemplo.com"
```

## ✅ Verificar se Foi Configurado Corretamente

```bash
# Ver todas as configurações
git config --global --list

# Ou ver apenas nome e email
git config --global user.name
git config --global user.email
```

## 📝 Configuração Atual do Seu Sistema

**Nome:** Maycon-debug  
**Email:** mayconykarus@gmail.com

## 💡 Dicas Importantes

1. **Use o mesmo email do GitHub:**
   - Se o email for diferente, seus commits podem não aparecer no seu perfil do GitHub
   - Você pode adicionar múltiplos emails no GitHub em Settings → Emails

2. **Email Privado no GitHub:**
   - Se você marcou "Keep my email address private" no GitHub, use o email no formato:
   ```
   seu-usuario@users.noreply.github.com
   ```

3. **Verificar no GitHub:**
   - GitHub → Settings → Emails
   - Veja quais emails estão associados à sua conta

## 🔄 Alterar Configuração Existente

Se quiser alterar:

```bash
# Alterar nome
git config --global user.name "Novo Nome"

# Alterar email
git config --global user.email "novo.email@exemplo.com"
```

## 🎯 Pronto!

Após configurar, todos os seus commits usarão essas informações automaticamente!

