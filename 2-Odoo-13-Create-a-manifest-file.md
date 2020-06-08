# How to create a Custom Module in Odoo 13

## Create a __manifest__ file in Odoo

### What is Manifest File?

The manifest file serves to declare a python package as an Odoo module and to specify module metadata.

It is a file called __manifest__.py and contains a single Python dictionary, where each key specifies module metadatum.


### Steps to create a manifest file

### Step 1 : Create a module folder

First of all, go to the customs folder where you want to keep the custom modules.
For example, I have created a o13-custom folder. 

Inside this folder, I have created a folder named: ob_bank

This ob_bank is the technical name of my module. You can name your module according to your needs. Here, I have used ob representing odoo buddy, underscore, and followed by my actual module bank.


### Step 2 : Create a __manifest__.py file

Inside your module folder(here: ob_bank), create a __manifest__.py file

### Step 3 : Edit __manifest__.py file

Now open your favourite file editor. Here we are using Visual Studio Code and open the module folder: ob_bank. 

Now we go to the odoo13 core code, go to sale module and copy the content of the ___manifest__.py file and paste in our __manifest__.py file

We then edit according to our needs:

# -*- coding: utf-8 -*-
{
    'name': "Bank Management",
    'summary': """Bank Management Summary""",
    'description': """Bank Management Application""",
    'author': "Odoo Buddy",
    'website': "http://www.odoo-buddy.com",
    'category': 'Extra Tools',
    'version': '13.0.1.0.0',
    'depends': [],
    'data': [ 

    ],
    'demo': [

     ],
    'qweb': [ 

    ],
    'application': True,
    'installable': True,
    'auto_install': False
}

The above are the basic details for a manifest file.

Available manifest fields are:

name (str):  This is the human-readable name of the module. Here it is given as "Bank Management"
summary (str): This is the summary of the module. Here it is given as "Bank Management Summary"
version (str): This module’s version, should follow semantic versioning rules
description (str): Extended description for the module, in reStructuredText.
Here it is given as "13.0.1.0.0". 13- represents the odoo version, 1 represents release one. the other numbers are updated on revisions of the versions.
author (str) : Name of the module author. Here it is given as "odoo Buddy"
website (str): Website URL for the module author. Here it is given as "http://www.odoo-buddy.com"
license (str, defaults: LGPL-3) : distribution license for the module. 
By default, if it is not added, the dafault is LGPL-3. You can change if your module has specific license.

Possible other values are : GPL-2, GPL-3 or any later version, AGPL-3, LGPL-3, Other OSI approved licence, OEEL-1 (Odoo Enterprise Edition License v1.0), OPL-1 (Odoo Proprietary License v1.0), Other proprietary
category (str, default: Uncategorized): classification category within Odoo, rough business domain for the module.

Although using existing categories is recommended, the field is freeform and unknown categories are created on-the-fly. Category hierarchies can be created using the separator / e.g. Foo / Bar will create a category Foo, a category Bar as child category of Foo, and will set Bar as the module’s category.

depends (list(str)): Odoo modules which must be loaded before this one, either because this module uses features they create or because it alters resources they define.

When a module is installed, all of its dependencies are installed before it. Likewise dependencies are loaded before a module is loaded.

data (list(str)): List of data files which must always be installed or updated with the module. A list of paths from the module root directory

demo (list(str)): List of data files which are only installed or updated in demonstration mode

auto_install (bool, default: False): If True, this module will automatically be installed if all of its dependencies are installed.

It is generally used for “link modules” implementing synergic integration between two otherwise independent modules.

For instance sale_crm depends on both sale and crm and is set to auto_install. When both sale and crm are installed, it automatically adds CRM campaigns tracking to sale orders without either sale or crm being aware of one another

application (bool, default: False): Whether the module should be considered as a fully-fledged application (True) or is just a technical module (False) that provides some extra functionality to an existing application module.

active (bool): This indicates whether this module is to be used or not. It is generally used to archive obsolete modules.

Others Fields(not added here):

external_dependencies (dict(key=list(str))): A dictionary containing python and/or binary dependencies.

For python dependencies, the python key must be defined for this dictionary and a list of python modules to be imported should be assigned to it.

For binary dependencies, the bin key must be defined for this dictionary and a list of binary executable names should be assigned to it.

The module won’t be installed if either the python module is not installed in the host machine or the binary executable is not found within the host machine’s PATH environment variable.

css (list(str)): Specify css files with custom rules to be imported, these files should be located in static/src/css inside the module.

images (list(str)): Specify image files to be used by the module.
installable (bool default: True)
Whether a user should be able to install the module from the Web UI or not.

maintainer (str): Person or entity in charge of the maintenance of this module, by default it is assumed that the author is the maintainer.
{pre_init, post_init, uninstall}_hook (str)

    Hooks for module installation/uninstallation, their value should be a string representing the name of a function defined inside the module’s __init__.py.

    pre_init_hook takes a cursor as its only argument, this function is executed prior to the module’s installation.

    post_init_hook takes a cursor and a registry as its arguments, this function is executed right after the module’s installation.

    uninstall_hook takes a cursor and a registry as its arguments, this function is executed after the module’s uninstallation.

    These hooks should only be used when setup/cleanup required for this module is either extremely difficult or impossible through the api.


### Step 4 : Add customs folder to your odoo.conf file

Open your odoo.conf file and add the location of your folder to the addons_path

Example:
[options]
addons_path = /home/real/o13-custom,/home/real/Desktop/ERGO/odoosrc/o13/odoo/addons,/home/real/Desktop/ERGO/odoosrc/o13/addons

### Step 5 : Restart your server

Open your terminal and use the following command:

./enV/bin/python3.6 ./odoosrc/o13/odoo-bin -c odoo.conf

### Step 6 : Check user interface

Now open http://127.0.0.1:8069 in your browser. Go to settings and at the bottom of the page, click on "Activate developer mode".

Now go Apps, remove the Apps filter and then search for your app:
Here it is ob_bank. You can also search with the name: Bank Management.

Your app will be shown. You can check the module information by clicking on the Three-dots and click on "Module Info".




### Step 7 : Add a icon to the module

If you have seen the module, there was no icon. Now, to add the icon, create a folder static folder, followed by description folder inside your static folder.

Now, add an image with .png format inside your description folder. Change the name of the image to icon.png.

Now if you restart the server, check the module. You can see the icon image.



If click on install, the module will be installed but you nothing will be shown yet on your User Interface.

Follow nest tutorials to the complete the custom module on Odoo 13.
