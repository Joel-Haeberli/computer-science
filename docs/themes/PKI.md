tags: #SPA #certificates
 
# PKI

links: [[611 SPA TOC - Certificates and PKI|SPA TOC - Certificates and PKI]] - [[themes/000 Index|Index]]

---

This topic was already handled in [[Public Key Infrastructure|AC2 - Public Key Infrastructure]]. This document adds some redundancy but summarizes the talking points discussed in the module SPA. 

## PKI Components

- Certificate Authority ([[Public Key Infrastructure#Certification Authority (CA)|CA]])
- Registration Authority ([[Public Key Infrastructure#Registration Authority (RA)|RA]])
- Validation Authority ([[Public Key Infrastructure#Validation Authority (VA)|VA]])
- End Entity ([[Public Key Infrastructure#End Entity (EE)|EE]])
- [[Public Key Infrastructure#Repository|Repository]]
## PKI Architecture

![[PKI-Overview.png]]

![[pki-architecture.png]]

## Certificate Request (PKCS#10)

![[certificate-request.png]]

```bash
openssl req -in newreq.pem -text
```

```
Certificate Request:
	Data:
		Version: 1 (0x0)
		Subject: C = CH, ST = Bern, L = Bern, O = BFH, OU = Informatics, CN = client01.n025.nslab.ch
		Subject Public Key Info:
			Public Key Algorithm: rsaEncryption
				Public-Key: (2048 bit)
				Modulus:
					00:a1:cb:f0:ef:cf:aa:dc:86:f5:
					...
				Exponent: 65537 (0x10001)
			Attributes:
				(none)
				Requested Extensions:
	Signature Algorithm: sha256WithRSAEncryption
	Signature Value:
		11:81:c3:64:19:22:bf:bb:10:5b:
		...
```

## How a certificate is created

![[certificate-creation.png]]


---
links: [[611 SPA TOC - Certificates and PKI|SPA TOC - Certificates and PKI]] - [[themes/000 Index|Index]]