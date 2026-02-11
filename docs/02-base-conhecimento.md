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


---

## Adaptações nos Dados

Todos os dados utilizados no agente foram criados manualmente como dados fictícios (mockados), com o objetivo de simular um ambiente realista de planejamento financeiro pessoal.

As bases foram estruturadas de forma modular, separando:

- Dados do usuário (perfil, renda e gastos)
- Histórico financeiro mensal
- Regras financeiras e boas práticas
- Configuração de alertas
- Perfis comportamentais
- Respostas seguras (anti-alucinação)

Essa separação permite maior organização, escalabilidade e controle das informações utilizadas pelo agente.  
Os dados podem ser facilmente expandidos com novos usuários, novas categorias de gastos ou regras adicionais, sem necessidade de alterar a arquitetura principal do sistema.

---

## Estratégia de Integração

### Como os dados são carregados?

Os arquivos JSON são carregados no início da execução do agente e armazenados em memória para consulta durante a sessão.

Cada base possui uma função específica:
- `user_financial_data.json` → contexto principal do usuário
- `financial_rules.json` → regras fixas de orientação
- `monthly_history.json` → análise de tendência
- `safe_responses.json` → fallback seguro

Essa abordagem garante organização e evita que todas as informações sejam inseridas diretamente no prompt de uma só vez.

---

### Como os dados são usados no prompt?

Os dados são consultados dinamicamente de acordo com a solicitação do usuário.

- Informações estruturais e regras gerais são incluídas no *system prompt*, definindo o comportamento e as limitações do agente.
- Dados específicos do usuário (gastos, metas e histórico) são inseridos no contexto apenas quando necessários para gerar respostas personalizadas.
- As regras financeiras são utilizadas como base para validação das sugestões.
- Caso não haja dados suficientes, o agente utiliza respostas definidas em `safe_responses.json`.

Essa estratégia reduz risco de alucinação e mantém as respostas contextualizadas e coerentes.

---

## Exemplo de Contexto Montado

```text
Contexto do Usuário:

Perfil:
- Nome: Usuário Exemplo
- Idade: 24 anos
- Renda mensal: R$ 3.200
- Perfil comportamental: Equilibrado

Gastos Mensais:
- Moradia: R$ 1.200
- Alimentação: R$ 650
- Transporte: R$ 220
- Lazer: R$ 300
- Outros: R$ 180

Metas Financeiras:
- Reserva de emergência: R$ 1.500 de R$ 6.000
- Viagem: R$ 800 de R$ 4.000

Regras Aplicáveis:
- Gastos com lazer acima de 10% da renda mensal.
- Reserva de emergência abaixo do recomendado (3 a 6 meses de despesas).

Objetivo da Resposta:
Gerar sugestões personalizadas para ajuste de gastos e aceleração das metas financeiras, mantendo tom acessível e consultivo.
```

