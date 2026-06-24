# 9º PRÊMIO INOVA MINAS GERAIS
**Edital SEPLAG/SCPRH nº 01/2026**
**Categoria: Ideias Inovadoras Implementáveis**

---

# Automação Python dos Sistemas TN3270 do Estado

> *Uma biblioteca de código aberto que permite a qualquer equipe técnica da Administração Pública mineira automatizar tarefas no SIAFI, no SIAD e no SISAP — os três sistemas estruturantes do Estado.*

---

## 1. O cenário: três sistemas, quase nenhuma automação

O Estado de Minas Gerais inteiro funciona sobre três sistemas hospedados no terminal PRODEMGE: o SIAFI, que executa a despesa pública; o SIAD, que cuida das compras, contratos e patrimônio; e o SISAP, que administra as pessoas, da folha de pagamento às aposentadorias. Não há secretaria que escape deles. Saúde, Educação, Segurança Pública, Fazenda — todas dependem desses três sistemas para funcionar no dia a dia.

A realidade operacional é direta: a quase totalidade dos servidores que operam esses sistemas o faz de forma manual. Tela a tela, campo a campo, digitando informações que muitas vezes já existem organizadas em planilhas. Uma parcela menor já utiliza automação via RPA visual. O trabalho manual é lento, exposto a erros e não deixa rastro estruturado: ao final de um lote de operações, o servidor tem apenas a memória das telas que viu.

Esse cenário não é trivial de mudar. SIAFI, SIAD e SISAP são sistemas legados, acessados pelo protocolo TN3270 do mainframe — um protocolo robusto e maduro, mas que cria uma barreira técnica específica para quem quer automatizar: as ferramentas de automação mais conhecidas e acessíveis não foram projetadas para esse ambiente. Aplicá-las ao terminal exige adaptações e contorna limitações que raramente são superadas com estabilidade.

O resultado é um paradoxo: três sistemas que movimentam o dinheiro, as compras e as pessoas de todo o Estado, operados manualmente por milhares de servidores, enquanto a tecnologia para automatizá-los de forma robusta existe há décadas e nunca foi tornada amplamente acessível no setor público estadual.

---

## 2. A ideia: uma ferramenta, não um produto pronto

A proposta é simples e direta: **apresentar e institucionalizar uma biblioteca Python de código aberto que interage com o terminal TN3270 via protocolo nativo**, tornando-a disponível e documentada para que qualquer equipe técnica da Administração estadual possa construir suas próprias automações.

É importante distinguir o que esta proposta é e o que não é.

**O que é:** uma ferramenta — uma biblioteca que resolve o problema de acesso ao protocolo TN3270 e permite que o programador escreva, em Python, o que a automação deve fazer. Com ela, a equipe técnica de um órgão pode criar um script que preenche um empenho, gera um remanejamento ou consulta um saldo, automaticamente, a partir de uma planilha de dados.

**O que não é:** um catálogo de fluxos prontos para distribuir. Não existe um pacote que o órgão instala e passa a usar sem nenhuma construção. Cada automação precisa ser desenvolvida pela equipe técnica do próprio órgão, para as tarefas específicas que esse órgão realiza. A biblioteca oferece a fundação; o que se constrói sobre ela depende de quem a usa.

Essa distinção é fundamental para a honestidade da proposta: ela requer equipe técnica, ela requer Python, ela requer esforço de desenvolvimento. O que ela elimina é a barreira que hoje impede que essa possibilidade sequer exista — a dificuldade de comunicar com o protocolo do terminal.

---

## 3. Como a ferramenta funciona

No núcleo técnico da solução está a biblioteca **py3270**, interface Python para o emulador **x3270/s3270** — ferramentas de código aberto mantidas pela comunidade há mais de duas décadas e amplamente utilizadas em instituições internacionais que operam mainframes em escala.

Em termos práticos, quando um script Python usa essa biblioteca para automação:
- Conecta-se ao terminal TN3270 da PRODEMGE pelo protocolo nativo
- Identifica em qual campo da tela do mainframe está, por coordenadas reais de linha e coluna
- Lê e escreve dados diretamente nessas posições
- Envia comandos nativos do mainframe (Enter, F3, F5, F8, entre outros)
- Captura, em texto, o retorno exato que o sistema exibe

Não há simulação visual. Não há captura de imagem. Não há reconhecimento de pixel. A automação fala com o mainframe pela mesma linguagem que o mainframe entende, o que resulta em uma interação estável e previsível — o sistema responde ao protocolo da mesma forma que responderia a um operador humano no terminal.

Uma consequência técnica importante: como o emulador usado (s3270) opera em modo texto, sem interface gráfica, a automação roda em segundo plano sem capturar mouse, teclado ou tela. O servidor que disparou a execução pode continuar trabalhando normalmente no mesmo computador enquanto a automação processa — sem travar a máquina, sem ocupar a tela.

---

## 4. A prova de que funciona: o que a SPLOR/SEPLAG já fez com ela

