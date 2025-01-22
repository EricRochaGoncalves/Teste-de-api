

# Sistema de Login com API do Google

Eu não sou como todos vocês,
Eu não sou apenas mais um dev júnior que segue tutoriais e copia código. Eu sou aquele que resolve problemas de maneiras inovadoras, que não tem medo de aprender e experimentar. Eu não me contento com o básico, e não fico preso às limitações. Programar no celular? Feito. API do Google? Eu implemento. Não sou apenas um dev, sou alguém que constantemente desafia os limites e redefine o que é possível. Não subestimem o poder de um dev que está sempre evoluindo. Porque eu não sou como todos vocês.

"Eu sou mais forte, mais esperto, eu sou melhor, eu sou melhor."


---

# Tecnologias usadas


![HTML](https://img.shields.io/badge/HTML-E34F26?style=flat-square&logo=html5&logoColor=white)
![CSS](https://img.shields.io/badge/CSS-1572B6?style=flat-square&logo=css3&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat-square&logo=javascript&logoColor=black)
![Google API](https://img.shields.io/badge/Google_API-34A853?style=flat-square&logo=google&logoColor=white)
![Code Studio](https://img.shields.io/badge/Code_Studio-007ACC?style=flat-square&logo=visualstudiocode&logoColor=white)

---

Como Implementar o Login com Google API

Este tutorial mostra como integrar o Login com a API do Google no seu projeto. Ele permitirá que os usuários se autentiquem com suas contas do Google.

Passos para Implementação:

1. Criar um Projeto no Google Cloud Console

Para usar a Google API em seu projeto, você precisa configurar um projeto no Google Cloud Console. Aqui estão os passos para configurar:

Acesse Google Cloud Console.

Crie um novo projeto ou use um já existente.

Vá para APIs & Services > Library.

Pesquise por Google Sign-In API e ative-a.

Vá para APIs & Services > Credentials.

Crie um ID de Cliente OAuth 2.0:

Escolha Web application como o tipo de aplicação.

Adicione a URL de redirecionamento para seu site.

Copie o Client ID e Client Secret gerados.



2. Incluir o Script da Google API no Seu HTML

Adicione o script da Google API no cabeçalho do seu arquivo index.html:

<script src="https://apis.google.com/js/api.js"></script>

Isso carregará a API do Google em seu site, permitindo o uso da autenticação.

3. Configurar a Autenticação do Google em Seu Código JavaScript

Agora, vamos configurar o login com Google no seu arquivo app.js. Primeiro, você precisa inicializar a API do Google com o Client ID que você obteve no Google Cloud Console.

function start() {
    gapi.client.init({
        apiKey: 'SUA_API_KEY',  // Insira sua API Key aqui
        clientId: 'SEU_CLIENT_ID',  // Insira seu Client ID aqui
        scope: 'https://www.googleapis.com/auth/userinfo.profile',
        discoveryDocs: ["https://www.googleapis.com/discovery/v1/apis/plus/v1/rest"]
    }).then(function () {
        // Carregar o botão de login
        gapi.auth2.getAuthInstance().isSignedIn.listen(updateSigninStatus);
        updateSigninStatus(gapi.auth2.getAuthInstance().isSignedIn.get());
    });
}

function updateSigninStatus(isSignedIn) {
    if (isSignedIn) {
        // Exibir informações do usuário
        var user = gapi.auth2.getAuthInstance().currentUser.get();
        var profile = user.getBasicProfile();
        document.getElementById("user-name").innerHTML = profile.getName();
        document.getElementById("user-info").style.display = "block";
    }
}

function handleSignInClick() {
    gapi.auth2.getAuthInstance().signIn();
}

function handleSignOutClick() {
    gapi.auth2.getAuthInstance().signOut();
}

gapi.load('client:auth2', start);

4. HTML para o Botão de Login

Crie um botão de login que aciona a função de autenticação no seu arquivo index.html:

<button id="google-login" class="google-btn" onclick="handleSignInClick()">Login com Google</button>

5. Estilização do Botão de Login (CSS)

Adicione o estilo básico ao botão de login no arquivo styles.css:

.google-btn {
    background-color: #4285F4;
    color: white;
    padding: 10px 20px;
    border: none;
    border-radius: 4px;
    font-size: 16px;
    cursor: pointer;
    transition: background-color 0.3s;
}

.google-btn:hover {
    background-color: #357ae8;
}

6. Exibindo as Informações do Usuário

Depois de realizar o login com sucesso, as informações do usuário serão exibidas no seu site. O código JavaScript acima cuida dessa parte, exibindo o nome do usuário:

<div id="user-info" class="user-info" style="display: none;">
    <h3>Bem-vindo, <span id="user-name"></span></h3>
</div>

7. Conclusão

Agora, seu projeto está integrado com a Google API para realizar o login com Google! Quando o usuário clicar no botão de login, será redirecionado para a página de login do Google, e após a autenticação, as informações do usuário serão exibidas.

Dica

Lembre-se de substituir 'SUA_API_KEY' e 'SEU_CLIENT_ID' pelos valores reais da sua configuração no Google Cloud Console.


---

Este tutorial fornece uma explicação passo a passo para adicionar a Google API e autenticação via Google ao seu projeto. Adicione este tutorial no seu README para que outras pessoas saibam como utilizar a API no seu código!



# Link

https://teste-de-api-1kzk.onrender.com
