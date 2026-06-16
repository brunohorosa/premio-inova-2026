**9º PRÊMIO INOVA MINAS GERAIS**

**Edital SEPLAG/SCPRH nº 01/2026**

**Categoria: Ideias Inovadoras Implementáveis**

**Plataforma Aberta de Automação dos Sistemas Estruturantes do Estado**

**uma chave única, em software livre, para devolver ao cidadão o tempo que hoje se perde digitando no SIAFI, SIAD e SISAP**

# 1. Resumo da ideia

O Estado de Minas Gerais inteiro funciona sobre três sistemas estruturantes hospedados no terminal PRODEMGE: o SIAFI, que move o dinheiro público; o SIAD, que cuida das compras, contratos e patrimônio; e o SISAP, que administra as pessoas, da folha de pagamento às aposentadorias. Não há secretaria que escape deles. Saúde, Educação, Segurança Pública, Fazenda, Meio Ambiente, todas dependem desses três sistemas para funcionar no dia a dia.

O problema é que, ainda hoje, milhares de servidoras e servidores operam esses sistemas manualmente, digitando tela a tela, dado por dado, dados que muitas vezes já existem prontos em planilhas. São horas de trabalho humano consumidas por tarefas repetitivas, horas que poderiam estar sendo dedicadas a planejar, analisar e, no fim da linha, atender melhor o cidadão.

**A ideia é simples e poderosa: **uma plataforma aberta de automação, em software livre, que funciona como uma chave única capaz de abrir as três portas, SIAFI, SIAD e SISAP, e executar automaticamente as operações que hoje são feitas à mão. A plataforma é oferecida aos órgãos com fluxos prontos e crescentes; o órgão adota, usa com as próprias credenciais e seus próprios controles, e colhe o benefício imediato de liberar seus servidores para o que realmente importa.

A viabilidade dessa ideia não é teórica. Ela já foi comprovada no sistema mais crítico dos três, o SIAFI, onde a equipe da SPLOR/SEPLAG colocou em produção fluxos reais de automação orçamentária, validados inclusive por um órgão externo, a Polícia Civil de Minas Gerais. O que se propõe agora é transformar essa prova de conceito em uma plataforma institucional que cobre os três sistemas e fica disponível para todo o Estado.

# 2. O problema que se pretende resolver

Apesar de toda a transformação digital dos últimos anos, o núcleo da operação do Estado ainda depende de sistemas legados acessados por terminal TN3270. São sistemas robustos e confiáveis, mas que só aceitam operação manual, tela a tela. Três problemas estruturais convivem nesse cenário.

## 2.1. Tempo de servidor desperdiçado em escala estadual

Cada operação exige digitação manual de informações que, em geral, já estão organizadas em planilhas ou outros sistemas. Multiplicado por milhares de servidores, por todos os órgãos, ao longo de todo o ano, isso representa um volume gigantesco de horas de trabalho qualificado gastas em tarefa mecânica. É tempo que não volta, e que poderia estar sendo usado em análise, planejamento e atendimento.

## 2.2. As ferramentas atuais não foram feitas para esses sistemas

A ferramenta de automação hoje disponível no Estado, baseada em RPA visual (Power Automate Desktop), é excelente para o ecossistema Microsoft moderno, mas opera no limite quando aplicada ao terminal legado: por não conhecer o protocolo do mainframe, ela trata a tela como uma imagem, simula cliques e captura telas como foto. Qualquer mudança de resolução, posição de janela ou atualização quebra a automação. É uma solução frágil para sistemas tão críticos.

## 2.3. Custo, dependência e falta de rastreabilidade

Soluções proprietárias têm custo de licença que cresce com o uso, exigem computadores dedicados, dependem de um único fornecedor e não guardam histórico auditável das operações. Para uma camada cada vez mais estratégica da máquina pública, isso significa custo recorrente, dependência tecnológica e baixa transparência.

# 3. A ideia proposta

A proposta é desenvolver e institucionalizar uma Plataforma Aberta de Automação dos Sistemas Estruturantes, organizada de modo que o órgão receba valor desde o primeiro dia, sem precisar de conhecimento técnico para começar.

## 3.1. Uma chave que abre as três portas

