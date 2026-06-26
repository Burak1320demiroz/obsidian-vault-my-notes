---
title: PortSwigger Web Security Academy - All Labs
date: 2026-06-25
tags:
  - cyber-security
  - portswigger
  - web-security
  - burp-suite
  - pentesting
aliases:
  - PortSwigger Labs
  - Web Security Academy
---

# 🎯 PortSwigger Web Security Academy — All Labs

> [!abstract] Genel Bakış
> [PortSwigger Web Security Academy](https://portswigger.net/web-security/all-materials), web güvenliği konusunda ==ücretsiz== ve kapsamlı bir eğitim platformudur. Gerçekçi lab ortamlarında 30 farklı zafiyet kategorisinde pratik yapma imkanı sunar. Bu not, tüm kategorileri ve lab'ları takip etmek için hazırlanmıştır.

**Zorluk Seviyeleri:** 🟢 Apprentice · 🟡 Practitioner · 🔴 Expert

---

## 1. SQL Injection

> [!info]- Nedir?
> Kullanıcı girdisinin SQL sorgusuna enjekte edilerek veritabanı manipülasyonu yapılmasıdır.

- [ ] 🟢 SQL injection vulnerability in WHERE clause allowing retrieval of hidden data
- [ ] 🟢 SQL injection vulnerability allowing login bypass
- [ ] 🟡 SQL injection attack, querying the database type and version on Oracle
- [ ] 🟡 SQL injection attack, querying the database type and version on MySQL and Microsoft
- [ ] 🟡 SQL injection attack, listing the database contents on non-Oracle databases
- [ ] 🟡 SQL injection attack, listing the database contents on Oracle
- [ ] 🟡 SQL injection UNION attack, determining the number of columns returned by the query
- [ ] 🟡 SQL injection UNION attack, finding a column containing text
- [ ] 🟡 SQL injection UNION attack, retrieving data from other tables
- [ ] 🟡 SQL injection UNION attack, retrieving multiple values in a single column
- [ ] 🟡 Blind SQL injection with conditional responses
- [ ] 🟡 Blind SQL injection with conditional errors
- [ ] 🟡 Visible error-based SQL injection
- [ ] 🟡 Blind SQL injection with time delays
- [ ] 🟡 Blind SQL injection with time delays and information retrieval
- [ ] 🟡 Blind SQL injection with out-of-band interaction
- [ ] 🟡 Blind SQL injection with out-of-band data exfiltration
- [ ] 🟡 SQL injection with filter bypass via XML encoding

---

## 2. Cross-Site Scripting (XSS)

> [!info]- Nedir?
> Kötü amaçlı JavaScript kodunun kurbanın tarayıcısında çalıştırılmasıdır. Reflected, Stored ve DOM-based olmak üzere üç türü vardır.

- [ ] 🟢 Reflected XSS into HTML context with nothing encoded
- [ ] 🟢 Stored XSS into HTML context with nothing encoded
- [ ] 🟢 DOM XSS in document.write sink using source location.search
- [ ] 🟢 DOM XSS in innerHTML sink using source location.search
- [ ] 🟢 DOM XSS in jQuery anchor href attribute sink using location.search source
- [ ] 🟢 DOM XSS in jQuery selector sink using a hashchange event
- [ ] 🟢 Reflected XSS into attribute with angle brackets HTML-encoded
- [ ] 🟢 Stored XSS into anchor href attribute with double quotes HTML-encoded
- [ ] 🟢 Reflected XSS into a JavaScript string with angle brackets HTML encoded
- [ ] 🟡 DOM XSS in document.write sink using source location.search inside a select element
- [ ] 🟡 DOM XSS in AngularJS expression with angle brackets and double quotes HTML-encoded
- [ ] 🟡 Reflected DOM XSS
- [ ] 🟡 Stored DOM XSS
- [ ] 🟡 Reflected XSS into HTML context with most tags and attributes blocked
- [ ] 🟡 Reflected XSS into HTML context with all tags blocked except custom ones
- [ ] 🟡 Reflected XSS with some SVG markup allowed
- [ ] 🟡 Reflected XSS in canonical link tag
- [ ] 🟡 Reflected XSS into a JavaScript string with single quote and backslash escaped
- [ ] 🟡 Reflected XSS into a JavaScript string with angle brackets and double quotes HTML-encoded and single quotes escaped
- [ ] 🟡 Stored XSS into onclick event with angle brackets and double quotes HTML-encoded and single quotes and backslash escaped
- [ ] 🟡 Reflected XSS into a template literal with angle brackets, single, double quotes, backslash and backticks Unicode-escaped
- [ ] 🟡 Exploiting cross-site scripting to steal cookies
- [ ] 🟡 Exploiting cross-site scripting to capture passwords
- [ ] 🟡 Exploiting XSS to bypass CSRF defenses
- [ ] 🔴 Reflected XSS with AngularJS sandbox escape without strings
- [ ] 🔴 Reflected XSS with AngularJS sandbox escape and CSP
- [ ] 🔴 Reflected XSS with event handlers and href attributes blocked
- [ ] 🔴 Reflected XSS in a JavaScript URL with some characters blocked
- [ ] 🟡 Reflected XSS protected by very strict CSP, with dangling markup attack
- [ ] 🔴 Reflected XSS protected by CSP, with CSP bypass

---

## 3. Cross-Site Request Forgery (CSRF)

> [!info]- Nedir?
> Oturum açmış kullanıcının, farkında olmadan saldırganın istediği eylemi gerçekleştirmesini sağlayan saldırıdır.

- [ ] 🟢 CSRF vulnerability with no defenses
- [ ] 🟡 CSRF where token validation depends on request method
- [ ] 🟡 CSRF where token validation depends on token being present
- [ ] 🟡 CSRF where token is not tied to user session
- [ ] 🟡 CSRF where token is tied to non-session cookie
- [ ] 🟡 CSRF where token is duplicated in cookie
- [ ] 🟡 SameSite Lax bypass via method override
- [ ] 🟡 SameSite Strict bypass via client-side redirect
- [ ] 🟡 SameSite Strict bypass via sibling domain
- [ ] 🟡 SameSite Lax bypass via cookie refresh
- [ ] 🟡 CSRF where Referer validation depends on header being present
- [ ] 🟡 CSRF with broken Referer validation

---

## 4. Clickjacking

> [!info]- Nedir?
> Görünmez bir iframe ile kullanıcıyı farkında olmadan bir butona/linke tıklatma saldırısıdır.

- [ ] 🟢 Basic clickjacking with CSRF token protection
- [ ] 🟢 Clickjacking with form input data prefilled from a URL parameter
- [ ] 🟢 Clickjacking with a frame buster script
- [ ] 🟡 Exploiting clickjacking vulnerability to trigger DOM-based XSS
- [ ] 🟡 Multistep clickjacking

---

## 5. DOM-Based Vulnerabilities

> [!info]- Nedir?
> JavaScript'in DOM'u güvensiz şekilde manipüle etmesiyle oluşan istemci taraflı zafiyetlerdir.

- [ ] 🟡 DOM XSS using web messages
- [ ] 🟡 DOM XSS using web messages and a JavaScript URL
- [ ] 🟡 DOM XSS using web messages and JSON.parse
- [ ] 🟡 DOM-based open redirection
- [ ] 🟡 DOM-based cookie manipulation
- [ ] 🔴 Exploiting DOM clobbering to enable XSS
- [ ] 🔴 Clobbering DOM attributes to bypass HTML filters

---

## 6. Cross-Origin Resource Sharing (CORS)

> [!info]- Nedir?
> CORS politikasının yanlış yapılandırılmasıyla farklı origin'lerden hassas verilere erişim sağlanmasıdır.

- [ ] 🟢 CORS vulnerability with basic origin reflection
- [ ] 🟢 CORS vulnerability with trusted null origin
- [ ] 🟡 CORS vulnerability with trusted insecure protocols

---

## 7. XML External Entity (XXE) Injection

> [!info]- Nedir?
> XML parser'ın harici entity tanımlarını işlemesiyle sunucu tarafında dosya okuma veya SSRF yapılmasıdır.

- [ ] 🟢 Exploiting XXE using external entities to retrieve files
- [ ] 🟢 Exploiting XXE to perform SSRF attacks
- [ ] 🟡 Blind XXE with out-of-band interaction
- [ ] 🟡 Blind XXE with out-of-band interaction via XML parameter entities
- [ ] 🟡 Exploiting blind XXE to exfiltrate data using a malicious external DTD
- [ ] 🟡 Exploiting blind XXE to retrieve data via error messages
- [ ] 🟡 Exploiting XInclude to retrieve files
- [ ] 🟡 Exploiting XXE via image file upload
- [ ] 🔴 Exploiting XXE to retrieve data by repurposing a local DTD

---

## 8. Server-Side Request Forgery (SSRF)

> [!info]- Nedir?
> Sunucunun, saldırganın belirlediği iç/dış kaynaklara HTTP istekleri yapmasını sağlayan zafiyettir.

- [ ] 🟢 Basic SSRF against the local server
- [ ] 🟢 Basic SSRF against another back-end system
- [ ] 🟡 Blind SSRF with out-of-band detection
- [ ] 🟡 SSRF with blacklist-based input filter
- [ ] 🟡 SSRF with filter bypass via open redirection vulnerability
- [ ] 🔴 Blind SSRF with Shellshock exploitation
- [ ] 🔴 SSRF with whitelist-based input filter

---

## 9. HTTP Request Smuggling

> [!info]- Nedir?
> Front-end ve back-end sunucuların HTTP isteğinin sınırlarını farklı yorumlamasından kaynaklanan zafiyettir.

- [ ] 🟡 HTTP request smuggling, basic CL.TE vulnerability
- [ ] 🟡 HTTP request smuggling, basic TE.CL vulnerability
- [ ] 🟡 HTTP request smuggling, obfuscating the TE header
- [ ] 🟡 HTTP request smuggling, confirming a CL.TE vulnerability via differential responses
- [ ] 🟡 HTTP request smuggling, confirming a TE.CL vulnerability via differential responses
- [ ] 🟡 Exploiting HTTP request smuggling to bypass front-end security controls, CL.TE vulnerability
- [ ] 🟡 Exploiting HTTP request smuggling to bypass front-end security controls, TE.CL vulnerability
- [ ] 🟡 Exploiting HTTP request smuggling to reveal front-end request rewriting
- [ ] 🟡 Exploiting HTTP request smuggling to capture other users' requests
- [ ] 🟡 Exploiting HTTP request smuggling to deliver reflected XSS
- [ ] 🟡 Response queue poisoning via H2.TE request smuggling
- [ ] 🟡 H2.CL request smuggling
- [ ] 🟡 HTTP/2 request smuggling via CRLF injection
- [ ] 🟡 HTTP/2 request splitting via CRLF injection
- [ ] 🟡 CL.0 request smuggling
- [ ] 🔴 0.CL request smuggling
- [ ] 🔴 Exploiting HTTP request smuggling to perform web cache poisoning
- [ ] 🔴 Exploiting HTTP request smuggling to perform web cache deception
- [ ] 🔴 Bypassing access controls via HTTP/2 request tunnelling
- [ ] 🔴 Web cache poisoning via HTTP/2 request tunnelling
- [ ] 🔴 Client-side desync
- [ ] 🔴 Server-side pause-based request smuggling

---

## 10. OS Command Injection

> [!info]- Nedir?
> Kullanıcı girdisinin işletim sistemi komutlarına enjekte edilerek sunucuda rastgele komut çalıştırılmasıdır. Bkz: [[CWE-78]]

- [ ] 🟢 OS command injection, simple case
- [ ] 🟡 Blind OS command injection with time delays
- [ ] 🟡 Blind OS command injection with output redirection
- [ ] 🟡 Blind OS command injection with out-of-band interaction
- [ ] 🟡 Blind OS command injection with out-of-band data exfiltration

---

## 11. Server-Side Template Injection (SSTI)

> [!info]- Nedir?
> Kullanıcı girdisinin sunucu tarafındaki template motoruna enjekte edilerek RCE elde edilmesidir.

- [ ] 🟡 Basic server-side template injection
- [ ] 🟡 Basic server-side template injection (code context)
- [ ] 🟡 Server-side template injection using documentation
- [ ] 🟡 Server-side template injection in an unknown language with a documented exploit
- [ ] 🟡 Server-side template injection with information disclosure via user-supplied objects
- [ ] 🔴 Server-side template injection in a sandboxed environment
- [ ] 🔴 Server-side template injection with a custom exploit

---

## 12. Path Traversal

> [!info]- Nedir?
> Dosya yolundaki `../` gibi dizileri kullanarak sunucudaki kısıtlı dosyalara erişim sağlanmasıdır.

- [ ] 🟢 File path traversal, simple case
- [ ] 🟡 File path traversal, traversal sequences blocked with absolute path bypass
- [ ] 🟡 File path traversal, traversal sequences stripped non-recursively
- [ ] 🟡 File path traversal, traversal sequences stripped with superfluous URL-decode
- [ ] 🟡 File path traversal, validation of start of path
- [ ] 🟡 File path traversal, validation of file extension with null byte bypass

---

## 13. Access Control Vulnerabilities

> [!info]- Nedir?
> Yetkilendirme kontrollerinin eksik veya hatalı uygulanmasıyla kullanıcıların yetkisiz kaynaklara erişmesidir.

- [ ] 🟢 Unprotected admin functionality
- [ ] 🟢 Unprotected admin functionality with unpredictable URL
- [ ] 🟢 User role controlled by request parameter
- [ ] 🟢 User role can be modified in user profile
- [ ] 🟢 User ID controlled by request parameter
- [ ] 🟢 User ID controlled by request parameter, with unpredictable user IDs
- [ ] 🟢 User ID controlled by request parameter with data leakage in redirect
- [ ] 🟢 User ID controlled by request parameter with password disclosure
- [ ] 🟢 Insecure direct object references
- [ ] 🟡 URL-based access control can be circumvented
- [ ] 🟡 Method-based access control can be circumvented
- [ ] 🟡 Multi-step process with no access control on one step
- [ ] 🟡 Referer-based access control

---

## 14. Authentication

> [!info]- Nedir?
> Kimlik doğrulama mekanizmalarındaki mantık hataları, brute-force koruması eksiklikleri ve 2FA bypass'larıdır.

- [ ] 🟢 Username enumeration via different responses
- [ ] 🟢 2FA simple bypass
- [ ] 🟢 Password reset broken logic
- [ ] 🟡 Username enumeration via subtly different responses
- [ ] 🟡 Username enumeration via response timing
- [ ] 🟡 Broken brute-force protection, IP block
- [ ] 🟡 Username enumeration via account lock
- [ ] 🟡 2FA broken logic
- [ ] 🟡 Brute-forcing a stay-logged-in cookie
- [ ] 🟡 Offline password cracking
- [ ] 🟡 Password reset poisoning via middleware
- [ ] 🟡 Password brute-force via password change
- [ ] 🔴 Broken brute-force protection, multiple credentials per request
- [ ] 🔴 2FA bypass using a brute-force attack

---

## 15. WebSockets

> [!info]- Nedir?
> WebSocket bağlantılarındaki mesaj manipülasyonu ve cross-site hijacking zafiyetleridir.

- [ ] 🟢 Manipulating WebSocket messages to exploit vulnerabilities
- [ ] 🟡 Cross-site WebSocket hijacking
- [ ] 🟡 Manipulating the WebSocket handshake to exploit vulnerabilities

---

## 16. Web Cache Poisoning

> [!info]- Nedir?
> Cache mekanizmasının unkeyed input'larla zehirlenerek diğer kullanıcılara zararlı içerik sunulmasıdır.

- [ ] 🟡 Web cache poisoning with an unkeyed header
- [ ] 🟡 Web cache poisoning with an unkeyed cookie
- [ ] 🟡 Web cache poisoning with multiple headers
- [ ] 🟡 Targeted web cache poisoning using an unknown header
- [ ] 🟡 Web cache poisoning via an unkeyed query string
- [ ] 🟡 Web cache poisoning via an unkeyed query parameter
- [ ] 🟡 Parameter cloaking
- [ ] 🟡 Web cache poisoning via a fat GET request
- [ ] 🟡 URL normalization
- [ ] 🔴 Web cache poisoning to exploit a DOM vulnerability via a cache with strict cacheability criteria
- [ ] 🔴 Combining web cache poisoning vulnerabilities
- [ ] 🔴 Cache key injection
- [ ] 🔴 Internal cache poisoning

---

## 17. Insecure Deserialization

> [!info]- Nedir?
> Güvenilmeyen verinin deserialize edilmesiyle nesne enjeksiyonu ve RCE elde edilmesidir.

- [ ] 🟢 Modifying serialized objects
- [ ] 🟡 Modifying serialized data types
- [ ] 🟡 Using application functionality to exploit insecure deserialization
- [ ] 🟡 Arbitrary object injection in PHP
- [ ] 🟡 Exploiting Java deserialization with Apache Commons
- [ ] 🟡 Exploiting PHP deserialization with a pre-built gadget chain
- [ ] 🟡 Exploiting Ruby deserialization using a documented gadget chain
- [ ] 🔴 Developing a custom gadget chain for Java deserialization
- [ ] 🔴 Developing a custom gadget chain for PHP deserialization
- [ ] 🔴 Using PHAR deserialization to deploy a custom gadget chain

---

## 18. Information Disclosure

> [!info]- Nedir?
> Uygulamanın hata mesajları, debug sayfaları veya yedek dosyalar aracılığıyla hassas bilgi sızdırmasıdır.

- [ ] 🟢 Information disclosure in error messages
- [ ] 🟢 Information disclosure on debug page
- [ ] 🟢 Source code disclosure via backup files
- [ ] 🟢 Authentication bypass via information disclosure
- [ ] 🟡 Information disclosure in version control history

---

## 19. Business Logic Vulnerabilities

> [!info]- Nedir?
> Uygulamanın iş mantığındaki tasarım hatalarının istismar edilmesiyle amaçlanmayan işlemlerin yapılmasıdır.

- [ ] 🟢 Excessive trust in client-side controls
- [ ] 🟢 High-level logic vulnerability
- [ ] 🟢 Inconsistent security controls
- [ ] 🟢 Flawed enforcement of business rules
- [ ] 🟡 Low-level logic flaw
- [ ] 🟡 Inconsistent handling of exceptional input
- [ ] 🟡 Weak isolation on dual-use endpoint
- [ ] 🟡 Insufficient workflow validation
- [ ] 🟡 Authentication bypass via flawed state machine
- [ ] 🟡 Infinite money logic flaw
- [ ] 🟡 Authentication bypass via encryption oracle
- [ ] 🔴 Bypassing access controls using email address parsing discrepancies

---

## 20. HTTP Host Header Attacks

> [!info]- Nedir?
> Host header'ının manipüle edilerek password reset poisoning, SSRF veya cache poisoning yapılmasıdır.

- [ ] 🟢 Basic password reset poisoning
- [ ] 🟢 Host header authentication bypass
- [ ] 🟡 Web cache poisoning via ambiguous requests
- [ ] 🟡 Routing-based SSRF
- [ ] 🟡 SSRF via flawed request parsing
- [ ] 🟡 Host validation bypass via connection state attack
- [ ] 🔴 Password reset poisoning via dangling markup

---

## 21. OAuth Authentication

> [!info]- Nedir?
> OAuth akışlarındaki yapılandırma hatalarının istismar edilerek hesap ele geçirme yapılmasıdır.

- [ ] 🟢 Authentication bypass via OAuth implicit flow
- [ ] 🟡 SSRF via OpenID dynamic client registration
- [ ] 🟡 Forced OAuth profile linking
- [ ] 🟡 OAuth account hijacking via redirect_uri
- [ ] 🟡 Stealing OAuth access tokens via an open redirect
- [ ] 🔴 Stealing OAuth access tokens via a proxy page

---

## 22. File Upload Vulnerabilities

> [!info]- Nedir?
> Dosya yükleme mekanizmalarının bypass edilerek sunucuya web shell yüklenmesidir.

- [ ] 🟢 Remote code execution via web shell upload
- [ ] 🟢 Web shell upload via Content-Type restriction bypass
- [ ] 🟡 Web shell upload via path traversal
- [ ] 🟡 Web shell upload via extension blacklist bypass
- [ ] 🟡 Web shell upload via obfuscated file extension
- [ ] 🟡 Remote code execution via polyglot web shell upload
- [ ] 🔴 Web shell upload via race condition

---

## 23. JWT

> [!info]- Nedir?
> JSON Web Token'ların imza doğrulama eksiklikleri, zayıf anahtar ve algoritma karmaşası ile bypass edilmesidir.

- [ ] 🟢 JWT authentication bypass via unverified signature
- [ ] 🟢 JWT authentication bypass via flawed signature verification
- [ ] 🟡 JWT authentication bypass via weak signing key
- [ ] 🟡 JWT authentication bypass via jwk header injection
- [ ] 🟡 JWT authentication bypass via jku header injection
- [ ] 🟡 JWT authentication bypass via kid header path traversal
- [ ] 🔴 JWT authentication bypass via algorithm confusion
- [ ] 🔴 JWT authentication bypass via algorithm confusion with no exposed key

---

## 24. Essential Skills

- [ ] 🟡 Discovering vulnerabilities quickly with targeted scanning
- [ ] 🟡 Scanning non-standard data structures

---

## 25. Prototype Pollution

> [!info]- Nedir?
> JavaScript'in prototype zincirinin manipüle edilerek istemci veya sunucu tarafında XSS/RCE elde edilmesidir.

- [ ] 🟡 Client-side prototype pollution via browser APIs
- [ ] 🟡 DOM XSS via client-side prototype pollution
- [ ] 🟡 DOM XSS via an alternative prototype pollution vector
- [ ] 🟡 Client-side prototype pollution via flawed sanitization
- [ ] 🟡 Client-side prototype pollution in third-party libraries
- [ ] 🟡 Privilege escalation via server-side prototype pollution
- [ ] 🟡 Detecting server-side prototype pollution without polluted property reflection
- [ ] 🟡 Bypassing flawed input filters for server-side prototype pollution
- [ ] 🟡 Remote code execution via server-side prototype pollution
- [ ] 🔴 Exfiltrating sensitive data via server-side prototype pollution

---

## 26. GraphQL API Vulnerabilities

> [!info]- Nedir?
> GraphQL endpoint'lerinin keşfi, introspection istismarı ve brute-force koruması bypass'ıdır.

- [ ] 🟢 Accessing private GraphQL posts
- [ ] 🟡 Accidental exposure of private GraphQL fields
- [ ] 🟡 Finding a hidden GraphQL endpoint
- [ ] 🟡 Bypassing GraphQL brute force protections
- [ ] 🟡 Performing CSRF exploits over GraphQL

---

## 27. Race Conditions

> [!info]- Nedir?
> Eşzamanlı isteklerle uygulamanın zamanlama varsayımlarını kırarak limit aşımı veya yetki yükseltme yapılmasıdır.

- [ ] 🟢 Limit overrun race conditions
- [ ] 🟡 Bypassing rate limits via race conditions
- [ ] 🟡 Multi-endpoint race conditions
- [ ] 🟡 Single-endpoint race conditions
- [ ] 🟡 Exploiting time-sensitive vulnerabilities
- [ ] 🔴 Partial construction race conditions

---

## 28. NoSQL Injection

> [!info]- Nedir?
> NoSQL veritabanı sorgularına operatör enjeksiyonu yapılarak kimlik doğrulama bypass'ı ve veri sızdırılmasıdır.

- [ ] 🟢 Detecting NoSQL injection
- [ ] 🟢 Exploiting NoSQL operator injection to bypass authentication
- [ ] 🟡 Exploiting NoSQL injection to extract data
- [ ] 🟡 Exploiting NoSQL operator injection to extract unknown fields

---

## 29. API Testing

> [!info]- Nedir?
> API endpoint'lerinin keşfi, dokümantasyon istismarı, mass assignment ve parametre kirliliği zafiyetleridir.

- [ ] 🟢 Exploiting an API endpoint using documentation
- [ ] 🟡 Exploiting server-side parameter pollution in a query string
- [ ] 🟡 Finding and exploiting an unused API endpoint
- [ ] 🟡 Exploiting a mass assignment vulnerability
- [ ] 🔴 Exploiting server-side parameter pollution in a REST URL

---

## 30. Web LLM Attacks

> [!info]- Nedir?
> LLM tabanlı AI agent'ların prompt injection, excessive agency ve güvensiz çıktı işleme ile istismar edilmesidir.

- [ ] 🟢 Exploiting LLM APIs with excessive agency
- [ ] 🟢 Exploiting AI agents to perform destructive actions
- [ ] 🟢 Exploiting AI agents to exfiltrate sensitive information
- [ ] 🟡 Exploiting vulnerabilities in LLM APIs
- [ ] 🟡 Indirect prompt injection
- [ ] 🟡 Exploiting AI agents to trigger secondary vulnerabilities
- [ ] 🟡 Bypassing AI scanner defenses to exfiltrate sensitive information
- [ ] 🔴 Exploiting insecure output handling in LLMs

---

## 31. Web Cache Deception

> [!info]- Nedir?
> Cache kurallarının istismar edilerek diğer kullanıcıların hassas yanıtlarının cache'lenmesi ve okunmasıdır.

- [ ] 🟢 Exploiting path mapping for web cache deception
- [ ] 🟡 Exploiting path delimiters for web cache deception
- [ ] 🟡 Exploiting origin server normalization for web cache deception
- [ ] 🟡 Exploiting cache server normalization for web cache deception
- [ ] 🔴 Exploiting exact-match cache rules for web cache deception

---

> [!quote] Kaynak
> [PortSwigger Web Security Academy](https://portswigger.net/web-security/all-materials)
