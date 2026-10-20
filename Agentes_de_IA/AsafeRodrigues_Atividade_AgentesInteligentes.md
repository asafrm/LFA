# Atividade sobre agentes inteligentes

Aula 20/10/2026 | Professora Kadidja Valéria | Inteligência artificial

**Disciplina:** Linguagens Formais e Autômatos | Ciência da Computação

**Estudante:** Asafe Rodrigues Marinho | **Turma:** N1

Realize os exercícios 2.3, 2.4 e 2.5 do Capítulo 2 sobre agentes inteligentes. Analise a racionalidade, descreva ambientes de tarefa por meio do modelo PEAS e explique os conceitos com suas próprias palavras. Utilize o capítulo disponibilizado e justifique suas respostas.

**Modalidade sugerida:** individual com consulta. **Tempo estimado:** 2h30. **Prazo:** conforme orientação da professora.

## Preparação
Leia os tópicos sobre racionalidade, ambientes e estrutura dos agentes, especialmente a Seção 2.3.2.

## Exercício 2.3
Para cada afirmação, indique V ou F, justifique e forneça exemplo ou contraexemplo. Explicite as hipóteses utilizadas.

### a. Um agente que detecta apenas informações parciais sobre o estado não pode ser perfeitamente racional.

- Julgamento: F
- Justificativa: Racionalidade não significa onisciência ou saber tudo com perfeição. Ser racional é apenas tomar a melhor decisão possível com as informações e percepções que estão disponíveis no momento.
- Exemplo ou contraexemplo: Um jogador de cartas que não enxerga a mão dos oponentes, mas calcula perfeitamente as probabilidades e faz a aposta estatisticamente correta, está sendo plenamente racional, mesmo com visão parcial do jogo.

### b. Existem ambientes de tarefa nos quais nenhum agente reativo puro pode comportar-se racionalmente.

- Julgamento: V
- Justificativa: Se o ambiente não for totalmente visível e a decisão certa depender do passado, um agente sem memória (sem estado interno) não sabe o que acabou de fazer e acaba ficando preso em laços infinitos.
- Exemplo ou contraexemplo: Um robô aspirador que só sabe se o chão atual está limpo ou sujo, mas não tem sensor de localização: se o chão estiver limpo e sua regra fixa for "ir para a direita", ele baterá repetidamente na parede da direita caso já esteja nela, pois não se lembra de onde veio.

### c. Existe um ambiente de tarefa em que todo agente é racional.

- Julgamento: V
- Justificativa: A racionalidade é medida pela nota de desempenho. Se o ambiente for configurado para dar a mesma pontuação máxima (ou a mesma nota fixa) independentemente do que seja feito, qualquer comportamento será ótimo.
- Exemplo ou contraexemplo: Um ambiente onde a regra de pontuação atribui nota 0 para qualquer ação que o agente execute, ou um cenário onde apertar qualquer botão confere nota máxima com 100% de sucesso.

### d. A entrada para o programa de agente é a mesma que a entrada para a função de agente.

- Julgamento: F
- Justificativa: A função de agente é a fórmula matemática abstrata que considera todo o histórico de percepções acumuladas desde o início ($f: P^* \to A$). Já o programa de agente é o código real executado na máquina, e ele recebe fisicamente apenas a percepção imediata do instante atual.
- Exemplo ou contraexemplo: O programa `executar(percepcao_atual)` recebe somente a leitura sensorial deste segundo, enquanto a função teórica $f([p_1, p_2, \dots, p_t])$ recebe a lista inteira de leituras passadas.

### e. Toda função de agente é implementável por uma combinação de programa/máquina.

- Julgamento: F
- Justificativa: Existem problemas matemáticos que nenhum computador físico consegue resolver (problemas indecidíveis de computação) e funções que exigiriam tempo de cálculo ou capacidade de memória infinitos.
- Exemplo ou contraexemplo: Uma função matemática de agente que exigisse solucionar o "Problema da Parada" de Alan Turing (prever com certeza absoluta se um programa genérico qualquer irá travar em loop infinito antes de rodar) não pode ser implementada em nenhum computador real.

### f. Suponha que um agente selecione sua ação uniformemente ao acaso do conjunto de ações possíveis. Existe um ambiente de tarefa determinista em que esse agente é racional.

