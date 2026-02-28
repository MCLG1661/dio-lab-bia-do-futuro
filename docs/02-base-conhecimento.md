# Base de Conhecimento

## Dados Utilizados

Descreva se usou os arquivos da pasta `data`, por exemplo:

| Arquivo | Formato | Utilização no Agente |
|---------|---------|---------------------|
| `historico_atendimento.csv` | CSV | Contextualizar interações anteriores |
| `perfil_investidor.json` | JSON | Personalizar recomendações |
| `produtos_financeiros.json` | JSON | Sugerir produtos adequados ao perfil |
| `transacoes.csv` | CSV | Analisar padrão de gastos do cliente |

> [!TIP]
> **Quer um dataset mais robusto?** Você pode utilizar datasets públicos do [Hugging Face](https://huggingface.co/datasets) relacionados a finanças, desde que sejam adequados ao contexto do desafio.

---

## Adaptações nos Dados

Você modificou ou expandiu os dados mockados ? 

A Base de Dados não foi modificada e nem expandida.

---

## Estratégia de Integração

### Como os dados são carregados?
> Descreva como seu agente acessa a base de conhecimento.

 Existem duas possibilidades, injetar os dados diretamente no prompt (Ctrl + C, Crtl + V) ou carregar via código, como no exemlo abaixo.

```python
import pandas as pd
import json

# CSVs
historico = pd.read_csv('data/historico_atendimento.csv')
transacoes = pd.read_csv('data/transacoes.csv')

# JSONs
with open('data/perfil_investidor.json', 'r', encoding='utf-8') as f:
   perfil = json.load(f)

with open('data/produtos_finaceiros.json', 'r', encoding='utf-8') as f:
   produtos = json.load(f) 
```

### Como os dados são usados no prompt?
> Os dados vão no system prompt ? São consultados dinamicamente ?

```text
Dados do Cliente e Perfil (data/perfil_investidor.json) :
{
  "nome": "João Silva",
  "idade": 32,
  "profissao": "Analista de Sistemas",
  "renda_mensal": 5000.00,
  "perfil_investidor": "moderado",
  "objetivo_principal": "Construir reserva de emergência",
  "patrimonio_total": 15000.00,
  "reserva_emergencia_atual": 10000.00,
  "aceita_risco": false,
  "metas": [
    {
      "meta": "Completar reserva de emergência",
      "valor_necessario": 15000.00,
      "prazo": "2026-06"
    },
    {
      "meta": "Entrada do apartamento",
      "valor_necessario": 50000.00,
      "prazo": "2027-12"
    }
  ]
}

Transacoes do Cliente (data/transacoes.csv) :
data	descricao	categoria	valor	tipo
2025-10-01	Salário	receita	5000.00	entrada
2025-10-02	Aluguel	moradia	1200.00	saida
2025-10-03	Supermercado	alimentacao	450.00	saida
2025-10-05	Netflix	lazer	55.90	saida
2025-10-07	Farmácia	saude	89.00	saida
2025-10-10	Restaurante	alimentacao	120.00	saida
2025-10-12	Uber	transporte	45.00	saida
2025-10-15	Conta de Luz	moradia	180.00	saida
2025-10-20	Academia	saude	99.00	saida
2025-10-25	Combustível	transporte	250.00	saida

Historico de Atendimento do Cliente (data/historico_atendimento.csv) :
data	canal	tema	resumo	resolvido
2025-09-15	chat	CDB	Cliente perguntou sobre rentabilidade e prazos	sim
2025-09-22	telefone	Problema no app	Erro ao visualizar extrato foi corrigido	sim
2025-10-01	chat	Tesouro Selic	Cliente pediu explicação sobre o funcionamento do Tesouro Direto	sim
2025-10-12	chat	Metas financeiras	Cliente acompanhou o progresso da reserva de emergência	sim
2025-10-25	email	Atualização cadastral	Cliente atualizou e-mail e telefone	sim

Produtos Disponiveis (data/produtos_financeiros.json) :


```
---

## Exemplo de Contexto Montado

> Mostre um exemplo de como os dados são formatados para o agente.

```
Dados do Cliente:
- Nome: João Silva
- Perfil: Moderado
- Saldo disponível: R$ 5.000

Últimas transações:
- 01/11: Supermercado - R$ 450
- 03/11: Streaming - R$ 55
...
```
