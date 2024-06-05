# PROGRAMMINGPART2
ST10398118

PROGRAMMING2A PART 2


  COMPILING A SOFTWARE
- First you must write a source code in a text editor, and then save the file with the appropriate file extensions for example in this case we will make use of c++.

  COMPILING AND RUNNING SOFTWARE
  - Writing a source code a specific and then it will be saved as an file with an appropriate extension for a specific programming language in this case c++.
 
    
COMPILING THE CODE:
- For instance in c++, the command allows for a c++ program for exmple goodbye.cpp
- g++ goodbye.cpp
- The command that translates the source code into an object file, which also links a library to allow for executable code.

IDE: 

- Using an IDE: If you’re using an IDE, it often has built-in tools to compile and run your programs. You typically write your code, then click a button to compile, and another to run the program.
- Troubleshooting: If you encounter errors during compilation, check your code for syntax errors or missing dependencies. Compiler error messages can help you pinpoint the issue.

Fixed mistakes from PART1 

CORRECTED CODE:



using System;
using System.Collections.Generic;

namespace RecipeMaker
{
    // the the ingredient class with an array
    

    public class Ingredient
    {
        public string Name { get; set; }
        public double Quantity { get; set; }
        public string Unit { get; set; }

        public Ingredient(string name, double quantity, string unit)
        {
            Name = name;
            Quantity = quantity;
            Unit = unit;
        }
    }
       // the recipe class 
    public class Recipe
    {
        private List<Ingredient> ingredients;
        private List<string> steps;

        public Recipe() // method
        {
            ingredients = new List<Ingredient>();
            steps = new List<string>();
        }
          // the method that allows for the user to input their data 
        public void EnterDetails()
        {
            ingredients.Clear();
            steps.Clear();

            try
            {
                Console.WriteLine("Please Enter the name of the recipe:");
                string recipeName = Console.ReadLine();

                Console.WriteLine("Please Enter the number of ingredients:");
                int numIngredients = Convert.ToInt32(Console.ReadLine());

                for (int i = 0; i < numIngredients; i++)
                {
                    Console.WriteLine($"Please input the name of ingredient {i + 1}:");
                    string name = Console.ReadLine();

                    Console.WriteLine($"Please input the quantity of your ingredients {i + 1}:");
                    double quantity;
                    while (!double.TryParse(Console.ReadLine(), out quantity))
                    {
                        Console.WriteLine("Invalid quantity. Please enter a valid number:");
                    }

                    Console.WriteLine($"Please enter unit of measurement for ingredient {i + 1}:");
                    string unit = Console.ReadLine();

                    ingredients.Add(new Ingredient(name, quantity, unit));
                }
                 //user can input their steps 
                Console.WriteLine("Please input the number of steps:");
                int numSteps = Convert.ToInt32(Console.ReadLine());

                for (int i = 0; i < numSteps; i++)
                {
                    Console.WriteLine($"Enter step {i + 1}:");
                    string step = Console.ReadLine();
                    steps.Add(step);
                }

                Console.WriteLine("Recipe details entered successfully! for " + recipeName + "!");
            }
            catch (FormatException)
            {
                Console.WriteLine("Format was invalid. Please enter a valid number.");
            }
            catch (OverflowException)
            {
                Console.WriteLine("Input is too large or too small for the expected data type.");
            }
            catch (Exception ex)
            {
                Console.WriteLine($"Unfortunately an error occurred: {ex.Message}");
            }
        }
        // where the program will be displayed 
        public void Display()
        {
            Console.WriteLine("Recipe:");
            Console.WriteLine("Ingredients:");
            foreach (Ingredient ingredient in ingredients)
            {
                Console.WriteLine($"- {ingredient.Quantity} {ingredient.Unit} of {ingredient.Name}");
            }

            Console.WriteLine("Steps:");
            for (int i = 0; i < steps.Count; i++)
            {
                Console.WriteLine($"{i + 1}. {steps[i]}");
            }
        }

        public void Scale()
        {
            Console.WriteLine("Please enter the scaling factor (0.5 for half, 2 for double, or 3 for triple):");
            double factor = Convert.ToDouble(Console.ReadLine());

            foreach (Ingredient ingredient in ingredients)
            {
                ingredient.Quantity *= factor;
            }

            Console.WriteLine("Your recipe was scaled successfully!");
        }

        public void ResetQuantities()
        {
            Console.WriteLine("The quantities have been reset to their original values!");
        }

        public void ClearData()
        {
            ingredients.Clear();
            steps.Clear();
            Console.WriteLine("Your recipe has been cleared!");
        }
    }

