# Game Design Document (GDD): Ciclo dos Condenados

**Versão:** 0.1 (Edição: Ciclo Contínuo)  
**Autor:** Vinícius Barbosa de Souza  

---

## 1. Informações Gerais
* **Título do Jogo:** Ciclo dos Condenados
* **Gênero:** Action Roguelite / Bullet Hell "Seamless"
* **Plataforma:** Windows / linux / web
* **Público-alvo:** Jogadores hardcore que buscam imersão total e desafio mecânico ininterrupto.

---

## 2. Conceito e Visão Geral
### High Concept
Um bullet hell de alta intensidade onde a morte não é um fim, mas um reinício imediato. Sem menus, sem hubs e sem pausas; apenas o ciclo eterno de combate e evolução.

### Diferenciais (USPs)
* **Experiência Ininterrupta:** Não existe Menu Principal ou Hub. O jogo começa assim que o executável é aberto e a morte lança o jogador instantaneamente na próxima tentativa.
* **Meta-progressão Orgânica:** A evolução permanente ocorre durante a ação, através de encontros raros com o Mercador de Memória.
* **Narrativa de Aprisionamento:** A ausência de "zonas seguras" reforça o sentimento de que o personagem está verdadeiramente condenado ao Reino Metafísico.
* **Drops exclusivos:** Matar inimigos tem uma chance de dropar itens impossiveis de serem comprados.

---

## 3. Jogabilidade e Mecânicas Core
### Os 3Cs
* **Personagem:** Hitbox mínima (2-3 pixels). Movimentação ágil necessária para navegar no caos.
* **Câmera:** Top-down com foco dinâmico no cursor.
* **Controles:** WASD + Mouse. 
    

### O Reinício Instantâneo
Ao zerar a barra de vida, a tela sofre uma distorção visual rápida e o jogador reaparece imediatamente na sala inicial da nova run. Não há telas de "Game Over" ou retorno ao título.

---

## 4. Sistemas e Economia
### Economia Bifurcada em Tempo Real
1.  **Ouro (Volátil):** Coletado de inimigos comuns. Gasto no **Mercador Comum** para itens de cura e melhorias que duram apenas na run atual.
2.  **Fragmentos de Memória (Persistentes):** Obtidos ao derrotar chefes ou inimigos de elite. Esses fragmentos são mantidos mesmo após a morte.

### O Mercador de Memória (Meta-progressão)
* **Ocorrência:** Em vez de um mercador comum, há uma chance de surgir o **Mercador de Memória** em salas de descanso entre biomas.
* **Função:** Ele é o único meio de gastar seus Fragmentos de Memória. 
* **Efeito:** As melhorias compradas aqui são **permanentes** (ex: aumento de vida base, novas habilidades passivas, novos tipos de tiros). 
* **Risco/Decisão:** O jogador precisa sobreviver até encontrar esse mercador raro para "sacar" seu progresso permanente.

---

## 5. Fluxo de Jogo (Game Loop)
1.  **Combate:** Sobreviver e destruir ondas de inimigos.
2.  **Coleta:** Acumular Ouro e Fragmentos de Memória.
3.  **Decisão:** Gastar Ouro para sobreviver mais tempo OU economizar Fragmentos para quando o Mercador de Memória aparecer.
4.  **Morte:** Reinício instantâneo. O progresso em Ouro é perdido, mas os Fragmentos e as melhorias compradas no Mercador de Memória persistem.

---

## 6. História e Narrativa
### A Consciência Aprisionada
* **Trama:** O "Condenado" é uma entidade sem passado, presa em um nexo que devora o tempo. 
* **A Ausência de Hub:** Narrativamente, isso explica por que não há descanso. O mundo não permite que o jogador saia.
* **O Mercador de Memória:** Uma entidade misteriosa que parece ser a única que retém consciência entre os ciclos. Ele troca fragmentos do seu "eu" passado (memórias) por poder, tornando o jogador menos humano e mais uma arma de combate a cada compra.

---

## 7. Aspectos Técnicos
* **Carregamento (Seamless):** O jogo utiliza *Streaming de Níveis* para garantir que a transição entre a morte e a nova run seja inferior a 1 segundo, mantendo o estado de fluxo (*flow*) do jogador.
* **Persistência de Dados:** O jogo salva automaticamente a cada Fragmento de Memória coletado e a cada compra, garantindo que o progresso não seja perdido apesar da ausência de menus de save.



## 8. MECÂNICAS DE JOGO: CICLO DOS CONDENADOS

# Sistema de Ataque
O combate é focado em disparos contínuos e na gestão de energia para habilidades destrutivas.

* Ataque Primário (Disparo de Almas): O personagem realiza disparos lineares constantes em 360 graus, direcionados pela posição do cursor do mouse. A cadência é alta, exigindo que o jogador mantenha o foco no inimigo enquanto se esquiva.
* Ataque Especial (Liberação de Memória): Uma habilidade de alto impacto que consome a barra de energia carregada exclusivamente pela mecânica de Graze. Esta habilidade pode assumir a forma de um feixe de luz concentrado ou uma explosão que anula todos os projéteis inimigos no ecrã.
* Modificadores de Projéteis: Durante a exploração, o jogador encontra itens que alteram o comportamento do disparo primário, adicionando efeitos como ricochete em paredes, tiros que se fragmentam ao atingir alvos ou propriedades de perfuração.

# Mecânica de Graze (Raspar)
O Graze é o sistema central de risco e recompensa que incentiva o jogador a jogar de forma agressiva.

* Zona de Proximidade: Cada projétil inimigo possui uma área ao redor da sua zona de dano. Quando a hitbox do jogador entra nesta área sem ser atingida, o Graze é ativado.
* Geração de Energia: O Graze é a única forma de carregar a barra de Ataque Especial. Quanto mais tempo o jogador passar a "raspar" em projéteis, mais rápido poderá utilizar o seu poder máximo.
* Multiplicador de Recursos: Manter uma sequência de Grazes aumenta o multiplicador de pontuação e a probabilidade de inimigos deixarem cair ouro ao serem derrotados.

# Interação com Cadáveres (Ecos do Ciclo)
A morte não é um reset total, mas uma alteração no ecossistema da tentativa seguinte.

* Marca da Queda: Ao morrer, um cadáver ou túmulo é gerado no local exato da derrota.
* Recuperação de Ouro: O jogador pode interagir com o seu cadáver anterior para recuperar uma percentagem do ouro que transportava na vida passada.
* O Eco Hostil: O cadáver tem uma probabilidade de se reanimar como um "Eco". Este inimigo possui o mesmo nível de poder e os mesmos modificadores de tiro que o jogador tinha quando morreu, criando um desafio personalizado.
* Obtenção de Memórias: Derrotar um Eco garante a queda de Fragmentos de Memória, que são utilizados com o Mercador de Memória para comprar melhorias permanentes.

# Movimentação e Foco
O controlo do personagem é desenhado para precisão absoluta em situações de Bullet Hell.

* Movimentação Base: Deslocação digital em 8 direções (WASD) com aceleração e paragem instantâneas para evitar inércia indesejada.
* Modo de Foco: Ao segurar a tecla Shift, a velocidade de movimento é reduzida em 50%. Durante este modo, a hitbox central do personagem (de 2 a 3 pixels) torna-se visível, permitindo a navegação entre padrões de balas muito densos.
* Dash (Esquiva Rápida): Um movimento curto que garante invulnerabilidade temporária, essencial para atravessar barreiras de projéteis impossíveis de evitar apenas com o movimento normal.