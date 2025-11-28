# Sistema de Controle de Atendimento (SCA) - UNINASSAU

Este projeto consiste em uma **Single Page Application (SPA)** desenvolvida para simular um sistema de gestão de filas e chamados para laboratórios médicos. O sistema atende aos requisitos de lógica de priorização, emissão de senhas e relatórios definidos no documento de especificação do projeto acadêmico.

## 📋 Sobre o Projeto

O objetivo é gerenciar o fluxo de atendimento através de três agentes principais:
1. **Agente Sistema (AS):** Emite senhas e gerencia a lógica.
2. **Agente Atendente (AA):** Chama o próximo da fila e realiza o atendimento.
3. **Agente Cliente (AC):** Solicita a senha e aguarda no painel.

O sistema foi construído utilizando tecnologias Web padrão (HTML5, CSS3 e JavaScript ES6+), não necessitando de instalação de dependências complexas para execução.

---

## ⚙️ Funcionalidades Implementadas

### 1. Tipos de Senha e Priorização
O sistema gerencia três filas distintas com regras específicas de Tempo Médio (TM) e prioridade:

- **SP (Senha Prioritária):** Alta prioridade. TM estimado de 15 min (±5 min).
- **SE (Senha Exames):** Atendimento rápido. TM estimado < 1 min (95% dos casos).
- **SG (Senha Geral):** Prioridade normal. TM estimado de 5 min (±3 min).

### 2. Algoritmo de Intercalação
O sistema obedece rigorosamente à regra de alternância de prioridade definida no diagrama de requisitos:

$$[SP] \rightarrow [SE | SG] \rightarrow [SP] \rightarrow [SE | SG]$$

* Sempre que uma senha Prioritária (SP) é atendida, a próxima chamada deve ser, obrigatoriamente, uma de Exame (SE) ou Geral (SG), garantindo fluxo contínuo.
* A senha SE tem preferência sobre a SG dentro do bloco de "não-prioritários" devido à rapidez do atendimento.

### 3. Formatação de Senhas
As senhas são geradas automaticamente seguindo o padrão `YYMMDD-PPSQ`, onde:
- **YYMMDD:** Data da emissão.
- **PP:** Tipo da senha (SP, SE, SG).
- **SQ:** Sequencial diário reiniciável.

### 4. Painel e Relatórios
- **Painel de Chamadas:** Exibe a senha atual e as últimas 5 chamadas (histórico), sem revelar a próxima senha da fila (Fila Cega).
- **Relatórios:** Gera uma tabela com horário de emissão, atendimento e cálculo do tempo médio simulado.
- **Descarte:** Opção para registrar clientes ausentes (meta de 5%).

---

## 🚀 Como Executar

Como o projeto foi desenvolvido em um arquivo único para portabilidade:

1. Baixe o arquivo `index.html` (ou o nome que você salvou o código).
2. Dê um clique duplo para abri-lo em qualquer navegador moderno (Chrome, Firefox, Edge, Safari).
3. Não é necessário servidor web (Apache/Nginx) ou Node.js para rodar esta versão do protótipo.

---

## 🎮 Guia de Uso

### Visão do Cliente (Lado Esquerdo)
1. **Totem:** Clique nos botões coloridos para retirar uma senha (SP, SE ou SG).
2. **Painel (TV):** Observe sua senha aparecer no destaque quando for chamada.

### Visão do Atendente (Lado Direito)
1. **Status da Fila:** Acompanhe quantas pessoas existem em cada categoria.
2. **Chamar Próximo:** Clique no botão para acionar o algoritmo de prioridade.
3. **Finalizar:**
* *Finalizar Atendimento:* Conclui com sucesso e registra o tempo.
* *Cliente Ausente:* Descarta a senha e registra no relatório.
4. **Relatórios:** Acompanhe a tabela gerada dinamicamente na parte inferior.

---

## 🛠️ Tecnologias

- **Frontend:** HTML5, CSS3 (Grid/Flexbox).
- **Lógica:** JavaScript (Vanilla JS).
- **Persistência:** Memória volátil (os dados são resetados ao recarregar a página).

---

## 📄 Referência

Projeto baseado na especificação:
> "Sistema para controle de atendimento" - UNINASSAU / VERITAS.