- Julgamento: V
- Justificativa: Se todas as opções de ação disponíveis gerarem exatamente o mesmo resultado excelente, agir no cara ou coroa é tão eficiente e racional quanto pensar muito.
- Exemplo ou contraexemplo: Uma sala com duas portas abertas que levam exatamente à mesma saída e dão a mesma pontuação máxima; escolher qualquer uma das portas ao acaso garante a nota máxima com certeza.

### g. É possível para um dado agente ser perfeitamente racional em dois ambientes de tarefa distintos.

- Julgamento: V
- Justificativa: Um mesmo conjunto de regras pode ser a escolha ideal em ambientes diferentes que compartilhem dinâmicas compatíveis.
- Exemplo ou contraexemplo: Um aspirador com a regra "se estiver sujo, limpe; se estiver limpo, mude de sala" tem desempenho ótimo tanto em um ambiente onde apenas a sala B começa suja, quanto em outro onde ambas as salas começam sujas.

### h. Todo agente é racional em um ambiente não observável.

- Julgamento: F
- Justificativa: Mesmo sem enxergar nada (sem sensores), um agente racional pode usar o conhecimento das regras para planejar uma sequência cega de passos que funcione com certeza. Um agente que agir sem critério continuará tendo desempenho ruim.
- Exemplo ou contraexemplo: Em um mundo de aspirador sem sensores, o agente que executa a sequência fixa `[Aspirar, Andar para o lado, Aspirar]` limpa tudo com certeza; já um agente que escolhe `[Ficar Parado]` não limpa nada e é claramente irracional.

### i. Um agente jogador de pôquer perfeitamente racional nunca perde.

- Julgamento: F
- Justificativa: A racionalidade escolhe a jogada mais inteligente estatisticamente, mas não controla a sorte do embaralhamento nem as cartas escondidas dos adversários.
- Exemplo ou contraexemplo: Um jogador com 98% de chance de vitória aposta corretamente todas as fichas. Se a carta improvável de 2% de chance do oponente sair na mesa por puro azar, o jogador racional perde a partida mesmo tendo tomado a melhor decisão.

---

## Exercício 2.4
Para cada caso, delimite o agente, preencha o PEAS e justifique todas as classificações. Considere Titã como cenário hipotético do exercício.

### Caso 1 — Jogar futebol.

- Agente analisado: Um jogador robótico individual de linha atuando em campo regulamentar.
- Objetivo e hipóteses: Cooperar com os companheiros de time, respeitar as regras da arbitragem, conduzir/passar a bola e marcar gols na meta adversária.
- P — Medida de desempenho: Gols marcados a favor, gols sofridos contra, precisão nos passes e desarmes, tempo de posse de bola e vitória da equipe.
- E — Ambiente: Campo de futebol gramado com demarcações e traves, bola, 10 companheiros de equipe, 11 adversários, arbitragem e intempéries climáticas.
- A — Atuadores: Motores/servos nas pernas e articulações para locomoção e corrida, atuadores para chutes e desarmes, sistema de rádio para comunicação entre jogadores.
- S — Sensores: Câmeras digitais de alta taxa de quadros (visão computacional), sensores inerciais (IMU com giroscópio e acelerômetro), sensores de toque nos membros e antena de localização em campo.

| Propriedade | Classificação | Justificativa |
|---|---|---|
| Observabilidade | Parcialmente observável | O jogador não enxerga todo o campo ao mesmo tempo, existindo pontos cegos e oclusões causadas pelo corpo de outros atletas. |
| Número de agentes | Multiagente (cooperativo e competitivo) | Há colaboração com os colegas de equipe para a estratégia tática e oposição antagônica direta contra o time adversário. |
| Previsibilidade | Estocástico | A dinâmica da bola sofre desvios físicos e o comportamento dos outros jogadores não pode ser previsto com precisão determinística. |
| Dependência entre decisões | Sequencial | Uma decisão tomada no presente (como um passe errado ou posicionamento tático) afeta as rodadas seguintes e o desfecho da partida. |
| Mudança durante a decisão | Dinâmico | Os demais jogadores e a bola continuam em movimento contínuo enquanto o robô processa e toma sua decisão. |
| Natureza dos elementos | Contínuo | Coordenadas de posicionamento, velocidade, aceleração articular, força do chute e fluxo temporal variam de forma contínua. |
| Conhecimento do funcionamento | Conhecido | As regras oficiais do jogo de futebol e as leis da mecânica clássica de movimento são conhecidas previamente. |

