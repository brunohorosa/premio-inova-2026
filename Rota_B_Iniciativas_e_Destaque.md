**9º PRÊMIO INOVA MINAS GERAIS**

Edital SEPLAG/SCPRH nº 01/2026

**Categoria: Iniciativas Implementadas de Sucesso**

+ Habilitação ao Destaque em Automatização e Inteligência Artificial

**Biblioteca Python para Automação do Terminal PRODEMGE:**

automação aberta, governada e auditável de sistemas legados do Estado (SIAFI, SIAD, SISAP)

# 1. Resumo da iniciativa

Esta iniciativa apresenta uma biblioteca Python para automação programática do terminal TN3270 da PRODEMGE, desenvolvida e implementada na Superintendência Central de Planejamento Orçamentário (SPLOR/SEPLAG) e atualmente em produção com múltiplos fluxos aplicados ao SIAFI/MG, entre eles aprovação e anulação de cotas, remanejamento de crédito e descentralização de cotas para Unidades Executoras. A iniciativa demonstra, em escala real, uma abordagem técnica complementar à do programa Automatiza.MG, especializada para o cenário específico de sistemas legados, em que o RPA visual baseado em captura de tela apresenta limitações estruturais.

**[NOVO] A plataforma já opera transações da área orçamentária em produção: aprovação, descentralização e remanejamento de cotas orçamentárias, realocação de créditos orçamentários e geração automática de minutas para publicação de decretos orçamentários. A mesma arquitetura permite expandir para qualquer outra transação do SIAFI, incluindo empenhos, liquidações, ordens de pagamento, folha de pessoal e restos a pagar, sem necessidade de nova infraestrutura, cobrindo o sistema em sua totalidade.**

**[NOVO] A validação da solução transcende o ambiente interno da SPLOR/SEPLAG. Os testes da automação de descentralização de cotas orçamentárias para Unidades Executoras foram realizados com credenciais reais da Polícia Civil de Minas Gerais (PCMG), com aval formal da Diretoria de Orçamento do órgão, em ambiente real de produção. A PCMG foi o órgão piloto da versão anterior em Power Automate, amplamente divulgada pela Agência Minas, e é também o primeiro órgão externo a validar a nova solução em Python. A solução está pronta para substituir o Power Automate na PCMG, órgão com um dos maiores volumes de movimentações orçamentárias do Estado.**

O resultado mensurado é direto e comprovado em teste real: um lote de 50 operações que consumia cerca de 1h17min de digitação manual passou a ser executado em 28 segundos pela biblioteca, redução superior a 97%, com eliminação virtual de erros. A iniciativa cobre hoje o ciclo de movimentação orçamentária da diretoria (aprovação, remanejamento, descentralização, alterações e minutas de decreto) e já foi validada externamente pela PCMG, com oito órgãos demandando sua adoção.

A iniciativa é apresentada também à categoria Destaque em Automatização e Inteligência Artificial por preencher integralmente seus requisitos: trata-se de uso estrutural, não meramente demonstrativo, de automatização de processos em larga escala, com governança formal (versionamento em Git institucional, padrão de credenciais por variáveis de ambiente, revisão por pares), conformidade com a LGPD e arquitetura desenhada para replicabilidade e sustentabilidade de longo prazo.

# 2. O problema enfrentado

A SPLOR/SEPLAG é responsável, entre outras atribuições, por operações no SIAFI/MG que envolvem volumes mensais expressivos de lançamentos repetitivos, aprovações de cota orçamentária, anulações, remanejamentos de crédito. Cada uma dessas operações exige digitação tela a tela, no terminal mainframe, de dados que já existem em planilhas trabalhadas pela equipe. O processo é tedioso, lento e exposto a erro de digitação, risco particularmente grave porque opera sobre valores financeiros e gera documentos contábeis cuja correção exige procedimentos formais.

**[DADO PÚBLICO A VALIDAR] Para dar a dimensão do sistema sobre o qual a iniciativa atua: o SIAFI-MG é o sistema que executa o orçamento estadual, fixado para 2026 em R$ 132 bilhões de despesa. Cada operação automatizada pela iniciativa, portanto, incide sobre o sistema que move a integralidade dos recursos públicos do Estado. (Fonte: LOA 2026/ALMG.)**

