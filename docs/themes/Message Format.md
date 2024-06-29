tags: #secure-mail

# Message Format

links: [[613 SPA TOC - Secure Email|SPA TOC - Secure Email]] - [[themes/000 Index|Index]]

---

## Internet Message Format

- Internet Message Format: **RFC 5322** & **RFC822**
- consists of a **header** and a **body** section (yellow parts of the following image)

![[internet-message-format.png]]

### Header fields

- all header fields have the structure `field: field-body`  (e.g. `To: Jan`)
- **Required header fields**: origination date field and the originator from (address) fields

![[field-definitions.png]]

### Receiver Header

- the "trace fields" are a group of header fields consisting of an optional `Return-Path:` field, and one or more `Received:` fields
- when forwarding a message, a gateway *must* prepend a `Received:` line, but it *must not* alter an already existing `Received:` line

![[receiver-header.png]]

### Content-Transfer-Encoding

- Header field names and, without `SMTPUTF8`, field bodies are restricted to **7-bit ASCII characters**
- the following transfer encoding schemes are common
	- "Q"-Encoding (Quoted-Printable)
	- "B"-Encoding (Base64)
- the content type and encoding must be specified in [[MIME]] Header:

```bash
Content-Type: image/gif
Content-Transfer-Encoding: base64
```

### Quoted-Printable

- each 8-Bit value will be replaced with 3 ASCII characters
	- "ö" (ASCII 246, hex F6) will be replaced with `=F6`
	- "=" (ASCII 61, hex 3D) will be replaced with `=3D`
	- "Jörg Järmann" will lead to `J=F6rg J=E4rman`

### Base64 Encoding

- Binary representation of an ASCII symbol is used (8 bits) and **encoded in 6-bit**
- so every 4 characters of Base64-encoded text represent 3 octets. This means that when the length of the unencoded input is not a multiple of three, the encoded output must have padding added. The padding character is `=`

![[base64-padding.png]]

## Problems with RFC 5321 & 5322

Internet Message Format: **RFC 5322** & SMTP: **RFC 5321**

- binary files must be converted into ASCII
- text data with special characters (e.g. German text) need encoding
- some MTA-Servers do strange things:
	- reject messages over a certain size
	- delete, add, or reorder CR and LF characters
	- truncate or wrap lines longer than 76 characters
	- remove trailing white space (tabs and spaces)
	- pad lines in a message to the same length
	- convert tab characters into multiple spaces

## MIME

See documentation [[MIME|MIME AC2]]

- MIME (Multipurpose Internet Mail Extensions) is an extension to the Internet Message Format to **support text in character sets other than ASCII** as well as **attachments** of audio, video, images and application programs
- MIME Header field consists of
	- MIME-Version: e.g. `MIME-Version: 1.0`
	- Content-Type: e.g. `Content-Type: text/plain`
	- Content-Disposition: e.g. `Content-Disposition: attachment; filename=image.jpg`
	- Content-Transfer-Encoding: e.g. `Content-Transfer-Encoding: base64`
	- Optional fields such as Content-ID, Content-Description

### Single Part Message

![[mime-single-part-message.png]]

### Multi Part Message

![[mime-multi-part-message.png]]

## S/MIME

See documentation [[MIME#S/MIME|S/MIME AC2]]

- based on [[PKCS|PKCS#7]] 
- specifies the MIME type `application/pkcs7-mime`
- S/MIME provides:
	- Authentication
	- Message integrity
	- Non-repudiation or origin (using digital signatures)
	- Privacy and Data security (using encryption)
- S/MIME not always suited for web-mail clients
- need certificates

### BLOB and Signatures

- Encrypted and signed S/MIME messages comes as BLOB of content type `application/pkcs7-mime`

**Detached signatures**

- S/MIME signatures are usually sent as "detached signatures" of content type `multipart/signed` with the second part having a MIME subtype of `application/pkcs7-signature`
- **Detached signatures are separate from the data**, preserving the original format of the data
- **Important**: Mailing list software is notorious for changing textual parts of a message and thereby invalidating the signature

![[s-mime-detached-signature.png]]

**Regular PKCS#7 signature**

- Content-Type is `application/pkcs7-mime` instead of `application/pkcs7-signature`
- the MIME content is carried within the PKCS#7 structure (the signature is bundled together with the data being signed, the data and the signature are encapsulated in a single file)
- **Pro**: MIME content is not prone to changes in the transfer between multiple MTAs
- **Contra**: Recipients with mail clients which do not support S/MIME cannot read the content

### Signature Structure

**SignedData**

![[structure-signing.png]]

**envelopedData & multiple Recipients**

- there is a separate `recipientinfo` for each recipient which also holds the symmetric key encrypted with the recipients public key

![[structure-envelope-data.png]]
### Encrypted Message With Multiple Recipients

- generate a single symmetric key to encrypt the data
- encrypt the symmetric key with each recipient's public key



![[encrypted-message-multiple-recipients.png]]

---
links: [[613 SPA TOC - Secure Email|SPA TOC - Secure Email]] - [[themes/000 Index|Index]]