---

### Caso 2 — Explorar os oceanos subterrâneos de Titã.

- Agente analisado: Submarino/sonda robótica autônoma de exploração planetária.
- Objetivo e hipóteses: Explorar águas oceânicas subglaciais em Titã, coletar dados geoquímicos e batimétricos, buscar bioassinaturas e preservar sua fonte de energia sob comunicação nula com a Terra.
- P — Medida de desempenho: Volume e relevância dos dados científicos coletados, área subaquática mapeada, integridade do casco e preservação da energia útil.
- E — Ambiente: Oceano subterrâneo sob grossa crosta de gelo em Titã, ausência de luz solar, altas pressões hidrostáticas, fendas minerais e correntes de amônia/água.
- A — Atuadores: Hélices/propulsores direcionais subaquáticos, lemes, braço manipulador para amostragem física e transmissor acústico subaquático.
- S — Sensores: Sonar ativo/passivo de alta resolução, ecobatímetro, sensores de temperatura, pressão e condutividade, espectrômetro de massa e giroscópios.

| Propriedade | Classificação | Justificativa |
|---|---|---|
| Observabilidade | Parcialmente observável | O alcance dos sonares e feixes ópticos é limitado pelas águas escuras e turvas, cobrindo apenas o entorno imediato. |
| Número de agentes | Agente único | A sonda opera isolada no oceano subglacial, sem a presença de outros agentes inteligentes artificiais ou concorrentes. |
| Previsibilidade | Estocástico | O comportamento de correntes marítimas e deslizamentos no assoalho subaquático envolve incerteza probabilística. |
| Dependência entre decisões | Sequencial | As escolhas de percurso e gasto energético impactam a integridade e as missões que a sonda poderá realizar adiante. |
| Mudança durante a decisão | Dinâmico | As correntes e a própria inércia do veículo no meio aquático movem a sonda enquanto ela computa suas decisões. |
| Natureza dos elementos | Contínuo | Profundidade, velocidade do fluxo, temperatura e orientação espacial variam continuamente. |
| Conhecimento do funcionamento | Desconhecido | A topografia detalhada, hidrodinâmica e reações químicas do oceano profundo de Titã precisam ser aprendidas empiricamente pela sonda. |

---

### Caso 3 — Comprar livros usados de IA na Internet.

- Agente analisado: Agente de software de compras automáticas (*softbot*).
- Objetivo e hipóteses: Encontrar e comprar títulos específicos de livros usados de IA pelo menor valor total possível (preço somado ao frete), em condições de leitura adequadas.
- P — Medida de desempenho: Minimização dos gastos monetários totais, integridade/estado de conservação do livro, rapidez na entrega e sucesso da transação.
- E — Ambiente: Lojas virtuais e sebos online, páginas da Web, plataformas de e-commerce, servidores de pagamento e serviços postais.
- A — Atuadores: Emissão de requisições de rede (HTTP GET/POST), preenchimento automático de formulários de compra, envio de ordens de pagamento e mensagens aos livreiros.
- S — Sensores: Páginas HTML processadas, APIs de catálogo e preço, confirmações de resposta bancária e alertas de feeds de estoque.

| Propriedade | Classificação | Justificativa |
|---|---|---|
| Observabilidade | Parcialmente observável | O agente lê as páginas web, mas não tem como inspecionar diretamente o estado físico das páginas do livro nem auditar o estoque real físico do livreiro. |
| Número de agentes | Multiagente (competitivo e cooperativo) | Coopera com os servidores das lojas e compete com outros compradores que buscam simultaneamente exemplares únicos a preços baixos. |
| Previsibilidade | Estocástico | O estoque pode esgotar subitamente e preços podem ser reajustados sem aviso no intervalo entre a checagem e o fechamento da compra. |
| Dependência entre decisões | Sequencial | Efetivar a compra consome parte do orçamento monetário disponível, restringindo compras de outros títulos nas rodadas seguintes. |
| Mudança durante a decisão | Dinâmico | Preços e disponibilidade dos itens sofrem alterações em tempo real causadas por terceiros enquanto o agente compara opções. |
| Natureza dos elementos | Discreto | As páginas web, preços monetários em centavos, números de ISBN e ações de clique são representados por entidades discretas. |
| Conhecimento do funcionamento | Conhecido | Os protocolos de navegação (HTTP), APIs e fluxos transacionais de comércio eletrônico são conhecidos e especificados. |

