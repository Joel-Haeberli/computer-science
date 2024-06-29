tags: #web-security #injection

# XML-Injection

links: [[501 WS TOC - Injections|WS TOC - Injections]] - [[themes/000 Index|Index]]

---

## How it works

The system somehow uses XML. This can be an XML database, an API accepting XML and so on. The idea of XML-Injection is to somehow poison such a communication by hijacking the XML document. Like this the system shall be forced to behave somehow different as expected.

## Risks

The Risk of XML-Injection lies in API's not able to parse XML because they are not valid anymore.

## Techniques to use vulnerabilities

XML-Injection are caused by abusing metacharacters of XML. These include:

- Single Quote `'`
- Double Quote `"`
- `<` and `>`
- Comments `<!-- -->` 
- `&` char which signals linking to an XML class
- `CDATA` sections

With this we can perform various attacks:

- [[505 WS TOC - Cross Site Scripting (XSS)|XSS (Cross Site Scripting)]]
- [XXE (External Entity)](https://portswigger.net/web-security/xxe): with this we are for example able to read data from files (also from outside the servers network)
- Tag Injection

## Protect

Validate incoming XML. Deny XML documents containing unwanted or unknown content. Validate fields reading from the XML structure, escaping metacharacters. **Validate your inputs :)**

More on XML Security:

- [OWASP XML Cheatsheet](https://cheatsheetseries.owasp.org/cheatsheets/XML_Security_Cheat_Sheet.html)
- [XXE, XPath, XQuery](https://www.akto.io/blog/xml-injection-vulnerability-examples-cheatsheet-and-prevention)
- [XML Injection](https://www.synopsys.com/blogs/software-security/xml-external-entity-injection.html)

---
links: [[501 WS TOC - Injections|WS TOC - Injections]] - [[themes/000 Index|Index]]