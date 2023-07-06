# price-product-manager-db
'''
needs sqlite file or csv alternative.

Uses category and product objects file to utilize in main application to manipulate product database with fitness products (insert your own csv/db), prices and ID codes. User can view products, update prices in the databases and  exit the program with commited data to database.'''

import db
import objects
from objects import Product
from objects import Category

'''Use the db file to connect your sqlite database to your product manager py file, will use SQL to commit changes to your db.'''
