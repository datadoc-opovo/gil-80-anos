# Gilberto Gil - 80 anos

Este repositório contém as análises e apurações feitas para a reportagem em alusão ao aniversário de 80 anos de Gilberto Gil, comemorado em 26 de junho de 2022. Produzida em parceria entre a Central de Jornalismo de Dados do O POVO e o Vida & Arte, a matéria foi publicada no O POVO Online e no O POVO+.

![[Gilberto Gil - 80 anos] Nuvem de palavras.png](Gilberto%20Gil%20-%2080%20anos%20a08f11f6ed204b6d842aa15dc518be06/Gilberto_Gil_-_80_anos_Nuvem_de_palavras.png)

## ****Fonte e coleta de dados****

- [Site letras.mus.br](https://www.letras.mus.br/)
- [API do Spotify](https://developer.spotify.com/documentation/web-api/)
- [API do YouTube](https://developers.google.com/youtube/v3/)

Para essa análise, buscou-se dados nas APIs do [Spotify](https://developer.spotify.com/documentation/web-api/) e do [YouTube](https://developers.google.com/youtube/v3/) e por meio da raspagem das letras de músicas do site [letras.mus.br](https://www.letras.mus.br/). Os dados foram coletados em  21/06/2022.

Do site letras.mus.br foram coletadas as letras das músicas de Gilberto Gil. Com esses textos, foram aplicadas técnicas de processamento de linguagem natural, como tokenização, para encontrar os termos mais recorrentes nas canções.

Da API do Spotify foram coletados referentes a: quantidade de seguidores do artista na plataforma; quantidade de álbuns disponíveis; quantidades de músicas em cada álbum; top 10 músicas mais ouvidas; artistas relacionados; países em que os álbuns estão disponíveis; e características das faixas (indicadores como “dançabilidade”, energia, valência etc, definidas pelo próprio Spotify). Algumas informações, como ouvintes mensais, estão disponíveis na página do artista na plataforma.

Por fim, da API do YouTube, foram coletadas as estatísticas do canal (visualizações, número de inscritos e números de vídeos); quantidades de playlists; vídeos de cada playlist e estatísticas por vídeo (quantidade de comentários, likes e visualizações).

## Metodologia

### Nuvem de palavras

Do site letras.mus.br foram coletadas as letras das músicas de Gilberto Gil. Com esses textos, foram aplicadas técnicas de processamento de linguagem natural, como tokenização, para encontrar os termos mais recorrentes nas canções. Para isso, utilizamos a biblioteca Natural Language Toolkit (NLTK).

Na análise, vimos que “Amor” foi o termo mais cantado por Gilberto Gil entre as músicas coletadas nesta análise. O termo está presente em 220 letras das 635 analisadas e é repetido 411 vezes. Em seguida, destacaram-se os termos “dia” (247), “mundo” (224), “coração” (195) e “vida” (188).

Para chegarmos a esses resultados, primeiramente realizamos o web scraping (raspagem) das letras das músicas cadastradas no site letras.mus.br. Ao todo, há 638 músicas no site, mas três são repetidas e foram excluídas.

Dessa forma, consolidamos a amostra de 635 letras musicais em um corpus único. Em seguida , iniciamos a limpeza textual, com a exclusão das stopwords, caracteres especiais e pontuação, e em seguida foi feita a divisão do texto em frases e posteriormente em palavras — ou tokens —, processo chamado de tokenização do corpus.

Do corpus, emergiram 10.072 ocorrências (palavras, formas ou vocábulos) sendo 4.657 palavras se repetem e 5.415 palavras têm uma única ocorrência. Para gerar a visualização da nuvem de palavras, foi feito um filtro que considerou apenas os termos que se repetiram 40 vezes ou mais ao longo do corpus.

### **Spotify**

No Spotify, Gilberto Gil tem 2.632.947 ouvintes mensais e 995.562 seguidores. A popularidade dele na plataforma é 61 — esse valor, que é calculado a partir da popularidade de todas as faixas do artista, varia de 0 e 100; quanto mais próximo de 100, mais popular.

Há, ao todo, 84 álbuns de Gilberto Gil no Spotify, lançados entre 1962 e 2021. Eles estão disponíveis para 181 países, como Singapura, Peru, Paraguai, Costa Rica, Israel e Nova Zelândia, além do Brasil.

Os artistas relacionados a Gil, por ordem decrescente de seguidores na plataforma, são: 'Caetano Veloso',  'Jorge Ben Jor',  'Milton Nascimento',  'Gal Costa',  'Ney Matogrosso',  'Cartola',  'Gonzaguinha',  'Novos Baianos',  'Luiz Melodia',  'Secos & Molhados',  'Elza Soares',  'Paulinho Da Viola',  'João Bosco',  'Chico César',  'Tom Zé',  'Moraes Moreira',  'Wilson Simonal',  'Dorival Caymmi',  'Nara Leão' e  'Jards Macalé'. Ao inserir Gilberto Gil (995.562 seguidores) nessa lista, ele fica em segundo lugar, atrás de Caetano Veloso (1.857.779 seguidores).

Ao todo, a plataforma conta com 1.252 músicas de Gilberto Gil. Destas, 987 são títulos “únicos”, e as outras 265 são títulos repetidos. Ao explorar essas músicas duplicadas, é possível perceber duas situações: ou as faixas estão presentes em álbuns distintos — como a faixa ‘Aquele abraço - Ao vivo’, que aparece em três discos —, ou ocorre de a mesma faixa aparecer no banco de dados com IDs diferentes, mas segmentada por “mercados” (países em que está disponível) diferentes.

[https://lh4.googleusercontent.com/yUwJmpqu8q1olwKrHsHDm5w7aNO_TWD2Mz8rZHmg7vklKOFbYv90oU7H73ywcYMEPviWS9dWDGDbWiqOYnbmxPhCac5HCWqODlQiOzyK7ZUsIxFKLiyvna-8B_I0IGRpOEegJ6TmOvA1ZS9mDw](https://lh4.googleusercontent.com/yUwJmpqu8q1olwKrHsHDm5w7aNO_TWD2Mz8rZHmg7vklKOFbYv90oU7H73ywcYMEPviWS9dWDGDbWiqOYnbmxPhCac5HCWqODlQiOzyK7ZUsIxFKLiyvna-8B_I0IGRpOEegJ6TmOvA1ZS9mDw)

Um exemplo desse último caso é a música ‘São João, Xangô Menino - Ao Vivo'. Como é possível ver na imagem a seguir, as músicas que têm ‘Caetano Veloso’ como artista se referem à mesma faixa, número 9, do disco.

Por conta de situações como essa última, ao selecionar todas as músicas em uma visualização mais adiante, farei um filtro para não utilizar músicas repetidas.

[https://lh6.googleusercontent.com/jPEy4N-7vMXqKrFJwlACPlYM9RWpBZ3BRlNEkwoxYStzgflTrkLCh7Tt7ailU9aD76HJnR63agCX3Uqq3JPBWZyo8KrQm_1b_3kwcLxo_tBvC-ONkcBsE97rvX6HhnJi8Rqu_Jc2N3VCPaB31w](https://lh6.googleusercontent.com/jPEy4N-7vMXqKrFJwlACPlYM9RWpBZ3BRlNEkwoxYStzgflTrkLCh7Tt7ailU9aD76HJnR63agCX3Uqq3JPBWZyo8KrQm_1b_3kwcLxo_tBvC-ONkcBsE97rvX6HhnJi8Rqu_Jc2N3VCPaB31w)

[https://lh5.googleusercontent.com/5lGPpTe8uzqyJhFDO5ZexS4LUxfYMexn3gj1ewgDT-35UbAeuMqGmFl0VUbeAvW1REqm0L-cJWzrXNkgbrlIz-McnfbKwu1a2PsdHEzrpw_7hf88SmQvznzvoJpfpu-5k7b5PgaKSrys7LnG6w](https://lh5.googleusercontent.com/5lGPpTe8uzqyJhFDO5ZexS4LUxfYMexn3gj1ewgDT-35UbAeuMqGmFl0VUbeAvW1REqm0L-cJWzrXNkgbrlIz-McnfbKwu1a2PsdHEzrpw_7hf88SmQvznzvoJpfpu-5k7b5PgaKSrys7LnG6w)

**Top 10 Spotify**

O Top 10 de músicas de Gilberto Gil ou com participação do artista conta com as seguintes faixas: 'Esperando na janela',  'Camarão Que Dorme a Onda Leva',  'Andar com fé',  'Toda Menina Baiana',  'Aos Pés da Cruz',  'Palco',  'É tudo pra ontem',  'Aquele Abraço',  'A paz - Ao vivo' e  'Desde Que O Samba É Samba'.

**Top 10 Audio Features**

O Spotify dispõe de algumas relacionadas a cada música, como “acústica”, “dançabilidade”, “energia” etc, criadas pela própria plataforma. É possível coletar esses dados e observar se esses indicadores estão mais presentes ou ausentes nas faixas. Eles vão de 0 a 1. Quanto mais próximo de 0, menos presente o indicador tende a estar, e quanto mais próximo de 1, maior a probabilidade de a faixa conter aquela característica. Coletamos esses dados, primeiro, para as músicas presentes no Top 10.

![[Gilberto Gil 80 anos] Top 10 - Características das músicas.png](Gilberto%20Gil%20-%2080%20anos%20a08f11f6ed204b6d842aa15dc518be06/Gilberto_Gil_80_anos_Top_10_-_Caractersticas_das_msicas.png)

*A explicação dos indicadores pode ser conferida no seguinte link: [Web API Reference | Spotify for Developers](https://developer.spotify.com/documentation/web-api/reference/#/operations/get-audio-features)*

Na visualização é possível observar os indicadores de cada música do Top 10. Aqui, coloco a **mediana** de cada deles:

[Untitled](https://www.notion.so/c7a0ceac7f2e40bcb0ea2ccedb48f8f2)

Pode-se perceber que as características mais presentes nas 10 músicas de mais destaque no Spotify são “dançabilidade” e valência, mostrando músicas mais “dançantes” e positivas. A instrumentalidade, por outro lado, tende a 0.

Na visualização a seguir, constam os dados das 987 músicas cujos títulos não se repetem.

![[Gilberto Gil 80 anos] Características de 987 músicas de Gilberto Gil disponíveis no Spotify.png](Gilberto%20Gil%20-%2080%20anos%20a08f11f6ed204b6d842aa15dc518be06/Gilberto_Gil_80_anos_Caractersticas_de_987_msicas_de_Gilberto_Gil_disponveis_no_Spotify.png)

Ao reunir as 987 músicas, percebe-se novamente o que foi visto no Top 10. Principalmente em relação a energia e acústica, há uma distribuição mais uniforme das músicas em relação a outras características como instrumentalidade, que se destaca pela concentração em valores próximos a 0 e pela presença mais clara de valores destoantes (caso da faixa ‘Ponta de Areia (vinheta)’, de 45 segundos). Mais da metade das músicas, por outro lado, tendem a ser mais “dançantes” e “positivas”, segundo os indicadores “dançabilidade” e “valência”.

### **YouTube**

No YouTube, o canal de Gilberto Gil soma 95.559.307 visualizações e 413.000 inscritos.

O vídeo com mais visualizações do canal é ‘Gilberto Gil - Respeita Januário, Xote das meninas, Eu só quero um xodó - Fé na Festa Ao Vivo (2010)’, publicado em fevereiro de 2011. Ele conta com 6.061.680 visualizações, 63.557 likes e 1.686 comentários.

Já o vídeo com mais curtidas é ‘Gilberto Gil e Amigos - Andar com Fé | Gil 78 Anos’, de 2020. Ele conta com 78.524 likes, 1.154.600 visualizações e 4.093 comentários. Esse mesmo vídeo, que tem com a participação de familiares e amigos de Gilberto Gil — entre personalidades como Alcione, Caetano Veloso, Djavan, Emicida, Fernanda Montenegro e Chico Buarque — foi a publicação mais comentada do canal do artista.

## Arquivos gerados

### *Dataframes*

- ´df_artistas_relacionados_spotify´: artistas relacionados a Gilberto Gil no Spotify;
- ´df_coleta_letras_gilberto_gil´: letras de música coletadas no letras.mus.br;
- ´df_estatisticas_por_ano_canal_gilberto_gil_youtube´: dados estatísticos do canal no YouTube;
- ´df_nuvem_de_palavras´: total de palavras para nuvem de palavras;
- ´df_nuvem_palavras_40_repeticoes´: nuvem de palavras com termos com pelo menos 40 repetições;
- ´df_top_10´: 10 músicas mais ouvidas no Spotify;
- ´df_top_10_total_gilberto_gil_youtube´: 10 vídeos mais visualizados no YouTube;
- ´df_top10_features_infoviz´: audio features das 10 músicas mais ouvidas no Spotify;
- ´df_total_musicas_features_infoviz_tidy_sem_duplicacao´: audio features de todas as músicas disponíveis no Spotify, sem duplicação.

### *Visualizações*

- [Nuvem de palavras das letras de músicas de Gilberto Gil](https://public.flourish.studio/visualisation/10429229/)
- [Artistas relacionados](https://public.flourish.studio/visualisation/10408575/)
- [Top 10 músicas do Spotify](https://public.flourish.studio/visualisation/10408337/)
- [Top 10 músicas do Spotify - Audio Features](https://public.flourish.studio/visualisation/10407048/)
- [Audio Features todas as músicas no Spotify](https://public.flourish.studio/visualisation/10407657/)
- [Top 10 vídeos com mais likes, visualizações e comentários no YouTube](https://public.flourish.studio/visualisation/10418765/)
- [Comentários, likes e visualizações no YouTube por ano](https://public.flourish.studio/visualisation/10419215/)

---

**Como utilizar:**

Para executar os notebooks, é necessário um ambiente com *Python3* e dependências que podem ser instaladas via [Pip](https://pypi.org/project/pip/):

Coleta das letras de músicas e criação da nuvem de palavras

```python
!pip install pandas
!pip install beautifulsoup4
!pip install urllib3
!pip install nltk
```

Acesso à API do Spotify:

```python
!pip install pandas
!pip install spotipy
```

Acesso à API do YouTube

```python
!pip install pandas
!pip install --upgrade google-api-python-client
```

---

**A Central DATADOC**

A Central de Jornalismo de Dados do O POVO (DATADOC) alia tecnologia e técnicas diversas de análises de dados para produzir um jornalismo de precisão para que você forme sua opinião com segurança. Nosso objetivo é fazer com que todos tenham acesso aos dados utilizados nas notícias que produzimos.

A DATADOC é composta por uma equipe de três jornalistas (sendo uma infografista), uma desenvolvedora front-end e um cientista da computação que coletam, enriquecem e disponibilizam as bases e códigos de cada reportagem para um jornalismo transparente e baseado em evidências.

---

**🔥📰👩🏻‍💻 Se você gostou do nosso material, apoie assinando o OP+ e acompanhando o nosso trabalho.
📝📨 Para feedback, dúvidas ou sugestões: [datadoc@opovodigital.com](mailto:datadoc@opovodigital.com)**

📱🎲**Entre no nosso canal no Telegram: [https://t.me/+Ny9mUUhGUKA4Nzkx](https://t.me/+Ny9mUUhGUKA4Nzkx)**

---

🗓️🕵🏻 Confira também outras produções recentes da central DATADOC: O especial ***#CredosDeFortaleza*** revelou benefícios fiscais indevidos, templos fantasmas e os principais devedores do fisco e está [disponível no O POVO+](https://bit.ly/3gkGPyF).