---

### Caso 4 — Jogar uma partida de tênis.

- Agente analisado: Robô tenista autônomo em quadra regulamentar.
- Objetivo e hipóteses: Devolver a bola de tênis por cima da rede dentro dos limites da quadra adversária, acumulando pontos até vencer os sets.
- P — Medida de desempenho: Pontos, games e sets vencidos; minimização de erros não forçados e regularidade de saque.
- E — Ambiente: Quadra de tênis com rede e demarcações, raquete, bola de tênis, adversário e condições ambientais de vento e luminosidade.
- A — Atuadores: Motores de esteira ou pernas robóticas para deslocamento rápido de base e braço mecânico para empunhadura e execução de golpes.
- S — Sensores: Câmeras de rastreamento estereoscópico de alta frequência (visão computacional), sensores de impacto na raquete e acelerômetros/IMU.

| Propriedade | Classificação | Justificativa |
|---|---|---|
| Observabilidade | Completamente observável | A quadra, a bola e a posição corporal do adversário permanecem diretamente acessíveis aos sensores visuais e inerciais. |
| Número de agentes | Multiagente (competitivo) | O adversário é um agente deliberativo com objetivo antagônico em um jogo de soma zero. |
| Previsibilidade | Estocástico | O comportamento do quique no solo, a resistência do ar e os golpes desferidos pelo oponente contêm incerteza inerente. |
| Dependência entre decisões | Sequencial | A forma como a bola é rebatida determina o posicionamento do agente e o tempo de reação disponível para as próximas jogadas. |
| Mudança durante a decisão | Dinâmico | A bola se desloca velozmente pelo ar enquanto os algoritmos de cinemática computam o ponto de impacto. |
| Natureza dos elementos | Contínuo | Ângulos do braço mecânico, rotação (*spin*), aceleração da bola e tempo variam de forma contínua. |
| Conhecimento do funcionamento | Conhecido | As regras formais do esporte e a mecânica newtoniana de colisões e gravidade são conhecidas a priori. |

---

### Caso 5 — Praticar tênis contra uma parede.

- Agente analisado: Robô tenista autônomo em regime de treinamento solo.
- Objetivo e hipóteses: Sustentar uma sequência ininterrupta de devoluções de bola contra um paredão vertical rígido, treinando tempo de reação e precisão.
- P — Medida de desempenho: Número consecutivo de rebatidas válidas sem deixar a bola cair, consistência de ritmo e precisão na área da parede.
- E — Ambiente: Parede plana e rígida, chão da quadra de treino, bola de tênis e raquete.
- A — Atuadores: Base motora para deslocamento de posicionamento e atuadores elétricos do braço mecânico para golpes.
- S — Sensores: Câmeras de rastreamento visual rápido da trajetória da bola e sensores inerciais na raquete.

| Propriedade | Classificação | Justificativa |
|---|---|---|
| Observabilidade | Completamente observável | O ambiente é compacto e controlado, permitindo acesso total ao estado da bola e da quadra a cada instante. |
| Número de agentes | Agente único | A parede não é um agente deliberativo, mas um corpo inanimado que apenas reflete a bola segundo as leis da mecânica. |
| Previsibilidade | Determinístico (ou fracamente estocástico por atrito) | O rebote na parede plana decorre da força e do ângulo aplicados pelo próprio robô, sendo diretamente previsível pelas leis de choque elástico. |
| Dependência entre decisões | Sequencial | Cada golpe dado impõe a trajetória que exigirá uma nova correção motora e novo golpe no ciclo seguinte. |
| Mudança durante a decisão | Dinâmico | A bola ricocheteia e voa em direção ao robô continuamente enquanto ele prepara o golpe. |
| Natureza dos elementos | Contínuo | Grandezas cinemáticas como velocidade vetorial, ângulo de batida e coordenadas espaciais comportam-se de forma contínua. |
| Conhecimento do funcionamento | Conhecido | O comportamento da gravidade e as fórmulas de reflexão de impacto rígido são plenamente conhecidos. |

---

### Caso 6 — Realizar um salto de altura.

