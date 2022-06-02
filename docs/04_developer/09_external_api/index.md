---
title: External API
summary: This is Developer Guide
authors:
  - Wilson Loh
date: 2021-10-26
---

## Introduction

PerfectWORK is usually extended internally via modules, but many of its features and all of its data are also available from the outside for external analysis or integration with various tools. Part of the Models API is easily available over [XML-RPC](https://en.wikipedia.org/wiki/XML-RPC) and accessible from a variety of languages.

## Connection

### Configuration

If you already have an PerfectWORK server installed, you can just use its parameters

!!!info
    To make exploration simpler, you can also ask https://demo.perfectwork.app for a test database.

=== "Python"

    ``` python
    import xmlrpc.client
    info = xmlrpc.client.ServerProxy('https://demo.perfectwork.app/start').start()
    url, db, username, password = info['host'], info['database'], info['user'], info['password']
    ```

=== "Ruby"

    ``` ruby
    require "xmlrpc/client"
    info = XMLRPC::Client.new2('https://demo.perfectwork.app/start').call('start')
    url, db, username, password = info['host'], info['database'], info['user'], info['password']
    ```

=== "PHP"

    ``` php
    require_once('ripcord.php');
    $info = ripcord::client('https://demo.perfectwork.app/start')->start();
    list($url, $db, $username, $password) = array($info['host'], $info['database'], $info['user'], $info['password']);
    ```

=== "Java"

    ``` java
    final XmlRpcClient client = new XmlRpcClient();

    final XmlRpcClientConfigImpl start_config = new XmlRpcClientConfigImpl();
    start_config.setServerURL(new URL("https://demo.perfectwork.app/start"));
    final Map<String, String> info = (Map<String, String>)client.execute(
        start_config, "start", emptyList());

    final String url = info.get("host"),
        db = info.get("database"),
        username = info.get("user"),
        password = info.get("password");
    ```

!!! note
    These examples use the [Apache XML-RPC](https://ws.apache.org/xmlrpc/) library. <br>
    The examples do not include imports as these imports couldn’t be pasted in the code.

### Logging in

PerfectWORK requires users of the API to be authenticated before they can query most data.
<br /><br />
The _xmlrpc/2/common_ endpoint provides meta-calls which don’t require authentication, such as the authentication itself or fetching version information. To verify if the connection information is correct before trying to authenticate, the simplest call is to ask for the server’s version. The authentication itself is done through the _authenticate_ function and returns a user identifier (_uid_) used in authenticated calls instead of the login.

=== "Python"

    ``` python
    common = xmlrpc.client.ServerProxy('{}/xmlrpc/2/common'.format(url))
    common.version()
    ```

=== "Ruby"

    ``` ruby
    common = XMLRPC::Client.new2("#{url}/xmlrpc/2/common")
    common.call('version')
    ```

=== "PHP"

    ``` php
    $common = ripcord::client("$url/xmlrpc/2/common");
    $common->version();
    ```

=== "Java"

    ``` java
    final XmlRpcClientConfigImpl common_config = new XmlRpcClientConfigImpl();
    common_config.setServerURL(new URL(String.format("%s/xmlrpc/2/common", url)));
    client.execute(common_config, "version", emptyList());
    ```

**Result**:
``` 
{ "server_version": "13.0", "server_version_info": [13, 0, 0, "final", 0], "server_serie": "13.0", "protocol_version": 1, } `
```

=== "Python"

    ``` python
    uid = common.authenticate(db, username, password, {})
    ```

=== "Ruby"

    ``` ruby
    uid = common.call('authenticate', db, username, password, {})
    ```

=== "PHP"

    ``` php
    $uid = $common->authenticate($db, $username, $password, array());
    ```

=== "Java"

    ``` java
    int uid = (int)client.execute(common_config, "authenticate", asList(db, username, password, emptyMap()));
    ```

### Calling Methods

The second endpoint is _xmlrpc/2/object_. It is used to call methods of PerfectWORK data models via the _execute_kw_ RPC function.
<br /><br />
Each call to _execute_kw_ takes the following parameters:

- the database to use, a string
- the user id (retrieved through _authenticate_), an integer
- the user’s password, a string
- the model name, a string
- the method name, a string
- an array/list of parameters passed by position
- a mapping/dict of parameters to pass by keyword (optional)

!!!Example
    For instance, to see if we can read the _res.partner_ model, we can call _check_access_rights_ with _operation_ passed by position and _raise_exception_ passed by keyword (in order to get a true/false result rather than true/error):

    === "Python"

        ``` python
        models = xmlrpc.client.ServerProxy('{}/xmlrpc/2/object'.format(url))
        models.execute_kw(db, uid, password, 'res.partner', 'check_access_rights', ['read'], {'raise_exception': False})
        ```

    === "Ruby"

        ``` ruby
        models = XMLRPC::Client.new2("#{url}/xmlrpc/2/object").proxy
        models.execute_kw(db, uid, password, 'res.partner', 'check_access_rights', ['read'], {raise_exception: false})
        ```

    === "PHP"

        ``` php
        $models = ripcord::client("$url/xmlrpc/2/object");
        $models->execute_kw($db, $uid, $password, 'res.partner', 'check_access_rights', array('read'), array('raise_exception' => false));
        ```
    === "Java"

        ```java
        final XmlRpcClient models = new XmlRpcClient() {
            setConfig(new XmlRpcClientConfigImpl() {
                setServerURL(new URL(String.format("%s/xmlrpc/2/object", url)));
            });
        };
        models.execute("execute_kw", asList(
            db, uid, password,
            "res.partner", "check_access_rights",
            asList("read"),
            new HashMap() { put("raise_exception", false); }
        ));
        ```

    **Result**:
        ``` 
        true
        ```
### List Records
Records can be listed and filtered via *search()*.
<br /><br />
*search()* takes a mandatory *domain* filter (possibly empty), and returns the database identifiers of all records matching the filter.
!!!Example
    To list customer companies, for instance:

    === "Python"

        ```python
        models.execute_kw(db, uid, password, 'res.partner', 'search', [[['is_company', '=', True]]])
        ```

    === "Ruby"

        ```ruby
        models.execute_kw(db, uid, password, 'res.partner', 'search', [[['is_company', '=', true]]])
        ```

    === "PHP"

        ```php
        $models->execute_kw($db, $uid, $password, 'res.partner', 'search', array(array(array('is_company', '=', true))));
        ```
    === "Java"

        ```java
        asList((Object[])models.execute("execute_kw", asList(
            db, uid, password,
            "res.partner", "search",
            asList(asList(
                asList("is_company", "=", true)))
        )));
        ```
    **Result**:
        ```
        [7, 18, 12, 14, 17, 19, 8, 31, 26, 16, 13, 20, 30, 22, 29, 15, 23, 28, 74]
        ```

#### Pagination
By default a search will return the ids of all records matching the condition, which may be a huge number. offset and limit parameters are available to only retrieve a subset of all matched records. 

!!!Example
    To list customer companies, for instance:

    === "Python"

        ``` python
        models.execute_kw(db, uid, password, 'res.partner', 'search', [[['is_company', '=', True]]], {'offset': 10, 'limit': 5})
        ```

    === "Ruby"

        ``` ruby
        models.execute_kw(db, uid, password, 'res.partner', 'search', [[['is_company', '=', true]]], {offset: 10, limit: 5})
        ```

    === "PHP"

        ``` php
        $models->execute_kw($db, $uid, $password, 'res.partner', 'search', array(array(array('is_company', '=', true))), array('offset'=>10, 'limit'=>5));
        ```
    === "Java"

        ```java
        asList((Object[])models.execute("execute_kw", asList(
            db, uid, password,
            "res.partner", "search",
            asList(asList(
                asList("is_company", "=", true))),
            new HashMap() { put("offset", 10); put("limit", 5); }
        )));
        ```
    Result:
        ```json 
        [13, 20, 30, 22, 29]
        ```
### Count records
Rather than retrieve a possibly gigantic list of records and count them, _search_count()_ can be used to retrieve only the number of records matching the query. It takes the same _domain_ filter as _search()_ and no other parameter.

!!!Example
    To list customer companies, for instance:

    === "Python"

        ``` python
        models.execute_kw(db, uid, password, 'res.partner', 'search_count', [[['is_company', '=', True]]])
        ```

    === "Ruby"

        ``` ruby
        models.execute_kw(db, uid, password, 'res.partner', 'search_count', [[['is_company', '=', true]]])
        ```

    === "PHP"

        ``` php
        $models->execute_kw($db, $uid, $password, 'res.partner', 'search_count', array(array(array('is_company', '=', true))));
        ```
    === "Java"

        ```java
        (Integer)models.execute("execute_kw", asList(
            db, uid, password,
            "res.partner", "search_count",
            asList(asList(
                asList("is_company", "=", true)))
        ));
        ```
    Result:
        ```json 
        19
        ```
!!!Note

    Calling _search_ then _search_count_ (or the other way around) may not yield coherent results if other users are using the server: stored data could have changed between the calls.

### Read records
Record data are accessible via the _read()_ method, which takes a list of ids (as returned by _search()_), and optionally a list of fields to fetch. By default, it fetches all the fields the current user can read, which tends to be a huge amount.

!!!Example

    === "Python"

        ``` python
        ids = models.execute_kw(db, uid, password, 'res.partner', 'search', [[['is_company', '=', True]]], {'limit': 1})
        [record] = models.execute_kw(db, uid, password, 'res.partner', 'read', [ids])
        # count the number of fields fetched by default
        len(record)
        ```

    === "Ruby"

        ``` ruby
        ids = models.execute_kw(db, uid, password, 'res.partner', 'search', [[['is_company', '=', true]]], {limit: 1})
        record = models.execute_kw(db, uid, password, 'res.partner', 'read', [ids]).first
        # count the number of fields fetched by default
        record.length
        ```

    === "PHP"

        ``` php
        $ids = $models->execute_kw($db, $uid, $password, 'res.partner', 'search', array(array(array('is_company', '=', true))), array('limit'=>1));
        $records = $models->execute_kw($db, $uid, $password, 'res.partner', 'read', array($ids));
        // count the number of fields fetched by default
        count($records[0]);
        ```
    === "Java"

        ```java
        final List ids = asList((Object[])models.execute(
            "execute_kw", asList(
                db, uid, password,
                "res.partner", "search",
                asList(asList(
                    asList("is_company", "=", true))),
                new HashMap() { put("limit", 1); })));
        final Map record = (Map)((Object[])models.execute(
            "execute_kw", asList(
                db, uid, password,
                "res.partner", "read",
                asList(ids)
            )
        ))[0];
        // count the number of fields fetched by default
        record.size();
        ```
    Result:
        ```json 
        121
        ```
    Conversely, picking only three fields deemed interesting.

    === "Python"

        ``` python
        models.execute_kw(db, uid, password, 'res.partner', 'read', [ids], {'fields': ['name', 'country_id', 'comment']})
        ```

    === "Ruby"

        ``` ruby
        models.execute_kw(db, uid, password, 'res.partner', 'read', [ids], {fields: %w(name country_id comment)})
        ```

    === "PHP"

        ``` php
        $models->execute_kw($db, $uid, $password, 'res.partner', 'read', array($ids), array('fields'=>array('name', 'country_id', 'comment')));
        ```
    === "Java"

        ```java
        asList((Object[])models.execute("execute_kw", asList(
            db, uid, password,
            "res.partner", "read",
            asList(ids),
            new HashMap() {
                put("fields", asList("name", "country_id", "comment"));
            }
        )));
        ```
    Result:
        ```json 
        [{"comment": false, "country_id": [21, "Belgium"], "id": 7, "name": "Agrolait"}]
        ```
!!!Note
    Even if the _id_ field is not requested, it is always returned.

### List record fields
_fields_get()_ can be used to inspect a model’s fields and check which ones seem to be of interest.
<br /><br />
Because it returns a large amount of meta-information (it is also used by client programs) it should be filtered before printing, the most interesting items for a human user are string (the field’s label), _help_ (a help text if available) and _type_ (to know which values to expect, or to send when updating a record).

!!!Example

    === "Python"

        ``` python
        models.execute_kw(db, uid, password, 'res.partner', 'fields_get', [], {'attributes': ['string', 'help', 'type']})
        ```

    === "Ruby"

        ``` ruby
        models.execute_kw(db, uid, password, 'res.partner', 'fields_get', [], {attributes: %w(string help type)})
        ```

    === "PHP"

        ``` php
        $models->execute_kw($db, $uid, $password, 'res.partner', 'fields_get', array(), array('attributes' => array('string', 'help', 'type')));
        ```
    === "Java"

        ```java
        (Map<String, Map<String, Object>>)models.execute("execute_kw", asList(
            db, uid, password,
            "res.partner", "fields_get",
            emptyList(),
            new HashMap() {
                put("attributes", asList("string", "help", "type"));
            }
        ));
        ```
    Result:
        ```json 
        {
        "ean13": {
            "type": "char",
            "help": "BarCode",
            "string": "EAN13"
        },
        "property_account_position_id": {
            "type": "many2one",
            "help": "The fiscal position will determine taxes and accounts used for the partner.",
            "string": "Fiscal Position"
        },
        "signup_valid": {
            "type": "boolean",
            "help": "",
            "string": "Signup Token is Valid"
        },
        "date_localization": {
            "type": "date",
            "help": "",
            "string": "Geo Localization Date"
        },
        "ref_company_ids": {
            "type": "one2many",
            "help": "",
            "string": "Companies that refers to partner"
        },
        "sale_order_count": {
            "type": "integer",
            "help": "",
            "string": "# of Sales Order"
        },
        "purchase_order_count": {
            "type": "integer",
            "help": "",
            "string": "# of Purchase Order"
        },
        ```
### Search and read
Because it is a very common task, PerfectWORK provides a _search_read()_ shortcut which, as its name suggests, is equivalent to a _search()_ followed by a _read()_, but avoids having to perform two requests and keep ids around.
<br /><br />
Its arguments are similar to _search()_’s, but it can also take a list of fields (like _read()_, if that list is not provided it will fetch all fields of matched records).

!!!Example

    === "Python"

        ``` python
        ids = models.execute_kw(db, uid, password, 'res.partner', 'search', [[['is_company', '=', True]]], {'limit': 1})
        [record] = models.execute_kw(db, uid, password, 'res.partner', 'read', [ids])
        # count the number of fields fetched by default
        len(record)
        ```

    === "Ruby"

        ``` ruby
        ids = models.execute_kw(db, uid, password, 'res.partner', 'search', [[['is_company', '=', true]]], {limit: 1})
        record = models.execute_kw(db, uid, password, 'res.partner', 'read', [ids]).first
        # count the number of fields fetched by default
        record.length
        ```

    === "PHP"

        ``` php
        $ids = $models->execute_kw($db, $uid, $password, 'res.partner', 'search', array(array(array('is_company', '=', true))), array('limit'=>1));
        $records = $models->execute_kw($db, $uid, $password, 'res.partner', 'read', array($ids));
        // count the number of fields fetched by default
        count($records[0]);
        ```
    === "Java"

        ```java
        asList((Object[])models.execute("execute_kw", asList(
            db, uid, password,
            "res.partner", "search_read",
            asList(asList(
                asList("is_company", "=", true))),
            new HashMap() {
                put("fields", asList("name", "country_id", "comment"));
                put("limit", 5);
            }
        )));
        ```
    Result:
        ```json 
        121
        ```
    Conversely, picking only three fields deemed interesting.

    === "Python"

        ``` python
        models.execute_kw(db, uid, password, 'res.partner', 'search_read', [[['is_company', '=', True]]], {'fields': ['name', 'country_id', 'comment'], 'limit': 5})
        ```

    === "Ruby"

        ``` ruby
        models.execute_kw(db, uid, password, 'res.partner', 'search_read', [[['is_company', '=', true]]], {fields: %w(name country_id comment), limit: 5})
        ```

    === "PHP"

        ``` php
        $models->execute_kw($db, $uid, $password, 'res.partner', 'search_read', array(array(array('is_company', '=', true))), array('fields'=>array('name', 'country_id', 'comment'), 'limit'=>5));
        ```
    === "Java"

        ```java
        asList((Object[])models.execute("execute_kw", asList(
            db, uid, password,
            "res.partner", "search_read",
            asList(asList(
                asList("is_company", "=", true))),
            new HashMap() {
                put("fields", asList("name", "country_id", "comment"));
                put("limit", 5);
            }
        )));
        ```
    Result:
        ```json 
        [
            {
                "comment": false,
                "country_id": [ 21, "Belgium" ],
                "id": 7,
                "name": "Agrolait"
            },
            {
                "comment": false,
                "country_id": [ 76, "France" ],
                "id": 18,
                "name": "Axelor"
            },
            {
                "comment": false,
                "country_id": [ 233, "United Kingdom" ],
                "id": 12,
                "name": "Bank Wealthy and sons"
            },
            {
                "comment": false,
                "country_id": [ 105, "India" ],
                "id": 14,
                "name": "Best Designers"
            },
            {
                "comment": false,
                "country_id": [ 76, "France" ],
                "id": 17,
                "name": "Camptocamp"
            }
        ]
        ```
### Create records
Records of a model are created using _create()_. The method creates a single record and returns its database identifier.
<br /><br />
_create()_ takes a mapping of fields to values, used to initialize the record. For any field which has a default value and is not set through the mapping argument, the default value will be used.

!!!Example

    === "Python"

        ``` python
        id = models.execute_kw(db, uid, password, 'res.partner', 'create', [{'name': "New Partner"}])
        ```

    === "Ruby"

        ``` ruby
        id = models.execute_kw(db, uid, password, 'res.partner', 'create', [{name: "New Partner"}])
        ```

    === "PHP"

        ``` php
        $id = $models->execute_kw($db, $uid, $password, 'res.partner', 'create', array(array('name'=>"New Partner")));
        ```
    === "Java"

        ```java
        final Integer id = (Integer)models.execute("execute_kw", asList(
            db, uid, password,
            "res.partner", "create",
            asList(new HashMap() { put("name", "New Partner"); })
        ));
        ```
    Result:
        ```json 
        121
        ```
    Conversely, picking only three fields deemed interesting.

    === "Python"

        ``` python
        models.execute_kw(db, uid, password, 'res.partner', 'search_read', [[['is_company', '=', True]]], {'fields': ['name', 'country_id', 'comment'], 'limit': 5})
        ```

    === "Ruby"

        ``` ruby
        models.execute_kw(db, uid, password, 'res.partner', 'search_read', [[['is_company', '=', true]]], {fields: %w(name country_id comment), limit: 5})
        ```

    === "PHP"

        ``` php
        $models->execute_kw($db, $uid, $password, 'res.partner', 'search_read', array(array(array('is_company', '=', true))), array('fields'=>array('name', 'country_id', 'comment'), 'limit'=>5));
        ```
    === "Java"

        ```java
        asList((Object[])models.execute("execute_kw", asList(
            db, uid, password,
            "res.partner", "search_read",
            asList(asList(
                asList("is_company", "=", true))),
            new HashMap() {
                put("fields", asList("name", "country_id", "comment"));
                put("limit", 5);
            }
        )));
        ```
    Result:
        ```json 
            78
        ```
!!!Warning
    While most value types are what would expect (integer for Integer, string for Char or Text)

    - _Date_, _Datetime_ and _Binary_ fields use string values
    - _One2many_ and _Many2many_ use a special command protocol detailed in the _documentation to the write method_.

### Update records
Records can be updated using write(). It takes a list of records to update and a mapping of updated fields to values similar to create().
<br /><br />
Multiple records can be updated simultaneously, but they will all get the same values for the fields being set. It is not possible to perform “computed” updates (where the value being set depends on an existing value of a record).

!!!Example

    === "Python"

        ``` python
        models.execute_kw(db, uid, password, 'res.partner', 'write', [[id], {'name': "Newer partner"}])
        # get record name after having changed it
        models.execute_kw(db, uid, password, 'res.partner', 'name_get', [[id]])
        ```

    === "Ruby"

        ``` ruby
        models.execute_kw(db, uid, password, 'res.partner', 'write', [[id], {name: "Newer partner"}])
        # get record name after having changed it
        models.execute_kw(db, uid, password, 'res.partner', 'name_get', [[id]])
        ```

    === "PHP"

        ``` php
        $models->execute_kw($db, $uid, $password, 'res.partner', 'write', array(array($id), array('name'=>"Newer partner")));
        // get record name after having changed it
        $models->execute_kw($db, $uid, $password,'res.partner', 'name_get', array(array($id)));
        ```
    === "Java"

        ```java
        models.execute("execute_kw", asList(
            db, uid, password,
            "res.partner", "write",
            asList(
                asList(id),
                new HashMap() { put("name", "Newer Partner"); }
            )
        ));
        // get record name after having changed it
        asList((Object[])models.execute("execute_kw", asList(
            db, uid, password,
            "res.partner", "name_get",
            asList(asList(id))
        )));
        ```
    Result:
        ```json 
        [[78, "Newer partner"]]
        ```

### Delete records
Records can be deleted in bulk by providing their ids to _unlink()_.

!!!Example

    === "Python"

        ``` python
        models.execute_kw(db, uid, password, 'res.partner', 'unlink', [[id]])
        # check if the deleted record is still in the database
        models.execute_kw(db, uid, password, 'res.partner', 'search', [[['id', '=', id]]])
        ```

    === "Ruby"

        ``` ruby
        models.execute_kw(db, uid, password, 'res.partner', 'unlink', [[id]])
        # check if the deleted record is still in the database
        models.execute_kw(db, uid, password, 'res.partner', 'search', [[['id', '=', id]]])
        ```

    === "PHP"

        ``` php
        $models->execute_kw($db, $uid, $password, 'res.partner', 'unlink', array(array($id)));
        // check if the deleted record is still in the database
        $models->execute_kw($db, $uid, $password, 'res.partner', 'search', array(array(array('id', '=', $id))));
        ```
    === "Java"

        ```java
        models.execute("execute_kw", asList(
            db, uid, password,
            "res.partner", "unlink",
            asList(asList(id))));
        // check if the deleted record is still in the database
        asList((Object[])models.execute("execute_kw", asList(
            db, uid, password,
            "res.partner", "search",
            asList(asList(asList("id", "=", 78)))
        )));
        ```
    Result:
        ```json 
        []
        ```
### Inspection and introspection
While we previously used fields_get() to query a model and have been using an arbitrary model from the start, PerfectWORK stores most model metadata inside a few meta-models which allow both querying the system and altering models and fields (with some limitations) on the fly over XML-RPC.
<br /><br />

- **ir.model** <br>
    Provides information about PerfectWORK models via its various fields.

- **name** <br>
a human-readable description of the model

- **model** <br>
the name of each model in the system

- **state** <br>
whether the model was generated in Python code (base) or by creating an ir.model record (manual)

- **field_id** <br>
list of the model’s fields through a One2many to ir.model.fields

- **view_ids** <br>
One2many to the Views defined for the model

- **access_ids** <br>
One2many relation to the Access Rights set on the model

_ir.model_ can be used to

- Query the system for installed models (as a precondition to operations on the model or to explore the system’s content).
- Get information about a specific model (generally by listing the fields associated with it).
- Create new models dynamically over RPC.

!!! Important
    - Custom model names must start with x_.
    - The state must be provided and set to manual, otherwise the model will not be loaded.
    - It is not possible to add new methods to a custom model, only fields.

!!!Example

    === "Python"

        ``` python
        models.execute_kw(db, uid, password, 'ir.model', 'create', [{
            'name': "Custom Model",
            'model': "x_custom_model",
            'state': 'manual',
        }])
        models.execute_kw(db, uid, password, 'x_custom_model', 'fields_get', [], {'attributes': ['string', 'help', 'type']})
        ```

    === "Ruby"

        ``` ruby
        models.execute_kw(db, uid, password, 'ir.model', 'create', [{
            name: "Custom Model",
            model: 'x_custom_model',
            state: 'manual' 
        }])
        fields = models.execute_kw(db, uid, password, 'x_custom_model', 'fields_get', [], {attributes: %w(string help type)})
        ```

    === "PHP"

        ``` php
        $models->execute_kw($db, $uid, $password, 'ir.model', 'create', array(array(
            'name' => "Custom Model",
            'model' => 'x_custom_model',
            'state' => 'manual'
        )));
        $models->execute_kw($db, $uid, $password, 'x_custom_model', 'fields_get', array(), array('attributes' => array('string', 'help', 'type')));
        ```
    === "Java"

        ```java
        models.execute(
            "execute_kw", asList(
                db, uid, password,
                "ir.model", "create",
                asList(new HashMap<String, Object>() {
                    put("name", "Custom Model");
                    put("model", "x_custom_model");
                    put("state", "manual");
                })
        ));
        final Object fields = models.execute(
            "execute_kw", asList(
            db, uid, password,
            "x_custom_model", "fields_get",
            emptyList(),
            new HashMap<String, Object> () {
                put("attributes", asList(
                    "string",
                    "help",
                    "type"));
            }
        ));
        ```
    Result:
        ```json 
        {
          "create_uid": {
              "type": "many2one",
              "string": "Created by"
          },
          "create_date": {
              "type": "datetime",
              "string": "Created on"
          },
          "__last_update": {
              "type": "datetime",
              "string": "Last Modified on"
          },
          "write_uid": {
              "type": "many2one",
              "string": "Last Updated by"
          },
          "write_date": {
              "type": "datetime",
              "string": "Last Updated on"
          },
          "display_name": {
              "type": "char",
              "string": "Display Name"
          },
          "id": {
              "type": "integer",
              "string": "Id"
          }   
        }   
        ```

- **ir.model.fields** <br>
Provides information about the fields of PerfectWORK data models and allows adding custom fields without using Python code.

- **model_id** <br>
Many2one to ir.model to which the field belongs

- **name** <br>
the field’s technical name (used in read or write)

- **field_description** <br>
the field’s user-readable label (e.g. string in fields_get)

- **ttype** <br>
the type of field to create

- **state** <br>
whether the field was created via Python code (base) or via ir.model.fields (manual)

- **required, readonly, translate** <br>
enables the corresponding flag on the field

- **groups** <br>
field-level access control, a Many2many to res.groups

- **selection, size, on_delete, relation, relation_field, domain** <br>
type-specific properties and customizations, see the fields documentation for details

!!! Important

    - Like custom models, only new fields created with state="manual" are activated as actual fields on the model.
    - Computed fields can not be added via _ir.model.fields_, some field meta-information (defaults, onchange) can not be set either.

!!!Example

    === "Python"

        ``` python
        id = models.execute_kw(db, uid, password, 'ir.model', 'create', [{
            'name': "Custom Model",
            'model': "x_custom",
            'state': 'manual',
        }])
        models.execute_kw(db, uid, password, 'ir.model.fields', 'create', [{
            'model_id': id,
            'name': 'x_name',
            'ttype': 'char',
            'state': 'manual',
            'required': True,
        }])
        record_id = models.execute_kw(db, uid, password, 'x_custom', 'create', [{'x_name': "test record"}])
        models.execute_kw(db, uid, password, 'x_custom', 'read', [[record_id]])
        ```

    === "Ruby"

        ``` ruby
        id = models.execute_kw(db, uid, password, 'ir.model', 'create', [{
            name: "Custom Model",
            model: "x_custom",
            state: 'manual'
        }])
        models.execute_kw(db, uid, password, 'ir.model.fields', 'create', [{
            model_id: id,
            name: "x_name",
            ttype: "char",
            state: "manual",
            required: true
        }])
        record_id = models.execute_kw(db, uid, password, 'x_custom', 'create', [{x_name: "test record"}])
        models.execute_kw(db, uid, password, 'x_custom', 'read', [[record_id]])
        ```

    === "PHP"

        ``` php
        $id = $models->execute_kw($db, $uid, $password, 'ir.model', 'create', array(array(
            'name' => "Custom Model",
            'model' => 'x_custom',
            'state' => 'manual'
        )));
        $models->execute_kw($db, $uid, $password, 'ir.model.fields', 'create', array(array(
            'model_id' => $id,
            'name' => 'x_name',
            'ttype' => 'char',
            'state' => 'manual',
            'required' => true
        )));
        $record_id = $models->execute_kw($db, $uid, $password, 'x_custom', 'create', array(array('x_name' => "test record")));
        $models->execute_kw($db, $uid, $password, 'x_custom', 'read', array(array($record_id)));

        ```
    === "Java"

        ```java
        final Integer id = (Integer)models.execute(
            "execute_kw", asList(
                db, uid, password,
                "ir.model", "create",
                asList(new HashMap<String, Object>() {
                    put("name", "Custom Model");
                    put("model", "x_custom");
                    put("state", "manual");
                })
        ));
        models.execute(
            "execute_kw", asList(
                db, uid, password,
                "ir.model.fields", "create",
                asList(new HashMap<String, Object>() {
                    put("model_id", id);
                    put("name", "x_name");
                    put("ttype", "char");
                    put("state", "manual");
                    put("required", true);
                })
        ));
        final Integer record_id = (Integer)models.execute(
            "execute_kw", asList(
                db, uid, password,
                "x_custom", "create",
                asList(new HashMap<String, Object>() {
                    put("x_name", "test record");
                })
        ));

        client.execute(
            "execute_kw", asList(
                db, uid, password,
                "x_custom", "read",
                asList(asList(record_id))
        ));
        ```
    Result:
        ```json 
        [
          {
              "create_uid": [1, "Administrator"],
              "x_name": "test record",
              "__last_update": "2014-11-12 16:32:13",
              "write_uid": [1, "Administrator"],
              "write_date": "2014-11-12 16:32:13",
              "create_date": "2014-11-12 16:32:13",
              "id": 1,
              "display_name": "test record"
          }
        ]   
        ```