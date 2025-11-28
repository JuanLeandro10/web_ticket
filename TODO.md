# Lista de Tarefas (TODO) - Sistema de Controle de Atendimento

Este documento rastreia as tarefas pendentes, melhorias desejadas e requisitos de infraestrutura para a evolução do Sistema de Controle de Atendimento (SCA).

## 🚧 Back-End & Infraestrutura (Requisitos do PDF)
- [ ] **Migração para Node.js:** Implementar API RESTful em Node.js para substituir a lógica atual em memória.
- [ ] **Integração com MySQL 8.0:** Criar esquema de banco de dados para persistência das senhas e atendimentos.
- [ ] Tabela `senhas`: id, numero, tipo, data_emissao, data_atendimento, status, guiche_id.
- [ ] Tabela `historico`: logs de auditoria.
- [ ] **Reset Automático de Sequência:** Implementar "Cron Job" ou verificação lógica para reiniciar a numeração da sequência (SQ) diariamente (00:00).
- [ ] **Suporte a Múltiplos Guichês:** Expandir a lógica para permitir que múltiplos atendentes (AA) operem simultaneamente, concorrendo pela fila global.

## 💻 Front-End & Interface
- [ ] **Migração de Framework:** Portar a interface atual (HTML/JS Puro) para React, Angular ou Vue, conforme sugestão da infraestrutura.
- [ ] **Comunicação em Tempo Real (WebSockets):**
- [ ] Sincronizar o Painel (TV) com a ação do Atendente sem necessidade de refresh manual.
- [ ] Sincronizar a fila de espera entre múltiplos computadores de atendentes.
- [ ] **Layout Responsivo para Totem:** Otimizar a interface de emissão de senhas para telas touch verticais (Totens de autoatendimento).

## 📊 Regras de Negócio e Relatórios
- [ ] **Cálculo Real do Tempo Médio (TM):**
- [ ] Substituir a simulação randômica atual pelo cálculo real: `Hora Fim - Hora Início`.
- [ ] Implementar alertas visuais caso o atendimento exceda os tempos estipulados (15min para SP, 5min para SG).
- [ ] **Relatórios Consolidados:**
- [ ] Implementar relatório com filtros por data (Diário e Mensal).
- [ ] Adicionar totais quantitativos: Emitidas vs. Atendidas por prioridade.
- [ ] **Lógica de Descarte Automático:** Implementar limpeza automática de senhas não atendidas após o encerramento do expediente (17:00).

## 🧪 Testes e Qualidade
- [ ] **Testes Unitários:** Validar o algoritmo de intercalação $SP \rightarrow [SE|SG] \rightarrow SP$.
- [ ] **Simulação de Carga:** Testar o comportamento do sistema com alta emissão de senhas SE (Exames) para garantir que a priorização não bloqueie as senhas SG indefinidamente.
- [ ] **Validação de Formato:** Garantir que o gerador de senhas nunca falhe no formato `YYMMDD-PPSQ`.

## 📝 Documentação
- [ ] Criar diagrama ER (Entidade-Relacionamento) do Banco de Dados.
- [ ] Documentar endpoints da API (Swagger).
- [ ] Manual do Usuário para o perfil "Atendente".
