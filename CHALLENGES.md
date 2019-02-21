# HTTTPizza/2.0

Welcome to Hot Tasty Tomato Palace, I'll be your server tonight, could you please pick a table?
Unfortunately, I don't speak English, and I'm only able to speak [HTTPizza](https://github.com/ZeusWPI/HTTPizza).

## 0. Greeting the waiter

Please be a polite human and make a PIZZA request to `/welcome`.

Reward: you can now order drinks at reduced prices

## 1. Picking a table

To get a table, you'll need to login first. To do that, you need to make an ORDER request to `/login` with a `Name` header containing your teamname. The waiter will then give you a table number where you can sit down. This number will be in the `table` header in the response. In all further HTTPizza request, you'll need to add your tablenumber so the server doesn't get confused.

Reward:  every teammember gets one **free** slice of pizza AND you can choose one sticker from the stickertable

## 2. What's on the menu?

You've just sat down on your assigned table, and want to check what pizza's are on the menu. To check the menu, make a PIZZA request to `/menu`. Don't forget to add a `Table` header with your table number you got from logging in!

Reward:  every teammember gets one **free** slice of pizza

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

Try to bruteforce all possible pizzas to see what pizzas exist. The order of toppings/sauces doesn't matter, nor does how many times you include the same topping/sauce. You need to find the combination of  toppings that return a status code 200.

Reward: every teammember gets one **free** slice of pizza

## 4. Time to order!

Each table has an oven in which you can bake a single pizza. After finding which pizza you want to order in #3, you can now order the pizza you got by making an ORDER request to `/order`. This request needs to have the `Pizza-Type` header set to the name of the pizza you got in #3. The response will have an `Oven-Time` header containing a number. This number indicates the number of seconds the pizza needs to be baked in the oven.

After that time has passed, make a ORDER request to `/pickup`. This will return your pizza ID.

Reward:  every teammember gets one **free** slice of pizza

## 5. Om nom nom

My favorite part! We can now eat the pizza we just got from the oven by making an EAT request to `/pizza/<your-pizza-id-here>/`. This will redirect you to a pizza slice, which you then have to EAT. Every request to your pizza will return a new slice, until there's no more pizza left.

Please eat your entire pizza before continuing.

Reward: every teammember gets one **free** slice of pizza


## 6. Time to pay!

You thought all that pizza was free? Just cause we said so? WRONG!
Pay up by sending a PIZZA request to /pay. But hold up! The server will reject your request! Since the invoice contains a MASSIVE amount of IMPORTANT information, the server wants to gzip it. But you have to tell the server that you are ready to receive a gzipped file by including the correct header.

Once you have received the invoice, you need to parse the zipped file to find your payment token. 
The token is hidden somewhere in the wall of text with the format `$$PIZZATOKEN => ${token}$$` (you need whats inside the curly braces).

Then, send an ORDER request to /pay with that token included in a `Token` header. 

EXTRA CHALLENGE: do the above as fast as possible! Once you have succesfully completed the ORDER request you will receive a score, which is the amount of milliseconds you took to pay. Try to get it as low as possible!




# Extra challenges

## I. Start your own pizza place

Now write a HTTPizza/2.0 server from scratch that can handle HTTPizza requests.
