# 🍔 Delivery Assistant with AWS Step Functions & Amazon Bedrock

Projeto desenvolvido durante o bootcamp **AWS - Agentes de IA em Campo**, da DIO, com foco na construção de um assistente inteligente utilizando **Amazon Bedrock** e **AWS Step Functions**.

O objetivo deste projeto é demonstrar como criar um fluxo de execução serverless capaz de encadear múltiplos prompts (Prompt Chaining), preservando o contexto da conversa e permitindo que cada resposta sirva de entrada para a próxima interação com o modelo de linguagem.

---

## 📖 Sobre o projeto

O fluxo recebe uma lista de prompts e os executa sequencialmente através do Amazon Bedrock.

A cada execução:

- o próximo prompt é recuperado;
- o histórico da conversa é mantido;
- a resposta do modelo é adicionada ao contexto;
- o processo continua até que todos os prompts sejam processados.

Essa abordagem é conhecida como **Prompt Chaining**, uma técnica bastante utilizada para construir aplicações de IA Generativa mais robustas e capazes de executar tarefas complexas em etapas.

---

## 🏗️ Arquitetura

```
Entrada (JSON)
        │
        ▼
AWS Step Functions
        │
        ▼
Initialize
        │
        ▼
Choice State
        │
        ▼
Amazon Bedrock
        │
        ▼
Resposta do Modelo
        │
        ▼
Atualiza histórico
        │
        ▼
Próximo Prompt
        │
        ▼
Resultado Final
```

---

## 🛠️ Tecnologias utilizadas

- Amazon Bedrock
- AWS Step Functions
- Amazon Nova Lite
- JSON
- JSONata
- AWS IAM

---

## 📥 Entrada esperada

```json
{
  "prompts": [
    "Estou programando um jantar romântico. Nesse jantar, irei pedir um macarrão. Me dê uma lista de três itens que combinam em uma experiência gastronômica.",
    "Liste duas bebidas que acompanham um jantar romântico.",
    "Liste um lugar perfeito para jantar romântico em Paris."
  ]
}
```

---

## ⚙️ Funcionamento

O workflow realiza as seguintes etapas:

1. Inicializa as variáveis do fluxo.
2. Conta quantos prompts serão executados.
3. Inverte a lista para facilitar o processamento.
4. Invoca o Amazon Bedrock.
5. Armazena a resposta no histórico.
6. Atualiza o contador.
7. Repete o processo até consumir todos os prompts.
8. Retorna toda a conversa consolidada.

---

## 💡 Conceitos aplicados

- Serverless
- Workflow Orchestration
- Prompt Chaining
- Generative AI
- Context Management
- Amazon Bedrock Runtime
- State Machines
- JSONata Expressions

---

## 📸 Demonstração

> Capturas de tela da execução no AWS Step Functions.

<img width="1976" height="796" alt="image" src="https://github.com/user-attachments/assets/cfd13fa5-5fb7-4664-88b6-d5b67deaa735" />

---

## ▶️ Como executar

### Pré-requisitos

- Conta AWS
- Amazon Bedrock habilitado
- Permissões IAM para:
  - Amazon Bedrock
  - AWS Step Functions
- Modelo habilitado no Bedrock

### Passos

1. Criar uma State Machine no AWS Step Functions.
2. Importar o arquivo `state-machine.json`.
3. Configurar um modelo disponível no Amazon Bedrock.
4. Executar utilizando um JSON contendo a lista de prompts.

---

## ⚠️ Observações

Este projeto foi desenvolvido para fins de estudo.

Dependendo da região da AWS e da disponibilidade dos modelos, pode ser necessário alterar o `ModelId` utilizado na State Machine.

Também é possível que contas novas possuam limitações de uso do Amazon Bedrock (quotas e limites de tokens).

---

## 📚 Aprendizados

Durante este projeto foi possível praticar:

- criação de máquinas de estado no AWS Step Functions;
- integração direta com o Amazon Bedrock;
- utilização de JSONata para manipulação de dados;
- orquestração de fluxos serverless;
- engenharia de prompts (Prompt Chaining);
- gerenciamento de contexto em aplicações de IA Generativa.

---

## 🎓 Créditos

Projeto desenvolvido durante o bootcamp:

**AWS - Agentes de IA em Campo**

Plataforma: DIO

Projeto proposto:
**Criando um Assistente de Delivery com AWS Step Functions e Bedrock**. :contentReference[oaicite:1]{index=1}

---

## 👩‍💻 Autora

**Rafaella Massa**

- LinkedIn: https://www.linkedin.com/in/rafaella-massa/
- GitHub: https://github.com/rafaellamassa

---

## 📄 Licença

Este projeto foi desenvolvido exclusivamente para fins educacionais e de demonstração.
