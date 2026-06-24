# FORMULÁRIO DE INSCRIÇÃO — ROTA A
## Categoria: Ideias Inovadoras Implementáveis
### 9º Prêmio Inova Minas Gerais — Edital SEPLAG/SCPRH nº 01/2026

> **Como usar este arquivo:** cada campo está rotulado com o limite exato de caracteres. Copie o texto abaixo do rótulo e cole diretamente no formulário. Todos os textos foram verificados dentro dos limites.

---

## TELA 1 — Dados Básicos

### Categoria
```
Ideias Inovadoras Implementáveis
```

### Temática
```
Tecnologia e Inovação / Gestão Pública e Simplificação Administrativa
```
*(selecionar a opção mais adequada disponível no formulário)*

### Título `[máx 50 caracteres — atual: 46]`
```
Automação Python dos Sistemas TN3270 do Estado
```

### Instituição responsável
```
SEPLAG — Secretaria de Estado de Planejamento e Gestão
```

### Resumo `[600 a 1.000 caracteres — atual: 981]`
```
Os três sistemas estruturantes do Estado de Minas Gerais — SIAFI, SIAD e SISAP — são acessados pelo terminal TN3270 da PRODEMGE. Praticamente todos os órgãos dependem deles, e a quase totalidade dos servidores os opera de forma manual, digitando tela a tela. Uma parcela menor já utiliza automação via RPA visual.

A ideia é apresentar e institucionalizar uma abordagem alternativa de automação: uma biblioteca Python de código aberto que interage com esses sistemas via protocolo TN3270 nativo, sem simulação visual. Com ela, equipes técnicas dos órgãos podem construir automações para qualquer tarefa nesses sistemas, do empenho ao remanejamento, da compra à movimentação de pessoal.

A abordagem já foi usada pela própria equipe proponente para automatizar processos reais da SPLOR/SEPLAG no SIAFI: em menos de um mês, foram gerados 109 documentos e processados cerca de R$ 1,72 bilhão, com zero erros. A ideia é tornar essa tecnologia conhecida e disponível para todo o Estado.
```

---

## TELA 2 — Quadro de Estruturação
> Cada item tem **máximo 60 caracteres**. Adicione os itens um por linha no formulário.

### Desafios ou oportunidades
```
SIAFI, SIAD e SISAP usados manualmente pela maioria
Operação manual: lenta, exposta a erro e sem registro
Sistemas legados TN3270 têm particularidades técnicas
Servidores gastam tempo em tarefas mecânicas repetitivas
Automação desses sistemas exige abordagem especializada
```

### Público-alvo
```
Qualquer órgão que opere SIAFI, SIAD ou SISAP
Servidores que desenvolvem ou mantêm automações
```

### Ideia ou Iniciativa
```
Biblioteca Python para automação via protocolo TN3270
Cada órgão constrói os fluxos para suas próprias tarefas
Código aberto, auditável, sem custo de licença
Roda em background; computador livre durante execução
Versionamento Git; credenciais seguras em arquivo .env
```

### Valor gerado
```
Servidores liberados de digitação repetitiva e manual
Zero custo de licença de ferramenta de automação
Log automático de cada operação realizada
Execução sem bloqueio do computador do servidor
Código auditável: total transparência sobre o que faz
```

### Riscos e incertezas
```
Requer equipe técnica com conhecimento em Python
Cada fluxo deve ser construído individualmente
Ambiente de execução: Linux ou Windows com WSL
Curva de aprendizado para quem vem do RPA visual
```

### Recursos necessários e análise financeira
```
Python, py3270, x3270/s3270, Git: todos gratuitos
Linux moderno ou Windows com WSL (recurso nativo)
Equipe técnica: ao menos 1 servidor com Python básico
Sem custo de licença, sem hardware dedicado
Roda em hardware antigo sem suporte ao Windows 10
```

### Parcerias
```
PRODEMGE: estabilidade e disponibilidade do TN3270
Órgãos com equipe técnica para adoção e disseminação
Automatiza.MG: abordagem complementar ao programa
```

### Detalhamento da solução, aprimoramento e multiplicação
```
Disponibilizar biblioteca e documentação para os órgãos
Guia de primeiros passos em linguagem acessível
Capacitação de equipes técnicas interessadas
Repositório público no GitHub para contribuições
Crescimento por adoção e compartilhamento entre órgãos
```

---

## TELA 3 — Detalhamento da Ideia/Iniciativa

