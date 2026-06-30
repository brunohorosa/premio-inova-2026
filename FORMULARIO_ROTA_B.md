# FORMULÁRIO DE INSCRIÇÃO — ROTA B
## Categoria: Iniciativas Implementadas de Sucesso + Destaque em Automatização e IA
### 9º Prêmio Inova Minas Gerais — Edital SEPLAG/SCPRH nº 01/2026

> **Como usar este arquivo:** cada campo está rotulado com o limite exato de caracteres. Copie o texto abaixo do rótulo e cole diretamente no formulário. Todos os textos foram verificados dentro dos limites.
>
> **Atenção aos itens marcados `[VALIDAR]`** — dados públicos que devem ser conferidos antes de finalizar a inscrição (ver CHECKLIST_INSCRICAO.md).

---

## TELA 1 — Dados Básicos

### Categoria
```
Iniciativas Implementadas de Sucesso
```

### Temática
```
Tecnologia e Inovação / Gestão Pública e Simplificação Administrativa
```
*(selecionar a opção mais adequada disponível no formulário)*

### Usa automação/IA?
```
Sim
```

### Título `[máx 50 caracteres — atual: 49]`
```
Automação Python do Terminal PRODEMGE no SIAFI/MG
```

### Instituição responsável
```
SEPLAG — Secretaria de Estado de Planejamento e Gestão
```

### Resumo `[600 a 1.000 caracteres — atual: 979]`
```
Biblioteca Python para automação programática do terminal TN3270 da PRODEMGE, desenvolvida e implementada na SPLOR/SEPLAG e em produção com três fluxos aplicados ao SIAFI/MG: aprovação e anulação de cotas orçamentárias, remanejamento de crédito e descentralização de cotas para Unidades Executoras.

Em teste comparativo real, 50 operações que consumiam 1h17min de digitação manual foram concluídas em 28 segundos pela biblioteca — redução de 97%, com zero erro. Em menos de um mês (19/05 a 16/06/2026), o fluxo de remanejamento gerou 109 documentos SIAFI, processou 257 alterações orçamentárias e alocou ~R$ 1,72 bilhão, atendendo 29 unidades orçamentárias.

A Polícia Civil de MG validou a solução como órgão piloto externo. Doze órgãos manifestaram interesse formal em adotá-la. A iniciativa usa software livre, versionamento Git e log estruturado por operação — governança formal desde a base.
```

### Resumo para votação popular `[máx 486 caracteres — atual: 363]`
```
Imagine um servidor público que passa horas digitando no sistema financeiro do Estado dados que já estão em planilhas. A SEPLAG criou uma automação que faz esse trabalho em segundos: 50 operações que levavam 1h17min agora levam 28 segundos, sem erros. Já processou R$ 1,72 bilhão. Com isso, os servidores ficam livres para o que importa: atender melhor o cidadão.
```

---

## TELA 2 — Quadro de Estruturação
> Cada item tem **máximo 60 caracteres**. Adicione os itens um por linha no formulário.

### Desafios ou oportunidades
```
Digitação manual em sistemas legados: horas por lote
Erros de digitação em operações financeiras críticas
RPA visual é frágil e instável no terminal TN3270
Computador bloqueado durante execução do robô visual
Sem trilha de auditoria na operação manual
```

### Público-alvo
```
Equipe de orçamento da SPLOR/SEPLAG (uso imediato)
Equipes de orçamento de todos os órgãos (descentralização)
13 órgãos com interesse formal já manifestado
```

### Ideia ou Iniciativa
```
Biblioteca Python que opera o terminal via protocolo
3 fluxos em produção: cota, crédito, descentralização
Arquitetura modular e replicável com custo decrescente
Log automático, versionamento Git, credenciais seguras
```

### Valor gerado
```
28 seg vs 1h17min: redução de 97% no tempo
R$ 1,72 bi processados em menos de um mês
Zero erros de lançamento em produção real
Computador livre durante execução (sem bloqueio)
Auditoria automática de cada operação realizada
```

### Riscos e incertezas
```
Variabilidade técnica entre órgãos para adoção
Resistência cultural a processos manuais estabelecidos
```