- Agente analisado: Robô atleta saltador.
- Objetivo e hipóteses: Realizar a corrida de aproximação, impulsionar o corpo e transpor um sarrafo na altura máxima possível sem derrubá-lo, caindo no colchão.
- P — Medida de desempenho: Altura em metros do sarrafo superada sem derrubada, integridade estrutural e cumprimento das tentativas regulamentares.
- E — Ambiente: Pista semicircular de corrida, dois postes com sarrafo horizontal móvel e colchão de absorção de queda.
- A — Atuadores: Atuadores hidráulicos/motores potentes nas pernas para impulsão vertical e articulações de arqueamento do tronco (*Fosbury flop*).
- S — Sensores: Sensores a laser/LIDAR ou câmeras para distância até o sarrafo, células de carga nos pés e unidades de medição inercial (IMU).

| Propriedade | Classificação | Justificativa |
|---|---|---|
| Observabilidade | Completamente observável | A altura da barra, o ponto de partida e o posicionamento da pista estão visíveis ao robô. |
| Número de agentes | Agente único | Durante a execução do salto, não há outros agentes competindo nem interferindo fisicamente no aparelho do salto. |
| Previsibilidade | Determinístico (com baixo ruído de vento) | A trajetória parabólica do centro de massa e o arqueamento do corpo decorrem das equações newtonianas de impulso e momento. |
| Dependência entre decisões | Sequencial | A velocidade acumulada na corrida de aproximação condiciona diretamente o ângulo de impulsão e o sucesso na transposição do sarrafo. |
| Mudança durante a decisão | Dinâmico | O robô se move em velocidade em direção à barra durante o processamento do instante da decolagem. |
| Natureza dos elementos | Contínuo | Posição no espaço tridimensional, velocidade, aceleração articular e gravidade são contínuos. |
| Conhecimento do funcionamento | Conhecido | As equações da física de alavancas articulares e a mecânica balística são conhecidas a priori. |

---

### Caso 7 — Participar de um leilão de um item, realizando lances.

- Agente analisado: Agente de software licitante (*bidding agent*).
- Objetivo e hipóteses: Arrematar o item leiloado pagando um valor inferior à sua avaliação máxima interna (preço de reserva).
- P — Medida de desempenho: Margem de lucro (diferença positiva entre a valoração subjetiva do bem e o valor final pago) e taxa de lances vitoriosos sem sobrepreço.
- E — Ambiente: Plataforma de leilão digital, leiloeiro oficial (ou sistema automatizado), concorrentes e item à venda.
- A — Atuadores: Mensagens eletrônicas contendo novos lances numéricos ou comando formal de desistência/passar a rodada.
- S — Sensores: Leitura de dados do maior lance atual, rodada corrente, temporizador de encerramento e notificações do leiloeiro.

| Propriedade | Classificação | Justificativa |
|---|---|---|
| Observabilidade | Parcialmente observável | O agente tem acesso aos lances já tornados públicos, mas não sabe as avaliações de reserva nem os orçamentos ocultos dos concorrentes. |
| Número de agentes | Multiagente (competitivo) | Outros participantes tomam decisões estratégicas concorrentes para arrematar o mesmo bem. |
| Previsibilidade | Estocástico | A chegada de novos lances de concorrentes é incerta e probabilística sob a perspectiva do agente. |
| Dependência entre decisões | Sequencial | Cada lance submetido altera o piso de preços para as rodadas seguintes e compromete o capital disponível. |
| Mudança durante a decisão | Dinâmico | O cronômetro corre e lances de rivais podem ingressar no sistema enquanto o agente avalia se deve cobrir a oferta. |
| Natureza dos elementos | Discreto | Os lances sobem em incrementos monetários predefinidos e o leilão transcorre em rodadas ou intervalos pontuais. |
| Conhecimento do funcionamento | Conhecido | As regras do leilão (critérios de incremento, encerramento do pregão e comissões) são previamente especificadas. |

---

### Comparação final
1. **O que muda entre jogar tênis contra outra pessoa e praticar contra uma parede?**  
   Muda fundamentalmente o **número de agentes** e a **previsibilidade**: a partida contra outra pessoa é um ambiente **multiagente competitivo**, em que o oponente tenta maximizar o próprio ganho minimizando o do agente (impondo imprevisibilidade e comportamento estratégico). Contra a parede, o ambiente é de **agente único**, e a parede comporta-se como um objeto inanimado governado estritamente pelas leis da mecânica clássica de reflexão física elástica.
