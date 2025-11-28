# Sistema de Controle de Atendimento (SCA) - UNINASSAU

Este projeto consiste em uma **Single Page Application (SPA)** desenvolvida para simular um sistema de gestão de filas e chamados para laboratórios médicos. [cite_start]O sistema atende aos requisitos de lógica de priorização, emissão de senhas e relatórios definidos no documento de especificação do projeto acadêmico[cite: 5, 21].

## 📋 Sobre o Projeto

O objetivo é gerenciar o fluxo de atendimento através de três agentes principais:
1.  [cite_start]**Agente Sistema (AS):** Emite senhas e gerencia a lógica[cite: 23].
2.  [cite_start]**Agente Atendente (AA):** Chama o próximo da fila e realiza o atendimento[cite: 24].
3.  [cite_start]**Agente Cliente (AC):** Solicita a senha e aguarda no painel[cite: 29].

O sistema foi construído utilizando tecnologias Web padrão (HTML5, CSS3 e JavaScript ES6+), não necessitando de instalação de dependências complexas para execução.

---

## ⚙️ Funcionalidades Implementadas

### 1. Tipos de Senha e Priorização
[cite_start]O sistema gerencia três filas distintas com regras específicas de Tempo Médio (TM) e prioridade[cite: 31]:

* **SP (Senha Prioritária):** Alta prioridade. [cite_start]TM estimado de 15 min (±5 min)[cite: 32, 40].
* **SE (Senha Exames):** Atendimento rápido. [cite_start]TM estimado < 1 min (95% dos casos)[cite: 37, 43].
* **SG (Senha Geral):** Prioridade normal. [cite_start]TM estimado de 5 min (±3 min)[cite: 36, 40].

### 2. Algoritmo de Intercalação
[cite_start]O sistema obedece rigorosamente à regra de alternância de prioridade definida no diagrama de requisitos[cite: 50]:

$$[SP] \rightarrow [SE | SG] \rightarrow [SP] \rightarrow [SE | SG]$$

* [cite_start]Sempre que uma senha Prioritária (SP) é atendida, a próxima chamada deve ser, obrigatoriamente, uma de Exame (SE) ou Geral (SG), garantindo fluxo contínuo[cite: 48].
* [cite_start]A senha SE tem preferência sobre a SG dentro do bloco de "não-prioritários" devido à rapidez do atendimento[cite: 43].

### 3. Formatação de Senhas
[cite_start]As senhas são geradas automaticamente seguindo o padrão `YYMMDD-PPSQ`[cite: 58], onde:
* **YYMMDD:** Data da emissão.
* **PP:** Tipo da senha (SP, SE, SG).
* **SQ:** Sequencial diário reiniciável.

### 4. Painel e Relatórios
* [cite_start]**Painel de Chamadas:** Exibe a senha atual e as últimas 5 chamadas (histórico), sem revelar a próxima senha da fila (Fila Cega)[cite: 54, 55].
* [cite_start]**Relatórios:** Gera uma tabela com horário de emissão, atendimento e cálculo do tempo médio simulado[cite: 74, 75].
* [cite_start]**Descarte:** Opção para registrar clientes ausentes (meta de 5%)[cite: 57].

---

## 🚀 Como Executar

Como o projeto foi desenvolvido em um arquivo único para portabilidade:

1.  Baixe o arquivo `index.html` (ou o nome que você salvou o código).
2.  Dê um clique duplo para abri-lo em qualquer navegador moderno (Chrome, Firefox, Edge, Safari).
3.  Não é necessário servidor web (Apache/Nginx) ou Node.js para rodar esta versão do protótipo.

---

## 🎮 Guia de Uso

### Visão do Cliente (Lado Esquerdo)
1.  **Totem:** Clique nos botões coloridos para retirar uma senha (SP, SE ou SG).
2.  **Painel (TV):** Observe sua senha aparecer no destaque quando for chamada.

### Visão do Atendente (Lado Direito)
1.  **Status da Fila:** Acompanhe quantas pessoas existem em cada categoria.
2.  **Chamar Próximo:** Clique no botão para acionar o algoritmo de prioridade.
3.  **Finalizar:**
    * *Finalizar Atendimento:* Conclui com sucesso e registra o tempo.
    * *Cliente Ausente:* Descarta a senha e registra no relatório.
4.  **Relatórios:** Acompanhe a tabela gerada dinamicamente na parte inferior.

---

## 🛠️ Tecnologias

* **Frontend:** HTML5, CSS3 (Grid/Flexbox).
* **Lógica:** JavaScript (Vanilla JS).
* **Persistência:** Memória volátil (os dados são resetados ao recarregar a página).

---

## 📄 Referência

Projeto baseado na especificação:
> [cite_start]"Sistema para controle de atendimento" - UNINASSAU / VERITAS[cite: 1, 3, 6].
