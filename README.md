# 📱 CRUD React Native com Firebase Realtime Database & Auth

Projeto desenvolvido para a disciplina de **Programação Web III (PWIII)**. A aplicação é um sistema de gerenciamento de contatos (CRUD) completo com suporte a autenticação de usuários, construído em **React Native / Expo** e integrando os serviços de **Authentication** e **Realtime Database** do **Firebase**.

---

## 🚀 Tecnologias Utilizadas

- **[React Native](https://reactnative.dev/)** `v0.81.5` - Framework para desenvolvimento mobile multiplataforma (Android, iOS e Web).
- **[Expo](https://expo.dev/)** `v54.0.36` - Plataforma e ecossistema de desenvolvimento React Native.
- **[React Navigation](https://reactnavigation.org/)** `v7` - Gerenciamento de navegação em pilha (`createNativeStackNavigator`).
- **[Firebase](https://firebase.google.com/)** `v12.19.0` - Backend-as-a-Service (BaaS) fornecendo:
  - **Firebase Authentication**: Login e Cadastro de Usuários.
  - **Firebase Realtime Database**: Armazenamento e sincronização em tempo real do CRUD de contatos.

---

## 🗂️ Arquitetura do Projeto

```text
teste/
├── .claude/                # Configurações do ambiente de desenvolvimento
├── assets/                 # Ícones, splash screens e recursos visuais
├── screens/                # Telas da aplicação
│   ├── Tela1.js            # Tela de Autenticação (Login)
│   ├── Cadastro.js         # Tela de Registro de Novos Usuários
│   └── Tela2.js            # Tela Principal (CRUD de Contatos)
├── App.js                  # Configuração das rotas e navegação principal
├── firebaseConfig.js       # Inicialização das instâncias do Firebase (Auth & Database)
├── index.js                # Registro do componente raiz do Expo
├── app.json                # Configurações globais do Expo
└── package.json            # Dependências e scripts do projeto
```

---

## 🔑 Funcionalidades

### 1. 🛡️ Autenticação de Usuários
- **Tela de Login (`Tela1.js`)**:
  - Entrada via E-mail e Senha.
  - Validação de campos em tempo real.
  - Tratamento de exceções específicas do Firebase (ex: `auth/invalid-credential`, `auth/user-not-found`, `auth/network-request-failed`).
  - Indicadores de carregamento (`ActivityIndicator`).
- **Tela de Cadastro (`Cadastro.js`)**:
  - Criação de novas contas utilizando `createUserWithEmailAndPassword`.
  - Validação de senha mínima (6+ caracteres).
  - Feedback visual claro de sucesso/erro e redirecionamento automático para a tela de Login.

### 2. 📋 Gerenciamento de Contatos (CRUD - `Tela2.js`)
- **Criar (Create)**: Adiciona novos contatos (`nome`, `email`, `telefone`) ao nó `/contatos` do Realtime Database com identificadores únicos via `push` e `set`.
- **Ler (Read)**: Sincronização em tempo real utilizando o ouvinte `onValue`. Qualquer alteração no banco reflete na interface instantaneamente.
- **Atualizar (Update)**: Permite selecionar um contato existente da lista, preencher os formulários automaticamente para edição e salvar as alterações com a função `update`.
- **Excluir (Delete)**: Remove o contato selecionado no Firebase Realtime Database através da função `remove`.
- **Logout**: Encerramento da sessão do usuário via `signOut(auth)` com redirecionamento para a tela inicial.

---

## 🛠️ Como Executar o Projeto

### Pré-requisitos
- **Node.js** (versão 18 ou superior instalada)
- **npm** ou **yarn**
- Aplicativo **Expo Go** no celular (opcional para testes mobile) ou um emulador Android/iOS.

### Passos

1. **Clonar o repositório:**
   ```bash
   git clone https://github.com/ronaldoldiniz/crud_react_firebase.git
   cd crud_react_firebase
   ```

2. **Instalar as dependências:**
   ```bash
   npm install
   ```

3. **Iniciar a aplicação via Expo:**
   ```bash
   npm start
   ```
   ou para a versão Web:
   ```bash
   npm run web
   ```

4. **Testar a aplicação:**
   - Escaneie o QR Code gerado pelo Expo CLI no seu aplicativo **Expo Go**.
   - Ou pressione `w` no terminal para rodar diretamente no navegador web.

---

## ⚙️ Configuração do Firebase (`firebaseConfig.js`)

A aplicação consome os seguintes serviços do Firebase configurados no arquivo `firebaseConfig.js`:

- **Authentication**: Provedor de E-mail/Senha habilitado no Console do Firebase.
- **Realtime Database**: Regras de leitura e escrita configuradas na URL do banco:
  `https://testpwiii-default-rtdb.firebaseio.com`

---

## 📄 Licença

Este projeto foi desenvolvido para fins acadêmicos na disciplina de PWIII.
