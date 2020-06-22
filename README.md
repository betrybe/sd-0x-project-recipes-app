# Boas vindas ao repositório do projeto de Receitas!

Você já usa o GitHub diariamente para desenvolver os exercícios, certo? Agora, para desenvolver os projetos, você deverá seguir as instruções a seguir. Fique atento a cada passo, e se tiver qualquer dúvida, nos envie por _Slack_! #vqv 🚀

Aqui você vai encontrar os detalhes de como estruturar o desenvolvimento do seu projeto a partir desse repositório, utilizando uma branch específica e um _Pull Request_ para colocar seus códigos.

## O que deverá ser desenvolvido

Você irá desenvolver um app de receitas, utilizando o que há de mais moderno dentro do ecossistema React: Hooks e Context API!

Nela será possível ver, buscar, filtrar, favoritar e acompanhar o processo de preparação de receitas e drinks!

A base de dados serão 2 APIs distintas, uma para comidas e outra para bebidas.

O layout tem como foco dispositivos móveis, então todos os protótipos vão estar desenvolvidos em telas menores.

Você pode acessar um protótipo no link abaixo:

https://www.figma.com/file/WatDxtKl7g54QxhDi9qdbq/App-Receitas?node-id=0%3A1

Lembre-se de escrever testes unitários e sinta-se livre para alterar a UI, só respeite os atributos `data-testid`, eles serão usados na correção do exercício.

