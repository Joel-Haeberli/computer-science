tags: #web-security #injection

# LDAP-Injection

links: [[501 WS TOC - Injections|WS TOC - Injections]] - [[themes/000 Index|Index]]

---

## How it works

LDAP-Injections want to inject malicious input to an LDAP ([Lightweight Directory Access Protocol](https://en.wikipedia.org/wiki/Lightweight_Directory_Access_Protocol)) system. LDAP-Injections therefore try to exploit LDAP statements based on user input.

## Risks

The risks of LDAP-injection are that an attacker gains access to groups and users, which allows him to enumerate users and groups.

LDAP servers cannot be run in the DMZ of an organisation because it is responsible to authenticate and authorize users for tools used by the organisation. This means that if an attacker can manipulate LDAP, he has reached the private network of the organisation with his attack. So the attacker can control data behind authenticated firewalls.

## Techniques to use vulnerabilities

LDAP-Injections try to abuse the LDAP filter mechanisms. LDAP filter are build by defining operation binding conditions together, followed by the conditions:

- Simple filter: `(condition)`
- OR filter: `(|(condition)(other condition))`
- AND filter: `(&(condition)(other condition))`

These filters can be combined and encapsulated as you wish. 

Assume a program uses following filter to authenticate a user (accepting parameter `uname`and `pw`):

```
(&(USER=uname)(PASSWORD=pw))
```

If an attacker can inject the value `someusername)(&))` as parameter `uname`, this will result in the following filter which will prevent the password being checked and therefore the authentication can be bypassed:

```
(&(USER=someusername)(&))(PASSWORD=somepassword))
```

This filter contains two expressions. One is `(&(USER=someusername)(&))` and the other is `(PASSWORD=somepassword))`. The clue in this filter lies in the fact that just listing filters without an operator combining them will lead the LDAP interpreter to strip everything but the first expression in the list. This is because LDAP is buggy or accepts broken inputs on purpose.

## Protect

To protect against LDAP injection just **Validate the input**.

[OWASP LDAP Injection Prevention Cheatsheet](https://cheatsheetseries.owasp.org/cheatsheets/LDAP_Injection_Prevention_Cheat_Sheet.html)

---
links: [[501 WS TOC - Injections|WS TOC - Injections]] - [[themes/000 Index|Index]]