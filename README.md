 GK Events – Automação de Inscrição em Evento (Cypress + BDD)

Projeto de automação cobrindo o fluxo de (inscrição em evento) no sistema GK Events

---

- Cenários BDD

- Inscrição em Evento
  /Exibir detalhes de um evento ativo
  - Dado que estou na página inicial pública
  - Quando eu abro os detalhes do evento "Workshop React"
  - Então devo ver informações do evento
  - E devo ver a ação "Inscrever-se"

  /Solicitar login ao tentar inscrever-se sem autenticação
  - Dado que estou na página inicial pública
  - Quando eu tento me inscrever no evento "Workshop React" sem estar logado
  - Então devo ser redirecionado para a tela de login

  /Inscrição bem-sucedida (usuário autenticado)
  - Dado que estou autenticado como "aluno@teste.com" com a senha "senha123"
  - E estou nos detalhes do evento "Workshop React"
  - Quando eu confirmo a inscrição
  - Então devo ver a mensagem "Inscrição realizada com sucesso"
  - E o status do evento para mim deve ser "Inscrito"

  /Cancelar inscrição
  - Dado que estou autenticado como "aluno@teste.com" com a senha "senha123"
  - E estou inscrito no evento "Workshop React"
  - Quando eu cancelo minha inscrição
  - Então devo ver a mensagem "Inscrição cancelada"
  - E a ação "Inscrever-se" deve ficar disponível novamente

  /Impedir inscrição em evento encerrado
  - Quando eu abro os detalhes do evento "Maratona Laravel (Encerrado)"
  - Então devo ver o status "Encerrado"
  - E não devo ver a ação "Inscrever-se"

---

- Como rodar localmente
  Clone este repositório:
   bash
   git clone <github.com/GesielNascimento/Automacao-inscricao-cypress>.git
   cd gkevents-cypress-bdd-inscricao