### Recursos necessários e análise financeira
```
Software: Python, py3270, x3270, Git — tudo gratuito
Hardware: computador computador linux ou windowns com WSL
Pessoas: 1-2 técnicos para desenvolvimento/manutenção
Pessoas: servidores não técnicos dispostos a aprender
Sem custo de licença; sem servidor dedicado
```

### Parcerias
```
PCMG: órgão piloto — validação em produção real
13 órgãos: expansão e validação de novos fluxos
```

### Detalhamento da solução, aprimoramento e multiplicação
```
Atender os 13 órgãos com interesse já manifestado
Disseminação estadual como diretriz da SPLOR
Abrir catálogo para contribuições de outros órgãos
```

---

## TELA 3 — Detalhamento da Iniciativa

### Desafio ou oportunidade `[600 a 2.500 caracteres — atual: 1.156]`
```
A SPLOR/SEPLAG é responsável por operações mensais de alto volume no SIAFI/MG: aprovação e anulação de cotas orçamentárias e remanejamentos de crédito — operações centralizadas na própria diretoria. O processo de descentralização de cotas para Unidades Executoras, por sua vez, é realizado pelos departamentos de orçamento de cada órgão do Estado, que distribui às suas UEs as cotas já aprovadas. Cada operação, nas duas frentes, exige digitação manual tela a tela no terminal mainframe, sobre dados que já existem organizados em planilhas.

O processo é lento, tedioso e exposto a erros de digitação — risco grave porque opera sobre valores financeiros e gera documentos contábeis cuja correção exige procedimentos formais. Em meses de alta demanda, a digitação consome parcela desproporcional do tempo da equipe técnica, em detrimento das atividades de análise orçamentária que constituem o núcleo da função.

A ferramenta disponível no Estado, o Power Automate Desktop, apresenta limitação técnica relevante para esse contexto: opera o terminal por simulação visual (captura de imagem e clique em coordenadas de pixel), abordagem frágil para mainframe, sujeita a quebras por mudanças de resolução, posição da janela ou atualizações visuais, além de bloquear o computador para uso humano durante a execução da automação. A equipe identificou e desenvolveu uma solução tecnicamente superior para esse nicho específico.
```

### Ideia/iniciativa `[600 a 2.500 caracteres — atual: 1.248]`
```
A iniciativa consiste em uma biblioteca Python que dialoga com o terminal TN3270 da PRODEMGE via protocolo nativo, desenvolvida e implantada na SPLOR/SEPLAG com três fluxos completos em produção.

O núcleo técnico utiliza a biblioteca py3270 (interface Python para o emulador x3270/s3270), que opera o terminal por coordenadas lógicas (linha e coluna) em vez de simulação visual. A automação identifica campos, lê e escreve dados, envia comandos do mainframe (Enter, F3, F5, F8) e captura em texto o retorno exato do sistema — sem captura de imagem, sem OCR, sem clique por pixel.

Sobre esse núcleo, foram construídos três fluxos: aprovação e anulação de cota orçamentária, remanejamento de crédito e descentralização de cota para Unidades Executoras. Os três seguem arquitetura idêntica: leem planilha Excel padronizada, executam no SIAFI com as credenciais do operador e registram em log o retorno linha a linha.

A camada de governança cobre: versionamento integral em Git (organização splor-mg/GitHub), credenciais em arquivo .env fora do controle de versão, log estruturado com dados de entrada, operação e número do documento gerado, documentação técnica versionada e arquitetura modular com funções compartilhadas reutilizadas entre fluxos.
```

### Estudos preliminares (opcional) `[máx 1.000 caracteres — atual: 707]`
```
O desenvolvimento partiu de identificação prática de limitação técnica. A equipe tentou aplicar o Power Automate ao terminal pw3270 e documentou as quedas e instabilidades decorrentes da abordagem visual. A partir disso, pesquisou alternativas especializadas em protocolo TN3270 e identificou a biblioteca x3270/s3270, utilizada há décadas em instituições internacionais que operam mainframes em produção.

O teste comparativo estruturado realizado em 02/06/2026 (50 operações idênticas de remanejamento de crédito, mesma máquina, sistema em produção) quantificou a superioridade: 28 segundos (Python) contra 13 min 53 seg (Power Automate) e 1h17min (manual), com zero erros nos três cenários automatizados.
```