Em meses de alta demanda, fechamento de exercício, abertura de orçamento, remanejamentos extraordinários, a operação manual passa a consumir parcela desproporcional do tempo da equipe técnica, em detrimento das atividades de análise orçamentária que constituem o núcleo da função. A equipe identificou, na cultura institucional aberta pelo Automatiza.MG, uma oportunidade de atacar esse gargalo via automação. Ao explorar a aplicação do Power Automate ao terminal pw3270, no entanto, encontrou-se uma limitação técnica relevante: a ferramenta opera o terminal por simulação visual (captura de imagem e clique em coordenadas de pixel), abordagem frágil para a operação de sistemas mainframe, sujeita a quebras frequentes por mudanças de resolução, posição da janela, atualização do emulador ou alterações visuais do próprio sistema.

Diante desse cenário, a equipe pesquisou alternativas técnicas e identificou que existe, há décadas, uma classe de ferramentas livres especializadas em operação programática do protocolo TN3270, o mesmo protocolo do terminal mainframe, amplamente utilizadas em instituições internacionais que operam sistemas legados em escala. A partir dessa descoberta, a equipe construiu, em poucos meses, a primeira versão funcional da biblioteca apresentada nesta inscrição.

# 3. A solução implementada

A iniciativa consiste em uma biblioteca Python organizada em três camadas, hoje em operação real na SPLOR.

## 3.1. Núcleo técnico, comunicação nativa com o terminal

A camada de base utiliza a biblioteca py3270 (interface Python para o emulador x3270/s3270), que dialoga com o terminal pelo protocolo TN3270 nativo. Em termos práticos, a automação identifica em qual campo da tela do mainframe está, lê e escreve dados por coordenadas reais (linha e coluna), envia comandos do mainframe (Enter, F3, F5, F8) e captura, em texto, o retorno exato do sistema. Não há simulação visual de cliques, não há captura de imagem, não há OCR, todos os pontos de fragilidade do RPA visual aplicado a mainframes são eliminados.

## 3.2. Fluxos em produção

Sobre o núcleo técnico, foram desenvolvidos três fluxos completos, hoje em uso em produção:

**Aprovação e anulação de cota orçamentária **(repositório siafi-automacao-cota): lê planilha Excel padronizada com as operações a serem realizadas, faz login no SIAFI, navega até a transação de movimentação orçamentária, preenche os campos (mês, fonte, UO, grupo de despesa, ação, valor), executa a operação e captura linha a linha o retorno do sistema (sucesso, código de erro específico, número do documento gerado). Suporta as duas variantes, aprovação global e aprovação amarrada, e o fluxo reverso de anulação.

**Remanejamento de crédito **(repositório siafi-automacao-credito): segue padrão arquitetural idêntico ao fluxo de cota, validando empiricamente a tese de replicabilidade da biblioteca. Inclui módulo de análise prévia de saldo, que verifica antes de cada operação se há disponibilidade suficiente, evitando falhas operacionais em produção.

**[NOVO] Descentralização de cota orçamentária (repositório siafi-automacao-descentralizacao): automatiza a etapa em que cada órgão distribui, para suas Unidades Executoras, as cotas já aprovadas. É o fluxo mais maduro em empacotamento: conta com instalador automatizado, consolidação de múltiplas planilhas em um único lote e tradução dos retornos do SIAFI para mensagens em linguagem clara. Foi validado em ambiente real com a Polícia Civil de Minas Gerais (PCMG) como órgão piloto. Além desses três fluxos, a biblioteca também automatiza a análise para alterações orçamentárias e a geração de minutas para publicação de decretos orçamentários, cobrindo o ciclo completo de movimentação orçamentária operado pela diretoria.**

## 3.3. Camada de governança

A iniciativa adota desde o início práticas formais de governança:

Versionamento integral em Git, em repositórios institucionais sob a organização splor-mg no GitHub, com histórico auditável de cada alteração.

Segregação de credenciais em arquivo .env, fora do controle de versão, em conformidade com boas práticas de segurança da informação.

Log estruturado de execução: cada linha processada gera registro contendo dados de entrada, operação executada, retorno do sistema e número do documento gerado, trilha de auditoria que praticamente não existe na operação manual.

