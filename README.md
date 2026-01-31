# 💰 Sistema de Gestão Financeira Multimodal com IA (n8n + Gemini)

Este projeto consiste em um ecossistema de automação financeira ponta a ponta, capaz de processar transações a partir de **texto, áudio e imagem** via WhatsApp. Através da orquestração no n8n e do uso de modelos de visão e linguagem (LLMs), o bot transforma mensagens não estruturadas em registros organizados em um banco de dados relacional.

---

## 🚀 Funcionalidades Principal

- **Processamento Multimodal**: Captura de dados financeiros via mensagens de texto, notas de voz e fotos de comprovantes.
- **OCR com IA**: Utiliza Visão Computacional para extrair valor, estabelecimento e data de cupons fiscais ou recibos.
- **Transcrição de Áudio**: Processa áudios e identifica intenções de gastos através de Processamento de Linguagem Natural (NLP).
- **Agente de Intenção**: Classifica se o usuário deseja registrar um novo gasto ou consultar o histórico/resumo financeiro.
- **Validação de Dados**: Camada lógica em JavaScript para filtrar imagens inválidas (como fotos aleatórias) e garantir a integridade do banco de dados.

---

## 🛠️ Stack Tecnológica

| Componente | Tecnologia |
| :--- | :--- |
| **Orquestrador** | n8n (Self-hosted na AWS EC2) |
| **Interface de Chat** | WhatsApp (via WAHA API) |
| **Inteligência Artificial**| Google Gemini (Multimodal) |
| **Banco de Dados** | PostgreSQL |
| **Buffer/Cache** | Redis |
| **Linguagem de Script** | JavaScript (Node.js) |

---

## 📐 Arquitetura do Workflow

O fluxo segue uma arquitetura modular para garantir escalabilidade:

1. **Ingestão**: Webhook recebe o evento do WAHA e filtra o ID do WhatsApp.
2. **Triagem de Mídia**: Um nó condicional direciona o fluxo conforme o tipo de mensagem (`text`, `image` ou `audio`).
3. **Buffer (Redis)**: Mensagens de texto são acumuladas para evitar processamentos fragmentados.
4. **Extração e Formatação**: A IA processa a entrada e retorna um JSON estruturado. Um nó **Code** valida se os campos obrigatórios estão presentes.
5. **Persistência**: Os dados validados são inseridos via Query SQL no PostgreSQL.
6. **Resposta ao Usuário**: Notificação de sucesso ou erro enviada via WhatsApp.

---

## 🔧 Como Executar o Projeto

1. **Infraestrutura**: Configure uma instância AWS EC2 (Ubuntu).
2. **Docker**: Suba os containers do n8n, Redis e WAHA.
3. **Variáveis de Ambiente**:
   - Configure a `WEBHOOK_URL` para o IP público da sua instância.
   - Configure as credenciais do Google Gemini API.
4. **Importação**: Importe o JSON do workflow para o seu n8n.
5. **Webhook**: Aponte o Webhook do WAHA para o nó inicial do n8n.

---

