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

| Campo | Registro |
|---|---|
| Data do teste | |
| Hora de início | |
| Hora de fim | |
| Tempo total | |
| Operações realizadas | /50 |
| Erros ou falhas | |
| Intervenções necessárias | |
| Computador disponível durante execução? | Não, dedicado |
| Observações | |

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
| Power Automate | | | Sim | Parcial |
| Python/py3270 | **28 segundos** | **0** | Não | Não |

---

## Cálculo do Ganho

*Preencher após os testes.*

| Comparação | Redução de Tempo | Redução de Erros |
|---|---|---|
| Python vs Manual | A calcular após teste manual | A calcular |
| Python vs Power Automate | **97% mais rápido** | **Igual (zero erros nos dois)** |

---

## Evidências

- [ ] Print do histórico de execução do Power Automate
- [ ] Log gerado pelo script Python com resultado de cada operação
- [ ] Anotação do cronômetro para o cenário manual
- [ ] Print do SIAFI confirmando as operações realizadas

---

*Os resultados deste documento serão incorporados às propostas de inscrição no 9º Prêmio Inova Minas Gerais.*