A biblioteca não é proposta teórica. A equipe proponente a utiliza em produção real, no SIAFI/MG, desde maio de 2024. Foram desenvolvidos três fluxos completos, em uso contínuo na DCMEFO/SPLOR:

**Aprovação e anulação de cota orçamentária:** o script lê uma planilha com as operações do mês, acessa o SIAFI, navega até a transação correspondente, preenche os campos (mês, fonte, UO, grupo de despesa, ação, valor), executa e registra o retorno linha a linha — número do documento gerado, sucesso ou código de erro específico.

**Remanejamento de crédito:** segue o mesmo padrão arquitetural, com um módulo adicional de análise prévia de saldo que verifica disponibilidade antes de cada operação, evitando falhas em produção.

**Descentralização de cota para Unidades Executoras:** fluxo com empacotamento mais maduro — instalador automatizado, consolidação de múltiplas planilhas em lote e tradução dos retornos do SIAFI para mensagens em português claro. Validado em ambiente real com a Polícia Civil de Minas Gerais como órgão piloto.

Os resultados desses fluxos em produção são verificáveis. Somente no fluxo de remanejamento, em menos de um mês de operação (19/05 a 16/06/2026), foram gerados 109 documentos no SIAFI, processadas 257 alterações orçamentárias e alocados cerca de R$ 1,72 bilhão em recursos, atendendo 29 unidades orçamentárias, com zero erros de lançamento.

Para dar a dimensão do ganho em termos de tempo: um lote de 50 operações de remanejamento que consumia cerca de uma hora e dezessete minutos de digitação manual passou a ser concluído em 28 segundos pela automação. Não é uma estimativa: é um resultado medido em teste real, na mesma máquina e no mesmo sistema em produção.

Esses dados não são o produto desta proposta — são a prova de que a ferramenta funciona. O que a proposta apresenta é a ideia de tornar essa ferramenta e esse aprendizado acessíveis a todo o Estado.

---

## 5. O que a institucionalização proposta engloba

Ter a biblioteca desenvolvida e funcionando em um órgão não é suficiente para que outros órgãos possam adotá-la. A barreira de entrada existe: requer Python, requer familiaridade com o conceito de protocolo de terminal, requer configuração de ambiente Linux ou WSL. A proposta de institucionalização tem como objetivo central reduzir essa barreira.

Os componentes concretos:

**Documentação técnica em português:** a biblioteca existe com documentação voltada ao contexto corporativo internacional. Para o servidor público estadual, é necessário um material em português que explique o que é o protocolo TN3270, como configurar o ambiente, como estruturar um script básico e como interpretar os retornos do sistema. Esse material não existe hoje de forma organizada e acessível.

**Guia de primeiros passos:** um roteiro prático para que uma equipe técnica com Python básico consiga escrever sua primeira automação simples em um dos três sistemas. A experiência da equipe proponente mostrou que os primeiros obstáculos — conexão com o terminal, navegação inicial, leitura do retorno — são os mais difíceis. Um guia que já resolveu esses obstáculos reduz semanas de tentativa e erro.

**Repositório público com exemplos e fluxos:** o repositório já existe (organização splor-mg no GitHub), com os fluxos da SPLOR como referência. A proposta é formalizá-lo como espaço institucional de compartilhamento, onde outros órgãos possam contribuir com os fluxos que desenvolverem. Cada contribuição amplia o valor disponível para todos.

**Suporte inicial:** a equipe proponente pode oferecer suporte técnico inicial aos primeiros órgãos que queiram adotar a ferramenta, reduzindo ainda mais a barreira de entrada.

---

## 6. Requisitos e desafios honestos

Esta proposta não esconde seus requisitos. Eles são reais e precisam ser ditos com clareza.

**Requer conhecimento em Python.** Não é necessário ser especialista — conhecimento básico de lógica de programação e Python é suficiente para construir fluxos simples — mas não é uma ferramenta de arrastar e soltar. Órgãos sem nenhum servidor com perfil técnico precisarão desenvolver essa capacidade antes de adotar a ferramenta.

**Requer desenvolvimento individual de cada fluxo.** Não há automação pronta para empenhar, para registrar ponto ou para consultar saldo. Cada tarefa a ser automatizada requer que a equipe técnica entenda o processo, mapeie as telas do sistema e escreva o script correspondente. Esse é um investimento real de tempo.

**Requer ambiente Linux ou WSL.** O emulador x3270/s3270 é uma ferramenta Linux. No Windows, roda via WSL (Windows Subsystem for Linux), recurso nativo das versões atuais do Windows, mas que exige configuração inicial. Em máquinas com políticas de TI mais restritivas, pode ser necessária validação com a área de infraestrutura.

**Requer validação da conexão de rede.** A conexão com o terminal PRODEMGE precisa funcionar a partir do ambiente Linux/WSL. Em geral funciona — é a mesma conexão de rede que o emulador visual usa — mas políticas específicas do órgão podem exigir ajuste.

