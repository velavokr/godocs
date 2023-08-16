---
layout: default
title: ALTER LOGIN
description: Reference and syntax for the ALTER LOGIN command.
great_grand_parent: SQL reference
grand_parent:  SQL commands
parent: Database object commands
---

# ALTER LOGIN

Updates the configuration of the specified login.

For more information, see [Managing logins](../../../Guides/managing-your-organization/managing-logins.md).

## Syntax

```sql
ALTER LOGIN <login_name> SET 
      [ IS_PASSWORD_ENABLED = { TRUE | FALSE } ]
      [ IS_MFA_ENABLED = { TRUE | FALSE } ]
      [ NETWORK_POLICY_NAME = <network_policy_name> ]
      [ IS_ORGANIZATION_ADMIN = { TRUE | FALSE } ]
      [ FIRST_NAME = <first_name> | DEFAULT ]
      [ LAST_NAME = <last_name> | DEFAULT ] 
```
or 

```ALTER LOGIN <login_name> RENAME TO <new_login_name>;```

| Parameter | Description |
| :--- | :--- |
| `<login_name>`                              | The name of the login in the form of an email address. The login must be unique within the organization.   |
| `IS_PASSWORD_ENABLED` | A `BOOLEAN` value specifying if login with password is enabled. By default this is `TRUE` and passwords can be used to log in. |
| `IS_MFA_ENABLED` | A `BOOLEAN` value specifying if the login has multi-factor authentication (MFA) enabled. By default this value is `FALSE`. If set to `TRUE`, an enrollment email will be sent to the `<login_name>`.  |
| `<network_policy_name>`                      | An optional parameter to define the network policy to link to the created login. |         
| `IS_ORGANIZATION_ADMIN` | A `BOOLEAN` value specifying if the login is an organization admin. By default this value is `FALSE`. | 
| `<first_name>`, `<last_name>` | The first and last name of the user to use the login. |
| `<new_login_name>`                              | The new name of the login in the form of an email address. The login must be unique within the organization. Note: if the login was provisioned via SSO, it cannot be renamed.  |

## Example

The following command will rename the "alexs@acme.com" login to "alexspotter@acme.com".

```ALTER LOGIN "alexs@acme.com" RENAME TO "alexspotter@acme.com";```

This command will set the user "alexs@acme.com" as an organization admin. 

```ALTER LOGIN "alexs@acme.com" SET IS_ORGANIZATION_ADMIN = TRUE;```