### Desafio ou oportunidade `[600 a 2.500 caracteres — atual: 1.147]`
```
Os três sistemas estruturantes do Estado de Minas Gerais — SIAFI (execução orçamentária e financeira), SIAD (compras, contratos e patrimônio) e SISAP (administração de pessoal) — funcionam sobre o terminal TN3270 da PRODEMGE. Não há secretaria que escape deles: saúde, educação, segurança pública, fazenda, todas dependem desses sistemas no dia a dia.

A realidade operacional é que a quase totalidade dos servidores acessa esses sistemas de forma manual, digitando tela a tela informações que muitas vezes já existem prontas em planilhas. São tarefas repetitivas, lentas e expostas a erros de digitação — risco especialmente grave quando se opera sobre valores financeiros ou registros funcionais. Uma parcela menor de servidores já utiliza automação via RPA visual.

O desafio específico desses sistemas é que eles são legados, acessados pelo protocolo TN3270 do mainframe. Isso cria uma barreira técnica para automação: as ferramentas de automação mais conhecidas e disponíveis não foram projetadas especificamente para esse ambiente, e aplicá-las ao terminal exige conhecimento especializado que hoje não está amplamente disponível nos órgãos.
```

### Ideia/iniciativa `[600 a 2.500 caracteres — atual: 1.372]`
```
A proposta é apresentar e institucionalizar uma abordagem de automação desenvolvida especificamente para o terminal TN3270: uma biblioteca Python de código aberto que interage com os sistemas SIAFI, SIAD e SISAP pelo protocolo nativo do mainframe.

Com ela, qualquer equipe técnica de um órgão estadual pode construir automações para as tarefas que realiza nesses sistemas. Não há um catálogo de fluxos prontos a distribuir: o valor da ferramenta é que ela resolve o problema de acesso ao protocolo, e cada equipe escreve o fluxo que precisa para o seu contexto específico — do empenho ao remanejamento, da consulta de saldo à movimentação de pessoal.

No núcleo técnico, a biblioteca py3270 conecta o Python ao emulador x3270/s3270, que por sua vez fala com o terminal pelo protocolo TN3270 nativo. Em termos práticos, a automação identifica campos por coordenadas reais de linha e coluna, lê e escreve dados, envia comandos do sistema (Enter, F3, F5) e captura em texto o retorno exato do mainframe. O resultado é uma automação que entende o sistema pela sua linguagem nativa, não por uma foto da tela.

A institucionalização proposta envolve: disponibilizar a biblioteca com documentação acessível, criar um guia de primeiros passos para equipes sem experiência prévia com TN3270, e manter um repositório público onde os órgãos possam compartilhar fluxos desenvolvidos.
```

### Estudos preliminares (opcional) `[máx 1.000 caracteres — atual: 614]`
```
A viabilidade técnica já foi demonstrada na prática. A equipe proponente desenvolveu e usa em produção, no SIAFI/MG, automações construídas com esta mesma biblioteca: aprovação e anulação de cotas orçamentárias, remanejamento de crédito e descentralização para Unidades Executoras.

Em menos de um mês de operação (19/05 a 16/06/2026), o fluxo de remanejamento gerou 109 documentos no SIAFI, processou 257 alterações orçamentárias e alocou cerca de R$ 1,72 bilhão em recursos, atendendo 29 unidades orçamentárias, com zero erros de lançamento. A ferramenta não é conceitual: ela opera em ambiente real de produção.
```

### Grau de novidade `[máx 1.000 caracteres — atual: 856]`
```
A inovação está em trazer para o setor público estadual uma abordagem de automação que existe há décadas em instituições internacionais que operam mainframes, mas que permanece desconhecida e indisponível para a maioria dos órgãos do Estado.

O x3270/s3270 é mantido pela comunidade há mais de duas décadas e amplamente usado em contextos corporativos que operam sistemas legados TN3270 em escala. O que se propõe é tornar essa tecnologia acessível ao servidor público estadual, com documentação em português, guias de primeiros passos e suporte inicial — removendo a barreira de entrada que hoje impede sua adoção.

Institucionalmente, a novidade é que o Estado passa a ter, documentada e disponível, uma alternativa de automação para seus sistemas mais críticos, desenvolvida internamente, de código aberto, sem custo de licença e de propriedade pública.
```

