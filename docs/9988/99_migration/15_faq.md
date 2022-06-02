---
title: Migration Issues to 2.5
summary: Using SKNEQY Database
authors: Wilson Loh
date: 2021-10-26
tag: 2.0, 3.0
---

## Database

### Table : base_module_uninstall

!!! error "Error Message"
    psycopg2.errors.NotNullViolation: null value in column "module_id" of relation "base_module_uninstall" violates not-null constraint

!!! note "Solution"
    - Use database tool ( pgadmin or DBeave), go to table "base_module_uninstall", select **Tool** then **Truncate**
    - Click **Next** Select **Restart Identiy** and **Cascade**