No coração da plataforma está uma biblioteca em Python que conversa diretamente com o protocolo do terminal PRODEMGE, a mesma linguagem nativa que o sistema entende. Por ser uma camada de base comum, essa mesma biblioteca serve para SIAFI, SIAD e SISAP, e para qualquer outro sistema do mesmo terminal. É a chave única: resolvido o acesso ao terminal, abre-se o caminho para automatizar qualquer um dos três sistemas que sustentam o Estado.

## 3.2. Fluxos prontos como porta de entrada

O órgão não precisa programar nada para começar. A plataforma oferece um catálogo de fluxos prontos, automações já construídas para as operações mais comuns, que o órgão simplesmente adota: preenche uma planilha padronizada com os dados que já usa, executa, e a automação faz o resto, com suas credenciais e sob seu controle. Conforme o catálogo cresce, mais operações ficam disponíveis para todos. Montar um fluxo novo e próprio existe como possibilidade para os órgãos que quiserem ir além, mas é o estágio avançado, não a porta de entrada.

## 3.3. Cada órgão no controle do que é seu

A plataforma preserva integralmente a autonomia e a segurança de cada órgão. As credenciais usadas são as mesmas que o servidor já possui para operar o sistema manualmente, nada de novo acesso, nada de senha centralizada. Cada órgão opera seus próprios dados, suas próprias rotinas, seus próprios controles. A SEPLAG governa o padrão, mantém a biblioteca e dissemina, mas não opera no lugar de ninguém.

## 3.4. Governança e transparência desde a base

Todo o código vive em repositórios versionados, com histórico auditável. Cada execução gera registro estruturado do que foi feito, trilha de auditoria que praticamente não existe na operação manual. Por ser software livre, qualquer servidor com perfil técnico pode inspecionar exatamente o que a automação faz, não há caixa-preta. E a documentação é escrita em linguagem simples, pensada para quem não é da área técnica.

# 4. O valor que chega ao cidadão

Esta é a essência da proposta. Automatizar um sistema legado pode parecer, à primeira vista, um ganho apenas técnico, interno. Mas o encadeamento é direto e real:

**automação → servidor liberado da tarefa operacional → mais tempo para a atividade-fim → cidadão melhor atendido.**

Cada hora que um servidor deixa de gastar digitando é uma hora devolvida à missão do órgão. E como SIAFI, SIAD e SISAP atravessam o Estado inteiro, esse ganho se espalha por todas as áreas que tocam a vida das pessoas. Alguns exemplos do potencial, ilustrativos do alcance da plataforma quando adotada por cada área:

**[NOVO] A dimensão desse ganho já é mensurável onde a plataforma foi provada. No SIAFI, um lote de 50 operações que levava cerca de 1 hora e 17 minutos para ser digitado manualmente passou a ser concluído em 28 segundos pela automação. Cada lote assim libera mais de uma hora de trabalho qualificado, que volta para a atividade-fim do órgão. Multiplicado por todas as equipes, todos os meses, em todos os sistemas, o tempo devolvido ao serviço público, e ao cidadão, é de enorme magnitude.**

**Saúde. **A equipe de orçamento da Secretaria de Saúde, liberada da digitação de descentralizações e remanejamentos no SIAFI, dedica mais tempo a garantir que os recursos cheguem aos hospitais e às unidades de atendimento com agilidade. Recurso que anda mais rápido é leito, medicamento e exame que chegam antes ao paciente.

**Educação. **A equipe de compras automatiza no SIAD os processos de aquisição, e acelera a chegada de material escolar, merenda e insumos às escolas. Menos tempo no sistema é mais tempo garantindo que a escola tenha o que precisa no início do ano letivo.

**Segurança Pública. **As equipes de RH automatizam no SISAP as movimentações funcionais de militares e policiais, promoções, progressões, férias, e devolvem agilidade à vida funcional de quem está na ponta protegendo o cidadão, reduzindo atrasos que hoje desgastam a tropa.

**Fazenda e Meio Ambiente. **Equipes financeiras e administrativas de todas as pastas ganham execução orçamentária mais rápida e precisa, o que se traduz em pagamentos a fornecedores em dia, contratos executados no prazo e maior capacidade de resposta do Estado, especialmente em situações extraordinárias como calamidades ambientais.

