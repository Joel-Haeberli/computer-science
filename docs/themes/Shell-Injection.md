tags: #web-security #injection

# Shell-Injection

links: [[501 WS TOC - Injections|WS TOC - Injections]] - [[themes/000 Index|Index]]

---

## How it works

Shell-Injection is called after Unix shells but applies to all systems which allow software to programmatically execute command line. The idea of shell injection lies in poisoning the input to a function which allows the execution of commands on the systems shell. Such methods are common in most of programming languages and include:

- `system()` (PHP)
- `java.lang.Runtime.exec()`
- and many more

## Risks

Once the attacker finds a vulnerability to inject shell commands, he can execute everything he can bring through and the access rights of the process are sufficient. This includes:

- Creating files
- Read and modify config files
- Try privilege escalation techniques
- Implementing a reverse shell

## Techniques to use vulnerabilities

The techniques can be the same as described in [[SQL-Injection]]. First it makes sense to know which system is running the application and which shell is used to execute commands, since this defines which characters are useful for the task of invading the system through Shell-Injection.

## Protect

To protect from Shell-Injection try to not use any calls allowing to execute commands on the shell. If you see yourself forced to do so anyway, validate and sanitize the input and do not rely on methods of frameworks (they are unsafe with pretty high probability).

**eval is evil!**

---
links: [[501 WS TOC - Injections|WS TOC - Injections]] - [[themes/000 Index|Index]]