# Autenticação com Firebase (v2)

Este diretório adiciona suporte para autenticação com Firebase ao site estático.

O objetivo é fornecer arquivos prontos que você pode incluir no `index.html` sem alterar o arquivo principal automaticamente. Siga os passos abaixo para ativar o login com E-mail/Senha e Google.

Passos rápidos

1. Crie um projeto no Firebase Console: https://console.firebase.google.com/
2. Ative Authentication → Providers → Email/Password e Google (se quiser Google Sign-In).
3. Em Project settings → General, copie a configuração do seu app (o objeto firebaseConfig).
4. No `index.html`, dentro do <head> ou antes do fechamento do <body>, adicione os SDKs do Firebase compat e o script deste repositório, exemplo:

```html
<!-- SDKs do Firebase (compat) -->
<script src="https://www.gstatic.com/firebasejs/10.13.0/firebase-app-compat.js"></script>
<script src="https://www.gstatic.com/firebasejs/10.13.0/firebase-auth-compat.js"></script>
<script src="https://www.gstatic.com/firebasejs/10.13.0/firebase-firestore-compat.js"></script>

<!-- Defina sua configuração do Firebase (substitua pelos valores do console) -->
<script>
  window.FIREBASE_CONFIG = {
    apiKey: "SUA_API_KEY",
    authDomain: "SEU_PROJETO.firebaseapp.com",
    projectId: "SEU_PROJETO",
    // ... restante da configuração
  };
</script>

<!-- Script de autenticação (deste repo) -->
<script src="/auth/firebase-auth.js"></script>
```

5. Cole o bloco HTML do formulário (abaixo) no local do seu `index.html` onde quer que apareça o login — por exemplo, dentro do `#topbarActions` ou no final do `<body>`:

```html
<!-- Início do bloco de login (cole no index.html) -->
<div id="auth-root">
  <form id="loginForm" style="display:block; max-width:320px">
    <label for="email">E-mail</label>
    <input id="email" type="email" class="input" required />
    <label for="password">Senha</label>
    <input id="password" type="password" class="input" required />
    <div style="display:flex; gap:8px; margin-top:10px">
      <button id="loginBtn" class="btn btn-primary" type="submit">Entrar</button>
      <button id="signupBtn" type="button" class="btn btn-secondary">Registrar</button>
      <button id="googleBtn" type="button" class="btn" style="background:#4285F4; color:#fff">Google</button>
    </div>
  </form>

  <div id="userArea" style="display:none; gap:8px; align-items:center">
    <div id="userEmail" style="font-weight:700"></div>
    <button id="logoutBtn" class="btn btn-secondary">Sair</button>
  </div>

  <div id="protectedContent" style="display:none; margin-top:16px">
    <h3>Área protegida</h3>
    <p>Conteúdo visível apenas para usuários autenticados.</p>
  </div>
</div>
<!-- Fim do bloco de login -->
```

6. Atualize a regra de hospedagem se necessário (se estiver usando Firebase Hosting) e publique.

Observações de segurança

- Este código usa o SDK compat do Firebase e é projetado para sites estáticos.
- Não exponha outros segredos (como chaves de serviço) no cliente.

Se preferir, posso aplicar automaticamente a alteração no `index.html` do repositório e commitar o trecho de UI e a inclusão do SDKs (você precisa confirmar). Caso queira que eu faça isso, confirme e eu atualizo o arquivo `index.html` diretamente.