### Grau de novidade `[máx 1.000 caracteres — atual: 793]`
```
A inovação está em três frentes simultâneas. Tecnicamente, desloca a automação do RPA visual — paradigma de captura de tela e clique por pixel — para scripting de protocolo, eliminando estruturalmente as fragilidades do RPA aplicado a mainframes. Em modelo, substitui configuração proprietária por código aberto, versionado, auditável, que pertence ao Estado. Em postura institucional, demonstra que a Administração Pública é capaz de construir e manter sua própria camada de automação para sistemas estratégicos, sem custo de licença e sem dependência de fornecedor único.

A iniciativa complementa o Automatiza.MG: o programa cobre o ecossistema Microsoft moderno; esta solução cobre o nicho específico de sistemas legados TN3270, em que o RPA visual apresenta limitação técnica reconhecida.
```

### Valor gerado `[600 a 2.500 caracteres — atual: 1.170]`
```
O valor gerado é mensurável em várias dimensões. Em tempo: 50 operações que consumiam 1h17min de digitação manual passam a ser concluídas em 28 segundos — redução superior a 97%. Em erros: eliminação virtual de erros de digitação em operações financeiras, pois os dados são lidos da planilha revisada e digitados com precisão determinística. Em auditoria: cada operação gera registro automático com dados de entrada, retorno do sistema e número do documento — trilha que praticamente não existia na operação manual.

Em escala de produção, os números falam por si: somente no fluxo de remanejamento, em menos de um mês (19/05 a 16/06/2026), foram gerados 109 documentos SIAFI, processadas 257 alterações orçamentárias e alocados cerca de R$ 1,72 bilhão, atendendo 29 unidades orçamentárias — tudo sem erros.

O valor mais profundo é a elevação da natureza do trabalho: o servidor deixa a digitação repetitiva e passa a analisar, conferir e controlar. A PCMG relatou oficialmente que, com a automação, a equipe "passou a dedicar-se menos às rotinas de descentralizações" e mais ao "acompanhamento qualificado da execução dos contratos e despesas das unidades executoras".
```

### Resultados mensurados `[600 a 4.000 caracteres — atual: 2.149]`
```
Os resultados estão documentados em duas frentes complementares: teste comparativo controlado e dados de produção real.

TESTE COMPARATIVO (02/06/2026 — 50 operações de remanejamento de crédito, mesma máquina, sistema em produção):
• Manual: ~1h17min (medições por etapa: 39,7 seg por UO para liberação, 1min26,99 seg por linha de alteração, 17,62 seg por UO para finalização)
• Power Automate: 13 min 53 seg (horários registrados automaticamente pelo sistema)
• Python/py3270: 28 segundos
• Redução vs manual: 97%+ | vs Power Automate: ~30x mais rápido
• Erros: zero nos dois cenários automatizados; todos os 50 lançamentos retornaram "REGISTRO EFETUADO"
• Diferencial adicional: Python libera o computador durante a execução; Power Automate e manual exigem máquina dedicada

PRODUÇÃO REAL — Fluxo de remanejamento de crédito (19/05/2026 a 16/06/2026, menos de um mês):
• 109 documentos SIAFI gerados
• 257 linhas de alteração orçamentária processadas (145 suplementações + 112 anulações)
• ~R$ 1,72 bilhão suplementado (confirmado por dois caminhos independentes)
• 29 unidades orçamentárias atendidas
• Zero erros de lançamento

CASO DEMONSTRAÇÃO — Lote consolidado (257 linhas, 29 UOs):
• Manual: ~6,7 horas (~400 min)
• Power Automate: ~71 minutos
• Python: ~2,4 minutos

VALIDAÇÃO EXTERNA — PCMG (órgão piloto):
A Diretoria de Planejamento e Orçamento da PCMG avaliou formalmente a automação de descentralização de cotas em ambiente real de produção. Relatou que a equipe "passou a dedicar-se menos às rotinas de descentralizações" e mais ao "acompanhamento da execução dos contratos e despesas das unidades executoras, permitindo um controle mais próximo e qualificado dos recursos". Registrou também ganhos de agilidade, padronização e redução de falhas operacionais.

DEMANDA ESPONTÂNEA: Doze órgãos manifestaram interesse formal em adotar a automação de descentralização após divulgação institucional: PCMG (já implantado), PMMG, CBMMG, GMG, SEJUSP, FES, ARMBH, SECULT, SEINFRA, DER, Fapemig e SEPLAG (órgão proponente, opera internamente). A procura multissetorial e espontânea comprova que a demanda é real e transversal a todo o Estado.
```