Documentação técnica versionada (README, requirements, instruções de instalação) que permite a qualquer servidor com perfil técnico instalar e operar a solução em sua estação de trabalho.

**[NOVO] Para o fluxo de descentralização orçamentária, esse padrão de documentação evoluiu para um modelo ainda mais acessível: a instalação é feita por scripts automatizados para Windows que configuram todo o ambiente sem exigir conhecimento técnico prévio, e a operação diária é guiada por um manual em linguagem simples, permitindo que qualquer servidor opere a solução de forma autônoma, sem depender de suporte especializado para o uso cotidiano.**

Arquitetura modular: o login e funções utilitárias (finalização de documento, navegação por menus) ficam isolados em módulos compartilhados, e cada novo fluxo reaproveita essas funções, reduzindo o esforço marginal de adicionar uma nova transação ao catálogo.

# 4. Resultados mensurados

A iniciativa está em produção há meses e produziu resultados verificáveis e medidos. Para quantificar o impacto com precisão, a equipe realizou um teste comparativo estruturado, executando um mesmo lote de 50 operações de remanejamento de crédito no SIAFI em três cenários: manual, Power Automate e a biblioteca Python. Os resultados estão detalhados abaixo.

**[NOVO] Resultado do teste comparativo (50 operações idênticas, mesma máquina, mesmo sistema, em produção): execução manual estimada em cerca de 1 hora e 17 minutos; Power Automate em 13 minutos e 53 segundos; biblioteca Python em apenas 28 segundos. A biblioteca foi cerca de 97% mais rápida que a operação manual e aproximadamente 30 vezes mais rápida que o Power Automate, com zero erro de lançamento nos três casos automatizados. Todos os 50 lançamentos via Python retornaram REGISTRO EFETUADO.**

**[DADO INTERNO A LEVANTAR PELA EQUIPE] Volume total já processado pela automação em produção: inserir número de execuções, de dotações/operações processadas e, se possível, valor total movimentado pela solução em Python, além das horas/mês economizadas pela equipe da SPLOR. Caracterizar também os 8 órgãos demandantes (áreas/portes) e o volume da PCMG no piloto.**

## 4.1. Tempo de execução

Lotes que, em modo manual, consumiam mais de uma hora de digitação ininterrupta passaram a ser executados em menos de meio minuto. No teste comparativo, 50 remanejamentos de crédito levaram cerca de 1h17min no modo manual e 28 segundos pela biblioteca Python, redução superior a 97% no tempo de execução. Em escala de produção, isso significa devolver horas de trabalho qualificado à atividade analítica todos os meses.

## 4.2. Redução de erros

Erros de digitação em operações financeiras no SIAFI são particularmente onerosos, pois geram documentos contábeis cuja correção exige procedimentos formais. A iniciativa elimina, na prática, essa classe de erro: como os dados são lidos da planilha previamente revisada pela equipe e digitados pelo script com precisão determinística, não há margem para erro humano de digitação durante a execução. Erros remanescentes, quando ocorrem, são erros do dado de entrada na planilha, que são detectáveis em revisão prévia e podem ser tratados de forma estruturada.

## 4.3. Auditoria e transparência

**[NOVO] No fluxo de descentralização orçamentária, essa trilha de auditoria é reforçada por uma estrutura de pastas com arquivamento automático: planilhas já processadas são movidas para uma pasta de operações realizadas, e versões anteriores de conferências são preservadas com numeração sequencial, garantindo que nenhum registro de execução seja sobrescrito.**

Antes da iniciativa, a operação manual não produzia registro estruturado: o servidor digitava as operações e, ao final, tinha apenas a memória das telas que viu. Com a automação, cada operação produz registro automático em log, contendo dados de entrada, retorno do sistema e número de documento. Esse registro é arquivável, auditável e reutilizável, gera, em outras palavras, capacidade de governança que praticamente não existia.

## 4.4. Reprodutibilidade da arquitetura

