# Prêmio Inova Minas Gerais 2026

Repositório de trabalho da equipe para organização e versionamento das propostas de inscrição no **9º Prêmio Inova Minas Gerais** (Edital SEPLAG/SCPRH Nº 01/2026).

**Equipe:**
- Guilherme de Melo Ferreira
- Bruno Henrique de Oliveira Rosa
- Gabriel Braico Dornas

---

## Por que existem duas propostas?

O edital permite que a mesma equipe inscreva mais de uma ideia ou iniciativa (item 3.2.2), desde que não seja o mesmo trabalho inscrito em mais de uma categoria (item 3.2.3).

Construímos duas propostas **intencionalmente distintas**, cada uma com objeto, categoria e enquadramento diferentes. Veja abaixo:

---

## Rota B — Iniciativas Implementadas de Sucesso + Destaque em Automatização e IA

**Arquivo:** `Rota_B_Iniciativas_e_Destaque.md`

**Categoria:** Iniciativas Implementadas de Sucesso

**O que é:** A biblioteca Python/py3270 já em produção na SPLOR/SEPLAG, que automatiza transações orçamentárias no SIAFI-MG via terminal TN3270. Aprovação e anulação de cotas, descentralização, remanejamento, realocação de créditos e geração de minutas de decreto já estão funcionando e validados, inclusive com testes na PCMG.

**Por que essa categoria:** A iniciativa já existe, já roda em produção e tem resultados mensuráveis. Isso a enquadra como iniciativa implementada, não como ideia.

**Bônus:** Por usar automação de processos via Python/py3270, concorre também ao **Destaque em Automatização e IA**, abrindo a possibilidade de premiação dupla.

**Premiação possível:**
- Até R$ 15.000 na categoria principal
- Até R$ 10.000 no Destaque em Automatização e IA

---

## Rota A — Ideias Inovadoras Implementáveis

**Arquivo:** `Rota_A_Ideias_Inovadoras.md`

**Categoria:** Ideias Inovadoras Implementáveis

**O que é:** A ideia de institucionalizar a biblioteca como uma **plataforma aberta para todos os órgãos do Poder Executivo Estadual**, acessível via API na rede do governo, sem necessidade de computador dedicado, sem licença, cobrindo SIAFI-MG, SIAD e SISAP. A prova de viabilidade técnica na SPLOR é citada como demonstração de que o conceito funciona, não como o objeto da inscrição.

**Por que essa categoria:** O que está em produção hoje é uma solução setorial da SPLOR. A generalização como plataforma institucional para todos os órgãos ainda não foi implementada em escala. É uma ideia com prova de conceito, não uma iniciativa concluída.

**Diferença clara entre as duas rotas:** A Rota B inscreve o que já existe e funciona. A Rota A inscreve a visão de escala do que isso pode se tornar para todo o Estado.

**Se a equipe técnica do prêmio perguntar:** *"Uma é a iniciativa setorial que já existe na SPLOR. A outra é a ideia de generalizá-la como plataforma institucional aberta a todos os órgãos."*

---

## Datas importantes

| Etapa | Data |
|---|---|
| Abertura das inscrições | 28/05/2026 às 9h |
| Encerramento das inscrições | 26/06/2026 às 18h |
| Resultado da 1ª Etapa | até 28/10/2026 |
| Resultado Final e Premiação | até 11/12/2026 |

**Site do prêmio:** www.premioinova.mg.gov.br

---


## Atenção ao formato da inscrição (verificar no site)

O edital (itens 2.3 e 2.4) define que a inscrição é feita exclusivamente no site www.premioinova.mg.gov.br, preenchendo três documentos: Formulário de Inscrição (da categoria), Termo de Responsabilidade e Termo de Compromisso.

Pontos confirmados:
- O edital NÃO especifica limite de caracteres, palavras, páginas ou formato de arquivo. Essas orientações só aparecem no próprio site.
- A inscrição não é um artigo livre, e sim um formulário com campos (provavelmente alinhados aos critérios de avaliação).

Ação necessária:
- [ ] Ao abrir o site (28/05) ou antes, verificar os campos exatos do formulário e se há limite de caracteres por campo.
- [ ] Se houver limite, condensar as seções dos documentos-mãe para caber. Se for campo livre, copiar e colar das seções (que já estão organizadas por critério).

Observação: os documentos Rota_A e Rota_B funcionam como documento-mãe (fonte de verdade). O conteúdo será transposto para o formulário do site no ato da inscrição.

---

## Pendências antes do envio

- [x] Levantar números reais dos logs do sistema Python (substituir placeholders na Rota B)
- [x] Realizar testes comparativos: manual vs Power Automate vs Python/py3270
- [ ] Alinhar com PCMG os dados de volume para os testes
- [ ] Confirmar usernames para a inscrição no gov.br
- [ ] Revisão final dos dois textos pela equipe
- [ ] **Ajuste de consistência Rota A:** o repositório `siafi-automacao-descentralizacao` (instalação via WSL local) traz no RUNBOOK a instrução "Não mexa no computador enquanto ele trabalha". Isso contradiz a narrativa da Rota A de "Plataforma Virtual TN3270" (sem computador dedicado, execução em infraestrutura de governo via API). Necessário: (1) corrigir/atualizar o RUNBOOK do robô, e (2) revisar a Rota A para garantir coerência entre o que está descrito como arquitetura da plataforma e o que está implementado e público no repositório de produção.

