---
layout: post
title:  "Finally Through the First Part - Rails Project"
date:   2017-04-18 23:15:23 +0000
---

Superman had kryptonite, Achilles had his trick heal, and my silver bullet was the rails attribute writer. I'll get back to that though. This rails project has been such a great learning experience. When I began I was overwhelmed quickly with the undertaking. I remember many nights staying up late frustrated reading over the rails documentation. What should I put where? How do I properly use MVC? What do you mean skinny controller think model? I had so many questions.

I decided to create a recipe manager app. But I didn't want to stop at the bare bones `user` and `recipe` models. So I decided to add a `favorite` and `rating` models  as well. So now a user can create a review for a recipe and add a recipe to their favorites list. I also added a `recipes_of_the_day` method to home page that showed random recipes from db and `highest_rated` method that shows the currently top rated recipe. 

Ok back to the dreaded attribute writer. At first I was having a hard time deciding how to approach it. I wasn't sure if I had my form set up correctly or not. After a number of questions and help from my instructor, finally I set my form fields_for like this:
```
<% 10.times do |n| %>
   <%= f.fields_for :ingredients do |i| %>
      <div class="fluid field">
         <%= i.label :quantity %>
         <input type="text" name="recipe[ingredients_attributes][<%= n %>][quantity]" /><br>
         <%= i.label "Ingredient #{ n + 1 }" %>
         <%= i.text_field :name %>
      </div><br>
   <% end %>
<% end %>
```
I was having trouble properly creating my `recipe_ingredients quantity` attribute. But taking the advice of my instructor, when in doubt, just write plain html, after all, it all ends up being html anyway. Ok so now i have all the inputs that I need. So what do I do with the information that I'll get? Finally after many grueling nights and checking all over the net, which was no help in this case, I came up with this writer method:
```
def ingredients_attributes=(ingredients_attributes)
   ingredients_attributes.each do |i, attr|
      unless attr[:name].blank?
         ingredient = Ingredient.find_or_create_by(:name => attr[:name])

         if self.recipe_ingredients.ids.empty?
            self.recipe_ingredients.build(:ingredient => ingredient, :quantity => attr[:quantity])
         else
            self.recipe_ingredients[i.to_i].update(:ingredient => ingredient, :quantity => attr[:quantity])
         end
      end
   end
end
```
Perfection!!! Sorry I know I'm a little too excited about it. But I took forever on that writer. Creating new recipes, it worked perfectly. But updating it was a disaster. It just didn't work! But now it works perfectly everytime. I'm expecting there's a better way to accomplish this but I haven't found it yet. If anybody can improve on this I'm am all ears. Please DM me. That's pretty much the beginnings of my rails project. If you haven't noticed yet my writer was the big deal.

Well on to the next part of the project. Now it's time for the javascript portion of things. Can't wait to see how that goes. Stay tuned to find out.

