# 💰 Agente Financeiro Inteligente com IA Generativa

## 📝Contexto

Os assistentes virtuais nesse setor, estão evoluindo de simples chatbots reativos para **agentes inteligentes e proativos**. Neste desafio, idealizar e prototipar um agente financeiro que utiliza IA Generativa para :

- **Antecipar necessidades** ao invés de apenas responder perguntas
- **Personalizar** sugestões com base no contexto de cada cliente
- **Cocriar soluções** financeiras de forma consultiva
- **Garantir segurança** e confiabilidade nas respostas (anti-alucinação)

> [!TIP]
> Na pasta [`examples/`](./examples/) você encontra referências de implementação para cada etapa deste desafio.

---

## 🎯 O Que Deve Ser Entregue

### 1. 🗂️ Documentação do Agente

**O Que** o agente faz e **Como** ele funciona :

- **Caso de Uso:** Qual problema financeiro ele resolve? (ex: consultoria de investimentos, planejamento de metas, alertas de gastos)
- **Persona e Tom de Voz:** Como o agente se comporta e se comunica?
- **Arquitetura:** Fluxo de dados e integração com a base de conhecimento
- **Segurança:** Como evitar alucinações e garantir respostas confiáveis?

📄 **Template:** [`docs/01-documentacao-agente.md`](./docs/01-documentacao-agente.md)

---

### 2. 📚 Base de Conhecimento

| Arquivo | Formato | Para que serve no Edu ? |
|---------|---------|-----------|
| `transacoes.csv` | CSV | Analisar o histórico de transações e usar essas informações de forma a alertar ou orientar o cliente |
| `historico_atendimento.csv` | CSV | Histórico de atendimentos anteriores, ou seja, dar continuidade ao atendimento de forma mais eficiente  |
| `perfil_investidor.json` | JSON | Personalizar as recomendações e explicações sobre as dúvidas e as necessidades de aprendizado do cliente |
| `produtos_financeiros.json` | JSON | Conhecer os produtos e serviços disponíveis para que eles possam ser explicados e recomendados ao cliente |

---

### 3. 💬 Prompts do Agente

Os prompts que definem o comportamento do agente :

- **System Prompt:** Instruções gerais de comportamento e restrições

Você é o Edu, um consultor e educador financeiro amigável e didático

Objetivo :
Ensinar e aconselhar conceitos de finanças pessoais de forma simples, usando os dados como exemplos práticos.

Regras :

- NUNCA recomende investimentos específicos - Apenas explique como funcionam
- Use os dados fornecidos para dar exemplospersonalizados
- Linguagem simples, como se explicasse para um amigo
- Se não souber algo, admita ; "Não tenho essa informação, mas posso explicar..."
- Sempre pergunte se o cliente entendeu
...
> [!TIP]
> Use a técnica de _Few-Shot Prompting_, ou seja, dê exemplos de perguntas e respostas ideais em suas regras. Quanto mais claro você for nas instruções, menos o seu agente vai alucinar.
     
- **Exemplos de Interação:** Cenários de uso com entrada e saída esperada
- **Tratamento de Edge Cases:** Como o agente lida com situações limite

📄 **Template:** [`docs/03-prompts.md`](./docs/03-prompts.md)

---

### 4. ⚙️ Aplicação Funcional

**Protótipo Funcional** do agente :

- Chatbot interativo (sugestão: Streamlit, Gradio ou similar)
- Integração com LLM (via API ou modelo local)
- Conexão com a base de conhecimento

📁 **Pasta:** [`src/`](./src/)

---

### 5. 🧮 Avaliação e Métricas

Como é avaliada a qualidade do agente :

**Métricas Sugeridas:**
- Precisão/assertividade das respostas
- Taxa de respostas seguras (sem alucinações)
- Coerência com o perfil do cliente

📄 **Template:** [`docs/04-metricas.md`](./docs/04-metricas.md)

---

### 6. 🎤 Pitch

Grave um **pitch de 3 minutos** (estilo elevador) apresentando :

- Qual problema seu agente resolve ?
- Como ele funciona na prática ?
- Por que essa solução é inovadora ?

📄 **Template:** [`docs/05-pitch.md`](./docs/05-pitch.md)

---

## 🛠️ Ferramentas Sugeridas

Todas as ferramentas abaixo possuem versões gratuitas:

| Categoria | Ferramentas |
|-----------|-------------|
| **LLMs** | [ChatGPT](https://chat.openai.com/), [Copilot](https://copilot.microsoft.com/), [Gemini](https://gemini.google.com/), [Claude](https://claude.ai/), [Ollama](https://ollama.ai/) |
| **Desenvolvimento** | [Streamlit](https://streamlit.io/), [Gradio](https://www.gradio.app/), [Google Colab](https://colab.research.google.com/) |
| **Orquestração** | [LangChain](https://www.langchain.com/), [LangFlow](https://www.langflow.org/), [CrewAI](https://www.crewai.com/) |
| **Diagramas** | [Mermaid](https://mermaid.js.org/), [Draw.io](https://app.diagrams.net/), [Excalidraw](https://excalidraw.com/) |

---

## 🏗️ Estrutura do Repositório

```
📁 lab-agente-financeiro/
│
├── 📄 README.md
│
├── 📁 data/                          # Dados mockados para o agente
│   ├── historico_atendimento.csv     # Histórico de atendimentos (CSV)
│   ├── perfil_investidor.json        # Perfil do cliente (JSON)
│   ├── produtos_financeiros.json     # Produtos disponíveis (JSON)
│   └── transacoes.csv                # Histórico de transações (CSV)
│
├── 📁 docs/                          # Documentação do projeto
│   ├── 01-documentacao-agente.md     # Caso de uso e arquitetura
│   ├── 02-base-conhecimento.md       # Estratégia de dados
│   ├── 03-prompts.md                 # Engenharia de prompts
│   ├── 04-metricas.md                # Avaliação e métricas
│   └── 05-pitch.md                   # Roteiro do pitch
│
├── 📁 src/                           # Código da aplicação
│   └── app.py                        # (exemplo de estrutura)
│
├── 📁 assets/                        # Imagens e diagramas
│   └── ...
│
└── 📁 examples/                      # Referências e exemplos
    └── README.md
```

---

## ✨ Dicas Finais

1. **Comece pelo prompt:** Um bom system prompt é a base de um agente eficaz
2. **Use os dados mockados:** Eles garantem consistência e evitam problemas com dados sensíveis
3. **Foque na segurança:** No setor financeiro, evitar alucinações é crítico
4. **Teste cenários reais:** Simule perguntas que um cliente faria de verdade
5. **Seja direto no pitch:** 3 minutos passam rápido, vá ao ponto

## 🙏 Agradecimentos
- DIO
- Bradesco
- Bootcamp GenAI - Módulo : Desafio Final - Prof : Venilton Falvo Jr.

## Autor
- Marcus Guedes
- Linkedin : https://www.linkedin.com/in/marcusguedes/
- GitHub : https://github.com/MCLG1661 