O ponto comum é claro: a plataforma não substitui o servidor, ela o liberta da parte mecânica do trabalho para que ele se dedique ao que exige inteligência humana, e que beneficia diretamente o cidadão. O alcance real dependerá de cada órgão adotar e aproveitar a plataforma, mas o caminho fica aberto para todos.

**[NOVO] Esse benefício, aliás, já é reconhecido e medido pelo próprio Estado. Entre os indicadores oficiais de sucesso da política de automação mineira está o número de servidores reposicionados, pessoas que deixaram de executar tarefa repetitiva e passaram a atuar em atividades de maior valor. A plataforma proposta foi desenhada para ampliar exatamente esse indicador, levando-o aos sistemas estruturantes mais críticos e, com isso, a todas as áreas do Estado que servem diretamente ao cidadão. É uma diretriz de gestão que orienta o trabalho da equipe proponente: pensar primeiro no órgão atendido e em quem ele serve.**

# 5. Atendimento aos critérios de avaliação

A seguir, os oito critérios da Categoria Ideias Inovadoras Implementáveis (subitem 7.3.2 do Edital), com seus pesos.

## 5.1. Capacidade de inovação (peso 3)

A inovação está em três frentes. Tecnicamente, troca o paradigma frágil de RPA visual, que trata a tela como imagem, por comunicação direta com o protocolo do terminal, robusta e determinística. Em modelo, substitui a configuração presa a uma ferramenta proprietária por código aberto, versionado e auditável, que pertence ao Estado. Institucionalmente, propõe algo raro: uma única plataforma, sem custo de licença e sem fornecedor único, capaz de automatizar os três sistemas que sustentam toda a Administração estadual.

A inovação não compete com o Automatiza.MG, soma-se a ele. O Power Automate continua excelente para fluxos pontuais no ecossistema Microsoft moderno; a plataforma cobre o nicho complementar dos sistemas legados estruturantes, em que a abordagem visual é tecnicamente frágil. A própria biblioteca do Automatiza.MG confirma essa demanda ao listar robôs para SIAD, SIAFI e SISAP e um robô de "Login no Terminal PRODEMGE", reconhecendo o terminal como alvo, sem ainda cobrir os fluxos completos que esta plataforma propõe.

## 5.2. Efeitos da inovação na simplificação administrativa (peso 3)

A ideia atua no coração da Política de Simplificação (Decreto nº 47.441/2018). Substitui a digitação tela a tela, provavelmente a forma mais onerosa de execução administrativa ainda existente, por preenchimento estruturado em planilha com execução automática. Padroniza, entre órgãos diferentes, operações que hoje cada um executa à sua maneira; reduz drasticamente o tempo de execução; elimina retrabalho de erros de digitação; e gera trilha de auditoria automática de cada operação.

## 5.3. Geração de valor público com foco no usuário (peso 3)

A pessoa usuária imediata é a servidora ou servidor que opera os sistemas, e o desenho nasce da empatia direta com essa realidade: a equipe que concebeu a solução é a mesma que sofria com a operação manual. Mas o valor não para aí. Como detalhado na seção 4, o tempo devolvido ao servidor se converte em melhor atendimento ao cidadão em todas as áreas do Estado, da saúde à segurança. É valor público no sentido mais pleno: melhora a vida de quem opera e a de quem é servido.

## 5.4. Grau de agilidade na implantação (peso 2)

O ciclo é curto e incremental. A prova de viabilidade já existe no SIAFI, construída em poucos meses. Cada novo fluxo é um módulo independente que reaproveita o núcleo já validado e gera benefício imediato para a área correspondente, sem necessidade de esperar a conclusão do projeto inteiro. A expansão para os primeiros fluxos de SIAD e SISAP pode ser entregue em ciclos sequenciais de poucas semanas cada.

## 5.5. Grau de alcance (peso 2)

Este é o critério em que a plataforma mais se destaca. Como SIAFI, SIAD e SISAP atravessam todas as Secretarias, autarquias e fundações, o alcance é o Estado inteiro. Em escala individual, são milhares de servidores das áreas de orçamento, finanças, compras, contratos, patrimônio e administração de pessoal. Indiretamente, alcança todos os cidadãos atendidos pelos serviços que esses sistemas viabilizam. Poucas ideias têm um alcance potencial tão amplo quanto uma plataforma que toca os três pilares operacionais do Estado.

