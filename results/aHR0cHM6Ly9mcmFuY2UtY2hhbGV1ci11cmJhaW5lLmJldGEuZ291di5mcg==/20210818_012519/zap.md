
# ZAP Scanning Report

Generated on Wed, 18 Aug 2021 01:14:13


## Summary of Alerts

| Risk Level | Number of Alerts |
| --- | --- |
| High | 0 |
| Medium | 4 |
| Low | 4 |
| Informational | 5 |

## Alerts

| Name | Risk Level | Number of Instances |
| --- | --- | --- | 
| Application Error Disclosure | Medium | 1 | 
| Content Security Policy (CSP) Header Not Set | Medium | 9 | 
| Reverse Tabnabbing | Medium | 7 | 
| X-Frame-Options Header Not Set | Medium | 7 | 
| Incomplete or No Cache-control Header Set | Low | 7 | 
| Permissions Policy Header Not Set | Low | 11 | 
| Server Leaks Information via "X-Powered-By" HTTP Response Header Field(s) | Low | 9 | 
| X-Content-Type-Options Header Missing | Low | 11 | 
| Base64 Disclosure | Informational | 11 | 
| Information Disclosure - Suspicious Comments | Informational | 11 | 
| Modern Web Application | Informational | 11 | 
| Storable and Cacheable Content | Informational | 11 | 
| Timestamp Disclosure - Unix | Informational | 11 | 

## Alert Detail


  
  
  
  
### Application Error Disclosure
##### Medium (Medium)
  
  
  
  
#### Description
<p>This page contains an error/warning message that may disclose sensitive information like the location of the file that produced the unhandled exception. This information can be used to launch further attacks against the web application. The alert could be a false positive if the error message is found inside a documentation page.</p>
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/_next/static/chunks/pages/_error-ef6fb2a85018fcbd5e37.js](https://france-chaleur-urbaine.beta.gouv.fr/_next/static/chunks/pages/_error-ef6fb2a85018fcbd5e37.js)
  
  
  * Method: `GET`
  
  
  * Evidence: `Internal Server Error`
  
  
  
  
Instances: 1
  
### Solution
<p>Review the source code of this page. Implement custom error pages. Consider implementing a mechanism to provide a unique error reference/identifier to the client (browser) while logging the details on the server side and not exposing them to the user.</p>
  
### Reference
* 

  
#### CWE Id : 200
  
#### WASC Id : 13
  
#### Source ID : 3

  
  
  
  
### Content Security Policy (CSP) Header Not Set
##### Medium (High)
  
  
  
  
#### Description
<p>Content Security Policy (CSP) is an added layer of security that helps to detect and mitigate certain types of attacks, including Cross Site Scripting (XSS) and data injection attacks. These attacks are used for everything from data theft to site defacement or distribution of malware. CSP provides a set of standard HTTP headers that allow website owners to declare approved sources of content that browsers should be allowed to load on that page — covered types are JavaScript, CSS, HTML frames, fonts, images and embeddable objects such as Java applets, ActiveX, audio and video files.</p>
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/sitemap.xml](https://france-chaleur-urbaine.beta.gouv.fr/sitemap.xml)
  
  
  * Method: `GET`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/accessibilite](https://france-chaleur-urbaine.beta.gouv.fr/accessibilite)
  
  
  * Method: `GET`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/politique-de-confidentialite](https://france-chaleur-urbaine.beta.gouv.fr/politique-de-confidentialite)
  
  
  * Method: `GET`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/](https://france-chaleur-urbaine.beta.gouv.fr/)
  
  
  * Method: `GET`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/ressources](https://france-chaleur-urbaine.beta.gouv.fr/ressources)
  
  
  * Method: `GET`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/partenaires](https://france-chaleur-urbaine.beta.gouv.fr/partenaires)
  
  
  * Method: `GET`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/robots.txt](https://france-chaleur-urbaine.beta.gouv.fr/robots.txt)
  
  
  * Method: `GET`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/mentions-legales](https://france-chaleur-urbaine.beta.gouv.fr/mentions-legales)
  
  
  * Method: `GET`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr](https://france-chaleur-urbaine.beta.gouv.fr)
  
  
  * Method: `GET`
  
  
  
  
Instances: 9
  
### Solution
<p>Ensure that your web server, application server, load balancer, etc. is configured to set the Content-Security-Policy header, to achieve optimal browser support: "Content-Security-Policy" for Chrome 25+, Firefox 23+ and Safari 7+, "X-Content-Security-Policy" for Firefox 4.0+ and Internet Explorer 10+, and "X-WebKit-CSP" for Chrome 14+ and Safari 6+.</p>
  
### Reference
* https://developer.mozilla.org/en-US/docs/Web/Security/CSP/Introducing_Content_Security_Policy
* https://cheatsheetseries.owasp.org/cheatsheets/Content_Security_Policy_Cheat_Sheet.html
* http://www.w3.org/TR/CSP/
* http://w3c.github.io/webappsec/specs/content-security-policy/csp-specification.dev.html
* http://www.html5rocks.com/en/tutorials/security/content-security-policy/
* http://caniuse.com/#feat=contentsecuritypolicy
* http://content-security-policy.com/

  
#### CWE Id : 693
  
#### WASC Id : 15
  
#### Source ID : 3

  
  
  
  
### Reverse Tabnabbing
##### Medium (Medium)
  
  
  
  
#### Description
<p>At least one link on this page is vulnerable to Reverse tabnabbing as it uses a target attribute without using both of the "noopener" and "noreferrer" keywords in the "rel" attribute, which allows the target page to take control of this page.</p>
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/accessibilite](https://france-chaleur-urbaine.beta.gouv.fr/accessibilite)
  
  
  * Method: `GET`
  
  
  * Evidence: `<a href="https://formulaire.defenseurdesdroits.fr" target="_blank" rel="noreferrer">Défenseur des droits</a>`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/partenaires](https://france-chaleur-urbaine.beta.gouv.fr/partenaires)
  
  
  * Method: `GET`
  
  
  * Evidence: `<a href="http://www.driee.ile-de-france.developpement-durable.gouv.fr/" target="_blank" class="fr-card__link" rel="noreferrer nofollow">DRIEAT</a>`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/](https://france-chaleur-urbaine.beta.gouv.fr/)
  
  
  * Method: `GET`
  
  
  * Evidence: `<a href="https://github.com/etalab/licence-ouverte/blob/master/LO.md" target="_blank" rel="noreferrer">licence etalab-2.0</a>`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr](https://france-chaleur-urbaine.beta.gouv.fr)
  
  
  * Method: `GET`
  
  
  * Evidence: `<a href="https://github.com/etalab/licence-ouverte/blob/master/LO.md" target="_blank" rel="noreferrer">licence etalab-2.0</a>`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/politique-de-confidentialite](https://france-chaleur-urbaine.beta.gouv.fr/politique-de-confidentialite)
  
  
  * Method: `GET`
  
  
  * Evidence: `<a href="https://github.com/etalab/licence-ouverte/blob/master/LO.md" target="_blank" rel="noreferrer">licence etalab-2.0</a>`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/mentions-legales](https://france-chaleur-urbaine.beta.gouv.fr/mentions-legales)
  
  
  * Method: `GET`
  
  
  * Evidence: `<a href="https://github.com/etalab/licence-ouverte/blob/master/LO.md" target="_blank" rel="noreferrer">licence etalab-2.0</a>`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/ressources](https://france-chaleur-urbaine.beta.gouv.fr/ressources)
  
  
  * Method: `GET`
  
  
  * Evidence: `<a class="fr-btn" href="https://www.ademe.fr/sites/default/files/assets/documents/guide-pratique-se-raccorder-reseau-chaleur.pdf" target="_blank" download="" rel="noreferrer nofollow">Consulter<span class="fr-fi-arrow-right-s-line fr-pl-2w" aria-hidden="true"></span></a>`
  
  
  
  
Instances: 7
  
### Solution
<p>Do not use a target attribute, or if you have to then also add the attribute: rel="noopener noreferrer".</p>
  
### Reference
* https://owasp.org/www-community/attacks/Reverse_Tabnabbing
* https://dev.to/ben/the-targetblank-vulnerability-by-example
* https://mathiasbynens.github.io/rel-noopener/
* https://medium.com/@jitbit/target-blank-the-most-underestimated-vulnerability-ever-96e328301f4c

  
#### Source ID : 3

  
  
  
  
### X-Frame-Options Header Not Set
##### Medium (Medium)
  
  
  
  
#### Description
<p>X-Frame-Options header is not included in the HTTP response to protect against 'ClickJacking' attacks.</p>
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/politique-de-confidentialite](https://france-chaleur-urbaine.beta.gouv.fr/politique-de-confidentialite)
  
  
  * Method: `GET`
  
  
  * Parameter: `X-Frame-Options`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/mentions-legales](https://france-chaleur-urbaine.beta.gouv.fr/mentions-legales)
  
  
  * Method: `GET`
  
  
  * Parameter: `X-Frame-Options`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/partenaires](https://france-chaleur-urbaine.beta.gouv.fr/partenaires)
  
  
  * Method: `GET`
  
  
  * Parameter: `X-Frame-Options`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/accessibilite](https://france-chaleur-urbaine.beta.gouv.fr/accessibilite)
  
  
  * Method: `GET`
  
  
  * Parameter: `X-Frame-Options`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr](https://france-chaleur-urbaine.beta.gouv.fr)
  
  
  * Method: `GET`
  
  
  * Parameter: `X-Frame-Options`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/ressources](https://france-chaleur-urbaine.beta.gouv.fr/ressources)
  
  
  * Method: `GET`
  
  
  * Parameter: `X-Frame-Options`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/](https://france-chaleur-urbaine.beta.gouv.fr/)
  
  
  * Method: `GET`
  
  
  * Parameter: `X-Frame-Options`
  
  
  
  
Instances: 7
  
### Solution
<p>Most modern Web browsers support the X-Frame-Options HTTP header. Ensure it's set on all web pages returned by your site (if you expect the page to be framed only by pages on your server (e.g. it's part of a FRAMESET) then you'll want to use SAMEORIGIN, otherwise if you never expect the page to be framed, you should use DENY. Alternatively consider implementing Content Security Policy's "frame-ancestors" directive. </p>
  
