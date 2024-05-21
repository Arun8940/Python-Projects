from abc import ABC, abstractmethod

class TeaTime(ABC):
    
    @abstractmethod
    def view_menu(self):
        pass

    @abstractmethod
    def order_item(self):
        pass

    @abstractmethod
    def bill_item(self):
        pass
    
    @abstractmethod
    def review_item(self):
        pass

    @abstractmethod
    def cancel_order(self):
        pass

class Tea(TeaTime):

    def __init__(self):
        self.items = {
            'Hot Drinks': {
                'Tea': 15,
                'Special Tea': 20,
                'Coffee': 20,
                'Special Coffee': 25
            },
            'Cold Drinks': {
                'Coke': 30,
                'Sprite': 50,
                'Maza': 40
            },
            'Snacks': {
                'Biscuits': 10,
                'Lays': 10,
                'French fries': 50
            }
        }
        self.order = {}  #  store ordered items and quantities
        self.reviews = {}  #  store user revies for each item

    def view_menu(self):
        print("Categories:")
        for i, category in enumerate(self.items.keys(), 1):
            print(f"{i}. {category}")

    def order_item(self):
        try:
            print("Categories:")
            categories = list(self.items.keys())
            for i, category in enumerate(categories, 1):
                print(f"{i}. {category}")

            selected_category = categories[int(input("Enter the category number you want to order from: ")) - 1]
    
            print(f"\nItems in {selected_category}:")
            items = list(self.items[selected_category].items())
            for i, (item, price) in enumerate(items, 1):
                print(f"{i}. {item} - Price: ${price}")
    
            selected_item = items[int(input(f"Enter the item number you want to order from {selected_category}: ")) - 1]

            quantity = int(input("Enter the quantity:"))
            total_price = quantity * selected_item[1]

            self.order[selected_item[0]] = self.order.get(selected_item[0], 0) + quantity
            print(f"Order placed: {quantity} {selected_item[0]}(s) - Total: ${total_price}")

        except (ValueError, IndexError):
            print("Invalid input. Please enter a valid number.")

            
    def cancel_order(self):
        if not self.order:
            print("No items in the order to cancel.")
            return

        print("Current Order:")
        for i, (item, quantity) in enumerate(self.order.items(), 1):
            print(f"{i}. {item} - Quantity: {quantity}")

        try:
            item_to_cancel = int(input("Enter the number of the item you want to cancel: ")) - 1

            if 0 <= item_to_cancel < len(self.order):
                selected_item = list(self.order.keys())[item_to_cancel]
                canceled_quantity = int(input(f"Enter the quantity to cancel for {selected_item}: "))

                if 0 < canceled_quantity <= self.order[selected_item]:
                    self.order[selected_item] -= canceled_quantity
                    print(f"{canceled_quantity} {selected_item}(s) canceled successfully.")
                    if self.order[selected_item] == 0:
                        del self.order[selected_item]
                        print(f"All {selected_item}(s) canceled successfully.")
                else:
                    print("Invalid quantity to cancel. Please enter a valid quantity.")
            else:
                print("Invalid item number. Please enter a valid item number.")

        except ValueError:
            print("Invalid input. Please enter a valid number.")
    
    def bill_item(self):
         if not self.order:
            print("No items in the order. Please order something first.")
            return

         total_cost = sum(self.items[category].get(item, 0) * quantity for category, items in self.items.items() for item, quantity in self.order.items())

         if total_cost > 0:
            print(f"Total Bill: ${total_cost}")
         else:
            print("Error: Selected items not found in the menu.")

    def review_item(self):
        for item in self.order.keys():
            feedback = input(f"Provide feedback for {item}: ")
            self.reviews[item] = feedback
        print("Thank you for your feedback!")

# Creating an object
tea_obj = Tea()

while True:
    print("Welcome to Tea_Time..!")
    print("1. View Menu")
    print("2. Order Item")
    print("3. Cancel Order")
    print("4. View Bill")
    print("5. Review Items")
    print("6. Exit")

    choice = input("Enter your choice: ").lower()

    if choice == '1':
        tea_obj.view_menu()
    elif choice == '2':
        tea_obj.order_item()
    elif choice == '3':
        tea_obj.cancel_order()
    elif choice == '4':
        tea_obj.bill_item()
    elif choice == '5':
        tea_obj.review_item()
    elif choice == '6':
        break
    else:
        print("Invalid choice. Please enter a valid option.")
