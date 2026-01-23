![[Pasted image 20240717175334.png]]
1. #A record type
2. #AAAA record type
3. #CAA record type
4. #CNAME record type
5. #DS record type
6. #MX record type
7. #NAPTR record type
8. #NS record type
9. #PTR record type
10. #SOA record type
11. #SPF record type
12. #SRV record type
13. #TXT record type

---
#A  record:

WE use an A record to route traffic to a resource, such as a web server, using an IPv4 address in dotted decimal notation.
**Example for the Amazon Route 53 console**
`192.0.2.1`
---


#AAAA record
WE use an AAAA record to route traffic to a resource, such as a web server, using an IPv6 address in colon-separated hexadecimal format.
**Example for the Amazon Route 53 console**
`2001:0db8:85a3:0:0:8a2e:0370:7334`.
---


#CAA record
- A CAA record specifies which certificate authorities (CAs) are allowed to issue certificates for a domain or subdomain. 
- Creating a CAA record helps to prevent the wrong CAs from issuing certificates for your domains. 
- A CAA record isn't a substitute for the security requirements that are specified by your certificate authority, such as the requirement to validate that you're the owner of a domain.
**You can use CAA records to specify the following:
- Which certificate authorities (CAs) can issue SSL/TLS certificates, if any
- The email address or URL to contact when a CA issues a certificate for the domain or subdomain.

	*Authorize a CA to issue a certificate for a domain or subdomain
		- To authorize a CA to issue a certificate for a domain or subdomain, create a record that has the same name as the domain or subdomain, and specify the following settings
		- flags – `0`,  tag – `issue`, value – the code for the CA that you authorize to issue a certificate for the domain or subdomain.
		- WE create a CAA record for example.com with the following settings:
		- `0 issue "ca.example.net"`

	*Authorize a CA to issue a wildcard certificate for a domain or subdomain*
		- To authorize a CA to issue a wildcard certificate for a domain or subdomain, create a record that has the same name as the domain or subdomain, and specify the following settings
		- A wildcard certificate applies to the domain or subdomain and all of its subdomains.
		- flags – `0`,  tag – `issuewild`, value – the code for the CA that you authorize to issue a certificate for a domain or subdomain, and its subdomain
		- We create a CAA record for example.com with the following settings:
		- `0 issuewild "ca.example.net"`

	*Prevent any CA from issuing a certificate for a domain or subdomain*
		- To prevent any CA from issuing a certificate for a domain or subdomain, create a record that has the same name as the domain or subdomain, and specify the following settings:
		- flags – `0`,  tag – `issue`,  value – `";"`
		- We don't want any CA to issue a certificate for example.com. We create a CAA record for example.com with the following settings  `0 issue ";"`
		- If We don't want any CA to issue a certificate for example.com or its subdomains, have to create a CAA record for example.com with the following settings `0 issuewild ";"`

	*Request that any CA contacts you if the CA receives an invalid certificate request*
		- If you want any CA that receives an invalid request for a certificate to contact you, specify the following settings:
		- flags – `0`, tag– `iodef`,  value  – the URL or email address that you want the CA to notify if the CA receives an invalid request for a certificate. Use the applicable format:
	    - ``"mailto:`email-address`"``,    ``"http://`URL`"``,    ``"https://`URL`"``
	    - We create a CAA record with the following settings `0 iodef "mailto:admin@example.com"`

	*Use another setting that is supported by the CA*
		If your CA supports a feature that isn't defined in the RFC for CAA records, specify the following settings:
		flags – 128 (This value prevents the CA from issuing a certificate if the CA doesn't support the specified feature.), tag – the tag that you authorize the CA to use, value – the value that corresponds with the value of tag.   
		CA supports sending a text message if the CA receives an invalid certificate request. `128 exampletag "15555551212"`

	Examples:
		- Example for the Route 53 console
		- `0 issue "ca.example.net" 0 iodef "mailto:admin@example.com"`.
---


#CNAME record
- A CNAME record maps DNS queries for the name of the current record, such as acme.example.com, to another domain "example.com or example.net", subdomain "acme.example.com or zenith.example.org"
- Amazon Route 53 also supports alias records, which allow you to route queries to selected AWS resources, such as CloudFront distributions and Amazon S3 buckets. 
- Aliases are similar in some ways to the CNAME record type; however, you can create an alias for the zone apex.
- Example for the Route 53 console: `hostname.example.com`
---


#DS record
- (DS) record refers a zone key for a delegated subdomain zone.
- The first three values are decimal numbers representing the key tag, algorithm, and digest type.
- **Example for the Route 53 console**
- `123 4 5 1234567890abcdef1234567890absdef`
---


#MX record
- MX record specifies the names of your mail servers and, if you have two or more mail servers, the priority order. Each value for an MX record contains two values, priority and domain name.
	-**Priority**
	- An integer that represents the priority for an email server. If you specify only one server, the priority can be any integer between 0 and 65535. 
	- If you specify multiple servers, the value that you specify for the priority indicates which email server you want email to be routed to first, second, and so on. 
	- The server with the lowest value for the priority takes precedence. 
	- For example, if you have two email servers and you specify values of 10 and 20 for the priority, email always goes to the server with a priority of 10 unless it's unavailable. 
	- If you specify values of 10 and 10, email is routed to the two servers approximately equally.
	-**Domain name**
	- The domain name of the email server. Specify the name (such as mail.example.com) of an A or AAAA record. 
	-**Example for the Amazon Route 53 console**
	- `10 mail.example.com`

#NAPTR record(***Name Authority Pointer***)
	it is a type of DNS record that maps domain names to URIs (Uniform Resource Identifiers) and other resources.
- A Name Authority Pointer (NAPTR) is a type of record that is used by Dynamic Delegation Discovery System (DDDS) applications to convert one value to another or to replace one value with another. 
- For example, one common use is to convert phone numbers into SIP URIs.
- The `Value` element for an NAPTR record consists of six space-separated values:
**Order**
- When you specify more than one record, the sequence that you want the DDDS application to evaluate records in. Valid values: 0-65535.
**Preference**
- When you specify two or more records that have the same **Order**, your preference for the sequence that those records are evaluated in. 
- For example, if two records have an **Order** of 1, the DDDS application first evaluates the record that has the lower **Preference**. Valid values: 0-65535.
**Flags**
- A setting that is specific to DDDS applications. Values currently defined in [RFC 3404](https://www.ietf.org/rfc/rfc3404.txt) are uppercase- and lowercase letters **"A"**, **"P"**, **"S"**, and **"U"**, and the empty string, **""**. Enclose **Flags** in quotation marks.
**Service**
- A setting that is specific to DDDS applications. Enclose **Service** in quotation marks.

*For more information, see the applicable RFCs:
- URI DDDS application
- S-NAPTR DDDS application
- U-NAPTR DDDS application

**Regexp**
- A regular expression that the DDDS application uses to convert an input value into an output value. 
	- For example, an IP phone system might use a regular expression to convert a phone number that is entered by a user into a SIP URI.
- Enclose Regexp in quotation marks. Specify either a value for Regexp or a value for Replacement, but not both.
- The regular expression can include any of the following printable ASCII characters:
	- a-z
	- 0-9
	- - (hyphen)
	- (space)
	- ! # $ % & ' ( ) * + , - / : ; < = > ? @ [ ] ^ _ ` { | } ~ .
	- " (quotation mark). To include a literal quote in a string, precede it with a \ character: \".
	- \ (backslash). To include a backslash in a string, precede it with a \ character: \\.
	- Specify all other values, such as internationalized domain names, in octal format.
- **Replacement**
	- The fully qualified domain name (FQDN) of the next domain name that you want the DDDS application to submit a DNS query for. 
	- The DDDS application replaces the input value with the value that you specify for Replacement, if any. 
	- Specify either a value for Regexp or a value for Replacement, but not both. 
	- If you specify a value for Regexp, specify a dot (.) for Replacement.
	- The domain name can include a-z, 0-9, and - (hyphen).
- **Example for the Amazon Route 53 console**
- `100 50 "u" "E2U+sip" "!^(\\+441632960083)$!sip:\\1@example.com!" . 
- `100 51 "u" "E2U+h323" "!^\\+441632960083$!h323:operator@example.com!" . 
- `100 52 "u" "E2U+email:mailto" "!^.*$!mailto:info@example.com!" .`
---


#NS record
	which DNS server is authoritative for that domain (i.e. which server contains the actual DNS records). Basically, NS records **tell the Internet where to go to find out a domain's IP address**.
- NS record identifies the name servers for the hosted zone. 
	- The most common use for an NS record is to control how internet traffic is routed for a domain.
	- To use the records in a hosted zone to route traffic for a domain, you update the domain registration settings to use the four name servers in the default NS record. 
	-  can create a separate hosted zone for a subdomain use that hosted zone to route internet traffic for the subdomain and its subdomains can set up this configuration, known as "delegating responsibility for a subdomain to a hosted zone" by creating another NS record in the hosted zone for the root domain (example.com). 
	- also use NS records to configure white-label name servers.
- **Example for the Amazon Route 53 console**
	- `ns-1.example.com`
---

#PTR record
	- A PTR record maps an IP address to the corresponding domain name.

- **Example for the Amazon Route 53 console**

	- `hostname.example.com`
---

#SOA record
- A start of authority (SOA) record provides information about a domain and the corresponding Amazon Route 53 hosted zone. For information about the fields in an SOA record
**Example for the Route 53 console**
- `ns-2048.awsdns-64.net hostmaster.awsdns.com 1 1 1 1 60`
---
#SRV record
- An SRV record `Value` element consists of four space-separated values. The first three values are decimal numbers representing priority, weight, and port. 
- The fourth value is a domain name. 
- SRV records are used for accessing services, such as a service for email or communications. For information about SRV record format, refer to the documentation for the service that you want to connect to.
**Example for the Amazon Route 53 console**
- `10 5 80 hostname.example.com`
---
#TXT record
- A TXT record contains one or more strings that are enclosed in double quotation marks (`"`). 
***Topics***
- Entering TXT record values
- Special characters in a TXT record value
- Uppercase and lowercase in a TXT record value
- Examples
***Entering TXT record values***
- A single string can include up to 255 characters, including the following:
- a-z
- A-Z
- 0-9
- Space
- - (hyphen)
- ! " # $ % & ' ( ) * + , - / : ; < = > ? @ [ \ ] ^ _ ` { | } ~ .

- If you need to enter a value longer than 255 characters, break the value into strings of 255 characters or fewer, and enclose each string in double quotation marks (`"`). In the console, list all the strings on the same line:
- `"String 1" "String 2" "String 3"`
- For the API, include all the strings in the same `Value` element:
- `<Value>"String 1" "String 2" "String 3"</Value>`
- The maximum length of a value in a TXT record is 4,000 characters.
- To enter more than one TXT value, enter one value per row.
***Special characters in a TXT record value
- If your TXT record contains any of the following characters, you must specify the characters by using escape codes in the format `\``three-digit octal code`:
- Characters 000 to 040 octal (0 to 32 decimal, 0x00 to 0x20 hexadecimal)
- Characters 177 to 377 octal (127 to 255 decimal, 0x7F to 0xFF hexadecimal)
- To include a quotation mark (`"`) in a string, put a backslash (`\`) character before the quotation mark: `\"`.
***Uppercase and lowercase in a TXT record value
- Case is preserved, so `"Ab"` and `"aB"` are different values.
- ### Examples
**Example for the Amazon Route 53 console**
- Put each value on a separate line:
- `"This string includes \"quotation marks\"." "The last character in this string is an accented e specified in octal format: \351" "v=spf1 ip4:192.168.0.1/16 -all"`

---