### Público-alvo `[máx 1.000 caracteres — atual: 668]`
```
O público-alvo imediato são dois: a equipe da SPLOR/SEPLAG, que usa os fluxos de aprovação de cotas e remanejamento de crédito no dia a dia; e as equipes de orçamento de cada órgão do Estado, que realizam a descentralização de cotas para suas Unidades Executoras. O alcance potencial é estadual: qualquer servidor que opere SIAFI, SIAD ou SISAP — sistemas que atravessam todas as Secretarias, autarquias e fundações do Executivo — pode ser beneficiado pelos fluxos disponíveis e futuros.

A demanda concreta já aponta o alcance real: doze órgãos com interesse formal manifestado, com concentração expressiva na segurança pública (PCMG, PMMG, CBMMG, GMG, SEJUSP) e presença em saúde, desenvolvimento regional, cultura, infraestrutura e pesquisa científica. Em escala indireta, o alcance se estende a fornecedores, cidadãos e ao Estado como um todo.
```

### Riscos e incertezas `[600 a 2.500 caracteres — atual: 968]`
```
O principal risco operacional é a variabilidade de maturidade técnica entre órgãos. A mitigação está nos instaladores automatizados, na documentação em linguagem simples e no suporte da SPLOR como mantenedora. O fluxo de descentralização já adota esse modelo — instalação por script .bat, manual para uso sem suporte especializado.

Mudanças nas telas dos sistemas legados (SIAFI, SIAD, SISAP), apesar de incomum, podem exigir atualização dos fluxos. A mitigação está na arquitetura modular — cada fluxo é independente — e no versionamento em Git, que permite identificar desvios rapidamente. O protocolo TN3270 é estável há décadas, e as transações mapeadas mudam com baixíssima frequência.

Risco de resistência cultural existe em órgãos com processos manuais muito enraizados. A mitigação é a demonstração de resultado concreto desde o primeiro uso, como aconteceu com a PCMG: ver 50 operações concluídas em 28 segundos elimina a resistência mais rapidamente do que qualquer argumento.
```

### Estratégia de aprimoramento e multiplicação `[600 a 2.500 caracteres — atual: 841]`
```
A replicabilidade foi validada empiricamente: o segundo fluxo (remanejamento) foi construído a partir do primeiro (cota) com esforço significativamente menor, reutilizando as funções de login, navegação e finalização sem qualquer modificação.

Externamente, a multiplicação se viabiliza por três caminhos: repositórios públicos no GitHub (splor-mg), cloná­veis por qualquer órgão; ferramentas 100% gratuito sem custo de licença que cresça com o uso; e arquitetura modular que permite que cada órgão contribua com fluxos próprios ao catálogo compartilhado.

O alcance se estende além do Executivo estadual. Municípios mineiros e demais estados que operem terminais TN3270 podem adotar a solução sem adaptação institucional. A SPLOR conduz a disseminação como diretriz estratégica, com a equipe autora à frente, garantindo governança e continuidade.
```

### Recursos necessários `[máx 2.000 caracteres — atual: 796]`
```
Software: 100% gratuito — Python, py3270, x3270/s3270, Git. Sem licença, sem custo recorrente de ferramenta.

Hardware: qualquer computador com Linux ou Windows com WSL (recurso nativo). Sem servidor dedicado, sem edição corporativa do sistema operacional, sem requisito mínimo de CPU. Ponto relevante no contexto estadual: por rodar em qualquer Linux moderno, a solução pode ser instalada em hardware antigo que não suporta Windows 10 — uma máquina dessa geração pode ser reformatada com Linux e transformada em nó de automação dedicado, sem custo adicional de equipamento.

Pessoas: equipe técnica de 1 a 2 pessoas para desenvolvimento, manutenção e disseminação, modelo já validado na DCMEFO/SPLOR. O conhecimento de negócio dos processos orçamentários (Bruno Rosa e Guilherme Ferreira) e a assessoria de inteligência de dados (Gabriel Dornas) são recursos já existentes na equipe.
```

