# 💰 Sistema de Gestão Financeira Multimodal com IA (n8n + Gemini)

> ⚠️ **Nota de Demonstração**: Este projeto foi desenvolvido exclusivamente como uma prova de conceito (PoC) técnica para um processo seletivo. O sistema está hospedado em uma infraestrutura privada na **AWS** e não está aberto para uso público.

---

## 📸 Arquitetura do Workflow

Abaixo, a visualização completa do fluxo orquestrado no n8n. O sistema utiliza uma lógica de ramificação para tratar texto, áudio e imagem de forma independente, garantindo que cada tipo de dado receba o processamento de IA adequado.

![Fluxo de Automação n8n](/img/fluxo-agente-n8n.png)

---

## 🚀 Diferenciais da Implementação

Para este projeto, foquei em pilares de robustez e escalabilidade:

- **Infraestrutura Cloud**: Hospedagem self-hosted em instância **AWS EC2** com ambiente isolado via **Docker**.
- **Tratamento Multimodal**: Integração com **Google Gemini** para OCR de alta precisão em imagens e transcrição inteligente de áudios financeiros.
- **Camada de Validação**: Implementação de lógica em **JavaScript** para saneamento de dados, evitando a inserção de registros inválidos ou "sujos" no banco de dados.
- **Resiliência de API**: Configuração avançada do **WAHA** para gestão de sessões e tratamento de identificadores de usuário (LIDs).

---

## 🛠️ Tecnologias Utilizadas

- **n8n**: Orquestração de workflow.
- **AWS (EC2)**: Servidor de aplicação.
- **WAHA**: Interface de comunicação WhatsApp.
- **PostgreSQL**: Persistência de dados.
- **Redis**: Gestão de estados e buffers de mensagens.