### Valor gerado `[600 a 2.500 caracteres — atual: 1.159]`
```
O valor direto é a capacidade que o órgão ganha: qualquer equipe técnica passa a ter uma ferramenta para automatizar tarefas nos sistemas que toda a Administração já usa. Processos que hoje consomem horas de digitação manual podem ser executados em segundos, com registro automático de cada operação.

As automações desenvolvidas pela equipe proponente no SIAFI ilustram o potencial: um lote de 50 operações que consumia cerca de uma hora e dezessete minutos de digitação passou a ser concluído em 28 segundos, com zero erros. Os fluxos de remanejamento processaram R$ 1,72 bilhão em menos de um mês, com log completo de cada lançamento.

Além do ganho em velocidade e precisão, a ferramenta tem características que agregam valor ao órgão: roda em segundo plano, sem bloquear o computador do servidor durante a execução; não tem custo de licença; produz log estruturado e auditável de cada operação; e o código é inteiramente aberto e inspecionável. O servidor que antes passava horas digitando pode dedicar esse tempo à análise, ao controle e às atividades que exigem inteligência humana — o que beneficia, em última instância, o cidadão atendido pelo órgão.
```

### Público-alvo `[máx 1.000 caracteres — atual: 598]`
```
O público-alvo imediato são as equipes técnicas dos órgãos estaduais — servidores com perfil de TI, analistas de sistemas ou profissionais com conhecimento em Python — que queiram construir automações para as tarefas que seus órgãos realizam no SIAFI, SIAD ou SISAP.

Como esses três sistemas estão presentes em todas as Secretarias, autarquias e fundações do Executivo Estadual, o alcance potencial é amplo. O benefício final se estende a todos os servidores que, com automações construídas pelas equipes técnicas, ficam liberados de tarefas repetitivas para se dedicar ao trabalho de maior valor.
```

### Riscos e incertezas `[600 a 2.500 caracteres — atual: 1.032]`
```
O principal desafio é a exigência de capacidade técnica para uso da ferramenta. Diferentemente de soluções de interface gráfica, a construção de automações com esta biblioteca requer conhecimento em Python e familiaridade com o conceito de protocolo de terminal. Cada fluxo precisa ser desenvolvido individualmente para cada tarefa. Esse é um requisito real, não minimizável: a ferramenta é para equipes técnicas, não para o servidor geral.

A mitigação está na documentação acessível e no guia de primeiros passos que a proposta inclui — reduzir a barreira de entrada é parte central da ideia. Mas o limite permanece: sem ao menos um servidor com perfil técnico no órgão, a adoção não acontece.

O ambiente de execução requer Linux ou Windows com WSL (Windows Subsystem for Linux), recurso nativo das versões atuais do Windows, mas que pode demandar configuração inicial por perfil técnico. A PRODEMGE pode ter políticas de rede que precisem de validação prévia para garantir que a conexão TN3270 funcione a partir do ambiente WSL.
```

### Estratégia de aprimoramento e multiplicação `[600 a 2.500 caracteres — atual: 878]`
```
A ferramenta é multiplicável por design: é software livre, os repositórios são públicos no GitHub (organização splor-mg), e o stack é 100% gratuito, sem custo que cresça com o número de usuários ou órgãos.

O modelo de multiplicação é orgânico: cada órgão que adota e desenvolve fluxos pode contribuir com eles ao repositório compartilhado. Um fluxo construído para uma tarefa do SIAD, por exemplo, pode ser reaproveitado por outro órgão que realiza a mesma operação. Quanto mais órgãos adotam, mais fluxos ficam disponíveis para todos — o valor da ferramenta cresce com a comunidade de uso.

A replicabilidade também alcança outros entes: municípios e estados que operam terminais TN3270 — situação ainda comum no setor público brasileiro — podem usar a mesma biblioteca sem adaptação. A iniciativa de Minas Gerais pode servir de referência para outras administrações públicas.
```

### Recursos necessários `[máx 2.000 caracteres — atual: 768]`
```
Em software, todo o stack é gratuito: Python (linguagem), py3270 (interface Python para o terminal), x3270/s3270 (emulador TN3270 headless) e Git (controle de versão). Nenhuma licença, nenhum custo recorrente de ferramenta.

Em hardware, a ferramenta roda em qualquer computador com Linux ou Windows com WSL. Não há exigência de servidor dedicado, edição corporativa do sistema operacional ou requisito especial de CPU. Uma vantagem relevante no contexto estadual: por rodar em qualquer Linux moderno, a ferramenta pode ser instalada em hardware antigo que não atende os requisitos mínimos do Windows 10. Uma máquina dessa geração — que de outra forma ficaria ociosa ou seria descartada — pode ser reformatada com uma distribuição Linux leve e transformada em nó de automação dedicado, sem custo de hardware adicional.

Em pessoas, a adoção requer ao menos um servidor com conhecimento básico de Python por órgão, para construir e manter os fluxos. Para a fase de institucionalização — documentação, guia e disseminação — a equipe proponente da SPLOR/SEPLAG pode conduzir com sua própria equipe.
```