### Custos de implantação/manutenção `[máx 1.000 caracteres — atual: 411]`
```
Custo de implantação: essencialmente zero em software (todo gratuito). O investimento é de tempo da equipe para desenvolvimento de cada fluxo — estimado em semanas para fluxos novos, com redução progressiva pela reutilização da base.

Manutenção: baixo custo. Atualizações por mudanças nos sistemas legados são cirúrgicas e localizadas. Não há renovação de licença, não há custo de máquina dedicada por usuário.
```

### Recursos orçamentários e financeiros `[máx 1.000 caracteres — atual: 466]`
```
Não há dotação orçamentária específica necessária para as ferramentas tecnológicas — todo software é gratuito. O custo é integralmente de pessoal, já alocado e remunerado no quadro permanente da SEPLAG.

A economia potencial em relação a alternativas proprietárias é expressiva: sem licença de RPA comercial, sem máquinas dedicadas e sem dependência de fornecedor externo, o modelo de custo beneficia o Estado em escala proporcional ao número de órgãos que adotam a solução.
```

### Parcerias `[600 a 2.500 caracteres — atual: 1.003]`
```
A PRODEMGE é parceira essencial: garante estabilidade e disponibilidade do ambiente TN3270. A relação já existe — a SPLOR opera o terminal no dia a dia — e a plataforma não exige novos acessos ou configurações no mainframe.

A PCMG é a parceria mais concreta: primeiro órgão piloto, validou a automação de descentralização em produção real com suas próprias credenciais e com aval formal da Diretoria de Orçamento. O depoimento formal da PCMG é evidência da qualidade e do impacto real da solução.

Os doze órgãos com interesse formal (PMMG, CBMMG, GMG, SEJUSP, FES, ARMBH, SECULT, SEINFRA, DER, Fapemig e SEPLAG) são parceiros de expansão — cada um que adota contribui para validar novos contextos e, potencialmente, para ampliar o catálogo de fluxos disponíveis a todos.

O programa Automatiza.MG é parceiro estratégico de disseminação: a plataforma complementa o programa e pode aproveitar sua estrutura institucional para alcançar mais órgãos com menos esforço de divulgação.
```

### Detalhamento da solução `[300 a 1.000 caracteres — atual: 442]`
```
A solução opera em três camadas. O núcleo técnico é a biblioteca py3270/x3270 comunicando com o terminal TN3270 por protocolo nativo, lendo e escrevendo em coordenadas lógicas de linha e coluna. Sobre esse núcleo, fluxos específicos implementam cada transação de negócio, reutilizando funções compartilhadas de login, navegação e finalização. A camada de governança cobre versionamento Git, credenciais em .env e log estruturado por operação.
```

---

## TELA 4 — Detalhamento da Solução de Automatização/IA *(exclusiva desta rota)*
> Todos os campos: **600 a 4.000 caracteres**

### Relevância da solução e geração de valor `[atual: 1.936]`
```
A iniciativa resolve problema real e muito antigo, recorrente e de alta relevância institucional: a operação de sistemas legados TN3270 (SIAFI, SIAD, SISAP) consome horas de trabalho qualificado em digitação manual, todos os meses, em praticamente todos os órgãos do Estado. Não é dor de um único setor — é dor estrutural compartilhada por todo o Executivo estadual.

A relevância se comprova pela demanda espontânea: após a divulgação institucional da automação de descentralização de cotas, doze órgãos manifestaram interesse formal em adotá-la, com representação em segurança pública, saúde, desenvolvimento regional, cultura, infraestrutura e pesquisa. Órgãos tão distintos buscando a mesma solução demonstra que a demanda é transversal e real.

O valor gerado é direto e mensurável. Operações que consumiam 1h17min de trabalho humano passaram a ser concluídas em 28 segundos — redução de 97%. Em menos de um mês de operação do fluxo de remanejamento (19/05 a 16/06/2026), foram gerados 109 documentos SIAFI e alocados cerca de R$ 1,72 bilhão, atendendo 29 unidades orçamentárias, com zero erros. Esse resultado não é projeção: é dado de produção real, verificável.

O encadeamento de valor público é direto: a automação libera o servidor da tarefa operacional, que passa a analisar, controlar e planejar — atividades que beneficiam diretamente o cidadão. O órgão piloto (PCMG) relatou formalmente exatamente esse efeito: a equipe "passou a dedicar-se menos às rotinas de descentralizações" e mais ao "acompanhamento qualificado da execução dos contratos e despesas das unidades executoras". Em escala estadual, essa transformação do trabalho do servidor é, talvez, o maior valor público que a iniciativa pode gerar.

Por ser software livre, de custo praticamente nulo e arquitetura replicável, a relação custo-benefício é extraordinária: o impacto potencial em escala estadual não tem equivalente entre soluções proprietárias com o mesmo alcance.
```

