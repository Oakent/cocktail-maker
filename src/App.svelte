<script>
  let ing = "";
  const margarita = {
    name: "Margarita",
    ingredients: ["tequila", "lime", "triple sec"],
  };
  const mojito = {
    name: "Mojito",
    ingredients: ["rum", "lime", "mint", "soda water"],
  };
  const cocktails = [margarita, mojito];
  let Cingredients = [];
  let checkSubset = (parentArray, subsetArray) => {
    return subsetArray.every((el) => {
      return parentArray.includes(el);
    });
  };
  let checkCocktail = (cocktail, ingredients) => {
    return checkSubset(ingredients, cocktail.ingredients);
  };
  let cocktailsMade = [];
  let checkCocktails = () => {
    cocktailsMade = [];
    for (let i = 0; i < cocktails.length; i++) {
      if (checkCocktail(cocktails[i], Cingredients)) {
        cocktailsMade.push(cocktails[i].name);
      }
    }
    cocktailsMade = cocktailsMade;
  };

  let addIngredient = () => {
    Cingredients = [...Cingredients, ing];
    ing = "";
  };
</script>

<main>
  <p>Enter cocktail ingredients to find a recipe.</p>
  <p>Cocktails which can be made: {cocktailsMade.join(" ")}</p>
</main>

<input bind:value={ing} />

<button on:click={addIngredient}> Add ingredient </button>

<button on:click={checkCocktails}>Check cocktails</button>

<p>ingredients added: {Cingredients}</p>

<style>
</style>
