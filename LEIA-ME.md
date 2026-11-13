# Contemplados

Jogo de adedonha (stop) para jogar com amigos no celular e no PC, em um único arquivo: `index.html`. O nome é um trocadilho de consórcio: contemplado é quem leva. As rodadas se chamam assembleias e as salas são numeradas (Sala 1, Sala 2…) por aparelho de quem cria.

## Como funciona

- Quem cria a sala é o **anfitrião**. Os outros entram pelo link (`?sala=CODIGO`) ou digitando o código.
- A comunicação é direta entre os navegadores (WebRTC, pela biblioteca PeerJS). Não há servidor próprio nem banco de dados. O servidor público do PeerJS só apresenta um navegador ao outro.
- O anfitrião precisa manter a página aberta durante toda a partida. Se ele fechar, a sala acaba.
- Sem limite prático de jogadores (teto técnico de 30 por sala). A mesa redonda se ajusta: com mais gente, os bonecos ficam menores.

## Avatares e mesa

- Na tela inicial cada jogador escolhe uma fantasia (Pirata, Astronauta, Vampiro, Unicórnio, Ninja, Chef, Realeza, Alien, Robô, Dino, Mago, Abacaxi) e uma cor. Os bonecos são desenhados em SVG dentro do próprio arquivo, sem imagens externas. A escolha fica salva no aparelho.
- A sala de espera mostra todo mundo sentado numa mesa redonda. Sozinho, aparece uma cadeira "convide!".
- Na revelação, a mesa gira para trazer à frente quem está "falando", e a resposta aparece no centro da mesa.

## Chat

- Balão flutuante no canto inferior direito, em todas as telas depois da entrada. Toque abre um painel pequeno, que não cobre o jogo; o X fecha.
- Mensagem nova com o painel fechado: contador no balão e um aviso curto com o texto por 3,5 segundos. Toque no aviso abre o chat.
- As mensagens passam pelo anfitrião e chegam a todos. Sem histórico para quem entra depois.

## Regras

- 20 categorias padrão (as da imagem do usuário). O anfitrião pode editar a lista na sala de espera, uma por linha.
- Letras sorteadas: A B C D E F G I J L M N O P Q R S T U V. Ficam de fora H, K, W, X, Y e Z. Nenhuma letra repete na partida.
- Tempo: sem tempo, 1, 2, 3 ou 5 minutos por rodada. Nos 10 segundos finais o topo pisca em vermelho e uma contagem regressiva grande aparece na tela. No zero, uma bomba treme, explode com "BUM!" e a revelação começa.
- STOP: "só com tudo preenchido" (padrão) ou "a qualquer momento". A rodada só encerra quando dois jogadores derem STOP (ou um, se o anfitrião mudar a regra). Com tempo, o relógio zerando também encerra.
- Depois do tempo ou do STOP vem a revelação ao vivo, sem a tela rolar: a mesa mostra a resposta de quem está falando no centro, e ao lado (ou embaixo, no celular) fica um cartão fixo da categoria atual, com uma linha por jogador. Ao fechar a categoria, cada linha ganha os pontos com o motivo ("+10 única", "+5 repetida", "0 em branco", "0 letra errada") e cada boneco da mesa ganha um selo com os pontos. O resumo de todas as categorias só aparece no fim da revelação, para anular respostas. Roda sozinha, cerca de 1,3 segundo por resposta. O anfitrião tem Voltar (para na resposta anterior), Pular/Continuar, Mais rápido e Pular tudo.
- Pontos: 10 por resposta válida única, 5 se outra pessoa deu a mesma, 0 em branco, com letra errada ou invalidada. Acento, cedilha e maiúsculas não mudam a palavra ("Natália" e "NATALIA" são iguais).
- Depois da revelação, qualquer um pode marcar uma resposta alheia como inválida. Vale a maioria dos outros jogadores. Resposta que não começa com a letra já é riscada sozinha.
- A pontuação só aparece na tela final, com ranking, títulos e tabela por rodada.
- Comentários engraçados aparecem na sala, no sorteio da letra, no STOP, na conferência e no final.

## Como publicar (para o link funcionar fora do seu computador)

A página precisa estar em um endereço `https://`. Opções gratuitas, sem código:

1. **Netlify Drop**: abra <https://app.netlify.com/drop> e arraste a pasta `adedonha`. Sai um link na hora.
2. **Cloudflare Pages**: no painel, Workers & Pages → Create → Upload assets, envie a pasta.
3. **GitHub Pages**: repositório com o `index.html` e Pages ativado.

Depois, abra o link publicado, crie a sala e mande o link de convite para os amigos.

## Testar no computador

Pré-visualização `adedonha` em `.claude/launch.json` (porta 4177). Abra duas abas: uma cria a sala e a outra entra pelo link.

## Limitações conhecidas

- Em redes móveis muito restritivas, a conexão direta pode falhar (sem servidor TURN). Normalmente funciona em 4G/5G e Wi-Fi.
- Se um jogador recarregar a página no meio da partida, ele perde a vaga até a próxima partida.
- A validade de uma palavra é decidida pelos jogadores na conferência, não por dicionário.
