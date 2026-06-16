# Registro de Testes Comparativos

Comparativo de desempenho entre execução **Manual**, **Power Automate** e **Python/py3270** para operações de Remanejamento de Crédito no SIAFI-MG.

---

## Configuração dos Testes

| Item | Detalhe |
|---|---|
| Operação testada | Remanejamento de Crédito |
| Quantidade de operações | 50 por cenário |
| Sistema | SIAFI-MG |
| Ambiente | Produção |
| Responsável | DCMEFO em parceria com AID |

---

## Resultados

### Cenário 1, Execução Manual

**Estrutura do lote testado:**

| UO | Linhas de alteração |
|---|---|
| 1101 | 9 |
| 1371 | 14 |
| 2091 | 7 |
| 2101 | 11 |
| 2241 | 9 |
| **Total** | **50 linhas, 5 UOs** |

**Tempos medidos por etapa:**

| Etapa | Tempo medido |
|---|---|
| Abertura SIAFI + credenciais + liberação da UO | 00:39,70 (por UO) |
| Consulta 2ª tela + digitação de uma linha | 01:26,99 (por linha) |
| Justificativa + finalização | 00:17,62 (por UO) |

**Cálculo por UO:**

| UO | Liberação | Linhas | Finalização | Total UO |
|---|---|---|---|---|
| 1101 | 0:39,70 | 9 x 1:26,99 = 13:02,91 | 0:17,62 | 14:00,23 |
| 1371 | 0:39,70 | 14 x 1:26,99 = 20:17,86 | 0:17,62 | 21:15,18 |
| 2091 | 0:39,70 | 7 x 1:26,99 = 10:08,93 | 0:17,62 | 11:06,25 |
| 2101 | 0:39,70 | 11 x 1:26,99 = 15:56,89 | 0:17,62 | 16:54,21 |
| 2241 | 0:39,70 | 9 x 1:26,99 = 13:02,91 | 0:17,62 | 14:00,23 |

| Campo | Registro |
|---|---|
| Data do teste | 02/06/2026 |
| Tempo total estimado | **1 hora e 17 minutos** |
| Operações realizadas | 50/50 |
| Erros ou falhas | Sujeito a erros de digitação |
| Intervenções necessárias | Sim, constantes |
| Computador disponível durante execução? | Não, dedicado |
| Observações | Tempo calculado com base em medições reais por etapa. Inclui consulta em segunda tela do SIAFI para buscar dados da dotação, etapa eliminada pelo Python e Power Automate. |

---

### Cenário 2, Power Automate

| Campo | Registro |
|---|---|
| Data do teste | 29/05/2026 |
| Hora de início | 11:44:29 |
| Hora de fim | 11:58:22 |
| Tempo total | **13 min 53 seg** |
| Operações realizadas | 50/50 |
| Erros ou falhas | **Nenhum** |
| Quedas ou instabilidades | **Nenhuma** |
| Versão do Power Automate | 2.68.00237.26118 |
| Computador disponível durante execução? | Não, dedicado |
| Observações | Horários registrados automaticamente pelas variáveis HoraInicio e HoraFim |

> **Dica:** tirar print do histórico de execuções do Power Automate com hora de início e fim de cada fluxo.

---

### Cenário 3, Python/py3270

| Campo | Registro |
|---|---|
| Data do teste | 02/06/2026 |
| Hora de início | 16:02:09 |
| Hora de fim | 16:02:37 |
| Tempo total | **28 segundos** |
| Operações realizadas | 50/50 |
| Erros ou falhas | **Nenhum** |
| Erros de lançamento incorreto | **Zero, todos retornaram REGISTRO EFETUADO** |
| Computador disponível durante execução? | Sim, livre |
| Observações | Log gerado automaticamente pelo script |

> **Dica:** o script já registra automaticamente início, fim e resultado de cada operação no log.

---

## Resumo Comparativo

*Preencher após concluir os três testes.*

| Cenário | Tempo Total | Erros | Computador Dedicado | Intervenção Humana |
|---|---|---|---|---|
| Manual | | | Sim | Sim, o tempo todo |
| Power Automate | **13min 53seg** | Zero | Sim | Parcial |
| Python/py3270 | **28 segundos** | **0** | Não | Não |

---

## Cálculo do Ganho

*Preencher após os testes.*

| Comparação | Redução de Tempo | Redução de Erros |
|---|---|---|
| Python vs Manual | **97% mais rápido** | Elimina erros de digitação |
| Python vs Power Automate | **97% mais rápido** | Zero erros nos dois |

---

## Evidências

- [ ] Print do histórico de execução do Power Automate
- [ ] Log gerado pelo script Python com resultado de cada operação
- [ ] Anotação do cronômetro para o cenário manual
- [ ] Print do SIAFI confirmando as operações realizadas

---

*Os resultados deste documento serão incorporados às propostas de inscrição no 9º Prêmio Inova Minas Gerais.*


---

## Números de Produção (validados em 16/06/2026)

Dados extraídos por script de contagem (leitura da aba ROBO de todos os lotes da pasta "Realizados/Automação Python"), referentes ao fluxo de remanejamento de crédito e alterações orçamentárias.

| Métrica | Valor |
|---|---|
| Período | 19/05/2026 a 16/06/2026 (menos de um mês) |
| Documentos SIAFI gerados (operações) | 109 |
| Linhas de alteração processadas | 257 (145 suplementações + 112 anulações) |
| Valor suplementado (recurso alocado) | R$ 1.717.867.307,28 (~R$ 1,72 bilhão) |
| Unidades orçamentárias atendidas | 29 |
| Erros de lançamento | Zero |

**Validação do valor:** confirmado por dois caminhos independentes, (1) o consolidado manual (copia.xlsx) bate exatamente com a soma automática dos lotes; (2) escala confirmada pela equipe (valor 35.000.000.000 na planilha = R$ 350 milhões reais, ou seja, valores em centavos).

**Observação:** este é apenas um dos fluxos em produção. Os fluxos de aprovação de cotas, remanejamento pela administração central e descentralização de cotas operam em adição a este e ainda serão quantificados.

## Caso de demonstração, lote grande (257 linhas, 29 UOs)

Tempo estimado para processar o lote consolidado em cada cenário, com base nas medições reais por etapa:

| Cenário | Tempo estimado |
|---|---|
| Manual | ~6,7 horas (~400 min) |
| Power Automate | ~71 minutos |
| Python/py3270 | ~2,4 minutos |