A construção do segundo fluxo (remanejamento de crédito) a partir do primeiro (cota orçamentária) validou empiricamente a tese de que a arquitetura é replicável com custo marginal decrescente. Funções como login, navegação por menus principais e finalização de documentos foram reaproveitadas sem qualquer modificação. O esforço de desenvolvimento do segundo fluxo foi significativamente menor que o do primeiro, indicando que cada novo fluxo subsequente exigirá ainda menos esforço.

# 5. Atendimento aos critérios da categoria principal

A Categoria Iniciativas Implementadas de Sucesso é avaliada com base nos critérios 1 a 6 do subitem 7.3.2 do Edital. A seguir, cada um é abordado de forma direta.

## 5.1. Capacidade de inovação (peso 3)

A inovação está em três frentes simultâneas. Primeiro, em termos técnicos: desloca a automação de sistemas legados do paradigma de RPA visual, que trata a tela como imagem, para o paradigma de scripting de protocolo, em que o software dialoga com o mainframe na sua linguagem nativa, eliminando estruturalmente uma classe inteira de fragilidades operacionais. Segundo, em modelo: substitui a configuração interna de uma ferramenta proprietária por código aberto, versionado, revisado e auditável. Terceiro, em postura institucional: demonstra, na prática, que a Administração Pública mineira é capaz de construir e manter sua própria camada de automação para sistemas estratégicos, sem custo de licença e sem dependência de fornecedor único.

A inovação não compete com o Automatiza.MG, soma-se a ele. O programa existente cobre brilhantemente o ecossistema Microsoft moderno. A presente iniciativa cobre o nicho complementar dos sistemas legados, em que a abordagem do programa apresenta limitação técnica reconhecida.

**A própria biblioteca do Automatiza.MG confirma essa demanda: ela descreve explicitamente que seus robôs servem para utilizar SIAD, SIAFI e SISAP, fazer empenhos, liquidações e pagamentos, exatamente os sistemas e operações cobertos pela presente iniciativa. Além disso, a biblioteca já disponibiliza um robô específico chamado Login no Terminal PRODEMGE, reconhecendo o terminal como alvo de automação. O que a solução aqui apresentada oferece é a camada seguinte: não apenas o login, mas a execução completa de fluxos operacionais, com estabilidade e precisão superiores às do Power Automate nesse ambiente específico. Os números do Automatiza.MG reforçam a escala do impacto possível: o programa já economizou mais de 10.000 horas e viabilizou R$ 125 milhões em operações via automação. A presente iniciativa amplia esse impacto para o nicho que o programa ainda não cobre plenamente.**

## 5.2. Efeitos da inovação na simplificação administrativa (peso 3)

A iniciativa atua diretamente no objeto do Decreto nº 47.441/2018. Substitui a digitação manual repetitiva em sistemas legados, provavelmente a forma mais onerosa de execução administrativa ainda presente na máquina pública, por preenchimento estruturado em planilha, com execução automática. Os efeitos práticos já se observam na SPLOR: padronização do procedimento entre membros da equipe (todos usam a mesma planilha-modelo e o mesmo script), redução drástica do tempo de execução, eliminação de retrabalho associado a erros, geração automática de trilha de auditoria. Indiretamente, a maior agilidade da execução orçamentária se traduz em pagamentos mais rápidos a fornecedores e maior capacidade de resposta do Estado a demandas extraordinárias.

## 5.3. Geração de valor público com foco no usuário (peso 3)

A pessoa usuária imediata é a própria servidora ou servidor que opera os sistemas legados. O desenho da iniciativa nasceu da empatia direta com essa realidade, a equipe que construiu a solução é a mesma que sofria com a operação manual. Por isso a planilha de entrada espelha o formato com que a equipe já organizava seus dados, e o log de retorno responde, em linguagem clara, às perguntas que o servidor faz ao final de um lote ("deu certo?", "quais linhas falharam?", "qual o número do documento?").

O valor entregue é tangível: horas de trabalho recuperadas, risco de erro virtualmente eliminado, segurança quanto ao resultado de cada operação. Em escala secundária, beneficia pessoas usuárias externas, fornecedores que recebem mais rápido, áreas finalísticas que veem suas demandas orçamentárias processadas com mais agilidade, e o cidadão, último beneficiário da maior eficiência do Estado.