### Qualidade técnica da solução (automação/IA) `[atual: 2.170]`
```
A qualidade técnica da solução é diferenciada e tecnicamente justificada para o contexto específico de sistemas mainframe.

A escolha central — scripting de protocolo TN3270 em vez de RPA visual — é a decisão técnica mais importante da iniciativa. Para sistemas com interface gráfica moderna, o RPA visual é geralmente adequado. Para sistemas mainframe acessados via TN3270, a interação por protocolo é estruturalmente mais robusta: opera por coordenadas lógicas (linha e coluna do terminal) imunes a alterações de resolução, posição da janela, atualizações do emulador ou mudanças visuais do sistema. Cada ponto de fragilidade do RPA visual em mainframe é eliminado por design.

As ferramentas aqui propostas são maduras e mundialmente validadas. O x3270/s3270 é mantido pela comunidade há mais de duas décadas e é amplamente usado em instituições internacionais que operam mainframes em produção. O py3270 é interface Python madura para essa base. A arquitetura modular adotada — separação clara entre núcleo de acesso, fluxos de cada transação e funções utilitárias compartilhadas — é boa prática de engenharia de software, raramente aplicada a automações de RPA.

Há ainda uma dimensão de qualidade com consequências operacionais diretas: o s3270 opera em modo texto sem interface gráfica, sem capturar mouse ou teclado. A automação roda em segundo plano enquanto o servidor continua trabalhando normalmente na mesma máquina. O Power Automate Desktop, ao contrário, captura fisicamente a tela do Windows, exigindo máquina dedicada ou interrompendo o uso pelo operador. Isso representa, em escala estadual, economia de centenas de estações dedicadas ou servidor público parado aguardando o robô trabalhar.

Essa característica abre ainda uma possibilidade que o RPA visual estruturalmente não permite: execução em servidor central headless, conectado à rede de governo, viabilizando orquestração corporativa sem multiplicar estações ou licenças.

A efetividade está comprovada em produção: três fluxos em operação real, 109 documentos SIAFI gerados, R$ 1,72 bilhão processado, zero erros de lançamento. A construção do segundo fluxo a partir do primeiro — com esforço significativamente menor — valida empiricamente a qualidade arquitetural.
```