Você pode ler mais sobre atributos para testes [nesse link](https://www.eduardopedroso.com.br/?p=494)

#### ⚠️ Lembre-se de escrever testes unitários e sinta-se livre para alterar a UI, só respeite os atributos `data-testid`, eles serão usados na correção do exercício.

#### ⚠️ Para ver os comentários sobre cada componente, basta clicar no ícone de comentários no Figma (lado esquerdo superior).

![image](https://res.cloudinary.com/drdpedroso/image/upload/c_scale,w_400/v1575815877/Screenshot_2019-12-08_at_11.37.25_kzt7rl.png)

---

## Desenvolvimento e testes

Este repositório já contem um _template_ com um App React criado, configurado e com os testes automatizados.

Esses [testes E2E](https://www.guru99.com/end-to-end-testing.html) automatizados podem ser utilizados para ajudar a validar as funcionalidades do projeto. Porém, não são pré-requisitos para a avaliação; ou seja, não é necessário que todos esses testes passem. É possível executar os testes localmente via `npm run cy`. Esse comando roda a suite de testes do [Cypress](https://www.cypress.io/how-it-works/) que valida se o fluxo geral e os requisitos funcionais estão funcionando.

Esses testes não consideram o layout de maneira geral, mas sim os atributos e informações corretas, então preste atenção nos atributos definidos no protótipo.

Os testes te darão uma mensagem de erro caso não estejam passando (seja qual for o motivo). 😉

#### Além dos testes automatizados, um dos requisitos do projeto se baseia em **escrever testes unitários que cubram pelo menos 90% do projeto**. Na [documentação do Jest CLI](https://jestjs.io/docs/en/cli) é possível ver como essa cobertura é coletada.

## APIs

### TheMealDB API

O [TheMealDB](https://www.themealdb.com/) é um banco de dados aberto, mantido pela comunidade, com receitas e ingredientes de todo o mundo.

Os end-points são bastante ricos, você pode [vê-los aqui](https://www.themealdb.com/api.php)

O modelo de resposta para uma `meal` é o seguinte:
```json
{
   "meals":[
      {
         "idMeal":"52882",
         "strMeal":"Three Fish Pie",
         "strDrinkAlternate":null,
         "strCategory":"Seafood",
         "strArea":"British",
         "strInstructions":"Preheat the oven to 200C\/400F\/Gas 6 (180C fan).\r\nPut the potatoes into a saucepan of cold salted water. Bring up to the boil and simmer until completely tender. Drain well and then mash with the butter and milk. Add pepper and taste to check the seasoning. Add salt and more pepper if necessary.\r\nFor the fish filling, melt the butter in a saucepan, add the leeks and stir over the heat. Cover with a lid and simmer gently for 10 minutes, or until soft. Measure the flour into a small bowl. Add the wine and whisk together until smooth.\r\nAdd the milk to the leeks, bring to the boil and then add the wine mixture. Stir briskly until thickened. Season and add the parsley and fish. Stir over the heat for two minutes, then spoon into an ovenproof casserole. Scatter over the eggs. Allow to cool until firm.\r\nSpoon the mashed potatoes over the fish mixture and mark with a fork. Sprinkle with cheese.\r\nBake for 30-40 minutes, or until lightly golden-brown on top and bubbling around the edges.",
         "strMealThumb":"https:\/\/www.themealdb.com\/images\/media\/meals\/spswqs1511558697.jpg",
         "strTags":"Fish,Seafood,Dairy,Pie",
         "strYoutube":"https:\/\/www.youtube.com\/watch?v=Ds1Jb8H5Sg8",
         "strIngredient1":"Potatoes",
         "strIngredient2":"Butter",
         "strIngredient3":"Milk",
         "strIngredient4":"Gruy\u00e8re",
         "strIngredient5":"Butter",
         "strIngredient6":"Leek",
         "strIngredient7":"Plain Flour",
         "strIngredient8":"White Wine",
         "strIngredient9":"Milk",
         "strIngredient10":"Parsley",
         "strIngredient11":"Salmon",
         "strIngredient12":"Haddock",
         "strIngredient13":"Smoked Haddock",
         "strIngredient14":"Eggs",
         "strIngredient15":"",
         "strIngredient16":"",
         "strIngredient17":"",
         "strIngredient18":"",
         "strIngredient19":"",
         "strIngredient20":"",
         "strMeasure1":"1kg",
         "strMeasure2":"Knob",
         "strMeasure3":"Dash",
         "strMeasure4":"50g",
         "strMeasure5":"75g",
         "strMeasure6":"2 sliced",
         "strMeasure7":"75g",
         "strMeasure8":"150ml",
         "strMeasure9":"568ml",
         "strMeasure10":"2 tbs chopped",
         "strMeasure11":"250g",
         "strMeasure12":"250g",
         "strMeasure13":"250g",
         "strMeasure14":"6",
         "strMeasure15":"",
         "strMeasure16":"",
         "strMeasure17":"",
         "strMeasure18":"",
         "strMeasure19":"",
         "strMeasure20":"",
         "strSource":"https:\/\/www.bbc.co.uk\/food\/recipes\/three_fish_pie_58875",
         "dateModified":null
      }
   ]
}
```

Os ingredientes seguem uma ordem lógica onde o nome dele (`strIngredient1`) e a quantidade (`strMeasure1`) tem o mesmo número no final (1, nesse caso).

É possível listar todas as `categorias`, `áreas` e `ingredientes`:

```
categorias: https://www.themealdb.com/api/json/v1/1/list.php?c=list
areas: https://www.themealdb.com/api/json/v1/1/list.php?a=list
ingredientes: https://www.themealdb.com/api/json/v1/1/list.php?i=list
```

As fotos dos ingredientes vêm de um end-point padronizado com a seguinte lógica:

```
https://www.themealdb.com/images/ingredients/{nome-do-ingrediente}.png
// exemplo com "lime
https://www.themealdb.com/images/ingredients/Lime.png
```

### The CockTailDB API

Bem similar (inclusive mantida pela mesma entidade) a TheMealDB API, só que focado em bebidas.

Os end-points também são bastante ricos, você pode [vê-los aqui](https://www.thecocktaildb.com/api.php)

As respostas seguem a mesma estrutura, com algumas particularidade relativas as bebidas (como ser ou não alcoólica, por exemplo)

```json
{
   "drinks":[
      {
         "idDrink":"17256",
         "strDrink":"Martinez 2",
         "strDrinkAlternate":null,
         "strDrinkES":null,
         "strDrinkDE":null,
         "strDrinkFR":null,
         "strDrinkZH-HANS":null,
         "strDrinkZH-HANT":null,
         "strTags":null,
         "strVideo":null,
         "strCategory":"Cocktail",
         "strIBA":null,
         "strAlcoholic":"Alcoholic",
         "strGlass":"Cocktail glass",
         "strInstructions":"Add all ingredients to a mixing glass and fill with ice.\r\n\r\nStir until chilled, and strain into a chilled coupe glass.",
         "strInstructionsES":null,
         "strInstructionsDE":"Alle Zutaten in ein Mischglas geben und mit Eis f\u00fcllen. Bis zum Abk\u00fchlen umr\u00fchren und in ein gek\u00fchltes Coup\u00e9glas abseihen.",
         "strInstructionsFR":null,
         "strInstructionsZH-HANS":null,
         "strInstructionsZH-HANT":null,
         "strDrinkThumb":"https:\/\/www.thecocktaildb.com\/images\/media\/drink\/fs6kiq1513708455.jpg",
         "strIngredient1":"Gin",
         "strIngredient2":"Sweet Vermouth",
         "strIngredient3":"Maraschino Liqueur",
         "strIngredient4":"Angostura Bitters",
         "strIngredient5":null,
         "strIngredient6":null,
         "strIngredient7":null,
         "strIngredient8":null,
         "strIngredient9":null,
         "strIngredient10":null,
         "strIngredient11":null,
         "strIngredient12":null,
         "strIngredient13":null,
         "strIngredient14":null,
         "strIngredient15":null,
         "strMeasure1":"1 1\/2 oz",
         "strMeasure2":"1 1\/2 oz",
         "strMeasure3":"1 tsp",
         "strMeasure4":"2 dashes",
         "strMeasure5":null,
         "strMeasure6":null,
         "strMeasure7":null,
         "strMeasure8":null,
         "strMeasure9":null,
         "strMeasure10":null,
         "strMeasure11":null,
         "strMeasure12":null,
         "strMeasure13":null,
         "strMeasure14":null,
         "strMeasure15":null,
         "strCreativeCommonsConfirmed":"No",
         "dateModified":"2017-12-19 18:34:15"
      }
   ]
}
```

Os ingredientes seguem uma ordem lógica onde o nome dele (`strIngredient1`) e a quantidade (`strMeasure1`) tem o mesmo número no final (1, nesse caso).

---

# Requisitos do projeto

⚠️ Lembre-se que o seu projeto só será avaliado se estiver passando pelos _checks_ do **CodeClimate**.

Nesse projeto, a pessoa que estiver utilizando o app pode procurar uma receita especifica, explorar receitas baseado em diferentes critérios, favoritar e fazer as receitas entre outras funcionalidades.

As telas sofrem variações dependendo do tipo da receita (se é comida ou bebida, no caso).

#### O projeto sera composto por duas entregas, cada uma especificada abaixo com seus respectivos requisitos e o prazo decidido com o especialista.

## Requisitos - Apresentação 1

1. A cobertura de testes unitários deve ser de no mínimo 90%;

#### Tela de login

2. Todos os elementos devem respeitar os atributos descritos no protótipo para a tela de login;

3. A pessoa deve conseguir escrever seu email no input de email;

4. A pessoa deve conseguir escrever sua senha no input de senha;

5. O formulário só fica válido após um email válido e uma senha de mais de 6 caracteres serem preenchidos;

6. Caso o formulário esteja inválido, o botão de submeter deve estar desativado. Caso contrário, deve estar ativado;

7. Após a submissão, 2 tokens devem ser salvos em `localStorage` identificados pelas chaves `mealsToken` e `cocktailsToken` (o token de teste é sempre "1");

8. Após a submissão, o e-mail de pessoa usuária deve ser salvo em `localStorage` na chave `user` no formato `{ email: email-da-pessoa }`;

9. Após a submissão e validação com sucesso do login, o usuário deve ser redirecionado para a tela principal de receitas de comidas.

## Header

### 10 - Todos os elementos devem respeitar os atributos descritos no protótipo para o header disponível na tela principal de receitas.

### 11 - Deve apresentar um ícone para a tela de perfil, um título e um ícone para a busca (caso exista no protótipo). Todas as [rotas](#rotas) serão verificadas. Os ícones podem ser encontrados em `src/images/profileIcon.svg` e em `src/images/searchIcon.svg`.

##### As seguintes verificações serão feitas:

- Não tem header na tela de login;
- O header tem os ícones corretos na tela de principal de receitas de comidas;
- O header tem os ícones corretos na tela de principal de receitas de bebidas;
- Não tem header na tela de detalhes de uma receita de comida;
- Não tem header na tela de detalhes de uma receita de bebida;
- Não tem header na tela de receita em processo de comida;
- Não tem header na tela de receita em processo de bebida;
- O header tem os ícones corretos na tela de explorar;
- O header tem os ícones corretos na tela de explorar comidas;
- O header tem os ícones corretos na tela de explorar bebidas;
- O header tem os ícones corretos na tela de explorar comidas por ingrediente;
- O header tem os ícones corretos na tela de explorar bebidas por ingrediente;
- O header tem os ícones corretos na tela de explorar comidas por local de origem;
- O header tem os ícones corretos na tela de perfil;
- O header tem os ícones corretos na tela de receitas feitas;
- O header tem os ícones corretos na tela de receitas favoritas.

### 12 - Ao clicar no botão de perfil, deve-se ir para a tela de perfil.

### 13 - Ao clicar no botão de busca, a barra de busca deve aparecer. O mesmo serve para escondê-la.

##### As seguintes verificações serão feitas:

- Ao clicar no botão de busca pela primeira vez a barra de busca aparece;
- Ao clicar no botão de busca pela segunda vez a barra de busca desaparece.

## Barra de busca - Header

### 14 - Todos os elementos devem respeitar os atributos descritos no protótipo para a barra de busca.

### 15 - A barra de busca deve ficar logo abaixo do header e deve possuir 3 _radio buttons_: `Ingrediente`, `Nome` e `Primeira letra`. Eles devem mudar a forma como serão filtradas as receitas.  Os _endpoints_ da API que você deve usar podem ser consultados [aqui para a API de comidas](https://www.themealdb.com/api.php) e [aqui para a API de bebidas](https://www.thecocktaildb.com/api.php).

##### Exemplo: Ao selecionar `Ingrediente` e buscar por `chicken`, deve-se utilizar o endpoint `https://www.themealdb.com/api/json/v1/1/filter.php?i=chicken`.

##### Observação: Para esse requisito será verificada apenas a tela principal de receitas de comidas.

##### As seguintes verificações serão feitas:

- Se o radio selecionado for `Ingrediente`, a busca na API é feita corretamente pelo ingrediente. O endpoint utilizado deve ser `https://www.themealdb.com/api/json/v1/1/filter.php?i={ingrediente}`;
- Se o radio selecionado for `Nome`, a busca na API é feita corretamente pelo nome. O endpoint utilizado deve ser `https://www.themealdb.com/api/json/v1/1/search.php?s={nome}`;
- Se o radio selecionado for `Primeira letra`, a busca na API é feita corretamente pelo primeira letra. O endpoint utilizado deve ser `https://www.themealdb.com/api/json/v1/1/search.php?f={primeira-letra}`;
- Se o radio selecionado for `Primeira letra` e a busca na API for feita com mais de uma letra, deve-se exibir um `alert` com a mensgem "Sua busca deve conter somente 1 (um) caracter".

### 15 - A busca deve ocorrer 600 milissegundos após a última interação com o input (pesquise por debounce).

##### TODO: substituir por botão de busca, já que o debounce é inviável de testar.

### 16 - A busca deve ocorrer na API de comidas caso a pessoa esteja na página de comidas e na de bebidas caso esteja na de bebidas.

##### Observação: Para esse requisito será verificada apenas a tela principal de receitas de bebidas, já que a de comidas já foi verificada no requisito 15.

##### As seguintes verificações serão feitas:

- Na tela de bebidas, se o radio selecionado for `Ingrediente`, a busca na API é feita corretamente pelo ingrediente. O endpoint utilizado deve ser `https://www.thecocktaildb.com/api/json/v1/1/filter.php?i={ingrediente}`;
- Na tela de bebidas, se o radio selecionado for `Nome`, a busca na API é feita corretamente pelo nome. O endpoint utilizado deve ser `https://www.thecocktaildb.com/api/json/v1/1/search.php?s={nome}`;
- Na tela de bebidas, se o radio selecionado for Primeira letra, a busca na API é feita corretamente pelo primeira letra. O endpoint utilizado deve ser `https://www.thecocktaildb.com/api/json/v1/1/search.php?f={primeira-letra}`;
- Na tela de bebidas, se o radio selecionado for `Primeira letra` e a busca na API for feita com mais de uma letra, deve-se exibir um `alert` com a mensgem "Sua busca deve conter somente 1 (um) caracter".

### 17 - Caso apenas uma receita seja encontrada, a rota deve mudar para a tela de detalhes da receita com o ID da mesma na URL.

##### As seguintes verificações serão feitas:

- Caso apenas uma comida seja encontrada, deve-se ir para sua rota de detalhes (`/comidas/{id-da-receita}`);
- Caso apenas uma bebida seja encontrada, deve-se ir para sua rota de detalhes (`/bebidas/{id-da-receita}`).

### 18 - Caso mais de uma receita seja encontrada, mostrar as receitas em cards da mesma maneira que a tela principal de receitas;

##### As seguintes verificações serão feitas:

- Caso mais de uma comida seja encontrada, mostrar as 12 primeiras (ou menos, se não hoverem 12);
- Caso mais de uma bebida seja encontrada, mostrar as 12 primeiras (ou menos, se não hoverem 12).

### 19 - Caso nenhuma receita seja encontrada, um `alert` contendo o texto "Sinto muito, não encontramos nenhuma receita para esses filtros." deve ser exibido.

##### As seguintes verificações serão feitas:

- Caso nenhuma comida seja encontrada o alert deve ser exibido;
- Caso nenhuma bebida seja encontrada o alert deve ser exibido.

## Menu inferior

### 20 - Todos os elementos devem respeitar os atributos descritos no protótipo para o menu inferior disponível na tela principal de receitas.

### 21 - Deve ser fixo e apresentar 3 ícones: um para comidas, um para bebidas e outro para exploração.

##### As seguintes verificações serão feitas:

- O menu inferior deve ficar fixado sempre ao final da página;
- Apresenta os ícones corretos (drinkIcon.svg, exploreIcon.svg e mealIcon.svg, disponíveis na pasta `src/images/`).

### 22 - O menu inferior só deve aparecer apenas nas telas indicadas pelo protótipo.

##### As seguintes verificações serão feitas:

- Não tem footer na tela de login;
- Tem footer na tela de principal de receitas de comidas;
- Tem footer na tela de principal de receitas de bebidas;
- Não tem footer na tela de detalhes de uma receita de comida;
- Não tem footer na tela de detalhes de uma receita de bebida;
- Não tem footer na tela de receita em processo de comida;
- Não tem footer na tela de receita em processo de bebida;
- Tem footer na tela de explorar;
- Tem footer na tela de explorar comidas;
- Tem footer na tela de explorar bebidas;
- Tem footer na tela de explorar comidas por ingrediente;
- Tem footer na tela de explorar bebidas por ingrediente;
- Tem footer na tela de explorar comidas por local de origem;
- Tem footer na tela de perfil;
- Não tem footer na tela de receitas feitas;
- Não tem footer na tela de receitas favoritas.

### 23 - Ao clicar no ícone de comidas, a pessoa deve ser redirecionada para uma lista de comidas;

### 24 - Ao clicar no ícone de bebidas, a pessoa deve ser redirecionada para uma lista de cocktails;

### 25 - Ao clicar no ícone de exploração, a rota deve mudar para a tela de explorar.

## Tela principal de receitas

### 26 - Todos os elementos devem respeitar os atributos descritos no protótipo para a tela principal de receitas.

##### As seguintes verificações serão feitas:

- A tela tem os data-testids de todos os 12 cards da tela de comidas;
- A tela tem os data-testids de todos os 12 cards da tela de bebidas.

### 27 - Devem ser carregadas as 12 primeiras receitas de comidas ou bebidas, uma em cada card. O Card de receita deve conter sua foto (`strMealThumb` ou `strDrinkThumb`) e seu nome (`strMeal` ou `strDrink`).

##### As seguintes verificações serão feitas:

- Caso as receitas sejam de comida, deve-se carregar as 12 primeiras receitas obtidas através do endpoint `https://www.themealdb.com/api/json/v1/1/search.php?s=`;
- Caso as receitas sejam de bebida, deve-se carregar as 12 primeiras receitas obtidas através do endpoint `https://www.thecocktaildb.com/api/json/v1/1/search.php?s=`.

### 28 - A tela deve possuir botões de categoria para serem utilizados como filtro. Cada um com o atributo prefixado: `data-testid=${categoryName}-category-filter`. Devem ser exibidas apenas as 5 primeiras categorias retornadas da API.

##### As seguintes verificações serão feitas:

- Caso as receitas sejam de comida, deve-se exibir as 5 primeiras categorias de comida obtidas através do endpoint `https://www.themealdb.com/api/json/v1/1/list.php?c=list`;
- Caso as receitas sejam de bebida, deve-se exibir as 5 primeiras categorias de bebida obtidas através do endpoint `https://www.thecocktaildb.com/api/json/v1/1/list.php?c=list`.

### 29 - Ao clicar no filtro de categoria, todas as receitas devem mudar para os dados filtrados da API. As categorias disponíveis devem ser obtidas através da API de [comidas](https://www.themealdb.com/api.php) ou [bebidas](https://www.thecocktaildb.com/api.php).

##### As seguintes verificações serão feitas:

- Caso as receitas sejam de comida e a categoria seja "Beef", deve-se carregar as 12 primeiras receitas de "Beef";
- Caso as receitas sejam de comida e a categoria seja "Breakfast", deve-se carregar as 12 primeiras receitas de "Breakfast";
- Caso as receitas sejam de comida e a categoria seja "Chicken", deve-se carregar as 12 primeiras receitas de "Chicken";
- Caso as receitas sejam de comida e a categoria seja "Dessert", deve-se carregar as 12 primeiras receitas de "Dessert";
- Caso as receitas sejam de comida e a categoria seja "Goat", deve-se carregar as 12 primeiras receitas de "Goat";
- Caso as receitas sejam de bebida e a categoria seja "Ordinary Drink", deve-se carregar as 12 primeiras receitas de "Ordinary Drink";
- Caso as receitas sejam de bebida e a categoria seja "Cocktail", deve-se carregar as 12 primeiras receitas de "Cocktail";
- Caso as receitas sejam de bebida e a categoria seja "Milk / Float / Shake", deve-se carregar as 12 primeiras receitas de "Milk / Float / Shake";
- Caso as receitas sejam de bebida e a categoria seja "Other/Unknown", deve-se carregar as 12 primeiras receitas de "Other/Unknown";
- Caso as receitas sejam de bebida e a categoria seja "Cocoa", deve-se carregar as 12 primeiras receitas de "Cocoa".

### 30 - Caso o filtro selecionado no momento seja selecionado de novo, o app deve retornar as receitas sem nenhum filtro, como se fosse um toggle.

##### As seguintes verificações serão feitas:

- Caso as receitas sejam de comida e o filtro tenha sido selecionado novamente, deve-se retornar as 12 primeiras receitas sem filtro;
- Caso as receitas sejam de bebida e o filtro tenha sido selecionado novamente, deve-se retornar as 12 primeiras receitas sem filtro.

### 31 - Apenas um filtro de categoria deve poder ser selecionado por vez. Ou seja, se outro filtro de categoria for selecionado, ele deve substituir o anterior.

##### As seguintes verificações serão feitas:

- Caso as receitas sejam de comida apenas um filtro de categoria deve poder ser selecionado por vez;
- Caso as receitas sejam de bebida apenas um filtro de categoria deve poder ser selecionado por vez.

### 32 - No filtro de categorias deve existir a opção de filtrar por todas as categorias, retornando novamente todas as receitas. O nome do filtro deve ser "All".

##### As seguintes verificações serão feitas:

- Caso as receitas sejam de comida deve existir a opção de filtrar por todas as categorias;
- Caso as receitas sejam de bebida deve existir a opção de filtrar por todas as categorias.

### 33 - Ao clicar no card, a rota deve mudar para a tela de detalhes da receita com o ID da mesma na URL, além de dizer se a pessoa veio da tela de comidas ou de bebidas. Exemplo: `/comidas/{id-da-receita}`.

##### As seguintes verificações serão feitas:

- Caso as receitas sejam de comida a rota deve mudar para a tela de detalhes da receita;
- Caso as receitas sejam de bebida a rota deve mudar para a tela de detalhes da receita.

#### Tela de detalhes de uma receita

40. Todos os elementos devem respeitar os atributos descritos no protótipo para a tela de detalhes de uma receita;

41. Uma request para a API deve ser feita passando o `id` da receita que deve estar disponível nos parâmetros da URL;

42. Essa tela deve conter uma imagem da receita, o titulo, a categoria (ou se é ou não alcoólico), uma lista de ingredientes seguidos pelas quantidades instruções, um vídeo do youtube "embedado" e recomendações. Obs.: O vídeo do youtube só deve estar disponível para receitas de comida, já que não é retornado pela [API de bebidas](https://www.thecocktaildb.com/api.php);

43. As recomendações para receitas de comida deverão ser bebidas e vice-versa. Obs.: Para simplificar, utilize receitas aleatórias;

44. Deverão ser mostrados 6 cards de recomendação, onde apenas 2 são mostrados e o scroll é horizontal, similar a um `carousel`;

45. Um botão de nome "Iniciar Receita" deve ficar fixo na parte de baixo da tela o tempo todo;

46. Caso a receita já tenha sido feita, o botão "Iniciar Receita" deve sumir;

47. Caso a receita tenha sido iniciada mas não finalizada, o texto do botão deve ser "Continuar Receita";

48. Quando o botão "Iniciar Receita" for clicado, a rota deve mudar para a tela de receita em processo;

49. Um botão de compartilhar e um de favoritar a receita devem estar disponíveis;

50. Ao clicar no botão de compartilhar, o link da receita dentro do app deve ser copiado para o clipboard e uma mensagem avisando que o link foi copiado deve aparecer;

51. O ícone do coração (favorito) deve vir preenchido caso a receita esteja favoritada, e _"despreenchido"_ caso contrário;

52. Ao clicar no botão de favoritar, o ícone do coração deve mudar de seu estado atual, caso esteja preenchido deve mudar para _"despreenchido"_ e vice-versa;

53. As receitas favoritas devem ser salvas em `localStorage` na chave `favoriteRecipes` no formato `[{ id, type, area, category, alcoholic, name, image }]`. E as receitas feitas devem ser salvas em `localStorage` na chave `doneRecipes` no formato `[{ id, type, area, category, alcoholic, name, image, doneDate, tags }]`.

---

## Requisitos - Apresentação 2

54. A cobertura de testes unitários deve ser de no mínimo 90%;

#### Tela de receita em processo

55. Essa tela deve conter uma imagem da receita, seu titulo, sua categoria (ou se a bebida é alcoólica ou não) uma lista de ingredientes com suas respectivas quantidades, e suas instruções;

56. A lista de ingredientes deve conter um checkbox para cada um dos items;

57. Ao clicar no checkbox de um ingrediente, o nome dele deve ser "riscado" da lista;

58. O estado do progresso deve ser mantido caso a pessoa atualize a pagina ou volte para a mesma receita. O progresso das receitas devem ser salvos em `localStorage` na chave `inProggressRecipes` no formato `{ id-da-receita: [lista-de-ingredientes-utilizados], ... }`;

59. A mesma lógica de favoritar e compartilhar da tela de detalhes de uma receita se aplica aqui;

60. O botão de finalizar receita só pode estar habilitado quando todos os ingredientes estiverem _"checkados"_ (marcados);

61. Após clicar no botão "Finalizar receita", a rota deve mudar para a página de receitas feitas, cuja rota deve ser `/receitas-feitas`.

#### Tela de receitas feitas

62. Todos os elementos devem respeitar os atributos descritos no protótipo para a tela de receitas feitas;

63. A tela deve conter cards horizontais, um para cada receita feita;

64. Caso a receita do card seja uma comida, ela deve possuir: a foto da receita, o nome, a categoria, a area, a data em que a pessoa fez a receita, as 2 primeiras tags retornadas pela API e um botão de compartilhar;

65. Caso a receita do card seja uma bebida, ela deve possuir: a foto da receita, o nome, se é alcoólica, a data em que a pessoa fez a receita e um botão de compartilhar;

66. O botão de compartilhar deve copiar a URL da tela de detalhes daquela receita para o clipboard;

67. Devem existir 2 botões que filtram as receitas por comida ou bebida e um terceiro que remove todos os filtros. Os nomes dos botões devem ser "Food", "Drinks" e "All", respectivamente;

68. Ao clicar na foto ou no nome da receita, a rota deve mudar para a tela de detalhes daquela receita;

69. A rota dessa página deve ser `/receitas-feitas`.

#### Tela de receitas favoritas

70. Todos os elementos devem respeitar os atributos descritos no protótipo para a tela de receitas favoritas (cumulativo com os atributos em comum com a tela de receitas feitas);

71. A tela deve conter cards horizontais, um para cada receita feita;

72. Caso a receita do card seja uma comida, ela deve possuir: a foto da receita, o nome, a categoria, a area, um botão de compartilhar e um de _"desfavoritar"_;

73. Caso a receita do card seja uma bebida, ela deve possuir: a foto da receita, o nome, se é alcoólica ou não, um botão de compartilhar e um de _"desfavoritar"_;

74. O botão de compartilhar deve copiar a URL da tela de detalhes daquela receita para o clipboard;

75. O botão de _"desfavoritar"_ deve remover a receita da lista de receitas favoritas do `localStorage` e da tela;

76. Devem existir 2 botões que filtram as receitas por comida ou bebida e um terceiro que remove todos os filtros. Os nomes dos botões devem ser "Food", "Drinks" e "All", respectivamente;

77. Ao clicar na foto ou no nome da receita, a rota deve mudar para a tela de detalhes daquela receita;

78. A rota dessa página deve ser: `/receitas-favoritas`.

#### Tela de explorar

79. Todos os elementos devem respeitar os atributos descritos no protótipo para a tela de explorar;

80. A tela deve ter dois botões: um para explorar comidas e o outro para explorar bebidas. O nomes dos botões devem ser "Explorar Comidas" e "Explorar Bebidas", respectivamente;

81. Ao clicar em um dos botões, a rota deve mudar para a pagina de explorar comidas ou de explorar bebidas.

#### Tela de explorar bebidas ou comidas

82. Todos os elementos devem respeitar os atributos descritos no protótipo para a tela de explorar bebidas ou comidas;

83. Caso na tela de explorar a pessoa tenha clicado em comidas, o titulo deve mostrar "Explorar - Comidas". O mesmo para bebidas, cujo título deve mostrar "Explorar - Bebidas";

84. A tela deve ter três botões: um para explorar por ingrediente, um para explorar por local de origem e um para pegar uma receita aleatória. O nomes dos botões devem ser "Por ingredientes", "Por local de origem" e "Me surpreenda!", respectivamente. Obs: se a opção escolhida for explorar bebidas, o botão para explorar por local de origem não deve estar disponível;

85. Ao clicar em "Por ingredientes", a rota deve mudar para tela de explorar ingredientes;

86. Ao clicar em "Por local de origem", a rota deve mudar para tela de explorar por local de origem;

87. Ao clicar em "Me surpreenda", a rota deve mudar para a tela de detalhes de uma receita, que deve ser escolhida de forma aleatória através da API;

88. A rota deve ser `/explorar/comidas` ou `/explorar/bebidas`, dependendo de qual é a origem.

#### Tela de explorar ingredientes

89. Todos os elementos devem respeitar os atributos descritos no protótipo para a tela de explorar ingredientes;

90. A tela deve ter cards que contêm: o nome do ingrediente e uma foto;

91. Ao clicar no card do ingrediente a rota deve mudar para tela principal de receitas, mas mostrando apenas as receitas que contém o ingrediente escolhido;

92. As receitas mostradas devem representar o tipo escolhido antes na tela de explorar, que pode ser comida ou bebida;

93. A rota deve ser `/explorar/comidas/ingredientes` ou `/explorar/bebidas/ingredientes`.

## Tela de explorar por local de origem/area

### 94 - Todos os elementos devem respeitar os atributos descritos no protótipo para a tela de explorar por local de origem.

### 95 - A tela segue as mesmas especificações da tela de receitas principal, a única diferença é que os filtros de categoria são substituídos por um dropdown.

##### As seguintes verificações serão feitas:

- Devem ser carregadas as 12 primeiras receitas de comidas;
- Ao selecionar um filtro de local de origem, todas as receitas devem mudar para os dados filtrados da API;
- Ao clicar no card, a rota deve mudar para a tela de detalhes da receita com o ID da mesma na URL.

### 96 - No dropdown devem estar disponíveis todas as áreas retornadas da API, incluindo a opção "All", que retorna as receitas sem nenhum filtro.

##### As seguintes verificações serão feitas:

- No dropdown devem estar disponíveis todas as áreas retornadas da API, incluindo a opção "All";
- A opção "All" retorna as receitas sem nenhum filtro.

### 97 - A rota deve ser apenas `/explorar/comidas/area`. A rota `/explorar/bebidas/area` não deve estar disponível, retornando um erro de "Not Found".

#### Tela de perfil

98. Todos os elementos devem respeitar os atributos descritos no protótipo para a tela de perfil;

99. O e-mail da pessoa usuária deve estar visível;

100. Essa tela deve conter 3 botões: um de nome "Receitas feitas", um de nome "Receitas Favoritas" e um de nome "Sair";

101. Ao clicar no botão de "Receitas Favoritas", a rota deve mudar para a tela de receitas favoritas;

102. Ao clicar no botão de "Receitas Feitas", a rota deve mudar para a tela de receitas feitas;

103. Ao clicar no botão de "Sair", o `localStorage` deve ser limpo e a rota deve mudar para a tela de login.

---

***Obs: A maneira como as APIs devem ser estruturadas segue os seguintes modelos: https://www.themealdb.com/api.php e https://www.thecocktaildb.com/api.php***

---

### Implementações técnicas

Algumas coisas devem seguir um padrão pré-estabelecido para que os teste de correção funcionem corretamente.

#### Rotas

As rotas a serem utilizadas na aplicação devem ser as seguintes:

* Tela de login: `/`;
* Tela principal de receitas de comidas: `/comidas`;
* Tela principal de receitas de bebidas: `/bebidas`;
* Tela de detalhes de uma receita de comida: `/comidas/{id-da-receita}`;
* Tela de detalhes de uma receita de bebida: `/bebidas/{id-da-receita}`;
* Tela de receita em processo de comida: `/bebidas/{id-da-receita}/in-progress`;
* Tela de receita em processo de bebida: `/bebidas/{id-da-receita}/in-progress`;
* Tela de explorar: `/explorar`;
* Tela de explorar comidas: `/explorar/comidas`;
* Tela de explorar bebidas: `/explorar/bebidas`;
* Tela de explorar comidas por ingrediente: `/explorar/comidas/ingredientes`;
* Tela de explorar bebidas por ingrediente: `/explorar/bebidas/ingredientes`;
* Tela de explorar comidas por local de origem: `/explorar/comidas/area`;
* Tela de perfil: `/perfil`;
* Tela de receitas feitas: `/receitas-feitas`;
* Tela de receitas favoritas: `/receitas-favoritas`.

#### `localStorage`

O uso de `localStorage` é necessário para que as informações não se percam caso a pessoa atualize a página.
O correto é usar os valores para iniciar sua store ou seu context.

No `localStorage` do navegador:

* a chave `mealsToken` deve conter a seguinte estrutura:
```
1
```

* a chave `cocktailsToken` deve conter a seguinte estrutura:
```
1
```

* a chave `user` deve conter a seguinte estrutura:
```
{
    email: email-da-pessoa
}
```

* a chave `doneRecipes` deve conter a seguinte estrutura:
```
[{
    id: id-da-receita,
    type: comida-ou-bebida,
    area: area-da-receita-ou-texto-vazio,
    category: categoria-da-receita-ou-texto-vazio,
    alcoholic: alcoholic-ou-non-alcoholic-ou-texto-vazio,
    name: nome-da-receita,
    image: imagem-da-receita,
    doneDate: quando-a-receita-foi-concluida,
    tags: array-de-tags-da-receita-ou-array-vazio
}]
```

* a chave `favoriteRecipes` deve conter a seguinte estrutura:
```
[{
    id: id-da-receita,
    type: comida-ou-bebida,
    area: area-da-receita-ou-texto-vazio,
    category: categoria-da-receita-ou-texto-vazio,
    alcoholic: alcoholic-ou-non-alcoholic-ou-texto-vazio,
    name: nome-da-receita,
    image: imagem-da-receita
}]
```

* a chave `inProggressRecipes` deve conter a seguinte estrutura:
```
{
    id-da-receita: [lista-de-ingredientes-utilizados],
    ...
}
```

    **Observação:** Cada ID representa o ID de uma receita e cada item da lista de ingredientes da respectiva receita deve ser representado apenas pelo número do ingrediente no formato numérico.

---

## Instruções para entregar seu projeto:

### ANTES DE COMEÇAR A DESENVOLVER:

1. Clone o repositório
  * `git clone git@github.com:tryber/sd-0x-recipes-app-N.git`.
  * Entre na pasta do repositório que você acabou de clonar:
    * `cd sd-0x-recipes-app-N`

2. Instale as dependências, inicialize o projeto e rode os testes
  * Instale as dependências:
    * `npm install`
  * Inicialize o projeto:
    * `npm start` (uma nova página deve abrir no seu navegador com um texto simples)
  * Verifique que os testes E2E estão executando:
    * `npm run cy` (os testes devem rodar e falhar)
    * `npm run cy:open` (os testes devem rodar e falhar, legal caso queira ver o Cypress funcionando)

3. Crie uma branch a partir da branch `master`
  * Verifique que você está na branch `master`
    * Exemplo: `git branch`
  * Se não estiver, mude para a branch `master`
    * Exemplo: `git checkout master`
  * Agora, crie uma branch onde você vai guardar os `commits` do seu projeto
    * Você deve criar uma branch no seguinte formato: `nome-de-usuário-nome-do-projeto`
    * Exemplo: `git checkout -b joaozinho-movie-card-library`

5. Adicione as mudanças ao _stage_ do Git e faça um `commit`
  * Verifique que as mudanças ainda não estão no _stage_
    * Exemplo: `git status` (deve aparecer listada a pasta _components_ em vermelho)
  * Adicione o novo arquivo ao _stage_ do Git
      * Exemplo:
        * `git add .` (adicionando todas as mudanças - _que estavam em vermelho_ - ao stage do Git)
        * `git status` (deve aparecer listado o arquivo _components/Header.jsx_ em verde)
  * Faça o `commit` inicial
      * Exemplo:
        * `git commit -m 'iniciando o projeto. VAMOS COM TUDO :rocket:'` (fazendo o primeiro commit)
        * `git status` (deve aparecer uma mensagem tipo _nothing to commit_ )

6. Adicione a sua branch com o novo `commit` ao repositório remoto
  * Usando o exemplo anterior: `git push -u origin joaozinho-movie-cards-library`

7. Crie um novo `Pull Request` _(PR)_
  * Vá até a página de _Pull Requests_ do [repositório no GitHub](https://github.com/tryber/sd-0x-recipes-app-N/pulls)
  * Clique no botão verde _"New pull request"_
  * Clique na caixa de seleção _"Compare"_ e escolha a sua branch **com atenção**
  * Clique no botão verde _"Create pull request"_
  * Adicione uma descrição para o _Pull Request_ e clique no botão verde _"Create pull request"_
  * **Não se preocupe em preencher mais nada por enquanto!**
  * Volte até a [página de _Pull Requests_ do repositório](https://github.com/tryber/sd-0x-recipes-app-N/pulls) e confira que o seu _Pull Request_ está criado

---

### DURANTE O DESENVOLVIMENTO

* ⚠ **LEMBRE-SE DE CRIAR TODOS OS ARQUIVOS DENTRO DA PASTA COM O SEU NOME** ⚠


* Faça `commits` das alterações que você fizer no código regularmente

* Lembre-se de sempre após um (ou alguns) `commits` atualizar o repositório remoto

* Os comandos que você utilizará com mais frequência são:

1. `git status` _(para verificar o que está em vermelho - fora do stage - e o que está em verde - no stage)_

2. `git add` _(para adicionar arquivos ao stage do Git)_

3. `git commit` _(para criar um commit com os arquivos que estão no stage do Git)_

4. `git push -u nome-da-branch` _(para enviar o commit para o repositório remoto na primeira vez que fizer o `push` de uma nova branch)_

5. `git push` _(para enviar o commit para o repositório remoto após o passo anterior)_

---

### DEPOIS DE TERMINAR O DESENVOLVIMENTO

Para **"entregar"** seu projeto, siga os passos a seguir:

* Vá até a página **DO SEU** _Pull Request_, adicione a label de _"code-review"_ e marque seus colegas
  * No menu à direita, clique no _link_ **"Labels"** e escolha a _label_ **code-review**
  * No menu à direita, clique no _link_ **"Assignees"** e escolha **o seu usuário**
  * No menu à direita, clique no _link_ **"Reviewers"** e digite `students`, selecione o time `tryber/students-sd-0x`

Se ainda houver alguma dúvida sobre como entregar seu projeto, [aqui tem um video explicativo](https://vimeo.com/362189205).

---

### REVISANDO UM PULL REQUEST

⚠⚠⚠

À medida que você e os outros alunos forem entregando os projetos, vocês serão alertados **via Slack** para também fazer a revisão dos _Pull Requests_ dos seus colegas. Fiquem atentos às mensagens do _"Pull Reminders"_ no _Slack_!

Os monitores também farão a revisão de todos os projetos, e irão avaliar tanto o seu _Pull Request_, quanto as revisões que você fizer nos _Pull Requests_ dos seus colegas!!!

Use o material que você já viu sobre [Code Review](https://course.betrybe.com/real-life-engineer/code-review/) para te ajudar a revisar os projetos que chegaram para você.