Esses desafios não invalidam a proposta — definem seu público-alvo. A ferramenta é para equipes técnicas que já têm ou querem desenvolver capacidade de automação. Para órgãos com esse perfil, ela remove a barreira que hoje impede que essa possibilidade sequer exista.

---

## 7. Por que esta abordagem agrega valor ao contexto existente

O Estado de Minas Gerais já possui o programa Automatiza.MG, com mais de 110 automações desenvolvidas e resultados expressivos em tempo economizado. Esta proposta não compete com o programa — complementa-o, cobrindo um nicho que o programa ainda não atende plenamente.

O Automatiza.MG cobre com excelência o ecossistema Microsoft moderno: aplicativos de Office, portais web, formulários, e-mail, sistemas com interface gráfica. Para esse universo, ele é a solução adequada.

O nicho que esta proposta aborda é diferente: sistemas legados acessados por protocolo TN3270, ambiente específico onde o RPA visual encontra seus limites naturais. A própria biblioteca do Automatiza.MG confirma essa demanda ao listar automações para SIAFI, SIAD e SISAP — e ao incluir um robô específico de "Login no Terminal PRODEMGE". O que esta proposta oferece é a camada técnica especializada para esse ambiente.

As duas abordagens existem lado a lado para fins diferentes. Uma equipe pode usar Power Automate para um processo no SharePoint e Python/py3270 para um processo no SIAFI. Não é escolha entre um e outro: é ter a ferramenta certa para cada contexto.

---

## 8. Características técnicas que geram valor operacional

**O computador fica livre durante a execução.** Por rodar em modo texto sem interface gráfica, a automação não precisa controlar mouse, teclado ou tela. O servidor que disparou o processo pode continuar trabalhando normalmente enquanto o script executa.

**Zero custo de licença.** Python, py3270, x3270/s3270 e Git são todos gratuitos e de código aberto. O órgão não paga nada pela ferramenta — o custo é exclusivamente de tempo de desenvolvimento da equipe.

**Código auditável e log por operação.** Por ser software livre, qualquer servidor com perfil técnico pode ler o código e entender exatamente o que a automação faz. Cada execução pode gerar log estruturado com dados de entrada, operação realizada e retorno do sistema — trilha de auditoria que praticamente não existe na operação manual.

**Credenciais seguras por padrão.** A prática recomendada é armazenar credenciais em arquivo `.env`, excluído do controle de versão. Cada operador usa suas próprias credenciais — não há conta compartilhada.

**Possibilidade de execução em servidor.** Por não depender de interface gráfica, a automação pode rodar em servidor Linux headless, conectado via VPN ao ambiente da PRODEMGE, abrindo a possibilidade de execuções agendadas e centralizadas.

**Roda em qualquer hardware comum.** Não há exigência de máquina dedicada, edição corporativa de sistema operacional ou requisito especial de CPU.

---

## 9. Potencial de multiplicação

A ferramenta é multiplicável por design. Os repositórios são públicos, o stack é gratuito, e o modelo de compartilhamento é orgânico: cada fluxo desenvolvido por um órgão pode ser contribuído ao repositório compartilhado e reutilizado por outros que realizam a mesma operação.

Esse modelo tem uma propriedade importante: o valor cresce com o uso. Quanto mais órgãos adotam e contribuem com fluxos, mais fluxos ficam disponíveis para todos, com custo marginal decrescente para cada novo órgão que entra.

A multiplicação também alcança outros entes: municípios e outros estados que operam terminais TN3270 — situação ainda comum no Brasil — podem adotar a mesma biblioteca sem adaptação. A experiência de Minas Gerais pode servir de referência nacional para automação de sistemas legados na Administração Pública.

---

## 10. Equipe proponente

A solução foi concebida e desenvolvida por equipe pequena e multidisciplinar da SEPLAG:

**Guilherme de Melo Ferreira** — principal responsável técnico. Desenvolveu a arquitetura da biblioteca e os fluxos em produção, concebendo o modelo modular que viabiliza a replicabilidade.

**Bruno Henrique de Oliveira Rosa** — domínio técnico do SIAFI e das regras orçamentárias. Traduz os processos em especificações para a automação e valida os fluxos em produção.

**Gabriel Braico Dornas** — Assessor Chefe de Inteligência de Dados. Direção técnica estratégica do projeto, avaliação de viabilidade e respaldo às decisões técnicas.

---

## 11. Próximos passos propostos

1. **Documentação em português:** guia completo de configuração do ambiente, primeiros passos e boas práticas para sistemas TN3270.
2. **Guia prático:** roteiro para a primeira automação — conexão, navegação básica, leitura de retorno — baseado nos aprendizados reais da equipe.
3. **Capacitação inicial:** sessões técnicas para equipes de órgãos interessados.
4. **Formalização do repositório:** espaço institucional de compartilhamento de fluxos entre órgãos, com orientações para contribuição.
5. **Acompanhamento dos primeiros adotantes:** suporte técnico inicial e coleta de aprendizados para aprimorar a documentação.

---

*A biblioteca já está em produção. O que esta proposta apresenta é a ideia de abrir esse caminho para todo o Estado.*
