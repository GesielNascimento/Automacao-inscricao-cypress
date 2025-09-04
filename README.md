# GK Events – Automação de Inscrição em Evento (Cypress + BDD)

Projeto de automação E2E com **Cypress 13** e **BDD (Cucumber/Gherkin)** cobrindo o fluxo de **inscrição em evento** no GK Events.

## ✅ Cenários BDD
Arquivo: `cypress/e2e/features/inscricao.feature`

- Exibir detalhes de um evento ativo
- Solicitar login ao tentar inscrever-se sem estar autenticado
- Inscrição bem-sucedida (usuário autenticado)
- Cancelar inscrição
- Impedir inscrição em evento encerrado

## 🧱 Pré-requisitos
- Node.js 18+
- npm 9+
- Uma instância do **GK Events** em execução (local ou homolog) com ao menos:
  - Um usuário: `aluno@teste.com` / `senha123` (ajuste se necessário)
  - Um evento **ativo**: `Workshop React`
  - Um evento **encerrado**: `Maratona Laravel (Encerrado)`

## ⚙️ Configuração
1. Clone e instale as dependências:
   ```bash
   git clone <seu-repo>.git
   cd gkevents-cypress-bdd-inscricao
   npm install
   ```
2. Ajuste a **URL base** no `cypress.config.js`:
   ```js
   baseUrl: "http://localhost:8000" // troque para a URL do seu GK Events
   ```
3. Se necessário, ajuste seletores/mensagens em:
   - `cypress/pages/*.js` (Page Objects)
   - `cypress/e2e/features/inscricao.feature` (textos esperados)

## ▶️ Como executar
- **Modo interativo (GUI):**
  ```bash
  npm run cy:open
  ```
- **Modo headless (CI/CD):**
  ```bash
  npm run cy:run
  ```

## 🗂️ Estrutura
```
cypress/
  e2e/
    features/inscricao.feature   # cenários BDD
    steps/inscricao.steps.js     # step definitions
  pages/
    HomePage.js
    LoginPage.js
    EventDetailsPage.js
  support/
    commands.js
    e2e.js
cypress.config.js
package.json
```

## 💡 Dicas
- Prefira IDs estáveis nos elementos do GK Events (ex.: `data-testid="btn-inscrever"`).
- Se usar modais de confirmação, veja `confirmEnrollIfModal()` em `EventDetailsPage.js`.
- Para ambiente seed, crie usuários e eventos fixos para evitar flutuação dos testes.

---

Feito com ❤️ para seu portfólio de **QA Júnior**.