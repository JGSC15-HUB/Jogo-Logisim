# 🎮 Jogo Jokenpô (Pedra, Papel e Tesoura) - Logisim

![Logisim](https://shields.io)
![Status](https://shields.io)
![Academic](https://shields.io)

Este projeto consiste em um jogo de **Pedra, Papel e Tesoura** totalmente digital, automatizado e síncrono, desenvolvido no simulador de circuitos **Logisim**. O circuito simula a experiência de um console de videogame clássico ou fliperama para dois jogadores humanos, aplicando na prática conceitos fundamentais de **Sistemas Digitais** e **Arquitetura de Computadores**.

---

## 🚀 Funcionalidades Principais

*   **🧠 Mesa de Combate Avançada:** Processamento lógico robusto das regras clássicas do jogo (Pedra vence Tesoura, Tesoura vence Papel, Papel vence Pedra) implementado diretamente através de cruzamento de portas lógicas, eliminando curtos-circuitos e bugs elétricos.
*   **🙈 Mecânica de Mão Oculta (Blind Choice):** Sistema de privacidade onde os jogadores realizam suas escolhas secretamente. Durante a fase de seleção, os displays de 7 segmentos locais permanecem completamente apagados, impedindo trapaças.
*   **💻 Controle de Turnos Adaptado para Notebook:** Utilização de interruptores locais (`PRONTO_J1` e `PRONTO_J2`) que funcionam como travas de estado. Isso resolve o problema de touchpads/mouses de notebooks que não permitem cliques simultâneos, permitindo jogadas assíncronas em turnos.
*   **📺 Matrizes de LED Individuais com Varredura:** Renderização gráfica gigante dos símbolos (Pedra, Papel e Tesoura) em matrizes de LED exclusivas para cada jogador no topo da tela, acionadas por um sistema de multiplexação temporal via *Clock* rápido.
*   **📊 Placar Automático de Pontuação (Scoreboard):** Sistema de memória em tempo real totalmente isolado da fiação principal. Ele detecta pulsos de vitória gerados na mesa de combate e incrementa automaticamente os displays hexadecimais locais.
*   **🔄 Botão Unificado de Reset:** Um comando de limpeza geral que reinicia a memória dos contadores do placar, resetando os displays visuais para `0` instantaneamente para uma nova partida.

---

## 🛠️ Componentes e Conceitos de Arquitetura Utilizados

O projeto foi estruturado sem códigos abstratos, utilizando apenas blocos de hardware fundamentais:

1.  **Flip-Flops e Contadores:** Utilizados para salvar e alternar as escolhas dos jogadores (valores binários de 1 a 3) e acumular de forma sólida os pontos do placar.
2.  **Distribuidores (*Splitters*):** Gerenciamento e padronização de barramentos, agrupando ou separando fios de 1 bit em cabos de dados combinados.
3.  **Decodificadores lógicos:** Responsáveis por interpretar o número binário da escolha de cada jogador e convertê-lo em saídas exclusivas de sinal elétrico isolado (fios dedicados para Pedra, Papel ou Tesoura).
4.  **Barreiras de Portas AND de 2 Entradas:** Injetadas diretamente nas entradas físicas `A, B, C, D` dos decodificadores dos displays de 7 segmentos. Funcionam como portões eletrônicos que barram os bits, habilitando o recurso de ocultação de jogada.
5.  **Malha de Portas NOT e OR de Controle:** Responsáveis pelo gerenciamento de fluxo energético, permitindo que os visores e telas de LED só se acendam após a validação mútua dos sinais de pronto e do comando de revelação.

---

## 🎮 Como Jogar no Simulador

1.  **Fase de Escolha:** Ative a simulação no Logisim (`Ctrl + E`). O Jogador 1 e o Jogador 2 usam os botões dos seus contadores locais para escolher suas jogadas (1 = Pedra, 2 = Papel, 3 = Tesoura). Os displays de 7 segmentos e as matrizes estarão apagados.
2.  **Travar Jogada:** Assim que escolherem, cada jogador dá um clique no seu pino de prontidão:
    *   O Jogador 1 clica no pino quadrado `PRONTO_J1` (o pino travará em `1`).
    *   O Jogador 2 clica no pino quadrado `PRONTO_J2` (o pino travará em `1`).
3.  **A Grande Revelação:** Com os dois prontos e as telas apagadas, clique no pino quadrado **`REVELAR`** no centro da tela.
    *   *O efeito instantâneo:* Os dois displays de 7 segmentos acendem revelando os números, as matrizes de LED renderizam os desenhos piscando no topo, o LED de placar acende o vencedor da rodada e o placar digital soma o ponto automaticamente!
4.  **Próxima Rodada:** Desclique os pinos de `PRONTO` e o pino `REVELAR` voltando-os para `0`. As telas se apagarão e o circuito estará limpo para o próximo confronto.
5.  **Zerar o Campeonato:** A qualquer momento, clique no botão **`ZERAR`** perto do placar para limpar a memória dos pontos e retornar os displays para `0`.

---

## 📂 Como Executar o Projeto

1. Faça o download do arquivo do circuito (`.circ`) presente neste repositório.
2. Baixe e abra o simulador **Logisim**.
3. No Logisim, vá em `File > Open` e selecione o arquivo do jogo.
4. Certifique-se de ativar o motor de simulação em `Simulate > Simulation Enabled` (`Ctrl + E`) e ligar os pulsos de clock em `Simulate > Ticks Enabled` (`Ctrl + K`).

---
*Circuito digital autoral projetado, depurado e otimizado com foco em alta fidelidade lógica e blindagem contra falhas.*
