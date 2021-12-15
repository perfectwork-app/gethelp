---
title: Actions
summary: Action
authors: Wilson Loh
date: 2021-10-26
tag: 3.0
---


## Server Action

In PerfectWORK we can execute server actions, an intriguing feature using which the customers can meet their requirements. Let's discuss the functionality and how to use various parameters in server actions accordingly.

<br />

Server Actions are actions that can be executed automatically. These actions are added to the ‘Action’ contextual menu.

<br />

To create a server action create a data record in data.xml file as shown below:

``` xml title="Server Action in XML"
<?xml version="1.0" encoding="utf-8"?>
<odoo>
	<data>
    	<record model="ir.actions.server" id="action_working_on_something">
            <field name="name">ETL - Working On Something</field>
            <field name="model_id" ref="model_res_partner"/>
            <field name="binding_model_id" ref="model_res_partner"/>
            <field name="binding_view_types">list</field>
            <field name="state">code</field>
            <field name="code">model.python_method()
            </field>
        </record>
	</data>
</odoo>
```

- **binding_model_id** - Model linked to the action.

- **name** - Name of the server action.

- **state** - The field name ‘state’ specifies the type of server action.

In the above example, we are going to call the model method - python_method()

!!! note 
    We can also add server actions easily via the user interface. In order to create a server action activate the developer mode, go to Settings --> Technical -->Server Actions.



