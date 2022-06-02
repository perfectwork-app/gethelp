---
title: REST API
summary: Action
authors: Wilson Loh
date: 2021-10-26
tag: 3.0
---


## Base REST

This addon provides the basis to develop high level REST APIs for Odoo.

As Odoo becomes one of the central pieces of enterprise IT systems, it often becomes necessary to set up specialized service interfaces, so existing systems can interact with Odoo.

While the XML-RPC interface of Odoo comes handy in such situations, it requires a deep understanding of Odoo’s internal data model. When used extensively, it creates a strong coupling between Odoo internals and client systems, therefore increasing maintenance costs.

Once developed, an OpenApi documentation is generated from the source code and available via a Swagger UI served by your odoo server at https://my_odoo_server/api-docs.

### Installation

Need to install base_rest, base_rest_datamodel, data_model modules
<br /><br />
Need to have the following python libraries - 

!!!note
    apispec,
    cachetools,
    cerberus,
    jsondiff,
    marshmallow,
    marshmallow_objects,
    pyquerystring,
    parse-accept-language

### Configuration
If an error occurs when calling a method of a service (ie missing parameter, ..) the system returns only a general description of the problem without details. This is done on purpose to ensure maximum opacity on implementation details and therefore lower security issue.
<br /><br />
This restriction can be problematic when the services are accessed by an external system in development. To know the details of an error it is indeed necessary to have access to the log of the server. It is not always possible to provide this kind of access. That's why you can configure the server to run these services in development mode.
<br /><br />
To run the REST API in development mode you must add a new section '[base_rest]' with the option 'dev_mode=True' in the server config file.

!!!note
    [base_rest]
    dev_mode=True

When the REST API runs in development mode, the original description and a stack trace is returned in case of error. Be careful to not use this mode in production.