
# Chatbot Institucional com IA para Acesso a Informações Oficiais do IFBA

![Status do Projeto](https://img.shields.io/badge/Status-MVP-success)
![Technology](https://img.shields.io/badge/Architecture-RAG-blue)
![Platform](https://img.shields.io/badge/Orchestration-n8n-red)

Este projeto apresenta um assistente virtual inteligente desenvolvido para otimizar a busca e a interpretação de documentos normativos (editais, portarias e regimentos) do **Instituto Federal da Bahia (IFBA)**. Através da arquitetura **Retrieval-Augmented Generation (RAG)**, o sistema mitiga barreiras de usabilidade do portal institucional, transformando documentos estáticos em uma interface de diálogo dinâmico.

## 🚀 Funcionalidades Principais

* **Busca Semântica:** Supera a busca por palavras-chave tradicionais ao interpretar a intenção real do usuário através de vetores matemáticos.
* **Citação de Fontes (Princípio da Auditabilidade):** Garante a rastreabilidade em 100% das interações técnicas, citando o item exato da norma consultada.
* **Gestão de Retificações:** Utiliza uma camada de reordenamento (Reranker) para garantir que retificações e documentos mais atuais prevaleçam sobre informações obsoletas.
* **Arquitetura de Microagentes:** Distribuição de carga entre agentes especializados (Analisador de Intenção, Auditor de Relevância, Especialista em Respostas) para reduzir alucinações e custos.

## 🛠️ Stack Tecnológico

A solução foi desenhada com foco em soberania tecnológica e baixo custo operacional:

* **Orquestração:** [n8n](https://n8n.io/) (Self-hosted/Fair-Code).
* **LLMs (Modelos de Linguagem):** OpenAI GPT-5-Nano (síntese final) e GPT-4o-mini (processamento e filtragem).
* **Banco de Dados Vetorial:** [Supabase](https://supabase.com/) com a extensão `pgvector`.
* **Embeddings:** `text-embedding-3-small` (vetores de 1536 dimensões).
* **Processamento de Dados:** Node.js/JavaScript para sanitização de caracteres e fragmentação semântica estruturada em Markdown.

## 🏗️ Arquitetura do Sistema

O projeto é estruturado em dois eixos operacionais principais:

1. **Pipeline de Preparação de Documentos (Ingestão):** Monitoramento em tempo real do Google Drive, extração de conteúdo bruto de PDFs, limpeza de ruídos administrativos via Regex e conversão para Markdown para preservação da hierarquia lógica.
2. **Pipeline de Resposta Contextual:** Sistema de roteamento de intenção com janela de contexto de 15 interações, busca vetorial por similaridade de cosseno e consolidação de fontes relevantes.

## 📊 Indicadores de Desempenho

Os resultados obtidos durante os protocolos de validação com discentes e servidores demonstraram a eficácia do MVP:

| Indicador | Resultado |
| :--- | :--- |
| **Assertividade (Golden Dataset)** | 94,60%  |
| **Sucesso em Consultas de Usuários Reais** | 71,43%  |
| **Citação de Fontes em Consultas Técnicas** | 100%  |
| **Média de Facilidade de Uso (Escala 1-5)** | 4.0  |
| **Ausência de Contradições Lógicas** | 77,78%  |

## 📂 Estrutura do Repositório

* `/workflows`: Templates JSON para importação no n8n (Pipeline de Chat e Ingestão).
* `/scripts`: Códigos JavaScript para tratamento de caracteres nulos e normalização de texto.
* `/prompts`: Prompts de sistema utilizados para configurar a persona e as regras de cada microagente.

---

**Trabalho de Conclusão de Curso**
Licenciatura em Computação - Instituto Federal da Bahia (IFBA), Campus Porto Seguro.

**Autor:** Pedro Henrique Almeida Bomfim.
**Orientador:** Prof. Dr. Diêgo Braga Monteiro de Moura.
