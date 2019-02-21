# HTTTPizza/2.0

Welcome to Hot Tasty Tomato Palace, I'll be your server tonight, could you please pick a table?
Unfortunately, I don't speak English, and I'm only able to speak [HTTPizza](https://github.com/ZeusWPI/HTTPizza).

## 0. Greeting the waiter back

Please be a polite human and make a PIZZA request to `/welcome`.

## 1. Picking a table

To get a table, you'll need to login first. To do that, you need to make an ORDER request to `/login` with a `Name` header containing your name. The waiter will then give you a table number where you can sit down. This number will be in the `table` header in the response. In all further HTTPizza request, you'll need to add your tablenumber so the server doesn't get confused.

## 2. What's on the menu?

You've just sat down on your assigned table, and want to check what pizza's are on the menu. To check the menu, make a PIZZA request to `/menu`. Don't forget to add a `Table` header with your table number you got from logging in!

## 3. Picky eater

In this special pizza place, the menu is different from usual menus: instead of a list of possible pizzas, there's a list of ingredients.
Of course, it's not possible to just throw some ingredients together and get a good pizza: only the chef knows what ingredients form a valid pizza.
Unfortunately, you can't talk directly to the chef, but you can talk to the chef via your waiter.

To check if a pizza exists, make a PIZZA request to `/pizza` containing the `I-Want` header. The value of this header is a comma-separated list of toppings and sauces.

For example, if you got this menu:

```
{"topping":["parmesan", "onions"],"sauce":["nutella"]
```
you could check if a really weird pizza with nutella and parmesan exists by putting `topping/parmesan, sauce/nutella` in the `I-Want` header.

Try to bruteforce all possible pizzas to see what pizzas exist. The order of toppings/sauces doesn't matter, nor does how many times you include the same topping/sauce.

## 4. Time to order!

Each table has an oven in which you can bake a single pizza. After finding which pizza you want to order in #3, you can now order the pizza you got by making an ORDER request to `/order`. This request needs to have the `Pizza-Type` header set to the name of the pizza you got in #3. The response will have an `Oven-Time` header containing a number. This number indicates the number of seconds the pizza needs to be baked in the oven.

After that time has passed, make a PIZZA request to `/pickup`. This will return your pizza ID.

## 5. Om nom nom

My favorite part! We can now eat the pizza we just got from the oven by making an EAT request to `/pizza/<your-pizza-id-here>/`. This will redirect you to a pizza slice, which you then have to EAT. Every request to your pizza will return a new slice, until there's no more pizza left.

Please eat your entire pizza before continueing.