Totalmente vibe code, inclusive as instruções a seguir. Mapa interativo para um RPG no universo de Ben 10.

MAPA DA VIA LÁCTEA - COMO EDITAR

PASTAS
- index.html ... a página (não precisa mexer)
- dados/ ....... planetas.json, faccoes.json e config.json
- icones/ ...... um PNG por planeta: o desenho (estrela, planeta, nome, setas)
- imagens/ ..... a imagem de cada planeta, mostrada na cena ao clicar no planeta
- procurados/ .. as imagens dos procurados
- mapa/ ........ fundo.jpg e uma camada PNG por território

A página só exibe as informações; os textos não são editáveis nela. Tudo se altera nos arquivos da pasta dados.

COMO EDITAR
1. Abra dados/planetas.json em qualquer editor de texto, altere e salve.
2. Recarregue a página.
Campos de texto aceitam uma frase ("texto") ou uma lista de linhas (["linha 1", "linha 2"]).

PROCURADOS (com imagem)
O campo "procurados" aceita uma lista. Cada item pode ser um texto simples ou um bloco com nome, descrição e imagem:

  "procurados": [
    {
      "nome": "Fulano",
      "descricao": "Ladrão de naves. Visto pela última vez perto de Pyros.",
      "imagem": "procurados/fulano.png"
    },
    "Beltrana, contrabandista"
  ]

- A imagem fica numa miniatura na guia "Missões e procurados"; ao clicar nela, abre ampliada (clique de novo ou Esc para fechar).
- "descricao" e "imagem" são opcionais. Se o arquivo da imagem não existir, o procurado aparece só com o texto.
- Coloque as imagens na pasta procurados/ (PNG ou JPG). O nome do arquivo é livre; só precisa bater com o caminho no JSON.

POSIÇÃO ("posicao": x e y)
x e y mandam em tudo: o círculo de seleção e o ícone ficam nesse ponto.
Medida usada: o mapa tem 1728 de largura por 1834 de altura (config.json > referencia).
Dica: na página, Shift+clique em qualquer ponto do mapa mostra o x e o y daquele ponto (dentro do botão "Dados").

ÍCONES (pasta icones)
- O PONTO DO PLANETA FICA NO CENTRO EXATO DO PNG. A página coloca o centro do PNG em x,y.
- Escala: o ícone vem no tamanho do seu desenho original. Um PNG com 6000 px de largura cobriria o mapa inteiro (config.json > escala_icones). No seu arquivo de desenho de 7000 x 6368, o mapa ocupa os 6000 px da esquerda.
- O contorno claro em volta do desenho é feito pela página (config.json > contorno: cor, largura em px do PNG e opacidade). Use PNG com fundo transparente e sem contorno.
- Para trocar um desenho: substitua o PNG mantendo o nome e o centro no planeta.

ADICIONAR UM PLANETA
1. Desenhe o ícone e salve o PNG (fundo transparente) com o planeta no centro. Coloque em icones/.
2. Opcional: coloque a imagem do planeta em imagens/. Com imagem, ao clicar o mapa dá zoom com fade e a imagem aparece ao lado do painel. Sem imagem (campo "imagem" vazio ou arquivo inexistente), só dá o zoom.
3. Copie um bloco de dados/planetas.json, mude "id" (único), "nome", "posicao" e os textos, e aponte "icone" e "imagem" para os arquivos.

FACÇÕES (dados/faccoes.json)
Cada facção tem "cor" e, opcionalmente, "territorio" (PNG transparente do mesmo tamanho proporcional do mapa, em mapa/).

COMO USAR
- Hospedado (GitHub Pages, Netlify, Cloudflare Pages ou "python -m http.server" na pasta): a página lê tudo sozinha.
- Abrindo index.html direto do arquivo (sem servidor): o navegador bloqueia a leitura dos JSON. Use "Dados" > "Importar arquivos JSON" e escolha os JSON da pasta dados. Ícones e imagens carregam normalmente.
- Se um JSON tiver erro de sintaxe, a página avisa no botão "Dados" e usa os dados anteriores.

BOTÃO "DADOS"
- Importar arquivos JSON: carrega seus JSON neste aparelho (reconhece planetas, facções e config pelo formato).
- Voltar aos dados originais: descarta o que foi importado neste aparelho.
