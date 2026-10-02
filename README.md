# Análise de Performance — Copa do Mundo 2026

## Sobre o projeto

Este projeto foi desenvolvido para analisar dados de jogadores e seleções da Copa do Mundo de 2026.

O objetivo foi conhecer melhor a base, encontrar possíveis problemas, criar comparações e apresentar os resultados de forma simples.

## Fonte dos dados

Foi utilizado um dataset disponível no Kaggle:

`rauffauzanrambe/fifa-world-cup-2026-player-performance-dataset`

O download foi feito pelo Python para que o processo pudesse ser repetido.

O arquivo original possui:

- 54.600 linhas;
- 75 colunas.

## Principais análises

Foram analisados:

- tamanho da base;
- uso de memória;
- valores ausentes;
- tipos de informação;
- nomes e códigos dos jogadores;
- datas e partidas;
- minutos jogados;
- gols, assistências e passes-chave por 90 minutos;
- ranking de gols por 90 minutos;
- resultados agrupados por seleção;
- comparação entre gols e xG;
- notas por posição;
- distância percorrida, sprint e nota dos jogadores.

## Principais problemas encontrados

A base não apresentou valores ausentes nem colunas com um único valor repetido em todas as linhas.

Mesmo assim, alguns pontos precisam de atenção:

- alguns nomes aparecem associados a mais de um código de jogador;
- alguns jogadores aparecem em mais de uma partida no mesmo dia;
- cada jogador aparece associado a muitas partidas;
- os minutos acumulados não acompanham claramente os minutos registrados em cada partida;
- notas iguais a zero aparecem nos registros em que o jogador não entrou em campo;
- os totais de gols, assistências e distância por seleção parecem altos para uma única Copa do Mundo.

Por causa desses pontos, os rankings e totais foram tratados como resultados exploratórios. Eles mostram o que aparece na base, mas não devem ser apresentados como resultados reais confirmados do torneio.

## Principais resultados

O ranking de gols por 90 minutos foi calculado depois de reunir os dados de cada jogador.

Também foi usado um mínimo de 180 minutos acumulados para evitar que uma participação muito curta tivesse um peso exagerado.

A comparação entre os cortes de 180 e 270 minutos apresentou os mesmos 10 jogadores na mesma ordem.

Na comparação entre gols e xG, alguns jogadores marcaram mais gols do que o esperado e outros marcaram menos. Essa diferença, sozinha, não é suficiente para dizer quem é o melhor jogador.

As notas médias foram parecidas entre goleiros, defensores, meio-campistas e atacantes.

A comparação entre distância em sprint e nota apresentou correlação de 0,022. Portanto, não apareceu uma relação clara entre correr mais e receber uma nota maior.

## Gráfico por seleção

O desafio mencionava uma pizza 3D com 24 países.

A base possui 48 seleções. Além disso, uma pizza com muitas partes dificulta a comparação entre os valores.

Por esse motivo, foram escolhidas as 24 seleções com mais registros e foi utilizado um gráfico de barras horizontal, que facilita a leitura.

## Página interativa

Também foi criada uma página HTML para consultar o ranking de jogadores.

A página:

- carrega os dados automaticamente;
- permite escolher uma seleção;
- permite escolher quantos jogadores serão exibidos;
- mostra uma tabela com o ranking;
- apresenta minutos, gols e gols por 90 minutos;
- mostra um gráfico de barras;
- utiliza uma paleta de cores inspirada no Agibank;
- não depende de bibliotecas externas ou CDN.

A página lê o arquivo `ranking_jogadores.json`.

O arquivo JSON foi criado a partir dos dados tratados no notebook. O arquivo Parquet é usado para salvar e conferir a base tratada. Portanto, os dois arquivos têm funções diferentes.

Se os dados do notebook forem alterados, é necessário executar novamente a célula que cria o JSON para atualizar a página.

## Como abrir a página

Abra a pasta do projeto no VS Code.

Depois:

1. Clique com o botão direito em `index.html`.
2. Escolha **Open with Live Server**.
3. A página será aberta no navegador.
4. Os dados serão carregados automaticamente.

## Ajuste ao vivo

Durante a apresentação, será mostrado como a média das notas muda quando são considerados:

- apenas os jogadores que entraram em campo;
- todos os registros, incluindo quem não jogou.

Essa comparação mostra que os registros com nota zero diminuem a média.

## Arquivos do projeto

- `analise_copa_2026.ipynb`: notebook com os códigos, análises e gráficos;
- `ranking_jogadores.json`: dados usados pela página interativa;
- `index.html`: página do ranking;
- `fifa_world_cup_2026_player_performance_tratado.parquet`: base tratada e salva;
- `README.md`: explicação do projeto;
- `LICENSE`: licença do projeto;
- `.gitignore`: arquivos que não devem ser enviados ao Git;
- `requirements.txt`: bibliotecas usadas no notebook.

## Como executar o notebook

1. Abra a pasta do projeto no VS Code.
2. Abra o arquivo `analise_copa_2026.ipynb`.
3. Execute as células na ordem.
4. Ao final, salve o notebook.

O notebook faz o download da base, realiza as análises, cria as novas medidas, salva o arquivo Parquet e gera o arquivo JSON usado pelo front-end.

## Controle de versões

O projeto foi iniciado com Git e possui um primeiro registro das alterações.

O arquivo `.gitignore` impede o envio de:

- arquivos CSV originais;
- credenciais do Kaggle;
- arquivos temporários;
- ambientes virtuais;
- arquivos de sistema.

## Licença

Este projeto utiliza a licença MIT.

A licença permite usar, copiar e adaptar o código, desde que o aviso de autoria seja mantido.

## Limitações

A base apresenta indícios de problemas na relação entre jogadores, partidas, datas e minutos.

Por isso, os resultados devem ser usados como uma análise exploratória dos dados disponíveis.

Antes de usar os resultados como informação oficial do torneio, seria necessário confirmar como a base foi criada e comparar os registros com a fonte original.