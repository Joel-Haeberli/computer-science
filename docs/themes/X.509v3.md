tags: #SPA #certificates
 
# X.509v3

links: [[611 SPA TOC - Certificates and PKI|SPA TOC - Certificates and PKI]] - [[themes/000 Index|Index]]

---

This topic was already handled in [[X.509 Certificates|AC2 X.509 - X.509 Certificates]]. In this document we will summarize the direct talking point from the module SPA.

## X.509 Certificate

- International Telecommunication Unit (ITU) standard, defining the format of public key certificates
- Assumes a strict hierarchical system of certificate authorities (CAs) to issue certificates.
- Version 3 of X.509 include the support of other topologies like bridges and meshes
- Common PKI installation use LDAP or AD server to store certificates
- Certificates should be provided with the full chain of trust.
	- Root, top level (self-signed) CA certificates
	- End-entity, end-user, leaf certificates
	- Intermediate, subordinate CA certificates

## X.509v3 

![[x509v3-certificate-overview.png]]

### Structure

X.509v3 certificates are ASN.1 encoded. Followed are the mandatory fields:

```
Certificate:
	Data:
		Version: 3 (0x2)
		Serial Number:
			5b:34:0f:bf:66:b8:79:83:70:bb:db:18:b7:28:ad:7d:0f:dc:00:cc
		Signature Algorithm: sha256WithRSAEncryption
		Issuer: C = CH, O = QuoVadis Trustlink Schweiz AG, CN = QuoVadis Swiss Advanced CA G4
		Validity
			Not Before: Jul 26 10:20:10 2021 GMT
			Not After : Jul 26 10:30:00 2024 GMT
		Subject: C = CH, ST = Bern, L = Bern, O = Berner Fachhochschule, CN = Benjamin Fehrensen
		Subject Public Key Info:
			Public Key Algorithm: rsaEncryption
			Public-Key: (4096 bit)
			Modulus:
				00:a4:c1:8e:ec:4c:81:12:8f:ca:9a:57:b0:73:6e:
				...
			Exponent: 65537 (0x10001)
	Signature Algorithm: sha256WithRSAEncryption
	Signature Value:
69:54:b9:34:b2:1f:b0:d3:e8:5c:88:f2:5b:8b:2f:ea:7e:d5:
...
```

### Distinguished Name (DN)

The Subject and Issuer fields contain DN. A DN consists of Relative Distinguished Names (RDN) see table below. Special characters such as äöé might lead to interoperability issues.

| Acronym | RDN | Example |
| ---- | ---- | ---- |
| C | Country | C=CH |
| ST | State or Province | ST=Bern |
| L | Location | L=Bern |
| O | Organization | O=Berner Fachhochschule |
| OU | Organizational Unit | OU=TI |
| CN | CommonName Unit | CN=www.bfh.ch |
| G | GivenName | G=Alice |
| SN | SerialNumber | SN=987654321 |
| Email | Email (deprecated) | Email=alice@bfh.ch |
| ... | Arbitrary RDN | jurisdictionC = CH |

### Extensions

There are many optional extensions, each with its own unique id, expressed as object identifier (OID). http://www.oid-info.com

Extensions can be **critical** or **non-critical**. Critical extensions can't be ignored, if it cannot be recognized or processed the certificate has to be rejected. Non-critical may be ignored.

**Examples**

```
X509v3 extensions:
	X509v3 Authority Key Identifier:
		95:01:E3:59:D7:55:73:E4:C2:36:0D:A8:3B:92:4B:D9:E6:1E:10:7E
	Authority Information Access:
		CA Issuers - URI:http://trust.quovadisglobal.com/quovadisswissadvancedcag4.crt
		OCSP - URI:http://ocsp.quovadisglobal.com
	X509v3 Subject Alternative Name:
		email:benjamin.fehrensen@bfh.ch
	X509v3 Certificate Policies:
		Policy: 1.3.6.1.4.1.8024.1.200
		CPS: http://www.quovadisglobal.com/repository
	X509v3 Extended Key Usage:
		TLS Web Client Authentication, E-mail Protection
	X509v3 CRL Distribution Points:
		Full Name:
			URI:http://crl.quovadisglobal.com/quovadisswissadvancedcag4.crl
	X509v3 Subject Key Identifier:
		03:FC:B3:79:65:06:A7:4D:B1:C8:70:3F:F5:ED:9F:A1:39:5C:8B:25
	X509v3 Key Usage: critical
		Digital Signature, Key Encipherment
	...
```

#### subjectAltName

| SubjectAltName type | Notation |
| ---- | ---- |
| ipAddress | IP: 11.22.33.44 |
| dNSName | DNS:gateway.example.com |
| rfc822Name | email:alice@example.com |
| uniformResourceIdentifier | URI:https://www.example.com |
| directoryName | dirName: CN=Alice |
| ... |  |

X509v3 certificate extensions may contain multiple subjectAltName entries:

```
subjectAltName=DNS:gateway.example.com,IP:11.22.33.44
subjectAltName=email:alice.example.com,email:alice2@example.com
```

### Certificate Encoding

- Binary DER format(.der, .cer)
- Base64 encoded PEM format (.pem, .cer, .crt)
- PKCS#12 Container either DER or PEM encoded (.p12, .pfx)
	- Certificate belongs to a private key
	- Private key is encrypted using a symmetric key derived from a passphrase
	- Optional: Might contain the full key chain

With the openssl command line tool you are able to convert between the encodings:

```bash
#Convert PEM to DER
openssl x509 -inform PEM -outform DER -in cert.pem -out cert.der

#Dump ASN1 structure
openssl asn1pare -inform der -in qvrca1g3.der
```

## Chain of Trust Overview

![[chain-of-trust-overview.png]]

## PKCS standards

[[PKCS]]

## Revoke Certificates

There are multiple mechanisms to revoke certificates;

- Certificate Revocation List ([[Trust Issues in X.509#Certificate revocation lists (CRL)|CRL]])
- Online Certificate Status Protocol ([[Trust Issues in X.509#Online Certificate Status Protocol (OCSP)|OCSP]])
- (CRL) Distribution Points (DP's)
- Authority revocation list (ARL)

## Certificate Types

- SSL certificates
	- Domain Validation DV (single domain)
	- Organization Validation OV (single domain)
	- Wildcard (multi-domain, DV, OV)
	- Extended validation (EV)
- Email certificates
- Authentication certificates
- Signing / timestamping certificates

## Certificate Transparency (CT)

- Internet security standard for monitoring and auditing the issuance digital TLS server certificate
- CT originated after the 2011 attack on DigiNoter (CA)
- Before a CA can log a Certificate it needs an Signed Certificate Timestamp (SCT). To get an SCT the certificate has to be submitted to a log.
- Each entry of this log references the hash of the previous one forming a Merkle tree
	- Append-only. Certificates can only be added to a log
	- Merkle trees to prevent tempering and misbehaviour
	- Publicly auditable
- Most browser enforce CT. At least 2 SCTs are required

![[certificate-transparency-overview.png]]

### Deliver SCTs to the Browser

CT offers 3 ways to deliver SCTs to a browser:

- In the TLS extension
- In stapled OCSP
- In the X509v3 certificate CT extensions

## Precertificate

PreCertificates are issued by CAs with a "poisoned critical exteions" OID (1.3.6.1.4.1.11129.2.4.3). It will be submitted to the CT Log afterward. If a browser catches a poisoned certificate it would rise an alert. Because there is an extension marked as critical but is unknown.

---
links: [[611 SPA TOC - Certificates and PKI|SPA TOC - Certificates and PKI]] - [[themes/000 Index|Index]]