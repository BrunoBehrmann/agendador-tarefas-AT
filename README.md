# ⏱️ Agendador de Tarefas

> Microsserviço responsável pelas regras de agendamento, persistência de dados e execução temporizada de tarefas do ecossistema.

---

## 🎯 Sobre o Projeto

O **agendador-tarefas** é o componente de domínio focado na lógica principal de tarefas. Ele é acionado pela camada de BFF para criar, atualizar, listar e remover agendamentos. Além disso, conta com um componente de execução agendada (**Task Scheduling / Cron**) para processar tarefas pendentes de forma automática.

---

## 🏛️ Arquitetura do Ecossistema

O sistema completo é composto por 4 microsserviços independentes e containerizados com **Docker**:

1. **[bff-agendador-tarefas](https://github.com/BrunoBehrmann/bff-agendador-tarefas-AT)**: Gateway / BFF que recebe as chamadas externas e orquestra os fluxos.
2. **[agendador-tarefas](https://github.com/BrunoBehrmann/agendador-tarefas-AT)** *(Repositório Atual)*: Microsserviço responsável pelas regras de agendamento, persistência e execução temporizada (Cron/Task).
3. **[usuario](https://github.com/BrunoBehrmann/usuario-AT)**: Microsserviço de gestão, cadastro e validação dos dados de usuários.
4. **[notificacao](https://github.com/BrunoBehrmann/notificacao-AT)**: Microsserviço dedicado ao disparo automatizado de e-mails e alertas.

---

## 🛠️ Tecnologias e Dependências

* **Core & Framework:**
  * **Java 17+**
  * **Spring Boot**
  * **Spring Data JPA / Hibernate** (Persistência de tarefas)
  * **Spring Web** (Exposição das rotas REST)
  * **Spring Scheduling** (Execução de rotinas assíncronas e temporizadas via Cron)
* **Banco de Dados:**
  * **PostgreSQL** (Armazenamento das tarefas e seus status)
* **DevOps & Build:**
  * **Docker**
  * **Maven**

---

## 📌 Endpoints Internos

| Método | Endpoint | Descrição |
| :--- | :--- | :--- |
| `POST` | `/tarefas` | Cadastra uma nova tarefa no banco de dados |
| `GET` | `/tarefas` | Lista tarefas cadastradas |
| `GET` | `/tarefas/{id}` | Busca os detalhes de uma tarefa por ID |
| `DELETE` | `/tarefas/{id}` | Deleta uma tarefa |
