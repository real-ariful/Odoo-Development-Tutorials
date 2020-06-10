# How to create a Custom Module in Odoo 13

## Create a custom model in Odoo13

### Steps to create a manifest file

### Step 1 : Create a "model" folder

First of all, go to the customs folder where you want to keep the custom modules.
We go to our module folder: "ob_bank". Inside our folder, we create a new folder named "models".

Inside our models folder, we create two new python files:
1. __init__.py
2. customers.py


### Step 2 : Edit "__init__.py" file

Open "__init__.py" in your editor and add the following line:

'''
from . import customers
'''


### Step 3 : Edit "customers.py" file

Open "__init__.py" in your editor and add the following lines:

'''
from odoo import models, fields

class BankCustomers(models.Model):
    _name = "bank.customers"
    _description = "Bank Customers"

    customer_name = fields.Char(string="Customer Name")
    customer_age = fields.Integer(string="Customer Age")
    customer_image = fields.Binary(string="Customer Image")

'''

We first import models and fields from odoo

Then we define a new model named "bank.customers", giving description as "Bank Customers".

After that, we create three new fields:
1. Character field named customer_name
2. Integer field named customer_age
3. Binary field named customer_image


### Step 4: Create "__init__.py" inside "ob_bank" folder

Create a new python file inside "ob_bank" folder. Add the following line:

'''
from . import models
'''

This line imports all the python files given inside the __init__.py inside the models folder.


### Step 5: Restart your server

Stop the server from terminal and start your odoo server again.

### Step 6: Upgrade "Bank Management" module

Go to frontend, settings and activate the developer mode.

Then go to Apps, search for your module: here "bank.management" and then upgrade the module.

### Step 7: Check the models in Techinical Settings

Make sure you are in developer mode. Now, go to Settings --> Technical --> Database Structure --> Models.

If you search for bank.customers, you will see the new models. Also the available fields. In addition, there will more fields. These details will be discussed in next part.