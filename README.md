# GK Events – Automação de Inscrição em Evento (Cypress + BDD)

Projeto de automação E2E com **Cypress 13** e **BDD (Cucumber/Gherkin)** cobrindo o fluxo de **inscrição em evento** no GK Events.



##  Pré-requisitos
- Node.js 18+
- npm 9+
- Uma instância do **GK Events** em execução (local ou homolog) com ao menos:
  - Um usuário: `aluno@teste.com` / `senha123` (ajuste se necessário)
  - Um evento **ativo**: `Workshop React`
  - Um evento **encerrado**: `Maratona Laravel (Encerrado)`

##  Configuração
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

##  Como executar
- **Modo interativo (GUI):**
  ```bash
  npm run cy:open
  ```
- **Modo headless (CI/CD):**
  ```bash
  npm run cy:run
  ```

##  Estrutura
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


##  CENARIO BDD
```gherkin
Feature: Inscrição em Evento

  Scenario: Exibir detalhes de um evento ativo
    Given estou na página inicial pública
    When abro os detalhes do evento "Workshop React"
    Then devo ver as informações do evento
    And devo ver a opção "Inscrever-se"

  Scenario: Solicitar login ao tentar inscrever-se sem autenticação
    Given estou na página inicial pública
    When tento me inscrever no evento "Workshop React" sem estar logado
    Then devo ser redirecionado para a tela de login

  Scenario: Inscrição bem-sucedida
    Given estou autenticado como "aluno@teste.com" com a senha "senha123"
    And estou nos detalhes do evento "Workshop React"
    When confirmo a inscrição
    Then devo ver a mensagem "Inscrição realizada com sucesso"
    And o status do evento deve aparecer como "Inscrito"

  Scenario: Cancelar inscrição
    Given estou autenticado como "aluno@teste.com" com a senha "senha123"
    And já estou inscrito no evento "Workshop React"
    When cancelo minha inscrição
    Then devo ver a mensagem "Inscrição cancelada"
    And devo ver novamente a opção "Inscrever-se"

  Scenario: Impedir inscrição em evento encerrado
    Given estou na página inicial pública
    When abro os detalhes do evento "Maratona Laravel (Encerrado)"
    Then devo ver o status "Encerrado"
    And não devo ver a opção "Inscrever-se"


Cenários BDD


- Exibir detalhes de um evento ativo
- Solicitar login ao tentar inscrever-se sem estar autenticado
- Inscrição bem-sucedida (usuário autenticado)
- Cancelar inscrição
- Impedir inscrição em evento encerrado