    class main_program
    {
        static void Main(string[] args)
        {
            Recipe recipe = new Recipe();

            while (true)
            {
                Console.WriteLine("1. Please Input The Details Of Your Recipe");
                Console.WriteLine("2. Display/Results Of Your Recipe");
                Console.WriteLine("3. Scale Recipe");
                Console.WriteLine("4. Reset Quantities");
                Console.WriteLine("5. Clear Data");
                Console.WriteLine("6. Exit");
                Console.WriteLine("Please select an option:");

                int choice;
                while (!int.TryParse(Console.ReadLine(), out choice) || choice < 1 || choice > 6)
                {
                    Console.WriteLine("Invalid choice. Please enter a number between 1 and 6.");
                }

                Console.WriteLine("Please press Enter to confirm or any other option to cancel.");
                if (Console.ReadKey().Key != ConsoleKey.Enter)
                {
                    Console.WriteLine("The operation cancelled.");
                    continue;
                }

                switch (choice)
                {
                    case 1:
                        recipe.EnterDetails();
                        recipe.Display();
                        break;

                    case 2:
                        recipe.Display();
                        break;
                    case 3:
                        recipe.Scale();
                        break;
                    case 4:
                        recipe.ResetQuantities();
                        break;
                    case 5:
                        recipe.ClearData();
                        break;
                    case 6:
                        Environment.Exit(0);
                        break;
                }
            }
        }
    }
}










Link to GITHUB:
- https://github.com/Obianuju345/PROGRAMMINGPART2/edit/main/README.md



o	Exception Handling:
Add a try- catch  blocks that is surrounded by user inputs to allow for the handling of any potential errors.
o	Input Validation:
The implementation of validation for any numerical inputs to prevent any occurrences to prevent any common errors. User Confirmation: 
Introduced a confirmation step after selecting an option, asking the user to press Enter to confirm their choice, adding an extra layer of user intent verification to avoid accidental selections.


HOW THE APP WORKS

Recipe_App
Overview
Recipe_App is a console-based application that allows users to manage cooking recipes. Users can add recipes with ingredients and steps, display recipes, scale recipe quantities, reset quantities to original values, and clear all data.

Features
Add Recipes: Input recipe name, ingredients, and cooking steps.
Display Recipes: View a list of all recipes.
Display Recipe Details: View detailed information about a specific recipe, including ingredients, steps, and total calories.
Scale Recipe Quantities: Adjust ingredient quantities by a scaling factor (e.g., half, double, triple).
Reset Quantities: Reset ingredient quantities to their original values.
Clear Data: Remove all recipes from the application.


Navigate to the project directory:
bash
Copy code
cd Recipe_App
Running the Application
Build and run the application:
bash
Copy code
dotnet run
Follow the on-screen prompts to interact with the application.
Example Usage
Adding a Recipe
After starting the application, you will be prompted to enter recipe details.
Enter the recipe name, number of ingredients, and details for each ingredient (name, quantity, unit, calories, food group).
Enter the number of steps and details for each step.
Displaying Recipes
Select "Display All Recipes" from the menu to view a list of all recipes.
Select "Display Recipe Details" from the menu and enter the recipe name to view detailed information about a specific recipe.
Scaling Recipes
Select "Scale Recipe" from the menu.
Choose a scaling factor (0.5, 2, or 3).
The ingredient quantities and calories will be adjusted accordingly.
Resetting Quantities
Select "Reset Quantities" from the menu to revert ingredient quantities to their original values.
Clearing Data
Select "Clear All Data" from the menu and confirm to remove all recipes from the application.
Code Structure
Enums
FoodGroup: Enum representing different food groups (Protein, Carbohydrate, Vegetable, Fruit, Dairy, Fat, Other).
Classes
RecipeIngredient: Represents an ingredient with properties for name, quantity, unit, calories, and food group.
CookingRecipe: Represents a recipe with properties for name, a list of ingredients, and a list of steps.
CookingRecipeManager: Manages a collection of recipes, including adding recipes, displaying recipes, and handling calorie notifications.
CookingRecipeApp: Handles user interactions, including inputting recipes, displaying recipes, scaling recipes, resetting quantities, and clearing data.
CookingRecipeProgram: Entry point for the application, running the main program loop.
Delegates
CalorieNotification: Delegate for notifying when the total calories of a recipe exceed a threshold (300 calories).
Unit Testing
Unit tests are included to ensure the correctness of the application's functionality. The tests cover:

Creating ingredients.
Calculating total calories of a recipe.
Adding and sorting recipes.
Scaling recipe quantities.
Running Unit Tests
Navigate to the tests directory:
bash
Copy code
cd Recipe_App.Tests
Run the tests:
bash
Copy code
dotnet test
Contributing
Contributions are welcome! Please fork the repository and submit a pull request with your changes.



 

