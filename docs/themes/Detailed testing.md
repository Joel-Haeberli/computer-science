tags: #web-security

# Detailed testing

links: [[507 WS TOC - Testing|WS TOC - Testing]] - [[themes/000 Index|Index]]

---

### Configuration Management Testing

- TLS
	- Verify the usage of strong ciphers
	- Use nmap for testing (`nmap -F -sV localhost`)
- DB listener testing
	- Shouldn't be exposed to the internet without restrictions
	- Shouldn't use default ports
	- Shouldn't use weak ciphers
	- Only allow access from authorized and trusted networks
	- Check fingerprinting too
- Infrastructure configuration management
	- Check all elements in the infrastructure for vulnerabilities
		- Firewalls, OS, Server, Database, LDAP
	- List all possible admin interfaces and from where they are accessible
		- Check access control (change default user / password, use strong cipher, etc.)
- Application configuration management
	- Ensure no default installations or sample files are left on the server
	- Check application comments $\rightarrow$ no information leaking
	- Verify that the server is only running necessary modules
	- Customize error pages (no stack traces)
	- Verify the server runs with minimized privileges
	- Make suer the server logs all access and errors
	- Ensure that the server handles overloads and prevent DoS
- Testing for file extension handling
	- Determine the way the server handles requests corresponding to files having different extensions
	- Determine what is returned as text and what is executed on the server
		- For example, if a `.inc` file containing PHP code is served as text, it could leak sensitive information like database credentials.
	- Examples of sensitive extensions: `.asa`,`.inc`,`.zip`,`.tar`,`.tgz`,(or other compressed files extensions) `.java`,`.txt`,`.pdf`,`.doc`,`.rtf`, . . .
- Old backup and unreferenced files
	- Files like `index.php.back` can be a security issue
	- Forgotten app.zip could leak source code
- Testing for HTTP Methods and Cross-Site Tracing (XST)
	- Identifying which http methods the server supports and ensuring that unsafe methods are disabled
	- Disable HTTP TRACE to prevent Cross-Site Tracing

### Data validation

- Test for [[505 WS TOC - Cross Site Scripting (XSS)|XSS]] and [[501 WS TOC - Injections|Injections]]
- Additional: ORM injection, SSI injection, XPath injection, IMAP / SMTP injections, buffer overflow testing, http splitting

### Authentication / Authorization

- TLS is used where ever needed / possible
- Check if it's possible to find valid users by interacting with authentication mechanism $\rightarrow$ for brute force attack
- Testing brute force (timeouts)
- Check if authentication schema can by bypassed / skipped
- Check for password reset vulnerability
- Check if logout and browser cache management is implemented correctly $\rightarrow$ delete session token etc.
- Captcha testing $\rightarrow$ avoid replay attack
- Test MFA, correct usage
- Test for race conditions $\rightarrow$ Users logging in at the same time, etc.

### Session management

- Understand session management schema and try to bypass it
- Check cookie attributes
	- secure: https
	- httponly: can't be used by javascript
	- domain or path cookie only sent to the legitimate issuer
- Test for session fixation
	- When an application does not renew the cookie after a successful user authentication, it could be possible to find a session fixation vulnerability and force a user to utilize a cookie known to the attacker.
- Test for exposed session variables
- Test for CSRF (Cross-Site-Request-Forgery)

### Authorization

- Test for path traversal (e.g. GET request with ../)
- Testing for bypassing authorization schema
- Testing for privilege escalation (horizontal or vertical escalation)

### Business logic

- Examples
	- Setting the quantity of a product as a negative number may result in funds being credited to the attacker
	- Access directly to the validation of an order without having paid for it
	- Being able to enter data with another identity

### AJAX / JSON

- Many endpoints $\rightarrow$ increased number of places an attacker can exploit
- Check that API doesn't accidentally exposes functions that are supposed to be internal
- Check APIs interaction with third party external services
- Blurred lines between client-side and server-side code

### DoS

- Test for SQL wild-card attacks: WHERE column LIKE, causing time-consuming searches
- Locking customer accounts: Attacker can trigger this
- User input as a loop counter: Attacker can cause performance issues or infinite loops
- Writing user provided data to disk: Could fill up disk space
- Failure to release resources: Memory leak
- Storing too much data in session: Could overwhelm memory

---
links: [[507 WS TOC - Testing|WS TOC - Testing]] - [[themes/000 Index|Index]]