**[NOVO] E o alcance não é apenas potencial: já há tração concreta. Após a divulgação institucional da automação de descentralização de cotas, oito órgãos do Estado manifestaram interesse formal em adotá-la. Isso demonstra que existe demanda real e espontânea da Administração pela plataforma, e que a expansão proposta atende a uma necessidade já manifestada, não a uma hipótese.**

## 5.6. Capacidade de multiplicação (peso 1)

A solução é multiplicável por desenho. Por ser software livre, qualquer órgão adota o núcleo sem adaptação e sem custo. O catálogo de fluxos cresce de forma colaborativa: cada fluxo construído por um órgão fica disponível para todos. O custo marginal de cada nova automação é decrescente. E a multiplicação ultrapassa o Executivo estadual: outros Poderes, Municípios e demais estados que operam terminais TN3270, situação ainda comum no Brasil, podem adotar a plataforma sem custo. Minas passa a exportar tecnologia pública.

**[NOVO] Há ainda um vetor de multiplicação imediato e concreto: a base de automações que o Estado já possui. O programa Automatiza.MG contabiliza mais de 110 robôs criados, mais de 10 mil horas economizadas e dezenas de servidores reposicionados para atividades de maior valor. Parte relevante dessas automações opera justamente sobre SIAFI, SIAD e SISAP, a própria biblioteca do programa descreve robôs para empenhos, liquidações, pagamentos e inserção de dados nesses sistemas. São exatamente as operações em terminal legado nas quais a abordagem visual encontra mais limitações de estabilidade. A plataforma proposta oferece a essa base já instalada um motor técnico mais robusto, rápido e auditável: automações que hoje rodam de forma frágil podem migrar para uma fundação mais sólida, sem reescrever a lógica de negócio, apenas trocando a camada que conversa com o sistema. A multiplicação, portanto, não parte do zero, encontra um ecossistema de automação maduro e em expansão pronto para se beneficiar.**

**[NOVO] A disseminação aos órgãos é, ela própria, uma diretriz estratégica da SPLOR. Sob orientação da Subsecretaria, a área trabalha com a lógica de servir seus órgãos clientes, levando a eles soluções que aumentem sua capacidade operacional. A plataforma nasce alinhada a essa diretriz: foi concebida desde o início para ser compartilhada, e a própria SPLOR conduz essa disseminação, com a equipe autora à frente, sem depender de estrutura externa para levar a solução adiante.**

## 5.7. Governabilidade (peso 1)

A implantação depende apenas de articulação interna ao Executivo estadual: SEPLAG na governança do padrão, PRODEMGE na gestão do ambiente, e os órgãos na adoção e na proposição de fluxos. Não há dependência de fornecedor externo, nova contratação ou novo perfil de acesso. As credenciais são as que o servidor já tem. Opera em conformidade com a LGPD, pois não coleta novos dados pessoais e produz logs internos auditáveis.

## 5.8. Disponibilidade de recursos (peso 2)

A ideia exige poucos recursos. Em software, tudo é livre e gratuito (Python, py3270, x3270/s3270, Git). Em pessoas, viabiliza-se com equipe técnica pequena atuando junto às áreas usuárias, modelo já validado na prática. Em hardware, roda em qualquer computador comum, sem máquina dedicada e sem licença, e os requisitos não crescem com o número de fluxos. A diferença de custo em relação ao modelo proprietário, em escala estadual, é de ordem de grandeza, e é o que torna realista a ambição de uma plataforma única para todos os sistemas legados do Estado.

# 6. Vantagens estruturais da abordagem

Além dos critérios formais, três vantagens técnicas se traduzem diretamente em economia pública e viabilidade de escala.

## 6.1. Não trava o computador do servidor

A base técnica da plataforma opera inteiramente em modo texto, sem interface gráfica, sem capturar mouse ou teclado. Isso significa que a automação roda em segundo plano enquanto o servidor continua trabalhando normalmente na mesma máquina. Não há tela travada, não há estação dedicada. No modelo de RPA visual, ao contrário, o computador frequentemente fica bloqueado durante a execução ou exige máquina exclusiva. Em escala estadual, isso representa economia direta de centenas de computadores que deixam de precisar ser dedicados.

