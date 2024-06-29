tags: #web-security #injection

# SQL-Injection

links: [[501 WS TOC - Injections|WS TOC - Injections]] - [[themes/000 Index|Index]]

---

## How it works

SQL-Injection uses SQL statements to smuggle SQL into the interpreter which is not supposed to be run by the program. Like this the attacker can for example read out tables which he should not be able to or he could even delete the content of a table.

Assume we have following query:

```sql
SELECT * FROM users WHERE username = REPLACEME1 and password = REPLACEME2;
```

If now an attacker somehow finds out how to replace the content of REPLACEME1 or REPLACEME2 in his favour, he can execute his own SQL on the system of the victim.

For example the attacker could gain control over parameter REPLACEME1 and replace it with `"hans"; #`. This would search for all users named 'hans' and not check the password in parameter REPLACEME2, because after giving the name the statement is terminated and the rest of the statement is commented out with the SQL comment char '#'.

## Risks

SQL Injections pose risks because:

- An attacker might pass commands directly to the compiler
- Modify commands such that security checks can be omitted and therefore data that should not be accessible gets visible for the attacker
- An attacker might be able to write files to the filesystem. This file could also be an executable.

## Techniques to use vulnerabilities

In order to use programs vulnerability for SQL injection, we could use following techniques:

- Try out injection the attacker code and comment out the rest
	- therefore use `#` or `--` at the end
- Make a condition to resolve to true all the time
	-  `1 = 1` or `null = null` and so on
- Change a condition in the `WHERE` part of the query
	- `SELECT * FROM table WHERE id = ID` $\rightarrow$ change ID
- Use `UNION ALL` to concatenate data of a second query
- Use `INTO OUTFILE` to write a file on the filesystem

## Protect

Avoid using the interpreter. Which means keeping data separate form commands and queries.

Use safe API such as Strongly typed parameterized queries (Prepared Statements) or an ORM (Object Relational Mapping). Remember to still do some validation because these techniques do only handle data escaping.

If you cannot avoid using an interpreter directly take care and be reminded of following techniques
:

- Validate your input
- Use Prepared Statements (strongly typed parameterized queries)
- Enforce least privilege
- Avoid detailed error messages
- Use stored procedures
- Never use a dynamic query interface such as `mysql_query()` (PHP).
- Refer to use simple escaping functions (they are not sufficient and insecure)

### Prepared Statements

Prepared statements are the solution to the problem of SQL-Injection. They are precompiled and parameters are added after the precompilation. This will make replacing parameters in queries type-safe and attacks like a comment char at the end will not have the effect the attacker wants it to have. 

Be sure to escape string parameters using quotes. Otherwise an attacker might smuggle his SQL statements into the execution:

Assume our prepared statement is:

```sql
UPDATE users SET name = :name WHERE id = :id;
```

This allows the attacke to inject anything in the `:name`-parameter, because it's a string param and it is not escaped using quotes. The better prepared statement is:

```sql
UPDATE users SET name = ':name' WHERE id = :id
```

Take care that the library you use, is binding parameters after validating them for type. Otherwise this query could still introduce a vulnerability with the `:id`-parameter. 

---
links: [[501 WS TOC - Injections|WS TOC - Injections]] - [[themes/000 Index|Index]]