2. **Por que comprar livros usados pode exigir decisões com informações incompletas?**  
   Porque o ambiente é **parcialmente observável**: o agente de software tem acesso apenas ao texto e fotos postados pelo vendedor, mas desconhece avarias internas ocultas nas páginas (como mofo, grifos ou fragilidade da lombada), além de não ter como verificar a acurácia do estoque real físico nem a confiabilidade da logística postal de terceiros.
3. **Como outros agentes influenciam futebol e leilões?**  
   No futebol, a influência é mista e dinâmica no plano físico: coopera-se com colegas de equipe por meio de passes e posicionamento tático, ao mesmo tempo em que se disputa espaço e bola contra adversários. No leilão, a influência é estratégica e psicológica no plano da teoria dos jogos: concorrentes tentam superar as ofertas uns dos outros sem demonstrar seu valor teto, forçando o agente a recalcular seu lance esperado sob o risco de pagar mais do que o item realmente vale.

---

## Exercício 2.5
Defina cada termo com suas palavras em duas a quatro linhas e apresente um exemplo.

### Agente
- Definição: Entidade capaz de perceber o meio em que está inserida por meio de dispositivos sensores e de produzir transformações sobre ele por meio de atuadores.
- Exemplo: Um termostato eletrônico que afere a temperatura da sala e aciona ou desliga a ventoinha do ar-condicionado.

### Função de agente
- Definição: Mapeamento matemático abstrato formal que associa qualquer sequência histórica completa de percepções recebidas pelo agente a uma ação específica ($f: P^* \to A$).
- Exemplo: Uma tabela matemática que estipula formalmente que a sequência de leituras `[(Sala A, Suja), (Sala A, Limpa)]` deve conduzir à ação de ir para a direita.

### Programa de agente
- Definição: Implementação computacional real da função de agente que executa sobre uma arquitetura de máquina concreta, recebendo a percepção sensorial atual para escolher a ação.
- Exemplo: Um código em Python executando em uma placa controladora que lê valores de sensores e envia sinais PWM para os servomotores.

### Racionalidade
- Definição: Princípio de tomada de decisão no qual o agente escolhe, a cada passo, a ação que maximiza o valor esperado de sua medida de desempenho, com base em suas percepções e conhecimento prévio.
- Exemplo: Um software de roteamento GPS que escolhe o caminho que minimiza o tempo provável de viagem dadas as condições atuais de tráfego.

### Autonomia
- Definição: Propriedade do agente de pautar suas decisões por sua própria experiência e aprendizado com o ambiente, compensando limitações do conhecimento prévio inserido pelo projetista.
- Exemplo: Um robô aspirador de pó que mapeia autonomamente os cômodos de uma casa desconhecida em vez de exigir uma planta pré-programada.

### Agente reativo
- Definição: Agente cuja decisão fundamenta-se exclusivamente na percepção sensorial imediata do presente, descartando o histórico pregresso por meio de regras diretas do tipo condição-ação.
- Exemplo: Uma porta automática de shopping center que aciona os motores de abertura sempre que o sensor de presença detecta alguém se aproximando.

### Agente baseado em modelo
- Definição: Agente que mantém uma representação de estado interno (memória) para rastrear aspectos ocultos do mundo, usando regras de como o ambiente evolui e de como suas ações afetam o meio.
- Exemplo: O piloto automático de um veículo que mantém guardada a posição de um carro ao lado mesmo quando este entra temporariamente no ponto cego do retrovisor.

### Agente baseado em objetivos
- Definição: Agente que avalia o estado do mundo e utiliza a representação explícita de uma meta desejada para planejar ou buscar uma sequência ordenada de ações que permita atingi-la.
- Exemplo: Um algoritmo de GPS que traça uma sequência de conversões de ruas com a meta final explícita de chegar ao endereço solicitado.

### Agente baseado em utilidade
- Definição: Agente que utiliza uma função de utilidade real contínua que mensura graus de satisfação entre múltiplos estados finais, balanceando compromissos conflitantes sob incerteza.
- Exemplo: Um sistema financeiro de alocação de investimentos que balanceia o lucro potencial esperado contra a tolerância ao risco de prejuízo.

### Agente com aprendizagem
- Definição: Arquitetura modular separada entre elemento de desempenho e elemento de aprendizado, auxiliada por um crítico e um gerador de problemas para otimizar sua tomada de decisão com a experiência.
- Exemplo: Um classificador de spam de e-mails que reajusta seus pesos estatísticos sempre que o usuário marca manualmente uma mensagem como indesejada.