## 6.2. Roda em qualquer máquina comum, sem licença

A plataforma funciona em qualquer Linux moderno (gratuito) ou no Windows via WSL, recurso nativo das versões atuais. Os requisitos de hardware são modestos e não escalam com o número de fluxos: rodar dez automações no mesmo computador exige apenas um pouco mais de memória, sem licença adicional. No modelo proprietário, cada nova frente de uso adiciona custo de licença, de máquina, ou de ambos.

## 6.3. Estável e rápida, comprovado em teste real

Por conversar diretamente com o protocolo do sistema, em vez de "olhar" a tela como imagem, a automação é muito mais fluida e o próprio sistema responde de forma mais estável. Isso não é teoria: em teste comparativo real, um mesmo lote de 50 operações no SIAFI foi executado em cerca de 28 segundos na abordagem proposta, contra 13 minutos e 53 segundos no RPA visual, na mesma máquina e no mesmo sistema. A diferença de estabilidade e velocidade é estrutural, e favorece o cumprimento de prazos legais críticos.

# 7. Por que esta ideia é confiável: a prova já existe

Diferentemente de uma ideia puramente conceitual, esta proposta se apoia em uma prova de conceito concreta e em produção. No sistema mais crítico dos três, o SIAFI, a equipe da SPLOR/SEPLAG já desenvolveu e colocou em uso fluxos reais de automação: aprovação e anulação de cotas, remanejamento de crédito, análise para alterações orçamentárias e até a geração de minutas para publicação de decretos. Esses fluxos rodam no dia a dia da diretoria.

**Validação externa real. **A automação da descentralização de cotas para órgãos foi validada com a Polícia Civil de Minas Gerais como piloto, em ambiente real, com aval da diretoria de orçamento do órgão. Após divulgação institucional da iniciativa, oito órgãos já manifestaram interesse formal em adotá-la, demonstrando que existe apetite real e espontâneo da Administração pela automação desses sistemas.

**Evolução tecnológica honesta. **A versão inicialmente divulgada da iniciativa foi construída em Power Automate e serviu como laboratório para a equipe compreender o lado dos órgãos. A partir desse aprendizado, a solução evoluiu para uma implementação própria em Python, tecnicamente superior e mais estável, que substituiu a anterior, e é essa versão que fundamenta a plataforma aqui proposta.

Em outras palavras: a parte mais difícil, provar que dá para automatizar com robustez o sistema mais crítico do Estado, já foi feita. A ideia agora é estender esse padrão comprovado ao SIAD e ao SISAP e institucionalizá-lo como plataforma aberta para todos os órgãos.

# 8. Origem e relação com o contexto institucional

A ideia tem uma fagulha inicial honesta: o contato da equipe da SPLOR com o tema da automação se deu a partir de um curso básico de Power Automate oferecido pela SEPLAG. Foi o ponto de partida. A partir dali, porém, a trajetória foi inteiramente própria: ao tentar aplicar o Power Automate ao terminal PRODEMGE, a equipe constatou as limitações técnicas dessa abordagem para sistemas legados e, por conta própria, pesquisou, desenhou e desenvolveu uma solução especializada e tecnicamente muito superior, a biblioteca em Python que fundamenta esta proposta. A autoria e a evolução da solução são da própria equipe da DCMEFO/SPLOR.

# 9. Resultados esperados com a institucionalização

- Devolução de milhares de horas de trabalho qualificado, hoje gastas em digitação, às atividades-fim de cada órgão, com benefício direto ao cidadão.

- Ampliação do indicador de servidores reposicionados, métrica oficial da política de automação do Estado, ao levar a automação aos três sistemas estruturantes mais críticos do Executivo.

- Redução do risco em operações financeiras e administrativas críticas pela eliminação de erros de digitação.

- Padronização da automação de sistemas legados no Executivo estadual, com biblioteca compartilhada e governança unificada.

- Trilha de auditoria automática de cada operação, ampliando transparência e controle interno.

- Autonomia tecnológica do Estado: solução própria, sem custo de licença e sem dependência de fornecedor único.

- Desenvolvimento de capacidade técnica interna capaz de manter e evoluir a plataforma.

- Posicionamento de Minas Gerais como referência nacional em automação aberta de sistemas legados, com tecnologia exportável a outros entes.