### Resultado mensurável `[atual: 1.945]`
```
Os resultados se sustentam em duas frentes complementares, ambas verificáveis.

TESTE COMPARATIVO ESTRUTURADO (50 operações de remanejamento de crédito, mesma máquina, produção real):
- Manual: ~1h17min (baseado em medições por etapa: 39,7 seg/UO para liberação, 1min26,99 seg/linha, 17,62 seg/UO para finalização)
- Power Automate: 13min53seg (horários registrados automaticamente pelo sistema, testado em 29/05/2026)
- Python/py3270: 28 segundos (testado em 02/06/2026, log automático)
- Redução vs. manual: 97%+ | Vs. Power Automate: ~30x mais rápido
- Erros de lançamento: zero nos dois cenários automatizados
- Disponibilidade do computador: livre durante execução Python; dedicado nos outros dois cenários

CASO DEMONSTRAÇÃO — lote consolidado (257 linhas, 29 UOs):
- Manual: ~6,7 horas (~400 min)
- Power Automate: ~71 minutos
- Python: ~2,4 minutos
O que tomaria quase um dia inteiro é concluído em 2 minutos e meio, com o computador livre.

PRODUÇÃO REAL — Fluxo de remanejamento (19/05/2026 a 16/06/2026, menos de um mês):
- 109 documentos SIAFI gerados
- 257 linhas de alteração orçamentária (145 suplementações + 112 anulações)
- ~R$ 1,72 bilhão suplementado (confirmado por dois caminhos independentes)
- 29 unidades orçamentárias atendidas
- Zero erros de lançamento
Observação: este é apenas um dos fluxos em produção. Aprovação de cotas, descentralização e geração de minutas de decreto operam em adição.

VALIDAÇÃO EXTERNA — PCMG:
Testes da automação de descentralização realizados com credenciais reais da PCMG, com aval formal da Diretoria de Orçamento. A PCMG relatou formalmente que a equipe "passou a dedicar-se menos às rotinas de descentralizações" e mais ao "acompanhamento qualificado da execução dos contratos e despesas das unidades executoras". Ganhos adicionais relatados: agilidade, padronização, redução de falhas.

DEMANDA QUANTIFICADA: doze órgãos com interesse formal manifestado após divulgação institucional.
```

### Governança, ética e conformidade `[atual: 2.160]`
```
A iniciativa foi construída com atenção formal à governança, conformidade legal e ética operacional desde o início.

CONFORMIDADE COM A LGPD (Lei nº 13.709/2018):
A solução não coleta novos dados pessoais. Opera com as credenciais nominais já concedidas ao servidor para uso manual do terminal, preservando integralmente o modelo de controle de acesso existente. Os logs gerados ficam em ambiente controlado, sem exposição externa. Não há novo processamento de dados pessoais além do que já ocorria na operação manual.

TRATAMENTO SEGURO DE CREDENCIAIS:
Credenciais de acesso ao terminal não residem no código-fonte. São armazenadas em arquivo .env local, excluído explicitamente do controle de versão (Git ignore), seguindo padrão amplamente recomendado em segurança da informação. Cada órgão mantém suas próprias credenciais em seu próprio ambiente — não há centralização de senha.

VERSIONAMENTO E AUDITORIA INTEGRAL DO CÓDIGO:
Todo o código-fonte vive em repositórios Git institucionais (organização splor-mg no GitHub) com histórico completo de alterações, autoria identificada por commit e possibilidade de revisão por pares antes de cada mudança entrar em produção.

TRANSPARÊNCIA TOTAL:
Por ser software livre, qualquer servidor com perfil técnico pode auditar o código e entender exatamente o que a automação faz. Não há caixa-preta. Cada decisão da automação é rastreável diretamente à linha de código que a produziu — explicabilidade plena, diferente de soluções baseadas em modelos visuais como o Power Automate.

EXPLICABILIDADE PARA O USUÁRIO FINAL:
No fluxo de descentralização, cada retorno do SIAFI é traduzido para mensagens em português claro ("saldo zerado na conta", "natureza de despesa inexistente"), registradas na própria planilha de trabalho. O operador sabe exatamente o que aconteceu em cada linha, sem precisar interpretar códigos técnicos do sistema legado.

MITIGAÇÃO DE RISCOS OPERACIONAIS:
A arquitetura prevê tratamento explícito dos códigos de retorno do SIAFI, com log de falhas, separação entre operações bem-sucedidas e linhas que precisam de revisão humana. O operador nunca precisa adivinhar o resultado — o sistema registra tudo.
```