**[NOVO] O encadeamento de valor é direto: a automação libera o servidor da tarefa operacional, que passa a dedicar mais tempo à atividade-fim do órgão, e essa atividade-fim é, em última instância, o que chega ao cidadão. No caso da execução orçamentária, recurso que se move mais rápido e com menos erro significa serviços públicos executados no prazo e fornecedores pagos em dia.**

## 5.4. Grau de agilidade na implantação (peso 2)

A prova de implantação ágil já está dada. A iniciativa saiu da ideia inicial para a operação em produção em poucos meses, com o primeiro fluxo (cota) implantado primeiro e o segundo (crédito) construído em prazo significativamente menor, graças à reutilização da arquitetura. A entrega ocorre em ciclos curtos: cada fluxo novo é módulo independente, que pode ser desenvolvido, testado e colocado em produção em semanas, e gera benefício imediato sem depender da conclusão do projeto como um todo.

**[NOVO] O terceiro fluxo, a descentralização de cotas, confirma esse padrão de agilidade: já chegou ao estágio mais maduro de empacotamento, com instalador automatizado e manual em linguagem simples, e foi validado externamente pela PCMG, evidenciando que cada novo fluxo não apenas reaproveita a arquitetura, mas avança em facilidade de adoção.**

## 5.5. Grau de alcance (peso 2)

O alcance imediato compreende a equipe da SPLOR, onde a iniciativa opera diariamente. O alcance potencial, dado pela arquitetura replicável da biblioteca, é estadual: qualquer servidor que opere SIAFI/MG, SIAD ou SISAP pode ser beneficiado pelos próximos fluxos a serem desenvolvidos. Como esses três sistemas atravessam todas as Secretarias, autarquias e fundações do Executivo Estadual, o público potencial direto é da ordem de milhares de servidores.

O alcance se torna especialmente expressivo quando se considera processos como a Descentralização Orçamentária, executada mensalmente por todos os órgãos sem exceção, e fluxos análogos no SIAD, naturalmente próximos da arquitetura já validada. Em escala indireta, o alcance se estende a fornecedores do Estado, beneficiários de programas e à sociedade, beneficiados pela maior agilidade da máquina pública.

**[NOVO] Vale destacar o peso específico do SISAP, administração de pessoal: movimentações funcionais, folha de pagamento, aposentadorias, progressões, promoções, concessão de férias regulamentares e prêmio, quinquênios, lançamento de faltas e demais operações do ciclo funcional do servidor, realizadas mensalmente por equipes de RH em todos os órgãos do Estado. A biblioteca do Automatiza.MG já lista 11 robôs dedicados ao SISAP, confirmando a dimensão da demanda e o potencial de impacto da plataforma nesse sistema.**

**[DADO PÚBLICO A VALIDAR] A dimensão do SISAP é expressiva: a folha de pagamento estadual supera R$ 4,2 bilhões mensais e alcança mais de 640 mil servidores ativos e inativos. Levar a automação a operações desse sistema, no futuro, significaria atuar sobre um dos maiores volumes administrativos do Estado. (Fonte: folha out/2025, Agência Minas.)**

**[NOVO] O fluxo de descentralização orçamentária inclui ainda uma etapa de consolidação automática, que reúne múltiplas planilhas, por exemplo, de diferentes unidades de um mesmo órgão, em um único lote de processamento antes de acionar a automação no SIAFI, demonstrando que a arquitetura já opera em escala acima de um único usuário ou unidade.**

**[NOVO] A demanda externa já é concreta. Após divulgação institucional da iniciativa, oito órgãos do Estado manifestaram interesse formal em adotar a automação da descentralização de cotas. A versão inicialmente divulgada foi construída em Power Automate e serviu como laboratório; a partir desse aprendizado, a solução evoluiu para a implementação em Python aqui apresentada, tecnicamente superior, que a substituiu. É essa versão que será disponibilizada aos órgãos interessados. A procura espontânea demonstra que o alcance potencial não é hipótese: é demanda real batendo à porta.**

## 5.6. Capacidade de multiplicação (peso 1)

