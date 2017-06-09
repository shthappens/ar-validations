<!-- Let's add some validations to our Brussels Sprouts recipe blog.

Validate that the title of each recipe exists. -->

Recipe.create returns ROLLBACK

<!-- Validate that the title of each recipe is unique. -->

Recipe.create(recipe_name: "Brussels sprouts") returns ROLLBACK as "Brussels sprouts" already exists in the DB.

<!-- Validate that the title of each recipe contains "Brussels sprouts" in it. -->

Recipe.create(recipe_name: "Brussels crackers") returns ROLLBACK.

<!-- Validate that the length of a comment be a maximum of 140 characters long. -->

Comment.create(recipe_id: 1, body: "This is a long comment that is more than one hundred forty characters in total. This comment will not save to the database due to the character length validation.") returns ROLLBACK.

<!-- Validate that a comment has a recipe. -->

Comment.create(body: "A comment") returns ROLLBACK.

<!-- Add a field servings to your Recipe table. This field is optional, but if supplied, it must be greater than or equal to 1. Write a validation for this. -->

recipe = Recipe.create(recipe_name: "Brussels sprouts gum") COMMITS with servings blank.
recipe.update(servings: 1) COMMITS with 1 serving.

<!-- Load up your app in irb and confirm that your validations work. -->