---

## Síntese com autômatos
Escolha um caso do item 2.4. Apresente três estados internos, três percepções, três ações e duas regras no formato estado atual + percepção → próximo estado e ação. Explique como estados internos representam informação passada e cite uma limitação da simplificação.

**Caso selecionado:** Caso 5 — *Praticar tênis contra uma parede*.

### Elementos do Autômato (Máquina de Mealy):
* **3 Estados Internos ($S$):**
  1. $q_0$: *Aguardando Rebote* (robô posicionado no centro da quadra após bater, esperando o retorno da bola vinda da parede).
  2. $q_1$: *Em Posicionamento* (robô detectou o retorno da bola e desloca a base preparando a raquete).
  3. $q_2$: *Executando Golpe* (robô atinge o ponto de interceptação e engatilha o movimento da raquete).

* **3 Percepções dos Sensores ($\Sigma$):**
  1. $p_1$: `bola_em_retorno` (visão computacional detecta a bola vindo em alta velocidade em direção à quadra).
  2. $p_2$: `bola_na_zona_de_impacto` (sensores de proximidade/visão acusam a bola na distância de alcance da raquete).
  3. $p_3$: `posicao_base_recuperada` (sensores de odometria confirmam que o robô centralizou-se na quadra).

* **3 Ações dos Atuadores ($\Gamma$):**
  1. $a_1$: `deslocar_para_trajetoria` (mover base de tração para interceptar a linha de voo da bola).
  2. $a_2$: `golpear_forehand` (acionar servomotores do braço mecânico para rebater a bola com velocidade contra a parede).
  3. $a_3$: `retornar_ao_centro` (comandar motores para reposicionar a base no centro da quadra).

* **2 Regras de Transição (Formato: Estado Atual + Percepção $\to$ Próximo Estado + Ação):**
  * **Regra 1:**
    $$\langle q_0, p_1 \rangle \longrightarrow \langle q_1, a_1 \rangle$$
    *Se o robô está em $q_0$ (Aguardando Rebote) e percebe $p_1$ (`bola_em_retorno`), ele transita para $q_1$ (Em Posicionamento) e executa a ação $a_1$ (`deslocar_para_trajetoria`).*
  * **Regra 2:**
    $$\langle q_1, p_2 \rangle \longrightarrow \langle q_2, a_2 \rangle$$
    *Se o robô está em $q_1$ (Em Posicionamento) e percebe $p_2$ (`bola_na_zona_de_impacto`), ele transita para $q_2$ (Executando Golpe) e executa a ação $a_2$ (`golpear_forehand`).*

### Explicação do Histórico e Limitação:
* **Como o estado interno representa informação passada:** O estado interno sintetiza de modo compacto o histórico anterior de percepções. Por exemplo, estar no estado $q_1$ condensa o conhecimento de que a bola já tocou na parede anteriormente e está em rota de descida em direção ao robô. Graças a essa memória sintetizada, no momento em que o robô recebe a percepção $p_2$, ele não precisa reprocessar os quadros de vídeo passados para saber se deve bater ou aguardar: o estado interno já preserva o contexto necessário para acionar a ação adequada no tempo correto.
* **Limitação dessa simplificação:** O modelo de autômato finito trata grandezas dinâmicas de forma puramente discreta e determinística. No tênis real, fatores contínuos e estocásticos — tais como rotação da bola (*topspin*), imperfeições na parede, rajadas de vento e milissegundos de aceleração dos motores — variam continuamente. Tentar mapear essas variáveis contínuas em um conjunto reduzido de estados discretos acarreta perda de precisão motora fina ou explosão combinatória no número de estados.

---

## Referências
Material-base: Capítulo 2 — Agentes inteligentes, disponibilizado para a aula de 19/10/2026.  
Referências adicionais:
1. RUSSELL, Stuart; NORVIG, Peter. *Inteligência Artificial: Uma Abordagem Moderna*. 3. ed. Rio de Janeiro: Elsevier, 2013 (Capítulo 2 — Agentes Inteligentes).
2. HOPCROFT, John E.; MOTWANI, Rajeev; ULLMAN, Jeffrey D. *Introdução à Teoria de Autômatos, Linguagens e Computação*. 2. ed. Rio de Janeiro: Campus, 2002.