A iniciativa já comprovou empiricamente sua capacidade de multiplicação: o segundo fluxo (crédito) foi construído a partir do primeiro (cota) com esforço significativamente reduzido, validando a arquitetura. Externamente à SPLOR, a multiplicação se viabiliza por três caminhos: (i) os repositórios são públicos no GitHub e podem ser clonados e adaptados por qualquer órgão; (ii) o stack é integralmente gratuito (Python, py3270, x3270/s3270, Git), sem custo de adoção; (iii) a arquitetura modular permite que cada novo órgão contribua com fluxos próprios para a biblioteca compartilhada. A multiplicação alcança naturalmente outros entes federativos: Municípios mineiros e demais estados que operem terminais TN3270, situação ainda comum no setor público brasileiro, podem adotar a solução sem qualquer adaptação institucional.

**[NOVO] Há ainda um vetor de multiplicação imediato: a base de automações que o Estado já possui. O programa Automatiza.MG contabiliza mais de 110 robôs e milhares de horas economizadas, e parte relevante dessas automações opera justamente sobre SIAFI, SIAD e SISAP, terreno em que a abordagem visual é mais frágil. Essas automações podem migrar para o motor mais robusto desta biblioteca sem reescrever a lógica de negócio, apenas trocando a camada que conversa com o sistema. A multiplicação, portanto, encontra um ecossistema maduro e pronto para se beneficiar.**

# 6. Habilitação ao Destaque em Automatização e Inteligência Artificial

A iniciativa preenche integralmente os requisitos para concorrer ao Destaque em Automatização e IA (Capítulo 5 do Edital): é Iniciativa Implementada de Sucesso, já está em operação, apresenta resultados mensuráveis, demonstra uso estrutural e não meramente demonstrativo de automatização de processos, e oferece informações suficientes para avaliação adequada por comissão especializada. A seguir, aborda-se cada um dos cinco critérios específicos do Destaque (subitem 7.3.3 do Edital).

## 6.1. Qualidade técnica da solução (peso 3)

A qualidade técnica da solução é elevada e tecnicamente diferenciada. Em vez de adotar a abordagem comum de RPA visual (captura de tela, cliques por coordenadas de pixel), a iniciativa opta por interação programática direta com o protocolo TN3270, a mesma linguagem nativa do terminal mainframe. A escolha técnica não é arbitrária: é apropriada ao problema. Para sistemas modernos com interface gráfica, o RPA visual é geralmente adequado. Para sistemas mainframe acessados via TN3270, a interação por protocolo é estruturalmente mais robusta, pois opera por coordenadas lógicas (linha e coluna) imunes a alterações de resolução, posição da janela, atualizações do emulador visual ou alterações visuais do sistema.

A adequação metodológica é reforçada pela escolha de stack consolidado: o x3270/s3270 é mantido pela comunidade há mais de duas décadas, é amplamente utilizado em instituições internacionais que operam mainframes em produção, e o py3270 é interface Python madura para essa base. A arquitetura modular adotada, separação clara entre núcleo de acesso ao terminal, fluxos específicos de cada transação e funções utilitárias compartilhadas, é boa prática de engenharia de software, raramente vista em automações de RPA tradicionais. A efetividade está demonstrada: a solução resolve, na prática, o problema público apresentado, com dois fluxos em produção e arquitetura validada para replicação.

Há ainda uma dimensão técnica da qualidade que merece destaque por suas consequências operacionais diretas: a forma como o software se comporta enquanto executa. A biblioteca utilizada (s3270) opera inteiramente em modo texto, sem qualquer interface gráfica, o que significa que a automação roda em segundo plano sem capturar mouse, teclado ou tela do servidor. A pessoa que disparou a execução continua trabalhando normalmente no mesmo computador. Em contraste, o RPA visual depende de controlar fisicamente a tela do Windows, e a documentação oficial do Power Automate Desktop é explícita quanto à exigência de máquina sem sessão de usuário ativa para execução não atendida. Na prática institucional, isso se traduz em duas opções para o RPA visual: o servidor para de usar o computador enquanto a automação roda, ou destina-se uma estação exclusiva para a automação. Nenhuma dessas situações ocorre na abordagem aqui apresentada.