### Replicabilidade e sustentabilidade `[atual: 2.359]`
```
A replicabilidade já foi demonstrada empiricamente, não é apenas promessa. O segundo fluxo (remanejamento de crédito) foi construído a partir do primeiro (cota orçamentária) reutilizando, sem qualquer modificação, as funções de login, navegação no menu do SIAFI e finalização de documentos. O esforço foi significativamente menor que o do primeiro fluxo. O terceiro fluxo (descentralização) reforçou o padrão e ainda avançou em empacotamento: conta com instalador automatizado via script .bat e manual em linguagem simples para operação sem suporte especializado.

MODELO DE REPLICAÇÃO EXTERNA:
Repositórios públicos no GitHub (splor-mg), cloná­veis por qualquer órgão sem custo. Ferramentas 100% gratuitas (Python, py3270, x3270/s3270, Git) sem licença que cresça com o número de usuários, máquinas ou fluxos. Arquitetura modular que permite a qualquer órgão contribuir com fluxos próprios ao catálogo compartilhado, criando valor crescente para todos.

COMPATIBILIDADE COM HARDWARE DO PARQUE ESTADUAL:
A solução roda em qualquer Linux moderno, incluindo hardware que não atende os requisitos mínimos do Windows 10. No contexto do parque de equipamentos estadual, isso significa que máquinas antigas — que não conseguiriam rodar nenhuma ferramenta moderna de automação — podem ser reformatadas com uma distribuição Linux leve e transformadas em nós de automação dedicados, sem custo de hardware adicional. O Power Automate Desktop, por comparação, exige Windows 10/11 Pro/Enterprise, ao menos 4 núcleos de CPU para execução não atendida e licença Process adicional — requisitos que excluem grande parte do parque mais antigo e geram custo recorrente de licença.

SUSTENTABILIDADE:
As ferramentas (x3270, Python, py3270) é estável há décadas, com baixíssima frequência de mudanças disruptivas. A documentação no repositório permite que novos servidores assumam a manutenção sem dependência dos autores originais. A disseminação é diretriz estratégica da SPLOR, conduzida pela própria equipe autora. A possibilidade de execução em servidor headless centralizado reforça a sustentabilidade em escala, permitindo que uma equipe enxuta suporte múltiplos órgãos.

ALCANCE ALÉM DO EXECUTIVO ESTADUAL:
Municípios mineiros e demais estados que operam terminais TN3270 — situação ainda comum no setor público brasileiro — podem adotar a solução sem adaptação institucional. Minas Gerais passa a exportar tecnologia pública aberta para automação de sistemas legados.
```

---

## TELA 5 — Cronograma

| Etapa | Início | Término | Status | Entrega |
|---|---|---|---|---|
| Fluxo de cota orçamentária | mai/2024 | ago/2024 | Concluído | Em produção na SPLOR |
| Fluxo de remanejamento de crédito | ago/2024 | dez/2024 | Concluído | Em produção na SPLOR |
| Fluxo de descentralização de cotas | jan/2025 | mai/2026 | Concluído | Validado com PCMG |
| Atendimento aos 12 órgãos | jul/2026 | dez/2026 | Em andamento | Órgãos implantados |
| Expansão para SIAD | jan/2027 | jun/2027 | Planejado | Fluxos SIAD em produção |
| Expansão para SISAP | jul/2027 | dez/2027 | Planejado | Fluxos SISAP em produção |

### Outras observações (Tela 5) `[máx 2.000 caracteres]`
```
A iniciativa está em operação real desde maio de 2026, com cronograma de entregas incrementais — cada fluxo é módulo independente que gera benefício imediato sem aguardar a conclusão do projeto como um todo. Os números de produção do fluxo de remanejamento (19/05 a 16/06/2026) foram validados por dois caminhos independentes e refletem operação real, não teste controlado. O atendimento aos doze órgãos com interesse manifestado é o próximo passo imediato e depende exclusivamente de recursos internos da SPLOR.
```

---

## TELA 6 — Arquivos Complementares

> Até 3 arquivos PDF, máx 10 MB cada, sem espaço no nome. **Não se identificar nos arquivos.**

Sugestões de arquivos a preparar:
- `resultados_comparativo.pdf` — tabela comparativa (Manual / Power Automate / Python) + dados de produção real (109 docs, 257 linhas, R$ 1,72 bi, 29 UOs)
- `depoimento_pcmg.pdf` — manifestação formal da Diretoria de Orçamento da PCMG (já autorizada via Marcela)
- `arquitetura_governanca.pdf` — diagrama da arquitetura em três camadas + print do repositório GitHub + exemplo de log de execução

---

## TELA 7 — Pesquisa de satisfação
*(não conta para avaliação — responder conforme experiência da equipe)*

---

*Arquivo gerado automaticamente com base nos documentos do projeto. Todos os textos foram verificados nos limites de caracteres estabelecidos pelo MAPA_FORMULARIO.md.*
