# Game Design Document (GDD): Ciclo dos Condenados

**Versão:** 21.0  
**Autor:** Vinícius Barbosa de Souza  
**Data:** 20/01/2026  

---

## 1. Informações Gerais
* **Título do Jogo:** Ciclo dos Condenados
* **Gênero:** Action Roguelite / Bullet Hell
* **Plataforma:** PC (Windows)
* **Modelo de Negócio:** Premium (Buy-to-Play)
* **Público-alvo:** Jogadores entre 16 e 35 anos, perfil midcore a hardcore que apreciam desafios baseados em habilidade e precisão.

---

## 2. Conceito e Visão Geral
### High Concept
Um jogo single-player de alta intensidade focado em precisão mecânica e persistência narrativa, onde o jogador enfrenta um ciclo perpétuo de combate e renascimento.

### Diferenciais (USPs)
* **Transposição do "Realmlike" para Single Player:** Oferece o caos de jogos como *Realm of the Mad God* sem latência de rede, permitindo padrões de balas mais complexos.
* **Narrativa Recursiva:** A morte é uma mecânica diegética; o mundo guarda memórias das tentativas anteriores, permitindo interagir com os cadáveres das "runs" passadas.
* **Economia Bifurcada:** Decisões constantes entre poder imediato (sobrevivência na run) e poder futuro (meta-progressão).

---

## 3. Jogabilidade e Mecânicas Core
### Mecânica Principal
Sobrevivência Balística em Tempo Real. O jogador deve evitar centenas de projéteis enquanto mantém uma ofensiva constante.

### Os 3Cs
* **Personagem:** Sprite em Pixel Art (16x16). A **Hitbox** real é um núcleo central de apenas 2-3 pixels, permitindo desvios milimétricos.
* **Câmera:** Visão top-down ortogonal (90º) com sistema *Look-Ahead* (desloca-se levemente para a direção da mira).
* **Controles:** Movimentação digital em 8 direções (WASD) e mira analógica 360º (Mouse).
    * *Mecânica de Foco:* Reduz a velocidade em 50% e revela a hitbox para navegação precisa.

### Recursos Especiais
* **Graze Mechanic (Raspar):** Recompensa o jogador por passar perto de projéteis, gerando energia para habilidades.
* **Interação com Cadáveres:** Possibilidade de encontrar o local da última morte para recuperar recursos ou enfrentar um "eco" do jogador anterior.

---

## 4. Sistemas e Economia
### Ciclo de Progressão
* **Ouro (Soft Currency):** Obtido de inimigos, volátil (perdido ao morrer). Usado em lojas dentro da partida para cura e buffs temporários.
* **Fragmentos de Memória (Hard Currency):** Obtidos de Chefes, persistentes após a morte. Usados no Hub para desbloquear novas classes e melhorias permanentes.

### Loops de Jogo
1.  **Micro:** Esquiva e combate rápido (segundos).
2.  **Meso:** Limpeza de salas e escolha de rotas (minutos).
3.  **Macro:** Ciclo de runs, morte e meta-progressão no Hub (horas).

---

## 5. Design de Níveis e Inimigos
* **Inimigos:** Atuam como geradores de padrões (Drones, Artilharia, Espalhadores e Perseguidores).
* **Geração de Níveis:** Sistema procedural híbrido utilizando "chunks" (blocos) desenhados à mão para garantir um fluxo de combate equilibrado.
* **Tutorial:** Integrado organicamente nas primeiras salas, ensinando movimento e ataque sem interromper o fluxo.

---

## 6. Estética e Aspectos Técnicos
* **Estilo Visual:** Pixel Art de alto contraste. Cores quentes/neon para projéteis (perigo) e cores frias para o cenário e jogador (segurança).
* **Game Feel:** Uso de *Hit Stop*, *Screen Shake* e pistas sonoras dinâmicas.
* **Performance:** Arquitetura baseada em *Object Pooling* para sustentar até 2.000 projéteis ativos simultaneamente sem quedas de FPS.

---