Essa característica técnica abre, ainda, uma possibilidade que o RPA visual estruturalmente não permite: execução em servidor central, headless (sem tela), conectado à rede de governo via VPN, a mesma rede já exigida pelo SIAFI, SIAD e SISAP. Em termos arquiteturais, isso significa que a plataforma é compatível com modelos de orquestração corporativa (execução agendada, lotes orquestrados, múltiplas automações em paralelo no mesmo servidor) sem multiplicar estações de trabalho ou licenças de sessão.

## 6.2. Resultado mensurável (peso 2)

Os resultados mensuráveis estão detalhados na seção 4. Em síntese, comprovados por teste comparativo em produção: redução superior a 97% no tempo de execução (de cerca de 1h17min para 28 segundos em um lote de 50 operações), execução cerca de 30 vezes mais rápida que o Power Automate na mesma máquina, eliminação virtual de erros de digitação (todos os lançamentos automatizados retornaram REGISTRO EFETUADO), trilha de auditoria estruturada por log, e validação externa pela PCMG, com oito órgãos já demandando a adoção.

## 6.3. Governança, ética e conformidade (peso 3)

A iniciativa foi construída com atenção formal à governança, à conformidade legal e à ética operacional.

**Conformidade com a LGPD **(Lei nº 13.709/2018): a solução não coleta novos dados pessoais; opera com as credenciais nominais já concedidas aos servidores para uso manual do terminal, preservando integralmente o modelo de controle de acesso existente. Os logs gerados ficam armazenados em ambiente controlado, sem exposição externa.

**Tratamento seguro de credenciais: **credenciais de acesso ao terminal não ficam no código-fonte. São armazenadas em arquivo .env local, fora do controle de versão (Git ignore explícito), seguindo padrão amplamente recomendado em segurança da informação.

**Versionamento e auditoria integral do código: **todo o código-fonte vive em repositórios Git institucionais (organização splor-mg no GitHub), com histórico completo de alterações, autoria identificada por commit e possibilidade de revisão por pares antes de cada mudança entrar em produção.

**[NOVO] No fluxo de descentralização, essa explicabilidade chega até o usuário final: cada retorno do SIAFI é traduzido para mensagens em português claro, como "saldo zerado na conta" ou "natureza de despesa inexistente", registradas em uma coluna de progresso na própria planilha de trabalho, eliminando a necessidade de interpretar códigos técnicos do sistema legado.**

**Transparência da tecnologia: **como toda a solução é software livre, qualquer servidor com perfil técnico pode auditar o código, entender exatamente o que a automação faz e propor melhorias. Não há caixa-preta.

**Mitigação de riscos operacionais: **a arquitetura prevê tratamento explícito de erros do sistema (cada código de retorno do SIAFI é interpretado pelo script), com possibilidade de retentativa controlada, log de falhas e separação clara entre operações bem-sucedidas e linhas que precisam de revisão humana.

**Explicabilidade: **diferentemente de soluções baseadas em modelos estatísticos opacos, a automação aqui apresentada é determinística, cada passo é código legível, e cada decisão da automação é diretamente rastreável à linha de código que a produziu. Isso facilita auditoria, debugging e responsabilização.

## 6.4. Replicabilidade e sustentabilidade (peso 2)

A replicabilidade já foi demonstrada empiricamente, internamente à SPLOR, com a construção do segundo fluxo a partir do primeiro. Externamente, a replicação se viabiliza pelos repositórios públicos no GitHub, pelo stack 100% gratuito e pela arquitetura modular que separa o que é genérico (login, navegação) do que é específico de cada transação. Não há custo de licença que cresça com o número de usuários, máquinas ou fluxos, característica especialmente relevante em uma estratégia de escala estadual.

Os requisitos de ambiente também favorecem a replicabilidade. A solução opera em qualquer Linux moderno (Ubuntu, por exemplo, gratuito e de baixíssimo consumo de hardware) ou em Windows via WSL (Windows Subsystem for Linux), recurso nativo das versões atuais do sistema. Não há exigência de Windows Pro ou Enterprise, não há exigência de mínimo de núcleos de CPU, não há licença adicional para execução não atendida. Para fins de comparação direta, a documentação oficial do Power Automate Desktop estabelece como requisitos: Windows 10/11 Pro/Enterprise ou Windows Server (ARM não suportado); ao menos quatro núcleos de CPU para execução não atendida; .NET Framework instalado; e licenciamento adicional do plano Process para automações sem supervisão humana. Cada uma dessas exigências, multiplicada pela escala estadual, representa custo institucional não trivial. A abordagem aqui apresentada elimina todos.

