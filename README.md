# price-product-manager-db
'''Uses category and product objects file to utilize in main application to manipulate product database with fitness products (insert your own csv/db), prices and ID codes. User can view products, update prices in the databases and  exit the program with commited data to database.'''

import db
import objects
from objects import Product
from objects import Category


def display_title():
    print( )
    print("\t"*9 + " -Product Manager-")


def display_categories():
    print("*"*40 + "CATEGORIES" + "*"*40)
    categories = db.get_categories()
    for category in categories:
        print(str(category.id) + "__" + str(category.name))
    print("*"*90 + "\n")


def display_menu():
    print("-"*11 + "COMMAND MENU" + "-"*11)
    print("view   - View products by category")
    print("update - Update product price")
    print("exit   - Exit program")
    print("-"*34)


def display_products_by_category():
    category_name = input("Category Name: ")
    print("-"*90)
    line_format = "{:15s}  {:50s}  {:110s}"
    print(line_format.format ("Code", "Name", "Price"))
    print("-" * 90)
    if category_name == "Freeweights":
        products = db.get_products_by_category(category_name)
        for category in products:
            print(line_format.format(str(category.code), str(category.name), str(category.price)))
    elif category_name == "Strengthtraining":
        products = db.get_products_by_category(category_name)
        for category in products:
            print(line_format.format(str(category.code), str(category.name), str(category.price)))
    else:
        category_name == "Smartfitness"
        products = db.get_products_by_category(category_name)
        for category in products:
            print(line_format.format(str(category.code), str(category.name), str(category.price)))
print("-" * 90)

def update_product():
    code = input("Product Code: ")                             #objects.Product.__init__(self,code)
    price = input("New Product Price: ")                       #objects.Product.__init__(self,price)
    db.update_product(code, price)
    print("Product updated.\n")

def main():
    db.connect()
    display_title()
    display_categories()
    display_menu()
    while True:
        command = input("Command: ")
        if command == "view":
            display_products_by_category()
        elif command == "update":
            update_product()
        elif command == "exit":
            break
        else:
            print("Not a valid command. Please try again.\n")
            display_menu()
    db.close()
    print("Bye!")


if __name__ == "__main__":
    main()
