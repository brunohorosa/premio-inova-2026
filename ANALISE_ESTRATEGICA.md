# Análise Estratégica das Propostas, 9º Prêmio Inova MG

## Visão geral

Duas propostas, duas categorias, sem competir entre si (item 3.2.2 do edital permite). A relação entre elas precisa ser de **complementaridade clara**, não de sobreposição.

- **Rota B** = o que já existe e funciona (Iniciativa Implementada + Destaque IA)
- **Rota A** = a visão de escala estadual (Ideia Inovadora Implementável)

---

## Diagnóstico honesto de cada rota

### Rota B, força máxima

A Rota B é a aposta mais forte de premiação. Tem tudo que o avaliador procura em "Iniciativa Implementada":

- Implementada e em produção (cota, remanejamento, descentralização, minutas de decreto)
- Resultado mensurado e irrefutável: 28 segundos vs 13min53seg (Python vs Power Automate), na mesma máquina, mesmo sistema
- Validação externa real: PCMG como piloto
- Demanda espontânea: 8 órgãos já solicitaram após a divulgação
- Diferencial técnico claro: scripting de protocolo vs RPA visual
- Governança madura: Git, logs, .env, mensagens traduzidas, arquivamento

**Conclusão:** a Rota B ganha por mérito próprio. É a prioridade.

### Rota A, potencial alto, mas com risco de enquadramento

A Rota A tem alcance estadual genuíno (SIAFI + SIAD + SISAP = todos os órgãos), mas corre três riscos:

1. **Risco "ferramenta para técnico":** se posicionada como "biblioteca que o órgão programa", pressupõe que o órgão tenha alguém que saiba Python. Isso encolhe o alcance real e enfraquece o critério de valor público (peso 3).

2. **Risco "infraestrutura, não serviço":** o prêmio valoriza valor sentido pelo cidadão. Uma camada técnica precisa traduzir esse valor de forma concreta.

3. **Risco "versão sem provas da B":** lado a lado com a B, a A pode parecer a mesma coisa sem números.

---

## O reposicionamento da Rota A

A correção central é deslocar o enquadramento:

| De (enquadramento arriscado) | Para (enquadramento vencedor) |
|---|---|
| "Biblioteca que o órgão pega e programa" | "Plataforma de automação que o Estado oferece aos órgãos" |
| Porta de entrada = programar fluxo próprio | Porta de entrada = adotar fluxos prontos e crescentes |
| Beneficia o servidor técnico | Beneficia o cidadão via liberação de servidores para o que importa |
| SIAFI já provado, SIAD/SISAP no futuro | A mesma chave abre as três portas do Estado inteiro |

### A grande narrativa da Rota A

> "O Estado de Minas inteiro funciona sobre três sistemas no terminal PRODEMGE: SIAFI (o dinheiro), SIAD (as compras) e SISAP (as pessoas). Toda secretaria, de saúde a segurança, depende deles. Hoje, milhares de servidores gastam horas digitando manualmente nesses sistemas, tempo que poderia estar sendo usado para atender o cidadão. A ideia é transformar a biblioteca já comprovada no SIAFI em uma plataforma institucional que automatiza os três sistemas, devolvendo esse tempo ao serviço público. Cada hora que um servidor da saúde não gasta digitando é uma hora a mais para cuidar de gente."

### Por que isso conecta com o cidadão

A chave é o **encadeamento de valor**:

automação → servidor liberado de tarefa operacional → mais tempo para atividade-fim → cidadão melhor atendido

Exemplos por área (ilustrativos, mostram o alcance):
- **Saúde:** equipe de orçamento da SES automatiza descentralização e dedica tempo à execução de recursos para hospitais
- **Educação:** equipe de compras da SEE automatiza no SIAD e acelera aquisição de material escolar
- **Segurança:** RH automatiza movimentações no SISAP e agiliza a vida funcional dos militares

---

## Como manter as duas rotas distintas (proteção ao item 3.2.3)

| Aspecto | Rota B | Rota A |
|---|---|---|
| Categoria | Iniciativa Implementada + Destaque IA | Ideia Inovadora Implementável |
| Objeto | A biblioteca de fluxos do SIAFI já em produção | A plataforma institucional estadual para os 3 sistemas |
| Sistema | SIAFI (em produção) | SIAFI + SIAD + SISAP (visão integrada) |
| Prova | Números, PCMG, 8 órgãos | A biblioteca do SIAFI como prova de que o conceito funciona |
| Foco | "Funciona, está rodando, tem resultado" | "Pode transformar o Estado inteiro" |

**Resposta pronta se a equipe técnica perguntar:** "A Rota B é a iniciativa setorial que já existe e roda no SIAFI. A Rota A é a ideia de transformar esse padrão comprovado em uma plataforma institucional que cobre os três sistemas estruturantes do Estado, disponível a todos os órgãos."

---

## Melhorias propostas para a Rota A

1. **Reabrir o resumo** com a narrativa "três sistemas, Estado inteiro, cidadão no fim da linha"
2. **Reforçar valor ao cidadão** com o encadeamento e exemplos por área (saúde, educação, segurança)
3. **Reposicionar a adoção:** fluxos prontos como porta de entrada, fluxo próprio como estágio avançado
4. **Resolver a contradição da descentralização:** ela é prova de conceito (já roda no SIAFI), não o objeto futuro. O objeto futuro é SIAD + SISAP + institucionalização
5. **Honestidade sobre a divulgação:** a matéria da Agência Minas falou da versão Power Automate; a solução evoluiu para Python, que a substituiu
6. **Demanda real como tração:** os 8 órgãos provam que existe apetite institucional pela automação, fortalecendo viabilidade
7. **Ajustar o RUNBOOK / execução local:** remover a ideia de "central única"; o modelo é cada órgão autônomo com a biblioteca, suas credenciais e seus controles

---

## Melhorias propostas para a Rota B

1. **Incluir a descentralização como terceiro fluxo implementado**, com PCMG e os 8 órgãos
2. **Substituir os números placeholder pelos dados reais** dos testes (28seg vs 13min53seg vs 1h17min manual)
3. **Honestidade sobre a divulgação Power Automate → Python** (mesma observação da Rota A)
4. **Destacar o comparativo de 3 cenários** como prova de qualidade técnica no Destaque IA

---

## Prioridade de esforço

1. Rota B com números reais e descentralização = aposta principal de premiação
2. Rota A reposicionada = aposta de visão, cobre categoria diferente, alcance estadual
3. Ambas honestas quanto à evolução Power Automate → Python