### Custos de implantação/manutenção `[máx 1.000 caracteres — atual: 509]`
```
O custo da ferramenta em si é zero: todo o stack tecnológico é gratuito e de código aberto. O custo de implantação se concentra no tempo de desenvolvimento de cada fluxo de automação, que varia conforme a complexidade da tarefa a automatizar. Fluxos mais simples podem ser construídos em dias; fluxos complexos podem demandar semanas.

A manutenção é de baixo custo: fluxos existentes raramente precisam de atualização (o protocolo TN3270 é estável), e quando precisam, a intervenção é cirúrgica e localizada.
```

### Recursos orçamentários e financeiros `[máx 1.000 caracteres — atual: 352]`
```
Não há necessidade de dotação orçamentária específica para a ferramenta — todo o software é gratuito. O único custo é o tempo de pessoal já alocado na SPLOR/SEPLAG para a elaboração da documentação, do guia de primeiros passos e do suporte inicial aos órgãos interessados. A disseminação pode ser conduzida dentro das atividades regulares da diretoria.
```

### Parcerias `[600 a 2.500 caracteres — atual: 830]`
```
A PRODEMGE é parceira essencial para garantir que a conexão TN3270 funcione a partir dos ambientes dos órgãos (Linux/WSL) e para esclarecer eventuais políticas de rede que possam afetar a comunicação com o terminal. A relação já existe — a SPLOR opera o terminal PRODEMGE no dia a dia — e não exige novos acessos ou configurações no mainframe.

Os órgãos que já possuem equipes técnicas com perfil para desenvolvimento em Python são os parceiros naturais de expansão: cada fluxo que desenvolvem pode ser contribuído ao repositório compartilhado, ampliando o valor disponível para todos.

O programa Automatiza.MG é parceiro estratégico: a presente proposta endereça um nicho complementar ao do programa, e sua estrutura de disseminação pode ajudar a alcançar órgãos interessados em automação que ainda não conhecem esta abordagem.
```

### Detalhamento da solução `[300 a 1.000 caracteres — atual: 605]`
```
A solução tem três componentes. A biblioteca técnica é formada por py3270 e x3270/s3270, que juntos estabelecem a comunicação com o terminal TN3270 via protocolo nativo: a automação lê e escreve em coordenadas reais de linha e coluna, envia comandos do mainframe e captura o retorno do sistema em texto. A documentação e o guia são o componente de acesso — materiais em português que reduzem a barreira de entrada para equipes sem experiência prévia. O repositório público no GitHub é o componente de comunidade — onde o código vive, versões são controladas e fluxos podem ser compartilhados entre órgãos.
```

---

## TELA 5 — Cronograma

| Etapa | Início | Término | Status | Entrega |
|---|---|---|---|---|
| Desenvolvimento e validação da biblioteca | mai/2024 | jun/2026 | Concluído | Biblioteca em produção na SPLOR |
| Documentação técnica e guia de primeiros passos | jul/2026 | set/2026 | Planejado | Documentação publicada no GitHub |
| Capacitação inicial dos órgãos interessados | out/2026 | dez/2026 | Planejado | Primeiros órgãos adotando |
| Expansão e comunidade de contribuidores | jan/2027 | dez/2027 | Planejado | Catálogo crescente de fluxos |

### Outras observações (Tela 5) `[máx 2.000 caracteres]`
```
A biblioteca já está desenvolvida e em operação real desde maio de 2024 na SPLOR/SEPLAG. O que esta proposta adiciona é a institucionalização: tornar a ferramenta conhecida, documentada e acessível a qualquer órgão do Estado que queira adotá-la. O cronograma acima reflete essa fase de disseminação, que pode ocorrer em paralelo ao uso contínuo da ferramenta pela equipe proponente.
```

---

## TELA 6 — Arquivos Complementares

> Até 3 arquivos PDF, máx 10 MB cada, sem espaço no nome. **Não se identificar nos arquivos.**

Sugestões de arquivos a preparar:
- `resultados_producao.pdf` — dados de produção da SPLOR (109 docs, 257 linhas, R$ 1,72 bi) como prova de que a ferramenta funciona em escala real
- `arquitetura_tecnica.pdf` — diagrama da arquitetura Python/py3270/TN3270 + exemplos de código comentados
- `depoimento_pcmg.pdf` — manifestação formal da PCMG sobre o uso da automação (já autorizada via Marcela)

---

## TELA 7 — Pesquisa de satisfação
*(não conta para avaliação — responder conforme experiência da equipe)*

---

*Arquivo gerado com base nos documentos do projeto. Todos os textos foram verificados nos limites de caracteres estabelecidos pelo MAPA_FORMULARIO.md.*
