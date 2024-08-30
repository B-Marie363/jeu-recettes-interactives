document.addEventListener("DOMContentLoaded", function() {
    const ingredients = document.querySelectorAll(".ingredient");
    const mixButton = document.getElementById("mix");
    const cookButton = document.getElementById("cook");
    const resultText = document.getElementById("resultText");

    let selectedIngredients = [];

    ingredients.forEach(ingredient => {
        ingredient.addEventListener("click", function() {
            const ingredientName = this.getAttribute("data-name");
            selectedIngredients.push(ingredientName);
            this.classList.add("disabled");
            checkIngredients();
        });
    });

    function checkIngredients() {
        if (selectedIngredients.includes("Farine") && selectedIngredients.includes("Œufs") &&
            selectedIngredients.includes("Lait") && selectedIngredients.includes("Sucre")) {
            mixButton.classList.remove("disabled");
        }
    }

    mixButton.addEventListener("click", function() {
        if (!this.classList.contains("disabled")) {
            resultText.textContent = "Vous avez mélangé les ingrédients ! Maintenant, cuisez vos crêpes.";
            cookButton.classList.remove("disabled");
        }
    });

    cookButton.addEventListener("click", function() {
        if (!this.classList.contains("disabled")) {
            resultText.textContent = "Bravo ! Vous avez fait de délicieuses crêpes !";
            mixButton.classList.add("disabled");
            cookButton.classList.add("disabled");
        }
    });
});
