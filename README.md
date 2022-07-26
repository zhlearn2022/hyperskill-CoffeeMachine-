package main

import (
	"fmt"
"os"
)

func main() {

	var has = []int{400, 540, 120, 9, 550}
    action(has)
}

func actionRemaining(has []int) {
	fmt.Println("The coffee machine has:")
	fmt.Printf("%d ml of water\n", has[0])
	fmt.Printf("%d ml of milk\n", has[1])
	fmt.Printf("%d g of coffee beans\n", has[2])
	fmt.Printf("%d disposable cups\n", has[3])
	fmt.Printf("%d$ of money\n", has[4])
 action(has)
}

func action(has []int) []int {
	var action string

	fmt.Println("Write action (buy, fill, take, remaining, exit):")
_, _ = fmt.Scan(&action)
	switch {
	case action == "buy":
		actionBuy(has)
case action == "fill":
	actionFill(has)
case action == "take":
		actionTake(has)
	case action == "remaining":
		actionRemaining(has)
   case action == "exit":
    exits(has)
 
}
	return has
}

func exits(has []int) []int {
exit := true
if exit {
		fmt.Println("Exit")
		os.Exit(0)
	} else {
		fmt.Println("NO Exit")
		os.Exit(1)
	}
	return has
}



func actionStatusBuyespresso(has []int) []int {
	if 250 <= has[0] &&  16 <= has[2]&&  1 <= has[3] {
		fmt.Println("I have enough resources, making you a coffee!")
		espresso(has)
		} else if has[0] < 249 {
		fmt.Println("Sorry, not enough water!")
		action(has)
	}
	return has

}
func actionStatusBuyLatte(has []int) []int {
	if 350 <= has[0] && 75 <= has[1]&&  20 <= has[2]&&  1 <= has[3] {
		fmt.Println("I have enough resources, making you a coffee!")
		latte(has)
		} else if has[0] < 349 {
		fmt.Println("Sorry, not enough water!")
		action(has)
	}
	return has

}

func actionStatusBuycappuccino(has []int) []int {
	if 200 <= has[0] && 100 <= has[1]&& 12 <= has[2]&&  1 <= has[3] {
		fmt.Println("I have enough resources, making you a coffee!")
		cappuccino(has)
		} else if has[0] < 200 {
		fmt.Println("Sorry, not enough water!")
		action(has)
	}
	return has

}
func actionBuy(has []int) []int {
	var num string
	fmt.Println("What do you want to buy? 1 - espresso, 2 - latte, 3 - cappuccino, back - to main menu:")
	_, _ = fmt.Scan(&num)
		switch num {
case  "1":
     actionStatusBuyespresso(has)
case "2":
	 actionStatusBuyLatte(has)
case "3":
		actionStatusBuycappuccino(has)
case "back":	
action(has)
	default: 
	fmt.Println("back")
			action(has)
	}
	return has
}
func espresso(has []int) []int {
	has[0] -= 250
	has[2] -= 16
	has[3] -= 1
	has[4] += 4
action(has)
		return has
}
func latte(has []int) []int {
	
	has[0] -= 350
	has[1] -= 75
	has[2] -= 20
	has[3] -= 1
	has[4] += 7
action(has)	
		return has

}
func cappuccino(has []int) []int {
	has[0] -= 200
	has[1] -= 100
	has[2] -= 12
	has[3] -= 1
	has[4] += 6
	
action(has)
		return has
}

func actionFill(has []int) []int {
	
	fmt.Println("Write how many ml of water you want to add:")
	var waterAdd int
	_, _ = fmt.Scan(&waterAdd)
	has[0] += waterAdd
	fmt.Println("Write how many ml of milk you want to add:")
	var milkAdd int
	_, _ = fmt.Scan(&milkAdd)
	has[1] += milkAdd
	fmt.Println("Write how many grams of coffee beans you want to add: ")
	var beansAdd int
	_, _ = fmt.Scan(&beansAdd)
	has[2] += beansAdd
	fmt.Println("Write how many disposable cups of coffee you want to add:")
	var cupsAdd int
	_, _ = fmt.Scan(&cupsAdd)
	has[3] += cupsAdd
	action(has)
		return has
}

func actionTake(has []int) []int {
	fmt.Println("I gave you $%", has[4])
has[4] -= has[4]
	action(has)
		return has
}
