# Base de Conhecimento

## Dados Utilizados

Descreva se usou os arquivos da pasta `data`, por exemplo:


| Arquivo                         | Formato | Utilização no Agente |
|----------------------------------|---------|----------------------|
| `user_financial_data.json`       | JSON    | Armazena perfil do usuário, renda mensal, gastos por categoria, limites definidos e metas financeiras |
| `monthly_history.json`           | JSON    | Analisa o histórico financeiro mensal para identificar tendências, variações de gastos e padrões sazonais |
| `financial_rules.json`           | JSON    | Define regras financeiras e boas práticas utilizadas para orientar respostas e evitar alucinações |
| `goals_progress.json`            | JSON    | Acompanha o progresso das metas financeiras e permite sugestões proativas de ajuste |
| `alerts_config.json`             | JSON    | Padroniza alertas automáticos sobre excesso de gastos e risco no cumprimento de metas |
| `user_behavior_profiles.json`    | JSON    | Classifica o perfil comportamental do usuário para personalizar sugestões e tom de comunicação |
| `safe_responses.json`            | JSON    | Contém respostas seguras utilizadas quando há falta de dados, incerteza ou limitação do sistema |

> [!TIP]
> **Quer um dataset mais robusto?** Você pode utilizar datasets públicos do [Hugging Face](https://huggingface.co/datasets) relacionados a finanças, desde que sejam adequados ao contexto do desafio.

---

## Adaptações nos Dados

> Você modificou ou expandiu os dados mockados? Descreva aqui.

[Sua descrição aqui]

---

## Estratégia de Integração

### Como os dados são carregados?
> Descreva como seu agente acessa a base de conhecimento.

[ex: Os JSON/CSV são carregados no início da sessão e incluídos no contexto do prompt]

### Como os dados são usados no prompt?
> Os dados vão no system prompt? São consultados dinamicamente?

[Sua descrição aqui]

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