A sustentabilidade operacional ao longo do tempo é favorecida por três fatores: o stack técnico utilizado (x3270, Python, py3270) é maduro e estável há décadas, com baixíssima frequência de mudanças disruptivas; a documentação no repositório permite que novos servidores assumam a manutenção sem dependência dos autores originais; e a disseminação aos órgãos é uma diretriz estratégica da própria SPLOR, que conduz a iniciativa com sua equipe autora à frente, garantindo governança e continuidade institucional. A possibilidade adicional de execução em servidor, viabilizada pela natureza headless do stack, reforça a sustentabilidade ao permitir que uma equipe enxuta mantenha e dissemine a solução para múltiplos órgãos.

## 6.5. Relevância da solução e geração de valor (peso 3)

A solução resolve problema real, recorrente e de alta relevância institucional. Não se trata de iniciativa demonstrativa, prova de conceito acadêmica ou exercício tecnológico sem aplicação prática. É iniciativa que nasceu de necessidade concreta da equipe da SPLOR, foi aplicada a operações que a equipe efetivamente realiza, e gera valor mensurável a cada execução.

Em escala maior, a relevância se amplia: a operação de sistemas legados via terminal mainframe é dor estrutural compartilhada por dezenas de áreas do Estado de Minas Gerais e por inúmeras administrações públicas brasileiras. Oferecer uma solução técnica madura, aberta e replicável para esse problema gera valor que extrapola a SPLOR e o próprio Estado. Em termos estratégicos, a iniciativa reforça a soberania tecnológica do Estado em uma camada cada vez mais crítica da operação pública, a camada de automação, e posiciona Minas Gerais como referência em automação aberta de sistemas legados na Administração Pública brasileira.

# 7. Origem e relação com o contexto institucional

A iniciativa tem uma fagulha inicial honesta: o primeiro contato da equipe da SPLOR com o tema da automação se deu por um curso básico de Power Automate oferecido pela SEPLAG. Daí em diante, a trajetória foi inteiramente própria. Ao aplicar o Power Automate ao terminal PRODEMGE, a equipe esbarrou em suas limitações técnicas para sistemas legados e, por conta própria, pesquisou, projetou e desenvolveu a biblioteca em Python aqui apresentada, tecnicamente muito superior. A autoria, o desenvolvimento e a evolução da solução são da equipe da DCMEFO/SPLOR.

A biblioteca proposta não compete com o Power Automate, nem com o programa Automatiza.MG. Compete com a operação manual em sistemas legados, esta sim, a verdadeira ineficiência que precisa ser superada. Power Automate continua sendo solução adequada para a vasta maioria dos casos cobertos pelo programa: fluxos pontuais, no ecossistema Microsoft moderno, construídos por servidores não técnicos. A presente iniciativa cobre o nicho complementar de sistemas legados estruturantes, em escala, com necessidade de governança formal, em que o RPA visual apresenta limitação técnica reconhecida.

# 8. Próximos passos planejados

Com a institucionalização da iniciativa, planejam-se os seguintes desenvolvimentos:

Atendimento aos oito órgãos que já demandaram a automação da descentralização de cotas, com implantação da versão Python e acompanhamento dos resultados, ampliando a base de órgãos atendidos.

Expansão da biblioteca para o SIAD (compras, almoxarifado, patrimônio), com fluxos prioritários a serem definidos em conjunto com a Subsecretaria de Logística e Patrimônio.

Expansão da biblioteca para o SISAP (administração de pessoal), automatizando operações de alto volume como movimentações funcionais, folha, aposentadorias, progressões e concessão de férias, em articulação com as áreas de gestão de pessoas.

Disseminação da biblioteca aos órgãos do Estado, conduzida pela SPLOR como diretriz estratégica de servir seus órgãos clientes, com documentação, capacitação e suporte à adoção.

Documentação institucional, capacitação técnica e abertura formal dos repositórios para contribuições de servidores de outros órgãos.

Consolidação de indicadores de uso e benefício, com painel de acompanhamento institucional.