### Reference
* https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/X-Frame-Options

  
#### CWE Id : 1021
  
#### WASC Id : 15
  
#### Source ID : 3

  
  
  
  
### Incomplete or No Cache-control Header Set
##### Low (Medium)
  
  
  
  
#### Description
<p>The cache-control header has not been set properly or is missing, allowing the browser and proxies to cache content.</p>
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/partenaires](https://france-chaleur-urbaine.beta.gouv.fr/partenaires)
  
  
  * Method: `GET`
  
  
  * Parameter: `Cache-Control`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/accessibilite](https://france-chaleur-urbaine.beta.gouv.fr/accessibilite)
  
  
  * Method: `GET`
  
  
  * Parameter: `Cache-Control`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/ressources](https://france-chaleur-urbaine.beta.gouv.fr/ressources)
  
  
  * Method: `GET`
  
  
  * Parameter: `Cache-Control`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/](https://france-chaleur-urbaine.beta.gouv.fr/)
  
  
  * Method: `GET`
  
  
  * Parameter: `Cache-Control`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr](https://france-chaleur-urbaine.beta.gouv.fr)
  
  
  * Method: `GET`
  
  
  * Parameter: `Cache-Control`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/mentions-legales](https://france-chaleur-urbaine.beta.gouv.fr/mentions-legales)
  
  
  * Method: `GET`
  
  
  * Parameter: `Cache-Control`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/politique-de-confidentialite](https://france-chaleur-urbaine.beta.gouv.fr/politique-de-confidentialite)
  
  
  * Method: `GET`
  
  
  * Parameter: `Cache-Control`
  
  
  
  
Instances: 7
  
### Solution
<p>Whenever possible ensure the cache-control HTTP header is set with no-cache, no-store, must-revalidate.</p>
  
### Reference
* https://cheatsheetseries.owasp.org/cheatsheets/Session_Management_Cheat_Sheet.html#web-content-caching
* https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Cache-Control

  
#### CWE Id : 525
  
#### WASC Id : 13
  
#### Source ID : 3

  
  
  
  
### Permissions Policy Header Not Set
##### Low (Medium)
  
  
  
  
#### Description
<p>Permissions Policy Header is an added layer of security that helps to restrict from unauthorized access or usage of browser/client features by web resources. This policy ensures the user privacy by limiting or specifying the features of the browsers can be used by the web resources. Permissions Policy provides a set of standard HTTP headers that allow website owners to limit which features of browsers can be used by the page such as camera, microphone, location, full screen etc.</p>
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/mentions-legales](https://france-chaleur-urbaine.beta.gouv.fr/mentions-legales)
  
  
  * Method: `GET`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr](https://france-chaleur-urbaine.beta.gouv.fr)
  
  
  * Method: `GET`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/partenaires](https://france-chaleur-urbaine.beta.gouv.fr/partenaires)
  
  
  * Method: `GET`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/ressources](https://france-chaleur-urbaine.beta.gouv.fr/ressources)
  
  
  * Method: `GET`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/_next/static/chunks/main-cdc763525a8ea4696302.js](https://france-chaleur-urbaine.beta.gouv.fr/_next/static/chunks/main-cdc763525a8ea4696302.js)
  
  
  * Method: `GET`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/](https://france-chaleur-urbaine.beta.gouv.fr/)
  
  
  * Method: `GET`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/_next/static/chunks/webpack-9e447151ce92b4aa8322.js](https://france-chaleur-urbaine.beta.gouv.fr/_next/static/chunks/webpack-9e447151ce92b4aa8322.js)
  
  
  * Method: `GET`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/accessibilite](https://france-chaleur-urbaine.beta.gouv.fr/accessibilite)
  
  
  * Method: `GET`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/robots.txt](https://france-chaleur-urbaine.beta.gouv.fr/robots.txt)
  
  
  * Method: `GET`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/sitemap.xml](https://france-chaleur-urbaine.beta.gouv.fr/sitemap.xml)
  
  
  * Method: `GET`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/politique-de-confidentialite](https://france-chaleur-urbaine.beta.gouv.fr/politique-de-confidentialite)
  
  
  * Method: `GET`
  
  
  
  
Instances: 11
  
### Solution
<p>Ensure that your web server, application server, load balancer, etc. is configured to set the Permissions-Policy header.</p>
  
### Reference
* https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Feature-Policy
* https://developers.google.com/web/updates/2018/06/feature-policy
* https://scotthelme.co.uk/a-new-security-header-feature-policy/
* https://w3c.github.io/webappsec-feature-policy/
* https://www.smashingmagazine.com/2018/12/feature-policy/

  
#### CWE Id : 693
  
#### WASC Id : 15
  
#### Source ID : 3

  
  
  
  
### Server Leaks Information via "X-Powered-By" HTTP Response Header Field(s)
##### Low (Medium)
  
  
  
  
#### Description
<p>The web/application server is leaking information via one or more "X-Powered-By" HTTP response headers. Access to such information may facilitate attackers identifying other frameworks/components your web application is reliant upon and the vulnerabilities such components may be subject to.</p>
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/ressources](https://france-chaleur-urbaine.beta.gouv.fr/ressources)
  
  
  * Method: `GET`
  
  
  * Evidence: `X-Powered-By: Next.js`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/sitemap.xml](https://france-chaleur-urbaine.beta.gouv.fr/sitemap.xml)
  
  
  * Method: `GET`
  
  
  * Evidence: `X-Powered-By: Next.js`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/mentions-legales](https://france-chaleur-urbaine.beta.gouv.fr/mentions-legales)
  
  
  * Method: `GET`
  
  
  * Evidence: `X-Powered-By: Next.js`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/politique-de-confidentialite](https://france-chaleur-urbaine.beta.gouv.fr/politique-de-confidentialite)
  
  
  * Method: `GET`
  
  
  * Evidence: `X-Powered-By: Next.js`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/robots.txt](https://france-chaleur-urbaine.beta.gouv.fr/robots.txt)
  
  
  * Method: `GET`
  
  
  * Evidence: `X-Powered-By: Next.js`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/](https://france-chaleur-urbaine.beta.gouv.fr/)
  
  
  * Method: `GET`
  
  
  * Evidence: `X-Powered-By: Next.js`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/accessibilite](https://france-chaleur-urbaine.beta.gouv.fr/accessibilite)
  
  
  * Method: `GET`
  
  
  * Evidence: `X-Powered-By: Next.js`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/partenaires](https://france-chaleur-urbaine.beta.gouv.fr/partenaires)
  
  
  * Method: `GET`
  
  
  * Evidence: `X-Powered-By: Next.js`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr](https://france-chaleur-urbaine.beta.gouv.fr)
  
  
  * Method: `GET`
  
  
  * Evidence: `X-Powered-By: Next.js`
  
  
  
  
Instances: 9
  
### Solution
<p>Ensure that your web server, application server, load balancer, etc. is configured to suppress "X-Powered-By" headers.</p>
  
### Reference
* http://blogs.msdn.com/b/varunm/archive/2013/04/23/remove-unwanted-http-response-headers.aspx
* http://www.troyhunt.com/2012/02/shhh-dont-let-your-response-headers.html

  
#### CWE Id : 200
  
#### WASC Id : 13
  
#### Source ID : 3

  
  
  
  
### X-Content-Type-Options Header Missing
##### Low (Medium)
  
  
  
  
#### Description
<p>The Anti-MIME-Sniffing header X-Content-Type-Options was not set to 'nosniff'. This allows older versions of Internet Explorer and Chrome to perform MIME-sniffing on the response body, potentially causing the response body to be interpreted and displayed as a content type other than the declared content type. Current (early 2014) and legacy versions of Firefox will use the declared content type (if one is set), rather than performing MIME-sniffing.</p>
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/accessibilite](https://france-chaleur-urbaine.beta.gouv.fr/accessibilite)
  
  
  * Method: `GET`
  
  
  * Parameter: `X-Content-Type-Options`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/](https://france-chaleur-urbaine.beta.gouv.fr/)
  
  
  * Method: `GET`
  
  
  * Parameter: `X-Content-Type-Options`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/ressources](https://france-chaleur-urbaine.beta.gouv.fr/ressources)
  
  
  * Method: `GET`
  
  
  * Parameter: `X-Content-Type-Options`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/partenaires](https://france-chaleur-urbaine.beta.gouv.fr/partenaires)
  
  
  * Method: `GET`
  
  
  * Parameter: `X-Content-Type-Options`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/_next/static/chunks/main-cdc763525a8ea4696302.js](https://france-chaleur-urbaine.beta.gouv.fr/_next/static/chunks/main-cdc763525a8ea4696302.js)
  
  
  * Method: `GET`
  
  
  * Parameter: `X-Content-Type-Options`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/_next/static/css/00104bcde2c4b2198fa2.css](https://france-chaleur-urbaine.beta.gouv.fr/_next/static/css/00104bcde2c4b2198fa2.css)
  
  
  * Method: `GET`
  
  
  * Parameter: `X-Content-Type-Options`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/_next/static/chunks/webpack-9e447151ce92b4aa8322.js](https://france-chaleur-urbaine.beta.gouv.fr/_next/static/chunks/webpack-9e447151ce92b4aa8322.js)
  
  
  * Method: `GET`
  
  
  * Parameter: `X-Content-Type-Options`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/_next/static/chunks/framework-c93ed74a065331c4bd75.js](https://france-chaleur-urbaine.beta.gouv.fr/_next/static/chunks/framework-c93ed74a065331c4bd75.js)
  
  
  * Method: `GET`
  
  
  * Parameter: `X-Content-Type-Options`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr](https://france-chaleur-urbaine.beta.gouv.fr)
  
  
  * Method: `GET`
  
  
  * Parameter: `X-Content-Type-Options`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/mentions-legales](https://france-chaleur-urbaine.beta.gouv.fr/mentions-legales)
  
  
  * Method: `GET`
  
  
  * Parameter: `X-Content-Type-Options`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/politique-de-confidentialite](https://france-chaleur-urbaine.beta.gouv.fr/politique-de-confidentialite)
  
  
  * Method: `GET`
  
  
  * Parameter: `X-Content-Type-Options`
  
  
  
  
Instances: 11
  
### Solution
<p>Ensure that the application/web server sets the Content-Type header appropriately, and that it sets the X-Content-Type-Options header to 'nosniff' for all web pages.</p><p>If possible, ensure that the end user uses a standards-compliant and modern web browser that does not perform MIME-sniffing at all, or that can be directed by the web application/web server to not perform MIME-sniffing.</p>
  
### Other information
<p>This issue still applies to error type pages (401, 403, 500, etc.) as those pages are often still affected by injection issues, in which case there is still concern for browsers sniffing pages away from their actual content type.</p><p>At "High" threshold this scan rule will not alert on client or server error responses.</p>
  
### Reference
* http://msdn.microsoft.com/en-us/library/ie/gg622941%28v=vs.85%29.aspx
* https://owasp.org/www-community/Security_Headers

  
#### CWE Id : 693
  
#### WASC Id : 15
  
#### Source ID : 3

  
  
  
  
### Base64 Disclosure
##### Informational (Medium)
  
  
  
  
#### Description
<p>Base64 encoded data was disclosed by the application/web server. Note: in the interests of performance not all base64 strings in the response were analyzed individually, the entire response should be looked at by the analyst/security team/developer(s).</p>
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/sitemap.xml](https://france-chaleur-urbaine.beta.gouv.fr/sitemap.xml)
  
  
  * Method: `GET`
  
  
  * Evidence: `da7-dqT/FrcMr+B5VYd+0JL6294IqdE`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/ressources](https://france-chaleur-urbaine.beta.gouv.fr/ressources)
  
  
  * Method: `GET`
  
  
  * Evidence: `4a22-KacPoiU+VoEzC7MzwEYD9fQaIro`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/partenaires](https://france-chaleur-urbaine.beta.gouv.fr/partenaires)
  
  
  * Method: `GET`
  
  
  * Evidence: `35f3-X8LL8R2DQtKSqwW5CIJlYuU0HIk`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/_next/static/chunks/pages/ressources-34c11a3384a53e3a875d.js](https://france-chaleur-urbaine.beta.gouv.fr/_next/static/chunks/pages/ressources-34c11a3384a53e3a875d.js)
  
  
  * Method: `GET`
  
  
  * Evidence: `fr/jorf/id/JORFTEXT000042176809`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/politique-de-confidentialite](https://france-chaleur-urbaine.beta.gouv.fr/politique-de-confidentialite)
  
  
  * Method: `GET`
  
  
  * Evidence: `3b1b-RI45maNnMWgwROhiUrr1GBnYPeE`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/_next/static/css/00104bcde2c4b2198fa2.css](https://france-chaleur-urbaine.beta.gouv.fr/_next/static/css/00104bcde2c4b2198fa2.css)
  
  
  * Method: `GET`
  
  
  * Evidence: `d09GRgABAAAAABnQAAsAAAAANhAAAQAAAAAAAAAAAAAAAAAAAAAAAAAAAABHU1VCAAABCAAAAFsAAACEI00oO09TLzIAAAFkAAAAQgAAAFZZDkN/Y21hcAAAAagAAAIWAAAGch5gS9hnbHlmAAADwAAAEToAACPAlpW6CWhlYWQAABT8AAAAMQAAADYdwQw/aGhlYQAAFTAAAAAeAAAAJAiYBEJobXR4AAAVUAAAABYAAAFkdpwAAGxvY2EAABVoAAAAsAAAALSFg48KbWF4cAAAFhgAAAAdAAAAIAFtAGBuYW1lAAAWOAAAATEAAAIuRB1J2XBvc3QAABdsAAACYwAABX8p96PdeJxjYGRgYOBiMGCwY2BycfMJYeDLSSzJY5BiYGGAAJA8MpsxJzM9kYEDxgPKsYBpDiA2YmACmiUBFjUD4iCGYIYQMM8FKB7EEMYQDiQj4DQjUH0gQygAoDUKywB4nGNgZDFjnMDAysDA9JPZg4GBYQWEZnJgsGI0BdIMrMwMWEFAmmsKgwOD7wN/5hf/LRhymF8wnAAKM4LkANBODB8AAHiczdRJU1NhFITh90JARFDEEcVZwZlBEQQUxXlkEmRPUcWKBVX83/4n2Cf0KuXOjZd6UuQLCTm3TjfQA3TbY2tB1zKNf6NZ9GnTPu+mv33eaob8/DxDPmnxg3V22GWPfQ441MrRkV/tPKV92nk1/pTOH1hjky2//zcbbPPLf9XV/k899HKCPk76e5xigEFOc8bf4izDnPM7L3CRS1xmhCtcZZRrXOcGN7nFbe5wl3uMMc59HvCQR57nCU+ZYJIppnnGc2Z4wSxzvGSeBRZ5xWuWeMNblnnHez7wkU985gtf+cZ3z/iTFVY9Ru9fZvuXa60eNjtP6574ptS1Ydv43vw/10A9tCbzzF/O9+dYTbMeNdRObNlu1Gt7USPuRw16EPWZh+HJxbHaToU3BUVts6I2WlGbrvBGofBuofCWofC+oagEKLyDKGp6hfcShTcUhXcVhbcWhfcXhTcZhXcaReVC4T1H4Y1H4d1H4RSgcB5QOBkonBEUTgsK5waFE4TCWULhVKFwvlA4aSicORROHwrnEIUTicLZROGUonBeUTi5KJxhFNVaCucahROOwllH4dSjcP5RuAlQuBNQuB1QuCdQuDFQuDtQuEVQuE9QuFlQuGNQuG1QuHdQuIFQuItQuJVQuJ9QuKlQuLNQuL1QuMdQuNFQuNtQuOVQuO9QuPlQuANRuA1RVOYVbkgU7koUrP4Bmz3bVwAAeJy1WQ1wU9eVfvc9+cm/EkJ6ehhbQj9Iz47/9Yv/ZDPYTyYYDIaAlxgHmBcHQpKFBkgJJGynNmUJZp2m1e5saNLFm03I7NCw7ZDuhmkZZ2arTpp0M+MwWya7w3am2exMNttJ3eCq1suec9+TLBk5MbOzGD1dXd17/u453znniuEY5ouLhn5unLExLqaBYUhAtIv2FUbeyLskv+RfEY1EIxxMBWDQSDx8NBAjIRiYiM1J2KGzR49s6OnZcOSo+tvMaKp1y7Zr2wbWdb309y99UttbU9M7iA9uLH8ZWYGj9L4dTc0tTdvburqm9IXwYIry5IowG5h+hinyZCVyZaX0wYCKZiJGKcbaRfhWaiSS3wgTPCzzeRpJKEYCTmIzESkQCfk9vM2eI7kmCBXu9Mbh3X8y3Bccf/6bLb2xV9+83N1eXu5Z+1f7947s/45rjdncSboiw5HI8GP4iNS2tw+2tyuLiFAN32q3We32WHAd2xHu27CR6+0eVPYNj5yx2ysrz+0d3qds/alOBR4KkhlsZxhm4TzKQO8wnEc4KAQFr+ANe8PWQvpLeDCREH7jwc82/Ib1K8mkkkwV0PHs43t2h6PR8O49tzIDMo2Lk0r6ViFNlLy1dABiMSjsNfZTkJMhlqDFLbgtXos7DJxJvTqjqDNkOjOoV6he7xlGuUOMhRGYSoYpIXY4Dq8bDydK4HjsnBAM44sdIx/yJrFivq9iVYWRfGgUq1YNKYrCDc7/rKzabjLZq8u41jKTKX1IUchIKoWiGHLo25hVTHUhDsRNOLClBV6FmKg7uHL16YBSiNf8B+xU+ncKmU5ldP83zsUUM4yPiCUkChZgz5HyuHpSPRkn5cpPcXyKjMvq79m9uFzbk2A3o2eTKO5hh+Z61bfVaZnsvBNXp0ksnl33MScgbQJGJcYSIpKz7N709yl9oEmmFXU2TsbJeJxh6foT7HWwcAmeBJyBaBSNhEwqLB+fmwPK7PX0GHsqfmdOJjFcru25yr4PsuDpicjCLYFIEvtmSlZvkG5ZndHeU2QyJZNuGMFn9YacysoosO9RXehu1qmrQCbvyKSTxOTFugD1EiIRd5irVWdlMo52qki/DE6yYLWsbGML+oBngToi4VxKOoX6kFhhff6BfUfXR0JOPvokf0DpQW7Wrw/I5O+pJptS+ntGTpeuD93HvoCM1GnQZ05Wp2GQ1Qdlo/qgMuDznEsdjJMr6jh4PrtS3QZjCKSFM9f9BE+GgI2N7Lns6bH70i+z+9TfxdEcctZHhqgcRrp4SDcneUcXSNMXfH0zdw0sVMUwVrfFxoOb+8MkGLA7QKpQpB1hwx0OKtzHDmH+lOBgP00KjvlVDiEJ4QlurMYEh0PgBh1CKiU4wON17HkPsOcaIzJeRgIZgJ6QIW5ZoGp0IxzBCGBJdFvc3GASqSEfnQFEvZLgXAklNX+bcyGb+duUoYsySyoUntTDms4Gnv0J6qzH0iz5hZz+FALjM/KLePq/aWCgzi+CzpgPVi+RCTg4EslYENj/ieyPq7+ZiBeEalJP9svqby7EdRtk+NQyTUtwKoi5USkqQiQUYl8Ac9tn4hOkqrBABRA3ORO/QKrkPDu4lrKDhBETFUEgqbA4E/GJzP+CArDtOSuY3BqhFnLxPdjEGkUwkowSGme5pnn8gjxxQf6LCfn8hHxhuQYiNy/IF2ALbITteiz9JcR0GcXbrBSIup/PyX+4I38OoXVzTp6DEXyek/Wz7+fGMjmKYLLIuL83HAy7EY/wjxtMKQ4h3QPenCKz6mFMGQBQK9HH2U/B/S+ph8kkvvTclEvXgVndLeQTFy1uS1HQ4rXCi4yQ2Sz9JDukxmjIAAclh0e6h72e0NhkMGE18OCYcoaJQuYoyWSmBDc2fwqiqllWh9RdfaRJCSjkLGmS1V3ksqy+zzZq+y/C/m8ypYwJItEbJpHAGsigRpqEHp1hO8y1pgtm8/xvkZqCn80TMJV+SGGydQvuNzBmxoqxLBFBXERmPfljXC06jJtrzFliSZw1yEjTZAKa5vTeLM2Mr9OMXtjbsWyAIykc95jMC8b8CNQOk1ibZM4nE/MNTMs9RT0tKCzeZce9spRIBZw6pYBzzTDMwvkOMisR84mAtVYwB5uDPnAisDk8ZlOQisB7jmsQr6hPy+TMR+x1SEspdYa6zznBAa7zEf1GWaifjlP6tbTexk7ASUQsol1YT8dINGKlFoj6syYw2qkN8ivsvP5g/NiRF0XxxSPH1Tv66Nj4gT0Pdq0XxfVdD+75l4XhgdgjHR2PnMJHzNPq8bT24IMb7Gh79/Tpd9s6Mu/ztxvqB7Y9/PC2gfqGhdEz+lZ4KPpWeNA+4hnQa4qpYJyMDzTrAN/kDZpCUhTSLDYOTjYSlUykEd5EiXey0SIJWgrOKEWcrMgbCbwZuWePqv/zx9crV+xcfzHO/Xv8lfTrwV6zePbtD/aM1o/uvd9dVv3JJZM5vNFDzvcFrcLjL7+5e8vXPv/XSbt9i9ra/GCPh/NuFJ64+a1dFzsvxuc98VfYnU1PbTjwys6y0Gh1mfv+vaP1n1zybgybTUfifTt3J0ZWVQ40rHjq5yeeOUh+xnp6HmymNcUXl6iv1sEHegaCDc+J4hO4AUSb4IV5BwkavRY8tDD1WN0/10VvPHX69Oguz31ru+qElc/Zjz11I7oOnVBrz86efOzAeSsZmXxiz2hR0clVNs/IpHrJev7AYyfp/owvvmioAhkqIGKgAsx1Q0KLgijnSmVyPpSriWSSG0shnIFDjgkOtTwJ/3JxY4zhAbfQs4NGKRgORqGssHh9QNAN5I0affYcEEoAupaz15Pp18CPh1LmCjuyIZNIcf42zAgO4GQzmx0Cs4BrY+DXAtZKgUjY4s6WNRIIHRUSpB4ozNIa5ra9wgzxA2LXaxWN2SSw12mTkdF7DPQGhLMSd055RCPSApRYv0YHKI6k2OvsUIYQxmIqfQvKwSy2raY2FJk1d1lRC6I6YrFCDWbj60iuQSdpCxqBlAANaK2SZ9p0D+0oIS/UY0dpyJ5VCWQfESIAsN0S1EIVoBPbYa81z9i6rYeSScrmrymTRK7NNUGSKAewIvVJ4ETqc4zvpLbPrRu+BL8BPSVs++4Jv1k/YneS1q2GvPrkHvHbis31/xd+Q62vaPitybgZfKeZ6WRkZjvFV0BYTrQLkB5tRhMHXs57JI/UyIFb+kPRUDTGRSPBiKhhqeYSPu36IhAp0s5Qg152aP9a533y6GaJYwlhOWnzqFzn8E8Xmtzb8+SGDU+exQchvqAP/qtv5V7TwNKa/qX350ymdDrwqKhEQr5dOXc4Wk6p4rbD2fvgZNppXUHtryEUduJBOJIgvXMSfB5/KILeboUviNvDQ3DZgzRiwUlbuO+Oc0WmFa4mq2n8z8gK59qGbp/bVJ7+uauhobux0XvmDBtNM1WSVMV+US1J1dvf96ysNls9qwMfkCvtjpX2qlUtNd3zjd24XF1FrpBt/qp5tcrvr+LYKn8mJjFWHND91BXsf0LoQpq4xrCW5hxExBLkWiAT9w4h0Nw4MPiTwYHGZoUaB3qiWYegltPoBZwJPITf4aKHAgF6HD0BDRANOTK4wWpNXyVFEa0bBS/JSrOEJFguYqFK6qlISwpES0oFgjsjmF579ENtYNYxNE+eEryikBIIPjrQkVvqjfXkG+TU+vzOT91CVvSrPyZ9/XqvuRl8wwxRK95NtaiEWNwlbC5Z7hH1qPoY55pPkRPkaD7pGfV7REn/EFT8IdmsYQ8YczWALccYsQewQv2Z+aMFMTuUfg3foapOwd+y9mRfuXuWUaNm2obCl46/XhLkziHI0SL1/1SjcnpfsVyMq6XtxrJBzq9JqedaDYc9S6G9n0a1aO8iIGVBgd4tFXhDWelsSUlho7zGl5Wrb/GlLM9P8QLPLOpP2+4J/UW7zUx4qG/R56KRZfeoNSDebGlpEY+iLttSPVNGoWiK59kSnvRSDZic/IW9mwg1EOZo8Dgf9IhevR7IBAdBpHFnbnmwT4S8PJTuUTLpH2MiEcCQhlydACdNaQGuBTuZxa7HISQSAjShRVm+XvCnMNMKmQkQegFlKF9HBn/qiKCFZyeb/QbAxyq4ofiBF4JQfQJZJTSemfECzCjzt5NaW5y+lUgEtEl6d5TUllE9khS/ArgQKr5E+ngiAe3a4nqieel+sJPE2EYOynoxRpxQ3ns9WA4vUWDUdFaXNfU9sClUvL+opc1vqHPiFdVSPeNgeduWHT21nHd9rc3hKW7oqHEImwrUIPK99pBRwUvL9xhpJDz+kOFEBe6pKnEIzjqDv62laH9xaNMDfU1l1R21y+80r7k2CY6ajoZij8NWu34tV9u7Y0trObOojvMywSU0i4LknFGETknwWiW+kQ0HoaNyctGCOhyMRYWHXni1v6X12Uc7Ei0tbfg2oU8WFPrztpdemRjg1+6qLJP/tEt9e2g1fddnM33JecMu7gV6BgzBeIbOyA7SccFQIwd9HJ4A/jYEolu9NicXiRLLyIljx078+L77zOb49xMdT3z7ey+0ssMjJ44f+/o/1tWazX2ZSa5sW1WVY83fHTvy9ZMPE+fA80dibOu69OhgdbXT+SrMnhpVf731+cNdpDWa06/jnQ+DWTobyyINJrw3HUu/pmj9OPh/EuOCer2W0pLYwOP9BJelVczY8fbTB9SgaHZbOHdu10CjECBBmUi/H6AkaX4kZlIfQIBmmybSPZwrqV8MuBAjsOjAnnLCMAznuwpoi0YJIwZPOKfMsPHcmZvyzc7JzU8fHO3o7OwYPTiLg+BlmG0OZj/j4On+5/Wz0Gg2fQlVY4yEF0UD9CRRYBa/2XEXs+80B7P1DC1Wek63XIaVTYsE2DwptpzuydY0dH2weeFO/hqZRqtifocWLd0DLSpMl4LM63QcxvyP91iIx2uYECIj0X86wttEfFlBJ4IviFy8EPctqLAQ5FicBy1QpCP0QjPw5/JBmQ3Dowhe6X+GB/fLBEA2698m99TU1tb0yJcyA/U/tT6PG8MVHGzdlH4HdwziXhxBoQb/Unm76ECdiWAPGBnWdf7iM8MDXCtWDQRNHuWN+HupCKHAC5CN/ZIADYbIS/TCB55B7aInEg6FI4YdrV3upvJYvHnimbYVz/7H1upAXbC+rr+lqVk4tGH932zvm3rguWOHBu6v9cfYdyuLbR1rfaaQuOEbvfzX9resiwxXk0quZWdHaXlJ91YSaihtbI4Edu84dODRcnNDJm4vch9z1+hvnoyY4yBkkcfY0MTJLGqphwd7NbV7/zYzULLo+DiZzvuGDjJ4RvmJTD1kvTyO3gVvLMw9735rQRQla3tSf7dQgws/GufIlz3ybYUkVRZ+H9Zs9F/QF0QBAXy5WdqHKQ7Ss4n4JV+RhOHkl6IwBcKS69MY6dOkhDdVFBdXmHh1jnwW99UG6/rauh3VSbzlEBy/MrB8efH8R8XlPGv4lbOventTeHdVX93pvp7ONt1eGu8iqHCxLzJCyyxKy5KBPff6j370+ntfLgh7+rnkc9JypNHscIXawbOUHRpI9jeHqEj8d/Nmb16NX70qv/GGfPVqvKAVkplv4T+TtcEV3QY1X26DfP6zSxggT4ilLZAviSbHad0PQsv1BN8ixyhkk6l438CuLfHh0eYmNfUVTvLLePcbex9+szu+5cMTTx06oNzlM4asnJrPtN2b1yyWd0kbLiH00ub8Csnpb8mQA1xQX0KlQyDq1xB6022ib15EBFpCSP4wxUi8Yo1GgogPUG2QBmIIl/IGvDAx8KUlobXhyzvu37onvt+/NlRi4rkC0+kkzc5TUl+wMxTqDMZrfJFSs7a0rDTiW/dkaxNM90l502rlD37A/C93fqv3AAB4nGNgZGBgAOLrq24eiue3+crAzbIBKMJw5+fjSwj6vwXLOuZtQC4HAxNIFAC4FA89AAAAeJxjYGRgYH7x34KBgWUDAxCwrGNgZEAFkQBgNQPkAAB4nGNgYGBg2TCKMbAP8WoJAQBQDjfdAAB4nGNgAAIfhhOMMowmjCmMsxi3MJ5gfMD4i0mKSY/JgymJqYlpGtM6pmNMt5jZmB2YQ5g7mG+wCLHksLSxbGJ5wsrCqsLqx9rEeoWNha2A7Qa7FLsDewH7NPY97B849DiSOLZw6nG2cZ7gEuKy4crhauNawHWFW407ifsQ9z+eMJ4lvEK8abxreC/xMfHp8FXwtfF94nfir+K/IiAkECEwReCGoI5gh+ADdAgAM0MwdHicY2BkYGCIZAhh4GIAASYg5gKz/4P5DAAaxwHOAAAAeJxtkT1OwzAYht/0D9FKCARiYfECC2r6M3ZkaPcO3dPESVMlceS4Fb0DJ+AQHIKBM3AIDsFb80mVUG3Jfr7H7xcrCYBrfCHAcQTo+/U4Wrhg9cdt0o1wh/wg3MUAj8I9+rFwH8+YCQ9wC80nBJ1Lmju8CrdwhTfhNv27cIf8IdzFPT6Fe/Tfwn2s8CM8wFPwkjSpHeaxqZqlznZFZE/iRCttm9xUahKOT3KhK20jpxO1Pqhmn02dS1VqTanmpnK6KIyqrdnq2IUb5+rZaJSKD2NTIkGDFBZD5IhhULFe8n0z7FAg4sm5xDm3YpflnvtaYYKQ3/NccsFk5dMRHPeE6TUOXBvsefOU1rFL+U6DkjT3vcd0wWloan+2pYnpQ2x8V83/NuJM/+VDf3v5C7A1ZCwAAAB4nG1UV1vbQBD0kEYxAQwJkN67Ukjvvfce8naWTlgfpzvnJGH497nblWwZ0IO/mbndvd1ZS42RBj/NxvbPMkawAzuxC7uxB6MYwzgm0MQk9mIK05hBC7OYwz7sxzwWsIgDOIhDOIwjOIpjOI4TOIlTOI0zOItzOI8LuIhLCHAZV3AV17CE67iBm7iF27iDu7iH+3iAh3iEx3iCp3iG53iBl3iF13iDt3iH9/iAj/iEz/iCr/iG7/iBn/iF3/iDZfxtNEUYmkLnQZwo1Scq0XJKRFEQJjZUkvio5x6MCyUtJ5SQw601vSAyPU18psazeoSSMWfM13jmytmM9YUh3SuuStFWVcnawTQrNlnpDNVkwcWIsubiJn1QtLX1ZLYuFV3SJlkr2VSfccZk6IzQkbDkyoCRXWFHhqsE5wi2zXrlq4/eIpJ7oTKZrIcNK1yYFA8nIqlkzoEVpr68/coIXtyYjBLeGyOvtaSbxAY9YXWiV+hwk8RR67m0WijPeJZRucF3ND0wccwTxiKUbWNW66233I8M+q1sI1F3JFF3hKh/Qt0oZl/7jHaf6NjYVOSJ0XQ8JPiIvYnOcrFiRcoO+t7d4DrwZtNFyrjNDBC1kYpEsUaI7E2lLoKlUvWY6nVFsWlHQwpV6yqxwXmEyLCuTbSzk1+5itC4/wqZ9ecZMMqyMrYy63BWReiOTKyVxhGijjMpbMjBFaYbsqKdWxHy8sfzjkw5tZn3krxqasxNUUdk95pRRco7Y7vrQj0iLcp/4pBACykF99748xqlCTdMkRdtznUfLQmNwn2yQnRgG43/Nx/DWwA=`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr](https://france-chaleur-urbaine.beta.gouv.fr)
  
  
  * Method: `GET`
  
  
  * Evidence: `3817-R3R37/a9boT3ugjozCb+XIbXS3M`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/](https://france-chaleur-urbaine.beta.gouv.fr/)
  
  
  * Method: `GET`
  
  
  * Evidence: `3817-R3R37/a9boT3ugjozCb+XIbXS3M`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/robots.txt](https://france-chaleur-urbaine.beta.gouv.fr/robots.txt)
  
  
  * Method: `GET`
  
  
  * Evidence: `da7-dqT/FrcMr+B5VYd+0JL6294IqdE`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/mentions-legales](https://france-chaleur-urbaine.beta.gouv.fr/mentions-legales)
  
  
  * Method: `GET`
  
  
  * Evidence: `33f5-TuJ7M/bLA5Nh5i6Kho44PfLHMxc`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/accessibilite](https://france-chaleur-urbaine.beta.gouv.fr/accessibilite)
  
  
  * Method: `GET`
  
  
  * Evidence: `2118-CkWYwwlsoOfO/z42LPD9V6+JW+E`
  
  
  
  
Instances: 11
  
### Solution
<p>Manually confirm that the Base64 data does not leak sensitive information, and that the data cannot be aggregated/used to exploit other vulnerabilities.</p>
  
### Other information
<p>u��v��\x0016�\x000c��yU�~В���\x0008��</p>
  
### Reference
* http://projects.webappsec.org/w/page/13246936/Information%20Leakage

  
#### CWE Id : 200
  
#### WASC Id : 13
  
#### Source ID : 3

  
  
  
  
### Information Disclosure - Suspicious Comments
##### Informational (Low)
  
  
  
  
#### Description
<p>The response appears to contain suspicious comments which may help an attacker. Note: Matches made within script blocks or files are against the entire content not only comments.</p>
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/accessibilite](https://france-chaleur-urbaine.beta.gouv.fr/accessibilite)
  
  
  * Method: `GET`
  
  
  * Evidence: `query`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/partenaires](https://france-chaleur-urbaine.beta.gouv.fr/partenaires)
  
  
  * Method: `GET`
  
  
  * Evidence: `query`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/_next/static/chunks/framework-c93ed74a065331c4bd75.js](https://france-chaleur-urbaine.beta.gouv.fr/_next/static/chunks/framework-c93ed74a065331c4bd75.js)
  
  
  * Method: `GET`
  
  
  * Evidence: `select`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/ressources](https://france-chaleur-urbaine.beta.gouv.fr/ressources)
  
  
  * Method: `GET`
  
  
  * Evidence: `query`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/_next/static/chunks/main-cdc763525a8ea4696302.js](https://france-chaleur-urbaine.beta.gouv.fr/_next/static/chunks/main-cdc763525a8ea4696302.js)
  
  
  * Method: `GET`
  
  
  * Evidence: `query`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/robots.txt](https://france-chaleur-urbaine.beta.gouv.fr/robots.txt)
  
  
  * Method: `GET`
  
  
  * Evidence: `query`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/politique-de-confidentialite](https://france-chaleur-urbaine.beta.gouv.fr/politique-de-confidentialite)
  
  
  * Method: `GET`
  
  
  * Evidence: `query`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/mentions-legales](https://france-chaleur-urbaine.beta.gouv.fr/mentions-legales)
  
  
  * Method: `GET`
  
  
  * Evidence: `query`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/](https://france-chaleur-urbaine.beta.gouv.fr/)
  
  
  * Method: `GET`
  
  
  * Evidence: `query`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr](https://france-chaleur-urbaine.beta.gouv.fr)
  
  
  * Method: `GET`
  
  
  * Evidence: `query`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/sitemap.xml](https://france-chaleur-urbaine.beta.gouv.fr/sitemap.xml)
  
  
  * Method: `GET`
  
  
  * Evidence: `query`
  
  
  
  
Instances: 11
  
### Solution
<p>Remove all comments that return information that may help an attacker and fix any underlying problems they refer to.</p>
  
### Other information
<p>The following pattern was used: \bQUERY\b and was detected in the element starting with: "<script id="__NEXT_DATA__" type="application/json">{"props":{"pageProps":{}},"page":"/accessibilite","query":{},"buildId":"nfGCw", see evidence field for the suspicious comment/snippet.</p>
  
### Reference
* 

  
#### CWE Id : 200
  
#### WASC Id : 13
  
#### Source ID : 3

  
  
  
  
### Modern Web Application
##### Informational (Medium)
  
  
  
  
#### Description
<p>The application appears to be a modern web application. If you need to explore it automatically then the Ajax Spider may well be more effective than the standard one.</p>
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/ressources](https://france-chaleur-urbaine.beta.gouv.fr/ressources)
  
  
  * Method: `GET`
  
  
  * Evidence: `<noscript data-n-css=""></noscript>`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/partenaires](https://france-chaleur-urbaine.beta.gouv.fr/partenaires)
  
  
  * Method: `GET`
  
  
  * Evidence: `<noscript data-n-css=""></noscript>`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/politique-de-confidentialite](https://france-chaleur-urbaine.beta.gouv.fr/politique-de-confidentialite)
  
  
  * Method: `GET`
  
  
  * Evidence: `<noscript data-n-css=""></noscript>`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/_next/static/chunks/framework-c93ed74a065331c4bd75.js](https://france-chaleur-urbaine.beta.gouv.fr/_next/static/chunks/framework-c93ed74a065331c4bd75.js)
  
  
  * Method: `GET`
  
  
  * Evidence: `<script>`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr](https://france-chaleur-urbaine.beta.gouv.fr)
  
  
  * Method: `GET`
  
  
  * Evidence: `<noscript data-n-css=""></noscript>`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/accessibilite](https://france-chaleur-urbaine.beta.gouv.fr/accessibilite)
  
  
  * Method: `GET`
  
  
  * Evidence: `<noscript data-n-css=""></noscript>`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/](https://france-chaleur-urbaine.beta.gouv.fr/)
  
  
  * Method: `GET`
  
  
  * Evidence: `<noscript data-n-css=""></noscript>`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/robots.txt](https://france-chaleur-urbaine.beta.gouv.fr/robots.txt)
  
  
  * Method: `GET`
  
  
  * Evidence: `<script>
              /* Matomo */
               var _paq = window._paq = window._paq || [];
              _paq.push(['trackPageView']);
              _paq.push(["disableCookies"]);
              _paq.push(['enableLinkTracking']);
              (function() {
                var u="https://stats.data.gouv.fr/";
                _paq.push(['setTrackerUrl', u+'matomo.php']);
                _paq.push(['setSiteId', '192']);
                var d=document, g=d.createElement('script'), s=d.getElementsByTagName('script')[0];
                g.type='text/javascript'; g.async=true; g.defer=true; g.src=u+'matomo.js'; s.parentNode.insertBefore(g,s);
              })();
            </script>`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/_next/static/chunks/polyfills-eef578260fd80f8fff94.js](https://france-chaleur-urbaine.beta.gouv.fr/_next/static/chunks/polyfills-eef578260fd80f8fff94.js)
  
  
  * Method: `GET`
  
  
  * Evidence: `<script>`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/sitemap.xml](https://france-chaleur-urbaine.beta.gouv.fr/sitemap.xml)
  
  
  * Method: `GET`
  
  
  * Evidence: `<script>
              /* Matomo */
               var _paq = window._paq = window._paq || [];
              _paq.push(['trackPageView']);
              _paq.push(["disableCookies"]);
              _paq.push(['enableLinkTracking']);
              (function() {
                var u="https://stats.data.gouv.fr/";
                _paq.push(['setTrackerUrl', u+'matomo.php']);
                _paq.push(['setSiteId', '192']);
                var d=document, g=d.createElement('script'), s=d.getElementsByTagName('script')[0];
                g.type='text/javascript'; g.async=true; g.defer=true; g.src=u+'matomo.js'; s.parentNode.insertBefore(g,s);
              })();
            </script>`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/mentions-legales](https://france-chaleur-urbaine.beta.gouv.fr/mentions-legales)
  
  
  * Method: `GET`
  
  
  * Evidence: `<noscript data-n-css=""></noscript>`
  
  
  
  
Instances: 11
  
### Solution
<p>This is an informational alert and so no changes are required.</p>
  
### Other information
<p>A noScript tag has been found, which is an indication that the application works differently with JavaScript enabled compared to when it is not.</p>
  
### Reference
* 

  
#### Source ID : 3

  
  
  
  
### Storable and Cacheable Content
##### Informational (Medium)
  
  
  
  
#### Description
<p>The response contents are storable by caching components such as proxy servers, and may be retrieved directly from the cache, rather than from the origin server by the caching servers, in response to similar requests from other users.  If the response data is sensitive, personal or user-specific, this may result in sensitive information being leaked. In some cases, this may even result in a user gaining complete control of the session of another user, depending on the configuration of the caching components in use in their environment. This is primarily an issue where "shared" caching servers such as "proxy" caches are configured on the local network. This configuration is typically found in corporate or educational environments, for instance.</p>
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/mentions-legales](https://france-chaleur-urbaine.beta.gouv.fr/mentions-legales)
  
  
  * Method: `GET`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/politique-de-confidentialite](https://france-chaleur-urbaine.beta.gouv.fr/politique-de-confidentialite)
  
  
  * Method: `GET`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/robots.txt](https://france-chaleur-urbaine.beta.gouv.fr/robots.txt)
  
  
  * Method: `GET`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/ressources](https://france-chaleur-urbaine.beta.gouv.fr/ressources)
  
  
  * Method: `GET`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/sitemap.xml](https://france-chaleur-urbaine.beta.gouv.fr/sitemap.xml)
  
  
  * Method: `GET`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/_next/static/chunks/webpack-9e447151ce92b4aa8322.js](https://france-chaleur-urbaine.beta.gouv.fr/_next/static/chunks/webpack-9e447151ce92b4aa8322.js)
  
  
  * Method: `GET`
  
  
  * Evidence: `max-age=31536000`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/_next/static/css/00104bcde2c4b2198fa2.css](https://france-chaleur-urbaine.beta.gouv.fr/_next/static/css/00104bcde2c4b2198fa2.css)
  
  
  * Method: `GET`
  
  
  * Evidence: `max-age=31536000`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/accessibilite](https://france-chaleur-urbaine.beta.gouv.fr/accessibilite)
  
  
  * Method: `GET`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/](https://france-chaleur-urbaine.beta.gouv.fr/)
  
  
  * Method: `GET`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr](https://france-chaleur-urbaine.beta.gouv.fr)
  
  
  * Method: `GET`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/partenaires](https://france-chaleur-urbaine.beta.gouv.fr/partenaires)
  
  
  * Method: `GET`
  
  
  
  
Instances: 11
  
### Solution
<p>Validate that the response does not contain sensitive, personal or user-specific information.  If it does, consider the use of the following HTTP response headers, to limit, or prevent the content being stored and retrieved from the cache by another user:</p><p>Cache-Control: no-cache, no-store, must-revalidate, private</p><p>Pragma: no-cache</p><p>Expires: 0</p><p>This configuration directs both HTTP 1.0 and HTTP 1.1 compliant caching servers to not store the response, and to not retrieve the response (without validation) from the cache, in response to a similar request. </p>
  
### Other information
<p>In the absence of an explicitly specified caching lifetime directive in the response, a liberal lifetime heuristic of 1 year was assumed. This is permitted by rfc7234.</p>
  
### Reference
* https://tools.ietf.org/html/rfc7234
* https://tools.ietf.org/html/rfc7231
* http://www.w3.org/Protocols/rfc2616/rfc2616-sec13.html (obsoleted by rfc7234)

  
#### CWE Id : 524
  
#### WASC Id : 13
  
#### Source ID : 3

  
  
  
  
### Timestamp Disclosure - Unix
##### Informational (Low)
  
  
  
  
#### Description
<p>A timestamp was disclosed by the application/web server - Unix</p>
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/_next/static/css/00104bcde2c4b2198fa2.css](https://france-chaleur-urbaine.beta.gouv.fr/_next/static/css/00104bcde2c4b2198fa2.css)
  
  
  * Method: `GET`
  
  
  * Evidence: `23000091`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/_next/static/chunks/framework-c93ed74a065331c4bd75.js](https://france-chaleur-urbaine.beta.gouv.fr/_next/static/chunks/framework-c93ed74a065331c4bd75.js)
  
  
  * Method: `GET`
  
  
  * Evidence: `268435456`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/_next/static/chunks/framework-c93ed74a065331c4bd75.js](https://france-chaleur-urbaine.beta.gouv.fr/_next/static/chunks/framework-c93ed74a065331c4bd75.js)
  
  
  * Method: `GET`
  
  
  * Evidence: `67108864`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/_next/static/chunks/framework-c93ed74a065331c4bd75.js](https://france-chaleur-urbaine.beta.gouv.fr/_next/static/chunks/framework-c93ed74a065331c4bd75.js)
  
  
  * Method: `GET`
  
  
  * Evidence: `134217727`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/_next/static/chunks/framework-c93ed74a065331c4bd75.js](https://france-chaleur-urbaine.beta.gouv.fr/_next/static/chunks/framework-c93ed74a065331c4bd75.js)
  
  
  * Method: `GET`
  
  
  * Evidence: `805306368`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/_next/static/chunks/framework-c93ed74a065331c4bd75.js](https://france-chaleur-urbaine.beta.gouv.fr/_next/static/chunks/framework-c93ed74a065331c4bd75.js)
  
  
  * Method: `GET`
  
  
  * Evidence: `1073741825`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/_next/static/chunks/framework-c93ed74a065331c4bd75.js](https://france-chaleur-urbaine.beta.gouv.fr/_next/static/chunks/framework-c93ed74a065331c4bd75.js)
  
  
  * Method: `GET`
  
  
  * Evidence: `62914560`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/_next/static/chunks/framework-c93ed74a065331c4bd75.js](https://france-chaleur-urbaine.beta.gouv.fr/_next/static/chunks/framework-c93ed74a065331c4bd75.js)
  
  
  * Method: `GET`
  
  
  * Evidence: `134217728`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/_next/static/chunks/framework-c93ed74a065331c4bd75.js](https://france-chaleur-urbaine.beta.gouv.fr/_next/static/chunks/framework-c93ed74a065331c4bd75.js)
  
  
  * Method: `GET`
  
  
  * Evidence: `33554432`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/_next/static/chunks/framework-c93ed74a065331c4bd75.js](https://france-chaleur-urbaine.beta.gouv.fr/_next/static/chunks/framework-c93ed74a065331c4bd75.js)
  
  
  * Method: `GET`
  
  
  * Evidence: `1073741823`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/_next/static/chunks/framework-c93ed74a065331c4bd75.js](https://france-chaleur-urbaine.beta.gouv.fr/_next/static/chunks/framework-c93ed74a065331c4bd75.js)
  
  
  * Method: `GET`
  
  
  * Evidence: `1073741824`
  
  
  
  
Instances: 11
  
### Solution
<p>Manually confirm that the timestamp data is not sensitive, and that the data cannot be aggregated to disclose exploitable patterns.</p>
  
### Other information
<p>23000091, which evaluates to: 1970-09-24 04:54:51</p>
  
### Reference
* http://projects.webappsec.org/w/page/13246936/Information%20Leakage

  
#### CWE Id : 200
  
#### WASC Id : 13
  
#### Source ID : 3
