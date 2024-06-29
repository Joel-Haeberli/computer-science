tags: #web-security

# Preparing for testing

links: [[507 WS TOC - Testing|WS TOC - Testing]] - [[themes/000 Index|Index]]

---

### Preparation questions

- Who is the owner / hoster and in what country is the website hosted?
	- Use [RDAP](https://en.wikipedia.org/wiki/Registration_Data_Access_Protocol) which replaces Whois
- Which language is used?
- Which architecture is used?
	- Framework, layers (?)
- Which CMS is used?
	- How is it configured?
	- What are the installed extensions?
- Which structure has the website?
	- Pages, navigation, secure area, insecure area

### Information gathering

- Testing for web application fingerprint
	- Is it possible to find server version / configuration?
	- Use the fingerprint of an application (order of http headers, capitalizations, different responses to malformed requests)
	- Tools like httprint and netcraft can be used
	- Goal: change config so that an attacker can't easily find information about the server / configuration
- Application discovery
	- An attacker would look for over applications on the domain using standard names like webmail.domain.com or domain.com/admin to find other applications
	- $\rightarrow$ Change default paths
- Analysis of error codes
	- Error codes can indicate what OS, web server, db is used $\rightarrow$ fingerprinting
- View the source
	- Attacker can check the website source and figure out what CSS and javascript libs are used
	- Comments can help understand the structure
- Draw a site map
	- Web spider can be used to map out the sites structure $\rightarrow$ wget, OWASP ZAP
	- Or surf by yourself
- List entry points
	- URL, parameters, GET parameters, POST form parameters, Cookies
	- AJAX, JSON, REST
	- DB listeners (should normally be closed)

---
links: [[507 WS TOC - Testing|WS TOC - Testing]] - [[themes/000 Index|Index]]