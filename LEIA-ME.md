# Adedonha dos Amigos

Jogo de adedonha (stop) para jogar com amigos no celular e no PC, em um único arquivo: `index.html`.

## Como funciona

- Quem cria a sala é o **anfitrião**. Os outros entram pelo link (`?sala=CODIGO`) ou digitando o código.
- A comunicação é direta entre os navegadores (WebRTC, pela biblioteca PeerJS). Não há servidor próprio nem banco de dados. O servidor público do PeerJS só apresenta um navegador ao outro.
- O anfitrião precisa manter a página aberta durante toda a partida. Se ele fechar, a sala acaba.
- Sem limite prático de jogadores (teto técnico de 30 por sala). A mesa redonda se ajusta: com mais gente, os bonecos ficam menores.

## Avatares e mesa

- Na tela inicial cada jogador escolhe uma fantasia (Pirata, Astronauta, Vampiro, Unicórnio, Ninja, Chef, Realeza, Alien, Robô, Dino, Mago, Abacaxi) e uma cor. Os bonecos são desenhados em SVG dentro do próprio arquivo, sem imagens externas. A escolha fica salva no aparelho.
- A sala de espera mostra todo mundo sentado numa mesa redonda. Sozinho, aparece uma cadeira "convide!".
- Na revelação, a mesa gira para trazer à frente quem está "falando", e a resposta aparece no centro da mesa.

## Regras

- 20 categorias padrão (as da imagem do usuário). O anfitrião pode editar a lista na sala de espera, uma por linha.
- Letras sorteadas: A B C D E F G I J L M N O P Q R S T U V. Ficam de fora H, K, W, X, Y e Z. Nenhuma letra repete na partida.
- Tempo: sem tempo, 1, 2, 3 ou 5 minutos por rodada. Com tempo, a rodada acaba no zero ou quando alguém dá STOP.
- STOP: "só com tudo preenchido" (padrão) ou "a qualquer momento". A rodada só encerra quando dois jogadores derem STOP (ou um, se o anfitrião mudar a regra). Com tempo, o relógio zerando também encerra.
- Depois do tempo ou do STOP vem a revelação ao vivo: categoria por categoria, a tela mostra o que cada jogador escreveu ("Lucas colocou em Nome: Pedro"), passa para o próximo e, ao fechar a categoria, já dá os pontos na hora. O anfitrião pode acelerar ou pular a revelação.
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
