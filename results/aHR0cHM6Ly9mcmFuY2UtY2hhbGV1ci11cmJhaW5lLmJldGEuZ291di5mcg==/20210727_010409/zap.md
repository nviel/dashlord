
# ZAP Scanning Report

Generated on Tue, 27 Jul 2021 00:57:17


## Summary of Alerts

| Risk Level | Number of Alerts |
| --- | --- |
| High | 1 |
| Medium | 5 |
| Low | 4 |
| Informational | 5 |

## Alerts

| Name | Risk Level | Number of Instances |
| --- | --- | --- | 
| PII Disclosure | High | 1 | 
| Application Error Disclosure | Medium | 1 | 
| Content Security Policy (CSP) Header Not Set | Medium | 8 | 
| Reverse Tabnabbing | Medium | 6 | 
| Source Code Disclosure - PHP | Medium | 1 | 
| X-Frame-Options Header Not Set | Medium | 6 | 
| Incomplete or No Cache-control Header Set | Low | 6 | 
| Permissions Policy Header Not Set | Low | 11 | 
| Server Leaks Information via "X-Powered-By" HTTP Response Header Field(s) | Low | 8 | 
| X-Content-Type-Options Header Missing | Low | 11 | 
| Base64 Disclosure | Informational | 11 | 
| Information Disclosure - Suspicious Comments | Informational | 11 | 
| Modern Web Application | Informational | 11 | 
| Storable and Cacheable Content | Informational | 11 | 
| Timestamp Disclosure - Unix | Informational | 12 | 

## Alert Detail


  
  
  
  
### PII Disclosure
##### High (High)
  
  
  
  
#### Description
<p>The response contains Personally Identifiable Information, such as CC number, SSN and similar sensitive data.</p>
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/APC.pdf](https://france-chaleur-urbaine.beta.gouv.fr/APC.pdf)
  
  
  * Method: `GET`
  
  
  * Evidence: `509604299271`
  
  
  
  
Instances: 1
  
### Solution
<p></p>
  
### Other information
<p>Credit Card Type detected: Maestro</p><p>Bank Identification Number: 509604</p><p>Brand: MAESTRO</p><p>Category: </p><p>Issuer: </p>
  
### Reference
* 

  
#### CWE Id : 359
  
#### WASC Id : 13
  
#### Source ID : 3

  
  
  
  
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
  
  
  
  
Instances: 8
  
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
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/partenaires](https://france-chaleur-urbaine.beta.gouv.fr/partenaires)
  
  
  * Method: `GET`
  
  
  * Evidence: `<a href="http://www.driee.ile-de-france.developpement-durable.gouv.fr/" target="_blank" class="fr-card__link" rel="noreferrer">DRIEAT</a>`
  
  
  
  
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
  
  
  * Evidence: `<a href="https://carto.viaseva.org/public/viaseva/map/" target="_blank" class="fr-card__link" rel="noreferrer">Portail des réseaux de chaleur et de froid</a>`
  
  
  
  
Instances: 6
  
### Solution
<p>Do not use a target attribute, or if you have to then also add the attribute: rel="noopener noreferrer".</p>
  
### Reference
* https://owasp.org/www-community/attacks/Reverse_Tabnabbing
* https://dev.to/ben/the-targetblank-vulnerability-by-example
* https://mathiasbynens.github.io/rel-noopener/
* https://medium.com/@jitbit/target-blank-the-most-underestimated-vulnerability-ever-96e328301f4c

  
#### Source ID : 3

  
  
  
  
### Source Code Disclosure - PHP
##### Medium (Medium)
  
  
  
  
#### Description
<p>Application Source Code was disclosed by the web server - PHP</p>
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/Aides-ADEME.png](https://france-chaleur-urbaine.beta.gouv.fr/Aides-ADEME.png)
  
  
  * Method: `GET`
  
  
  * Evidence: `<?=FydSO¬ìï
û-ÙÉßyê¾Wz¬¦ý\x0014\x001ez\x000c\x001eåÿ~Þlî7ëÙýÜFâ2<~0<ç\x0005^Lª\x0017Pò\x0006w&Ûwå»b@û´-Ä±#µ{s\x001f½Í§\x0003zW5GaõËOýRÀqínæ¹®í2ÞÔÎç\x0018£1<·K]ç¯ô¿\x0014Tá%umGT8å
ôÕÒr§Aj¸ÚÈìG§1Ö«U\x0003\x0001
ÔÎâ´ý9QÜZ46]m{/\{?n^Ã»×½\x0016\x0012¿t2§\x001cñz\x0013r]YÍ#$Ý°pÛNx¥ñéH¸­¢O¿8[	4>o#>D`ÖúíÙÎHMðö\x000c¹=1Â3³íER\x000crÕßÉ¸Gg½\5°j`ÕÀªÿ¹5Àü`Î\x0011ä¶ç
^5<+®S¼Q\x0008wùjÞKæT5ïË:\x0018ÆÕÿüù2:?ÿüó\x0011¯¿Áó\x0019\x000cÏ1à=\x001dÃ3Æ°ûcd\x00032§ë¹\\x000cy!¸.þío
b¨ýÉ³9nû§Ïe9þÈÄç8\x001eùJíN~ø\x001cýÐ}E÷\x001bßøzÅ_/#Ù¥¬Õ\Î¼¹#g\x000cÚÀ^zqóãg
Íg7ÏÇ¸1û÷¿-þõ\x0018î®ÄÈcï¹+·Çb(fkxæ¹\x001c¹ýÈ#¯W{÷ò\x000b/l^Ê\x000eïct~ååëxdëÀ\x0007"ßÅðÀiÌ5c¬øCü\x000f7\x000feG/G\x0019>þÇ\x001fß|éË³ùr\x000cÛë^Ì/ÕT\x001b+oÔ±ÞßùÎwkW2;¯^íc 1\x0004ò­è¯|%Fï¯|¥¾ïûË_ölvùbLe÷/\x0006ÕûîÃðü÷¿ÿûog÷îßîk½6uðBäîw¾ó/\x0015îõÓ^{ÀM\x0019ìöÅ¸ÜµÞ\x000b]Ôg<óf7¡aè|öÙ\x0018ùcèÿÙÏ~,¬'ôÂÕ|*õþìÄÅÀÌºZ\x001b|_\x000bÌé²yXéõâÃÒù×¿Þõð¯<]G¶cXÅÈJÙ:è2v}\x0000:¯¿\x000e½×ª\x001d¡\x0007üïÿ»e±×<]ßs\x0017o\x001fAý«\x0018\x0013¾0öú#/\x0014üëý\x000fñÿX\x0006ã_Î.ç_É\x0007¿¬öPm6íõ×Ú¹
è	ÙÚ~p¹\x000cÊ¿û]»
.Ýº]qä6:ÆcDn~_	¿¨6ìZÈl\x001b¬[b`ç\x0004äuþ¦ÁÝãìÇ£?ðçÐ%ï[±QÞ{ï±FqÝÎ\x000f¶ÿÜ'ób\x0004r?ýôÓÅ²\x0000á_O\x001d¨wÚ\x0012u¡ë
`K|ë¢7ñio¨u¢ó\x0007!I­ð¯J\x00035cÄÂ)¼íkBÃ{xs=¹Ôv\x001eqèÿö¿htÆð\gFÇ\x0000a-x\x0018 ³È_á,\x0008fp»\x001dÎc0¾}ï=\x001fdàMËßÜÌïf\x000cÍÀë¹]g'Kv¸`\x0018cñ_\x0010Þ\x0012ÕÃ\x0018\x000fó¶Éá\x0003\x000fn.bÔÎ`~9W \x0019\x0008ßy\x0006^Ïîç·Óißÿí7sìb\x0006º\x0018Î¾QQöæÛÍ1>§#±Ç#ÀñÂëI\x0016.oÅèñùøâåÍ­\x0018ãoå{ÌY\x0005ÎIsÀ|G4þÂâ/\x0016Ä(ÖFÊ\x000bµ\x000eNÑ\x0018Õ\x0016Oç]|Ö³\x0000\x001c#mÁ\x0018U2¨ô÷\x0015Ù-µ3Nñ¦\x000f\x000fÜüë&Á£v¬F§\x000e(@\x001c:DoàÖ"90ºèXceá\x0017ñAó\x0002F3<7b\x001e\x0008â©k¾Y\x0000^ÑÃàÉ\x0002ñG¦Q2ØÁzãz\x000ffKtå?+l\x001cr\x000eÄ\x0011Ös­Gæ9ØVæü\x0014¯\x000bsð$\x000cï!e\x0008¡OX\x0018Êa\iC¹©`D\x0005^_Â@\x0006û­>¢\x0017\x001e°0:k|\x0016\x0012_¤\x0016«ÐïÂãÔ}É@HÚÍÐ¿1n*ÈZÆ@óÀ32\x0015\x001fKÝtY%qÉCSßÈVu\x001fj±äÍ\x0003Ã4k\x0010.=Áu\x0011|rLö\×M±Â]bça×|íd«]mïT|Ñ%ý§yêÑÚi½´Eå±|\x000c:;é>yåÁ¬ô\x0019\x00186SV\x0015I©Û6Ôq\7¥ú\x001dáÒÊ¢ huMl\x0019Eh+ñ¸BÍ/õº36·q\x0003|)\x0003Ùzìë:s\x001c<V¤¨+\x001eÞHÃ!¯z\x0010Ê\x001f×¥¯E\x000e+wå.\x001aütÞÅH¶­Ï¾æ
¼öo\x000eûÁ¤\x001fÖì{<üÙGÚèÜ::­\x0012Ã\x000b:×ÓårÌn\x001béSö\x0005t8ùg|¢ì	\x001d·ºÓrÈoXy'=â>YG% ü\x0002?ÙÂÎ§NñqÑN\x0007Îùe\x001cX\x001apé
´\x0019çuQ©mÚZ·ø&iê«*q[ä6`â\x001etvIÔßé\x0017.,ã4¤^Û\x0019¿£Aö§pÐ¬«=X§HU¹\x0019GÒæ\x0018]cò2^\x001bv\x001c.º\x000bÍ¦a\x0019~â±¹Û_Æ
\x000cÎômÆÀ9÷X¼Ä×8ðB£è.?[cwÆEÆXy=õì\x0010þ½\x001cåhiúW¹©îQ³8F5ÜCÝçû\x001ebÿoåþCK[ª\x0003Ýµï{ñ\x0014_}sé£õ²	\x0010¼ ´,F¼]É	ÒöÅ¤»ò,X§\x001eäy\x0010\x0003´^ý\x0017]Zîö~nx\x0006à>Ë¸Ìç\x0003ú\x001bL@'a¼,Ä8Üßtæ´¼XÈ\x000eh2þ\x0016ïË:¤;!æ.¾U»ûm»\x0017õXTi\x0011~µ¨\x0008
e¡·P
]ÆÓ\x001eS\x001baý]5ðÖ@\x001aå¹÷¯9$¼mÐ{ñ[Ï¯|ç¤ín©T Ð·\x0005&jÁØ¿>+î,\x001cð>å.ºùlJQóC
Vè³iýYªö|&ÎO9¿`Øk£úù8kÊªU\x0003«\x0006V
|z5À<¡½wÝiN\x001bwáÆ«yÍVìË\x000c+1Ò1Ñ¸¬\x000feM®æ<ï`x~þù\x0017cÐ}aóÂó/Kç½Y[ÇèüÌW¿¶yò©§6÷fÝ½v\x0011ß{OÖ³á#\x000cãÙðR\x0018~);Ù\x000c|)»ñÒ+e<®5¡K1\Õ|)kY£½°ù»¿û»Í¿ù7ÿ¦v¤²ëù"ù0/\x0016·ñùýÍ1\x0014û\x001dcxüc\x000cv¯ýñ\x0018å^¯/g\x0013
´1
\x0017¿Ï|uóÕ\x0018s\x001fâ:ºøÀWýêæ¹?WßYÆXË\x0011Ë¿áù×¿þÕæ\x001b_ÿÆæë1\x0003\x001f±ú\x001e\x000c9Bùåw¿û½2ì~7ÆcÅ\x001c±ö±Çb4þêS1ò=½yòÉ/EÝ¦\x0018NÌÂ8Èæ_eGõ÷¾÷½¢ÃqØì\x00188»»|[úé§Ú<\x0015ÝrÍnld}ñÅÊàìQÛ\x0018{§ávBý\x0002Áýþ÷¿We°\x001bù0u\x0002Dî>òúËõ­ç¿ÖÁådÀ++=\x000cÝmx~6»º­\x0013êåÁ|âÔo7³Ãï\x000eû\x001df¾»Ý\x001bRÞ-ý|ë[ßØ|óÑë×©6C»¡=aàîvu\x000bæÓÅ\x000fá\x000bÑÙîxqv>ÿ:uÆ\x000b\x0003\x0018^1\cønÈçûwNBã	<ºî©§^\x000cÏÿ:FØ/t;OûyþçÝÎÝÙÏZ%ÆcÚO\x001fO½û¤#åK~¡\x001c¼\x000càqâ_úÒký\x0000C6ß\x000f3\x001dWèðýìÝÚ('µýêWmPG>Oq\x0003²þ\x001bßøfé]êMï7E³OzÃØÜÇû­jÚèC\x000fß»yð¡ö´'vüã	ýº\x000eã\x0014:°¿Ãµ\x000exÖ]¯\x0017ú³B?ë§æYáª\x0001V®Nû©\x0013Û×÷ðN­)\x0004g;±Ë÷Êûß³ã¹\x0017=1@×"X-Å\x0008\x0002ÄÓ 3 ðMæË?Ì\x0000»Ä&+ve\x0004=Ê\x001b.7röþ\x001c+±Ýù]'ÜPë\x0018C\x0016ö²È·[¤0ë\x0000Ü\x0008/\x0004^Ë®ç«ñÀwßÑùíÍÉ;oå{Ñ9!\x0003Ø\x001bñïd0¸\x001cCÖ¥\x001cå\x0008ÔÃ¢-ÆØë¹	ß¡÷(7å¡1\x0003\x00060ÖÁ2<`tñ9Ìl\x0008oâ\x000fr3e×öA:äaÒ.F®\x0017cggA\x0014õ\x001cFyh©Öq³È\x0019¶¾\x001e\x001ex\x0018\x0008\x001fìÂÎ\x0017\x001fs\x0004xøIç÷
	\x001d8¨.\x0006³-ÄÁ\x0003ézÊqÀ`Aµ\x0016t\x0017C)iz\x0007+òCA\x0007è`APzîRÕ0\x0004\x0003¼7úí5v¶ÞíräN>»ÒbÀ\x000f?êµ\x000cãã<ò­\x0001
Þå\x0005\x0008z®§ßçÃr¥WþN§F\x0017\x0019R±Ö¶\x000fNèÙ²(¿\x001eÄ\x0016}z407TÂ,(Û6'ÏÕ\x000b¼\x0006¤<Ë"L\\x001b\x001b£/^\x001cÀ·ñVÂ¿:£LwqÙnf#Ï\x000ew÷°@Üt]»vd{Ú¯gó\x001f^5dò\x0010LYð WWò¥\x0011\x0019\x001aûô½VFy¶Î¸îÝÞiéëàO\x0019\x0008OO\x0019¦·¨§å%\x001dw|Z\x0008\x0010*Ù¤Ü\x00183àcö\x0015Êá!¬ÛW^âYú²Y/ÐV.\x000c»\x001a¹\x001d\ñ&$~Ê§¦Aû,\x001aÕ®Ò} ö\x001a\x001eÈñ´_ßF\x0004*«Pº@ÊåM\x001dÌ>Ú\x000f\ý°Eùê\x0005h\x0004Ò>&Üéæô\x0018(\x000fÈ·\x001f®¿ØO*Ú\x001dcugø\x0015|[AwjÛ"O}\x0011××ôõÆH(4s~úDHò¬ÿÛÃô¹¦q§_Ë8ÄÍö]´C\x000cr¶-ËkxvY6a=e\x0019ÇÚ[¶¾Ü§Ó\x0016i§ÀÝ½þÜß<·
\x001f=Á-Û'm1>ìØfpÊÒáÝ=\x0002\x001eKbÓà\x001d½À÷fÂÞ\x0013v:ã$\x0012ý÷C7ÂcÓvL\x0000ÂPö¡és\x001cÖä\x001dëxu\x0004´ÿ#\x0003aÚNË\x0017\x0002sOã¥µ¾¯ú"
/xõ÷ ËKQ\x001cåÆ\x0018Ô÷Ô»6w_»+f¸\x0012Ïw»v÷û¢ËèF»8âÑGïæÙË²z"ÆÃ[5Õüô§Súèmê°îÙ5î6ÖrSç!\x001e_í§2w=Qd\x0019¿\x0018\x0017y;¾yª¼DPÃKÞ
s´1º\x0005®nÕÀªU\x0003«\x0006V
¬\x001aX5°j`ÕÀªO\x0006\x001fôÚ_MM"CÏ\x00032-)w\x001an'\x00045Oj\x000cfÄë;vÖ\x0006F^ÖvnÈÛ9¾ú\x00180ì8mÃ3F¶\x0018¿úÌæ«ÏÄðüå§zçj1¾µqÖ\x0014·j0äxæ>¢ù§Á¬pÌ»ÚXxµÖhkºVùoÿí¿ÝüÇÿø\x001f7ÿá?üÍO>9NÏsSÃ3;;1\x0014³ãøG?úa/?vÆ²\x001bøÆ<±uÑðgbt^Í\x0006>ý\x001c¡]Åìåøhx|þù/Ç\x0016·áùßüV}ß¬o\x0001cüÃ\x0008gîüÏÿüOÿþßÿióOÿôO5\x0007ëOÇ]\x0001öóo|óäûZôót­¹\x000eÆQÊ½«õUÎ÷¿ÿ\x0018¿_Æç'x|k\x000cçXe¿-1û¹çräùÏ~V\x0010£(uÃÚ(iÿ÷ìxþû
Gm;W\x0006blþá\x000fPúá»Åsí]¯_Aþ¯~µ¾¿Ük
q?ºîù¸§
öü\x0018¾}öÙò\x0018YW&FghA\x0013ý¼\x0018C/Æò²#ý¿|5:þMª¿©úþö·ÿvó¯þ\x0015ßWþFÍ±Ôìâë	/ô\x0008j ;}9z\x001cÏ:#ùõ®3Ï'­ÛÆ6?þñ·k1¬\x0015Ð¦þá\x001fþ¡<G³\x0013ÿÙgÓNã)£OO{¯ôLxê]Ï\x0018ÖÙ\x0005M{ã\x0001<ÇÏõÍ~É¡wv#\x0013\x0006r<\x0006óØqêÎuQ õ!ûç?ÿyµkô\x001dÏ\x0008ßþößåo\x0001Ü\x001dßs-\x0005{\x0002rC\x000b\x0019î½ïêÖ#\x0003mocxfM\x0003\x0007ÔÓnÐù\Ã\x0011\x000f\èÛG)³×S®ì=nìÖ¬Á_ÝªÖ\x0000mmú©\x001e£ûÞD<×ÆíáÝÉðür\x000cÏìàÅp\x000b\x0008»cRH°=Fç´î­Ño3OÃ3,bp>áù(°¾Ë)
\x001dÜÜØåQÎâ®\x001d\x000cÏ\x0007áùbÞ<¹£\x001f®å­ 6<¿³ÙÄè|òN#à&ýz)x7çKYÄè|9ÆgøÆÑ±0<ßÀð\x001c\x0014éjv;ss?È5Ë\x0018 \x0018Ûèñù æ­ñ9×mp\x0011:;û\x0001bYx¥óçfoYg1À'1:`ü\å\x0013±ïN\x001fåf·\x000bÑ\x0001\x001eÇÀáà1o\x000eÜ\ô\x000c,ÓAÅr\x0006ZÔÍ mÚ¤n \x0005}ýþ`e>y\x0014:È\x0001Yð¾\x0019ßGC7ÿðE\x001aeè\x0008O?eÜ\x000fO>ÈC:Ðxo²ð'OÀ¹Ø=ãå\x0007(½Y¦ô£\x000cÓ`¿{ ´-\x0003ýª[à,üÒãF<of³ìÉ;á©ÓÒëÒ\x001e mYk\x001apÖ\x001faù\x0016R\x001e~âÁß¤¡N8ð3\K:ù§à\x000c£/ßâ\x0002R¶\x000f:¶k¯§Þ)kòhYÐV&áÆµÛøè´á\x0019\ðf\x001eÃ@×uqÆ\x000f<Lg>âÌk\x001crÃ+PÞ¤O~Õø^Gé¥O^è7¡eìËhYÀé,\x000f¨_\x001f\x0010}Q@£3º²M++t)Bù\x0000Ê²ÙW(\x0007 Ú\x0005tÛ\x0000PÙ÷!i\x0013rÕeÉË>_gp>9\x0017}×
\x0016½wûúäÊÚéÿ¼2>ÜûºÚ¿6ç|Ò¢à' ÖäÓº\x0014vù»¾zÖ5q¸}Þ¥\x0001´ïL\x001cÉ?úU÷[ûýÃñßxàtö5Û&íÖvLñû\x0010\x001aSîy=yoàä\x0001þæµéä%­ùî\x0017f¿óü\x0005Þf¾nÏ}_ò\x0013ßrt\x001dÙÏÕº?Âz^Îáåµ\x001e»w}x:dT¤<\x001f^¹SE.nýÔ\x0001t».\x001bîxÄðÌË\x0003¾ð×;yY\x000e#4µO></
Pv=£æù´N\x0003)}q\x000fiÈJØç\x0003Â]v§Óòð\x0017j;yI\x0001G\x001a\Ïºïp^¦©gíÓÏwà®nÕÀªU\x0003«\x0006V
¬\x001aX5°j`ÕÀªÿù5PóÌ\x000föaùBO(jÚ²¢±UÉz^ùF­%ßyLg]¾Ó\\x001fb~Åçw6?\x000eC\x0018>»cðÃè\x0001
Ãó×¾öõòO=õônÇsrÌ\x000bå\x0007|~?þq\x001b,ÙíQ\x000c\x000fÞ½Ù!\x0011õ<s@¾[üïÿý¿ßü»÷¿ÁÏ5fæU¼TÌZ&ó.võ6ý\x001f³¿}ÛôSòBó}ÙxVGaç\x0008d¾Áa\x0010C)ï%ÿ]ØîÌÁ\x0016£-Æ=tzòõäKu\x0018\x001c9Êú»ßýNmòd¬G\x001f}¸
ÏßúzÊnjGoS\x001a£ ;ý®ô³Ïþ¤\x000c¹è\x0007Ã&ßá\x0005òMjv%ã1tbÄøÇøÏú\x001a\x001eã¥ßxþÖÿÇÞhYq$iúæÎ¾\x000bJ ÐT©>§§ªfy~y«îêê®THÄ %;bÑ\x0006ä>ÿg\x0016ÿ
»ÁM¤î\x0012s3\x0011ài\x001e¾{¸_÷?Ìã½÷¢OÐÞ8ÀßÏ?ÿ|ðÅ\x0017_\x0004Èîr]:3XXÀ";b@_ÂÇ­çáã=\x0001ÚßÀ3Çm×ô\x0000Ù8ø%èüuèñî]@b@Ô\x0007\x0001Ü>
\x000f\x0000z*ä§m¨\x0007{ÝÏ{\x0006(u­ÁNöû¨7ý
Çý^a<am.Jþ4\x0002þ5<à3}¤î)ðýpú÷ß?¾s]gú÷D8>ÛVÂÔ}LÀm\x001cmG\x0016õ´®Ù¼áO\x001eú;r³\x0017À5ý^§\x0003 ¯êG}©\x000fíkàv¶C^Ú\x0000\x001e=\x001a//\x0000H\x0003Nû\x000fe`Yã%:f~×n½h/zâÄñ!ð\x000c\x000f÷\x0013Ëí{ø¸? \x0017\x0017a\\x0015xæÞû*´÷Q¼GC|õ\x001aH
´ûcì^*µ¿¦TØ¿\x0005xÖV2hR	O\x001dÎ,\x0007ø\x000cà<§7d°zÔÛ$\x0001àª\x0013#Úª& 5M
kÍ"Oø¶\x0006\x001a\x00021èÌ&_\x000c\x0012Íê\x0004°\x0006úIM\x0000Ï;Àó^Y<ÿ(à\x0019g\x0001Ïß?\x001a|¯ö;§ÿXÇ8Å³xAk\x0001WÅ\x001bàyM\x0000ñÙå¨í\x001d`·íÐÑà;\x0002BÛÚÙÀsZ>\x000b\x0006\x0004pfPf>g\x0019°\x0019ð\x0015ÀyC¨ë\x000czÚH]uME¼6W\x0005F¯¨Þ+¢k¢\x000c\x0012\P\x0006\x0005;\x0006
\x0006
;\x0003sLÜ(HãÄ\x0007Z(\x0003´ÁJ(\x0003Ë¥lx¸\x001cxÃ×tðªÎ\x0003y@SnåÕ\x0003~ ø²|fÚ¬«Ëù9ê<¤Ã_Ó[\x001e×ÍÜ¦GN;×»ËËõ\x001f	×ÑíiÅÖ\x001c=.}À\x0007¾u\x0012d¢ó}­?²ÒnÖq­\x0003éÐ­å²¬PdðE\x001a\x0007­\x0017|ë\x000fº*;~óqùîCË¯ÔñæQå6ÏÞu·Þ+Í\x001fùC³Êë~mêv¥\x001dÌ»ö=Â¸çÂÏeù,Sü åØ÷üÆµã«ü.ÇÔiLÍ7
èüq¹Nc¾¾ZNËN/\x0001åªzsz(ñÖ\x000bmÆå<ø)Ã{_¤©õ²|;=~TûÛ0~ úÇ	má\x001f&Pd²sðãªÔåB]®ëçr)³QÄû\x0019âè/:Üuv/gZeC\x000fUÝ¼¿Þ½äú\x0004<§Þé\x000fm\x001büÒ:ÖtÉ'5`¿©õÂð>)à\x0019µKÃ6'Þi»Ôy»´½ß¼·¦#¬{ïôP;úU×_ÃË\x0005§æì
^.Ê±#Ã3¯û®ùP6~Ê¯}þÉ½û©ûoí¯Õ_åùº\x001c¨eòìX\x0016ûM\x001dï¼Üçé«e[Æ.­i¯ÊòQ÷³<.¯Æ\x0011VÇ6Ëhi3/aëkY·´ànÛËc
t»\x0000g¿\x00043§\x0013uèôEýÜ\x001bê$eQþá\x000fãFÐæ>eb®n-c\x000c\x0002xºdÙÌù¼\x0010ÉoSô?îES'ÙÿÑ«\x0013¦f¤£\x0000\x0004£óÓ@Ý6©g\x001aß¯ªToñzú«×@¯^\x0003½\x0006z
ô\x001aè5Ðk ×ÀK§\x0001¯\x0011LYkÔëY ¹Y°$âp»uÃp3uC{\x0001<_¼xipQÖ P[ê>1\x0018ÀóÛ:~#¨ù\x0016qZî\x000f
0àÐ\x001e
y\x0000ÿÎ\x0007|¾Ðì\x001båþÑ¶ms\x0001\x0008s\4/érôô-\x001do
=uêdXñ9ó¡@Ø7\x0004Xú(åíÍz-×¶KKK²VÕ7\x0005\x0002\x001ecøÀ\x0011Ë\x001c7ÌZÔëS»æ;Â¬\x0001)ÏÀ3ólYJÙ_ËJ\x0017@ûúõëª#ß±>\x0015ôÕW\x0013xæ¨cöª/\ ^é\x0000¼³Ü¤½aíüÎ{\x001ck|bhëoóÂ\x0017\x00078»¸¨ã\x0017ó8è\x0001#±p\x0005\x001cÄØ 'é\x0000%Ç\x0001Ï\x0000X³Ö\x000bkpãe]@çççÕniÉ\5õ2ûÐ\W&WQüèËñ\x0000´\x0000æ\x001c1
L»à¨ç#Yç\x000b\x0001?\x0006\x0008Ï·»q'O¾5\x0002ÂÖ=Bäár_¯ûÀì1Òf8Â9æ\x001d\x0010\x0017
6´¢õøªöqïÞ»;l\x001fäõÞ\x0007\x0008ø~8\x000ey\x0001éçPêÄÞ\x000b6ð\x0007è\x000b\x0019\x0001Y¡\x0015xF×àÈ\x0004ýøã\x000e`=Q\x001cû\x0015äõ^\x0004÷ì+P\x000fú <\x0001ág°\x001d^
<Ó7làóXý¼~J\x0003\x000cúórÃÎ]úÎ9nç,ü[à\x0017\x0005ÐCî[ä^ï]÷	Ú0÷v¡äµ>è/U¿äé¯^\x0003­\x0006³ªkcÔ»Jíï¤\x001bÎU+MÜ§¢kñÌÄ¨íKuTÅ\x001f»~
ð|@ÀsÏ;w
ôTË	ÄUÒ5}¯a½\x00019¢ \x0006\x001bQ\x001eÖ)Y&ó``M\x0012\x000f\x001e"(Àó¤\x001eôIÏ3¢;4¨$ø,àYó@à3ô©¬¿x_îÁàÞF\x0011H8+°|FÊx E\x0003x\x0016øË1ÛkzÐf%ã¬@g(à3nº\x0001¡7£¶\x0013\x0016à\x0003à,ÇwåQÙxl1¶\x0015ã[Ê\x000274ø¬	ðZÇ\x00026\x0000hmb\x0013Ï·\x0017WµÙ¹SØª\Ýàõ 	õÁ¤á	0âÐ\x0007\x0010Ê\x0003
46pU\x000eþ:È³±ÊÀè\x0001\x0012n·ÊaÞPó']uä­\x00172ÍÊb£09ªÄyÍ´öR&þ_B»ùkÙU.×Ñõ$®ê$údRv¯e©2f\x001f¥¦¼³þ\\x0006úöäã0Êv\x0019æ
µ«2üvñ\4iáQe7/ò»¿¸X>ÒÔËýtîCÄ²-s­\x0017~øTYì'e"/}\x000c\x001d\x0018H´ú\x000bZå­}ÛrY7·e3uù\x0006óà¯\x0013\x0016d½ß
Î#ß«>¶ªËtZ(iÜ4jÎ\x0007­\x0017iÕ´ò­<¯z£¿8\x001f<Ñ\x000f? \¤Çu/óVj¹Î\x000fûû­\x0019ÒÞü0©?NÜnð·LË÷Èay\x001c\x0006­e»LËÎC¹ã\·~Ü»l×±g?q\+ï^ä_õ	ÏÃIùÅç:¢Ûz¡Ë_re;r´oU½\x000f]=¿\x001bÓÿ°ý#wÓ?-ó©åV?ñ[Ý×¸._ß£\x0007ü8ü¾·ßÔñÐ\x0000"Ã\x0012¹rÕ"ô-myk_Ä?®¿:<5½yÀÓ²â·l]ê±\x0001Zý5ÃÍ\x000f\x0000ª_b\x001b}±\x000cÙüÂrº\x001e\x000fZùáÏ2yy¥\x001dã\x0008Ë8âGsÆ\x0012Ë=NF¾I\x0016yÄ.è²Åc\x000f\x001eÇÀ\x0001@óy\x0016NÙØàÍæ<\x0005¤Êß<qn)/\x0015xl6×\x00027\x0016¹»6u\x001aõ\x000c~á¹Zó&\x001b+8E52BÓñã¯\x0017¿
mñLÅ,_Mã<Ç\x00154ègÑ>:¯DþO¯^\x0003½\x0006z
ô\x001aè5Ðk ×@¯^\x0003ÿá5àuB|ªªHË@¿ú\x0010SÖ­¿M®°axÆ{Ý\x0010<ý\x0006Â\x0000UY¿\x0000<c{á|Z+s´ñ·ßÞ\x000f0\x0019à9¡~çÝ8nûÐÁCa9zPu\x0010`\x0019GacyÅé¹s	Ð²ÿn.¬\x0001=÷ïß§µäÔ\x0010]\¼* í¡¥)V¿{÷î\x001b~ØròM\}æ\x0018j,³Ü<\x0005ÏûÓÚg
Å^\x0011njj:m,~±fEÞ\x0004ò\x0000 ï	t¾\x0016À\x001fVÏ\x0006¨ßzë¤@à£QG@VÖ¼\x0000.a|I\x0016½ßÊÂ6u\x0005·Ú>õö[Ã<ä\x0003\\x0004T\x0004D\x0006 Df\x0003Ñ\x0000È\x0004\x0005\x0018åxpò°~u\x001e¨gd\x0006Ô\x0004t6ðì6RÆ'|\x0012|±.ÎÏÏ\x000f-yiÀkx¨×Í¬¹÷ºÞÀ3`;Ï^ïBiG\x0000Q\x001c\x0016Þõ(èÇh¯2?¥I;¢Ó'ßò\x0001ÕcmÞ|NÒeÓv^óÂ\x001f¿Ëc\x001fÀû~³®ß)c@x\x0001úþ ïgã8BÝ@9}¤^ÕB\x001bÐúâÅËÃ\x0017,xI#µqô=,ÉqÈÍ^3>\gú\x0002ú\x0000¿P¬õqÿ÷\x001fíìÈÍe\x001ePä5\x000cP\x000c\x001f\x001cíå:Ci/Ú\x0018ð\x00171¬\x000bóõ\x001e	Öôì´\x000f\x0016ü;\x00048ïØ9+ÝÌ\x0006ðl\x0010½\x000b<ÃÇå¹½Ý'è/vì9ó\x0001<sùy¦.Î\x000f¯þê50ª\x0001æªêjlÎG£sÃ:ébrhÓ\x000f<cö¦OìB\x000fædéÅ3.,µ1¨Oü&\x0007ëzÃfCGbC\x001fûM&½ÍÄæ\x001f\x001bØS\x000c¢ ó¡aX¥\x001a|¦5¸MÉÒyVr|ßY$´\x000b<ÿ Þ¸'\x001a¤À³øé9\x0007o+\x00038ãÖ\x0015>·kÏ`nçnQ\x0001ÛÏòã¦4øm
`Æm4tS\x0013\x001c ó&`3NV(ÆÅ;e\x001axÆÒ##\x0013xÖÑzc'Aç\x0004×\x0018lµ¹µ³ ß¢\x000edö3 à¯Ã\x000c\x001e¾¢nâîp\x001e¸ð£_\x000fì¦Þp­éàáÌÔ\x0003\x0014å\x0010_Ã eF?
æô¢\x0001\x0001ßáæ3vËâÞ<»é\x001d\x001e	?ÈÄåººn]JzÒtë\x0002*o½gm:³ñß\x0013¸e'-\x0017<­ÛJÑ{-´äµ£\û»<ÜæPÒø²n\x0008ÃO<~|\®óÀ¸Îi ÖiÕåëÒn>&1&4SêÎ=úðäWe°,º\x000cx#åÖötxºr\x000fèìïJ\x0013¡\x000bó¥|üU\x001e\x0011N¹¦ðã¾^ð¯WåKx\x0007?rB\x000eZ/âý\x0003\x0000J\x001d´þ\x0001\x0007øÌE\½¯ëÈ×­óXë1\x0001#Î}×å@i\x001fÊ·s{Ñß¸H3Îuep\x001aÊvYU\x001eü\U~·)qvµÞä¿©ËêÒ\x0007ÿ½PioÜ-ëÙzºf.w´ß ª¶úNã<Ò¶5músÞ_Uëí{¸Tåj¿Û ¶\x000bqÝð\x001aæ¼ðær\x0019]J?ÛÊÖqÎ\x0017 d\x0003<¯¯¯\x0005oËá>É½û\x001fÔý²Rü¾¯i×<£"?òX.\x0005î+µßáN[©ëRy#Ë¬¬q<³®KÍ2[Fâêe]\x00028Û2Ùòd\;æ9\x001c¹[ÙÛxdåJ\x001bªµ\x000eýM\x0013daÞã¥\x0017~[èÍzh¢Óª×Æ>!²®±KÀsü\x001eÖdK§
îQFFæ8e;ã\x001c2ÑæÙîISÎÔ}ÊâèÃ:ãÅºd!¯Ô\x0015ôG2Õ®X>lmÍ\x0003Nî\x0013IaÂE\x001b¶\x0003iû«×@¯^\x0003½\x0006z
ô\x001aè5Ðk ×@¯ÿø\x001aÈßû¹h\x0016+\x001d¡ùÝ\x000b\Ã<³hâ\x0015ÞlÔ{Ý\x001c^÷&u8èOó\x001c}>ÊæÈä´\x000c¾\x001fg~ÿø½\x0000o\x000f\x001d\x0002$\x0013ðÌPZ¸&øgÐù¼ø\x0000Ú\x00018\x001f8°?\x001c{C\x0000f|k\x0019ððá#7çßÔ÷£ß\x0014\x0008ûúàÃ¯$\x0010+kc¯9'µ»)àöâÅK\x0002/\x0006ØÉ¾aºÕXï\x0001jâ\x0008ã\x001bÕ\x000f%``UñÂ\x0002GC/Ä>U®K×ãxb¬¯]»*Ýë\x0002±
ÎoC\x001f=úª@Ä\x0003\x0001$ò21Àô7_s,w\x0002È7ô½]äáSN§N\x0001j\x000bHÖQÛ|C\x0018 \x000f\x0007¸\x0008H\x0003x¶¥5\x0014Ð\x0019p\x00130\x001cK[\x0000á\x0004åg$Oáãgs\x0006\x0004Tôþ\x0001\x0014\x0000ïOãðÓ7ì\x0000öçÑïü¼\x0000}\x0019ê5ûcä\x0003Å\x0001¼Úxõ?ÇÛÂ\x001b`ÓûPÀfdÆïÖ-¾ëõ¼_ÄFÔ\x0013GÙ¬É½?\x0008õ=rä¾@îeÐ_k%Îû\x0000³2XC>(2Þç\x0005\x00009¾\x000c8C¦yñ6\x0001ÀÅx0'¾í|áK\x0001¶\x0017¾þB}öèÄ\Ò$ð|:dæ\x0005	ú*//Ð\x0016\x001ccC¿·oßö½sçîà÷¿ÿ½¾OþûÁ\x001fþðhÛ|6ùÂlk\x0018¼>b\x001e \x001cW¯.õ¾u\x000f¥­gcØóåÜÓÌ½Wöb×â\x0019àxu\x001cß+ÇÚ9Áç9õããÑG°ò¦/æþ÷6Ú=/úB{t\x000få9b=g.ë\x0014\x001fmÓ_½\x0006F5ÀþUu5VóO\ÚßI\x0017óãDùùï\x0019à@A(â@\x0006Y©\x0013'ø¬Í}û\x0005:ËÅQÛ²xÖ$\x0011N ô¬7tÎýÎª"àù'Y*óvÈ\x0006:X\x0005\x001býI W\x000f6ê¦\x0005\x0006ÃsVoàÌ
|ÞÆà©A\x0014\x0007ðl·ü¾ ¾¸§:\x0017ZààLãxà\x0005Å3[ÉëªàÊÚ&àylÜ¬Àç)ÎÓr\x00027dÕ¼Ü:N{]@ó\x0006à¹èºê¼¡ü:\x00049¨\x0007T¾ßÌ·±vKÑ
¾/«\x0001°MÔÆ2\x0008JeeåÍÙ\x0013\x0001f¶C\x000e\x001e\x0010[ê\x0001Ã\x0003v\x001d\x0018,C»±Û\x000e<¹±ê
ÖjåP.A\x0019]Ç U'
ï°JI;-p~Z\x00004ùVik]ª\x001f\x0019j\x001eî¹\x001cwÏþµ.¢­K¨ubê:;­óÂ\x0015ÿ¸æjûèèdSõµLOæ\x0006ò\6Ôõv~tç0dµ¼ô\x0007&\x0004÷\x000bä£ê\x0008\x000bÝÇ$íEX·nÜS\x0006¼*¿Zïê/ËVÛ\x0002?éÕøÔ	Íu\x0012G=±ñ"Ë¯r;Ìe@«Î¬\x0017å8Â-7g=t®goUÏ |pU×.òí\x001c_ëê¼æo}Ôûxä"¾ë(´Pø:\x001eùy[\x001f\x0000Pë\x000b>¤å\x0007\x001c?¸¡®å¢<û·¢¤qYÐªGÊr[ÎtO<~×\x000b\x0019Ð<¹ý\x0008Ã÷¸z[&xU9Hk9 æ\x0001å"\x001fyL-K
3o§:¿ùU\x001cï|¦¿¸KGGÍ òâ

Î9ûQ\x0000\x0000@\x0000IDAT®·Tëèøæ0ôð¼Ëé\x0018\x0004ÔßvÎï<ê\x001d^Ö¿ý]þµLûk{Ô°nÞÊrÜÆâßÊËcy\x0001$ã¸m\x001dµÍo\x0011Ë\x0004­}\x0010?Ï\x0005Î~Ç\x0013VÓ\x0007ñ\¾§Lú>rú\x0019¨2ûùp¼ãªüÁ°áYy»\x000cSÀ[Æß|f\x001dnlö\x000fÔzéÊ²!7zf¾jõ]óÐwò>¸ñGûQö;Êåt\x001a»#Oü°àß\x001437\x0017Ü².\x0017Ñ5¯\x0000Nð\x001a`³H
v*\x0003\x001eÃ®MßoÇäa;KÿÔe
àZc\x001eAáV÷\x0006 ³/Ì	p\x0006ü"vê\x000cÚ85±ëÒór·\x0002SÀF\x0005Ã¼ÁCãFüÖñ£åÖûz
ô\x001aè5Ðk ×@¯^\x0003½\x0006z
ô\x001axY4ÐÎþÍ?*y®\x0007ZKç¼6
á¬qºñº
üv­I:¾\x0017ûÕW\x0017\x0005Ê}5øJ`ð½»ß
(Åª÷[\x0001Å³wæ(j,ÃéôR¹æm\x001cÖ¼çe1}AÞâsøð¡\x0000¡XÊ\x001e8\x0016·a©ùU\x001e}@x\x0000V¿á^mpìõcaMËÑÓr:¥}vÖÌK×\x0004\x0016¦E6eÅ~\x0014ë3­Ëâ»¿2BÛ'Ké'O\x000cnÅQÞ·Âb\x0018Ë\xCÙ#\x0017ûRà\x000bß,å7oÞ¸\x0019`ã	Ï\x0000¥ª\x0007d w@ud?ë¬K±0Å%`(Kæ«úläÄ`~á7ã¿\x0019ÌÏÿ&ËFn\x001ciýdk[»¢k\x0000g;¬
\x0000³®\x00038ÅQ\x000e\x0016Ïþf0\x0000) 3à3Gm{\x000b\x0005\x000cýóÿ\x001cîâÅKÒ
Feìsn¨ÞG\x0005`¾.^,õÓæB\x000f´IÞû\x0003D¶U2²¦õú¹\x0000 «á\x000b`3ÖÙ¸íÂBîÜ¹§ºÞ\x0013ýVëÞ\x0019ÕeÜvéðpëèsaaaD^döþ uöz6E.ï *û\x001a¬ýÆú?ýô9¬ìïÜ½3l\x001b\x0000]Â°¶æ¥\x0007(À³û\x0017å~ñù9µ¸/¢?X÷ô\x000f\x0000}ÀÚãÇ\x001cÈ£¿ñ\x0004º¥]n¨¿\¿~+ÿã\x001fÿ0ø¯ÿ5Ýa½4Q÷a\Iõa¬äy\x0019\x0001ù\x00138Âòøú}aéÏ\x0002XÂã\x0000ÑO|T÷bÙC'/Ç«={vpùÊeµív}ã9Ý\x0013£À3zô¾åÂÛuleÍ½+\x0003ÏÏä­mf^Ðþê50ªÜKc_+]õ|T©ýt1O9N4îI£Y­{Ô6\x00014\x0003>\x000bÕ4Tþ9½Õ\x0013à³ÀâÉÝ\x0000Ï;\x0006:\x0017@¨À	}{ySoà\x0000:kp\x0006|^Õ\x0003¦m9\x0015&§N\x001eÀ3T\x000fÍ\x0006âí\x0018¶q|·\x0006\x0019ñÑ·\x001dfÄ3@gY7CÅû'\x0001Û¸§º\x0007xÖ\x00037#\x0011\x0001y\x0000×åÂ\x000f,±ÂÞÎ7£÷ì\x000b:#ày²\x0001'ô­gfÁáV~MJYò}h÷a5ÍÑÙñ ³ñ\x001a\x000eYaò«ÐÆÉ\x0007XÐ)½i3£ÍKÜ´60\x0019\x0010ºÃ\x00188¢)D= 0G\x001bWïë áø.e\x0002 \x000fi¡\uBÀÏÄQ\x0007-Ë´\x0015
\x000b%ú­àK\x001dbp-ÛðpÓv\x0007»z_ý¤÷ExuÔ)ê'\x001amßÜ\x000fÃzGÆoÞæ\x0003ï\x000cØ8n'Ô.¥NÎ\x000bõ$\x0002\x001fQÒ9¶pÝ¡Ö1ü¸7\x000fdc2°Å»ÛÇy]whm\x0013îk½ì/éÜ¶×ñæ;Âp.ø\x0007G]jÝ\WSÇÏo,úÇ¡ëSeÇï«[û°Ësù¥êmCG\x001a\x0018\x000cq_tÝ]hõwå ¾®s	?eÖ|!e1%ÜåAáKëÀ§\x0007ø1\x0008¥~\x000e'­,¢¿.\x000fË8R&e°¬?h·º½ ô=;÷AÓ*ë1¢\x001bËÒ´ò¸=«{Õ|äïÞWø¹(ßÔu\x001eG»¼"Ó\x000bû#ÙbB¥_§/¬¨q£a1ZtÏ\x0018I°õ4Lò=-oñ`öOjÝQ÷ÞáP·i7l\8iÌ³¶©û´)}ªë'<\x000eV\x001eÕ\x001fºQ½ Ô\x0015Yè/vµßW¿ãMÉgìÝ8äò3ègÞ2úÙ0u8´^\x000fY({+\x0008g~ÑÑÔÐç]Ö©Ë¶¼))\x000bàVç¤%_½Ú7zÑ¥Áú×òCya(çX~ÿ1ç¶s:\x001b\x0000ÓòR]©¯Üô´~ïéÔ\x001c\x001c|2(Ï[<r)O¶sÊr2!{ó;*¾ë=:%\x0008`4¼»ø\x0019.Ê>ýD?\x0019\x0015f\x0017\x00057jhê\x0015ÀxÖiT?y\x0007?®¤øù=!Ú\x0003Ï¡þO¯^\x0003½\x0006z
ô\x001aè5Ðk ×@¯O\x0003^[®²\x001e^3@«¿[ËõÍ0Ó(®ÙoðZ\x001f
\x0018ÊQÒq´h\x001eµý 9j{wX_¾ó\x000eÀóÉ\x0000c\x0001d\x0001ù¦/ßjÆâõkY\x0004)kÒ/¿Ìïç\x0002v¦ã(éCaÑ»?çÉ!ü¥,wËPìÀ×W\x0004d¾&ðÏ\x0016ÊX¨æ)¬	'?`èy9@è\\x000f²\x0016ÜÈüâ\x0001ÈÈ>Ùâb~K\x0019PïÐ¡\x0001\x0003î\x0012hº]ø\x0000ßÆ\x001a:¿å2 1\x0000é[\x0002ûÞ:ù\x0000?\x0001Ï\x0002e÷\x000b|Þ677x Ïtr´2ß¼ÆR\x001b`ýKYóYÌcÇ^\x001d\x001c{Cù±\x0004·9²\x0019\x0010\x0013+\äÅJrX\x000f³®\x0002:\x0003pBË\x0016ÀÄ\x0003:ã\x000089ò\x001aà\x0019\x0007ðlggçaÍ	(ú§?ý)\x001c²=}º.kÕ5¹uÕEz}
ðõ°ê­\x0013fÕàÃ\x001fÐÛ\x000eðÓ\x0016êì3"7\x000eËgï=\x0012N¹ylº\x000cþôéÌ»w\x001f¨¿<\x0014}¨ðÝâ·_í°_\x0016ÆÇ¢¿Ðg\x0016\x0016\x0016¢<ïA@s}ûÞsd¿±\x0002¤±¼èí©tçÅ\x0002(moè\x0008vú+ =VÅôe^\x001c\x0000´Ú
\x001dËzø}öégOå>ùä3Õe6\x0000wÀt^\x0016@VÜüüüpO=;wn«M¾V\x001f¼\x0016ýðë¯o^µòÁûo\x0008÷ßÿû\x001f¢#§÷<²ÿæþ\x0010VÒ\x0006oß¾%w¥³;Ñ§ü²Âk¯½\x001a}>tìØ\x001bñÂ\x0006ÏºÄg~uÕVþ+aO=>ûì3½xpI/_ì\x001cº\x0013'\x0012x\x0006H·Å³G\x0000÷Cú\x0000ú¨mR÷h\x000b@g\x0000hÒ\x001aÏ ÷pLÍ»§½\x0006b4ös.\x001bÕHtd\x0005UjM©°§\x001cç{Òèy¸þ¿ÿa·1Øø\x0012eã\x000fÀ9h\x0000³l=§\x000bàYo$Í\x0001<k²Ñ\x0013N
\x0016\x0003\x0001Å\x001aau\x001cv\x0002ÏuO§7 Gç§£û~\x000e`ø ÞºÛ&¾S\x001a\x0010§´á7¥xSy7\x00042CÅó±ÀgÜ²ïÖ>¤dQ±d\x00060ä#õðæxíM
Ê\x001c
¾c¯Þ\x0002\x0012ß\x001drÓ²~\x0006xÆ
æ¶§U´êuô2.k#tEø1ß^\x0015 lj°\x0019Ê\x0004É)T\x0018LÈ?S¹¡¡Î¨\x001eÛõÖÐ¶;\x0006s \x0019\x0018ì<XsÏe@
æy\x0010¯4ê×L|\x001e,R£\x001bî\x000cJvÄ?åÖA)7©Û·#¬¦±ß²¼CÀ{\x0006ÔÖ{Sû£¢úÃ}p×ÁÔaP.òpÕ|NkJ\x001d]Oû·¢äqZç§?Ú\x0012Mêª\x001b&Qqø¹,\x0013íCÿ®àÛ4vÖ­õK¹¾àmG<y¬?ÒXFó\x0012æ6îÖ¼µÝj<q4N\x000bõ\x0005oòÔ¾WëG8e?r1ùÛÁ¿Ê\ý.ÃÔu1_ó®áãôÐÜ°ÇpølQZG×ÕÔuv:êl¹ð'ßl\x001bü\x000eszÒr¹Î5
áã²HëtÔ\x001f~8~T¹~Ä#\x00133à3üþáF¹¯K)Ïå»\x001cë\x000bþ8÷E·ËuºúÃ·öqdpÏüM)\x0017?ÔrÞ\x0017áNC:Ê«éðs9¬Ò\x001a\x001eÊ\x001fxrÿV\x0014~UwÅ\x000bðª.Ã	6ëõ\x0002
	]=\x0011hØß½ÿ?\x0017í+×iÏcÑæiÛÔé»q×0§s[rï¾åþæþ
urïk\x001eó².*ÍÏ*h.d¬Ð\x0008÷s(}ÝÏ/þêjº®ü.\x000fÙ«çùÁsDÕò»NÄ¹\x000eð·£\d²\
\x001e\x001fª|)»eÎgÑ²-³;&pßå³ë\x0017|¶1ËN\x0019§§-_þ¶ \x001eÖË7*Ã Ö#öÚ6Ëi\x000cúÌ¨yY?tWwYóÈúæøD\x001fðáwýÍ©<îj-]Ç¿\x0012ånßÎé\x0013rúÝfÞYV w$\x001döcvjøÑg\x0005\x0019¸R6Ú³Í\x0003?®M\x0000g\x001dA3ºÿÛk ×@¯^\x0003½\x0006z
ô\x001aè5Ðk ×ÀK¥\x0001~÷WW×»^[Wj­¤Ö\x000bú§\x001bkgöar/½¥+9ªx1Ü½{ß\x0006èÕ3'Çþ\x001axÞ¯ýûý\x0002q¤ã\x0018i ^\¼&\x0000ô,§¯\x0008\x0008[\x0014</«Í7\x001e9ú¬:e,Çì+Y;\x0007x«c\x0001Nó»Î{\x0003t\x0003Åqôµ_D\x0006À»zõZ\x001c+ÌÑÂX\x0010{]E=\x0001z\x001dÃ\x001d\x0013ðãð{¿ÈfV(GMï\x0011n\x0000ÀÊº\x000eð\x0012ëSK\x0000Ç\x0000\x001bg[\x0002³ûQGÿ(,ý7Àä³g?\x000fKÓÇÂ\x0013\x000e\x000bØ="«î#²ðå¸f;ÀfdÅ"2¼OË¾gêI9^³×v­\x0001¡\x0000Ï\x0006T»\x0016ÏÞó\x0002<ÿã?þc¸sç.èdÄ5¹U\x0019ª¬\x0005\x0008|ôèA°2ÒÓÑàÔµ3kaY@O[x\x001bPÆÂ\x0019Ù\x0001©/À7u²`zFG^ß»÷½Üwá^}õ\x0000ç£á\x001f3ê^ËØknz#ë[¯·¡u¯Ñ{Pò8\x001diÐ\x001dú¥\x001f,--ÅK\x0001æAú7ul»\x001dÀ+Öë\x0007\x000f\x001eSgÿõ/ÿgðýËà_å¨\x000búcßtX\x0019Ó\x0007xéÁò¢'G\x000f[e.-ÝP_üFýý\x001bÑë\x0003\x0000gÜÿø\x001f\x0014ð|p¸w¹àÃ¼n[ú\x001dmãÙ[XX\x0008\x000cóB\x0000zöÎ¼\x001f\x0004 LßþôÓOã»Þ\x001cç¾wß®Á¾ýêã¢Ô\x0003Ð\x0019G½ê~¼wB¸÷D¼\x001fäý"\x0005¥lâI\x000båò\x001eEÜôz
\x000c5Pç¯ÜÇ\x001aFÅÄç­qsT\x0013?Ü\x0017¯÷é\x001f\x0002ÏSz¸â8\x0006t\x0010p\x000bsÀ\õsm?O\x000c\x0000±LÞ&:©É,g\x0000h
0\x001a%\x0007\x001a%E\x001f\x000fVô >Õ¾,º¦\x000fÕÓÁÙ\x0000Í9üü\x0013Ñ\x0011 \x001cÛ=+7#`xjF\x001b\x001aHp\x001b?~?ØÐ ¹.º"
Í÷Å\x001fà\x0019Ð\x0019\x001aÀ³@á°zÄ\x001cÓÓ%Ðyÿ`&Yè´\x0000ç	}Ô~BÇ{ë,EY4cÝ<\x0008\x000bç\x0016x\x0006|Ö ªJ¯2\x0006Ø¬\x0001V	^BË\x0008,\x001b\x0002£)4ÄAPADÒ\x001fTaªÇÞÄÁÚ9ê¤ÁË\x0003\x0019~\x000fÊ\x000c$ÞôõÆowI=¶`O\x0017ñ\x001f÷\P_\x0007'ü0ë ä¬RòÃ.6¡Ñ·\x001ca]G\x001eÙ\x001fBèOòher}º´¦7/A¾ú	£î]j}tãÌ#Ók3Zo¾­5Î:z£¿nöS/âh3;ÚÌ\x0013'~_Èïôè\x001a½*ÿn'\x0017(\x0017¼¸ÙåÖúáwYÈg};
aÜî¦ð¬¼k_¬õJë±\x0016$LúC¹\x0000¨ü\x0008vÛÍüI_ÛÂ²nU/òÛñ»\x0017cZ:FZê[ãÝ&Èbâ·Ãr0×Åi\x001doJ^.N¹§^ÔÉÀ3o\x001c¢O×\x0013¬3¨û\x0019´ë²áße_¥\x001eG\x001cf\x001d\x001axº\x001fº?XWP§ëär·Ñé×é,¿ëãðzï4ÐzÁ«RËápî+Oó/äÉá\x0004Ïç\x000b)FL]/ÚÄWÕ\x0005a[Ý;ýÏÑV_¥£`Z\x001b×>7\x000e35î»²\x0010ç°ê'Ìþßý\x0006J¿\x001bGkZó5ÿ8ÐÝ´JÉïÿä\x0018I\x0018i¡8ãzß¼ ÕuèÊáxä\x001e\x001d;³nÄwóÀ8ËAYuLÁÏóiÇ½ÓB<.h·\x000cÊÃm¥K;]Ê|²>­B²¼ÔåñØ\x0005ø<­Sp¦äB&ý¡.Y\x0006s&r\x0000pçüéq*©OHyÙ°Ø©·¼wîÐ÷´À½ëì6ÉZö\x0019I\x001b:0u_¦^Ìó´\x000b.\x0017g¼\x0015¿S·«¬\x001d¿ ðO§¾¤\x001fwü¾£>ø}\x0011\x001f¿mãW- yQ\x0010I0ÌOzË|4\x0014´}Í·§½\x0006z
ô\x001aè5Ðk ×@¯^\x0003½\x0006z
¼\x000c\x001aà÷?k\\x000bø7JÞ®#µ\x001aP×\x0011¦®_Æ)µ\x0003\x001aªû²× ¥¢ÊÉu\x000eßx¾² ó¢Àç´Æ¼7¸+@v·ö¾ýí[Ú\x0006xÞ\x0017G4ïc¯.ò­Ú´Ð½råëk\x0002å¾\x000e×7ß|=(GlïÒ1Ï»vqÔó¦Òë¨j\x0007e½\x0007ð\x0007\x0000ÈÈï½÷n\x001c%ýöÛ§ûJ\x0000vgÏr´p\x000b<\x0003b³·°°\x0010àæ\x0013Çeí»Ü|[ùb\x0000èu\x0017=2\x0003¶¬'±bæÈf\x0000ÀwÞÁ\x00029AoÀ?\x001fÌ~$¸K÷X\x0016À\x0017\x0002\x0005ý^§¨îÙ³k°[nß¾=!? 8\x000ep£¶/È2\x001aàÒ`- »\x0001N@Nî½&e=N¨+\x0014ù\x000cP\x0002<9s&Û>}úôpß\x000fù*ð\x000c ¯ªÉ±f\x0010\x0018ÿª@Ø×Ã¡¯Õé[yx\x001e\x000e0\x000f/ôÃ~#rcíL\x001dêþ#ët¿(@»Ü¾ý­Üý G\x001cTyGÃqô8 3öñ^\x0004\x0014\x0019¼fÝN?ä²\x001fàýDÖÛ¶ºEÿ´UZ?#ª±hGÏâä7y\x0001ÿy	\x0001
np¾`í§Oeñ\x000c¸mc'ú_\x0008\x001fÊL\x001c
À\x001dßúþf)¬¯]bñüû¡Õ3ýÔ:ÑÈe\x0007\x000fd5èìý\x0003ø»ÿ\x0002<c\x0001OßCÇ´\x0007:§ùÂ\x001bç£¶±x¾rå²¾ñÌ1ÛÚë\x0010å9\x0000tæÅ\x0006ú2mmW÷à©$áô?¨÷b \x000f\x000cÞ/º½BIý^\x0003#\x001aÈ9q>]ôT©ýtÃ¹p¥ûôOÜ\x0018cñ\x000cè<\x0004\x0005Ârô´ú­çÝñ½ä9
 S\x0002õ*Õ@OÎ'\x001b\x000ctìÎ¾\x0010]\x001e¬	\x001c\x000e'e#,IX\x000f(ÿ¸èøS\x0002§5	N\x000b\x0018\x0014(\x001c\x000f\x000f\x000fÜº¾ë¼.\x000bç5M\x000c+zø9b#¼W\x0002xÆb	ð\x0019\x0010K \x001c\x000f¶\¨IßlÖ\x00136Ðd\x0018 3À³\x001cßwÐQÞ¸ÍÙ9\x0001Ë²n"ViY\x001b¡ËB¡U×\x0000Å+¬u\x001f\x0016ÎÈ­rPo\x001c	)
P?­	3äåÞ\x001dÊM\x0004ÆÄ\x0006õ®\x0017:ð\x001b¢­5)÷ÄÛÕÁÅ\x000c´ëÈWóº<ç'=\x0003O×Õxü¾rAoNð­ë_\x0002<e0u¸¯²:\x001cêò]?ç­t\V\x001eæ]uâ0§Ë¸õÁú)VO8Ê´ìDÇQ
¯î¤Rã¬óqui7ëGÁJäò\x0004\x0005µ¼ðu}ÜwsËð$ãpÒ¸\x000eµLÂp¿ËeÂ²ßõs½ \Ö\x0015å\x0001`òC\x0000Êe¦È¿ÊÔõ;Þy WÜèÏs
Þ¨tÝg\÷.u¼ÛÖ¼LkYùÞñ:®RÊ³s~âÑ\x001d³\x001dzµ>\x0005}ñ\x001aê6R/.Òt/ë\x0012þøÝ\x0017ì7%Þi \\x0011&:×´\x0015åºOXþª+óâ*O·ÿ8:-´ÖÁþ­(2:\x000e½j\x001d\x001c>.ü[ñp¾_ªm\x0013ì³íôë\¨ûºùvëî¶!¾\x001bç<Ï£­Îhg¹ÆâÙáÐêàUã\&á¥R÷\x001apÇU?ý{SÇ9­ËV9ºýÒ2\x00038ÏÎÊ*WÖ³3zAÌáÎï{ó"Üe®2T?2vÓ\x0010Æ\x0018Zå5¿Jk¹nc_\x0005~.M=>8­´]ôÔ¾ B¹È0ÎUÙ«|Ô+_ì¡O>KÈjÙ(ßcGÒ\x0004CfÅ%'¤c!\x000b.Ï)««íËZ9÷¦åñê*ò&0
Ð¼W\x001b\x001e{öÈRË\x001em£\x001cgYá*¨\x000eÔ¤B£a3Ï· s~ÿêiôw,9Æ·äsS¤ôw
ÇðKWuøÃYtX°ËÌô©CüÎ'ªq\x0003Ð¹ýÞ\x001b²öW¯^\x0003½\x0006z
ô\x001aè5Ðk ×@¯^\x0003/\x0006Øoñ\x000b¨u
P~÷ÇNr]S9ÎµlîËF½cXG\x001bÆåo5\x0003\x0004§»\x001a\x0016º·o%¨·K{ô§O¿\x001fÇ<:%\x000b]\x0000ºWÀ\x0018ô¶?[Jcñüõ×Kk×¾	`îµ×
=\x0012n\x000f{ÿ²¶£~X^¿~#(ëDöýpd\x001f|ð~83öµølÑ½®	ÍoÚþUü¿Ñ:Îû×S\x0001\x001a¿óN\x0002Ö¬ß\x0016\x0017\x0001Ã\x0017\x0005\x0014.	4å³X,ÿ\x0014yXgâØÆ\x0019+^öÖ°ê\x0006ô\x0006dG½ª\x001f\x0016Ú|Ç\x0017\x0001\x0012S\x0000Äb\x0005|îÜ\x0017\x0002AïëEôüD\x0015Ç6Ûz\x0018\x0015õe}{ùÊ+q\x00044G>Û-,,\x000cp\x0000è×Ë:@V\x0000g·\x0005@ëÃ\x000f\x0003l\x0005xþðÃ\x000fÃ\x0019xö¾çú§ou\x0003æOMÉpmjF\x0016¼Ç\x0005¨¾%w"ÀLÖò¬×¹\x0000]\x0001¡èÄû\x0001\x001cY
O\x001cÖ´èÇà;û}\x0006å)çÆ[ánÞ¼\x001dGC»Ýß|3gÀõùùùàoÝ³\x001fkgüÞ |Öþvìu\x0002ÜÒ~´\x0013:Å\x0001â\x001aÎ\x00002õñ7½¡{Ý\x000f¯³ý\ýèl8êBz\x001c@u¾`ñ^¼\x0018`=A±X÷\x000b\x0001ô½¥%¬­¯Þ\x001cüñ¿×7qíQÛèú\x0019h"'mÉ\x0004´3ý\x001d}Ðô\x0003;t\x000bP\x000eè\x001e¨\x001bÎû@ðÆam«ô+WÄG¼¶§ã¸ú
<»]Ù? /{4¦ô\x0003ÂqÖ;òèóMzóöW¯­5ûYìi¥«)=WUj'Ýp_p¥\x0019ÎYê«7þ×?lrÄ6lqäv\x0003:\x0003è°!¶¦Á\x001d\x0010A~\x001eîm\x001ad¡S\x001c!\x0000ø\x000cÕÀ®^N\x001b:Ã\x001f§Qi°©£\x000cÅH\x0005k \x000cÚ\x0008§|\x0013²Ø½Wàµ¬$oÒ¬}ÿh°¦c\x0019VE\x00019b\x001b+êUñÌc¶\x001bàYéÃYÐ\x0003§$ç²¤\x0006tÞ!:-`28f{Coù¬H\x0015\x0015\x0007MàYà³fü	:7\x0016Ïî\x0011\x000bÐïKÇw\x0007õðÎHG3\x0002f±î8
º
g»~EÝª¾)¸\x0016?B:0\x0000Ø1pÛ\x0010&4¾\x0018P<°wi\x001dh3ïn~xÔ´ÜC=hR.þî\x0005ÈRX*:ýÏÑ.*#~\x000f 5\x001cUFxX&Ó._îÍÃ~óÞMn~,Ç\x0013½<Q.tÄä¡þÅ\x001cÄCáÃ@óG\x0018åÖt¤çr\x001d¨#¼¡æA~OV8ºò»\x000c÷\x0015â]\x0016¼pËyý£Á\x0013¦ï)²q\ÔÁåC)ÃÎõ·Ë1­zrÝ-óû¾ÒZ¶e\x0008A?ÖU
ãM½\x0019=çÓÓù
uÒà\x000fLÕaN3Ë\x001d'KC¿¦ïë8êZøY·è\x0019^µ_U\x001dº\x001cSóCª?ü]ýpçµÜ¾Ò\x000fèÇ8÷A×¡¦¯üÍ×²ÀÇz®yð;)aõ²,må¯éí_÷\x001a\x0017VyvÓÿz÷P\x0019/\x001d3½rò%\x000f÷eóu½+Å_ïIë{çÛ¶:{\x0016x&®ºn»§ËêöQîsxõ»uÓÔðn¾VÖì?Ö©Ç\x0000Ë	\x0005lfñÌ"\x0013\x0000z«\x000bÙì\®©µqÔi µ~ø¹ÆéÏòB-³ÇÔ.­i\x000fÇ¸â££0ËXç&A]Çgå³,9PeïÊèñ+Æ®ÆÒyº\x0019C\x0007¡K½è7<Ö:\x0001æ\x0015Àß\x0004ó­hÍÁËO#º\x0010Ç\x0002\x0007öï	·_o¤W} Oª5Û*ëóoÕ5¥üz\x0012BO9¯®ÄÂù©~«>Ñ\x000bèohíØà³ëuoÚ®\x0001Í\x001f
Oþ5ÂÄ½~ÌF\x000cå*g\x001f>\x0005ÀkS§îôÀs¨¢ÿÓk ×@¯^\x0003½\x0006z
ô\x001aè5Ðkà%Õ\x0000k\;³.ðoý¬ûóûßkô?SÙá&=15ü±´\x0018
ciq±µB¾qCßÎ»)\x00070úÁ\x0007\x001f\x0008xþ@\x0016ï4Ö®iyëæ­á·¡ÉýúÍ\x0000ãÈõçáÃ\x0007ãøaÖE\x0000ÅS²öÚÐ¾ö½{ß
<ü6@Dö½V:zôÈà£\x0000WÏ\x0008ì>\x001d\x0000-¿Ö÷u±îüì³¿
ôûzd-%0 ìG\x001f}¤ý¤©°L]ZÊc±µc\x001dkÝ±ïÏº\x0011Ç)VÔïý÷OG]\x001e}UõÜ\x0013u¥ü<]+×_é»Ôçeõ|þü¹\x0000@ã\x0004,p
)ÖÀ2\x0014ãqõ-G8Ûù(hQ¯÷\x0001+\x00018\x0001«\x0001\x0001Y\x0001q\x0000ÏÔ\x000fG{xÿ
ZgÀnë\x000cÐ\x001c=æ·¡ß\x000f\x000bgÊry¬¹íXÿzo\x0011ÙÁr ? 1\x000e ÔGr\x0017 ÖG^\x0013\x000ehO;RO,»qóóóÏûð³\x00155eÖºÔ5:åÙâ\x001bà¶\x0002¹þ34kl\x001f§ÍÚ)\x0003r\x001cúå~ÀÊàÑÃG/xiàó²Z?\x00172¡W\x001cò¢W\x001cÏÖ\x0005}\x0006ëb¿DÀ·óÅ	[?üá¿Èý^\x0000t\x0002ÏÖ/ÏÔ¥K"\x001f\x00149i_\x001cò\x001a¼Gnt\x0004ð\x000c\x0005\x0004·\x000eØÿ@Wvñ47ëú4/@`NÑ^ð¬0&Ñ\x0016xæ%\x0008Êó¾ÛÞ\x0014Ã3È>®÷|Ð\x0003ñ¹ûµäé¯^\x0003ã5À\x0004S]MÅ¼ÃU©ý\x0019\x0015öKgãyb\x0012ÐFßö\x0004x\x0016À¸\x0003xÖ\x0000;'\x0000wNtZ\x000fúçI\x001d'\x0015q\x0008ªÎ­\x001e®\x001dÆÆú\x0019\x000bhz\x0011æðÐú£· \x0006Û\x0005\x0008_@FSÌbä´*çU¬q¥ó\x001eø5mLN	ü£¶EyøÂâYy6á­7ôä
-±zÆM
tÞ¥óºÊYW\x001a¬jV 8WT,ßyæÛÎXxÛ°Mµ(\x0017\x001dÎh00ø\x001cÖÎM<ß^Ö`·¼®
VÕ'Ç\x0019ýÐhÚ&åb0ð Çw£96I0®Ì¡\x0002´\x0001\x0013µ	gü\x0000PûÄà¦°\x0018h"\àeÃ7Ú#¹ä_	ácMâ%\x0003É\x001eG«º\x001cê)\x001f? Èª?ñ_÷m\x001dù¤kääÊ¼üj]7<\x00126¨3\x0017´:×Ùaðc ´ã«K#°ùC\åO0÷ð6ßq4&ìØ\x0014÷ÛAY?~@¢£ªçYõ¡\x0004-ô-rý\x0010Ë5°ìJP\x001e^\x0000ÙÙ®Y6ç·!;ºnêß\x001bÍ#s²\x0004øÍo²ùÎ&y|_<êYôF[\x001eU¿Æ\x000eB.õÐGéWy¼l31Ñ_è;¢ê[4r4þäó¤\x001fizîóûé\x000b>¼Ä\x0013	²\x000fÑ\x0007=!¶ÇÔ\x0007¹R\x0007èR\x000e½è¹àÇbü0oäÎ\x0015õâ\x000f}¨éSøõ<Q´¼kâI¥0ÞÔ³Ë4NÛ\x0002¡hk|p¡rë3vá\x001eã¡.\x000fÊEZ.ê_øÑÆü(ð\x000f\x0002ÿPº¿Óç?4(ËºåÞ~Ó&iÈk~U6ørÏN~0B£7`\x0011q¾H\x000bß\x0004u²-k7?(iH*ù,³óÕ4¡ùã|5Ì~âÌÇaÿ1¨ê<`GûÕ¯-\x001f:p;V}X/ã¨Ã~,£úWë\x0005xÆ\Ô. IS]/åÙuûM÷tî³]åá8()~Ë^pôãqt3\x0006ÚÚ\x0019¿yA»Î²æØ>
èú¹pyÇe4µ¬UÎ®ßi,·óB¹L]\x0006å1gÄ"Zã\x000b÷È\x0002µl¦5Îù¡.Óñ(ox\\x000eã%EÍc¾\x0007n8~ÑGâ£#üËq\x0017\x0018S¶cÛEQZ6\x0013gÙùÍÉ\x001c
åwÏÞ½:\x0006Mn¯CËq*ÛYZÔ´\x001b}"ë	_òV}Å1Ù¹,[¡,\x0001\x001f?~"]­'ðÕ³Àgó@\x001fì1'¥ÖÚ6ð\x0018ý\x0013B4\x001b<üÃ|¸Ñx\x0016À3ãZD&Óþo¯^\x0003½\x0006z
ô\x001aè5Ðk ×@¯^\x0003/\x0006X\x000bä\x001eÎßþÜåÚ\x0019Úú3¿£Òx9\x0011ée­´Æ\x0011\x0006H\x0006xîÚ\x0010tÆªr×.ç3qÌ3À3`¦M¬/^¼4¸$uñ\x0007Â=\x0014ÀwèÐÁ°=tè@\x00005-Ð9g\x001dq-`óá\x0003,y\x001f\x0006\x0010û[Ë\x0002\x000f÷\x000fÞÿ@ÖÕ§ß\x001b¼+ëã½2Ló\x0011ÕKKKñ½d¬<ñÇ\x001aRÊa}õá\x001f
~ûÛ\x0006\x001fü±ö¤æ\x0004PÞ\x001aÜé-ÉOÚ¥ëX§.
\x001eÿôD§Sj_}EÆB¢±ÔÉYèü\x0003;sæý°\N«î½ZË	\x0018Ö:4ÖÂZ\x000f/^¹\x0012âÅ\x0017Ã\x0012\x0016@ñ{®
 ü¯P¬©±ÌåØr\x001aca\x0001`ñx\x0000Xâ¾öÚëa.§\x001dxïl/Ê\x0015J~éÆ\x0001Hþö·¿
gàßÙûê«?ýéOá\x0000mý\x000b\x0005x\x0006?sæ\x0003Éu0êá5<ëáééÄ\x00028AvÀêþý\x0007#À³×Öì9Ò\x001f\x0012`%[X\x0003ìöåc¸\x001c9:ç[Ëó\x0002uß|»wc]¼;ÖØ\x0006aY§Ç)rÂV¨K^©\x000ftxï^¾ `kgSÖßì\x0007³îÞ&|o"#\x0017\x001e8²\x001aÇþ//¤sÌ6\x0000þ¹s\x0002??\x0017Ç¥³we1}ú7\x0005èL_?uêdì¯R_ôBß\x0001x¾|9û9íqï^¾\x0010ð»ßýnðw÷\x0007¿û»ßÅ1ô\x0007Kí\x001f9ò%\x0002ÂãñSCS\x001eÏe¤/¼þzöm¦~Mÿf_ý{;\x001eeÅÄ>\x0000 <ßà\x0006@_¼zEº\x0011ã\x001cûSSêkóqÌ¶Úöþ,Ô{L¦î\x000bè=÷b\x0012\x0013bïÅû,¤õ¾N»oAþê5ÐÕ\x0000½¼º\x001aï½ªJíï¤\x001bî\x0013®4Ã}.õÿjñ<\x0004õ \x0003>3®è¡
àYG,Ïê\x0001Õ\x0000\x0001\x0005xÖ¤2%å)
êÕS\x0001êðêñ¢r\x001aT¢\x0012\x0005H<qÚ¼\x000b\x001a ±\x0006*Y-ªÀ6ò®è¨eM\x0006\x0001<kcpM\x001b«\x001a|Ö5XaulÇ½\x0016«\x001aÀá\x0005¤iw2¬·ë¨
Ü\x000e¹8^[q«:¢wUuÓÖä`U£éðsì¶vQ±Ìo[\x0017E¡8\x0006\x0013D\x0017$\x0014~Àï°tf3Vµt<\x000füSÕaY©«# \x0000\x000c:éÄFÿõ§¹4TÛ\x001bá±a
oév²\x0001ø¦$;þ\x001cD4á(Á\x0008ð\x0010ÿY5ì)Çåvé°PË¡÷ 6BoD'4c\x0016PiõwyûÞ|¹ïúÆrrßõ;¬¦µß\x0014¾\]þÏÞkS\m\x0016qÐÜ,\x0007`§y¼ÙXí²\x001dZ½ç\x0011äðÉ\x001f9L\x00088®ÐI´{SÚ\x001e±ßÀ\mfOT¦É¤ÕÃ°ßH¾¬R¨¾Cß0hk\x0019 ÔÃ}*ô©r#¬iCÊ\x0008ÑþüC\x00044}ø\x0011\x001eÎßÈO|2Ðc¯\x001fY¶ø4z°,ðÿ¼U\x0016O]\x001aiÓí\x0011ý=-Åq*\x001e?Ãê}Dù\x0013õlÂí7%\x0018¿ïágÙð\x0013N½\x001cOz\x0019íÐ¤ñ\x0019ÚÓ~(yÍÓùÆñ¯/âçàcW°Øoùùbç0Ëì² n7×³írÏuÖzÔ<÷óüæõ¼4ÄuÓÕr.ïß\x001e¯þ\x0016c"ý.ûÞßÎs<\x0007×ÓTµ®ãü5ô5/÷¾ºáj>¥Õs*ÿy\x0017eTWû\x000b~~\²¼¦[ýÜ#«]í·øk\x001f·´îñòUüTGömøÛueßJþqé\x0008ã2¯*\x000f²l%kÃÏåúi·\Â\x001d`m\x0002¯NoJ\x001aû£æË±lïÅ\x000b s\x000f}¢9\x0004Å¹O¶ºåØhéR? B&Í+ü\x0006j\x0016P\x0003Ìô\x0005Ò¢2¨þP\x0008\x0007xÞ¹o<o\x001bì\x0012­:¥
Q^ð¡%X

\x0011õ'æ;õÈÇ<%×Á+±ÙÀ3\x0016Ïëz\x0007\x0012kg¾#ö·\x0000Ï!Yè(Ôº\x001aOêx=ð"ú«×@¯^\x0003½\x0006z
ô\x001aè5Ðk ×ÀK¬\x0001Ö1Þ\x000fb]Ãoÿøño¸\x000eH?á9Ô¬iz/-Ã4\x0011§µ\x0003éµ\x0013k Ú¾¦£¬\x0001\x0011¡7eÉ53G\x000cïX~[øÃ\x0000³r½`åÒÒõÁE	ÂÞ½þ5íù\x0003&\x001e8x`pPÖ\x0007EY\x000fÍÌÈXA VÍG:ô»Grß}GI\x0003DË\x0001Â¾ýö©ÁÛ²8=yò-å=(>\x0000Ø\x0007\x0003DÆº\x0013\x0005jTE²C±\x0002\x0006\x0005xÞ)\x001e÷u\x0004ö\x0003§|£\x001a0:A\x001f=ü^§Ã=\x0011\x0010k_\x0019wÇ3²v\x0002\x000cïç8qÈ·u\x000f\x0012\x0010ò¬áyCÀû\x0006\Æ"w×®ÒW~Ë\x001a\x0000\x0017ðñ\x001f~=ß'O%-´¤\x0000nC_c\x0003ÏXµ&ÐzWrìúQGg@S;,jÿüç\x001eüó?ÿ9,¥Ñ#rC9>ôX=c]K{{=O[Ú±¾Này%\x0000ÚË/\x0007À<5\x000fÀz~Cùõ\x0000Ñ\x0003\x000eðY½JürÝ\x000f\x0000ýúë	®£OÚ\x0010 \x0015J}s]{Þ3\x0002væZ-ú\x0004/?Ð\x000f\x0001Zmý\x000c¥îX_£?Ê:räH8Àg¬
K¨xAÄ\x0001\x0001ÏêåÏÏ~AT\x001aP©Ü×^}-tÄ\x000f'ß:rðB{\x0003<_\x0012è|ùÒåÁ7âyá»è?é\x000f¤×\x000f\x0004êóÒÂN\x0019V>\x0016ÞôD/¢cì8òP·\x0000¹![\x0000ä\x0005\x001fze(ë^\x001díN½¼ONç^}	)¬õÛ\x000b¾g92\ß=¿¢¶Ú¾cVN]Ü>;XX¾å6VßÖ/míË{\x001fÞWãxÒâ\x0008§L(\x0017mæ}\x001eîIß_½\x0006Õ\x0000ý¢ºÂsU¥öwÒ
÷Å	W\x001d\x0001\x0008µ¹((\x0015\x0000\x0016àyEßÜÎhÓ÷@e©<£·wf\x0005:Ï
|_O@_(\x001d:gE\x0015ØT\x0000ÙØÈÖ&`81\x0014\x0006¢0Ù kðÄ\x0001:?ÕHOEWõ\x0016Ñº&u6\x001b\x001aHf\x0004¼\x0002<C7\x000f\x000bM,jØöÝÔ\x0003§§OßXÖ !ù¶5n]\x0016Ë*ç©j¶,·\x0006ø¬ÍTÜzã_lëKï¤ÓÊ?äLHô¸#E\x0003@S¥\x0008#Ucå¼5ê\x0001h\x000f{ò°5j\x0000ÉÍ¨\x0007(Cõ
\x0000»\x0013\x0005ºóäb-\x0018é\x001búìÕåï\x001bÝçÿ&)ñüXâ67Ñ)?ÂVºå\x001e \x0011]¤¬¹	Ý0\x0008â×t\\
ó g:.0ÇïÏQò8
þz)qöûÇ"\x001f]L\x0016ë\x001a´3¶£Ûb%G´Î\x0008öK\x0000\x0001øKa\x001d¬¶÷D@¿\x000cðBçÉ\x0007fñ\x000f¦ù?\x00120IÄqßq4\x0007oI5ß%Q¿§N\x0013ý Ó7Úö£îrÄã\x0011sÿ0\x000bªF¦>\x0000\x0003üÓ
ÿÃOê\x0010F\x0013Gö©aÿløF?\x0015ÿÐóP~Þ71È\x0004ðî\x001fGÙ¢?5ý*Êiò¹?ù¹H+ìü1/S4~õía¹ñ \x001b H\x0003ü¿üÛ\x001c[ùÍ-tÖè2ý#ú§~[PÇiÉË\x0000ÒsÑ'ìøQæ\x0017
ü£Àù¦þHù·ôgÒ¦NS?ÈÊ\x000f!ÿ\x0018ñ\x000f\x0013ËVÓ×.nþ¸PËI\x0014~§ý¦Äûr>xluÕôðè^¿4Ìù*?ýúTr\x000e'ØgeþõËk9º~¦mÌó}]=»Gýz´Ô¦£À³ËÚ¹_Ô~B?æÞý¹Þ;\x001dùñ»,\x0013Ô~÷±ÚgÝ¡[ùk¾\x001cx±S)\x000c~2F¥ëÊiù»ñÝ:ð}­\x000bòø%%Á®|\x001eG\x001cîzÁÃ|)\x0017\x0019¼ðbÏ÷¦)\x001f:O½W9º~^)Ûå{\x0018GcÞa>ñk´¿t&Çzú\x0011àrünÌ0ßÕbAÑ|Kúe»ä8\x000c~s»/-Ô·é{ÜssrÚô°¬PÊô¼zÊÅ\x001d:É\x0017¬\x0018\x000båâ¥=½ ßPÌ¼ic\x000cæ
u¬\x0005pè\x0019Ðyû¯\x0002<§Öc\x0018ãYjìÏÄõÀsj¨ÿÛk ×@¯^\x0003½\x0006z
ô\x001aè5ÐkàeÖ×Åíº6ûç\x0002 õ{]kZê\x001c{rºo¶Ormå5ø4á¹ÇÆ§\x00027âØcL\x0006<äØä\x0000\x0005ôÝ¾u[@êÞ8ÆúÌ\x000f\x0003Ìb}dG\x001eþê«K\x0001ê¥õhZ\x001eÐ'*\x0001:q\x0000Å\x001alV--¬q?
½)P£q¬Ýø>íÂ\x0002n~pTV³Gtl3\x0014\x0010².ÊÝ\x0010è\x0016kmöÅ´fýè#Î\x0000Ïÿéã°\x0006ìå{¾\x000f\x001f>£À±T½$ÐðÎûó»p?þ¨Ïy2\x0004¸iwæÃ÷\x0004:¿§º\x0016`úª,%»@V,{ÙR&\x0000¨\x0001Å%Yy_Õ7­¯^åøå\x0002BgTO\x0000Ñ\x0019­-Ñm®©\x0001ïùæî»ïâÞ
`\x0014\x0000\x0017\x0014ðÔkVÖº\x0000½vÕóÝ»wB\x000e@ç?þOñ"\x0000ýÊµöLXâþË¿üË\x0000·¸x5\x0000gÀ~gÊÃêït'ð{ªÔu¹Od}Mùì\x001bûí}é+_(\x0000¶|P\x0000ÞãÇóhhêpíZ\x0002ûÏ¼ÀÖÅO¥¹Æ\x0002ù°ò\x001c\x000e0?-½_}Ü£P\x0013H\x000eïÃ²¾\x0005 f]
¥îywêã¹\x001fë©Ð=Âf\x0000²óH÷ÃÃãµ±´Þ¹\x0013«üAéßù9¬\x0004ÏÍo<={Vuå\x0018éÔ\x00072¦Në»Øoå>~Ó×ÃâYà>\x0000?/\x0003x?~AZÜÉo©=f\x0002p\x0006tþî;¬ÿ\x001fõ8ß\x0002ç8o?\x000f\x00046S\x001eº\x0004xÒ>k¶%{¾8kíJ;>É6O-Í[£D¼|ñé'\x000e>ùôÓh«]»w\x000cvíÞ®~²#\x001d^pÀ\x0019xö¾\x000c\x001a÷åý¡ì§\x001b±?B:öGj\x001cék\x001f í¸Lã¦ÿÓk 4@ß¨®ª¥ÙÈM8÷\x000eë¤\x001bî7éâ>ý\x00137õç\x00004`\x0000léq\x0019\x000e"ì	/³È±\x0016z§\x0004ºM\x0001¸\x0001¾ém9
Æs\x0002gäÐ ¥J\x0014ëe	\x0012²@U\x0001üFgµì4 l®ª\x0010YSoª\x001c\x00154Ø.kÒyª#¶ê#×Þ\x0014à¼!\x00196\x0005\x0008\x00028sÌõt\x0001ãx`\x0015³©~MI=|s»$\x0006\x000bèè'\x0002¾\x001eË\x0001@¯Éòy]éÊ¿¡xî7ågÇ}Sn P:7
\x0013T*\x000c«£ÁVþI=ÀÑFºg\x0000Ö=\x0016Øè\x000b\x001f\x001e~è\x0019\x0010¶rNó<òÐF­¦Dçº\x0008¯4n:Æ
6\x000eâ\x0018´L=HÃ;eÏ£7;lewÃ}oÙ¸wyãâ\x001c_eqÞçQÇãI\·L§6j ÿ(ZLßã5.àK{qyð7µÞ×Ôr\x0012N9Ç\x0006=\x0013¶ß\3HI\x0019PLÝÈï\x000bvð´\x000c	Zýw~(|)Ïü«ß¼]gç³üÔÁü­».5\x000f¨Ëº^¦5òpmÞÖ_eÀOy¾Æù\x001df:.­Ã ¤³³È<®«õhZëF:ÂÍÃm
ðQõ\x0005¯\x0004gÚc¸áÃÕ¥\x0011XþÔøª7ä¤¿ÚUùÉcç2Ì§°\x001eö!Ë\x000få~´]Fyó¢zÃº÷]yê}õß÷æajÞ/ª}\x0013l¶Õ)§í×®éóÊ³N¦ÞW?ñõn\x0017S`\x0003<SË«}ÙýÝÔÏC¥ö×4æg½sÿÒ¡öû¾KÆÔ¼Yä®\x0001<êÓ
\x0000¤É\x0014Y-o:ev\x001d¬[SÅ³\x0007ðÌ\x0002n\x001cðÌ»ÊI9ð"C\x001d\x0013Æ\x001d!g+ÛÉ2té8½Õñ\x0016uC\x0019Õ\x0019\x0012tÎ>\x001eMh@îª\x0017ä«22=yßnFN;úW\x001eãã~\x0002ôyìËÒ8ÓÓüÎÓ	78Þ)¶Ï>@]ý\x0013{¼0ÖÎM9>UPÛ 3ÔÇ%ð¼¦7\x0001Óê9tG~Õ=\x0007ú(?\x000bÇø¼â\x0007 Ú»vîá.(:\x000f´·xFCýÕk ×@¯^\x0003½\x0006z
ô\x001aè5ÐkàeÖ@»WäµóS«Öß®w\x0015:Za-!êRuE®-\x001aÚ,1XûäQÅ\x001b\x0002i\x001a\x0002|\x0000}\x0000wnß\x001dÜ\x0016È¶W\x0000\x001fßO\x0006x>yòT¼dëÏ\x000ba!}ñ"\x0000å%\x0001mß
@\x0000Áýûe­\x000cð,\x0000\x0017à\x0019ÐµÅ\x001e\x0000e\x0002\x0003ì^\\\x001c\ÃºôØ1\x001dê\x0008bÀJî\x0001ï._NPöÒ^µ"kÂÕ\x000fð\x0019«çýû÷
\x0001T\x0000hÀÂ\x0004/	¬»#ëÙo\x0005\x001c+ð§XW±¶\x0002|=sæ]Y­¾#÷®Ê{-dÇZ£¡½VÞ¿Ï1Ë8@Ñ%Õýr\x0000ï_\x000f¼p:m«Ù;cm/\x00000ÖÇPÀl\x001cVÉ¬ï½NfO/t!ð\x0019\x001aí 6\x0000%m\x0002Ï­Å³×º\x0000ÕùË_Â]½z5xÂ\x0017\x0007øå+Ç.\x0003\x0014{Nã½høx¿56i¶ëÅÐ\x001fñÈ\x0008¥=à\x0005O¬vý²\x0002|¶J?åá¨ý¶5¸ëÌ\x0002\x0017ºå\x0002Tæ¥\x0001\x001cÎÔ
],-]o@íüæ1}ìµ×^
yøq\x001eÿ}8¨ë\x000e¨O½Ð+\x000eÙÎÿrpá\x0002ßè¾\x0010eä\x001eÃè7§Ne½æçç}\x001cös6â¥\x0008d¸zuQu|\x0018z7åÐ7\x001d;\x0016²üMntA\x001dâ\x0005\x000bQjmy©G{ÚZ\x001a\x001a¢gëgÞ\x000eý¸/\x0002òÉ'á.]º8ØÃçÄä |?Ü8åÀËm
\x000fóC^ï©à¯mB9ÞÃ"÷ n+Sâû«×@jç¸ºª\x0017ÏUÚßI7Ü\x0017'\iÆ\x0001Ï\x001c\x0019íEÞÔÀÏÄ\x0016Àscñ<©Î?!7)vc·utÄ\x0006ß\x0019
BzqSÛc³µa³\x0002eª\x0012Èc"NtCó>®¼!þ\x0002·7µ\x0011¸Á\x001b,¢+:î`UV(+r\x001bºßÔÆ¢"±Úh,\x0005>\x0003<ëácõÐ­«

®\x001bð\x0016Ý¹[ ¸,³E9^û©âÈ=\x0002ÖU\x0007¬×\x0003ngù\x0001­\x0001cvU|\x001emà\x0019\x001d)jàÄË4Agª¨\x001f\x001eãØïØ\x0006.\x000e7~ë À`Á½ã+õ\x0000\x0003å2µß\x0003©ãM#SùãtÎï(Ò×<N\x0007e@ó}Ê\x001bÿ\x000e3\x000b­eU¿åw·ló\x001f~\\7y;m¥¤EÅP\x0006k;×\x0011J\x0007vhæÉv±¬\x001eè¹·£\x001c·/y¸ºy	c\x0002\x0001p¶ó&>Ô\x0013\x0001D¾Í\x001c\x0013¾ï±Õeh?×§ú)Ïá\x0015jÙ µº\x000e¦µ.Èàº»¿gW>ç7ïªÓêw¼i'Í÷æOy\µ\=/<2ùãúÕú \x001fzÇ!õÙ¥äöQzòÔËíÊ\x000f)ün\x0003ÿ0Ev×±RxY6óu<÷lÖ¥°Ty,ùt)|¬;ëÓz ÎË\x001dGÆÔ|¸7ï\x001agÿ¸xÂ,c×Ï=ãÍÛ4c_Ô_=ÏÃ	6í\x0017Uõ÷¼zY\x0007Á÷¦Ýpß:F}ÕKã~ÎbÑ^nÿJñãê³ï0Ëëô¾·ü¦£Ïvý~ö:_¥Ôûz!çê\x001aÖ·-ð\x001cÙÔaÐêÌË|kyÕoyyæxþxÞj<þZ_óV\x0019×ãAõ{ì&-áÈ<³Î.ËrzLà\x001e¥N\x0003uþ!\x001fo)%'f\x0004Ï© MÙÖQ±-ßÀÆâï9y¾áÈ)ÆGÊÏñtN/,&HÏ7çg\x0015/Ëðrá¤~hÈ©-Àdý>åuÅÉ"¡'ÉÃI%©\x000bõ+ý`ó\x001báY_\x001f\x0011co\x0002Ï²xÖ÷½6$_¼ñß±x\x000e\x001d¨üÔ\x00054ý©
ÿÍ~¢Æ\x0001II/òÔ|
Ð¸Á÷ûo<ª¬¿ë5Ðk ×@¯^\x0003½\x0006z
ô\x001aè5ðòh ]/²\x0016`ÍàëY®{\x0015Âpé\x0010+\x0008ýa}\x0013ÿ!\x0011ØRÂÓ5P\x001eµ
`yõj\x001e\x000cÐyïî½°2Þ§OM\x0002:sÜö[o\x0014`µ2GVÿ\x0010`5\x0016±|\x0018kW`æ[¹P¾'|P£²·o\x0007\Õ\x001aL/ÿªä0y\x0012­O\x0007W\x0005èaÌQÆ\x001cQ|èò	{\x0005`Q ^\x0000Ï\x0002;\x0001
\x00017¯ÉÝ\x0015\x0018ßjN@\x0011KÕ÷u4Ç\x001eS^XªÒìV`téú­Áõ%9ÑG¾µ\x0018k+^H~ï½·\x0007ï¼{jð\x001cf\x001cñ-°\x0010KÕP_³\x0007`çXpÜÒÒõÁ_^\x000c·¸xUzf-VÎÛ¶Í\x0005X\x000cÈ
øgð\x0017jÐ\x0012à²î¯±æ¥\x001d®Éz\x0018um´¬½áÃâ8êë|PÒ~öÙgOeýJ^ÖÓ¾\x0000Fóhl¾³¬cÃzÐ|\x001c7¼Y?{\x000fÀ\x0014À\x001e\x0007ðk×Üs =°Þ~ç·U¯#\x0001\x0003\x0010ã8\x0016<¿|/ÖÓ\x0006Ø9Z\x001a0Ô\x000eRw\x001ceZ&dÆZ¾\x0005Å
>_\x001c¸\x001cø|§½§OWÔ¿öÕðÑ£\x0003Ø¦\x000c\x000fÜ¼Íßû\x0016ìÆ1ò\x0015e7ò\x0002\x0016£GtÃ\x001ayc£}\x0016ç%\x0000ê\x0008Pßò>\x0010 zõóBFò¿©v»\x0017/¦óR:û\x0004{õ\x001c\x00012GÿV\x001fu>¬Þ½\x001f\x0003Ef¿GÔ³Á¾FZÑgÛnnþÊQÛÕQÛW.ÿîÁ}	>ÓÞÇ\x001f\x001fÌÏÏÇË\x0001Ôßmëý\x0019(û\x001f±ïÑìå×=áÞÒÐþuÇí²¸§õ´×\x0000\x001a`ì©®jÅóY¥öwÒ
÷Å	W¸OX<ómç8Þ¹\x0001sâ­ÆâYo1qÔv±ÚSçÈíY}`=¾ùÌ\x0000\x0003xV|ë\x001aa\x000c>GÐàº¬×õÆÜºgÑÞÐÀÃÊï:CõdIl}£V\x0002sX:\x000f-µ9Î1Û8M\x0019\x0002õ0Óª£\x001a¦·Ëòmg\x0003ÏËªg\x001c¯­Yt\x0008<OÎ\x0004\x0018
ðÌ÷­\x0007X>\x000f\x0000|¸ð#¶\x001e`ä\x0000N2¡¨\x001eÐð	ñÒ \x0003PãòÀoZ\x0007\x000f\x000f
ú²¿\x000e\x0010ö{ð`±ß<\¦ùÔ<\x000esZ¨\x0007¥\x001aætæíû¬­úQ39¶ñ­¯ÆÁÛËáÞáÏ\x0003gåáüÏ£æSywýÝû<\x001a#\x0008Ör»eÃÛm\x0007\x000fâíØt'/´^ÖmÍWetZ&\x0010ÎL°P LZ¹1¯çy\x001dÓ2Ãæ¼\ü@E\x0016ýã²<P×\x0005ª'÷.\x0003¼\ÈYëì::´µ\îëåtæe\x000c+çs¸©ÓÃ\x000b¿iå×\x001aå\x0013_åp=¶¢æ\x0007­Ë"¼è\x0006´\x0005?\x0002±êÍúE§Ä¦ûc\x0001¾Ä\x001btæªÛ K)ôðªõåÞq]êô¤Á!/®Êa=\x0007_ðzWW³T¹ª¿+\x0017ùëå{SÇùÞÔáRÎ¸ËáÎk:.í¯\x0017&Y\x0013ìx¹~­²¨Ou¯uOõPý\x000e3­yÇù75¯nè8j¤N\x0002Ìï>_Ç\x0016û÷³Üe\x0019LÝWM	Ç\x000fu_u\¥ÄÛÕrª,ÃÖô\x001b\x0003Ðye5ÁgWü\ÎrL«\x000cÏóÇñø+?\x0007Oû­7ë\x0012j]{l©q5=ü\x0001X)ÏÔe{\x000c\x0018G-#´^ÉÔeq\x001f / òæ\x000fQ.Â¹,³åe|[ÕoG(VÉù>óc¶-2\x0001@çB³±\x000e×\x00029ÏY\x0000<Ço¿	\x0016OzñP¿ÇRæÔ'²DÒ\x0015ã' 3/"R¬¶AÖ=õ2%ðoKçÂ\x00120}Gcñå3 5e¥Ëß~*>î£²ÔBñY÷|6¥²>\x0003Ç\x000fDÒr%%îåzà9ÔÒÿé5Ðk ×@¯^\x0003½\x0006z
ô\x001aè5ð\x0012j ]£³\x0016\x0018ýÍÕq\x0018\x0002¯\x0005eC\x0012-!Ä%\x0012,«¼H?<(#È0= 1\x0000#\x00002\x0001Æ}Ë1Á÷\x0007{\x0005ùà,Ï\x000cNxk\x0008º>zôP`àÒ'`Íº\x0018hÕ'ù>³@69è\x001cGOk]æ%\x0002¼sÿÊ\x0002¤Ü/¿ü2ÑæÏ»\x001bkàÝ:
\x00153­Z_\x000f0òÆëñ]å{ßÞ\x000b\x0000\x0012\x001eìybGY¿\x001båÍ°w¦=N^rÆ:\x001aÐcÃ\x0017+åkr\x0000Ç\¬ªø\x00122<y"(\x0016´X;c©Ë1Ùy¡´AcÅ¬|ãùË/¿\x0005íW¡?t\x0010û\x0003Úå¸g@E\x001c®¶@æ:»Ý[c
Ç\x001a£Î\x0001Ëq\x0006i\x000f^jÎom\x0010Óì#Úçs¾[,\x0007\x0008NXBmqL]X'Ó\x001fpÈ@e\x0004\x000c\x0006\x0006ô$/íÂK\x0005ô\x0007.ç£M°ÚÆ¡'[øVp\x0016}\x0003¶\x001a`\x0007Ø\x000fà\x0019J\x0006½-÷\x0008\x0000öyÉ\x0000J½.^Ì#¿¯	Pú4_F_^^\x0015ÐºG *ß> À¹\x0005²á7ÜëÖ\x001e\x0000e\x001bÈE_õr\x0003²A®G\x0019Ã*àõ>}g\x0019]øÙþ¤Ós\x001fÅ7É\x001fÞ\x0012 >\x0016Îszé=÷\x001fæ¢Oq
\x0000²\x0002RûÅyú)ý\x0008k|tN9ãe5öBØ{#Ì}tÛù\x0008ûÚ\x000eðÿâ/ÂqÜùÞ}»\x0003|Þ+ð\x0019ù\x0000ù±2§Ýk³\x001fÎ)3÷W)Ìö&\x001e\x000e\x001c\x000eu_öW¯Q
4KÌ.ÝþÁhËU©ý\x0019\x00156Ü\x0017oÒÇ}ú'nþÏØ\x000cà\x0019ËØÔSÇm(oT­bí¬
ðÌv¬ºp\x0003°Ê·g\x001b7£·fåf4hLèxÄ\x0000©5\x0019rIøMT§ßZP\x0000\x0000@\x0000IDAT>Â\x0014¾&kçU
D¸5\x0001ÏëÚ\x0014fãpMJM\x0000á4`å,8XòÉJFÙÙfÃ\x0007Oq	<ëÁWIëJ\x0013ßjVÜÔ¶íÉm²ÆãHmAØaí¼¬4\x001c½½.°\x0019Ê1Û\x001bÇ
oCOÈ\x000fxL\x001dxHS?èE2Hî øI<¡TªB\x0019\x001cg5ÉÌÉ¡î\x0003¢ÒGuNG\x0007:@x`¯aucxä5Oó3­ùHã´QGÕÍYüÕ·+K}¨\x001bï²jx
£\.ËXi
§L\x000fP.ËÑõGdùã2\x001cäû­)òPïl\x000fcj>¦\x000e¯òÙïö¨õ²~­WøX\x0016ó2ðC\x0003Ç$êÍ{(\x00131?\x0002üC 6æégÚ çG*ÿ¸
YLñ[&óó\x0004é	I\x000b?ñP×Å|ºu¡\x001e¹>§üZ/;­iÕûiåm~'a\É;åàúF»PÿÆ?\x000ckâGÒq£«ò\x001eç'¬ê\x001fþ±¬Ö©ug=tN_ë\õ H\x001eO[Û\x0001~\ä«:¯ï-/´ú\x001dï¼Ö­©ÃC_*Ãòç¯qµ<òY\x001a^ýN\x0003åWåg:mdÒ\x001fóô}¥\x001bÇ£¦ûuý\x001aÏ\x0013lm¿.ÿ\x001bõò3é:ºÎP;rtý\x000ek¹=ß\x0017G\x0007­3\x001fë\x0005\x0018õ\x0019Àï~o¿ãËÎ2TZû¦ÃÝ/MÝ?M	¯qä#Î\x0017÷ü\x000e`j9ÆÉE\x0018ÏØÊêS¯-ð\x000c\x001fë³ÊN¸e´,PËÃ³]ýÜ;\x001dá\o­Ê7NÕôðá¾ò«ü)wF\x000bud\x0000Èµ¾ \x0019æ¸VfË\x0008Ð¡ø»LËäñ¬ÊCXuä÷eýY^òårQ¾\x001doÏáô{)Ü,O½È¨ßz:ÓFÔx¨
\x000f·Çóä¥¼ËsNoÛ,ïëË÷¬ð=*-d\x0001Y ÆwE³¬¦\x000f¨»µegm¹Ï«íó\x00122ÜNDÉÔ<H´¹)¦=ð*ìÿö\x001aè5Ðk ×@¯^\x0003½\x0006z
ô\x001ax)50º\x0016ð\x001a¡Kµ"Úe¸üZ6ÄÊ!\x000f±Îó\x001aBK¿æ>)\x00193Nk~þiq\x0001ð\x001cVÇ²<\x0006l¼ÿAhËûöí%1Àó\x0007ñm_[µ\x0002.-]o@Òo'À¨]Zw¾"`ð\x0015­-u:èÆ²ö\x0002Ø\x001c5Á¢õÜ¹s:úø|yZåÖZ\x000e\x0013p\x0013å¨\x0006ä4¸
HzâÄæ;»'ÃÂ\x0013°µ\x0018kW<¶\x0003Ì\x0005HÅÁÃ\x0017û·í·¥\x0017â»¸\x0000v8¬h¹Ü\x0006ù²q|ëùÂ\x0005\x001dÝ|þBè/OÀÊ8òq\x00145\x000eù\x0017\x0016\x0016ÎëdÚ!×Þ¹×Çz÷úõëÒëR¸ªkêäo\x0010\x0003²\x0007N }](Áè#¤\x0001\x0001mó;ÃßÅ/º`ï\x0017}P&µ³{Ò^Ô7~^\x001fê	~^ÏC©\x000bGã\x00008m\x000cE\x000eËÏ=eP?ö©ÿüü|Pë\x0015\x001d!\x0017òx}Ï\x000b\x0001µ½¨\x0013/&$ Î\x001e÷ª\x0000è5µË.¸{d9\x000c8<àÃEyvÜÙ\x0017\x000f	Ý×ç>ÁÅÄûB´!å²÷ò3^¹WÃ©jì	øE	\x0000s/ç%\x000b(:Éâ×\x0007·ôrrÚ\x0010@Ùº#\x001f\x00009uÆÌn\x0017^®÷\x0008Ðè\x0018G»´\x0000õî¨\x001bO:õÄ\x001a\x001eÝà\x0000Î\x0003x\x0016ø¼Ogã¿q\x0000Ý´\x0001ý×{\x0019YÇü3å²§5\x001deØQ°Û4»½\x001a¡zÒk Ñ\x0000Ï`uU19oyþJê°Nºá¾8áÌqN71hgujÝ´(ÉNÎ\x0018`kb[\x0014ko7´dÓ\x0010ËËi¾û,\x0010\x0001TtZop\x001cb\x0008²ô\x0000¸"
¸\x0007J»®£¶×VpÚ\x0014À½¡\x0007gS\x000f\x0011G\x001eBÃió\x001bKg}â/äKð\x0019\x0000XxÄQÛÚÈÄ\x0006à\x0019kç\x0000\x00190\x0005<OÍ\x0001<o\x001f¬KV@æ5YB±æ¨íüÆssä¶î7äâ<\x0011Ñ8Ö1\x0000ImXºLè´Ê\x0006pVø4zCµú£\x001a\x000b¯ÖÀ.4¡Øâ\x0019]fcBC)»¼Ð½ý-u¾\x001c@\x0008÷`Rým\x0018S\x000eP×&þê&'KÒ²ñåy0óÆ ]7m×\x0014u0Ãï¸ðèÃ\x001cN\x0019õ²Ùï4¾w\x0019G¿ÃÇQóuïM	OñºmRÛ#ýÖ§e\x0002o´\x0016Ä'ÿ¶-ÐoN
ô\x0010ÚSwøh\x000fO?\x000f<ë\x000f@g¹Æâ2\x0013pmÁÚÞ\x0011ß<'çdêÉ\x0012p µ¼õDË3}%%DÆÖ\x000eÐ ëDÁO+Oztë0×þUõáû\x001c{HO[ö ÕWË\x000b`BW*4úÛ'3\x000faõ>nÊÑþÐMxÛÆùcI\x001f\x000c­®Ú\x001f(´#q¤1øìú:Á\x000fÒÂ\x0003s;Y^Ò#\x0003/»0\x001eá·C|ü¾ì¯t_y«ßi\\x000e<ì75ßî=áÎoÚ
s¸iÇÏe¾¦\x0019:>4ÓÖ8ó3u\x0017C¾:T_L)p¥\x000bS§î3É£¢^!ý¸]Ò\x001fÔþÑð\x0010gto]ùY2ðÌ¸g4~\x0016L\x001drå3\x0016åê\x000fm£ßÕ¾·Õ}
¯yÍÃaðÇ?y\<SÑô®W¼äÆç;Æ\ðæ²Ì.ßòù\x0007<´ë¯i³¼£+O\x001d7ÏñPëðzÁ{+l\x0006-S+o»\x0000Ëqöç¢ì\x000fÃ²yLò½ã[ª1O2FGdËq~ÉË\x0000ôWæ&~ß1§¸ôÃ¸ù±rfVßÅn¬\x0013xæ÷^¨Ó9aõì¾íßZQ{NËq8Û¡ö¿»\x0008Ï±·±x\x0016ð¼¬§\x0002yy!çíA[g÷åQÚ¶Mê/ûcûl9^E*#y	I"NÀ³F5©!""¨ÿÓk ×@¯^\x0003½\x0006z
ô\x001aè5Ðk ×ÀË¤\x0001ÿþo×Â¬9¸LGÖ\x0000üþçRòÈ\x0001ÕZ)Ds-a\x0004×¸LyùÆóW_]\x000c«cÀ8,N\x0013Pü!¾Ñ|ZGX¿úý8¾\x0017@3Å»wîÊ¢8­\x000fËc\x001cVÏXx\x0002²A§´\x0001¿¾!ÐYncÓ«½ÆÍ\x0000Í\x0016\x0017ó;¾^w²ÿÅQÎ\x001c{\x000c\x0000\x0007à\x000bØÍñÈßÿÀ<}õØ\x001boüF\x0016¸7Ã£gµ\x000e¯\x001f~Èï\x0005ÿø#ÀèÍ\x0006Ôý&¾ÕúaohÐ|§7ÁºC\x000e\x0006Hõ+Ö²u\x000fã\x0005\x00070|MÇ\x0003~óÍõ°¤5ø¼{÷®!ü´¯\x0003\x0006zMÌzub\x0018Â©¾ÇÎN\x0001`\x001f>Ì\x0000\x0000h\x0013ð<9X8~\{·ì#\x0013L\x0007\x0008òËWTÇë\x001ftTöj\x001fÌ\x0006À'ï6xí9d?É½Èýñ
n}Yt¿\x0000Z[@æ@õ86Z\x0016ã«2dÂ	\x0007nëí£GÆ\x000b\x0001¼\x0014Àç¦îHî²ÄÅ\x001aò£ÏJ¹\x000bú*ê«¯
öÉò\x0017Ëv@Õ9\x0019\x001fæÿ¹÷Ì\x001f>è\x0016w]Öå\x00182¦[Ó\x000bÞÛ\x0007»\x0005>ïÙ½Ska2ê\x0007á´\x000fjÐ\x0019J½\x000e5/\x0000ì×K\x0014è2·É]e2:ãezÉ"û\x0003{U­Ñ\x000e}(÷\x001dr\x0015Ðø¸ôÏË\x000eÇhÚ=®õ8^;å½¦v¼\x0015|ÜÇ%ËNldöþîðY\x0007 üèQúý\x0011õ\x0003\x0002©ó[àÐV¾x\x000e(kqq1\x0000ï]»·«¯Êº[þFÛÀg°^ÞÂ¯îÓPWÚ\x000cg¹¡\u_0öq\x001cWù÷þÿß5@©®êÃ{UÚßI÷KçüÆsvXýmvÉl\x0000´\x0004èÊá_Sj´
«`¥\x0006fðÄ
\x001aÊ@¬\x0019C.\x0005bÒ4¥ºä ­§"Ò°ï»¶Æf°øò\x001dçMÝð}	"å²=|é`+¿xs¿\x001eò\x0008tV\x001e¥Îo<K\x001e¾ñ<Åó\x001cVÏÛ\x00072?Ó[58YÒ¬ê;Î|÷\x0019·&Ð¢{3¾ñ,ùE=\x0002<c} sÒ\x0019&\x001c¥Ç±KmÑ\x001dõßl¡\x0003Ñ|î¨i\x0018ÓgýäzóÝó(ÅD©¢.»\x001dxòJ\x000e@lÌ21äFxÊ]Ç\x0004\x0012¥71ÍéQÙë e¿)¶òg)ù\x0017Þ\ZÞ\x001a\x001e?ãø\x000b«y¶ò»\Çç}¶	<q®{\x0002¡Òj£còøÇ\x0016é\x0018¸íR¶m]'Óv£ßmR\x0007ý,	$öh-ýÆ\x0015ÇÄt5ñys^ÏÜG&~ËR7ãUÚH¿s\x001d3m\x000b\x0004ääÅÄo0\x001a@\x0014WåD7	¶0µ@­è\x00004*\x0008M½p-Ðñ¬n³îÙ\x000eÙ79u\x001dGäÏ¸\x0016Ì¢ïv¯lÔ³ã\x001cæû­hÊ±ö£+òC©·\x001de·?@[0â\x000c<{ÂóÔ\x001f\x000b¤wÛQ²Ënå¶\x001f9ßiº<j\x0019N\x0003%oWOÁ/3Ô¤cËpZ¾ý]êrL\x0017ê0Ó\x001a7ÎoÞs>S¿\x0018Ju¿5}1%I1üç\x001e\x0016\x0010%æ\x0000}%b\x0014Ú\x0015¼C'Ïs.g\x0015kç\x0006x~n/EÓ\x0016n\x000fú:Îýß÷¦¤ëúk~ó«´¶i}.ýüøYêRòez~ð<\x0003ê¶ÏË5E®*å\x001cGÎyM)ÏÏ9Ô2\x0011ßa5<e,í[täqÇ´+K§Î-Ã8Ùè\x001cMiÆvì²LUnü\x0019\x001a2JwÑ\x0016ÒkÈ¡ßF\x001br^`N\x000eéô	i#°ã(ìF\x0017qß}¤µü\x0001@3¿\x0001DÇâ\§Gè}Àéiwê¤nÓÉuÈß8®;ßäo\x001aúR.p\x0005<«oç	#\x001ciö4êÅ[é,¡ÉCâë÷\x001cú\x001aÞ[y0«}¦âéN¸<¡\x0002\x0002Â\x001bB\x001fú¨4ºoîHÒ_½\x0006z
ô\x001aè5Ðk ×@¯^\x0003½\x0006z
¼L\x001ahûw×Ô"Ö\x0003ñ{ßý¾ð+\x001fÿÃµëö¸7~nc-¦ý?¾Ûå.¥PÀ¿\x0000\x0013\x0005(ò­f¬[O¿w:6Ö:O\x0015¿ÓñÃ\x000f\x001e`¡1Àïü|\x001e©Ì¿Ð	½ø»±ÙÎ§îÞ½\x00130ÖÃ|;Ú2³.Ä2ö@Q( §`F>ïS²þ\x0005dÃÊ\x0013\x00070k­ÔK{ÜñJ\x001c]\x001dÀ®\x0000M¬Í\x0003}\x0000Ò\x0001Øá\x0000ÿ\x0000q¼Lì53\x00149lm<·oßc¼ïè»ØOè\x0004,\x0001°\x001c\x0007dm
¨ü\x0000¶_9<xåð+Ãu,û³\\x001cõÍg\x000395ë>ß\x001d¾¯ï\x000e\x000bdçèñï\x0004²\x0003ôÏ	¸üôû¦OÆµÊúÒõ¥°6æeÇúÖ°Ûo\x0008<kïwZFm^.¢_[ÓîÞ¥ceËý\x001e9ô÷ðá£\x0000c\x001fR\x001f\x0003êè#£ï\x0008cÍ\x001eúÐ	pP^\x000cðñà´Qö3^úÈofK\x000fèrÐ\x000fnNýz{o \x000c§¢­¨_Ý\x0017ø\x00008 \x0002ÀE°§VÃú¬ÚòñB@\x0018UI_\x0001<«
B÷j×\x0003û\x000f\x000c¶\x000bÏÙ¦Sl¡Xh-ká¯¿ù:,ü}L:{\x0016îCì?SxV´ïÌo¾9?oú9ý/÷`Ö%ï\x0000Èá.Ð1|L[ôMç|¦±°f¿\x0017ÊñÚ¼ø6GsÓÿ|Ü¶uD¿¥ÿZ7µ}»öøõ-õm¢XMÛÊ\x001byÛ|\x001b¹/\x0002ÖÖ\x0000ÏÈî=*«Û¼\x000e§\x001e¸V\x001f9¦Deú?½\x0006B\x0003ôêªZ²ß\x000f\x0007¡gæ2§Uº½-ß\x0013¯ý´<j\x001b\x0010W\x001dROQn\x0011\x0012ç\x0002\x0000bñË"\x0013àY@Ôj\x0000]0@<Å\x0001\x0002k@äG9:yäW8³P\x0000Ïzà¡ñàé*Í\x0004ÛØàzÌ\x00163þ\x0007E4¾é,Z­\x0011¶ÀMø
<\x0007§\x001e|ËÞÐC9!\x0019Ð\x0019:¥ï<OíÜ5Þ©ã\x000e\x0014\x0006ð¼¢:\x0007\x0000-º\x0016~É!ºY\x001c@s<¬
«G|ó\x0006Ð&\x0019M6PÔèjHOl.«?"²1= (Y\x000c\x0000¾\x0017+ô¨JUEBa\x001eHZÐ¸Æ3Øfù\x000c>aíÕ\x001c\x001dAË¹|6gÙ46¯h#\x0015\x0004µlÐ­®\x001aWý¤÷½ë@ØÐO\x0019åÞåÖ4Ã´
4/SÒÙß¥ÄýÜeÞä5 ¬\x0007ú´e²Þë\x0004`æOýdzê\x0013ó#KÇ\x0016-Ha\x0019Çäá\x001fEPOP¿mà³´7\x0002ó[ô=y:\x001fò³ÊÒùÓÈ/ûë@Ù~ã\x000c°	\x0000{Â]?(:aÂ3¸À&	\x000eä¤ë¸Zî¦Çu¯¯ZVëgìhÛ´îïÈóK¯ZN7e\x00197}³!#ÒQ¦ËEUßÖ'}(u?HÈç2Ç?\x0016B.ú 
wßÖ<]ÿPNy\/ËJ\õ×´ÕoyÞÔü¶¦³ßÔiÆÑÆ~S5._-¿úÇ¥­ü\x001cï<¦\x000e14\x001e.±6}1¥T®<\x000bå²ó§}T\x0014\x0018ë³ÿÒ÷ÐKÐÇ\x0019ËpâpôMÆ5Ïôoë²KËm\x0000u¿òV?av5\x000f~Ë7~ßC«üøq9îµÏa÷¾æCO\x001aU>²fyÁ2ý\x001cuzËkZu\x001f9\x0018Çí,+á8tl¿ë\x0002­üÐ[\x001dG\x0012Më`ÇAqU®®,ÜçÕþ&@/ùr\x0011ò´/\x001ceÛç½ç\x0000Ë\x000e%\x001fz¤\x0013Rf\x0003ù«bá¨·¹Yûe$øæ\x001c\x0003mõ²¦¹&y¥YßÆ\x0002ZóËÜ¬¾\x0001-7\x000bú\.·kÕÃ¢õ'uI&üù,¤\x000ciñìo­¬<z%ð\x000cø¬rø¡Yx´<\x0010áÍ>JÙQBÐì»Q/þè"Ê÷êqOXõ\x001aè5Ðk ×@¯^\x0003½\x0006z
ô\x001aè5ð²j ×\x00015H^^pï°É¥\x0003ëvÍËzÂNË®ð:×\x0019¬/µþc
	ÀyîÜùp\x001cÙ\x000c/Õ.\x000b(<\x0014ßó}ïÝ÷\x0006ÇO\x001c\x001fæ§,>1ô£éþI\x0016Ó¬ã\x0000ÓÒòh
\x0016åQ¦ö\x0000t¦èÆæªBÖÖ{S\x0001 ùhå~ú)äA&ä\x0004Ã\x0001v²î"\x001e@\x0013pËu\x0001ÌL§ïI\x000b¬kcäTJþ\x0004¸\x0008HÃ¢;
sòÅh¬}í\x0000ër¯\x0014RlÒ%kS(Ö¹î[\x0019~û7¿ÿû½ä2@û4^@FnwÆrz(ßËÆkÈÜ'¥\x000eÞK M°æ\x0006TÄQW¬ÑùÆ0å§~_\x001d\x001c\x0011\x001a'ªÆ>Äd¤½{÷,°ïF\x001dÑÏ2ÙzI \x0002ÏèÝëPö)l\x0004­kWÚ\x0012\x001ev)GÊnÒ"÷h\x0000£¹\x001f{\x0012\x0000ñà\x0000ÆÕ/Ø[v[\x001aÈFY|»X/i³\x0017/\x0000\x0018|¦ßj@ûJ?ªÞ\x001cNÿ@\x001fèöF°,½°ÿe;mºJw\x0003Ï¼LÀ\x0005¼D±C óí;åv\x000cxYoc¥µ}õ?E;æ3ÏY»\x000f0\x0011\x0000þ\x001d{#^\x0000°ìÔ¶£\x001dpÈË>wö\x001d,²ëþE\x0004è~þi',±±PÎoAË*\§\x00058\x001cÚî£¬E¿@/è\x0017\x0013ffù\ÊãHo[¯Ã»îÉÄÞtFâBn\x001c¼³¹\x000fç½\x001a?cu_0Ç\x0007þO¯¡\x0006\x0018k«\x001bFÈãy«Rû;é\x0007<ßo<«£j7\x0016\x000bbÊÓÐ\x0010\x0003°iÈ÷±l^[7 ª
KuÜ´&µ¶ÐbQ°12"#\x0002)>6+s"(\x0006[y4\k"u²\x001c\x001f\x0013âNàrr¨`àÆ¯2ÄÎ[uðÆ¶\x0007I\x0003ñ¦6;õä\x000e6õPN4ÖÎ\x0013¼)\x0004è¼kÏ`Fo\x0006MhàÂÒyEàóªê
ø\x000cð[3ðüíqÛ	ÎW«gÛÆÚyFâ¸x ßæ\x0017Csy\x0000¨\x0014¿Ó£\x001eP³ß´\x000e(ø\x001d\x001e]'t\x0007(¨Ë¾òp~Êªé¸ç"¾^¤é^ãÂºùÈã°q0Ö<MkXõ×xÂî"=mæ\x0018]0qW]Ó9-y]^Mo¹¡5ýÎ_Ó1¹TàÙ\x001aÉÆ?2À¸÷\x0004\x0004/O<µñsY>×ÁpËá|.Ó÷w\x001eôbÇ\x001c¥^Õå\x000f³fl0³Z'Ï£$­õ¨mTÙY5ìoõ»\(ü)\x001bÇUuo]ÎòY7UÇ¼­+ò¹\x000c×Å\x0014\x001eÕï¼nå¯åW\x001fùÍÃéHãtÕïxh7OÃïüÝðçÝÿ-<ÇÕãyeýûã<\x0016þû9ý{sn¥[ëÏý\x0012jÇóm¿)éñ'õÙ\ÔuËp?¨ÔÏEz,í×¼¿ÛÎÔòui­Cõ;]­\x000fºå^]Y/Ç1¾§£Ü®\ãä­²Öv§y[^!\x0017¨«U®®¼Î\x0003E\x001eÇøÑu^@{\x001c¶¼Ö!´òÃOÙ¦\x0003Às\x000b#Wu¦ý½À=Wç1\x000e¶/â \x0007²y^ÂO]ü\x0010º`~\x0003tæ-öxó^k6\x0001øñä'ú²M^3\x0002
>ëmo]µnÈãÆ\x0008÷\x000b\x001444¿\x0017­\x0013åR\üò!åÉòX\x0016å,ª¡Ñ\x0006\x001aæ\x0016^ô¡z¥<\x001e7ZF§³\x001c£\x0014Fí/Z§íi¯^\x0003½\x0006z
ô\x001aè5Ðk ×@¯^\x0003/\x0006¼\x001fûE<û³{G\x000e²6áO¬QzÍF°×\x0014­<\x001c\x0019ýX@.ßw¾/\x0000ëÒÅKú>í¥øV1ë¢\·Lµè)\x001d}êÔÛùùùõ.k °(Öúõ\x001bÖÉ>¾\x0019P7O©Ò^gY¥\x0015\x0012¤2\x0006c]\x001a{Óaû\x0013\x0000«dÁb¤xud\x0005+¹O`WiTnÈ×`\x0001a¹+ÀnO\x001cë­ýøxé=yøÅe(\x0000êwß=
Ëi@F\x0003Ï§Cë_\x001dÍ\x001ei»nfM* =S­+ýÒ3õ\x0006\x0005¤ü\x0018À9Z\x0003öð§ëÀ\x0010?\x0014ùYÓCëZ\x000f½ÛR\x0019Ýü)\x0003y\x000c\x0003h{\x000f%-@'À/uôËêPÖÓÞó¥¼$_®\x0013$÷	G>;x\x0006è/ \x0018Ka[¡\x0003¶ýk3_ä\x0000\x0008EfêC»¦Êár ¬Ó½g@yÈe.ÍòcéÜ, ©\x000bÎ²"c\x0002Ï?\x0005O×
\x0019\x0017ÇK\x0000Ûfóí9Q¬É\x001fJg\x001c³ÕÿãÇYÏ'²\x0018Ï\x001d\x0005Jd'÷0¡¬ï_å:`6\x0014à9ÝFè\x0008Kñl\x0007äÈý\x0017\x0000açÜçÜ?R÷üÖsZ6ûÄ4(áÙvyzõIyèú~ÿ}NÀnS£¹?£w÷\x0007ú÷W ô\x0005ë6ò3þ)0(Û\x0004êphõ\x001a\x0018Õ@LF
2­±ñ\x0004+ Rû;é~	ðlgÞR\x000eKgU§ÑÃ.ÁfM?ê¬ÎiÑ«ÍlÝÓ'd\x000cµL<\x00042%?\x000fçv\x0010`Ó-Ag,Y_|ÈA5¦à)¿Ágôq
\x00173ýo6\x001cuËcÅ´¸	H®eB\x000f¤fÁ¤Þ\x0014È<ÉQ\x001b;v
¦\x0004:\x0003@\x000f\x0014ÆÑÚ|ç\x0019\x0000z].@çð#?à³Jüa\x0005.Ê¿¡µ5áÈ(A<\x0001û\x000bÙÑGèG\x0014¿'.UÒ\x0018\x0000G\x001dç¼ÜÛ_)~\x0007\x0017Ç9?\x0003\x0007(\x000fHëæs^h\x001d ð\x0013æxò?ïªÚÏå®+Þ¾j9Î[ù®Þoå7¿nú\x001aß:2\x0019n¥ÇÎ<,k7eBïä\x0012æú8ï÷\x001e¨4@ÜäÄü#Ä\x0013\x0010¼ÍßÔm])e?ÏQ\x001fËl,#uÃ_uSë¿\x001b\x0007?ç¯Ôe¸¼*S
³\x001fZ¯Êpî}ÙoÚw:Ó*Ë¸0â»¼¸w\x0018úµþÍ\x000b>øád\x0010fçôP.§þÜå2j:uiM³ßõ Þòó¸¾:ÎùÆQ§!y:\x000eúÛ{·\x001fÍvíº¯®Ý½wï}ìà8\x0016 Å\x0002¿-N\x0000ßòW\x0019p\x0012\x0004yÉÿ¥Ä\x000f\x0016 YAâ£\x000b\x0002H:çìî®êÊøÍÁ±8¿U_õµªº«DVñ¼LNNÎÅu!Ç"W×!éÇÒ·/³ç½«\x001d½üýÓ÷BïOòJêí'Üû[¿\x001e¤ï&­óR7§ÕôîóØ:×N	\x001fóp÷®cÚ¼®\x0003áèF\x001b\x0012Þ½]ðÆ\x001f³\x001b²q\x000c<
t\x001eàó¾
9\x0017{zÊ"\x001f×ëízíÓ\x0013§\x001các.²¡øØ0aôN{zLÇÔºC»í\x0012&Ï¶ô5g*\Ú\x0019YÐ[z\x0017
±et¢#×½\ûHÓñxÐöf»ÇÕÛØz£û­îuÞÎZí\x0017ó¥&	Ø¾ë\x0005÷:=Ë½¸<«ÕÎYñãÜiìë´ÞoÝJçiTÏ­okÐh\x0000Ü\x0003:o3\x0006'\x0003¾ò?e»7ë>Ûayý\x0017Ù²ìæ\x001eyNë\6tmÇ³ïrË\x0002Ë\x0002Ë\x0002Ë\x0002Ë\x0002Ë\x0002Ë\x0002Ë\x0002Ë\x0002Ë\x0002OÕ\x0002\x001e'2îé1DÍsï3ê!\x0004c\x0008\x001d\x0018?0¦©qËHcg2Ón
\x001cû¶eþ«ßh«hm\x0017Í7tñl\x0013\x000cà\x0015À¢ÿò_þõ]Û?ú£ÿ¢ÆÀß\x0001l\x000b¼\x0015ÈÌØí'¶lÛLÙw\x0001.\x0005¸i$®1Àì3\x0000m¨ÊK\x0006´\¸\x0001Çj|¥UÅÌ[za\x0001p\x0002áhÏÛÁÇ¸ÓÛSKê}ÅXOó|·\x0017ï_cS©Ø^TYí\x000bp
gÔcYÏ\x0016à§9EÆ¥±%v÷¼©Æªçt{ÃNd*ïïL\x0003 g5+ ¢_f~9WÒmÌ¿B]o^ÎãfÚò±Gâ×~ÐçI75$¶£\x001c>\x0000l^ä®N0~2_\x0000EßÌ\x000f#»ëL<cnø²\x0012±nÆªÐè\x0000E§×õE}]èÏØ\x001fþ\x0001½©\x001fçóOgÍê©§ëH]ñ±\x0019º¾\x0012h^/<\x0008«9\x0017~C_«Ø¥+«Ã-ãwZ-þêñø:þ§ý¬DþI/\x0015Ð×\x0019·ç\x001bÕlAÏêú\x0017/vÔ\Q-RÀ/ÉË\x000ei/«Âkûo\x001dS(}µ°"æ\x0014\x0006 ·­ôWêªóú}õAìü{½ôPu\x0015èÌÎº§u¾ä\x0005x-}c\x0007ÍqbKäYæÄg(4(4ø¡Ø;ù¹~\x00056\x000bpé~ËP 7µN\x0013Þñ}\x0008xþO»\x0015ÏÙºão\x0017¨^^êÍ!up(Ý{\x001f­¤½ªWo%)±&\x000eu¢Ñ±õoWÔ\x0013r\x0005>«1øæa²­à[\x0004Ú>¢þB±\x0000Î\x0000Ð\x0000Òb\x0012Õ¸N2\x0001xN*«[!W²3MXéær¦½g¶Ø\x0006\x0016=\x0013è|ö#+8¹ÒM¬¾ë,z­\x000bØ5\x0017j]Ì\x0000¯Yñ¬»a\x0001ÏÑ\x0006\x0001ó_ú¨Æ3Ú=ôB?{é(^ÛI:=|²ç¤wûm\x0007äÆq1¸Ë§SäàRpn\x000eÐ½«\x001byÙÍ\x0017"Êá¢W.L)G:\x0017§øðFÿð}
\x000e]FÚµ§áéezøX>iÊ\x0003\x001f\x001e;Ä÷òÉ=b¯ðvÛ\x0007Ý¹\x0001s£"ÞùbK(ùÜXâóà\x0001í7znbÄ¹ñà÷uå8#²<@@;\x001fá´'mîzõ\x0002Òó0iwì\x001dôÞ&Â¸Ððöº{|âq½\\x001b\x001eè1\x001eÊ'}O#»Ë í®x¯7²ÂßmJZò±\x0005vÃ\x0016>
õÄþäq,ñØ8é¡©g¯[Ò¡¸ä;vø\x001b\x000eS­kÏCÆ19ðì}d¿MøìcyÈ
oè]i=}\x001fN<u`ÃwîßjÁÃWuG
´7.m\x000fÅ\x0006ô¹~Màº@<4axãyà¦?ò¦g®\x000b9¿\x0013?F9~ðx|×3úB{:áè\x001a½Ñð¤ºº\x000e]m Ñçðæ¬è\x0018ÛD\x001f®©¹Æ|Ê¥îN{=ÝãÃ\x0013\x001a] ¸Ðè'6=¢Gt~ûcn~î\x0005L(ÌcG½]®çÌcÒà\x00104¾PëkÊM
®<xÒ\x0000Q(&\x0011ðL\x0000ð6{vÍáþÆàÞ\x0003}Ýãt¬.§«»­·°EN\x0005ÌT¦*sq½ßýÛ÷COäíw%îµ\x0000ç\x00005ñ\x000e9µieÆÞqøð~ôýqJÜ46:´!e[\x0016X\x0016X\x0016X\x0016X\x0016X\x0016X\x0016X\x0016X\x0016X\x0016x*\x0016`NêPW?ïèñðaî\x0018·hðñ
cMÍ<Îa*£Ç	ó­ã?û\x000fvògög'ÿñ/ÿòäÿ\x001bßjfËa¾\x000fûÏÿù\x001fÔöÄøxò/ô=_¶\x0016f«gtúX\x0013êel\x001c0\x0017\x0019\x0013\x0001>{l¤ùîsæFñÒ¥5 z1ÇÏ
iÀe]ÊyÒsð\x0005äfA·1ÖÜ"sdÛÇBéùK-|ó|äe­¦füÆ.Ye\x000b¯ÀV\x001aß½Ð\x0016ÝÖßs¢\x0000Ì\x0000Ë\x0000Û\x001eS¾\x0014XéUÞÌ³\x0002&º1¼ô>·-fÜÌ×s K|?O×U\x000fÓ\x0006ä\x0006Åe|ÜÇÓáÙÑ3VÏx{©Ý\x0017\x0017ÛCû0¼È·Í<æ//X\x0003êR6²:\x001f:§¯@Ó\x000ehìÂñ¥®®{ô"#7öÆEfdÀGZõ7ú<ñ´\x0017
/v"½\x0016GJg¨É;õ÷Ëõ2»ú\x0008åÎ´°ä\x0008wª8`°ÒYLÉ\x000b
È$\x000cYvøå\x0008ô`õ¶Î\x0015uI¨\x0000¡ê#´!¶¸~ï9ý\x0002+ÕK	\x0002¢=ÿKñ±ý6/TÐ7qÌCP[ÕE\x001fÕùBk'>Àç:\x000fç\x000e§Á\x0005Rnç¨ä=¤;úàºÝH'Ïí÷\x0003Ç¼\x001c{ò[\x0016°\x0005¸\x001etßí\x001b[§	ïø>\x0005xfÅ3+w¹P\½ó¤´z±n\x001c¯ä½ú\x0004pW·Ô\x0002yYíüï\x00027>à¥Ó\x0017¥~(ã\x0014«»¦b~SªN\x000ex½^XmÔ\x0005Ea¸í0á×W<ë\x000cáL×\x0006¯\x000bù¨m"K\x001fñ¿?Õêì3MXë$/Ï*g\x0000çÍÿtrª0+¯\x0001\x0001åù.4Àó{\x0001Ð7¢\x0001ëÃ\x0001\x0018M¡~)PzX'µ4éS\x0017®äÓnÙ³¾-ê\x0013Iå9ù	\x001f\x001e0.\x0002ÝçÂ4ÄúB­9IUò¸\x0010ãëbMÂ(ÞÈºlý\x0016O¿(Uæø7$äÅw¾{}IÛS·a¦îãÉ¬Ð¤Cï*s,¯óöð]¼Óv~\x0008RmÛq
\x0013ÙÞ\x00134à8ó@ãoGð@1Á_Ò³}\x00077½iKÎ½«çæ\x0007Üs\x000eØÌÍ:\x001e]| yÐáa\x0007 Û\x000fiÈãÜÏÔ\x0017\x0016Êê_7`\x001e²|\x0003g[\x001ann½®ÔÍÔ\x000b¤÷í¾ãdj¤¹]ç´i\x000f¨#öÙÓ~\x001cR&uíyÉO^\x000f÷z	ã:M²9ÖÅ4øÈ·Ý}/õ÷ó\x0010ÇS.\x001e¹ÝÎáÜè\x0010þÐ®GÂ¡ÇÚÚÓ:_tÝ×\x0013\x001e(<ó×,Ò£O§<Â8â9fNñoôú\x0010M\x001e%z8röi{]Â÷pÔ6\x0019]H:¦¦-{¡Ý¶	÷6\x001b`}3}
êÁ\x000co¦&<ûeú\x001cë\x0001ßZ¢or½J_¦\x001f\x0010ÆsMèqÒ8\x0016Çú

?Ôq\x0003=º÷ú¢s|ÏëmïõF¿Pô¯{°®Ïçz«ôð~<Ïñèß\x000fVêE¿\û50é¶¯mNØ(¾ëÃµ;×Ôä'>uµ=Ñ#}ú÷öJ¼øy¬çvß{ýàÑQ\x0019Íôý\x000c\x001dÐ3ºDÏèXmPßp[lWê^CX\x0003\x000f5ÈÒ3\x0013ù\x000cÆ\x000c6ÏoOñ2\x0008±
ÁÛ\x000f?\x0000<³MÕz\x0003·ù´	®Ú;Ëz8uëöÄ¿C£\x001f:ÐfoÅ}ÁåÛ:fØóÖ«Ò\x001bÿYñç!NLðá\x001bJ;±eéÓÒsÜQ?3n¹<ñò,¸Ü²À²À²À²À²À²À²À²À²À²ÀÓµÀé6ÿ}øÌÏÈÄãmR¬±D<®Èx*ã	\x0014çc¿\x0014Øü§ú§'|ÓùÏÿüÏ\x0005Ni\%\x000fýÃ?úÃ?þ\x0017|òÇüÇ'\x0000Ïð\x0007þvó¯ýÏª¾C2Ö4õ¼1c0â\x0019çBOØ^[k4U®¼èÈ¸9gÏ	0gàq\x0001NÆW¤%Ó\x0006ì@^æB½Ôã3Ú\x001cû¡'ó\x001eê\x0013Êó\x001c§ç2#\x000fê1ªe¢3v\x0000°\x0003@ôx1%z¶L~#YûT£XMïvç\x0008M@<ã@Ó:^ÊÏñ¡\Êv¢xÉÏ<\x0002´ys<Â\x001f^(\x000eáIÐÈ\x000fy\x0019·Ã\x001f>òú¼\x0004<\x0006á½MvU \x001føS/r§/ /s\x001cPâ©\x000b½°7u@3
8¼>O\x0002oÚùkhô\x001fß]×	½\a¯
ÖxEè¸íf& Ù7Ïüê\x001es\x0008Õß4\x0007\x0006UËéEË\x0006ú¤lé¡öWòÈC~á6\x0002³ql?\x000f\x001fcÿ\x0002yY^Ø\x0013«¦ÿþïÿ®<m\x0007x6ølà9uU»®ü²\x0006/PÔ6ÛcnêBsn{sg\x0005vçØ\x0017\x001a»¡\x000fº[ÇÙG«\x001dÃØ=ùÖÛ×\x0012Ê.·,0-À¼V÷3g(J¨bÐw|\x001f\x0004ÿí¿¾) W_À¿é¨>!uÑ¯	R&I/\x000bp\x0006Låtô¶ÛãBÊ	JÝü4\x001dà¤\x0001üé4­p.<uñ¹aÂM@¯è©|mOÀÉ!\x0019gD:¡¡^é,\x0019Lî\x0013='\x000eS§HÖ»9¼²¥m¶µÒY \x0019+ÙV-¶/´ÕÎ§
\x0016ð¬\x000bRÏmµ3àsV<\x0017ø	AéP\x000eZ:rBË\x0017%½òÝZ'\x001a{ø\x0013>4v@nÙNÔÅs10åbôÒ¡lÙuÅÀ\x0017ÇÅ:ð\x001c\x000cËòÁ?\x001dáqQ\x0016s\x001dYr­\x0003\x0017XtµÌ=_+òYÁC]\x000e~I\x001dwÉ;~<-mì¶Ç@¡:PÍË\x0003¦¶9\x000fYÄÝ?¹òp0\x001enR¾{ò~\x001e\x001f¿m\x0015X\x0014÷Ä8alÁ15XÒ'þ9|l9Æy\x0010sëïº\x0017Ký~@4èà\x0007\x0002\x0000\x0013\x001eøæ\x0007³¬¢wYD\x0018X°}"+Ç-ñÃ£JÌü¡ÑxålºMyûcvW±ú·ó''iÆ\x000e¡¤O}Ì\x0015>§ßùr-
\x001fyð\x0012O\x0019xâS\x0017|?0ÛÎ'ztþÔ\x000bK~âû¶îã¯çENè\x000fÞÎ|øSfOÃ\x0003M^OÛËëñ\x001eîe>\x0016>Çê£ì^î>\x001eùw¥'\x001fº¸\x0015(Æ\x001cvrh¥7wÓ\x00179¿
>¦ßqÎ§ßfP6û\òÑ·_#Ðó8º;Ì­4\x0003\x000b_kz&Ü\x0007$Äã±Y|I\x001d\x0002c'×\x0008fðÁ\x0011º\x0016;ír¨ç.½¢\x001fôÏÇ[{ñ\x000bî¢'u\x0013Þ¥otD·ÛÐØ\x0008âIO84m\x001d\x0017[F=E/\x0006d\x0019\x0000ú\x0018ûúÏ5:6nI³ís\x0019Çã_ñ\x0019G/Þ\x0016ÞlU&}gÆy?È5Átìuà¯'PÉ	\x0006¼øÄ 
_öÑ$ÎÙðU·\x0014.yæÃ\x0011\x0017©¶\x0011½ªÍ­Ý~	,/YL=ÜÏÎ$Ãµ\x0015·ý\x00116SïÞÙ®¼Ø\x0016r½ÌL-yV[nY`Y`Y`Y`Y`Y`Y`Y`Y`Yà©Z À)ãÿé<n9Lsn
ñÆôAcj\x000c±\x0013<khSã\x000bxþú¯ÿúä/þâ/äÿãÉ_ýÕ_i\x000bi¿L\x000bØõë_ÿZ«ÿs}ÃöéÛ¸¿®o\x000bÿÓúð½\?Æ\x0018J\x0003á7MÇâùr:À3«ÏµêùTÔº"Ïó¼ñ¶ÓÖ
yäã'É¸(c>èÃpi/ñV@aÆÇ¶Ç³vò\x0005ãGä¡{\x0000OÆ¥Ìiz\y©1¨Û´£Ê\x0008\x00078UY\x0012"×õÏ9Ä¡8øB	3ÆÆaØ´\x0012ÆOx<æÄs\x001e%å ©?cväù
A'2á<ìD8rÂÓëµ=<¾&?.u¦-i\x0007õ§?0'ùä%\x001fÙÛ¡Èy	òÓ^\x001e^â]ßè\x0003í:\x0011FNæÔ\x0001¸yA\x001dÀ\x0017]ëÛào'ßóò²ú2òóqý\x0003\x0003ì¥ß¥¯±XÒ¶Çúë\x000cV\x001eòJ\x000eT,s\x000cD.õiWÚ\x000b¥­|c\x001eÐ§òj.]-aé7´ÅýÕÛR|®Ö/e`_lN^AíÝP»}Ý\x001eë[ºÒÎáÝ\x0016Ï_õ<Â¸ØÛ±õ»,\x0010\x000bä\x0008M:4÷³N\x0013Þñ}\x000eð¬Þ¨79rñç\x0002:Þ\x001aÑ$¤N½
|'\x000e\úTýüøÄòªç(\x000fåÂÌQ¿bãâh¯&ð,\x001e@g\x0000ç¢\\x001c¨£Ò¤[µÏ¿:o
#]º
p>Ñ¶à|çùRÛ%^¼þùä·a\x0000\x0015\x0006x¾aÅ³x³ÊùJg|ÅIÓEÅ ±içU~¤ã¢¹ØC¥WåÒO
,ÎF.\x0008j;\x0006\x0018v¨¦´\x001fDHX5·Ó°8_±²aU;ø«àvÑI\x001d£º½\Ò#«ÔÙôA·îÜ\x0017RÞ¼=s\x0011)wªÏÜ½å|Hæ§ÊØ)ðá2³íÇêMÙP\x001fÃ\x001cWS\x0019¾ª¶ª¯ß8)9\x0014ãÀä¸oÒ<¸y\x0018¯Îò6Ù=¸QVéù\x00139I¡
y8\x001e\x001e;Îí©{çëaÿðù\x0001\x0012Ùi?4ÞuÂG\x001d\x001d>¡ÖÓýõ®prS®S¬å\x0007Úùz¸óôpÚ´}tätYáÙÓðt~Âðáó@LâäÑ\x000f||&_ä\x000fëéNù´ßèu;ú\x001dËKZ/ßÃ]\x001eN¹c´ïác¼=-òCÉ;\x0016NZhú:M8|û8éÇÒHÏ¹mÐãYÜ*À¿û\x000ceî°ÏNãÎçóæCw@Y¿±9Ó¹nçt\x001eÐÝßè{³¿Qo\x0006\x000cÒè¾&%¾>ßsp¾Ûð,7ÛÙ[Qö§^ý¡\x0007qhÂÄñ\óx°f ÈC{ÒCI8¶³þ>gúµª£[t¥\x000cÎkô\x0019×çÔ\x0013Ý \x001eÜ\x0018D¿\x0016¾^Èïõ¡\x000f\x0003\x0007<á®\x0013áci¤ã¢oê¦ÞÐõÍd}\x0008[Vï£\x000fªÁñ\x001cË®\x0003é>þéááí`Ç+2,¯êeðw°ûmÅy`ýè{ØyzBÓ%æs&\x0013\x0006¦\x0006»y\x0019\x0011ë¹Qo\x0017óô\x0019ÝÒ6Ù+í+[Ñ¿d+\x0006\x0019 fc:õs¤\x001f¨ÕVß¼\x0011ï·½\x0015ú
¥xïCî\?îËnïL½;drÔkîf[9Ë\x0002Ë\x0002Ë\x0002Ë\x0002Ë\x0002Ë\x0002Ë\x0002Ë\x0002Ë\x0002Ë\x0002OÊ\x0002süÚ\x001eCÜjÀ\x0018\x000ei\x0018R±\x000cÎ¤v¢\x0015ò7ó7'û·{òw÷w\x001aïhì#Ïn¤¯_ÿ¸}ãùµvùüAß\x0015þQ\x0004¤Ëx	½\x0002¦1\x0006q:ièÈ\TÆrÌÛ³[)sPÆMS.\x000fç\x0018P¼\x0015¹äáÜ¦ÌAÖØ­d2*.+ö\x001aóy>"ó¥cÜfÆM\x0017o]\x001fc<ôð\x001cHVe{Ì\x001d|Ü©V°\x001dÆ8,¶w°M½ÚC¨óY\x001f§ðºùÃ\x0007µ]bÑØÁÜùHÚË"­óD^ÆÇäãH\x000fÅ&áË\	üÝ\x001d\x0019==nv L¯+²¡¤gn\x0003>\x001f\x0003ëíHù®Cê§\wIw=³_z~Å\x000b#ÝWÃ§oþwü\x000f3{»îØÇ6R¬ªÄd6[ÒIöñBHÚN0òg{j\x0007\x000cIó"Ìc1w¾µòZó?¼@: n\x0013"ÜçyYEÓn¥c·
ùÌï`Ghl\x000bí\x000e¾jëh$q\(áèN\x0018×ó²~\x0005è7Ýwä:ÕiÂ;¾O\x0002uÑe«m ÑêÄÄu#RX]{x©¦ä¨WU¦X¥\QTÀjÐ\x0019!\ü4Ñ-ÙèÀd#`.Àî©Nâí\x001bÏâ*Àüá\x0001¯Ä{¥ì-\x0010ôÆÉ¼^39y¡\x000fÇ_þô«¢g
ëÃ}\x0005>\x0017ð¬\x0016 \x001aÀùJgûµ.E\x0015.àYÚ¨výá¬;áj='¸Â^­1ñ:É^ÜCùZ9gáh\x0019.Ô±çñë#Í\x0011þ\x001a§n)Ço&]V¿Èç\x00064(7©FÜ`|óÛt'
onèU£+®ó\x0016ò¹1eK\x0015Þ\x000cóÍs' Òq0²\x0011=Ó\x000eô´În_\x000fÃ\x001b\x001fþ£é¡\x000fWÓcIÆv¶çcÕøxõ¤_ÞUó¾ý=N8òÉ;F·4ñõ3:õw,âîÃÇâ¤q\x000eæ0uZÖ\x001cXõºs«ÛÊ¸Þ¦\x001eÎ|êú-c¯xíé\'°ÀhÞ\x0006\x0006\x0010õ[ÞÊëE@RôdàyØ&Ûiß\x0006t'
\x0007ÿÞ£\x0003i¾¾yÐ8\x0014À·Cñ\x0006MKTý 7×"ôë:FwtÎ[ ]ÿ´´-øl\x0006\x0014[E¯Ø\x0015koh·iG\x001d©\x0013º\x000f÷´èÓÛDxïc?ên]OÒ\x0012\x001dù¤\x0002Û1ýö·~Ó\x0016;Q_ìÅÎ\x0015öómäè
ølÛfòÁ:U;ë¹M!]fud}\x001ce3¾å¢¼U5úÄ~	£''\x001fÏLÐn\x000b\x0003Ì÷û_Â&vê7Z\x0019}£o)á­§Ë¥}P|l\x0005ÍÀ\x000fZoA·s\x0006¹Ø
W¶/@Þ÷Ë¼\x0015ÏjëÏsÈ³ÌO/G\x001byöM[?½äâ\\x0016X\x0016X\x0016X\x0016X\x0016X\x0016X\x0016X\x0016X\x0016X\x0016xâ\x0016¨ú·áfð1¶a¼Ì\x000bÇq\x001a¹Õpb\x001b'	ì:\x001bãæl=ìñ¦ç\x0000«DµnA2F²FåX±ª=Fµú¹*©»=öaµ
ã¶±Qø¡·ËL¹ÉÂ1©Ó\x000fuLêK~)§qiô&­rÊÆ\x001ffÝ.óT~»-æ¸ù¶öÇøöüç¶§P~/3¥"ûX>iÉ\x000fÿqÊ\x001c\x00049üàçü	aËyûczØ?f¿òthd#-ù=/ýÓeÐcêÒóqX()î£
eÎ¥Ò\Wl\x0013zÌH^nYàë-þ\x0019Ú%¦ïwð¯®­É\x0013Ýîo:\x001fþ¶Ú\x0006ìÕtß\x0000a/þ\x0011V
êæ¹Haåª\W8áP¸\:Àó~«môÑ,â\x0000E¹w\x0015\x0005L×jM\x0001ÆJ¿ÒÊw¢ï\x0001\x0007ð|SÀ³Ag\x0000h\x0003Ï¬xþùäFÛ)\x0006t\x000eð\«\x0005\_«î£	Á¡ål\x0016)è!Z·*\x0003>EÔD(\x001c|sÚrÊ VüYür\x001cq¡=ýß\x001c§ÐmQÕÂy¤>\x0014×'Î¼÷¤ù\x0004A\x0002@á
ø\x0010	øP\x001e>³eigò	{\x001eLkû1\x001fPôÐø¤'/üÐw±[èÃ×¸jør\x000b¤O"©ÓÕÐóö}\x000fþäFF´Ð×ÃÉîÓÅ9\x000f©7´ó$\x001czL&iÑ\x001bÚÃû¼\x0000zÿ9÷;%xtJèç\x0010À\x0011º\x0007l3`¥\x001c×øèãø¡MÒ®Î\x0013;@÷>ºA)\x0013\x001d\x0003Xr½#\x000f\x0017Ù\£Ð)t¯\x00073Ã²Ñ9ú¹>¯\x0008/\x0010³Vì¶ãGÝñ±qho\x0017òñ¹~ÆÐ®_l\x0019ý£Whô\x000b±\x001bqô!~º=¶3ù¼|mÎR§õñ1Ï÷´fÜíðK\x0012è\x0011\x001d6Ùã;F½ýÖ/ýÔÏ+ ÑGvÄ®ò¬v\x001dÞ2-ÇÕÌ\x000eûeèÁKQv¾®óògéÅ¶hcë¶zqªO¸m\x0005Øìû§·ó.\x001bJ\x000e4[om+ÀÕ¿\x0002¾÷ï
E> ïçÞ\x0002:?Æýò\x0013±Ø\x0005\x0005\x0005\x0005\x0005\x0005\x0005\x0005\x0005\x0005\x001eÇ\x0002ÛÄüÇªóxñN>ÉG1T÷\x0019ÖØJc&¯\x0000=|¹<»Ð9\x0006<Ô\x0002àYã¹[ÀsçÊøgÊ¹wå%\x001dÎ}¹äíÓáý¼éu![ã°Züv¬\x001exû¾,Àq<v,£åçäqÌïS^tÞ¥Ç]é*Ò\x0017hvQ+¼,ðh\x0016Èù\x0010Ú+Î5²Ów|\x001f\x0005uÁ/ð\x001bWý!\x0000a\x0005§´[oØUyúßN\x001e\x001eÜEàØN¤ÃF\x0000à\x0002ßÞ¼\x0007|+\x0018w[íÜg1\x000cÐY5#\x000e­¸îgæ'5I
à|s¡UÏ|'p¬vfÕ3À3ÛloÀóéÅ¶½6 syÉ\x0005,.Ð\x0018Ý¸)WèNÝè\x0005¸UMÐ¹V<WyàXÀsì	ýpTq¡=Äo\x001eöBSÇ6Ù¯Éq&È\x0003È\x0018Tð\x0004z\x0007B\x000c\x0000xk\x0013dÅóÀI\x0018á6È0\x001f<ó`\x001aJ%\x000bí\x0004á}<¼ð§L	x°\x001fí*ô`5-Á÷c:bê;¸\x000fõcyéoMxO>\x000c»7ù)Ûã=\x001cBÉ#x\x000f§®O\x001czÌs\x001e'½\x001cÂ¹\x001e@;_ò;ô"/çwh®\x000b{|¨Ëç\x001cCÊtÔ\x0013:C¹VåºD8´ÃC\x0019Òq±_§Ñ\x0007=	çZ\x0016½\x0016}{£Chê*\x001dÞëÓ\x0005lÅ\æícBðvÙÑ\x000b:TøÑï#\x0007tM\x0015G8¾×\x0017}c£n³á!\x001cÝ ÔÑ¿\x0015\x001dc;\x0000Õ«ÉRÖ×P\x001fÔ\x0001½|¿«ë£«·èæèYgkíÆ3Zçç$úÒXQl\x001dú7­½R\x0019Y¸nãØ\x0006IªAÞ[m\x0017£¹Ý~VåË\x001eèåóc®¼¾ÒJék^ÒP^µ±ô\x0002\x0000\x001f÷ÅAÏ\x0001Áu¼Î/Ð'v×YçB±ãxöyÔÁ}öá9ö5¯ø²À²À²À²À²À²À²À²À²À²À7¶À\x0017\x0000ÏyxÙñ\x000f.cMÆvC>çþ*¾;ú\x0018\x001bc\x0019¹1^ªhÎ\x0000Ïª§V<ÃÐÇ-£\x000cÉå¾$ïKÊPÙK\x0019¨ÆaeûÏ\x001dóUC×Ï£[`µ9t[·Ëñ\x001c	\x001fÊ;Ð÷±å|<©íÜÝk\x0012g?Ý\x001e¹­L\x0005÷ù\x0007BVdYà-@ÿë¾W¾ÚiÂ;¾\x000f\x0002Ïò¯o.´,Ï©îQÁq(²R\x0007Éru°S¶Ô»oDPAÎÞ:DÜ(gmÝM\x0005ôêFÇÄª\x0018ô\x001d\x0000n¬¬\aí+±¼Óªç\x0015Ï\x0005<g«mgÎl·­\x000f^×Ûl×ç±Ý¶W=ÏÊÇÕ,êVK&ð\ù¶Úy\x0001Ïó¨?ÝP:pèÃµ$\x000fÔ@84íÐ\x000b\x0007@ÀXé¸\x0007\x001dúÃeÂÐS_§ÉÛÓÎ\x0013ÝÐÏ\x0000iôLzòzYò\x001eÖk¯>\x000f[ÕþÕ\x0016HI_ÀÞÇHëñ\x001eÞ·§õ0}:à\x00122Èû\x0014\x001f]\x0016iÑã\x0018M=\x0000©«ËI½Ï\x001fòÓÉ§L\x000fGFº\x0006\x0004xîúìÏcâñ\x0001\x001fï§,ò\x0012v»¹çéú¤ÿnè\x0013\x001a]¡Ç®W\x0006\x0004'xÙÛJ\x0019lÇÎ\x000cìÊÀªáè	}÷4z¢sìÐõ ÎØ+:Y?ìÇÊjy1v.²ÜþymNä£\x000b:\x0012ÎªçÒ\x0013ðR>v«¡ü®\x000fF×Ø":Fï½îIw\x001b\x000cèwûc¿×z¶Áÿ¨ïyÅ>Ñ{[Ý+\x00108¶¸~ËË*aV
Û¿­mÐßê[E©\x001fJ¹/}¼ ê\x001dÕV$O°þ­Ü\x000f'èm`×zg9É+\x0019üBý¤yÆ·Åô\x0000È÷Åò}®÷úÆJ}»\x0017\x0008Æ9a¯j\x001bpòÞ\x0017\x001f°?:û{ÕgmËq¶÷Êï\x001cOtF\x001dø?Ïq?Ê=éSK.àùS-µø\x0005\x0005\x0005\x0005\x0005\x0005\x0005\x0005\x0005\x00056ðêÓZo\x0018_]yî1Ë1_cAFò\x001eØlã\x001b¥TE²æÐ¥F«N?\x0018Òh.^ã/¯zþÜqÎ§µçÛpa\x0003gÆb\x000bxþ6ÇàskUÿ\x0003\x0010J§Ý7ÌÞ¯G\x001dÉÛ)öÑ¯÷yuÜ7Ò?T×ònÕ\x0015yCßE\x0005\x001eÝ\x0002ôÁî»\x0002u2(¡Ów|Õ·'ºõuÝy~#à9 34\x0016QPkUâ)@R&¾íô@Ûy\x0014+?¹\x001dßJH\x0011o·Íß ó9«c¸AjRo<Ï\x0015ÏªDÅi¿Që··®\x0016àÙßxÖg¶Û\x001e+/ÇwÏÛ7O´ÕöµV<g»í¬v6ð<V<W\x001bÇ­9õJ¹Õö'¬xf]4myVc\x000buìéÿVÏzfÔÃ!=õêe£hÞ]N\x000fzZl[úþZ¨Á	\x0003X\x0001\x001dt\x0002É~Oô\x001bppØÛJ\x0016BK]©³Âá#½ùè6ht*Í\x0014	8Pz\x000eÙCü&\x0007Þue(U\x0011ú°µ-é_g\x0001ú\x000c YõÅ¨\x001a\x0010´CÃºw9=\x000c?ç@JÊß}ôèi	Spw©»Ó\x0003XA©7r \x0001\x0017Ù.8Ä|ÃÝÚá\x000fí²\x0008ûü #:Pçl/a¯æ4(ÊJaÇÃ2ÐxÚJØ´~·pÒ».è×Û×õï:&=i§|d\x0000Þþ\x0016½Û\x0015½ÓÎNQ\x0012\x00198dF>õ\x0001z«e\x0003Ð3¸¼¶ÚæXt\x001b x§±å¦õã\x001f>\x0000NøÓ¾ª[u%\x000eM:
¸ÛÓ¢74>rh7a./\x0004\x0000ÿüó¯Ê¿~ýzkW\x001fw\x001câ*C9ëa{0yq\x0000<­ªý\x001dgï¶\x0011½\x0000g_¾|¥cö²\x0000è\x0002kÇsÛÙ\x00064ÇfØÏ>Ïm±o¾·vX'µ\x0013Ýtÿ«¶©q\x0006Ù"[ç\x0014÷Â\x0002³ÂY ù¦«^*(ÐÜÇ¶ìÅr96P¾ã|©gD^\x0016È\x000b\x0003\x0000ÐäÙ\x001dÿ#ñ#$eB?ÂÎ½õÀå/\x000b,\x000b,\x000b,\x000b,\x000b,\x000b,\x000b,\x000b,\x000b,\x000b<+\x000bl\x0013óÖ*
=·P$Òx"ãÙ»)²á3­4d1øì±F^JfüUÄTc/V;\x0003>÷q[Ò?\x0018b\x0001ÏOç\x0010º\x001e\x0000Ï(s'Àr\x001aTìÕÙÕíGÙ-o¤\x0013¿3Oe\x001a[\x0015}°ºèQ\x0015®eÇ´\x0000çI÷½î\x000c&¼ã«ó$y¢9o¸ÿ\x0018xÖÄîDÇgu¹9ùÔ\x0015-y#>d×
+õl£LJº1fáÆÆ6 }ÏF®ßßb óøà\x0000\x0000@\x0000IDAThÕL«¨V%©X\x0019Ô\x0013Ü<YñÜgM²g«í\x0013&\x0017k«í_\jBöll³ÍvÛ¬x\x0006¤6ð|ám¶5Q|%yùÆ3«ÑÚõ\x0012B\x0007QÝ¡ÒúÈgçñ[[v\x0017ðüÞ¢âøá 	WÂ3øñ\x0011\x001e=íÑÚÓ\x001f\x0010«Ò2«\x001fýx°d\x0002þ½&Ïk\x0012]î\x0005D\x000fÐC\x0000§WrùSõc&ö+>LÙÁ_½YÍ¬:ÕG\x000fênéÊºí¢×¨³@\x0011vWPDõEöQ\x0019·¥~E

ÅUôQ,`Pk¾=ý$îXøXZø"§%\x0018¤r\x0002e'¸Å90ë#ñ;MøXýIë´Î5@7su¨sÕõ\x0005d\x000e
pø¤£Ù2xê6F¦)zºnïfÙÊØ\x0014À\x00190m\\x000fto´M(9m_WÍÈ&K Röªk2=Ø5øp§¯
ò»Ýz\x0018ð¶äí}/O\x0018ã\x0008Å¶Ô\x001d]bë¤ÃSùØYß
ö@]wêÖWöö$\x001eÀr\x001fN9Ûtê^A¬ËöÂõÛô®Ñ1:GÿÞ®\x00124~ö6Iký¹lÈq¯\x001ag\x0015ò¡}ê>Àý¤ú§íúèöé¾w8
"zéWég\x0000Ï\x0006I÷æC»Íó\x0011\x0019·,ôQÓ\x001fºdËì²\x0011éÔ)}Ot¼ôWÔ¶\x001aÇ\x0019°\x0008ä\x0001ÎcÏké:\x0000®­W^Â\x0000d\x000eàLßóË\x0003>WÒNUVå?ýçsù\x001dâ?½¦Å¹,°,°,°,°,°,°,°,°,°,ðÄ-°MÊz;jTc^ÆOe3¶b<êpÆ\x0019s2î¨a\x0018C,ªÜ¨Çc$ÔðLü\x0006<SO Ô3p¿\x0002<\x0013^îû·ú_õÁêw¨ÛòZpôv\x0019ÇónëÏ0â7ã$¨ÜÛ?­\x0016ü¼ºº\x001e·kX)Ë\x0002g\x0001:q÷½æqnä\x001c)´\x001d_ÝÓ'ºÝãtïùÍü7cÅ³_&MùÃA\x0001QK\x0007Â\x0015$Í¹Î2/'oTJ#Ã©¡.i	\x001bð\
\x0001iR\x001e\x0000ÉÆ
|æ\x000e(çë´OÂPçw\x0002&\x0017ð¬Õ,Y,à\x0019Ðo=½ßx®\x0015Ïgó\x001bÏ×\x0000Øgàù®\x0015ÏXB^º@?
x>\x0018é9¹íïcò|FãX=üñ*Ë\x001fúp|Õ­ê£\x0001\x000fñµÅè\x0000§*
Ãç¼Pßå¼)Ð9ç\x0006çþ& ÅÊ/ê¢ B\x0015\x0018qÊ:L§²u&Sg¯ßÙõk]Ö¡¤û=Û~x¿fú^¤¥\x001f£\x000fa÷?kw,|,mß\x0016äÜåöyû8å¥\x001d«7i{¤E^\x0007ö\x000c\x0005`\x0004 àX@?VBS\x0006]8Ç¥ÂHÃm\x0001GõúxéªÊ\x0006Ð¼\x0005´´\x0000Ï\x0000Îó~YRK¬ÏcëAx\x0007z¸þ©«ÁSVæÆÓ&¦Qöt°ÖäÜ¢zG<Þ:ºî\x001c#¨m4ÐÔ½×/ñð§¬u£ïÉ\x001akBS'vÇhçÇ@O\x0002C¯\x0003:^\x0016B¿Ø	\x001a}¢_×?yPäÇïu@©W²³¥wtSÜ(54u@£G­ô>è\x0006àsì±Oêfõrï?ÉetÇf¯lÀ³û'máØr_}òìâ1õäÜàØJ§²÷MñðMî·J\x0017%/-¬~Þ@sdù\x001c*\x001bÒ\x0016ÕYí(à9[£§\x000f\x0006p\x001ev\x0014`ÅVä³~\þãE°\x0007\x000ep%¬eeeeeeeeee§fmýá\x0014g2=c7êbÌ\x0013qdâPÜn¼¡!\x000b£\x0016\x000f}æ<\x0000¤á\x0001Ëë³GÏ\x000fx=ÖVÛ\x001cî'àª§.L\x0018×ûsÒsÿy½.êèõõ¼\x000eß§æÁ»Ü²À·´\x0000}·û®Kúq§	ïø\x000eð4ñl÷DÝî\x0002-j\x0008\x001c\x0005tËÙÀgWAÜ<º\x0005Ö¹Ut;\x0019}ò[c¶\x0012Ëg<ø\x0003t.\x0010MI\x0014ÐË!ÇD7>OdfÅó1à\x0019\x0000\x001aÀ\x0019àùò§rÂVÛ§?òç±âY\x0013¶×\x0003|.Ày\x000f<W[e ôÖÚð1àY­\x0011;¿\x0000ØZUÍÛTÏÆq\x00000Æ Ï¦]4Ä}ðð\x0006ñ0
\x000f<ÄåápRj%\x001d	ð^&iÅ \x001fÈ	\x0008\x0001Åeb\x001fð\x0001\x0017¹\x00159\x0012Oú¾Ä÷\x0014þ¤Evhd=\x000c¥\x001f\x0002¦Ó\x0017ûÞ->\x0012ºï#ï)íJÚ¾u,~Oþ1.ïX´¤ßE£ë1\x0018s-t\x0002~\x0006 ÇÇåoëÙuH]¤åü\x0006$\x001c`2$+9Iàóù¼6è¾Y/¢È.½þè­phx ÙÂ\x001aôÞÐ®\x0013zõï8U§9~Ôµ÷ÈìÔ\x00050xx \Âè\x0012g\x00012ë\x0019âÜ`s·iì¶§±}d!7uv]\x0012&\x000f½üÝa3¹IÙÐè\x0007Í1ÍqÄn±\x001fáø²¯VµC¥NÕõv|96âß¾}»\x001d7ãÚé®××PlvgUðemK}¹\x001dKtÂ±\x00057r]ó\x0001ç¬bWÛÍç0mí6¨ÊuN\x001c\x001eOx&ÎwoTÏ\x001b}Ëùl¼ô¼à\x0017«TSégÐÛ/3ôv¥}ÝÆ9þèº¡\x000fïÒ/C\x001f¾ÆUÃ²À²À²À²À²À²À²À²À²À²À=[``¿g¹wëcO÷¢IÛa¨ãáÎ\x001cSy\x001cdNò\x000c<>kàyÃö}ãûÓ!\x0019ãsÌBæI\x000b½+t\(ü½Ì§ä?ôsêB~Ê\x0011^nYà[Z }7´ë~ÚiÂ;¾º\x000f&Ot»/j~½\x0003Ï\x0017ÊSJókº×iÉä\ÂðÀ&Wyú½©\x000bÂL!Ç%C)2¸¥Èûò|\x000fQÀ\x0002³ê¹\x0000gMTú;ÏðK#\x0017«ÜDÙb²V<+\x001dðùpÅ³&kÙj»ç_5àùgoµ]À3àó¹V:Ëk\x0014\x0000-¶Ë£¥Â®\x0013Ý­7À3°²©ÂÄ\x0005³\x0002: ô\x00029þOÍ=\x001eð	x\x001eîèÇ{åúC¢\x001f\x0002óPhÚ­[çÂäßS:ãºì¤uJîzü®pø?&;|_O¥ã\x0002¿Þ,!ýgßOz<áÐc*F\x000ey=8iÇú|dÞE?VWäo\x0002\x0006S/uÏ<I\x001cø».\x0003\x0005¸#­§ß\x0015\x000er¡Ñ5uFPôL\x0018NÑ=y¤u\x001f¾ÈN;¢\x001b4Àiô* T iâi'2öõ#/iÑ!:\x0005T%?yÑ-ú¤í¦¾±Z\À3zÆ'?mH\x001c#\x001d\x0017Ý {\x0012ßÓ½½JÐúC©\x000f\x001bv°´7ýôÜÂ*a@ç\x0000Ï±]l\x0014}îãÍªc\x001cÍÂ#o/àøm¨µ-õ\x0006X¯ç%x-º³"\x001a ß:AmWÿên²\x001dO×Mù«\x0006:#++\x0003.ÛÎ\x0002¥\x0007ð|%jçã\x0010ÝCy\x0011Ñ/%NÀ96ìÔ:'6\x000fE\x0016õ>K;B\x001f§ÖUË²À²À²À²À²À²À²À²À²À²À=Z``¿G!±\x000c.t\x001f®ÌúÉØ1S³\x0015c Û\x0018ÁI~
:#÷±ÆGSÓ\x000ba+ùZñ¼Æa\x000fgçû¬þW}0ýpÜNwåíÓáM¹}^Ò?$ïCy{ywÕu\x000fÞå\x0005\x001eÓ\x0002ô÷î{Ýé£&¼ã«û`òD·û¢æ\x0006'ð|rr¡Ô\x0008¡¼ºõ\x0014\x0018\x000bÎa\x0000çq«RV?Q«T¥\x0019pv\x001eaÁ·\x001bðR5©ÉÃ´Ô¤²f6\x001bðÌµÆu±¥°'
wÀ³&Eo.ØfûEm¹\x001dÐ¹¶ÚÖç³\x001f½Ýv}ã\x0019ÀùÈçú6³nÜèæÖ\x0019\x000b¸\x001d\x0001jâ¶Ö4ë&]ù¢\x0000Ðü^\x0003O¯\x0015Ï³|÷¡Ç\x0001ëNý$@D&¼C1S\x000fÇl½\Oëü)\x0007er\x001dú¹è{þ\x001eïáèðí¨®#\x000bxþvæÿéÝ},Þy	÷~x,LZ|ÊRG÷¤'pxSö.
_ò²¢Ô«HÙºxÛ\x001düËùri3´\x0003a\x0001e\x0003<ö¼
\x0003®
P¯ËH[ÖÛÒõE\x000f\x0013\x0004O¼ëN»²Z2]þ^§½®û8e)ÓiôF§è\x0011[%=||çèK>®×\x0011;NÐ4[*ûÛÄµ"W@i\x001c²ö.:&=<Ô\x0017ßu^I':"\x0003yñ{\x001b\x0012ïv/<	C#§\x0002ã§\x0014ê,Ðù­VWëØQoôM8ñþ|fÙØÎõE²Àç\x000b\x0001àçcõrxPÃ²xÖÑ³âÈ1µR©§ì¤ç$¾ß\x001c»°=v¥gÀçØ36Î\x0005H¿û¥V<\x0003<û\x0018Óüh\x001bMÝù®¹¿åL¾WaïífÖ×ö$\x001e\x0017\x001b'þ°4õ>lmKú²À²À²À²À²À²À²À²À²À²À\x0003X``\x0000Ù\x001f\x0010ÙÇ.wgqFnÃ)àá¯Ç5öÒ\x000c8\x000c}X¼ç\x0018lÑok\x0001uÌ\x0003à\x0019m2ÞzuSñ®¼¤Ãº/¼}:¼_2\x001fª«Ë&¼Ü²À·°\x0000}¾û®Cúq§	ïøê><Ñí¾¨¹B\x0003Ï\x0006e\x00123\x0016CA\x0017\x0006^ev±h¯Cá,¶~¢:\x000c\x000b\x0007%í\x001cöjgrk½ðXí¼\x0003Y3lp\x000bxÖdm¾ñüN<^ñ\x000cèlðùR`sm·­ÏlµmàÙ+¯4)Y«\x00015Égèõh\x001f«Ñ²µ¼ôg³Ági-ÝXý\x000cå:UÏµâ¹d­­¶Ç\x0001\x0002äñç>É	ðc´\x001b-\x0013ñ¡É#²¤%¼§L¾ÃÛÝçÄ;/²¹Îs,ÿ~ÓÔ\x0005<ß¯I\x001fXZúM(Õõp¯>éû>Õã	Rp|ä!ëc>¼ÕÏÑaI'i\x0006gßÖVÆi©»ó$-uD\x0000b|\x0001H¡Ý\x0017\x00008V¿?åüÄ£gtìqt$\x001eÚÃ]\x000eízóæMyx¢\x0007º±íó16À®Ñ3íîò\x0013Ný\x0001ð»^ð\x0010ßû\x0000¼\x0001¥¾Ô\x001b\x001d³EuâP\x0000gVñ^\x0002¦ê²è\x0010J¸ÇSGÒGÇè\x0015Ý£\x0017éá
 Ñ\x0011=­Ë<ÖÝ¾)\x0003ÿþø¢GêïºRß[@çÚjûj;¯º¬è\x0010|Àäó¶R96¬¼Zá\x000c\x000f¾Ý[\x0014.\x0010ZÏ8ú\x001f¾s/öÔ±\x000bÈ|ÍÖÞ\x001cKoñmÛÍ0oÚ»=]\x000eï\x001efÅ³Àg\x0001ÏÖo®¯ãÉ1­c-Á/¥Agøc\x0003h\x001cÇ\x0006ãxxBÃÿ04ú>L-Kê²À²À²À²À²À²À²À²À²À²À\x0003Z``À:èýX¥Ç{x\x0016a¶\x001eç_È\x0018\x000ejìÆ\x001f	þ7(Þn1íôôC4F~­x~BR\x001dó\x0016ðüÔ¿SÕX¡w2®e\x0007´Î/.þïU¥ovðïsgM%ªt\x0000W-ÎaÝv|.¾T¨É\x0005Á¡J¨\x001f7À 3¥Ó ñK±kù¬.fëlOhJ¶ô6Ûº*#¾\x0012­ßÚRQ\x0013¦Ìzîg¯v6ølÐÙàs}ãùµÀgùW?ÎÕÎ\x0000ÐÈÑÌªgàï%\x001em]gµz\x0000Î
K\x0000Î\x0013|6\x000fÀtÁÑ	\x0010Nøù¸qìåE_ÇéàDy£î\x0006<\x0018Þå»\x0006½\x001cé(æá²Ó.\x0013à yòôrN¯¸YWRö²\x000e=V¾çß_XJ/àùþÌù\x0008öýf\x001f
ûô}J|O)OZ/0´áM0²¡\x001dàëáäÃKz¾uËêÌ:ÆÏ+_\x001e¬s\x001d°¯À<îwf¬*\x0015\x00089¾×k0
p
/\x001egðKáq?®è;¾w;A»wè%/}Þ\x0007h\x0006PUZ®;E\x0019d\x000c¥£¬<m#\x0008@øîAx\x0003\x0002ä\x0005Ð
%/ßk6HI»ü¢åÙ®±WtM¡ÝS&Ç#¶\x000eMYhx Ônøè\x0013p<ºCÍc°ã{\x001d¢cÒS_Ú\x0011=B\x001fý\x0013F¯n\x0013êßëÚÓÈÃ¥oÞUÏ^?×ïãÎq¦m<O\x0015\x001d lê=¤\x0006Ä½Ùá+se}u½Ò\x001fTDF¶Öööl9oüb·Î\x001e@s\x001d_¾ã\x001cðÙéá©ófô=¶Ù¦w. J\x001f~'ÿV}õêÔ1¬öÌcíóGÇ¼:\x0000én´çÔÙe»\x000eìëúÜçÌ;¯\x0015[¡\x0007	D©Ð\x0007©d	]\x0016X\x0016X\x0016X\x0016X\x0016X\x0016X\x0016X\x0016X\x0016X\x0016xH\x000bÔ<âCV°=\x000fÛìâNÚ2v\x0005ñ\x000eã.¸+Ê¸i\x0015Ê°HÚb\x001bÙ5ÿ[¹Ïà\x0007\x001bÑ~ÆÝûî-°á\x000f­s~÷Jª£?~*ûâ[\x0016¸w\x000bp^uß+È5²Ów|\x0007xx¶û¢îT¿ùÿúæB³rç*s.
ð\x001biz\x00050¢ëFä;_\ÿÎsæÐÁa>µíZ\x0017ü	<3Q(¯	SÍ\x000fàYLº\x0019VuR¼¨&\x0015ó=¿Ûßxî+õg­v¾ÔwÏ\x0007è<g¶Úßx¾ÌÃ\x0015Ïn'õYwM¶\x001eÒE4Àó¹&ïkÅ³¬r&Uá%·d±\x00117my6ntÆíÂÿl\x001a¦è8\x001d(\x000f×6@zÀ£?\x0001&
O	Cã<9Îià\x0007ÂPò\x0017ÞërOzøR.4éÐci=?²Br¡I\x0018ÊÉæ\x0014\x001eFþú\x0018\x0016Ø÷¡ÕÙûVÂ¡)L\x0003O·û=<á&Ü\x0001CÂ\x0001\x0012\x0003ðuJðsµ\x0007xÓO]ù¿Ý?9ëããÞfÐN@©î?g\x0002
\x000e MàYOK; ÄïU×V÷^ú\x0016Ð|¨{ÏjO\x0011 6=¤ù\x001bQ5©ÚD{Ð1Àm\Ý®;a\iô-³"8üØ5¼èEùî»Ìª`ü¤\x001e¢ÝNÑ5zv\x001d\x000bL­öÊ\x0016ú£þè³§]·Ô~¸^wÒ\x000el:Ú\x0011¡CoÓ±päbÈ]B£SèäµNõ\x0004§g\x000eìaÐ9ý+Ôý|tó(?î;n\x001f\x0016ÂñK?7¥O§\x001c|óÅ\x0007@ç¼D\x0000Ð,Û
l\x0006p&<u6uwß¬ZmcOÒ¨·\x0010O¯U­µ\x0006è\x0015ÍÛ¹¢öæ~`[SÚí 4Ý¡üN(ü¡¹Åq;éSr\x000fýbA«à²À²À²À²À²À²À²À²À²À²À·²À6ÁþÐ
xtvPKÆo$öð\x0001\x00139²«,E²óàjU ®æÂÕpÆ\x000cÿhÇ­,¾~¾Ä\x0002\x001bö@ÇlóKd}weZ_üît[
ýã±@Î­ÐÞò\ü;MxÇw§g»¾j~×À³@g]|;ð(&ë¢\ç·n9­´#§|åQq.\x0006¦u£ª4ÃËpØi\x0012]²XñÌ"Ógº³×ä¼iòUÏÜùjÅ³
¡MiÅJ\x001e\x0000]M6^-«ooµmÐ\x0019ðùüõ¯jµ³ç\x001fjÅó\x0004\x0005\x0014K\x0016å½Õ¶ª.´:©¿¨RH
ð\x001cÐ\x0019êtóÞH·\x0005<s¬{<à\x0007»L~g\x001bÚ}·\xS®Sø2I<LO#=eBIÛ»äõ²	\x001e+rû¼ûëì\Àóýô\x0001¥¥OîûÏ>~*)Oþ]á\x0000~\x000bïÞ\x0007Ì\x000b
8\x0016\x001a 2ñ	Mð7\x0000\x001c\x0000\x0018uu_ç\x001ei\x0005\x0019\x000c¬Î\x0001\x000bx\x0006\x00084h\x0016svG®î)w|\x0017W¾Â\x0001\x000bÀU¶2Î7sgX«°Ã§ûÌ°¹ºÎ:Dõ;ô×ó@\x0001|¬\x0010Î*áÃº±q\x0000UtEFlMÑ\x0011]ãóÍhhò ý8"#íïu\x0004¤O^·sÊÂCÙNSN½F+Á¯´Vö\x0012H\x001aÝ èÕiÚ\x0000E6.õF^§É\x000b\x001f:Ð\x0007³\x001aô´5v
¥\x000eÂUg{x¥ÉN&=e\x0000]//´Õ´>3\x0002-\x0010~6lÁwke°têv¥ÿÒ4±\x001d8ë¥ºë¼A7ëQ/Y³Ê²\x0001¡ØÏ+mK÷S÷Wt>û`ë\x0007ZÐ\x0017ô\x0019\x0018½Ïp¡íÀeJ·KÏiÓîî/ÛêìzR£19ßcs×Aÿ\x001fR<n{ï÷3í@âuûÁ>÷Ëâ\x0015úeRV©eeeeeeeeeeohmý\x001eu¸c±Çó}ü¤1
ÕnC\x0011ïª\x001ce90E\x0016ã§Qö<Í}or»À§\x001e¦QÏ²aOýÀÜ¡?\x001d³û;ØTrú`èR~)û¬,ÐÏ­Ü\x0004ÒÀ\';M8<P¥Õ}0y;ïô¯þä_Ý\x00008\x001f\x0002Ï\x0014ó\x0005\x000cA"È2\x000cKOô»ÝÐ¢¬\x001b`\x00087¥\x000egéPÀó \x0001\x000bVÑ¦¾n~Ô$ñ\x0001ßS+ï;Ç{µó?9¹Ì7µêÏµÕ¶x\x0001\x000b|fR_á¹âù\x0003À³îÆ´U8\x0007Às¥K-QV9_£¶ÚVøù¸q\x000c··OËtäv'ÊÃ¶}\À\x000el$=<Ä
\x0004¸LÂ¡äã:?ñÈÎ$}ÏO8\x0014þ\x000f¹cú?yÈOÞÃQ.
:é·\x0007å«iIþz\x000b¤_¤¿¥ÏDò>ôc42ÈëáÄ³Ò5À3<\x0006½L\x0013\x0006\x0014#\àÂ¡\x0006Ï\x001cO8|)\x001b
X\[c_\x001aÐ£\x001doÐ=øyW<çgÊÒ\x000eÂñ\x0007\x0014
@\x000eñÑ34mööGVdG×Ðèp!ð­´_\¾,ð4ù\x0012Þ;ô¡N(ºDçÐÏ]¿®\x00132\x0003Ø\x0006¸åx\x0016;F´å\x0018Ýó\x0018\x001cÕ·¯ÞJ7£Çô$-¶Æ.Ðè°§ÔÕë\x000bè\x001cýÃ±À§ý¤%|\x0017\x001eý8FN(ÛL¿xùêäåW:n/\x000flT 3vcK÷¼ô0ì¨æ¨mö\K#/u½g«kéÝ&hÌµw<\x0005N½
:¿Ã®Ú¦½V:\x0017®s©Êsÿ¢\x000e®Û©sOý¤NÊ=OÕ\x0007ÏÔ&yc<óõüV+ºÑ]<ðS\x00152ïÐu÷Õ.î\x0015úç\x0018âõ¤\x0017Ã­VÏ­¼/I\x0018:G÷/\x0011±Ê,\x000b,\x000b,\x000b,\x000b,\x000b,\x000b,\x000b,\x000b,\x000b,\x000b|[\x000b<*ðì1[opÆ7¤e\x001cÕók\x0010´åy¼´\x0018 \x000båer§XVÒ\x0007Û³ k\x001cö´\x000ecæ}[_¤\x001f2§þø´ÊÒö¹XóªûÞ®ôÍN\x0013Þñ}\x0008xþÍüW\x0003xÖª\x0012ÝY\x000eÿ\x0010$¡ÛÔ\x0010r%µÃ§ÿ¸\x0008dBòà\x0006f°67¼Pç+É®M\x0014Uw­¸\x001e´îvðÜ\x0000hñ¦y\x0000Ï¬"Û\x0003ÏsÅóË\x0013M³Å¶¿ó­¶ªUÏ§õgÎ\x0003|.Àù\x0013çl·o;\x0007|Îªè\x0005<÷Î÷Â\x000b<c\x0019&Ã3ùM<\x000f¡¤ÅÁ«	ô#áðíi¿Ïë2w¬nò¾§=/ºEnd>\x000c=\x0016ðü0¦}\x0000©é\x001bÇD§O%o\x001fOú¾_Ý\x0015§|<eá\x000bè\x0017\x0010/\x0014Ð,aè>NZtï4r·ïË\x000eP/À#4\x0000ih\x0001f;p´¸´çX=ð [@Òè	o×¿÷r\x0011»ìuI|Â¬t\x00060½¼xQínÈèrSß^èüc4rºN;Àí'-zBáÝ»®gÏ\x000bï\+àyl\x0001nÑ7´È¦^äØ>}Õí\x0000CÇ±§óåøw\x001bPÏ1\x001f\x001eê$Ü]ä\x001e£¶\x0013«_ÈV[ýÖÃ:óMæè\x0015ûÙÜ\x000eï/Ô_@s­Ï9\x0000õË\x000e¬\x001a·þ\x0000ônuí"­á#¶äA£\x001b;ð*¿\x000e+±z¿P«ÏÔ.úÛQå\x0004@\x001bx\x0016_gtV\x0019Û.çÒêX:\x001d\x001dpÈz|\x001e.f9òF¥Ü¼/I¬Ð/±Ê,\x000b,\x000b,\x000b,\x000b,\x000b,\x000b,\x000b,\x000b,\x000b,\x000b|S\x000blóå÷¨Å\x0018usp\x001e_9¼\x001f¿Ôxª\x0017RøvÚ±ñ\x0007òîJß	|òÑ´3ôÉ7è7`\x0001ÏÏü\x0000¯æ}S\x000bÔ,4\x0008íÊä\x001aÙiÂ;¾O\x0001µa\x0001¿`Ê/%J\x0002ø\x001b·¶
Ræ\x000eæ4¸ºó0Ý*:\x001fÀùJ%ÙÞ\x001a\x0010ÚÀ3¸âbÒ­¶E«L\x0015A\x000bn+Ùnûò
<¿<¹ÑäkgV;{«í\x0005:ß/ð\ 3ß\x001dÔäê\x0002é\x0003OÙ=>ð\x001ckåa1ôóp\x0019^hÒö´ó|J8åñ¦þä%¾§ä'
yñ)÷pT'ü\x0002\x001fÎ¼÷,9}-4âÓw÷pòÑ½cñ=G\x001c>h\x0007\x0017Ã|xâ©p×+áÐla|qa ôw\x0001)¶E\x0007ên\x0001%IK>4é£_ô&­\x0002ãúRç1\x0002vÝk«m\x0000ßsÑ!õw\x00000é}pt:¦Gôé\x0014½R?úD§CÃ\x0003Å¥ÍèGø\x0018
\x001fù¥çuV;¿Ûdt}	G>4uöãÚõEHøJàøI\x001a\x0014nÔ\x000fí6MßouâLoÁ~{%x¥m\x0005\x0010></æ:'Ô1y4×C¶ãL9\x0017d×_´lxuòæí·Ã£w\x0000éP\x0003Îî£\x000f¸Ë¹Ñí9Ï\x0015ÔE/È¥Býð(¨î -ÃíKFÎ£¿´2¨ãËë»æÞ.\:J\x001cÛª²å
<\x001fÚeê0C\x001cG\x001fËö5¡È
ý\x001aY«ì²À²À²À²À²À²À²À²À²À²À7±À#\x0002Ï\x0019ï\x001ck§6·ÜLcì³Ï	É\x001bÃÁÆèñaKx\x0006Á´;ô\x00194éY7yÌY<§Òÿx\x0001~õÃçtT^[rnö\x0016¤ovðïãÀ³V;«³kAº½nHÕñýËIàùJ\x0007hvE¡·\x000boLp;\x0013¡I¿Ä+Ýá®Ä	¼Ì¤â9[)r×ÓÄ¡W;×l¡r6nèÇV<³åö\x0006<kµó|V;\x0003>_hí³×¯ïeÅ3«Ùj;«\x0017ðÜ;ÜS
{à\x0019Ë}|òÛö500m½''é¡I\x000fíé½î\x001e7ñ=íyÈü£:á\x0017ðüpæ½gÉég¡O_ÚÅIÃõò=ì\ÿ\x0002êe;ê\x0000}\x0005B©¾\x001fÀ\x001fé\x000f@Õe\x0011\x000e°ø\x000e:&\x000eõ6Æ\x0002\x0005ÛçÎ\x001b\x00005ò ¸Ô
E\x000eDFw(úM`Ò`\x001aeð{>8h×q¯O@Üè\x0016Úù\x001c\x0016\x0000,0S\x0012K¿èõöí[oOÞ¼ySv&\yÚ^Ùv6\x0008\:dkäZ¹l@9«£Çíz
²&½ë¶ÑÎØ!Ç0v
í\x000f?«¯Æ6ÛðY\x001eÒ&ø¸¯·×O8:@ãr<:~¡Ñ\x000bÊñ¶÷
aVå\x000e`{\x0006°*Ùèq^«½õýfVË×öçl.-¼±' 3ÇÉÏHÖkêâãQ 0@òè?Î7h¬­>UyõàG?ãZ[ÿú¹©cýûßÿîäw¿ûÝÉïÿ{L\x000f\x0008«gÒ?)#\x001f°ÙÛ|óbáÜò»Ú(Tyã\x0003in®ÒUçÙð±K§9\x000eiW÷{Î×\x0005@ûR=Jú¥\x0002ÊÄG¿ÈiÕïèv¨ßá3£\x0015úÅ\x0017û²À²À²À²À²À²À²À²À²À²À··À7\x0000=;l:c§\x001a»éw?¶éñ\x001e¦Ä>N\x001aÎS\x000e5ºsÂ³ùÍø+ôÙ4ì6Äó\x000céÛÏ§ô¿\x0005<?ãùT[Â5¾ûÞ\#;MxÇ÷%À³Eirn»\x0012ÈØ¹u\x000bòÝm§¨oNá\x0012PÑÀ³ÀgÉ}/9\x0000ÎLºBYAlðÙB¸U\x0016]È\x0013Æj»låå;Ï\x001dx®\x0015Ïcµs}ã¹¾ï¬\x0015Ï?ý|rúêmíí¶%\x0013=ðT¯V+@
¾@gé¶\x0001ÏL\x0014\x0003WøDIA\x0017¶ðæ»ÓÏÇa\x0011\x001dmBú¹´Ì}Ûö\x0006\x001e®eØP}Ëd«F]n¸-Pñ~,ÿ¸¬pÒ]OèÌqh§Dõv\x001dÞM\x0005\x0007zÜaÎÁÈÚ\x0002J\x0018\x0013ü{±a½7J\x0005òÕ\x000fy\x0008Yî)X`?8ºkÓÛÒË$|\x0017M9@Ð¡\x0005æ	|¢\x000c\x001eP*\x0014þ¤\x0013Fî?\x0004@Âç|\x0011X\x0006ÜËÎ|Ä»\x000b8Fý\x0001\x000f\x0001I\x0003ðõ6ìå$\x000eÞÄ\x0013þ\x0018íe	×*V­dµý;¾\x001d4ÍvËsµ3íÁAjuª\x000cº\x0001m\x0003:÷4Âä\x0005à.P\hEÆOah·SìÕmLØ¼¬8\x0016Ø«­¢\x0001L©\x001bùÑ'4ºg¯\x000b2£C§=ÜõØó'N³\x0008ã¢\x00034vÝ 	'Ïü\x0002ÄõÜQÏFã:^ÂôSupßFWýÅ\x0016®Û+°o¶o9Ï\x001bø¾3xQ®·UÞýÑ«õ­ìwo©aTeZMÎ6s¿¬
\x00050»M¡Óî}Ûl\x001fö/Ô«}q¤\x000bKýgd#\x0003ÙçWl6ª¨ßcT\x001bF¯*©\x000b=s\CGvÑkõIÑce¥}°Å´,°,°,°,°,°,°,°,°,°,ð=X`3¿Gej®ëPÇo\x001eÎ1Ø!OÒk<ÎñOÊ90ãI7½y¶\x001dVñb\x0001¾Qý«ÚO·\x0000s¾Ì5ÄzÉïþ\x0017ÿÐ\x0018Ä÷k¥Ù÷`W¡]§\';MxÇW÷än÷\x000eÝoüçÛ+a7èÜ
êÄ@>ùi¼	FZY2w.\x0010³´Òõ-¦wºÃ½\x0013õgM´*\x000eø¬ÙÑáUCMÈZ¢TVõþÆ3ôZrÞ\x0015Íª\x000b¯v®\x0015ÏúÆ3 óåë±âù§NÎ\x0005@ðg½\x0012?ôZ\x0013¼Ä\x000btV\x0015i©[\x000ew\x0001Ïl¹]|Ò\x0005
,]rKÞsº¨jÝó[iJßâ s¬\x0008?¬Ëäxèamý!°ç\x001cK®\x001cã.uëX¹ãòû\x0003èþáu\x001fO\x001d¡Ç5º¯Tð\x000bx¾/c~\x00139é?ûþx§û0ñF\x0003\x0012Ï\( äx£\x0003´\x0003~\x001dô\x000bÀ\x0017\x0010²óÕõ°®ùêÍE.I£[t	\x0018~\x001fòáv\x001d	wN=?:ö´{¹\x001enê\iõò7ZÕ,\x001b\x0012Þðl`Þ8\x0006i[ÊwÑ£Sì\x0018\x001eÒw05ò ©+vHZâö<Â'\x000cÍñÊóJê\x000fÍ±îú\x0012F_\x001ct¯\x0013ñ=Ø\x001d½rl\x0001ò\x0011ÑÛ½¯c\x001fO£LtHyhôVÙS¯|öêçÊn?<¸ýÝ.þ>3+ÕçvéÖY/>Ô7°I'_ÇbÓ^á9Ü/Ý¶Ñ>^ÄP_ÈÈyÕ©ÂÚ^Çí\x0015\x0005<.\x0010Ù/+HJÙ

Ø|}­ÿÃwÀÙ/6X\x0001hëó¢\x001fs}}¨> 3Ô\x001d³~(½³ë.·ä\x001f¦}JÌÇê8çòX©Ë\x0002Ë\x0002Ë\x0002Ë\x0002Ë\x0002Ë\x0002Ë\x0002Ë\x0002Ë\x0002Ë\x0002ß\x0005¶	ö{Ôé\x0008ðÌ(&ã\x001cjª±Í®Ê1Ù¥&Êt?\x001c¼;N©ç	<Ï6Ç2~Ï\x0016`®M÷Úñò{Öó3uÛðç\x0019}¦
\x0016ûw`\x0001&Æºï*åZÙiÂ;¾/\x00029¯ø+@Qg¦õ0\x0005öÊF\x0000Èº1°9Î6ÛÎÏ·V<k¢S³*\x001f¢\x000e§\x0008\x0006tÞgåóçmÅ³Àç\x0017/
:³êYÀó¹V:×7¥\x0015Ï\x0002\x0007è|%Y\x0006
>\x001f¬x^èzþCçýçúÎs\x0007Åw£Tt1ý\x001cW<\x000b?ÿY¸ÑÏëÂÿÐ\x0017}\x001e\x0016Õ¥é'\x0004\x000e\âè3]\x001e\x0008\x000f)ù|³Ä\x000c¹\x000e×ÔÈqü°Nçs(û°L$Ý¦·ÛtçëSÐY¾\x001e<èË=\x0005\x000bôA\x000eÈ\x0012=¬÷\x0017Â'ü9\x0014\x001bÀ\x000fàÌ6Ðx@´c\x000e]ð\x0001ô \x0001\x001dCûêÒ\x000e\x0016¯øÏ\x0004\x0006¸»Ö*ZÂ¸»Ú\x00100ü\x0000\x00134xÙÓ;ÀÉ¥\x0002 m¯GÚ`\x0010Ï+IÓ¤õ¶¢\x001fñc®ëýËï9ùßþöä·ÿð»\x0002 -Ã\x0000gê\x000cM=wÑðYmÞõÀÞÙJp\x0007r±G¶¥N¸Û,6­hC|ÚØÛEÓ
z¢¶JW}ñ±-tß.³\x001f£¬V\x000fíy×lõÌ\x0005ã\x001bØ%wÔw¡­ÙÓæPò	S7:A±\x0019.mèíM¡\x0000¯|ûüü¢|ÊúÙ¬$mö¡\x001c 2À®mÌ
æxoþîJyZÕl>µÕÇr\x0017Ò6°\x00158uL\x0010ØÇ÷ì`u³û
<pÀé
\x0013/ï>Jsêê¶t×÷¤¡¤Å.>F\x001c¿¤¹ÿGVlV­ný¢\x001e)·ø´m5L?)ø¤\x001cãçÎäÙÂ\x001fºÏ_ñeeeeeeeeee'mG\x00065Ñ.\x0016Û\x0002I8B\x000fy4¤\x001añWÂÐ\x001ewç\x0003¦^`\x0005\x001eØ\x0002ô]ùg7÷Ë9%ÿ(\x0018Ä\x0003\x001f¢%þ[`cgå{sríï4á\x001dßg\x0003Ï*¨üZS\x0008\x0003\x001bO0\x0017(
ÅNÐy\x0000Ð°*ïJE½â¹\x0003ÏDÔ$ªf\x001cU\\x0013ª\x0000ÐuW6iHMÈ
Ð\x0005<V6 s­x\x0006\x001eßw>øÆ3+\x0005<	x>W8Àó;ÀaÉ`µ³W<{«í\x001bÝ}Ë«\x0005\x000c<KG,\x00010ý~\x0003/*%ãxÊØÏn¥i\x001d9õ³A\x001fø`u\x0010c?9¾¯Ið¸ýxÏ\x000bÏF>tÏ¿ïË&þi|ýá7%\x001fÒ\x000fåéË=	\x000b¤\x001fAÓ/Q<ah÷\x001dX#=ñcáÈ!\x000f\x0010-\x0000A9CÔÛ½+U\x0001ú\x0002BB\x0003Dö´^0sÀ;êê:\x0006L:´§õð¾MÄñq£Sô¢-{}÷ô´\x00179#÷\x0018íºÿòËúïï~û\x0000¿wL^úò·z'`ÛíC\x0018\x001d Ñ#:@£G\x0005Æ\x000fü´	O¸ÀÚ±\x0012¼¾\x001d½ûfw@^Ú\x0010ÛF\x001ei¸cu\x0007 þ\x0017\x0015úFo(¾Ëè¶éúå\x0018&-úD7Àç*«c\x000fH\x001bÛ\x00010ç;Í\x0001¡9¶Ñ¶ +¾×º èz~&û\x0001<ÞvZ¡Ìß°Yhúnç;³Ý; 4ß\x001a\x0017@]+ù.¶\x001e³.¤«ô½¼ô1\x000bøk\x001bÊ~²/mu;úyÇ±±çÉá}~ä	<_	x~7gÚ\x001a\x001f;\x00117øí:%¹xº\x001dh3.ÛÈÛ¦ö\èmGÚ±ôÛ3%ü¡3g\x0005\x0005\x0005\x0005\x0005\x0005\x0005\x0005\x0005\x0005\x0005j\x001eñÛqtÅ3u0¦ñ¸&ãÔ¼'=ü¡û±Î]ñ	:¯±Ì´å
=®\x0005Fs¿Â½\x0016ðü¸ÝiÕvÄ\x0002¹§v\û;MxÇ\x0017¼¶Å³Ý\x001757wt«m1 ªÿ\x0012\x000bà\x001cêjR©<\x0002<;7
 ¤Â°êçSçña¾¦$\x0002L\x000b4>Ý\x0003Ïß­¶\x000f¾ñÜV<\x0007x~GÙ\x0005<÷ò	aã\x0002?ÁP\x001feÉCa(\x0005öác\x000f=­?V!²÷üûøÇd$¿ë´Ç§\x000bx~|]½¿õ>D8>`\x001añÑ²¡Ñ2õAã\x000fª\x0000c\x001f¦¥\dR\x000fÛ\x000e³*3Û\x0010\x0007\x0018DgÂ\x0001I\x0003LFWø\x0017×ëÚ×I< ï±¼è\x0015LÂ±Uhì\x0019]£SÒC¯õF\x0017À)åR_×¡ëÒÃðÄG\x0007ôH¸\x0002»ä\x001c} \x001d\x0008Mzô\x0017Ýpis§Ñ9ùPÀI¯Ô5\x0000¼^?iÈO}¡¤\x0013\x000e\x001fG\x001c×eíõ]b¯c2]÷\x0012ª®OÂ¡<Sñ\¤\x00046^ò­w¾mío:cËîm¶«\x001f«]n\x001bõ),\x000få¾\x000fp­Ôj_ÙP/\x0017\x0018H·¾Ø¶Àæ\x0001î»
*ÂÓ[\x001d~ÛtÊ"oÚ,+¢Ý~Ê0\x0010þµÍ¶W]Sâ;´sÎ÷ùò\x0000eà±½J¬ÞkÇ8vìrn×C#æ¹z;ÿXJøCñ¬´eeeeeeeeee'kmý\x001e[ð\x0001ày\x000c­klÓkdL³w3-ã®=ã\x000e\x001dñî\x000fsWlYàq,à9ç¹èh\x0001ÏÓV-\x001f¶À8ÇÆ|ß!oî\x000b&Ü9ö5À³¦ðÆÜ Â5qWQÂq	KÙ\x001dðÌjár-]\x0012J\x001eôç*&Ö¡&$\x0005\x001c\x0002\x001cK\x001c«¡µÕö\x000exæ\x001bÏ}«ícÀóU­Pöªgãv¦kÅs\x000esQç\x0002\x000fLò<\x0008"®»øL'mÿpø]å)\x0017}82÷ô¬¤ö2]~O¿ÿð\x0002ïß¦'1}\x0007\x001ao ÌÀWÂ{°q\x0002f|]FV²¢\x0014`>\x0019 xÀ¿Náé|Xâ®¾\x001cÝá©ïÝÖ
ÚúDß¬\x0018ÍÝÄ\x000f7Ïó¾R\x0013ý²ú7+é\x001c}³\x000fwÙè\x001aíuN¡\x00052\x000fÀü\÷WVè^hekê}\x0012öp·gì\x001dý w9õ^Çcº¦OÐ&ÂÑ':£O×|\x001c´Rm\x0011}qaà9ýfo'äcèÑõËcMÚ³?~©\x001b]r,	G\x0007ôø\x0014\x001fþÔÓ)úvG\x0014|ø½\x0002Ð®/á«±6+{»ªÿ\x000ep\x0019]/sÛ
»áqÝ¬lTùµÚYÏP¥¦uÍ\x000b\x001a7²m\x0000m·c_¯\x0001c÷!µR+­ñZÿ<@qÿ¼n c¯{tô·§½±Yé½ä9Î)¿Ñíë°?o§(%ÏÇ¡\x001fâ]yË\x0002Ë\x0002Ë\x0002Ë\x0002Ë\x0002Ë\x0002Ë\x0002Ë\x0002Ë\x0002Ë\x0002OÎ\x0002\x0008<3´ÅÇ1K84é\x001aù(8ùfúa1Ôt»9+´,ðx\x0016\x0018}w­x~<¯þY ÷ÐÞüÜ\x0013:MxÇ÷Aàùßþ«\x001b¦D/TVSôc½&êTÈâ\x0008sË1\x0010k@¶W0L]QM&\x0012å\x0006·¥W¢¦×*Ê7ùÖóµü\x0019\x001e\x001dj¥\x000b³¨\x00144?\x001aP~\x00058×ê\x001eV-K\x0014Àó;Ñ÷JgmV=gÅ³g¾ïÌwÙjûçÚjûØg¶ÛfìëPê®ZjåhyMiÂ6><¬7Ò¸ÚsQ@8òã¸ÉØu<Eãèñ¶Ñ \x000fÜ.jÙ\x0016Õ°j\x001e\x000eMH?T"\x000f\x001bí2J\Iu¡!3\x0012R¦ÔÏäíyáFJëòvúr~G×È
íòî?L?¤\x000f>§~xÿVú®$¶~Dÿ/ð§À(V7jëj\x000b8ká\x0000iÉ§L÷Õ\x0007W¯^üðã'?üðÃöÍ\º·\x0000¨\x0002U¹l\x001dmûÏ\x000bht\x00062¥Þ©;ý?\x001e0- \x001e4Û}\x0017øüN\x001fíQ:rp©¯¾Ë+ \x0014²æÙzïéæ[ºI¹º\x001fÎS¹Ôfî±\x000fuR7:u½®¤Ó;Òø®¯¶SÆÆñ/_È?¼>ùñÇ\x001fN^¾|Uur®­¶±\x0019:\x0015¸8|lJ~tÕX~¶ã#U\x0001tã»Ü\x0001é£\x0003úGwÒ\x0000,}­tÙs­°E\x000f_@Þ:¶-­\x001f[ô1ðÌVÛ*§í {m6ZöáÇ>fÅ+=p[\x001bU·Áå	2_°Ýõø3v|ñòE\x001dWú\x0012î(U\x0016ÇnÚ¨XëÙCU¤ê$EÂ¢ô=V¨_]q\x000cC
W?¼}Ù:[«Õ\x000eÚI­ö\x0000ù\x0006ã}lÕ\x001em£}I¿\x0014µÝrÌÓéülíË}\x001c88.ÒN:öó¨¶õfËnßÐ\x0006 ÕjO<&Å¦ÈÙ¼déyãìL^4[\x0017}­8ç<;\x000e #jÉ\x001e[ytÙõÉ:\x000c6uéçógÍè`ê#ß\x0008\x000fMúÇhøC?Æ¿ò\x0005\x0005\x0005\x0005\x0005\x0005\x0005\x0005\x0005\x0005\x0005ô¬Ï°ê>]Í¹\x001e
ôxq\x0016ã\x0015çÍ±%qÏ\x0005¤Q\x000cp8öÔ²J\x0005ÝïyW|Yà±,¹ßOéÃ¥Ó×Ö3Î­µÕö×\x001arÿj\x000bä¼
í\x0002Çf»\x0017´\x001d_ái¹g(¯âæ?ýÿÝ{s¡»\x0016_\x0005\x0004|®û\x001bw(ù*¢ ©&\x0011\x0015pª\x000bó;+­iSGÑwpV(79\x0004\x0004`l\x001c¦n&Sj3a9\x000b0¡íIí\x001b\x0000æ\x0002tÏN:ÝV<\x000bT\x0000p¶×d¯@æK}×\x0019zñ£@g\x0001Ïg\x0003x¾Öd$@õµÊ\x0018p\x0006,ö7³ê\x0019\x0000¹»²\x0003ZXbxMúÓÏ\x0007Ä\x0004`WKÓ%=åp\x001aô¹8\x001fYwÐÇ8^®_[Q¿õ\x001f]3-Ì!7~,aÆ·,\x0005\2åÍ9ËNÎC\x0019¤\x000f7FB$ZGxx mÌ	K`i¹	\x000eÏCP*íþ!êøG 3#cM\x0007¹rso±\x001eðU'¸ÍRàÐ\x0000t½\x0004l\x0002,\x000b8ZT\x0019ßL~\x001f
Ð(ÙáÝ\x000bM_\x001bgÆ87òýY¸\x0000\x0013\x0012°\x0006¨ÕÓ¸§\x0008\x0002ô*7\x001aYúD¿è\x0013^è/o<\x001bü\x001aúJçZÑ)\x001eô¯îp]\x0003CUÅËU\x0005´©nV\x0017\x0017x\x0017P\x0015¹]Oé\x001d×e}>ì\x0019½öúG×|é\x0015=KGôãO:\x0003z¿zù²@g¾ç\x001b\x001b¡3º\x0017-\x0015ïyÖÑ¶,Ý8~ñU\x001fºÚ\x001eI\x000fÐûî­@QR9ÿ0ºõ
\x0014¡|^"\x0007ÞÒp\x0004 ®\x0012uß\x0016­¶nvãXÊ\x001e\x0002d
nf+jú(\x0005á¶³
h·ë­Õáðíx¡\x0013/\x000b`»¼@\x0010="g\x0013\x0018ÙØ*Ê^£Æ+O¹õÏOx«@õC¿@ðV2ßd¶Þ¬hÎ9å4µ²£Ýe*DÈ\x001e^Å<ì9¶Ë.À¹Ú¶ú|¡\x0008ÊP>À®Ï3÷:N±ñhCÍõhtË¹bZç©Hõ§\x001fèTÏYÔ£«jCé/\x0019\x0007T6A\x0019ÊãõSÇ'çY%g\x001e\x0015Ýl~XÆ§\x001c<C\x0016ò\x000eË\x001f¦},ö%e>&så/\x000b,\x000b,\x000b,\x000b,\x000b,\x000b,\x000b,\x000b,\x000b,\x000b|\x001f\x0016Ðó>ãûrÛðáPh%krk¨Â¸(u\x001fILNh\x0018Ð­Þ\x0004 	\x001fá_IË\x0002b\x0001ú®|-<z
\x001f¡\x0012W{ î\x0011j]U,\x000bÜ¶À8¿¶{Å#÷=í|Gús\x0007ÿÿõ¿\x0013ð\x000cè,ð\x00199¨Ôì½nZ\x00065éGVÉÝU6Efç¡lÅÑáÈ
«V\x0013S&AkUsÕG!ß8kB:¹¹jY3E\x0001ke²´*àYEXùü^<§\x0000ÏÚbõT+.|}r©U[\x0017¢\x0000Ïgµâù§S­«ÕÑDÎ{É-Zr-\x0015Ø\x0005@×$¤õ¯¶¤\x001dÕ&§¸¶\x000b¿´ûL\x00069{/\x001fÃíú\x001aVÍL»z{vú×±òqÜåÜot_E³?,ÞQÝ(g²\x0013²n×}ºD\x001f-Gôí[G{¯o+ûy²[ÁÏ\x000eJ	N´åîÅ\x0002½Ü²ê¸\x001e×un¹.]V\x0003P¼f»ßú^«À½\x0002Æ\x000c@e+\x0014à\x000fp|[6\x0012t-\x0005Ì/K W·fp9@àV¿\x0002¼¬d@l\x0002g.¯x@©\x0002·\x0004oU;ÕßÕ¨¬n-`¹VzhéZº£ëûZ¥ûöW¢wÉºw\x0018ÄKÝY)
X®3N¸Àµ*3Àh#Ç \x0018ç¬õ3X¶]\x0001xº\x001a\x0000÷å\x0002ç6\ÙÚÅ]Ø²¹§N\x0010×¶ÝêTWñ
4\x0015xÊl\x0015³N£|x+};ê\x0000îèf_z`+éBØ\x0000¨}­v\x001dàggV`\x0003ú=ê8³B9ÇyÒZ\x0001.¼³¿TCI÷\x0017Õ²\x0011º´p\x001d×z¹aè¡ün\x001fën\x0019È¬vJèÖgÒÿ~-ëå\x0005õR\x0006Ûå{ÈCj\x0011ó×éèÁ¿mg`\x0018Ýe»v¬\x0001ÁcWëjàóêÝÛ_NÞ¾ûE«×±Èc¿´?)\x000eE¥»û\x0002ýÕa3â\x0019Ç!Ç{{É@²Ý¬&·ÅhSµMíØtN;_
/¬ðV\x0017\x0002ü¯ºü\x0004Yå·²ÃVÈà87NZEze£tÕ9\x0008ýLÊÇÑoÑ»sn±ÞJø²·­eeeeeeeeeel\x0016Ð¢*æ(F¡\x0019\x0019Áð\x0019vò\x0013
ý\x000c!uYà^,>\x000cMø^\x0004\x0007B8¯rn~\x0007j-\x0015þY`[¯ìÎ±\x0003<óCýUy·ð´Ñ§~úÿoÿæF»)\x0016è\x000cø¬YbMvÊ³òH¬Û- UÔS\x001c\x0003WhÜÇÂÈ³Nµ>¥®	LßUºJ°E·Ý¤ç¿`²Yúð^\x0011%à·ÊéG§À=Õ$´fµ2Ù[s³Îø
/Û°ÕöòO\x000bt~qr&zñÃ'¯~,zþúµW<\x0003@ÿðJú¨ÑÃ¿×d+q\x0003Ú^ùlà9i¦´%`4m­°¨\x000fSk\x0012.µ#ç&/hÄrË\x0002Ë\x0002Ë\x0002ß£\x0005tÙ:\x0006³\x0014\x001cÃM.áP§Îß-}\\x0002É{wõF ­=@cV²
2[P\x001eP|À ¯ZDÝ\x0003\x0000A/´\x0012·h­$ÕR]ç\x000b\x001c%\x000fR´¶g,¶FA´À"³)Yÿºï\x001fðÔ2ÐÍÛS{5©ÀJÀQVmÖÊØë_Þ¼9ùå÷¿?ùå_ªM¬V\x0006¸å\x001bÓñÒóÅåÉ\x000bô/@uèLÝ9
ØÒ@©¨ôÀ\x0007Ì5h
kÙ6\x0014 [ñ±6¶\x0005¼'
U÷ ÄÓN¿Û<uä\x001bÎl¥\@sÙ\x000fW .£Ê@«¬Â\x0014ü?tt\x001f1ì\x00066\x001d¥ïÐ\x0019{\x000eýr¬\x0003<{Këë:ÆèÃqåø¾ä\x0018c?l'\x001b\x0016U^m	ò¸Í^ê;¶ë¶.\x0006¾k{q½(ðVÛsL\x000f\x001cm¢z\x0016¨\x0015Ë²\x0007zP\x000f+ëØb+ì­j«q×\x001d9Ñc¬Þ÷l³Øzì·²<Iè?v)À\x0017\x00088Ãû\x0005\x000eÅµ­vø\x0000Ø¯®ß¼yû\x000fêÿ ~ÿ»jëFèjZ}¯Òô¼T/>äpÛó"DéupÜRêGwâ
§\x0001	¹[ê¸p¶4\x0002ôõc®KÜòL8,W1~¦"=¸p 1UÂ¡¬\x001dóè¾ü\x0011´,°,°,°,°,°,°,°,°,°,°,ðÍ-ð¹c½Âkì³·È+\x000b|m_þVz¬Þu}ÌB+ÿ¡- së\x0018èjëÔK?ÝÓ0)}\x0003Ã3óNÿBÀ³>Ç·mµ­YoÍ|
5Å+Ì´êöãÛ\x0004`¡cz{L%6\x0000è¢æ3OÂªS³ªçR«\x0000ÐL¤Þ(\\x0000DÐ>À]Í\x000eàY+¯4á{-|\x001f\x001aÊç+é\x0003½Ñ$ê©&¦\x0001\x0001 \x000bt~õgy­zÎgçÎP@qÎ\x0002\x0005BgËí
|\x0015?gÎ\x0001Çi+Îí>§]2ßå\x0002Ë*ëgY`Yàû´@\x001fQ-`\x001alÇÂ¤qí¾+ô«ë·\x0002ËÆç\x0002DYý8Á³\x0002K¹þKV<å:p\x0007\x0008\x0008(ê­\x0005\x0006\x000e\x0010×é\x0006	\x0001ÕUà¶@Î\x0002^\x0001Ç¸ÈVdü¤¾ºÿ¶\x0004è3õ·\x0001É£g@¿	¾+½».Ño\x0003Mùf®t.0S÷4tí )êt\x001dz\x0018\x001dS·é\ù\x001a½¬+`³í\x0018\x001aº¨ú­ç\x0000\x0001Ë·4ÀIÝGÍ¢\x001fº¡\x0003.[\x001cw»Q\x0017~¯câèØó)\x001bý:E¾u³\x001e¶mvYß\x001aÇ9:B#\x000fY©ºý2Ã´]·\x0015|ÝuyØÀÞ6¢nôBä¥oÆ.Ý\x001eI'rS\x0017q\x\x0012îå{;z{X\x0011^6UÛ\x0000nÉ£\x001cç×»«ß\x0016è|uýË8o\x000c|{+÷´GtÎ´£Ú0\x0000tÊÄç\x0008à¯v©Ú~Hå|ª_[Þ
.\x000b,\x000b,\x000b,\x000b,\x000b,\x000b,\x000b,\x000b,\x000b,\x000b,\x000b,\x000b,\x000b,\x000b,\x000b,\x000b,\x000b,\x000b|ÿ\x0016`Oþ(ø¬ù¾mb0s¡i\x0019qø\x0006MòF5ø\x001fþÿ¡çsUÂw\x000b.\x0006pÖd&°*uW\x001ay[Hð\x0019¦DËdüÍ[\x001eYÅgàù&¤_P\x001f\x0013¨TÍ+U¡w}=É[Mú²ê¹V<«¼pÝZùÌjç\x0002ágõçS­:ÓVÛ\x0017Î¯^	þáä\À3ßx¾Ð7\x000fgÀäÏ\x0006'ð\x001cÀyPôÖDkÐ\x0015æ\x0018fvK§KÍi_^ß\x0008P?0´\nY`Y`YàÛ[ \x0000X(\x001aõp4\x000c \x0016\x001a°+×jè\x0004\x0018Û5\÷\x0010ÊÏ\x0015òF+y]H)%:ò$Üë'\x000cHæí~
²Ê4Àdh\x0000´ÐÔ\x0019v\x0013>Ô}.çötÑ·\x001a1~Ð\x0015\x000f\x001eµjv¬Mzt\x000c?´ëz¢[â¡þþ°uªª±qÙv]/ÂÑË4\x0000¤W¹Æ\x0005@¢»<«y{\x0019Â]\x001fì\x0015%l:=\x0000ï¾]èBZ§c\x001bo;n½\¿í\x0019]à#\x001c\x001fùÈ@¿èÄË\x0006Ñ+wô¬¬¤§lt\ÕP}cþâs\x000c£OÊC©'\x0014Ù©0¼½ïe¢g§ý÷5\x000eåè%·z)àzÃ[o#_Ûfs<9®\x0003d&\x000eà¬g\x001f¶ÏÞ¶}Õ|9~t¬Æã\x000b}lï°ÓrË\x0002Ë\x0002Ë\x0002Ë\x0002Ë\x0002Ë\x0002Ë\x0002Ë\x0002Ë\x0002Ë\x0002Ë\x0002Ë\x0002Ë\x0002Ë\x0002Ë\x0002Ë\x0002Ë\x0002Ë\x0002OÌ\x0002\x001bàÌß~Þo?çG¼§)\EÞó°ã§ÿþßý÷\x0002µ\x001d©¸YÝ|.Ê
hÂµÍv±
^°\x0003\x0011\x0007ÂÅ¤\ÌÞzÒáÆä:,Å\x0013zzr)À\x0019Ðù\x0000¬xÎö¡\x0001s\x000b4×d©f\x001bðìÕÎYñ\x000cq¥\x001ajÅ³V$é;ÏÏ\x0001¡õg¾ñüÓÏ'ç¯ô\x001dhM¸jV¸èü¾3\x0000ó\x0004kÅ³tinW;c_åÑ¦2Ìl#À3Ûl\x0003>/àã½Ü²À²À÷f\x0001@1Ü]\x0014`+.à\x0018i\x0001ø\x0002îyu±ÁH¯0í  ÁHa\x0002\x0018åu)\x001fÕnõ\x0016§ë(\x0019\x0001ó õ½YÑ\x000eôõ°y:Py\x0008LÒ®èÛuEÇx¶w¶ÎÖ?më Þ1û÷ªf¶ÔöJØ¤Æ¦½\x0000¤%l:Ê:\x0006\x00026Ù\x0019>ê«ú°!NéÝäÅcC§Oû\x000cå÷täàb\x0017è´V°ëû×e?Òkù\x0004»\x001d½R\x0007í¾_¾ÔÚ/_=©²¡»ïö±^³OfEsxÈ§lÙNíØ_¨\x0017z1c×ëÔ½°Slu\x0017èLèF¹Ô´.3i\x0015\x000eç\x0000\x0000\x0006cIDATáv»:>í\x0017ð>ü)\x001fJ}q§§z\x00129¿ÞúøÈÂÉê\x000fùÆy^ÞçLúH?gJRÉ«®Ý\x00196ËÈHdÑeeeeeeeeeeeeeeeeee'a\x0001fúä\x000fW\x001aß¡yæ Ek°Å3\x001f½QDïôÿüÿÍAg\x0001Ï¬<V:ßz\x000eø\x0018 Õ\x0012W]¿uªÔkÎpoÀ³d\x0012C\x0012ú9­¶_j\x0005Ü\x000bÁ·çª»¶d;SV
Q«ØWß\x0007ßxV^­\x0013Aç±Õ<L>½Ðç\x0001<_¼\x0014èÌªg­x¾øùçK­x>g«mt\x0018à³e\x0001Îª\x0007 y\x00035uÛ·Øv­A:î@Ï¡sg¾ï¼ç2ÓúY\x0016X\x0016øÎ,\x0000(\x0016×ÃI\x0006ä\x0006\x0000ë`Y@HÒðÄ\x0013\x000e\x001fåÎ/\x0000\x0018Y­<\x0001eêôË	.ç»¹\x0001ü\x0000Ê\x0012\x000e\x001704qôìú\î\x0019Þ]¯wú®ïôÎ§\x0001'\x0010ØeN°Î -ñÔ\x0001ùJ/2½âå&­í. `·a\x000fc\x0017â±«©AÖ¤\x000cñÔ\x001ftøèWºè¾s\x0008,\x001aTìvë:£;>2ºÎ	rÔé\x0017Â|±\x001f6\x000bh-À9Ç¼ëÝe\x0010F©Ó´% =öÃ\x0007\x000cFNÕ;ú\x0015ñÔ1i×á6Þ)\x001bZ6TÃ ÈÿAÞx©ç\x0002ÀnÒßí\x0011}i?>`
  
  
  
  
Instances: 1
  
### Solution
<p>Ensure that application Source Code is not available with alternative extensions, and ensure that source code is not present within other files or data deployed to the web server, or served by the web server. </p>
  
### Other information
<p><?=FydSO¬ìï
û-ÙÉßyê¾Wz¬¦ý\x0014\x001ez\x000c\x001eåÿ~Þlî7ëÙýÜFâ2<~0<ç\x0005^Lª\x0017Pò\x0006w&Ûwå»b@û´-Ä±#µ{s\x001f½Í§\x0003zW5GaõËOýRÀqínæ¹®í2ÞÔÎç\x0018£1<·K]ç¯ô¿\x0014Tá%umGT8å</p><p>ôÕÒr§Aj¸ÚÈìG§1Ö«U\x0003\x0001
ÔÎâ´ý9QÜZ46]m{/\{?n^Ã»×½\x0016\x0012¿t2§\x001cñz\x0013r]YÍ#$Ý°pÛNx¥ñéH¸­¢O¿8[	4>o#>D`ÖúíÙÎHMðö\x000c¹=1Â3³íER\x000crÕßÉ¸Gg½\5°j`ÕÀªÿ¹5Àü`Î\x0011ä¶ç</p><p>^5<+®S¼Q\x0008wùjÞKæT5ïË:\x0018ÆÕÿüù2:?ÿüó\x0011¯¿Áó\x0019\x000cÏ1à=\x001dÃ3Æ°ûcd\x00032§ë¹\\x000cy!¸.þío</p><p>b¨ýÉ³9nû§Ïe9þÈÄç8\x001eùJíN~ø\x001cýÐ}E÷\x001bßøzÅ_/#Ù¥¬Õ\Î¼¹#g\x000cÚÀ^zqóãg
Íg7ÏÇ¸1û÷¿-þõ\x0018î®ÄÈcï¹+·Çb(fkxæ¹\x001c¹ýÈ#¯W{÷ò\x000b/l^Ê\x000eïct~ååëxdëÀ\x0007"ßÅðÀiÌ5c¬øCü\x000f7\x000feG/G\x0019>þÇ\x001fß|éË³ùr\x000cÛë^Ì/ÕT\x001b+oÔ±ÞßùÎwkW2;¯^íc 1\x0004ò­è¯|%Fï¯|¥¾ïûË_ölvùbLe÷/\x0006ÕûîÃðü÷¿ÿûog÷îßîk½6uðBäîw¾ó/\x0015îõÓ^{ÀM\x0019ìöÅ¸ÜµÞ\x000b]Ôg<óf7¡aè|öÙ\x0018ùcèÿÙÏ~,¬'ôÂÕ|*õþìÄÅÀÌºZ\x001b|_\x000bÌé²yXéõâÃÒù×¿Þõð¯<]G¶cXÅÈJÙ:è2v}\x0000:¯¿\x000e½×ª\x001d¡\x0007üïÿ»e±×<]ßs\x0017o\x001fAý«\x0018\x0013¾0öú#/\x0014üëý\x000fñÿX\x0006ã_Î.ç_É\x0007¿¬öPm6íõ×Ú¹
è	ÙÚ~p¹\x000cÊ¿û]»
.Ýº]qä6:ÆcDn~_	¿¨6ìZÈl\x001b¬[b`ç\x0004äuþ¦ÁÝãìÇ£?ðçÐ%ï[±QÞ{ï±FqÝÎ\x000f¶ÿÜ'ób\x0004r?ýôÓÅ²\x0000á_O\x001d¨wÚ\x0012u¡ë
`K|ë¢7ñio¨u¢ó\x0007!I­ð¯J\x00035cÄÂ)¼íkBÃ{xs=¹Ôv\x001eqèÿö¿htÆð\gFÇ\x0000a-x\x0018 ³È_á,\x0008fp»\x001dÎc0¾}ï=\x001fdàMËßÜÌïf\x000cÍÀë¹]g'Kv¸`\x0018cñ_\x0010Þ\x0012ÕÃ\x0018\x000fó¶Éá\x0003\x000fn.bÔÎ`~9W \x0019\x0008ßy\x0006^Ïîç·Óißÿí7sìb\x0006º\x0018Î¾QQöæÛÍ1>§#±Ç#ÀñÂëI\x0016.oÅèñùøâåÍ­\x0018ãoå{ÌY\x0005ÎIsÀ|G4þÂâ/\x0016Ä(ÖFÊ\x000bµ\x000eNÑ\x0018Õ\x0016Oç]|Ö³\x0000\x001c#mÁ\x0018U2¨ô÷\x0015Ù-µ3Nñ¦\x000f\x000fÜüë&Á£v¬F§\x000e(@\x001c:DoàÖ"90ºèXceá\x0017ñAó\x0002F3<7b\x001e\x0008â©k¾Y\x0000^ÑÃàÉ\x0002ñG¦Q2ØÁzãz\x000ffKtå?+l\x001cr\x000eÄ\x0011Ös­Gæ9ØVæü\x0014¯\x000bsð$\x000cï!e\x0008¡OX\x0018Êa\iC¹©`D\x0005^_Â@\x0006û­>¢\x0017\x001e°0:k|\x0016\x0012_¤\x0016«ÐïÂãÔ}É@HÚÍÐ¿1n*ÈZÆ@óÀ32\x0015\x001fKÝtY%qÉCSßÈVu\x001fj±äÍ\x0003Ã4k\x0010.=Áu\x0011|rLö\×M±Â]bça×|íd«]mïT|Ñ%ý§yêÑÚi½´Eå±|\x000c:;é>yåÁ¬ô\x0019\x00186SV\x0015I©Û6Ôq\7¥ú\x001dáÒÊ¢ huMl\x0019Eh+ñ¸BÍ/õº36·q\x0003|)\x0003Ùzìë:s\x001c<V¤¨+\x001eÞHÃ!¯z\x0010Ê\x001f×¥¯E\x000e+wå.\x001aütÞÅH¶­Ï¾æ
¼öo\x000eûÁ¤\x001fÖì{<üÙGÚèÜ::­\x0012Ã\x000b:×ÓårÌn\x001béSö\x0005t8ùg|¢ì	\x001d·ºÓrÈoXy'=â>YG% ü\x0002?ÙÂÎ§NñqÑN\x0007Îùe\x001cX\x001apé
´\x0019çuQ©mÚZ·ø&iê«*q[ä6`â\x001etvIÔßé\x0017.,ã4¤^Û\x0019¿£Aö§pÐ¬«=X§HU¹\x0019GÒæ\x0018]cò2^\x001bv\x001c.º\x000bÍ¦a\x0019~â±¹Û_Æ
\x000cÎômÆÀ9÷X¼Ä×8ðB£è.?[cwÆEÆXy=õì\x0010þ½\x001cåhiúW¹©îQ³8F5ÜCÝçû\x001ebÿoåþCK[ª\x0003Ýµï{ñ\x0014_}sé£õ²	\x0010¼ ´,F¼]É	ÒöÅ¤»ò,X§\x001eäy\x0010\x0003´^ý\x0017]Zîö~nx\x0006à>Ë¸Ìç\x0003ú\x001bL@'a¼,Ä8Üßtæ´¼XÈ\x000eh2þ\x0016ïË:¤;!æ.¾U»ûm»\x0017õXTi\x0011~µ¨\x0008</p><p>e¡·P
]ÆÓ\x001eS\x001baý]5ðÖ@\x001aå¹÷¯9$¼mÐ{ñ[Ï¯|ç¤ín©T Ð·\x0005&jÁØ¿>+î,\x001cð>å.ºùlJQóC</p><p>Vè³iýYªö|&ÎO9¿`Øk£úù8kÊªU\x0003«\x0006V
|z5À<¡½wÝiN\x001bwáÆ«yÍVìË\x000c+1Ò1Ñ¸¬\x000feM®æ<ï`x~þù\x0017cÐ}aóÂó/Kç½Y[ÇèüÌW¿¶yò©§6÷fÝ½v\x0011ß{OÖ³á#\x000cãÙðR\x0018~);Ù\x000c|)»ñÒ+e<®5¡K1\Õ|)kY£½°ù»¿û»Í¿ù7ÿ¦v¤²ëù"ù0/\x0016·ñùýÍ1\x0014û\x001dcxüc\x000cv¯ýñ\x0018å^¯/g\x0013</p><p>´1</p><p>\x0017¿Ï|uóÕ\x0018s\x001fâ:ºøÀWýêæ¹?WßYÆXË\x0011Ë¿áù×¿þÕæ\x001b_ÿÆæë1\x0003\x001f±ú\x001e\x000c9Bùåw¿û½2ì~7ÆcÅ\x001c±ö±Çb4þêS1ò=½yòÉ/EÝ¦\x0018NÌÂ8Èæ_eGõ÷¾÷½¢ÃqØì\x00188»»|[úé§Ú<\x0015ÝrÍnld}ñÅÊàìQÛ\x0018{§ávBý\x0002Áýþ÷¿We°\x001bù0u\x0002Dî>òúËõ­ç¿ÖÁådÀ++=\x000cÝmx~6»º­\x0013êåÁ|âÔo7³Ãï\x000eû\x001df¾»Ý\x001bRÞ-ý|ë[ßØ|óÑë×©6C»¡=aàîvu\x000bæÓÅ\x000fá\x000bÑÙîxqv>ÿ:uÆ\x000b\x0003\x0018^1\cønÈçûwNBã	<ºî©§^\x000cÏÿ:FØ/t;OûyþçÝÎÝÙÏZ%ÆcÚO\x001fO½û¤#åK~¡\x001c¼\x000càqâ_úÒký\x0000C6ß\x000f3\x001dWèðýìÝÚ('µýêWmPG>Oq\x0003²þ\x001bßøfé]êMï7E³OzÃØÜÇû­jÚèC\x000fß»yð¡ö´'vüã	ýº\x000eã\x0014:°¿Ãµ\x000exÖ]¯\x0017ú³B?ë§æYáª\x0001V®Nû©\x0013Û×÷ðN­)\x0004g;±Ë÷Êûß³ã¹\x0017=1@×"X-Å\x0008\x0002ÄÓ 3 ðMæË?Ì\x0000»Ä&+ve\x0004=Ê\x001b.7röþ\x001c+±Ýù]'ÜPë\x0018C\x0016ö²È·[¤0ë\x0000Ü\x0008/\x0004^Ë®ç«ñÀwßÑùíÍÉ;oå{Ñ9!\x0003Ø\x001bñïd0¸\x001cCÖ¥\x001cå\x0008ÔÃ¢-ÆØë¹	ß¡÷(7å¡1\x0003\x00060ÖÁ2<`tñ9Ìl\x0008oâ\x000fr3e×öA:äaÒ.F®\x0017cggA\x0014õ\x001cFyh©Öq³È\x0019¶¾\x001e\x001ex\x0018\x0008\x001fìÂÎ\x0017\x001fs\x0004xøIç÷
	\x001d8¨.\x0006³-ÄÁ\x0003ézÊqÀ`Aµ\x0016t\x0017C)iz\x0007+òCA\x0007è`APzîRÕ0\x0004\x0003¼7úí5v¶ÞíräN>»ÒbÀ\x000f?êµ\x000cãã<ò­\x0001</p><p>Þå\x0005\x0008z®§ßçÃr¥WþN§F\x0017\x0019R±Ö¶\x000fNèÙ²(¿\x001eÄ\x0016}z407TÂ,(Û6'ÏÕ\x000b¼\x0006¤<Ë"L\\x001b\x001b£/^\x001cÀ·ñVÂ¿:£LwqÙnf#Ï\x000ew÷°@Üt]»vd{Ú¯gó\x001f^5dò\x0010LYð WWò¥\x0011\x0019\x001aûô½VFy¶Î¸îÝÞiéëàO\x0019\x0008OO\x0019¦·¨§å%\x001dw|Z\x0008\x0010*Ù¤Ü\x00183àcö\x0015Êá!¬ÛW^âYú²Y/ÐV.\x000c»\x001a¹\x001d\ñ&$~Ê§¦Aû,\x001aÕ®Ò} ö\x001a\x001eÈñ´_ßF\x0004*«Pº@ÊåM\x001dÌ>Ú\x000f\ý°Eùê\x0005h\x0004Ò>&Üéæô\x0018(\x000fÈ·\x001f®¿ØO*Ú\x001dcugø\x0015|[AwjÛ"O}\x0011××ôõÆH(4s~úDHò¬ÿÛÃô¹¦q§_Ë8ÄÍö]´C\x000cr¶-ËkxvY6a=e\x0019ÇÚ[¶¾Ü§Ó\x0016i§ÀÝ½þÜß<·
\x001f=Á-Û'm1>ìØfpÊÒáÝ=\x0002\x001eKbÓà\x001d½À÷fÂÞ\x0013v:ã$\x0012ý÷C7ÂcÓvL\x0000ÂPö¡és\x001cÖä\x001dëxu\x0004´ÿ#\x0003aÚNË\x0017\x0002sOã¥µ¾¯ú"</p><p>/xõ÷ ËKQ\x001cåÆ\x0018Ô÷Ô»6w_»+f¸\x0012Ïw»v÷û¢ËèF»8âÑGïæÙË²z"ÆÃ[5Õüô§Súèmê°îÙ5î6ÖrSç!\x001e_í§2w=Qd\x0019¿\x0018\x0017y;¾yª¼DPÃKÞ</p><p>s´1º\x0005®nÕÀªU\x0003«\x0006V
¬\x001aX5°j`ÕÀªO\x0006\x001fôÚ_MM"CÏ\x00032-)w\x001an'\x00045Oj\x000cfÄë;vÖ\x0006F^ÖvnÈÛ9¾ú\x00180ì8mÃ3F¶\x0018¿úÌæ«ÏÄðüå§zçj1¾µqÖ\x0014·j0äxæ>¢ù§Á¬pÌ»ÚXxµÖhkºVùoÿí¿ÝüÇÿø\x001f7ÿá?üÍO>9NÏsSÃ3;;1\x0014³ãøG?úa/?vÆ²\x001bøÆ<±uÑðgbt^Í\x0006>ý\x001c¡]Åìåøhx|þù/Ç\x0016·áùßüV}ß¬o\x0001cüÃ\x0008gîüÏÿüOÿþßÿióOÿôO5\x0007ëOÇ]\x0001öóo|óäûZôót­¹\x000eÆQÊ½«õUÎ÷¿ÿ\x0018¿_Æç'x|k\x000cçXe¿-1û¹çräùÏ~V\x0010£(uÃÚ(iÿ÷ìxþû
Gm;W\x0006blþá\x000fPúá»Åsí]¯_Aþ¯~µ¾¿Ük
q?ºîù¸§</p><p>öü\x0018¾}öÙò\x0018YW&FghA\x0013ý¼\x0018C/Æò²#ý¿|5:þMª¿©úþö·ÿvó¯þ\x0015ßWþFÍ±Ôìâë	/ô\x0008j ;}9z\x001cÏ:#ùõ®3Ï'­ÛÆ6?þñ·k1¬\x0015Ð¦þá\x001fþ¡<G³\x0013ÿÙgÓNã)£OO{¯ôLxê]Ï\x0018ÖÙ\x0005M{ã\x0001<ÇÏõÍ~É¡wv#\x0013\x0006r<\x0006óØqêÎuQ õ!ûç?ÿyµkô\x001dÏ\x0008ßþößåo\x0001Ü\x001dßs-\x0005{\x0002rC\x000b\x0019î½ïêÖ#\x0003mocxfM\x0003\x0007ÔÓnÐù\Ã\x0011\x000f\èÛG)³×S®ì=nìÖ¬Á_ÝªÖ\x0000mmú©\x001e£ûÞD<×ÆíáÝÉðür\x000cÏìàÅp\x000b\x0008»cRH°=Fç´î­Ño3OÃ3,bp>áù(°¾Ë)
\x001dÜÜØåQÎâ®\x001d\x000cÏ\x0007áùbÞ<¹£\x001f®å­ 6<¿³ÙÄè|òN#à&ýz)x7çKYÄè|9ÆgøÆÑ±0<ßÀð\x001c\x0014éjv;ss?È5Ë\x0018 \x0018Ûèñù æ­ñ9×mp\x0011:;û\x0001bYx¥óçfoYg1À'1:`ü\å\x0013±ïN\x001fåf·\x000bÑ\x0001\x001eÇÀáà1o\x000eÜ\ô\x000c,ÓAÅr\x0006ZÔÍ mÚ¤n \x0005}ýþ`e>y\x0014:È\x0001Yð¾\x0019ßGC7ÿðE\x001aeè\x0008O?eÜ\x000fO>ÈC:Ðxo²ð'OÀ¹Ø=ãå\x0007(½Y¦ô£\x000cÓ`¿{ ´-\x0003ýª[à,üÒãF<of³ìÉ;á©ÓÒëÒ\x001e mYk\x001apÖ\x001faù\x0016R\x001e~âÁß¤¡N8ð3\K:ù§à\x000c£/ßâ\x0002R¶\x000f:¶k¯§Þ)kòhYÐV&áÆµÛøè´á\x0019\ðf\x001eÃ@×uqÆ\x000f<Lg>âÌk\x001crÃ+PÞ¤O~Õø^Gé¥O^è7¡eìËhYÀé,\x000f¨_\x001f\x0010}Q@£3º²M++t)Bù\x0000Ê²ÙW(\x0007 Ú\x0005tÛ\x0000PÙ÷!i\x0013rÕeÉË>_gp>9\x0017}×
\x0016½wûúäÊÚéÿ¼2>ÜûºÚ¿6ç|Ò¢à' ÖäÓº\x0014vù»¾zÖ5q¸}Þ¥\x0001´ïL\x001cÉ?úU÷[ûýÃñßxàtö5Û&íÖvLñû\x0010\x001aSîy=yoàä\x0001þæµéä%­ùî\x0017f¿óü\x0005Þf¾nÏ}_ò\x0013ßrt\x001dÙÏÕº?Âz^Îáåµ\x001e»w}x:dT¤<\x001f^¹SE.nýÔ\x0001t».\x001bîxÄðÌË\x0003¾ð×;yY\x000e#4µO></</p><p>Pv=£æù´N\x0003)}q\x000fiÈJØç\x0003Â]v§Óòð\x0017j;yI\x0001G\x001a\Ïºïp^¦©gíÓÏwà®nÕÀªU\x0003«\x0006V
¬\x001aX5°j`ÕÀªÿù5PóÌ\x000föaùBO(jÚ²¢±UÉz^ùF­%ßyLg]¾Ó\\x001fb~Åçw6?\x000eC\x0018>»cðÃè\x0001
Ãó×¾öõòO=õônÇsrÌ\x000bå\x0007|~?þq\x001b,ÙíQ\x000c\x000fÞ½Ù!\x0011õ<s@¾[üïÿý¿ßü»÷¿ÁÏ5fæU¼TÌZ&ó.võ6ý\x001f³¿}ÛôSòBó}ÙxVGaç\x0008d¾Áa\x0010C)ï%ÿ]ØîÌÁ\x0016£-Æ=tzòõäKu\x0018\x001c9Êú»ßýNmòd¬G\x001f}¸
ÏßúzÊnjGoS\x001a£ ;ý®ô³Ïþ¤\x000c¹è\x0007Ã&ßá\x0005òMjv%ã1tbÄøÇøÏú\x001a\x001eã¥ßxþÖÿÇÞhYq$iúæÎ¾\x000bJ ÐT©>§§ªfy~y«îêê®THÄ %;bÑ\x0006ä>ÿg\x0016ÿ
»ÁM¤î\x0012s3\x0011ài\x001e¾{¸_÷?Ìã½÷¢OÐÞ8ÀßÏ?ÿ|ðÅ\x0017_\x0004Èîr]:3XXÀ";b@_ÂÇ­çáã=\x0001ÚßÀ3Çm×ô\x0000Ù8ø%èüuèñî]@b@Ô\x0007\x0001Ü>
\x000f\x0000z*ä§m¨\x0007{ÝÏ{\x0006(u­ÁNöû¨7ý</p><p>Çý^a<am.Jþ4\x0002þ5<à3}¤î)ðýpú÷ß?¾s]gú÷D8>ÛVÂÔ}LÀm\x001cmG\x0016õ´®Ù¼áO\x001eú;r³\x0017À5ý^§\x0003 ¯êG}©\x000fíkàv¶C^Ú\x0000\x001e=\x001a//\x0000H\x0003Nû\x000fe`Yã%:f~×n½h/zâÄñ!ð\x000c\x000f÷\x0013Ëí{ø¸? \x0017\x0017a\\x0015xæÞû*´÷Q¼GC|õ\x001aH
´ûcì^*µ¿¦TØ¿\x0005xÖV2hR	O\x001dÎ,\x0007ø\x000cà<§7d°zÔÛ$\x0001àª\x0013#Úª& 5M</p><p>kÍ"Oø¶\x0006\x001a\x00021èÌ&_\x000c\x0012Íê\x0004°\x0006úIM\x0000Ï;Àó^Y<ÿ(à\x0019g\x0001Ïß?\x001a|¯ö;§ÿXÇ8Å³xAk\x0001WÅ\x001bàyM\x0000ñÙå¨í\x001d`·íÐÑà;\x0002BÛÚÙÀsZ>\x000b\x0006\x0004pfPf>g\x0019°\x0019ð\x0015ÀyC¨ë\x000czÚH]uME¼6W\x0005F¯¨Þ+¢k¢\x000c\x0012\P\x0006\x0005;\x0006</p><p>\x0006
;\x0003sLÜ(HãÄ\x0007Z(\x0003´ÁJ(\x0003Ë¥lx¸\x001cxÃ×tðªÎ\x0003y@SnåÕ\x0003~ ø²|fÚ¬«Ëù9ê<¤Ã_Ó[\x001e×ÍÜ¦GN;×»ËËõ\x001f	×ÑíiÅÖ\x001c=.}À\x0007¾u\x0012d¢ó}­?²ÒnÖq­\x0003éÐ­å²¬PdðE\x001a\x0007­\x0017|ë\x000fº*;~óqùîCË¯ÔñæQå6ÏÞu·Þ+Í\x001fùC³Êë~mêv¥\x001dÌ»ö=Â¸çÂÏeù,Sü åØ÷üÆµã«ü.ÇÔiLÍ7</p><p>èüq¹Nc¾¾ZNËN/\x0001åªzsz(ñÖ\x000bmÆå<ø)Ã{_¤©õ²|;=~TûÛ0~ úÇ	má\x001f&Pd²sðãªÔåB]®ëçr)³QÄû\x0019âè/:Üuv/gZeC\x000fUÝ¼¿Þ½äú\x0004<§Þé\x000fm\x001büÒ:ÖtÉ'5`¿©õÂð>)à\x0019µKÃ6'Þi»Ôy»´½ß¼·¦#¬{ïôP;úU×_ÃË\x0005§æì
^.Ê±#Ã3¯û®ùP6~Ê¯}þÉ½û©ûoí¯Õ_åùº\x001c¨eòìX\x0016ûM\x001dï¼Üçé«e[Æ.­i¯ÊòQ÷³<.¯Æ\x0011VÇ6Ëhi3/aëkY·´ànÛËc
t»\x0000g¿\x00043§\x0013uèôEýÜ\x001bê$eQþá\x000fãFÐæ>eb®n-c\x000c\x0002xºdÙÌù¼\x0010ÉoSô?îES'ÙÿÑ«\x0013¦f¤£\x0000\x0004£óÓ@Ý6©g\x001aß¯ªToñzú«×@¯^\x0003½\x0006z
ô\x001aè5Ðk ×ÀK§\x0001¯\x0011LYkÔëY ¹Y°$âp»uÃp3uC{\x0001<_¼xipQÖ P[ê>1\x0018ÀóÛ:~#¨ù\x0016qZî\x000f</p><p>0àÐ\x001e
y\x0000ÿÎ\x0007|¾Ðì\x001båþÑ¶ms\x0001\x0008s\4/érôô-\x001do
=uêdXñ9ó¡@Ø7\x0004Xú(åíÍz-×¶KKK²VÕ7\x0005\x0002\x001ecøÀ\x0011Ë\x001c7ÌZÔëS»æ;Â¬\x0001)ÏÀ3ólYJÙ_ËJ\x0017@ûúõëª#ß±>\x0015ôÕW\x0013xæ¨cöª/\ ^é\x0000¼³Ü¤½aíüÎ{\x001ck|bhëoóÂ\x0017\x00078»¸¨ã\x0017ó8è\x0001#±p\x0005\x001cÄØ 'é\x0000%Ç\x0001Ï\x0000X³Ö\x000bkpãe]@çççÕniÉ\5õ2ûÐ\W&WQüèËñ\x0000´\x0000æ\x001c1
L»à¨ç#Yç\x000b\x0001?\x0006\x0008Ï·»q'O¾5\x0002ÂÖ=Bäár_¯ûÀì1Òf8Â9æ\x001d\x0010\x0017</p><p>6´¢õøªöqïÞ»;l\x001fäõÞ\x0007\x0008ø~8\x000ey\x0001éçPêÄÞ\x000b6ð\x0007è\x000b\x0019\x0001Y¡\x0015xF×àÈ\x0004ýøã\x000e`=Q\x001cû\x0015äõ^\x0004÷ì+P\x000fú <\x0001ág°\x001d^
<Ó7làóXý¼~J\x0003\x000cúórÃÎ]úÎ9nç,ü[à\x0017\x0005ÐCî[ä^ï]÷	Ú0÷v¡äµ>è/U¿äé¯^\x0003­\x0006³ªkcÔ»Jíï¤\x001bÎU+MÜ§¢kñÌÄ¨íKuTÅ\x001f»~
ð|@ÀsÏ;w
ôTË	ÄUÒ5}¯a½\x00019¢ \x0006\x001bQ\x001eÖ)Y&ó``M\x0012\x000f\x001e"(Àó¤\x001eôIÏ3¢;4¨$ø,àYó@à3ô©¬¿x_îÁàÞF\x0011H8+°|FÊx E\x0003x\x0016øË1ÛkzÐf%ã¬@g(à3nº\x0001¡7£¶\x0013\x0016à\x0003à,ÇwåQÙxl1¶\x0015ã[Ê\x000274ø¬	ðZÇ\x00026\x0000hmb\x0013Ï·\x0017WµÙ¹SØª\Ýàõ 	õÁ¤á	0âÐ\x0007\x0010Ê\x0003
46pU\x000eþ:È³±ÊÀè\x0001\x0012n·ÊaÞPó']uä­\x00172ÍÊb£09ªÄyÍ´öR&þ_B»ùkÙU.×Ñõ$®ê$údRv¯e©2f\x001f¥¦¼³þ\\x0006úöäã0Êv\x0019æ
µ«2üvñ\4iáQe7/ò»¿¸X>ÒÔËýtîCÄ²-s­\x0017~øTYì'e"/}\x000c\x001d\x0018H´ú\x000bZå­}ÛrY7·e3uù\x0006óà¯\x0013\x0016d½ß
Î#ß«>¶ªËtZ(iÜ4jÎ\x0007­\x0017iÕ´ò­<¯z£¿8\x001f<Ñ\x000f? \¤Çu/óVj¹Î\x000fûû­\x0019ÒÞü0©?NÜnð·LË÷Èay\x001c\x0006­e»LËÎC¹ã\·~Ü»l×±g?q\+ï^ä_õ	ÏÃIùÅç:¢Ûz¡Ë_re;r´oU½\x000f]=¿\x001bÓÿ°ý#wÓ?-ó©åV?ñ[Ý×¸._ß£\x0007ü8ü¾·ßÔñÐ\x0000"Ã\x0012¹rÕ"ô-myk_Ä?®¿:<5½yÀÓ²â·l]ê±\x0001Zý5ÃÍ\x000f\x0000ª_b\x001b}±\x000cÙüÂrº\x001e\x000fZùáÏ2yy¥\x001dã\x0008Ë8âGsÆ\x0012Ë=NF¾I\x0016yÄ.è²Åc\x000f\x001eÇÀ\x0001@óy\x0016NÙØàÍæ<\x0005¤Êß<qn)/\x0015xl6×\x00027\x0016¹»6u\x001aõ\x000c~á¹Zó&\x001b+8E52BÓñã¯\x0017¿
mñLÅ,_Mã<Ç\x00154ègÑ>:¯DþO¯^\x0003½\x0006z
ô\x001aè5Ðk ×@¯^\x0003ÿá5àuB|ªªHË@¿ú\x0010SÖ­¿M®°axÆ{Ý\x0010<ý\x0006Â\x0000UY¿\x0000<c{á|Z+s´ñ·ßÞ\x000f0\x0019à9¡~çÝ8nûÐÁCa9zPu\x0010`\x0019GacyÅé¹s	Ð²ÿn.¬\x0001=÷ïß§µäÔ\x0010]\¼* í¡¥)V¿{÷î\x001b~ØròM\}æ\x0018j,³Ü<\x0005ÏûÓÚg
Å^\x0011njj:m,~±fEÞ\x0004ò\x0000 ï	t¾\x0016À\x001fVÏ\x0006¨ßzë¤@à£QG@VÖ¼\x0000.a|I\x0016½ßÊÂ6u\x0005·Ú>õö[Ã<ä\x0003\\x0004T\x0004D\x0006 Df\x0003Ñ\x0000È\x0004\x0005\x0018åxpò°~u\x001e¨gd\x0006Ô\x0004t6ðì6RÆ'|\x0012|±.ÎÏÏ\x000f-yiÀkx¨×Í¬¹÷ºÞÀ3`;Ï^ïBiG\x0000Q\x001c\x0016Þõ(èÇh¯2?¥I;¢Ó'ßò\x0001ÕcmÞ|NÒeÓv^óÂ\x001f¿Ëc\x001fÀû~³®ß)c@x\x0001úþ ïgã8BÝ@9}¤^ÕB\x001bÐúâÅËÃ\x0017,xI#µqô=,ÉqÈÍ^3>\gú\x0002ú\x0000¿P¬õqÿ÷\x001fíìÈÍe\x001ePä5\x000cP\x000c\x001f\x001cíå:Ci/Ú\x0018ð\x00171¬\x000bóõ\x001e	Öôì´\x000f\x0016ü;\x00048ïØ9+ÝÌ\x0006ðl\x0010½\x000b<ÃÇå¹½Ý'è/vì9ó\x0001<sùy¦.Î\x000f¯þê50ª\x0001æªêjlÎG£sÃ:ébrhÓ\x000f<cö¦OìB\x000fædéÅ3.,µ1¨Oü&\x0007ëzÃfCGbC\x001fûM&½ÍÄæ\x001f\x001bØS\x000c¢ ó¡aX¥\x001a|¦5¸MÉÒyVr|ßY$´\x000b<ÿ Þ¸'\x001a¤À³øé9\x0007o+\x00038ãÖ\x0015>·kÏ`nçnQ\x0001ÛÏòã¦4øm</p><p>`Æm4tS\x0013\x001c ó&`3NV(ÆÅ;e\x001axÆÒ##\x0013xÖÑzc'Aç\x0004×\x0018lµ¹µ³ ß¢\x000edö3 à¯Ã\x000c\x001e¾¢nâîp\x001e¸ð£_\x000fì¦Þp­éàáÌÔ\x0003\x0014å\x0010_Ã eF?</p><p>æô¢\x0001\x0001ßáæ3vËâÞ<»é\x001d\x001e	?ÈÄåººn]JzÒtë\x0002*o½gm:³ñß\x0013¸e'-\x0017<­ÛJÑ{-´äµ£\û»<ÜæPÒø²n\x0008ÃO<~|\®óÀ¸Îi ÖiÕåëÒn>&1&4SêÎ=úðäWe°,º\x000cx#åÖötxºr\x000fèìïJ\x0013¡\x000bó¥|üU\x001e\x0011N¹¦ðã¾^ð¯WåKx\x0007?rB\x000eZ/âý\x0003\x0000J\x001d´þ\x0001\x0007øÌE\½¯ëÈ×­óXë1\x0001#Î}×å@i\x001fÊ·s{Ñß¸H3Îuep\x001aÊvYU\x001eü\U~·)qvµÞä¿©ËêÒ\x0007ÿ½PioÜ-ëÙzºf.w´ß ª¶úNã<Ò¶5músÞ_Uëí{¸Tåj¿Û ¶\x000bqÝð\x001aæ¼ðær\x0019]J?ÛÊÖqÎ\x0017 d\x0003<¯¯¯\x0005oËá>É½û\x001fÔý²Rü¾¯i×<£"?òX.\x0005î+µßáN[©ëRy#Ë¬¬q<³®KÍ2[Fâêe]\x00028Û2Ùòd\;æ9\x001c¹[ÙÛxdåJ\x001bªµ\x000eýM\x0013daÞã¥\x0017~[èÍzh¢Óª×Æ>!²®±KÀsü\x001eÖdK§
îQFFæ8e;ã\x001c2ÑæÙîISÎÔ}ÊâèÃ:ãÅºd!¯Ô\x0015ôG2Õ®X>lmÍ\x0003Nî\x0013IaÂE\x001b¶\x0003iû«×@¯^\x0003½\x0006z
ô\x001aè5Ðk ×@¯ÿø\x001aÈßû¹h\x0016+\x001d¡ùÝ\x000b\Ã<³hâ\x0015ÞlÔ{Ý\x001c^÷&u8èOó\x001c}>ÊæÈä´\x000c¾\x001fg~ÿø½\x0000o\x000f\x001d\x0002$\x0013ðÌPZ¸&øgÐù¼ø\x0000Ú\x00018\x001f8°?\x001c{C\x0000f|k\x0019ððá#7çßÔ÷£ß\x0014\x0008ûúàÃ¯$\x0010+kc¯9'µ»)àöâÅK\x0002/\x0006ØÉ¾aºÕXï\x0001jâ\x0008ã\x001bÕ\x000f%``UñÂ\x0002GC/Ä>U®K×ãxb¬¯]»*Ýë\x0002±</p><p>ÎoC\x001f=úª@Ä\x0003\x0001$ò21Àô7_s,w\x0002È7ô½]äáSN§N\x0001j\x000bHÖQÛ|C\x0018 \x000f\x0007¸\x0008H\x0003x¶¥5\x0014Ð\x0019p\x00130\x001cK[\x0000á\x0004åg$Oáãgs\x0006\x0004Tôþ\x0001\x0014\x0000ïOãðÓ7ì\x0000öçÑïü¼\x0000}\x0019ê5ûcä\x0003Å\x0001¼Úxõ?ÇÛÂ\x001b`ÓûPÀfdÆïÖ-¾ëõ¼_ÄFÔ\x0013GÙ¬É½?\x0008õ=rä¾@îeÐ_k%Îû\x0000³2XC>(2Þç\x0005\x00009¾\x000c8C¦yñ6\x0001ÀÅx0'¾í|áK\x0001¶\x0017¾þB}öèÄ\Ò$ð|:dæ\x0005	ú*//Ð\x0016\x001ccC¿·oßö½sçîà÷¿ÿ½¾OþûÁ\x001fþðhÛ|6ùÂlk\x0018¼>b\x001e \x001cW¯.õ¾u\x000f¥­gcØóåÜÓÌ½Wöb×â\x0019àxu\x001cß+ÇÚ9Áç9õããÑG°ò¦/æþ÷6Ú=/úB{t\x000få9b=g.ë\x0014\x001fmÓ_½\x0006F5ÀþUu5VóO\ÚßI\x0017óãDùùï\x0019à@A(â@\x0006Y©\x0013'ø¬Í}û\x0005:ËÅQÛ²xÖ$\x0011N ô¬7tÎýÎª"àù'Y*óvÈ\x0006:X\x0005\x001býI W\x000f6ê¦\x0005\x0006ÃsVoàÌ</p><p>|ÞÆà©A\x0014\x0007ðl·ü¾ ¾¸§:\x0017ZààLãxà\x0005Å3[ÉëªàÊÚ&àylÜ¬Àç)ÎÓr\x00027dÕ¼Ü:N{]@ó\x0006à¹èºê¼¡ü:\x00049¨\x0007T¾ßÌ·±vKÑ
¾/«\x0001°MÔÆ2\x0008JeeåÍÙ\x0013\x0001f¶C\x000e\x001e\x0010[ê\x0001Ã\x0003v\x001d\x0018,C»±Û\x000e<¹±ê
ÖjåP.A\x0019]Ç U'</p><p>ï°JI;-p~Z\x00004ùVik]ª\x001f\x0019j\x001eî¹\x001cwÏþµ.¢­K¨ubê:;­óÂ\x0015ÿ¸æjûèèdSõµLOæ\x0006ò\6Ôõv~tç0dµ¼ô\x0007&\x0004÷\x000bä£ê\x0008\x000bÝÇ$íEX·nÜS\x0006¼*¿Zïê/ËVÛ\x0002?éÕøÔ	Íu\x0012G=±ñ"Ë¯r;Ìe@«Î¬\x0017å8Â-7g=t®goUÏ |pU×.òí\x001c_ëê¼æo}Ôûxä"¾ë(´Pø:\x001eùy[\x001f\x0000Pë\x000b>¤å\x0007\x001c?¸¡®å¢<û·¢¤qYÐªGÊr[ÎtO<~×\x000b\x0019Ð<¹ý\x0008Ã÷¸z[&xU9Hk9 æ\x0001å"\x001fyL-K
3o§:¿ùU\x001cï|¦¿¸KGGÍ òâ</p><p></p><p>Î9ûQ\x0000\x0000@\x0000IDAT®·Tëèøæ0ôð¼Ëé\x0018\x0004ÔßvÎï<ê\x001d^Ö¿ý]þµLûk{Ô°nÞÊrÜÆâßÊËcy\x0001$ã¸m\x001dµÍo\x0011Ë\x0004­}\x0010?Ï\x0005Î~Ç\x0013VÓ\x0007ñ\¾§Lú>rú\x0019¨2ûùp¼ãªüÁ°áYy»\x000cSÀ[Æß|f\x001dnlö\x000fÔzéÊ²!7zf¾jõ]óÐwò>¸ñGûQö;Êåt\x001a»#Oü°àß\x001437\x0017Ü².\x0017Ñ5¯\x0000Nð\x001a`³H</p><p>v*\x0003\x001eÃ®MßoÇäa;KÿÔe
àZc\x001eAáV÷\x0006 ³/Ì	p\x0006ü"vê\x000cÚ85±ëÒór·\x0002SÀF\x0005Ã¼ÁCãFüÖñ£åÖûz
ô\x001aè5Ðk ×@¯^\x0003½\x0006z
ô\x001axY4ÐÎþÍ?*y®\x0007ZKç¼6
á¬qºñº
üv­I:¾\x0017ûÕW\x0017\x0005Ê}5øJ`ð½»ß</p><p>(Åª÷[\x0001Å³wæ(j,ÃéôR¹æm\x001cÖ¼çe1}AÞâsøð¡\x0000¡XÊ\x001e8\x0016·a©ùU\x001e}@x\x0000V¿á^mpìõcaMËÑÓr:¥}vÖÌK×\x0004\x0016¦E6eÅ~\x0014ë3­Ëâ»¿2BÛ'Ké'O\x000cnÅQÞ·Âb\x0018Ë\xCÙ#\x0017ûRà\x000bß,å7oÞ¸\x0019`ã	Ï\x0000¥ª\x0007d w@ud?ë¬K±0Å%`(Kæ«úläÄ`~á7ã¿\x0019ÌÏÿ&ËFn\x001ciýdk[»¢k\x0000g;¬
\x0000³®\x00038ÅQ\x000e\x0016Ïþf0\x0000) 3à3Gm{\x000b\x0005\x000cýóÿ\x001cîâÅKÒ
Feìsn¨ÞG\x0005`¾.^,õÓæB\x000f´IÞû\x0003D¶U2²¦õú¹\x0000 «á\x000b`3ÖÙ¸íÂBîÜ¹§ºÞ\x0013ýVëÞ\x0019ÕeÜvéðpëèsaaaD^döþ uöz6E.ï *û\x001a¬ýÆú?ýô9¬ìïÜ½3l\x001b\x0000]Â°¶æ¥\x0007(À³û\x0017å~ñù9µ¸/¢?X÷ô\x000f\x0000}ÀÚãÇ\x001cÈ£¿ñ\x0004º¥]n¨¿\¿~+ÿã\x001fÿ0ø¯ÿ5Ýa½4Q÷a\Iõa¬äy\x0019\x0001ù\x00138Âòøú}aéÏ\x0002XÂã\x0000ÑO|T÷bÙC'/Ç«={vpùÊeµív}ã9Ý\x0013£À3zô¾åÂÛuleÍ½+\x0003ÏÏä­mf^Ðþê50ªÜKc_+]õ|T©ýt1O9N4îI£Y­{Ô6\x00014\x0003>\x000bÕ4Tþ9½Õ\x0013à³ÀâÉÝ\x0000Ï;\x0006:\x0017@¨À	}{ySoà\x0000:kp\x0006|^Õ\x0003¦m9\x0015&§N\x001eÀ3T\x000fÍ\x0006âí\x0018¶q|·\x0006\x0019ñÑ·\x001dfÄ3@gY7CÅû'\x0001Û¸§º\x0007xÖ\x00037#\x0011\x0001y\x0000×åÂ\x000f,±ÂÞÎ7£÷ì\x000b:#ày²\x0001'ô­gfÁáV~MJYò}h÷a5ÍÑÙñ ³ñ\x001a\x000eYaò«ÐÆÉ\x0007XÐ)½i3£ÍKÜ´60\x0019\x0010ºÃ\x00188¢)D= 0G\x001bWïë áø.e\x0002 \x000fi¡\uBÀÏÄQ\x0007-Ë´\x0015
\x000b%ú­àK\x001dbp-ÛðpÓv\x0007»z_ý¤÷ExuÔ)ê'\x001amßÜ\x000fÃzGÆoÞæ\x0003ï\x000cØ8n'Ô.¥NÎ\x000bõ$\x0002\x001fQÒ9¶pÝ¡Ö1ü¸7\x000fdc2°Å»ÛÇy]whm\x0013îk½ì/éÜ¶×ñæ;Âp.ø\x0007G]jÝ\WSÇÏo,úÇ¡ëSeÇï«[û°Ësù¥êmCG\x001a\x0018\x000cq_tÝ]hõwå ¾®s	?eÖ|!e1%ÜåAáKëÀ§\x0007ø1\x0008¥~\x000e'­,¢¿.\x000fË8R&e°¬?h·º½ ô=;÷AÓ*ë1¢\x001bËÒ´ò¸=«{Õ|äïÞWø¹(ßÔu\x001eG»¼"Ó\x000bû#ÙbB¥_§/¬¨q£a1ZtÏ\x0018I°õ4Lò=-oñ`öOjÝQ÷ÞáP·i7l\8iÌ³¶©û´)}ªë'<\x000eV\x001eÕ\x001fºQ½ Ô\x0015Yè/vµßW¿ãMÉgìÝ8äò3ègÞ2úÙ0u8´^\x000fY({+\x0008g~ÑÑÔÐç]Ö©Ë¶¼))\x000bàVç¤%_½Ú7zÑ¥Áú×òCya(çX~ÿ1ç¶s:\x001b\x0000ÓòR]©¯Üô´~ïéÔ\x001c\x001c|2(Ï[<r)O¶sÊr2!{ó;*¾ë=:%\x0008`4¼»ø\x0019.Ê>ýD?\x0019\x0015f\x0017\x00057jhê\x0015ÀxÖiT?y\x0007?®¤øù=!Ú\x0003Ï¡þO¯^\x0003½\x0006z
ô\x001aè5Ðk ×@¯O\x0003^[®²\x001e^3@«¿[ËõÍ0Ó(®ÙoðZ\x001f</p><p>\x0018ÊQÒq´h\x001eµý 9j{wX_¾ó\x000eÀóÉ\x0000c\x0001d\x0001ù¦/ßjÆâõkY\x0004)kÒ/¿Ìïç\x0002v¦ã(éCaÑ»?çÉ!ü¥,wËPìÀ×W\x0004d¾&ðÏ\x0016ÊX¨æ)¬	'?`èy9@è\\x000f²\x0016ÜÈüâ\x0001ÈÈ>Ùâb~K\x0019PïÐ¡\x0001\x0003î\x0012hº]ø\x0000ßÆ\x001a:¿å2 1\x0000é[\x0002ûÞ:ù\x0000?\x0001Ï\x0002e÷\x000b|Þ677x Ïtr´2ß¼ÆR\x001b`ýKYóYÌcÇ^\x001d\x001c{Cù±\x0004·9²\x0019\x0010\x0013+\äÅJrX\x000f³®\x0002:\x0003pBË\x0016ÀÄ\x0003:ã\x000089ò\x001aà\x0019\x0007ðlggçaÍ	(ú§?ý)\x001c²=}º.kÕ5¹uÕEz}
ðõ°ê­\x0013fÕàÃ\x001fÐÛ\x000eðÓ\x0016êì3"7\x000eËgï=\x0012N¹ylº\x000cþôéÌ»w\x001f¨¿<\x0014}¨ðÝâ·_í°_\x0016ÆÇ¢¿Ðg\x0016\x0016\x0016¢<ïA@s}ûÞsd¿±\x0002¤±¼èí©tçÅ\x0002(moè\x0008vú+ =VÅôe^\x001c\x0000´Ú</p><p>\x001dËzø}öégOå>ùä3Õe6\x0000wÀt^\x0016@VÜüüüpO=;wn«M¾V\x001f¼\x0016ýðë¯o^µòÁûo\x0008÷ßÿû\x001f¢#§÷<²ÿæþ\x0010VÒ\x0006oß¾%w¥³;Ñ§ü²Âk¯½\x001a}>tìØ\x001bñÂ\x0006ÏºÄg~uÕVþ+aO=>ûì3½xpI/_ì\x001cº\x0013'\x0012x\x0006H·Å³G\x0000÷Cú\x0000ú¨mR÷h\x000b@g\x0000hÒ\x001aÏ ÷pLÍ»§½\x0006b4ös.\x001bÕHtd\x0005UjM©°§\x001cç{Òèy¸þ¿ÿa·1Øø\x0012eã\x000fÀ9h\x0000³l=§\x000bàYo$Í\x0001<k²Ñ\x0013N
\x0016\x0003\x0001Å\x001aau\x001cv\x0002ÏuO§7 Gç§£û~\x000e`ø ÞºÛ&¾S\x001a\x0010§´á7¥xSy7\x00042CÅó±ÀgÜ²ïÖ>¤dQ±d\x00060ä#õðæxíM
Ê\x001c
¾c¯Þ\x0002\x0012ß\x001drÓ²~\x0006xÆ
æ¶§U´êuô2.k#tEø1ß^\x0015 lj°\x0019Ê\x0004É)T\x0018LÈ?S¹¡¡Î¨\x001eÛõÖÐ¶;\x0006s \x0019\x0018ì<XsÏe@
æy\x0010¯4ê×L|\x001e,R£\x001bî\x000cJvÄ?åÖA)7©Û·#¬¦±ß²¼CÀ{\x0006ÔÖ{Sû£¢úÃ}p×ÁÔaP.òpÕ|NkJ\x001d]Oû·¢äqZç§?Ú\x0012Mêª\x001b&Qqø¹,\x0013íCÿ®àÛ4vÖ­õK¹¾àmG<y¬?ÒXFó\x0012æ6îÖ¼µÝj<q4N\x000bõ\x0005oòÔ¾WëG8e?r1ùÛÁ¿Ê\ý.ÃÔu1_ó®áãôÐÜ°ÇpølQZG×ÕÔuv:êl¹ð'ßl\x001bü\x000eszÒr¹Î5
áã²HëtÔ\x001f~8~T¹~Ä#\x00133à3üþáF¹¯K)Ïå»\x001cë\x000bþ8÷E·ËuºúÃ·öqdpÏüM)\x0017?ÔrÞ\x0017áNC:Ê«éðs9¬Ò\x001a\x001eÊ\x001fxrÿV\x0014~UwÅ\x000bðª.Ã	6ëõ\x0002</p><p>	]=\x0011hØß½ÿ?\x0017í+×iÏcÑæiÛÔé»q×0§s[rï¾åþæþ</p><p>urïk\x001eó².*ÍÏ*h.d¬Ð\x0008÷s(}ÝÏ/þêjº®ü.\x000fÙ«çùÁsDÕò»NÄ¹\x000eð·£\d²\
\x001e\x001fª|)»eÎgÑ²-³;&pßå³ë\x0017|¶1ËN\x0019§§-_þ¶ \x001eÖË7*Ã Ö#öÚ6Ëi\x000cúÌ¨yY?tWwYóÈúæøD\x001fðáwýÍ©<îj-]Ç¿\x0012ånßÎé\x0013rúÝfÞYV w$\x001döcvjøÑg\x0005\x0019¸R6Ú³Í\x0003?®M\x0000g\x001dA3ºÿÛk ×@¯^\x0003½\x0006z
ô\x001aè5Ðk ×ÀK¥\x0001~÷WW×»^[Wj­¤Ö\x000bú§\x001bkgöar/½¥+9ªx1Ü½{ß\x0006èÕ3'Çþ\x001axÞ¯ýûý\x0002q¤ã\x0018i ^\¼&\x0000ô,§¯\x0008\x0008[\x0014</«Í7\x001e9ú¬:e,Çì+Y;\x0007x«c\x0001Nó»Î{\x0003t\x0003Åqôµ_D\x0006À»zõZ\x001c+ÌÑÂX\x0010{]E=\x0001z\x001dÃ\x001d\x0013ðãð{¿ÈfV(GMï\x0011n\x0000ÀÊº\x000eð\x0012ëSK\x0000Ç\x0000\x001bg[\x0002³ûQGÿ(,ý7Àä³g?\x000fKÓÇÂ\x0013\x000e\x000bØ="«î#²ðå¸f;ÀfdÅ"2¼OË¾gêI9^³×v­\x0001¡\x0000Ï\x0006T»\x0016ÏÞó\x0002<ÿã?þc¸sç.èdÄ5¹U\x0019ª¬\x0005\x0008|ôèA°2ÒÓÑàÔµ3kaY@O[x\x001bPÆÂ\x0019Ù\x0001©/À7u²`zFG^ß»÷½Üwá^}õ\x0000ç£á\x001f3ê^ËØknz#ë[¯·¡u¯Ñ{Pò8\x001diÐ\x001dú¥\x001f,--ÅK\x0001æAú7ul»\x001dÀ+Öë\x0007\x000f\x001eSgÿõ/ÿgðýËà_å¨\x000búcßtX\x0019Ó\x0007xéÁò¢'G\x000f[e.-ÝP_üFýý\x001bÑë\x0003\x0000gÜÿø\x001f\x0014ð|p¸w¹àÃ¼n[ú\x001dmãÙ[XX\x0008\x000cóB\x0000zöÎ¼\x001f\x0004 LßþôÓOã»Þ\x001cç¾wß®Á¾ýêã¢Ô\x0003Ð\x0019G½ê~¼wB¸÷D¼\x001fäý"\x0005¥lâI\x000båò\x001eEÜôz
\x000c5Pç¯ÜÇ\x001aFÅÄç­qsT\x0013?Ü\x0017¯÷é\x001f\x0002ÏSz¸â8\x0006t\x0010p\x000bsÀ\õsm?O\x000c\x0000±LÞ&:©É,g\x0000h
0\x001a%\x0007\x001a%E\x001f\x000fVô >Õ¾,º¦\x000fÕÓÁÙ\x0000Í9üü\x0013Ñ\x0011 \x001cÛ=+7#`xjF\x001b\x001aHp\x001b?~?ØÐ ¹.º"</p><p>Í÷Å\x001fà\x0019Ð\x0019\x001aÀ³@á°zÄ\x001cÓÓ%Ðyÿ`&Yè´\x0000ç	}Ô~BÇ{ë,EY4cÝ<\x0008\x000bç\x0016x\x0006|Ö ªJ¯2\x0006Ø¬\x0001V	^BË\x0008,\x001b\x0002£)4ÄAPADÒ\x001fTaªÇÞÄÁÚ9ê¤ÁË\x0003\x0019~\x000fÊ\x000c$ÞôõÆowI=¶`O\x0017ñ\x001f÷\P_\x0007'ü0ë ä¬RòÃ.6¡Ñ·\x001ca]G\x001eÙ\x001fBèOòher}º´¦7/A¾ú	£î]j}tãÌ#Ók3Zo¾­5Î:z£¿nöS/âh3;ÚÌ\x0013'~_Èïôè\x001a½*ÿn'\x0017(\x0017¼¸ÙåÖúáwYÈg};
aÜî¦ð¬¼k_¬õJë±\x0016$LúC¹\x0000¨ü\x0008vÛÍüI_ÛÂ²nU/òÛñ»\x0017cZ:FZê[ãÝ&Èbâ·Ãr0×Åi\x001doJ^.N¹§^ÔÉÀ3o\x001c¢O×\x0013¬3¨û\x0019´ë²áße_¥\x001eG\x001cf\x001d\x001axº\x001fº?XWP§ëär·Ñé×é,¿ëãðzï4ÐzÁ«RËápî+Oó/äÉá\x0004Ïç\x000b)FL]/ÚÄWÕ\x0005a[Ý;ýÏÑV_¥£`Z\x001b×>7\x000e35î»²\x0010ç°ê'Ìþßý\x0006J¿\x001bGkZó5ÿ8ÐÝ´JÉïÿä\x0018I\x0018i¡8ãzß¼ ÕuèÊáxä\x001e\x001d;³nÄwóÀ8ËAYuLÁÏóiÇ½ÓB<.h·\x000cÊÃm¥K;]Ê|²>­B²¼ÔåñØ\x0005ø<­Sp¦äB&ý¡.Y\x0006s&r\x0000pçüéq*©OHyÙ°Ø©·¼wîÐ÷´À½ëì6ÉZö\x0019I\x001b:0u_¦^Ìó´\x000b.\x0017g¼\x0015¿S·«¬\x001d¿ ðO§¾¤\x001fwü¾£>ø}\x0011\x001f¿mãW- yQ\x0010I0ÌOzË|4\x0014´}Í·§½\x0006z
ô\x001aè5Ðk ×@¯^\x0003½\x0006z
¼\x000c\x001aà÷?k\\x000bø7JÞ®#µ\x001aP×\x0011¦®_Æ)µ\x0003\x001aªû²× ¥¢ÊÉu\x000eßx¾² ó¢Àç´Æ¼7¸+@v·ö¾ýí[Ú\x0006xÞ\x0017G4ïc¯.ò­Ú´Ð½råëk\x0002å¾\x000e×7ß|=(GlïÒ1Ï»vqÔó¦Òë¨j\x0007e½\x0007ð\x0007\x0000ÈÈï½÷n\x001c%ýöÛ§ûJ\x0000vgÏr´p\x000b<\x0003b³·°°\x0010àæ\x0013Çeí»Ü|[ùb\x0000èu\x0017=2\x0003¶¬'±bæÈf\x0000ÀwÞÁ\x00029AoÀ?\x001fÌ~$¸K÷X\x0016À\x0017\x0002\x0005ý^§¨îÙ³k°[nß¾=!? 8\x000ep£¶/È2\x001aàÒ`- »\x0001N@Nî½&e=N¨+\x0014ù\x000cP\x0002<9s&Û>}úôpß\x000fù*ð\x000c ¯ªÉ±f\x0010\x0018ÿª@Ø×Ã¡¯Õé[yx\x001e\x000e0\x000f/ôÃ~#rcíL\x001dêþ#ët¿(@»Ü¾ý­Üý G\x001cTyGÃqô8 3öñ^\x0004\x0014\x0019¼fÝN?ä²\x001fàýDÖÛ¶ºEÿ´UZ?#ª±hGÏâä7y\x0001ÿy	\x0001</p><p>np¾`í§Oeñ\x000c¸mc'ú_\x0008\x001fÊL\x001c
À\x001dßúþf)¬¯]bñüû¡Õ3ýÔ:ÑÈe\x0007\x000fd5èìý\x0003ø»ÿ\x0002<c\x0001OßCÇ´\x0007:§ùÂ\x001bç£¶±x¾rå²¾ñÌ1ÛÚë\x0010å9\x0000tæÅ\x0006ú2mmW÷à©$áô?¨÷b \x000f\x000cÞ/º½BIý^\x0003#\x001aÈ9q>]ôT©ýtÃ¹p¥ûôOÜ\x0018cñ\x000cè<\x0004\x0005Ârô´ú­çÝñ½ä9
 S\x0002õ*Õ@OÎ'\x001b\x000ctìÎ¾\x0010]\x001e¬	\x001c\x000e'e#,IX\x000f(ÿ¸èøS\x0002§5	N\x000b\x0018\x0014(\x001c\x000f\x000f\x000fÜº¾ë¼.\x000bç5M\x000c+zø9b#¼W\x0002xÆb	ð\x0019\x0010K \x001c\x000f¶\¨IßlÖ\x00136Ðd\x0018 3À³\x001cßwÐQÞ¸ÍÙ9\x0001Ë²n"ViY\x001b¡ËB¡U×\x0000Å+¬u\x001f\x0016ÎÈ­rPo\x001c	)</p><p>P?­	3äåÞ\x001dÊM\x0004ÆÄ\x0006õ®\x0017:ð\x001b¢­5)÷ÄÛÕÁÅ\x000c´ëÈWóº<ç'=\x0003O×Õxü¾rAoNð­ë_\x0002<e0u¸¯²:\x001cêò]?ç­t\V\x001eæ]uâ0§Ë¸õÁú)VO8Ê´ìDÇQ
¯î¤Rã¬óqui7ëGÁJäò\x0004\x0005µ¼ðu}ÜwsËð$ãpÒ¸\x000eµLÂp¿ËeÂ²ßõs½ \Ö\x0015å\x0001`òC\x0000Êe¦È¿ÊÔõ;Þy WÜèÏs
Þ¨tÝg\÷.u¼ÛÖ¼LkYùÞñ:®RÊ³s~âÑ\x001d³\x001dzµ>\x0005}ñ\x001aê6R/.Òt/ë\x0012þøÝ\x0017ì7%Þi \\x0011&:×´\x0015åºOXþª+óâ*O·ÿ8:-´ÖÁþ­(2:\x000e½j\x001d\x001c>.ü[ñp¾_ªm\x0013ì³íôë\¨ûºùvëî¶!¾\x001bç<Ï£­Îhg¹ÆâÙáÐêàUã\&á¥R÷\x001apÇU?ý{SÇ9­ËV9ºýÒ2\x00038ÏÎÊ*WÖ³3zAÌáÎï{ó"Üe®2T?2vÓ\x0010Æ\x0018Zå5¿Jk¹nc_\x0005~.M=>8­´]ôÔ¾ B¹È0ÎUÙ«|Ô+_ì¡O>KÈjÙ(ßcGÒ\x0004CfÅ%'¤c!\x000b.Ï)««íËZ9÷¦åñê*ò&0
Ð¼W\x001b\x001e{öÈRË\x001em£\x001cgYá*¨\x000eÔ¤B£a3Ï· s~ÿêiôw,9Æ·äsS¤ôw
ÇðKWuøÃYtX°ËÌô©CüÎ'ªq\x0003Ð¹ýÞ\x001b²öW¯^\x0003½\x0006z
ô\x001aè5Ðk ×@¯^\x0003/\x0006Øoñ\x000b¨u
P~÷ÇNr]S9ÎµlîËF½cXG\x001bÆåo5\x0003\x0004§»\x001a\x0016º·o%¨·K{ô§O¿\x001fÇ<:%\x000b]\x0000ºWÀ\x0018ô¶?[Jcñüõ×Kk×¾	`îµ×</p><p>=\x0012n\x000f{ÿ²¶£~X^¿~#(ëDöýpd\x001f|ð~83öµølÑ½®	ÍoÚþUü¿Ñ:Îû×S\x0001\x001a¿óN\x0002Ö¬ß\x0016\x0017\x0001Ã\x0017\x0005\x0014.	4å³X,ÿ\x0014yXgâØÆ\x0019+^öÖ°ê\x0006ô\x0006dG½ª\x001f\x0016Ú|Ç\x0017\x0001\x0012S\x0000Äb\x0005|îÜ\x0017\x0002AïëEôüD\x0015Ç6Ûz\x0018\x0015õe}{ùÊ+q\x00044G>Û-,,\x000cp\x0000è×Ë:@V\x0000g·\x0005@ëÃ\x000f\x0003l\x0005xþðÃ\x000fÃ\x0019xö¾çú§ou\x0003æOMÉpmjF\x0016¼Ç\x0005¨¾%w"ÀLÖò¬×¹\x0000]\x0001¡èÄû\x0001\x001cY
O\x001cÖ´èÇà;û}\x0006å)çÆ[ánÞ¼\x001dGC»Ýß|3gÀõùùùàoÝ³\x001fkgüÞ |Öþvìu\x0002ÜÒ~´\x0013:Å\x0001â\x001aÎ\x00002õñ7½¡{Ý\x000f¯³ý\ýèl8êBz\x001c@u¾`ñ^¼\x0018`=A±X÷\x000b\x0001ô½¥%¬­¯Þ\x001cüñ¿×7qíQÛèú\x0019h"'mÉ\x0004´3ý\x001d}Ðô\x0003;t\x000bP\x000eè\x001e¨\x001bÎû@ðÆam«ô+WÄG¼¶§ã¸ú</p><p><»]Ù? /{4¦ô\x0003ÂqÖ;òèóMzóöW¯­5ûYìi¥«)=WUj'Ýp_p¥\x0019ÎYê«7þ×?lrÄ6lqäv\x0003:\x0003è°!¶¦Á\x001d\x0010A~\x001eîm\x001ad¡S\x001c!\x0000ø\x000cÕÀ®^N\x001b:Ã\x001f§Qi°©£\x000cÅH\x0005k \x000cÚ\x0008§|\x0013²Ø½Wàµ¬$oÒ¬}ÿh°¦c\x0019VE\x00019b\x001b+êUñÌc¶\x001bàYéÃYÐ\x0003§$ç²¤\x0006tÞ!:-`28f{Coù¬H\x0015\x0015\x0007MàYà³fü	:7\x0016Ïî\x0011\x000bÐïKÇw\x0007õðÎHG3\x0002f±î8
º</p><p>g»~EÝª¾)¸\x0016?B:0\x0000Ø1pÛ\x0010&4¾\x0018P<°wi\x001dh3ïn~xÔ´ÜC=hR.þî\x0005ÈRX*:ýÏÑ.*#~\x000f 5\x001cUFxX&Ó._îÍÃ~óÞMn~,Ç\x0013½<Q.tÄä¡þÅ\x001cÄCáÃ@óG\x0018åÖt¤çr\x001d¨#¼¡æA~OV8ºò»\x000c÷\x0015â]\x0016¼pËyý£Á\x0013¦ï)²q\ÔÁåC)ÃÎõ·Ë1­zrÝ-óû¾ÒZ¶e\x0008A?ÖU
ãM½\x0019=çÓÓù
uÒà\x000fLÕaN3Ë\x001d'KC¿¦ïë8êZøY·è\x0019^µ_U\x001dº\x001cSóCª?ü]ýpçµÜ¾Ò\x000fèÇ8÷A×¡¦¯üÍ×²ÀÇz®yð;)aõ²,må¯éí_÷\x001a\x0017VyvÓÿz÷P\x0019/\x001d3½rò%\x000f÷eóu½+Å_ïIë{çÛ¶:{\x0016x&®ºn»§ËêöQîsxõ»uÓÔðn¾VÖì?Ö©Ç\x0000Ë	\x0005lfñÌ"\x0013\x0000z«\x000bÙì\®©µqÔi µ~ø¹ÆéÏòB-³ÇÔ.­i\x000fÇ¸â££0ËXç&A]Çgå³,9PeïÊèñ+Æ®ÆÒyº\x0019C\x0007¡K½è7<Ö:\x0001æ\x0015Àß\x0004ó­hÍÁËO#º\x0010Ç\x0002\x0007öï	·_o¤W} Oª5Û*ëóoÕ5¥üz\x0012BO9¯®ÄÂù©~«>Ñ\x000bèohíØà³ëuoÚ®\x0001Í\x001f</p><p>Oþ5ÂÄ½~ÌF\x000cå*g\x001f>\x0005ÀkS§îôÀs¨¢ÿÓk ×@¯^\x0003½\x0006z
ô\x001aè5Ðkà%Õ\x0000k\;³.ðoý¬ûóûßkô?SÙá&=15ü±´\x0018
ciq±µB¾qCßÎ»)\x00070úÁ\x0007\x001f\x0008xþ@\x0016ï4Ö®iyëæ­á·¡ÉýúÍ\x0000ãÈõçáÃ\x0007ãøaÖE\x0000ÅS²öÚÐ¾ö½{ß</p><p><ü6@Dö½V:zôÈà£\x0000WÏ\x0008ì>\x001d\x0000-¿Ö÷u±îüì³¿</p><p>ôûzd-%0 ìG\x001f}¤ý¤©°L]ZÊc±µc\x001dkÝ±ïÏº\x0011Ç)VÔïý÷OG]\x001e}UõÜ\x0013u¥ü<]+×_é»Ôçeõ|þü¹\x0000@ã\x0004,p</p><p>)ÖÀ2\x0014ãqõ-G8Ûù(hQ¯÷\x0001+\x00018\x0001«\x0001\x0001Y\x0001q\x0000ÏÔ\x000fG{xÿ
ZgÀnë\x000cÐ\x001c=æ·¡ß\x000f\x000bgÊry¬¹íXÿzo\x0011ÙÁr ? 1\x000e ÔGr\x0017 ÖG^\x0013\x000ehO;RO,»qóóóÏûð³\x00155eÖºÔ5:åÙâ\x001bà¶\x0002¹þ34kl\x001f§ÍÚ)\x0003r\x001cúå~ÀÊàÑÃG/xiàó²Z?\x00172¡W\x001cò¢W\x001cÏÖ\x0005}\x0006ëb¿DÀ·óÅ	[?üá¿Èý^\x0000t\x0002ÏÖ/ÏÔ¥K"\x001f\x00149i_\x001cò\x001a¼Gnt\x0004ð\x000c\x0005\x0004·\x000eØÿ@Wvñ47ëú4/@`NÑ^ð¬0&Ñ\x0016xæ%\x0008Êó¾ÛÞ\x0014Ã3È>®÷|Ð\x0003ñ¹ûµäé¯^\x0003ã5À\x0004S]MÅ¼ÃU©ý\x0019\x0015öKgãyb\x0012ÐFßö\x0004x\x0016À¸\x0003xÖ\x0000;'\x0000wNtZ\x000fúçI\x001d'\x0015q\x0008ªÎ­\x001e®\x001dÆÆú\x0019\x000bhz\x0011æðÐú£· \x0006Û\x0005\x0008_@FSÌbä´*çU¬q¥ó\x001eø5mLN	ü£¶EyøÂâYy6á­7ôä
-±zÆM</p><p>tÞ¥óºÊYW\x001a¬jV 8WT,ßyæÛÎXxÛ°Mµ(\x0017\x001dÎh00ø\x001cÖÎM<ß^Ö`·¼®
VÕ'Ç\x0019ýÐhÚ&åb0ð Çw£96I0®Ì¡\x0002´\x0001\x0013µ	gü\x0000PûÄà¦°\x0018h"\àeÃ7Ú#¹ä_	ácMâ%\x0003É\x001eG«º\x001cê)\x001f? Èª?ñ_÷m\x001dù¤kääÊ¼üj]7<\x00126¨3\x0017´:×Ùaðc ´ã«K#°ùC\åO0÷ð6ßq4&ìØ\x0014÷ÛAY?~@¢£ªçYõ¡\x0004-ô-rý\x0010Ë5°ìJP\x001e^\x0000ÙÙ®Y6ç·!;ºnêß\x001bÍ#s²\x0004øÍo²ùÎ&y|_<êYôF[\x001eU¿Æ\x000eB.õÐGéWy¼l31Ñ_è;¢ê[4r4þäó¤\x001fizîóûé\x000b>¼Ä\x0013	²\x000fÑ\x0007=!¶ÇÔ\x0007¹R\x0007èR\x000e½è¹àÇbü0oäÎ\x0015õâ\x000f}¨éSøõ<Q´¼kâI¥0ÞÔ³Ë4NÛ\x0002¡hk|p¡rë3vá\x001eã¡.\x000fÊEZ.ê_øÑÆü(ð\x000f\x0002ÿPº¿Óç?4(ËºåÞ~Ó&iÈk~U6ørÏN~0B£7`\x0011q¾H\x000bß\x0004u²-k7?(iH*ù,³óÕ4¡ùã|5Ì~âÌÇaÿ1¨ê<`GûÕ¯-\x001f:p;V}X/ã¨Ã~,£úWë\x0005xÆ\Ô. IS]/åÙuûM÷tî³]åá8()~Ë^pôãqt3\x0006ÚÚ\x0019¿yA»Î²æØ></p><p>èú¹pyÇe4µ¬UÎ®ßi,·óB¹L]\x0006å1gÄ"Zã\x000b÷È\x0002µl¦5Îù¡.Óñ(ox\\x000eã%EÍc¾\x0007n8~ÑGâ£#üËq\x0017\x0018S¶cÛEQZ6\x0013gÙùÍÉ\x001c</p><p>åwÏÞ½:\x0006Mn¯CËq*ÛYZÔ´\x001b}"ë	_òV}Å1Ù¹,[¡,\x0001\x001f?~"]­'ðÕ³Àgó@\x001fì1'¥ÖÚ6ð\x0018ý\x0013B4\x001b<üÃ|¸Ñx\x0016À3ãZD&Óþo¯^\x0003½\x0006z
ô\x001aè5Ðk ×@¯^\x0003/\x0006X\x000bä\x001eÎßþÜåÚ\x0019Úú3¿£Òx9\x0011ée­´Æ\x0011\x0006H\x0006xîÚ\x0010tÆªr×.ç3qÌ3À3`¦M¬/^¼4¸$uñ\x0007Â=\x0014ÀwèÐÁ°=tè@\x00005-Ð9g\x001dq-`óá\x0003,y\x001f\x0006\x0010û[Ë\x0002\x000f÷\x000fÞÿ@ÖÕ§ß\x001b¼+ëã½2Ló\x0011ÕKKKñ½d¬<ñÇ\x001aRÊa}õá\x001f
~ûÛ\x0006\x001fü±ö¤æ\x0004PÞ\x001aÜé-ÉOÚ¥ëX§.
\x001eÿôD§Sj_}EÆB¢±ÔÉYèü\x0003;sæý°\N«î½ZË	\x0018Ö:4ÖÂZ\x000f/^¹\x0012âÅ\x0017Ã\x0012\x0016@ñ{®</p><p> ü¯P¬©±ÌåØr\x001aca\x0001`ñx\x0000Xâ¾öÚëa.§\x001dxïl/Ê\x0015J~éÆ\x0001Hþö·¿
gàßÙûê«?ýéOá\x0000mý\x000b\x0005x\x0006?sæ\x0003Éu0êá5<ëáééÄ\x00028AvÀêþý\x0007#À³×Öì9Ò\x001f\x0012`%[X\x0003ìöåc¸\x001c9:ç[Ëó\x0002uß|»wc]¼;ÖØ\x0006aY§Ç)rÂV¨K^©\x000ftxï^¾ `kgSÖßì\x0007³îÞ&|o"#\x0017\x001e8²\x001aÇþ//¤sÌ6\x0000þ¹s\x0002??\x0017Ç¥³we1}ú7\x0005èL_?uêdì¯R_ôBß\x0001x¾|9û9íqï^¾\x0010ð»ßýnðw÷\x0007¿û»ßÅ1ô\x0007Kí\x001f9ò%\x0002ÂãñSCS\x001eÏe¤/¼þzöm¦~Mÿf_ý{;\x001eeÅÄ>\x0000 <ßà\x0006@_¼zEº\x0011ã\x001cûSSêkóqÌ¶Úöþ,Ô{L¦î\x000bè=÷b\x0012\x0013bïÅû,¤õ¾N»oAþê5ÐÕ\x0000½¼º\x001aï½ªJíï¤\x001bî\x0013®4Ã}.õÿjñ<\x0004õ \x0003>3®è¡
àYG,Ïê\x0001Õ\x0000\x0001\x0005xÖ¤2%å)
êÕS\x0001êðêñ¢r\x001aT¢\x0012\x0005H<qÚ¼\x000b\x001a ±\x0006*Y-ªÀ6ò®è¨eM\x0006\x0001<kcpM\x001b«\x001a|Ö5XaulÇ½\x0016«\x001aÀá\x0005¤iw2¬·ë¨
Ü\x000e¹8^[q«:¢wUuÓÖä`U£éðsì¶vQ±Ìo[\x0017E¡8\x0006\x0013D\x0017$\x0014~Àï°tf3Vµt<\x000füSÕaY©«# \x0000\x000c:éÄFÿõ§¹4TÛ\x001bá±a</p><p>oév²\x0001ø¦$;þ\x001cD4á(Á\x0008ð\x0010ÿY5ì)Çåvé°PË¡÷ 6BoD'4c\x0016PiõwyûÞ|¹ïúÆrrßõ;¬¦µß\x0014¾\]þÏÞkS\m\x0016qÐÜ,\x0007`§y¼ÙXí²\x001dZ½ç\x0011äðÉ\x001f9L\x00088®ÐI´{SÚ\x001e±ßÀ\mfOT¦É¤ÕÃ°ßH¾¬R¨¾Cß0hk\x0019 ÔÃ}*ô©r#¬iCÊ\x0008ÑþüC\x00044}ø\x0011\x001eÎßÈO|2Ðc¯\x001fY¶ø4z°,ðÿ¼U\x0016O]\x001aiÓí\x0011ý=-Åq*\x001e?Ãê}Dù\x0013õlÂí7%\x0018¿ïágÙð\x0013N½\x001cOz\x0019íÐ¤ñ\x0019ÚÓ~(yÍÓùÆñ¯/âçàcW°Øoùùbç0Ëì² n7×³írÏuÖzÔ<÷óüæõ¼4ÄuÓÕr.ïß\x001e¯þ\x0016c"ý.ûÞßÎs<\x0007×ÓTµ®ãü5ô5/÷¾ºáj>¥Õs*ÿy\x0017eTWû\x000b~~\²¼¦[ýÜ#«]í·øk\x001f·´îñòUüTGömøÛueßJþqé\x0008ã2¯*\x000f²l%kÃÏåúi·\Â\x001d`m\x0002¯NoJ\x001aû£æË±lïÅ\x000b s\x000f}¢9\x0004Å¹O¶ºåØhéR? B&Í+ü\x0006j\x0016P\x0003Ìô\x0005Ò¢2¨þP\x0008\x0007xÞ¹o<o\x001bì\x0012­:¥</p><p>Q^ð¡%X

\x0011õ'æ;õÈÇ<%×Á+±ÙÀ3\x0016Ïëz\x0007\x0012kg¾#ö·\x0000Ï!Yè(Ôº\x001aOêx=ð"ú«×@¯^\x0003½\x0006z
ô\x001aè5Ðk ×ÀK¬\x0001Ö1Þ\x000fb]Ãoÿøño¸\x000eH?á9Ô¬iz/-Ã4\x0011§µ\x0003éµ\x0013k Ú¾¦£¬\x0001\x0011¡7eÉ53G\x000cïX~[øÃ\x0000³r½`åÒÒõÁE	ÂÞ½þ5íù\x0003&\x001e8x`pPÖ\x0007EY\x000fÍÌÈXA VÍG:ô»Grß}GI\x0003DË\x0001Â¾ýö©ÁÛ²8=yò-å=(>\x0000Ø\x0007\x0003DÆº\x0013\x0005jTE²C±\x0002\x0006\x0005xÞ)\x001e÷u\x0004ö\x0003§|£\x001a0:A\x001f=ü^§Ã=\x0011\x0010k_\x0019wÇ3²v\x0002\x000cïç8qÈ·u\x000f\x0012\x0010ò¬áyCÀû\x0006\Æ"w×®ÒW~Ë\x001a\x0000\x0017ðñ\x001f~=ß'O%-´¤\x0000nC_c\x0003ÏXµ&ÐzWrìúQGg@S;,jÿüç\x001eüó?ÿ9,¥Ñ#rC9>ôX=c]K{{=O[Ú±¾Này%\x0000ÚË/\x0007À<5\x000fÀz~Cùõ\x0000Ñ\x0003\x000eðY½JürÝ\x000f\x0000ýúë	®£OÚ\x0010 \x0015J}s]{Þ3\x0002væZ-ú\x0004/?Ð\x000f\x0001Zmý\x000c¥îX_£?Ê:räH8Àg¬
K¨xAÄ\x0001\x0001ÏêåÏÏ~AT\x001aP©Ü×^}-tÄ\x000f'ß:rðB{\x0003<_\x0012è|ùÒåÁ7âyá»è?é\x000f¤×\x000f\x0004êóÒÂN\x0019V>\x0016ÞôD/¢cì8òP·\x0000¹![\x0000ä\x0005\x001fze(ë^\x001díN½¼ONç^}	)¬õÛ\x000b¾g92\ß=¿¢¶Ú¾cVN]Ü>;XX¾å6VßÖ/míË{\x001fÞWãxÒâ\x0008§L(\x0017mæ}\x001eîIß_½\x0006Õ\x0000ý¢ºÂsU¥öwÒ
÷Å	W\x001d\x0001\x0008µ¹((\x0015\x0000\x0016àyEßÜÎhÓ÷@e©<£·wf\x0005:Ï</p><p>|_O@_(\x001d:gE\x0015ØT\x0000ÙØÈÖ&`81\x0014\x0006¢0Ù kðÄ\x0001:?ÕHOEWõ\x0016Ñº&u6\x001b\x001aHf\x0004¼\x0002<C7\x000f\x000bM,jØöÝÔ\x0003§§OßXÖ !ù¶5n]\x0016Ë*ç©j¶,·\x0006ø¬ÍTÜzã_lëKï¤ÓÊ?äLHô¸#E\x0003@S¥\x0008#Ucå¼5ê\x0001h\x000f{ò°5j\x0000ÉÍ¨\x0007(Cõ</p><p>\x0000»\x0013\x0005ºóäb-\x0018é\x001búìÕåï\x001bÝçÿ&)ñüXâ67Ñ)?ÂVºå\x001e \x0011]¤¬¹	Ý0\x0008â×t\\
ó g:.0ÇïÏQò8
þz)qöûÇ"\x001f]L\x0016ë\x001a´3¶£Ûb%G´Î\x0008öK\x0000\x0001øKa\x001d¬¶÷D@¿\x000cðBçÉ\x0007fñ\x000f¦ù?\x00120IÄqßq4\x0007oI5ß%Q¿§N\x0013ý Ó7Úö£îrÄã\x0011sÿ0\x000bªF¦>\x0000\x0003üÓ
ÿÃOê\x0010F\x0013Gö©aÿløF?\x0015ÿÐóP~Þ71È\x0004ðî\x001fGÙ¢?5ý*Êiò¹?ù¹H+ìü1/S4~õía¹ñ \x001b H\x0003ü¿üÛ\x001c[ùÍ-tÖè2ý#ú§~[PÇiÉË\x0000ÒsÑ'ìøQæ\x0017</p><p>ü£Àù¦þHù·ôgÒ¦NS?ÈÊ\x000f!ÿ\x0018ñ\x000f\x0013ËVÓ×.nþ¸PËI\x0014~§ý¦Äûr>xluÕôðè^¿4Ìù*?ýúTr\x000e'ØgeþõËk9º~¦mÌó}]=»Gýz´Ô¦£À³ËÚ¹_Ô~B?æÞý¹Þ;\x001dùñ»,\x0013Ô~÷±ÚgÝ¡[ùk¾\x001cx±S)\x000c~2F¥ëÊiù»ñÝ:ð}­\x000bòø%%Á®|\x001eG\x001cîzÁÃ|)\x0017\x0019¼ðbÏ÷¦)\x001f:O½W9º~^)Ûå{\x0018GcÞa>ñk´¿t&Çzú\x0011àrünÌ0ßÕbAÑ|Kúe»ä8\x000c~s»/-Ô·é{ÜssrÚô°¬PÊô¼zÊÅ\x001d:É\x0017¬\x0018\x000båâ¥=½ ßPÌ¼ic\x000cæ
u¬\x0005pè\x0019Ðyû¯\x0002<§Öc\x0018ãYjìÏÄõÀsj¨ÿÛk ×@¯^\x0003½\x0006z
ô\x001aè5ÐkàeÖ×Åíº6ûç\x0002 õ{]kZê\x001c{rºo¶Ormå5ø4á¹ÇÆ§\x00027âØcL\x0006<äØä\x0000\x0005ôÝ¾u[@êÞ8ÆúÌ\x000f\x0003Ìb}dG\x001eþê«K\x0001ê¥õhZ\x001eÐ'*\x0001:q\x0000Å\x001alV--¬q?</p><p>½)P£q¬Ýø>íÂ\x0002n~pTV³Gtl3\x0014\x0010².ÊÝ\x0010è\x0016kmöÅ´fýè#Î\x0000Ïÿéã°\x0006ìå{¾\x000f\x001f>£À±T½$ÐðÎûó»p?þ¨Ïy2\x0004¸iwæÃ÷\x0004:¿§º\x0016`úª,%»@V,{ÙR&\x0000¨\x0001Å%Yy_Õ7­¯^åøå\x0002BgTO\x0000Ñ\x0019­-Ñm®©\x0001ïùæî»ïâÞ
`\x0014\x0000\x0017\x0014ðÔkVÖº\x0000½vÕóÝ»wB\x000e@ç?þOñ"\x0000ýÊµöLXâþË¿üË\x0000·¸x5\x0000gÀ~gÊÃêït'ð{ªÔu¹Od}Mùì\x001bûí}é+_(\x0000¶|P\x0000ÞãÇóhhêpíZ\x0002ûÏ¼ÀÖÅO¥¹Æ\x0002ù°ò\x001c\x000e0?-½_}Ü£P\x0013H\x000eïÃ²¾\x0005 f]
¥îywêã¹\x001fë©Ð=Âf\x0000²óH÷ÃÃãµ±´Þ¹\x0013«üAéßù9¬\x0004ÏÍo<={Vuå\x0018éÔ\x00072¦Në»Øoå>~Ó×ÃâYà>\x0000?/\x0003x?~AZÜÉo©=f\x0002p\x0006tþî;¬ÿ\x001fõ8ß\x0002ç8o?\x000f\x00046S\x001eº\x0004xÒ>k¶%{¾8kíJ;>É6O-Í[£D¼|ñé'\x000e>ùôÓh«]»w\x000cvíÞ®~²#\x001d^pÀ\x0019xö¾\x000c\x001a÷åý¡ì§\x001b±?B:öGj\x001cék\x001f í¸Lã¦ÿÓk 4@ß¨®ª¥ÙÈM8÷\x000eë¤\x001bî7éâ>ý\x00137õç\x00004`\x0000léq\x0019\x000e"ì	/³È±\x0016z§\x0004ºM\x0001¸\x0001¾ém9
Æs\x0002gäÐ ¥J\x0014ëe	\x0012²@U\x0001üFgµì4 l®ª\x0010YSoª\x001c\x00154Ø.kÒyª#¶ê#×Þ\x0014à¼!\x00196\x0005\x0008\x00028sÌõt\x0001ãx`\x0015³©~MI=|s»$\x0006\x000bèè'\x0002¾\x001eË\x0001@¯Éòy]éÊ¿¡xî7ågÇ}Sn P:7</p><p>\x0013T*\x000c«£ÁVþI=ÀÑFºg\x0000Ö=\x0016Øè\x000b\x001f\x001e~è\x0019\x0010¶rNó<òÐF­¦Dçº\x0008¯4n:Æ
6\x000eâ\x0018´L=HÃ;eÏ£7;lewÃ}oÙ¸wyãâ\x001c_eqÞçQÇãI\·L§6j ÿ(ZLßã5.àK{qyð7µÞ×Ôr\x0012N9Ç\x0006=\x0013¶ß\3HI\x0019PLÝÈï\x000bvð´\x000c	Zýw~(|)Ïü«ß¼]gç³üÔÁü­».5\x000f¨Ëº^¦5òpmÞÖ_eÀOy¾Æù\x001df:.­Ã ¤³³È<®«õhZëF:ÂÍÃm</p><p>ðQõ\x0005¯\x0004gÚc¸áÃÕ¥\x0011XþÔøª7ä¤¿ÚUùÉcç2Ì§°\x001eö!Ë\x000få~´]Fyó¢zÃº÷]yê}õß÷æajÞ/ª}\x0013l¶Õ)§í×®éóÊ³N¦ÞW?ñõn\x0017S`\x0003<SË«}ÙýÝÔÏC¥ö×4æg½sÿÒ¡öû¾KÆÔ¼Yä®\x0001<êÓ</p><p>\x0000¤É\x0014Y-o:ev\x001d¬[SÅ³\x0007ðÌ\x0002n\x001cðÌ»ÊI9ð"C\x001d\x0013Æ\x001d!g+ÛÉ2té8½Õñ\x0016uC\x0019Õ\x0019\x0012tÎ>\x001eMh@îª\x0017ä«22=yßnFN;úW\x001eãã~\x0002ôyìËÒ8ÓÓüÎÓ	78Þ)¶Ï>@]ý\x0013{¼0ÖÎM9>UPÛ 3ÔÇ%ð¼¦7\x0001Óê9tG~Õ=\x0007ú(?\x000bÇø¼â\x0007 Ú»vîá.(:\x000f´·xFCýÕk ×@¯^\x0003½\x0006z
ô\x001aè5ÐkàeÖ@»WäµóS«Öß®w\x0015:Za-!êRuE®-\x001aÚ,1XûäQÅ\x001b\x0002i\x001a\x0002|\x0000}\x0000wnß\x001dÜ\x0016È¶W\x0000\x001fßO\x0006x>yòT¼dëÏ\x000ba!}ñ"\x0000å%\x0001mß
@\x0000Áýûe­\x000cð,\x0000\x0017à\x0019ÐµÅ\x001e\x0000e\x0002\x0003ì^\\\x001c\ÃºôØ1\x001dê\x0008bÀJî\x0001ï._NPöÒ^µ"kÂÕ\x000fð\x0019«çýû÷
\x0001T\x0000hÀÂ\x0004/	¬»#ëÙo\x0005\x001c+ð§XW±¶\x0002|=sæ]Y­¾#÷®Ê{-dÇZ£¡½VÞ¿Ï1Ë8@Ñ%Õýr\x0000ï_\x000f¼p:m«Ù;cm/\x00000ÖÇPÀl\x001cVÉ¬ï½NfO/t!ð\x0019\x001aí 6\x0000%m\x0002Ï­Å³×º\x0000ÕùË_Â]½z5xÂ\x0017\x0007øå+Ç.\x0003\x0014{Nã½høx¿56i¶ëÅÐ\x001fñÈ\x0008¥=à\x0005O¬vý²\x0002|¶J?åá¨ý¶5¸ëÌ\x0002\x0017ºå\x0002Tæ¥\x0001\x001cÎÔ
],-]o@íüæ1}ìµ×^
yøq\x001eÿ}8¨ë\x000e¨O½Ð+\x000eÙÎÿrpá\x0002ßè¾\x0010eä\x001eÃè7§Ne½æçç}\x001cös6â¥\x0008d¸zuQu|\x0018z7åÐ7\x001d;\x0016²üMntA\x001dâ\x0005\x000bQjmy©G{ÚZ\x001a\x001a¢gëgÞ\x000eý¸/\x0002òÉ'á.]º8ØÃçÄä |?Ü8åÀËm
\x000fóC^ï©à¯mB9ÞÃ"÷ n+Sâû«×@jç¸ºª\x0017ÏUÚßI7Ü\x0017'\iÆ\x0001Ï\x001c\x0019íEÞÔÀÏÄ\x0016Àscñ<©Î?!7)vc·utÄ\x0006ß\x0019
BzqSÛc³µa³\x0002eª\x0012Èc"NtCó>®¼!þ\x0002·7µ\x0011¸Á\x001b,¢+:î`UV(+r\x001bºßÔÆ¢"±Úh,\x0005>\x0003<ëácõÐ­«

®\x001bð\x0016Ý¹[ ¸,³E9^û©âÈ=\x0002ÖU\x0007¬×\x0003ngù\x0001­\x0001cvU|\x001emà\x0019\x001d)jàÄË4Agª¨\x001f\x001eãØïØ\x0006.\x000e7~ë À`Á½ã+õ\x0000\x0003å2µß\x0003©ãM#SùãtÎï(Ò×<N\x0007e@ó}Ê\x001bÿ\x000e3\x000b­eU¿åw·ló\x001f~\\7y;m¥¤EÅP\x0006k;×\x0011J\x0007vhæÉv±¬\x001eè¹·£\x001c·/y¸ºy	c\x0002\x0001p¶ó&>Ô\x0013\x0001D¾Í\x001c\x0013¾ï±Õeh?×§ú)Ïá\x0015jÙ µº\x000e¦µ.Èàº»¿gW>ç7ïªÓêw¼i'Í÷æOy\µ\=/<2ùãúÕú \x001fzÇ!õÙ¥äöQzòÔËíÊ\x000f)ün\x0003ÿ0Ev×±RxY6óu<÷lÖ¥°Ty,ùt)|¬;ëÓz ÎË\x001dGÆÔ|¸7ï\x001agÿ¸xÂ,c×Ï=ãÍÛ4c_Ô_=ÏÃ	6í\x0017Uõ÷¼zY\x0007Á÷¦Ýpß:F}ÕKã~ÎbÑ^nÿJñãê³ï0Ëëô¾·ü¦£Ïvý~ö:_¥Ôûz!çê\x001aÖ·-ð\x001cÙÔaÐêÌË|kyÕoyyæxþxÞj<þZ_óV\x0019×ãAõ{ì&-áÈ<³Î.ËrzLà\x001e¥N\x0003uþ!\x001fo)%'f\x0004Ï© MÙÖQ±-ßÀÆâï9y¾áÈ)ÆGÊÏñtN/,&HÏ7çg\x0015/Ëðrá¤~hÈ©-Àdý>åuÅÉ"¡'ÉÃI%©\x000bõ+ý`ó\x001báY_\x001f\x0011co\x0002Ï²xÖ÷½6$_¼ñß±x\x000e\x001d¨üÔ\x00054ý©
ÿÍ~¢Æ\x0001II/òÔ|</p><p>Ð¸Á÷ûo<ª¬¿ë5Ðk ×@¯^\x0003½\x0006z
ô\x001aè5ðòh ]/²\x0016`ÍàëY®{\x0015Âpé\x0010+\x0008ýa}\x0013ÿ!\x0011ØRÂÓ5P\x001eµ
`yõj\x001e\x000cÐyïî½°2Þ§OM\x0002:sÜö[o\x0014`µ2GVÿ\x0010`5\x0016±|\x0018kW`æ[¹P¾'|P£²·o\x0007\Õ\x001aL/ÿªä0y\x0012­O\x0007W\x0005èaÌQÆ\x001cQ|èò	{\x0005`Q ^\x0000Ï\x0002;\x0001
\x00017¯ÉÝ\x0015\x0018ßjN@\x0011KÕ÷u4Ç\x001eS^XªÒìV`téú­Áõ%9ÑG¾µ\x0018k+^H~ï½·\x0007ï¼{jð\x001cf\x001cñ-°\x0010KÕP_³\x0007`çXpÜÒÒõÁ_^\x000c·¸xUzf-VÎÛ¶Í\x0005X\x000cÈ</p><p>øgð\x0017jÐ\x0012à²î¯±æ¥\x001d®Éz\x0018um´¬½áÃâ8êë|PÒ~öÙgOeýJ^ÖÓ¾\x0000Fóhl¾³¬cÃzÐ|\x001c7¼Y?{\x000fÀ\x0014À\x001e\x0007ðk×Üs =°Þ~ç·U¯#\x0001\x0003\x0010ã8\x0016<¿|/ÖÓ\x0006Ø9Z\x001a0Ô\x000eRw\x001ceZ&dÆZ¾\x0005Å</p><p>>_\x001c¸\x001cø|§½§OWÔ¿öÕðÑ£\x0003Ø¦\x000c\x000fÜ¼Íßû\x0016ìÆ1ò\x0015e7ò\x0002\x0016£GtÃ\x001ayc£}\x0016ç%\x0000ê\x0008Pßò>\x0010 zõóBFò¿©v»\x0017/¦óR:û\x0004{õ\x001c\x00012GÿV\x001fu>¬Þ½\x001f\x0003Ef¿GÔ³Á¾FZÑgÛnnþÊQÛÕQÛW.ÿîÁ}	>ÓÞÇ\x001f\x001fÌÏÏÇË\x0001Ôßmëý\x0019(û\x001f±ïÑìå×=áÞÒÐþuÇí²¸§õ´×\x0000\x001a`ì©®jÅóY¥öwÒ
÷Å	W¸OX<ómç8Þ¹\x0001sâ­ÆâYo1qÔv±ÚSçÈíY}`=¾ùÌ\x0000\x0003xV|ë\x001aa\x000c>GÐàº¬×õÆÜºgÑÞÐÀÃÊï:CõdIl}£V\x0002sX:\x000f-µ9Î1Û8M\x0019\x0002õ0Óª£\x001a¦·Ëòmg\x0003ÏËªg\x001c¯­Yt\x0008<OÎ\x0004\x0018
ðÌ÷­\x0007X>\x000f\x0000|¸ð#¶\x001e`ä\x0000N2¡¨\x001eÐð	ñÒ \x0003PãòÀoZ\x0007\x000f\x000f</p><p>ú²¿\x000e\x0010ö{ð`±ß<\¦ùÔ<\x000esZ¨\x0007¥\x001aætæíû¬­úQ39¶ñ­¯ÆÁÛËáÞáÏ\x0003gåáüÏ£æSywýÝû<\x001a#\x0008Ör»eÃÛm\x0007\x000fâíØt'/´^ÖmÍWetZ&\x0010ÎL°P LZ¹1¯çy\x001dÓ2Ãæ¼\ü@E\x0016ýã²<P×\x0005ª'÷.\x0003¼\ÈYëì::´µ\îëåtæe\x000c+çs¸©ÓÃ\x000b¿iå×\x001aå\x0013_åp=¶¢æ\x0007­Ë"¼è\x0006´\x0005?\x0002±êÍúE§Ä¦ûc\x0001¾Ä\x001btæªÛ K)ôðªõåÞq]êô¤Á!/®Êa=\x0007_ðzWW³T¹ª¿+\x0017ùëå{SÇùÞÔáRÎ¸ËáÎk:.í¯\x0017&Y\x0013ìx¹~­²¨Ou¯uOõPý\x000e3­yÇù75¯nè8j¤N\x0002Ìï>_Ç\x0016û÷³Üe\x0019LÝWM	Ç\x000fu_u\¥ÄÛÕrª,ÃÖô\x001b\x0003Ðye5ÁgWü\ÎrL«\x000cÏóÇñø+?\x0007Oû­7ë\x0012j]{l©q5=ü\x0001X)ÏÔe{\x000c\x0018G-#´^ÉÔeq\x001f / òæ\x000fQ.Â¹,³åe|[ÕoG(VÉù>óc¶-2\x0001@çB³±\x000e×\x00029ÏY\x0000<Ço¿	\x0016OzñP¿ÇRæÔ'²DÒ\x0015ã' 3/"R¬¶AÖ=õ2%ðoKçÂ\x00120}Gcñå3 5e¥Ëß~*>î£²ÔBñY÷|6¥²>\x0003Ç\x000fDÒr%%îåzà9ÔÒÿé5Ðk ×@¯^\x0003½\x0006z
ô\x001aè5ð\x0012j ]£³\x0016\x0018ýÍÕq\x0018\x0002¯\x0005eC\x0012-!Ä%\x0012,«¼H?<(#È0= 1\x0000#\x00002\x0001Æ}Ë1Á÷\x0007{\x0005ùà,Ï\x000cNxk\x0008º>zôP`àÒ'`Íº\x0018hÕ'ù>³@69è\x001cGOk]æ%\x0002¼sÿÊ\x0002¤Ü/¿ü2ÑæÏ»\x001bkàÝ:
\x00153­Z_\x000f0òÆëñ]å{ßÞ\x000b\x0000\x0012\x001eìybGY¿\x001båÍ°w¦=N^rÆ:\x001aÐcÃ\x0017+åkr\x0000Ç\¬ªø\x00122<y"(\x0016´X;c©Ë1Ùy¡´AcÅ¬|ãùË/¿\x0005íW¡?t\x0010û\x0003Úå¸g@E\x001c®¶@æ:»Ý[c
Ç\x001a£Î\x0001Ëq\x0006i\x000f^jÎom\x0010Óì#Úçs¾[,\x0007\x0008NXBmqL]X'Ó\x001fpÈ@e\x0004\x000c\x0006\x0006ô$/íÂK\x0005ô\x0007.ç£M°ÚÆ¡'[øVp\x0016}\x0003¶\x001a`\x0007Ø\x000fà\x0019J\x0006½-÷\x0008\x0000öyÉ\x0000J½.^Ì#¿¯	Pú4_F_^^\x0015ÐºG *ß> À¹\x0005²á7ÜëÖ\x001e\x0000e\x001bÈE_õr\x0003²A®G\x0019Ã*àõ>}g\x0019]øÙþ¤Ós\x001fÅ7É\x001fÞ\x0012 >\x0016Îszé=÷\x001fæ¢Oq</p><p>\x0000²\x0002RûÅyú)ý\x0008k|tN9ãe5öBØ{#Ì}tÛù\x0008ûÚ\x000eðÿâ/ÂqÜùÞ}»\x0003|Þ+ð\x0019ù\x0000ù±2§Ýk³\x001fÎ)3÷W)Ìö&\x001e\x000e\x001c\x000eu_öW¯Q
4KÌ.ÝþÁhËU©ý\x0019\x00156Ü\x0017oÒÇ}ú'nþÏØ\x000cà\x0019ËØÔSÇm(oT­bí¬
ðÌv¬ºp\x0003°Ê·g\x001b7£·fåf4hLèxÄ\x0000©5\x0019rIøMT§ßZP\x0000\x0000@\x0000IDAT>Â\x0014¾&kçU
D¸5\x0001ÏëÚ\x0014fãpMJM\x0000á4`å,8XòÉJFÙÙfÃ\x0007Oq	<ëÁWIëJ\x0013ßjVÜÔ¶íÉm²ÆãHmAØaí¼¬4\x001c½½.°\x0019Ê1Û\x001bÇ</p><p>oCOÈ\x000fxL\x001dxHS?èE2Hî øI<¡TªB\x0019\x001cg5ÉÌÉ¡î\x0003¢ÒGuNG\x0007:@x`¯aucxä5Oó3­ùHã´QGÕÍYüÕ·+K}¨\x001bï²jx
£\.ËXi
§L\x000fP.ËÑõGdùã2\x001cäû­)òPïl\x000fcj>¦\x000e¯òÙïö¨õ²~­WøX\x0016ó2ðC\x0003Ç$êÍ{(\x00131?\x0002üC 6æégÚ çG*ÿ¸
YLñ[&óó\x0004é	I\x000b?ñP×Å|ºu¡\x001e¹>§üZ/;­iÕûiåm~'a\É;åàúF»PÿÆ?\x000ckâGÒq£«ò\x001eç'¬ê\x001fþ±¬Ö©ug=tN_ë\õ H\x001eO[Û\x0001~\ä«:¯ï-/´ú\x001dï¼Ö­©ÃC_*Ãòç¯qµ<òY\x001a^ýN\x0003åWåg:mdÒ\x001fóô}¥\x001bÇ£¦ûuý\x001aÏ\x0013lm¿.ÿ\x001bõò3é:ºÎP;rtý\x000ek¹=ß\x0017G\x0007­3\x001fë\x0005\x0018õ\x0019Àï~o¿ãËÎ2TZû¦ÃÝ/MÝ?M	¯qä#Î\x0017÷ü\x000e`j9ÆÉE\x0018ÏØÊêS¯-ð\x000c\x001fë³ÊN¸e´,PËÃ³]ýÜ;\x001dá\o­Ê7NÕôðá¾ò«ü)wF\x000bud\x0000Èµ¾ \x0019æ¸VfË\x0008Ð¡ø»LËäñ¬ÊCXuä÷eýY^òårQ¾\x001doÏáô{)Ü,O½È¨ßz:ÓFÔx¨
\x000f·Çóä¥¼ËsNoÛ,ïëË÷¬ð=*-d\x0001Y ÆwE³¬¦\x000f¨»µegm¹Ï«íó\x00122ÜNDÉÔ<H´¹)¦=ð*ìÿö\x001aè5Ðk ×@¯^\x0003½\x0006z
ô\x001ax)50º\x0016ð\x001a¡Kµ"Úe¸üZ6ÄÊ!\x000f±Îó\x001aBK¿æ>)\x00193Nk~þiq\x0001ð\x001cVÇ²<\x0006l¼ÿAhËûöí%1Àó\x0007ñm_[µ\x0002.-]o@Òo'À¨]Zw¾"`ð\x0015­-u:èÆ²ö\x0002Ø\x001c5Á¢õÜ¹s:úø|yZåÖZ\x000e\x0013p\x0013å¨\x0006ä4¸</p><p>HzâÄæ;»'ÃÂ\x0013°µ\x0018kW<¶\x0003Ì\x0005HÅÁÃ\x0017û·í·¥\x0017â»¸\x0000v8¬h¹Ü\x0006ù²q|ëùÂ\x0005\x001dÝ|þBè/OÀÊ8òq\x00145\x000eù\x0017\x0016\x0016ÎëdÚ!×Þ¹×Çz÷úõëÒëR¸ªkêäo\x0010\x0003²\x0007N }](Áè#¤\x0001\x0001mó;ÃßÅ/º`ï\x0017}P&µ³{Ò^Ô7~^\x001fê	~^ÏC©\x000bGã\x00008m\x000cE\x000eËÏ=eP?ö©ÿüü|Pë\x0015\x001d!\x0017òx}Ï\x000b\x0001µ½¨\x0013/&$ Î\x001e÷ª\x0000è5µË.¸{d9\x000c8<àÃEyvÜÙ\x0017\x000f	Ý×ç>ÁÅÄûB´!å²÷ò3^¹WÃ©jì	øE	\x0000s/ç%\x000b(:Éâ×\x0007·ôrrÚ\x0010@Ùº#\x001f\x00009uÆÌn\x0017^®÷\x0008Ðè\x0018G»´\x0000õî¨\x001bO:õÄ\x001a\x001eÝà\x0000Î\x0003x\x0016ø¼Ogã¿q\x0000Ý´\x0001ý×{\x0019YÇü3å²§5\x001deØQ°Û4»½\x001a¡zÒk Ñ\x0000Ï`uU19oyþJê°Nºá¾8áÌqN71hgujÝ´(ÉNÎ\x0018`kb[\x0014ko7´dÓ\x0010ËËi¾û,\x0010\x0001TtZop\x001cb\x0008²ô\x0000¸"
¸\x0007J»®£¶×VpÚ\x0014À½¡\x0007gS\x000f\x0011G\x001eBÃió\x001bKg}â/äKð\x0019\x0000XxÄQÛÚÈÄ\x0006à\x0019kç\x0000\x00190\x0005<OÍ\x0001<o\x001f¬KV@æ5YB±æ¨íüÆssä¶î7äâ<\x0011Ñ8Ö1\x0000ImXºLè´Ê\x0006pVø4zCµú£\x001a\x000b¯ÖÀ.4¡Øâ\x0019]fcBC)»¼Ð½ý-u¾\x001c@\x0008÷`Rým\x0018S\x000eP×&þê&'KÒ²ñåy0óÆ ]7m×\x0014u0Ãï¸ðèÃ\x001cN\x0019õ²Ùï4¾w\x0019G¿ÃÇQóuïM	OñºmRÛ#ýÖ§e\x0002o´\x0016Ä'ÿ¶-ÐoN</p><p>ô\x0010ÚSwøh\x000fO?\x000f<ë\x000f@g¹Æâ2\x0013pmÁÚÞ\x0011ß<'çdêÉ\x0012p µ¼õDË3}%%DÆÖ\x000eÐ ëDÁO+Oztë0×þUõáû\x001c{HO[ö ÕWË\x000b`BW*4úÛ'3\x000faõ>nÊÑþÐMxÛÆùcI\x001f\x000c­®Ú\x001f(´#q¤1øìú:Á\x000fÒÂ\x0003s;Y^Ò#\x0003/»0\x001eá·C|ü¾ì¯t_y«ßi\\x000e<ì75ßî=áÎoÚ
s¸iÇÏe¾¦\x0019:>4ÓÖ8ó3u\x0017C¾:T_L)p¥\x000bS§î3É£¢^!ý¸]Ò\x001fÔþÑð\x0010gto]ùY2ðÌ¸g4~\x0016L\x001drå3\x0016åê\x000fm£ßÕ¾·Õ}
¯yÍÃaðÇ?y\<SÑô®W¼äÆç;Æ\ðæ²Ì.ßòù\x0007<´ë¯i³¼£+O\x001d7ÏñPëðzÁ{+l\x0006-S+o»\x0000Ëqöç¢ì\x000fÃ²yLò½ã[ª1O2FGdËq~ÉË\x0000ôWæ&~ß1§¸ôÃ¸ù±rfVßÅn¬\x0013xæ÷^¨Ó9aõì¾íßZQ{NËq8Û¡ö¿»\x0008Ï±·±x\x0016ð¼¬§\x0002yy!çíA[g÷åQÚ¶Mê/ûcûl9^E*#y	I"NÀ³F5©!""¨ÿÓk ×@¯^\x0003½\x0006z
ô\x001aè5Ðk ×ÀË¤\x0001ÿþo×Â¬9¸LGÖ\x0000üþçRòÈ\x0001ÕZ)Ds-a\x0004×¸LyùÆóW_]\x000c«cÀ8,N\x0013Pü!¾Ñ|ZGX¿úý8¾\x0017@3Å»wîÊ¢8­\x000fËc\x001cVÏXx\x0002²A§´\x0001¿¾!ÐYncÓ«½ÆÍ\x0000Í\x0016\x0017ó;¾^w²ÿÅQÎ\x001c{\x000c\x0000\x0007à\x000bØÍñÈßÿÀ<}õØ\x001boüF\x0016¸7Ã£gµ\x000e¯\x001f~Èï\x0005ÿø#ÀèÍ\x0006Ôý&¾ÕúaohÐ|§7ÁºC\x000e\x0006Hõ+Ö²u\x000fã\x0005\x00070|MÇ\x0003~óÍõ°¤5ø¼{÷®!ü´¯\x0003\x0006zMÌzub\x0018Â©¾ÇÎN\x0001`\x001f>Ì\x0000\x0000h\x0013ð<9X8~\{·ì#\x0013L\x0007\x0008òËWTÇë\x001ftTöj\x001fÌ\x0006À'ï6xí9d?É½Èýñ
n}Yt¿\x0000Z[@æ@õ86Z\x0016ã«2dÂ	\x0007nëí£GÆ\x000b\x0001¼\x0014Àç¦îHî²ÄÅ\x001aò£ÏJ¹\x000bú*ê«¯
öÉò\x0017Ëv@Õ9\x0019\x001fæÿ¹÷Ì\x001f>è\x0016w]Öå\x00182¦[Ó\x000bÞÛ\x0007»\x0005>ïÙ½Ska2ê\x0007á´\x000fjÐ\x0019J½\x000e5/\x0000ì×K\x0014è2·É]e2:ãezÉ"û\x0003{U­Ñ\x000e}(÷\x001dr\x0015Ðø¸ôÏË\x000eÇhÚ=®õ8^;å½¦v¼\x0015|ÜÇ%ËNldöþîðY\x0007 üèQúý\x0011õ\x0003\x0002©ó[àÐV¾x\x000e(kqq1\x0000ï]»·«¯Êº[þFÛÀg°^ÞÂ¯îÓPWÚ\x000cg¹¡\u_0öq\x001cWù÷þÿß5@©®êÃ{UÚßI÷KçüÆsvXýmvÉl\x0000´\x0004èÊá_Sj´
«`¥\x0006fðÄ</p><p>\x001aÊ@¬\x0019C.\x0005bÒ4¥ºä ­§"Ò°ï»¶Æf°øò\x001dçMÝð}	"å²=|é`+¿xs¿\x001eò\x0008tV\x001e¥Îo<K\x001e¾ñ<Åó\x001cVÏÛ\x00072?Ó[58YÒ¬ê;Î|÷\x0019·&Ð¢{3¾ñ,ùE=\x0002<c} sÒ\x0019&\x001c¥Ç±KmÑ\x001dõßl¡\x0003Ñ|î¨i\x0018ÓgýäzóÝó(ÅD©¢.»\x001dxòJ\x000e@lÌ21äFxÊ]Ç\x0004\x0012¥71ÍéQÙë e¿)¶òg)ù\x0017Þ\ZÞ\x001a\x001e?ãø\x000b«y¶ò»\Çç}¶	<q®{\x0002¡Òj£còøÇ\x0016é\x0018¸íR¶m]'Óv£ßmR\x0007ý,	$öh-ýÆ\x0015ÇÄt5ñys^ÏÜG&~ËR7ãUÚH¿s\x001d3m\x000b\x0004ääÅÄo0\x001a@\x0014WåD7	¶0µ@­è\x00004*\x0008M½p-Ðñ¬n³îÙ\x000eÙ79u\x001dGäÏ¸\x0016Ì¢ïv¯lÔ³ã\x001cæû­hÊ±ö£+òC©·\x001de·?@[0â\x000c<{ÂóÔ\x001f\x000b¤wÛQ²Ënå¶\x001f9ßiº<j\x0019N\x0003%oWOÁ/3Ô¤cËpZ¾ý]êrL\x0017ê0Ó\x001a7ÎoÞs>S¿\x0018Ju¿5}1%I1üç\x001e\x0016\x0010%æ\x0000}%b\x0014Ú\x0015¼C'Ïs.g\x0015kç\x0006x~n/EÓ\x0016n\x000fú:Îýß÷¦¤ëúk~ó«´¶i}.ýüøYêRòez~ð<\x0003ê¶ÏË5E®*å\x001cGÎyM)ÏÏ9Ô2\x0011ßa5<e,í[täqÇ´+K§Î-Ã8Ùè\x001cMiÆvì²LUnü\x0019\x001a2JwÑ\x0016ÒkÈ¡ßF\x001br^`N\x000eéô	i#°ã(ìF\x0017qß}¤µü\x0001@3¿\x0001DÇâ\§Gè}Àéiwê¤nÓÉuÈß8®;ßäo\x001aúR.p\x0005<«oç	#\x001ciö4êÅ[é,¡ÉCâë÷\x001cú\x001aÞ[y0«}¦âéN¸<¡\x0002\x0002Â\x001bB\x001fú¨4ºoîHÒ_½\x0006z
ô\x001aè5Ðk ×@¯^\x0003½\x0006z
¼L\x001ahûw×Ô"Ö\x0003ñ{ßý¾ð+\x001fÿÃµëö¸7~nc-¦ý?¾Ûå.¥PÀ¿\x0000\x0013\x0005(ò­f¬[O¿w:6Ö:O\x0015¿ÓñÃ\x000f\x001e`¡1Àïü|\x001e©Ì¿Ð	½ø»±ÙÎ§îÞ½\x00130ÖÃ|;Ú2³.Ä2ö@Q( §`F>ïS²þ\x0005dÃÊ\x0013\x00070k­ÔK{ÜñJ\x001c]\x001dÀ®\x0000M¬Í\x0003}\x0000Ò\x0001Øá\x0000ÿ\x0000q¼Lì53\x00149lm<·oßc¼ïè»ØOè\x0004,\x0001°\x001c\x0007dm</p><p>¨ü\x0000¶_9<xåð+Ãu,û³\\x001cõÍg\x000395ë>ß\x001d¾¯ï\x000e\x000bdçèñï\x0004²\x0003ôÏ	¸üôû¦OÆµÊúÒõ¥°6æeÇúÖ°Ûo\x0008<kïwZFm^.¢_[ÓîÞ¥ceËý\x001e9ô÷ðá£\x0000c\x001fR\x001f\x0003êè#£ï\x0008cÍ\x001eúÐ	pP^\x000cðñà´Qö3^úÈofK\x000fèrÐ\x000fnNýz{o \x000c§¢­¨_Ý\x0017ø\x00008 \x0002ÀE°§VÃú¬ÚòñB@\x0018UI_\x0001<«
B÷j×\x0003û\x000f\x000c¶\x000bÏÙ¦Sl¡Xh-ká¯¿ù:,ü}L:{\x0016îCì?SxV´ïÌo¾9?oú9ý/÷`Ö%ï\x0000Èá.Ð1|L[ôMç|¦±°f¿\x0017ÊñÚ¼ø6GsÓÿ|Ü¶uD¿¥ÿZ7µ}»öøõ-õm¢XMÛÊ\x001byÛ|\x001b¹/\x0002ÖÖ\x0000ÏÈî=*«Û¼\x000e§\x001e¸V\x001f9¦Deú?½\x0006B\x0003ôêªZ²ß\x000f\x0007¡gæ2§Uº½-ß\x0013¯ý´<j\x001b\x0010W\x001dROQn\x0011\x0012ç\x0002\x0000bñË"\x0013àY@Ôj\x0000]0@<Å\x0001\x0002k@äG9:yäW8³P\x0000Ïzà¡ñàé*Í\x0004ÛØàzÌ\x00163þ\x0007E4¾é,Z­\x0011¶ÀMø
<\x0007§\x001e|ËÞÐC9!\x0019Ð\x0019:¥ï<OíÜ5Þ©ã\x000e\x0014\x0006ð¼¢:\x0007\x0000-º\x0016~É!ºY\x001c@s<¬</p><p>«G|ó\x0006Ð&\x0019M6PÔèjHOl.«?"²1= (Y\x000c\x0000¾\x0017+ô¨JUEBa\x001eHZÐ¸Æ3Øfù\x000c>aíÕ\x001c\x001dAË¹|6gÙ46¯h#\x0015\x0004µlÐ­®\x001aWý¤÷½ë@ØÐO\x0019åÞåÖ4Ã´</p><p>4/SÒÙß¥ÄýÜeÞä5 ¬\x0007ú´e²Þë\x0004`æOýdzê\x0013ó#KÇ\x0016-Ha\x0019Çäá\x001fEPOP¿mà³´7\x0002ó[ô=y:\x001fò³ÊÒùÓÈ/ûë@Ù~ã\x000c°	\x0000{Â]?(:aÂ3¸À&	\x000eä¤ë¸Zî¦Çu¯¯ZVëgìhÛ´îïÈóK¯ZN7e\x00197}³!#ÒQ¦ËEUßÖ'}(u?HÈç2Ç?\x0016B.ú </p><p>wßÖ<]ÿPNy\/ËJ\õ×´ÕoyÞÔü¶¦³ßÔiÆÑÆ~S5._-¿úÇ¥­ü\x001cï<¦\x000e14\x001e.±6}1¥T®<\x000bå²ó§}T\x0014\x0018ë³ÿÒ÷ÐKÐÇ\x0019ËpâpôMÆ5Ïôoë²KËm\x0000u¿òV?av5\x000f~Ë7~ßC«üøq9îµÏa÷¾æCO\x001aU>²fyÁ2ý\x001cuzËkZu\x001f9\x0018Çí,+á8tl¿ë\x0002­üÐ[\x001dG\x0012Më`ÇAqU®®,ÜçÕþ&@/ùr\x0011ò´/\x001ceÛç½ç\x0000Ë\x000e%\x001fz¤\x0013Rf\x0003ù«bá¨·¹Yûe$øæ\x001c\x0003mõ²¦¹&y¥YßÆ\x0002ZóËÜ¬¾\x0001-7\x000bú\.·kÕÃ¢õ'uI&üù,¤\x000ciñìo­¬<z%ð\x000cø¬rø¡Yx´<\x0010áÍ>JÙQBÐì»Q/þè"Ê÷êqOXõ\x001aè5Ðk ×@¯^\x0003½\x0006z
ô\x001aè5ð²j ×\x00015H^^pï°É¥\x0003ëvÍËzÂNË®ð:×\x0019¬/µþc
	ÀyîÜùp\x001cÙ\x000c/Õ.\x000b(<\x0014ßó}ïÝ÷\x0006ÇO\x001c\x001fæ§,>1ô£éþI\x0016Ó¬ã\x0000ÓÒòh</p><p>\x0016åQ¦ö\x0000t¦èÆæªBÖÖ{S\x0001 ùhå~ú)äA&ä\x0004Ã\x0001v²î"\x001e@\x0013pËu\x0001ÌL§ïI\x000b¬kcäTJþ\x0004¸\x0008HÃ¢;
sòÅh¬}í\x0000ër¯\x0014RlÒ%kS(Ö¹î[\x0019~û7¿ÿû½ä2@û4^@FnwÆrz(ßËÆkÈÜ'¥\x000eÞK M°æ\x0006TÄQW¬ÑùÆ0å§~_\x001d\x001c\x0011\x001a'ªÆ>Äd¤½{÷,°ïF\x001dÑÏ2ÙzI \x0002ÏèÝëPö)l\x0004­kWÚ\x0012\x001ev)GÊnÒ"÷h\x0000£¹\x001f{\x0012\x0000ñà\x0000ÆÕ/Ø[v[\x001aÈFY|»X/i³\x0017/\x0000\x0018|¦ßj@ûJ?ªÞ\x001cNÿ@\x001fèöF°,½°ÿe;mºJw\x0003Ï¼LÀ\x0005¼D±C óí;åv\x000cxYoc¥µ}õ?E;æ3ÏY»\x000f0\x0011\x0000þ\x001d{#^\x0000°ìÔ¶£\x001dpÈË>wö\x001d,²ëþE\x0004è~þi',±±PÎoAË*\§\x00058\x001cÚî£¬E¿@/è\x0017\x0013ffù\ÊãHo[¯Ã»îÉÄÞtFâBn\x001c¼³¹\x000fç½\x001a?cu_0Ç\x0007þO¯¡\x0006\x0018k«\x001bFÈãy«Rû;é\x0007<ßo<«£j7\x0016\x000bbÊÓÐ\x0010\x0003°iÈ÷±l^[7 ª
KuÜ´&µ¶ÐbQ°12"#\x0002)>6+s"(\x0006[y4\k"u²\x001c\x001f\x0013âNàrr¨`àÆ¯2ÄÎ[uðÆ¶\x0007I\x0003ñ¦6;õä\x000e6õPN4ÖÎ\x0013¼)\x0004è¼kÏ`Fo\x0006MhàÂÒyEàóªê
ø\x000cð[3ðüíqÛ	ÎW«gÛÆÚyFâ¸x ßæ\x0017Csy\x0000¨\x0014¿Ó£\x001eP³ß´\x000e(ø\x001d\x001e]'t\x0007(¨Ë¾òp~Êªé¸ç"¾^¤é^ãÂºùÈã°q0Ö<MkXõ×xÂî"=mæ\x0018]0qW]Ó9-y]^Mo¹¡5ýÎ_Ó1¹TàÙ\x001aÉÆ?2À¸÷\x0004\x0004/O<µñsY>×ÁpËá|.Ó÷w\x001eôbÇ\x001c¥^Õå\x000f³fl0³Z'Ï£$­õ¨mTÙY5ìoõ»\(ü)\x001bÇUuo]ÎòY7UÇ¼­+ò¹\x000c×Å\x0014\x001eÕï¼nå¯åW\x001fùÍÃéHãtÕïxh7OÃïüÝðçÝÿ-<ÇÕãyeýûã<\x0016þû9ý{sn¥[ëÏý\x0012jÇóm¿)éñ'õÙ\ÔuËp?¨ÔÏEz,í×¼¿ÛÎÔòui­Cõ;]­\x000fºå^]Y/Ç1¾§£Ü®\ãä­²Öv§y[^!\x0017¨«U®®¼Î\x0003E\x001eÇøÑu^@{\x001c¶¼Ö!´òÃOÙ¦\x0003Às\x000b#Wu¦ý½À=Wç1\x000e¶/â \x0007²y^ÂO]ü\x0010º`~\x0003tæ-öxó^k6\x0001øñä'ú²M^3\x0002
>ëmo]µnÈãÆ\x0008÷\x000b\x001444¿\x0017­\x0013åR\üò!åÉòX\x0016å,ª¡Ñ\x0006\x001aæ\x0016^ô¡z¥<\x001e7ZF§³\x001c£\x0014Fí/Z§íi¯^\x0003½\x0006z
ô\x001aè5Ðk ×@¯^\x0003/\x0006¼\x001fûE<û³{G\x000e²6áO¬QzÍF°×\x0014­<\x001c\x0019ýX@.ßw¾/\x0000ëÒÅKú>í¥øV1ë¢\·Lµè)\x001d}êÔÛùùùõ.k °(Öúõ\x001bÖÉ>¾\x0019P7O©Ò^gY¥\x0015\x0012¤2\x0006c]\x001a{Óaû\x0013\x0000«dÁb¤xud\x0005+¹O`WiTnÈ×`\x0001a¹+ÀnO\x001cë­ýøxé=yøÅe(\x0000êwß=</p><p>Ëi@F\x0003Ï§Cë_\x001dÍ\x001ei»nfM* =S­+ýÒ3õ\x0006\x0005¤ü\x0018À9Z\x0003öð§ëÀ\x0010?\x0014ùYÓCëZ\x000f½ÛR\x0019Ýü)\x0003y\x000c\x0003h{\x000f%-@'À/uôËêPÖÓÞó¥¼$_®\x0013$÷	G>;x\x0006è/ \x0018Ka[¡\x0003¶ýk3_ä\x0000\x0008EfêC»¦Êár ¬Ó½g@yÈe.ÍòcéÜ, ©\x000bÎ²"c\x0002Ï?\x0005O×
\x0019\x0017ÇK\x0000Ûfóí9Q¬É\x001fJg\x001c³ÕÿãÇYÏ'²\x0018Ï\x001d\x0005Jd'÷0¡¬ï_å:`6\x0014à9ÝFè\x0008Kñl\x0007äÈý\x0017\x0000açÜçÜ?R÷üÖsZ6ûÄ4(áÙvyzõIyèú~ÿ}NÀnS£¹?£w÷\x0007ú÷W ô\x0005ë6ò3þ)0(Û\x0004êphõ\x001a\x0018Õ@LF</p><p>2­±ñ\x0004+ Rû;é~	ðlgÞR\x000eKgU§ÑÃ.ÁfM?ê¬ÎiÑ«ÍlÝÓ'd\x000cµL<\x00042%?\x000fçv\x0010`Ó-Ag,Y_|ÈA5¦à)¿Ágôq</p><p>\x00173ýo6\x001cuËcÅ´¸	H®eB\x000f¤fÁ¤Þ\x0014È<ÉQ\x001b;v
¦\x0004:\x0003@\x000f\x0014ÆÑÚ|ç\x0019\x0000z].@çð#?à³Jüa\x0005.Ê¿¡µ5áÈ(A<\x0001û\x000bÙÑGèG\x0014¿'.UÒ\x0018\x0000G\x001dç¼ÜÛ_)~\x0007\x0017Ç9?\x0003\x0007(\x000fHëæs^h\x001d ð\x0013æxò?ïªÚÏå®+Þ¾j9Î[ù®Þoå7¿nú\x001aß:2\x0019n¥ÇÎ<,k7eBïä\x0012æú8ï÷\x001e¨4@ÜäÄü#Ä\x0013\x0010¼ÍßÔm])e?ÏQ\x001fËl,#uÃ_uSë¿\x001b\x0007?ç¯Ôe¸¼*S
³\x001fZ¯Êpî}ÙoÚw:Ó*Ë¸0â»¼¸w\x0018úµþÍ\x000b>øád\x0010fçôP.§þÜå2j:uiM³ßõ Þòó¸¾:ÎùÆQ§!y:\x000eúÛ{·\x001fÍvíº¯®Ý½wï}ìà8\x0016 Å\x0002¿-N\x0000ßòW\x0019p\x0012\x0004yÉÿ¥Ä\x000f\x0016 YAâ£\x000b\x0002H:çìî®êÊøÍÁ±8¿U_õµªº«DVñ¼LNNÎÅu!Ç"W×!éÇÒ·/³ç½«\x001d½üýÓ÷BïOòJêí'Üû[¿\x001e¤ï&­óR7§ÕôîóØ:×N	\x001fóp÷®cÚ¼®\x0003áèF\x001b\x0012Þ½]ðÆ\x001f³\x001b²q\x000c<</p><p>t\x001eàó¾
9\x0017{zÊ"\x001f×ëízíÓ\x0013§\x001các.²¡øØ0aôN{zLÇÔºC»í\x0012&Ï¶ô5g*\Ú\x0019YÐ[z\x0017
±et¢#×½\ûHÓñxÐöf»ÇÕÛØz£û­îuÞÎZí\x0017ó¥&	Ø¾ë\x0005÷:=Ë½¸<«ÕÎYñãÜiìë´ÞoÝJçiTÏ­okÐh\x0000Ü\x0003:o3\x0006'\x0003¾ò?e»7ë>Ûayý\x0017Ù²ìæ\x001eyNë\6tmÇ³ïrË\x0002Ë\x0002Ë\x0002Ë\x0002Ë\x0002Ë\x0002Ë\x0002Ë\x0002Ë\x0002Ë\x0002OÕ\x0002\x001e'2îé1DÍsï3ê!\x0004c\x0008\x001d\x0018?0¦©qËHcg2Ón</p><p>\x001cû¶eþ«ßh«hm\x0017Í7tñl\x0013\x000cà\x0015À¢ÿò_þõ]Û?ú£ÿ¢ÆÀß\x0001l\x000b¼\x0015ÈÌØí'¶lÛLÙw\x0001.\x0005¸i$®1Àì3\x0000m¨ÊK\x0006´\¸\x0001Çj|¥UÅÌ[za\x0001p\x0002áhÏÛÁÇ¸ÓÛSKê}ÅXOó|·\x0017ï_cS©Ø^TYí\x000bp
gÔcYÏ\x0016à§9EÆ¥±%v÷¼©Æªçt{ÃNd*ïïL\x0003 g5+ ¢_f~9WÒmÌ¿B]o^ÎãfÚò±Gâ×~ÐçI75$¶£\x001c>\x0000l^ä®N0~2_\x0000EßÌ\x000f#»ëL<cnø²\x0012±nÆªÐè\x0000E§×õE}]èÏØ\x001fþ\x0001½©\x001fçóOgÍê©§ëH]ñ±\x0019º¾\x0012h^/<\x0008«9\x0017~C_«Ø¥+«Ã-ãwZ-þêñø:þ§ý¬DþI/\x0015Ð×\x0019·ç\x001bÕlAÏêú\x0017/vÔ\Q-RÀ/ÉË\x000ei/«Âkûo\x001dS(}µ°"æ\x0014\x0006 ·­ôWêªóú}õAìü{½ôPu\x0015èÌÎº§u¾ä\x0005x-}c\x0007ÍqbKäYæÄg(4(4ø¡Ø;ù¹~\x00056\x000bpé~ËP 7µN\x0013Þñ}\x0008xþO»\x0015ÏÙºão\x0017¨^^êÍ!up(Ý{\x001f­¤½ªWo%)±&\x000eu¢Ñ±õoWÔ\x0013r\x0005>«1øæa²­à[\x0004Ú>¢þB±\x0000Î\x0000Ð\x0000Òb\x0012Õ¸N2\x0001xN*«[!W²3MXéær¦½g¶Ø\x0006\x0016=\x0013è|ö#+8¹ÒM¬¾ë,z­\x000bØ5\x0017j]Ì\x0000¯Yñ¬»a\x0001ÏÑ\x0006\x0001ó_ú¨Æ3Ú=ôB?{é(^ÛI:=|²ç¤wûm\x0007äÆq1¸Ë§SäàRpn\x000eÐ½«\x001byÙÍ\x0017"Êá¢W.L)G:\x0017§øðFÿð}
\x000e]FÚµ§áéezøX>iÊ\x0003\x001f\x001e;Ä÷òÉ=b¯ðvÛ\x0007Ý¹\x0001s£"ÞùbK(ùÜXâóà\x0001í7znbÄ¹ñà÷uå8#²<@@;\x001fá´'mîzõ\x0002Òó0iwì\x001dôÞ&Â¸Ððöº{|âq½\\x001b\x001eè1\x001eÊ'}O#»Ë í®x¯7²ÂßmJZò±\x0005vÃ\x0016>
õÄþäq,ñØ8é¡©g¯[Ò¡¸ä;vø\x001b\x000eS­kÏCÆ19ðì}d¿MøìcyÈ</p><p>oè]i=}\x001fN<u`ÃwîßjÁÃWuG
´7.m\x000fÅ\x0006ô¹~Màº@<4axãyà¦?ò¦g®\x000b9¿\x0013?F9~ðx|×3úB{:áè\x001a½Ñð¤ºº\x000e]m Ñçðæ¬è\x0018ÛD\x001f®©¹Æ|Ê¥îN{=ÝãÃ\x0013\x001a] ¸Ðè'6=¢Gt~ûcn~î\x0005L(ÌcG½]®çÌcÒà\x00104¾PëkÊM
®<xÒ\x0000Q(&\x0011ðL\x0000ð6{vÍáþÆàÞ\x0003}Ýãt¬.§«»­·°EN\x0005ÌT¦*sq½ßýÛ÷COäíw%îµ\x0000ç\x00005ñ\x000e9µieÆÞqøð~ôýqJÜ46:´!e[\x0016X\x0016X\x0016X\x0016X\x0016X\x0016X\x0016X\x0016X\x0016X\x0016x*\x0016`NêPW?ïèñðaî\x0018·hðñ
cMÍ<Îa*£Ç	ó­ã?û\x000fvògög'ÿñ/ÿòäÿ\x001bßjfËa¾\x000fûÏÿù\x001fÔöÄøxò/ô=_¶\x0016f«gtúX\x0013êel\x001c0\x0017\x0019\x0013\x0001>{l¤ùîsæFñÒ¥5 z1ÇÏ</p><p>iÀe]ÊyÒsð\x0005äfA·1ÖÜ"sdÛÇBéùK-|ó|äe­¦füÆ.Ye\x000b¯ÀV\x001aß½Ð\x0016ÝÖßs¢\x0000Ì\x0000Ë\x0000Û\x001eS¾\x0014XéUÞÌ³\x0002&º1¼ô>·-fÜÌ×s K|?O×U\x000fÓ\x0006ä\x0006Åe|ÜÇÓáÙÑ3VÏx{©Ý\x0017\x0017ÛCû0¼È·Í<æ//X\x0003êR6²:\x001f:§¯@Ó\x000ehìÂñ¥®®{ô"#7öÆEfdÀGZõ7ú<ñ´\x0017</p><p>/v"½\x0016GJg¨É;õ÷Ëõ2»ú\x0008åÎ´°ä\x0008wª8`°ÒYLÉ\x000b
È$\x000cYvøå\x0008ô`õ¶Î\x0015uI¨\x0000¡ê#´!¶¸~ï9ý\x0002+ÕK	\x0002¢=ÿKñ±ý6/TÐ7qÌCP[ÕE\x001fÕùBk'>Àç:\x000fç\x000e§Á\x0005Rnç¨ä=¤;úàºÝH'Ïí÷\x0003Ç¼\x001c{ò[\x0016°\x0005¸\x001etßí\x001b[§	ïø>\x0005xfÅ3+w¹P\½ó¤´z±n\x001c¯ä½ú\x0004pW·Ô\x0002yYíüï\x00027>à¥Ó\x0017¥~(ã\x0014«»¦b~SªN\x000ex½^XmÔ\x0005Ea¸í0á×W<ë\x000cáL×\x0006¯\x000bù¨m"K\x001fñ¿?Õêì3MXë$/Ï*g\x0000çÍÿtrª0+¯\x0001\x0001åù.4Àó{\x0001Ð7¢\x0001ëÃ\x0001\x0018M¡~)PzX'µ4éS\x0017®äÓnÙ³¾-ê\x0013Iå9ù	\x001f\x001e0.\x0002ÝçÂ4ÄúB­9IUò¸\x0010ãëbMÂ(ÞÈºlý\x0016O¿(Uæø7$äÅw¾{}IÛS·a¦îãÉ¬Ð¤Cï*s,¯óöð]¼Óv~\x0008RmÛq
\x0013ÙÞ\x00134à8ó@ãoGð@1Á_Ò³}\x00077½iKÎ½«çæ\x0007Üs\x000eØÌÍ:\x001e]| yÐáa\x0007 Û\x000fiÈãÜÏÔ\x0017\x0016Êê_7`\x001e²|\x0003g[\x001ann½®ÔÍÔ\x000b¤÷í¾ãdj¤¹]ç´i\x000f¨#öÙÓ~\x001cR&uíyÉO^\x000f÷z	ã:M²9ÖÅ4øÈ·Ý}/õ÷ó\x0010ÇS.\x001e¹ÝÎáÜè\x0010þÐ®GÂ¡ÇÚÚÓ:_tÝ×\x0013\x001e(<ó×,Ò£O§<Â8â9fNñoôú\x0010M\x001e%z8röi{]Â÷pÔ6\x0019]H:¦¦-{¡Ý¶	÷6\x001b`}3}</p><p>êÁ\x000co¦&<ûeú\x001cë\x0001ßZ¢or½J_¦\x001f\x0010ÆsMèqÒ8\x0016Çú</p><p>
?Ôq\x0003=º÷ú¢s|ÏëmïõF¿Pô¯{°®Ïçz«ôð~<Ïñèß\x000fVêE¿\û50é¶¯mNØ(¾ëÃµ;×Ôä'>uµ=Ñ#}ú÷öJ¼øy¬çvß{ýàÑQ\x0019Íôý\x000c\x001dÐ3ºDÏèXmPßp[lWê^CX\x0003\x000f5ÈÒ3\x0013ù\x000cÆ\x000c6ÏoOñ2\x0008±
ÁÛ\x000f?\x0000<³MÕz\x0003·ù´	®Ú;Ëz8uëöÄ¿C£\x001f:ÐfoÅ}ÁåÛ:fØóÖ«Ò\x001bÿYñç!NLðá\x001bJ;±eéÓÒsÜQ?3n¹<ñò,¸Ü²À²À²À²À²À²À²À²À²À²ÀÓµÀé6ÿ}øÌÏÈÄãmR¬±D<®Èx*ã	\x0014çc¿\x0014Øü§ú§'|ÓùÏÿüÏ\x0005Ni\%\x000fýÃ?úÃ?þ\x0017|òÇüÇ'\x0000Ïð\x0007þvó¯ýÏª¾C2Ö4õ¼1c0â\x0019çBOØ^[k4U®¼èÈ¸9gÏ	0gàq\x0001NÆW¤%Ó\x0006ì@^æB½Ôã3Ú\x001cû¡'ó\x001eê\x0013Êó\x001c§ç2#\x000fê1ªe¢3v\x0000°\x0003@ôx1%z¶L~#YûT£XMïvç\x0008M@<ã@Ó:^ÊÏñ¡\Êv¢xÉÏ<\x0002´ys<Â\x001f^(\x000eáIÐÈ\x000fy\x0019·Ã\x001f>òú¼\x0004<\x0006á½MvU \x001føS/r§/ /s\x001cPâ©\x000b½°7u@3</p><p>8¼>O\x0002oÚùkhô\x001fß]×	½\a¯</p><p>ÖxEè¸íf& Ù7Ïüê\x001es\x0008Õß4\x0007\x0006UËéEË\x0006ú¤lé¡öWòÈC~á6\x0002³ql?\x000f\x001fcÿ\x0002yY^Ø\x0013«¦ÿþïÿ®<m\x0007x6ølà9uU»®ü²\x0006/PÔ6ÛcnêBsn{sg\x0005vçØ\x0017\x001a»¡\x000fº[ÇÙG«\x001dÃØ=ùÖÛ×\x0012Ê.·,0-À¼V÷3g(J¨bÐw|\x001f\x0004ÿí¿¾) W_À¿é¨>!uÑ¯	R&I/\x000bp\x0006Låtô¶ÛãBÊ	JÝü4\x001dà¤\x0001üé4­p.<uñ¹aÂM@¯è©|mOÀÉ!\x0019gD:¡¡^é,\x0019Lî\x0013='\x000eS§HÖ»9¼²¥m¶µÒY \x0019+ÙV-¶/´ÕÎ§</p><p>\x0016ð¬\x000bRÏmµ3àsV<\x0017ø	AéP\x000eZ:rBË\x0017%½òÝZ'\x001a{ø\x0013>4v@nÙNÔÅs10åbôÒ¡lÙuÅÀ\x0017ÇÅ:ð\x001c\x000cËòÁ?\x001dáqQ\x0016s\x001dYr­\x0003\x0017XtµÌ=_+òYÁC]\x000e~I\x001dwÉ;~<-mì¶Ç@¡:PÍË\x0003¦¶9\x000fYÄÝ?¹òp0\x001enR¾{ò~\x001e\x001f¿m\x0015X\x0014÷Ä8alÁ15XÒ'þ9|l9Æy\x0010sëïº\x0017Ký~@4èà\x0007\x0002\x0000\x0013\x001eøæ\x0007³¬¢wYD\x0018X°}"+Ç-ñÃ£JÌü¡ÑxålºMyûcvW±ú·ó''iÆ\x000e¡¤O}Ì\x0015>§ßùr-</p><p>\x001fyð\x0012O\x0019xâS\x0017|?0ÛÎ'ztþÔ\x000bK~âû¶îã¯çENè\x000fÞÎ|øSfOÃ\x0003M^OÛËëñ\x001eîe>\x0016>Çê£ì^î>\x001eùw¥'\x001fº¸\x0015(Æ\x001cvrh¥7wÓ\x00179¿
>¦ßqÎ§ßfP6û\òÑ·_#Ðó8º;Ì­4\x0003\x000b_kz&Ü\x0007$Äã±Y|I\x001d\x0002c'×\x0008fðÁ\x0011º\x0016;ír¨ç.½¢\x001fôÏÇ[{ñ\x000bî¢'u\x0013Þ¥otD·ÛÐØ\x0008âIO84m\x001d\x0017[F=E/\x0006d\x0019\x0000ú\x0018ûúÏ5:6nI³ís\x0019Çã_ñ\x0019G/Þ\x0016ÞlU&}gÆy?È5Átìuà¯'PÉ	\x0006¼øÄ </p><p>_öÑ$ÎÙðU·\x0014.yæÃ\x0011\x0017©¶\x0011½ªÍ­Ý~	,/YL=ÜÏÎ$Ãµ\x0015·ý\x00116SïÞÙ®¼Ø\x0016r½ÌL-yV[nY`Y`Y`Y`Y`Y`Y`Y`Y`Yà©Z À)ãÿé<n9Lsn
ñÆôAcj\x000c±\x0013<khSã\x000bxþú¯ÿúä/þâ/äÿãÉ_ýÕ_i\x000bi¿L\x000bØõë_ÿZ«ÿs}ÃöéÛ¸¿®o\x000bÿÓúð½\?Æ\x0018J\x0003á7MÇâùr:À3«ÏµêùTÔº"Ïó¼ñ¶ÓÖ</p><p>yäã'É¸(c>èÃpi/ñV@aÆÇ¶Ç³vò\x0005ãGä¡{\x0000OÆ¥Ìiz\y©1¨Û´£Ê\x0008\x00078UY\x0012"×õÏ9Ä¡8øB	3ÆÆaØ´\x0012ÆOx<æÄs\x001e%å ©?cväù
A'2á<ìD8rÂÓëµ=<¾&?.u¦-i\x0007õ§?0'ùä%\x001fÙÛ¡Èy	òÓ^\x001e^â]ßè\x0003í:\x0011FNæÔ\x0001¸yA\x001dÀ\x0017]ëÛào'ßóò²ú2òóqý\x0003\x0003ì¥ß¥¯±XÒ¶Çúë\x000cV\x001eòJ\x000eT,s\x000cD.õiWÚ\x000b¥­|c\x001eÐ§òj.]-aé7´ÅýÕÛR|®Ö/e`_lN^AíÝP»}Ý\x001eë[ºÒÎáÝ\x0016Ï_õ<Â¸ØÛ±õ»,\x0010\x000bä\x0008M:4÷³N\x0013Þñ}\x000eð¬Þ¨79rñç\x0002:Þ\x001aÑ$¤N½
|'\x000e\úTýüøÄòªç(\x000fåÂÌQ¿bãâh¯&ð,\x001e@g\x0000ç¢\\x001c¨£Ò¤[µÏ¿:o
#]º</p><p>p>Ñ¶à|çùRÛ%^¼þùä·a\x0000\x0015\x0006x¾aÅ³x³ÊùJg|ÅIÓEÅ ±içU~¤ã¢¹ØC¥WåÒO
,ÎF.\x0008j;\x0006\x0018v¨¦´\x001fDHX5·Ó°8_±²aU;ø«àvÑI\x001d£º½\Ò#«ÔÙôA·îÜ\x0017RÞ¼=s\x0011)wªÏÜ½å|Hæ§ÊØ)ðá2³íÇêMÙP\x001fÃ\x001cWS\x0019¾ª¶ª¯ß8)9\x0014ãÀä¸oÒ<¸y\x0018¯Îò6Ù=¸QVéù\x00139I¡
y8\x001e\x001e;Îí©{çëaÿðù\x0001\x0012Ùi?4ÞuÂG\x001d\x001d>¡ÖÓýõ®prS®S¬å\x0007Úùz¸óôpÚ´}tätYáÙÓðt~Âðáó@LâäÑ\x000f||&_ä\x000fëéNù´ßèu;ú\x001dËKZ/ßÃ]\x001eN¹c´ïác¼=-òCÉ;\x0016NZhú:M8|û8éÇÒHÏ¹mÐãYÜ*À¿û\x000ceî°ÏNãÎçóæCw@Y¿±9Ó¹nçt\x001eÐÝßè{³¿Qo\x0006\x000cÒè¾&%¾>ßsp¾Ûð,7ÛÙ[Qö§^ý¡\x0007qhÂÄñ\óx°f ÈC{ÒCI8¶³þ>gúµª£[t¥\x000cÎkô\x0019×çÔ\x0013Ý \x001eÜ\x0018D¿\x0016¾^Èïõ¡\x000f\x0003\x0007<á®\x0013áci¤ã¢oê¦ÞÐõÍd}\x0008[Vï£\x000fªÁñ\x001cË®\x0003é>þéááí`Ç+2,¯êeðw°ûmÅy`ýè{ØyzBÓ%æs&\x0013\x0006¦\x0006»y\x0019\x0011ë¹Qo\x0017óô\x0019ÝÒ6Ù+í+[Ñ¿d+\x0006\x0019 fc:õs¤\x001f¨ÕVß¼\x0011ï·½\x0015ú</p><p>¥xïCî\?îËnïL½;drÔkîf[9Ë\x0002Ë\x0002Ë\x0002Ë\x0002Ë\x0002Ë\x0002Ë\x0002Ë\x0002Ë\x0002Ë\x0002OÊ\x0002süÚ\x001eCÜjÀ\x0018\x000ei\x0018R±\x000cÎ¤v¢\x0015ò7ó7'û·{òw÷w\x001aïhì#Ïn¤¯_ÿ¸}ãùµvùüAß\x0015þQ\x0004¤Ëx	½\x0002¦1\x0006q:ièÈ\TÆrÌÛ³[)sPÆMS.\x000fç\x0018P¼\x0015¹äáÜ¦ÌAÖØ­d2*.+ö\x001aóy>"ó¥cÜfÆM\x0017o]\x001fc<ôð\x001cHVe{Ì\x001d|Ü©V°\x001dÆ8,¶w°M½ÚC¨óY\x001f§ðºùÃ\x0007µ]bÑØÁÜùHÚË"­óD^ÆÇäãH\x000fÅ&áË\	üÝ\x001d\x0019==nv L¯+²¡¤gn\x0003>\x001f\x0003ëíHù®Cê§\wIw=³_z~Å\x000b#ÝWÃ§oþwü\x000f3{»îØÇ6R¬ªÄd6[ÒIöñBHÚN0òg{j\x0007\x000cIó"Ìc1w¾µòZó?¼@: n\x0013"ÜçyYEÓn¥c·
ùÌï`Ghl\x000bí\x000e¾jëh$q\(áèN\x0018×ó²~\x0005è7Ýwä:ÕiÂ;¾O\x0002uÑe«m ÑêÄÄu#RX]{x©¦ä¨WU¦X¥\QTÀjÐ\x0019!\ü4Ñ-ÙèÀd#`.Àî©Nâí\x001bÏâ*Àüá\x0001¯Ä{¥ì-\x0010ôÆÉ¼^39y¡\x000fÇ_þô«¢g</p><p>ëÃ}\x0005>\x0017ð¬\x0016 \x001aÀùJgûµ.E\x0015.àYÚ¨výá¬;áj='¸Â^­1ñ:É^ÜCùZ9gáh\x0019.Ô±çñë#Í\x0011þ\x001a§n)Ço&]V¿Èç\x00064(7©FÜ`|óÛt'</p><p>onèU£+®ó\x0016ò¹1eK\x0015Þ\x000cóÍs' Òq0²\x0011=Ó\x000eô´În_\x000fÃ\x001b\x001fþ£é¡\x000fWÓcIÆv¶çcÕøxõ¤_ÞUó¾ý=N8òÉ;F·4ñõ3:õw,âîÃÇâ¤q\x000eæ0uZÖ\x001cXõºs«ÛÊ¸Þ¦\x001eÎ|êú-c¯xíé\'°ÀhÞ\x0006\x0006\x0010õ[ÞÊëE@RôdàyØ&Ûiß\x0006t'
\x0007ÿÞ£\x0003i¾¾yÐ8\x0014À·Cñ\x0006MKTý 7×"ôë:FwtÎ[ ]ÿ´´-øl\x0006\x0014[E¯Ø\x0015koh·iG\x001d©\x0013º\x000f÷´èÓÛDxïc?ên]OÒ\x0012\x001dù¤\x0002Û1ýö·~Ó\x0016;Q_ìÅÎ\x0015öómäè</p><p>ølÛfòÁ:U;ë¹M!]fud}\x001ce3¾å¢¼U5úÄ~	£''\x001fÏLÐn\x000b\x0003Ì÷û_Â&vê7Z\x0019}£o)á­§Ë¥}P|l\x0005ÍÀ\x000fZoA·s\x0006¹Ø
W¶/@Þ÷Ë¼\x0015ÏjëÏsÈ³ÌO/G\x001byöM[?½äâ\\x0016X\x0016X\x0016X\x0016X\x0016X\x0016X\x0016X\x0016X\x0016X\x0016xâ\x0016¨ú·áfð1¶a¼Ì\x000bÇq\x001a¹Õpb\x001b'	ì:\x001bãæl=ìñ¦ç\x0000«DµnA2F²FåX±ª=Fµú¹*©»=öaµ
ã¶±Qø¡·ËL¹ÉÂ1©Ó\x000fuLêK~)§qiô&­rÊÆ\x001ffÝ.óT~»-æ¸ù¶öÇøöüç¶§P~/3¥"ûX>iÉ\x000fÿqÊ\x001c\x00049üàçü	aËyûczØ?f¿òthd#-ù=/ýÓeÐcêÒóqX()î£</p><p>eÎ¥Ò\Wl\x0013zÌH^nYàë-þ\x0019Ú%¦ïwð¯®­É\x0013Ýîo:\x001fþ¶Ú\x0006ìÕtß\x0000a/þ\x0011V</p><p>êæ¹Haåª\W8áP¸\:Àó~«môÑ,â\x0000E¹w\x0015\x0005L×jM\x0001ÆJ¿ÒÊw¢ï\x0001\x0007ð|SÀ³Ag\x0000h\x0003Ï¬xþùäFÛ)\x0006t\x000eð\«\x0005\_«î£	Á¡ål\x0016)è!Z·*\x0003>EÔD(\x001c|sÚrÊ VüYür\x001cq¡=ýß\x001c§ÐmQÕÂy¤>\x0014×'Î¼÷¤ù\x0004A\x0002@á
ø\x0010	øP\x001e>³eigò	{\x001eLkû1\x001fPôÐø¤'/üÐw±[èÃ×¸jør\x000b¤O"©ÓÕÐóö}\x000fþäFF´Ð×ÃÉîÓÅ9\x000f©7´ó$\x001czL&iÑ\x001bÚÃû¼\x0000zÿ9÷;%xtJèç\x0010À\x0011º\x0007l3`¥\x001c×øèãø¡MÒ®Î\x0013;@÷>ºA)\x0013\x001d\x0003Xr½#\x000f\x0017Ù\£Ð)t¯\x00073Ã²Ñ9ú¹>¯\x0008/\x0010³Vì¶ãGÝñ±qho\x0017òñ¹~ÆÐ®_l\x0019ý£Whô\x000b±\x001bqô!~º=¶3ù¼|mÎR§õñ1Ï÷´fÜíðK\x0012è\x0011\x001d6Ùã;F½ýÖ/ýÔÏ+ ÑGvÄ®ò¬v\x001dÞ2-ÇÕÌ\x000eûeèÁKQv¾®óògéÅ¶hcë¶zqªO¸m\x0005Øìû§·ó.\x001bJ\x000e4[om+ÀÕ¿\x0002¾÷ï
E> ïçÞ\x0002:?Æýò\x0013±Ø\x0005\x0005\x0005\x0005\x0005\x0005\x0005\x0005\x0005\x0005\x001eÇ\x0002ÛÄüÇªóxñN>ÉG1T÷\x0019ÖØJc&¯\x0000=|¹<»Ð9\x0006<Ô\x0002àYã¹[ÀsçÊøgÊ¹wå%\x001dÎ}¹äíÓáý¼éu![ã°Züv¬\x001exû¾,Àq<v,£åçäqÌïS^tÞ¥Ç]é*Ò\x0017hvQ+¼,ðh\x0016Èù\x0010Ú+Î5²Ów|\x001f\x0005uÁ/ð\x001bWý!\x0000a\x0005§´[oØUyúßN\x001e\x001eÜEàØN¤ÃF\x0000à\x0002ßÞ¼\x0007|+\x0018w[íÜg1\x000cÐY5#\x000e­¸îgæ'5I
à|s¡UÏ|'p¬vfÕ3À3ÛloÀóéÅ¶½6 syÉ\x0005,.Ð\x0018Ý¸)WèNÝè\x0005¸UMÐ¹V<WyàXÀsì	ýpTq¡=Äo\x001eöBSÇ6Ù¯Éq&È\x0003È\x0018Tð\x0004z\x0007B\x000c\x0000xk\x0013dÅóÀI\x0018á6È0\x001f<ó`\x001aJ%\x000bí\x0004á}<¼ð§L	x°\x001fí*ô`5-Á÷c:bê;¸\x000fõcyéoMxO>\x000c»7ù)Ûã=\x001cBÉ#x\x000f§®O\x001czÌs\x001e'½\x001cÂ¹\x001e@;_ò;ô"/çwh®\x000b{|¨Ëç\x001cCÊtÔ\x0013:C¹VåºD8´ÃC\x0019Òq±_§Ñ\x0007=	çZ\x0016½\x0016}{£Chê*\x001dÞëÓ\x0005lÅ\æícBðvÙÑ\x000b:TøÑï#\x0007tM\x0015G8¾×\x0017}c£n³á!\x001cÝ ÔÑ¿\x0015\x001dc;\x0000Õ«ÉRÖ×P\x001fÔ\x0001½|¿«ë£«·èæèYgkíÆ3Zçç$úÒXQl\x001dú7­½R\x0019Y¸nãØ\x0006IªAÞ[m\x0017£¹Ý~VåË\x001eèåóc®¼¾ÒJék^ÒP^µ±ô\x0002\x0000\x001f÷ÅAÏ\x0001Áu¼Î/Ð'v×YçB±ãxöyÔÁ}öá9ö5¯ø²À²À²À²À²À²À²À²À²À²À7¶À\x0017\x0000ÏyxÙñ\x000f.cMÆvC>çþ*¾;ú\x0018\x001bc\x0019¹1^ªhÎ\x0000Ïª§V<ÃÐÇ-£\x000cÉå¾$ïKÊPÙK\x0019¨ÆaeûÏ\x001dóUC×Ï£[`µ9t[·Ëñ\x001c	\x001fÊ;Ð÷±å|<©íÜÝk\x0012g?Ý\x001e¹­L\x0005÷ù\x0007BVdYà-@ÿë¾W¾ÚiÂ;¾\x000f\x0002Ïò¯o.´,Ï©îQÁq(²R\x0007Éru°S¶Ô»oDPAÎÞ:DÜ(gmÝM\x0005ôêFÇÄª\x0018ô\x001d\x0000n¬¬\aí+±¼Óªç\x0015Ï\x0005<g«mgÎl·­\x000f^×Ûl×ç±Ý¶W=ÏÊÇÕ,êVK&ð\ù¶Úy\x0001Ïó¨?ÝP:pèÃµ$\x000fÔ@84íÐ\x000b\x0007@ÀXé¸\x0007\x001dúÃeÂÐS_§ÉÛÓÎ\x0013ÝÐÏ\x0000iôLzòzYò\x001eÖk¯>\x000f[ÕþÕ\x0016HI_ÀÞÇHëñ\x001eÞ·§õ0}:à\x00122Èû\x0014\x001f]\x0016iÑã\x0018M=\x0000©«ËI½Ï\x001fòÓÉ§L\x000fGFº\x0006\x0004xîúìÏcâñ\x0001\x001fï§,ò\x0012v»¹çéú¤ÿnè\x0013\x001a]¡Ç®W\x0006\x0004'xÙÛJ\x0019lÇÎ\x000cìÊÀªáè	}÷4z¢sìÐõ ÎØ+:Y?ìÇÊjy1v.²ÜþymNä£\x000b:\x0012ÎªçÒ\x0013ðR>v«¡ü®\x000fF×Ø":Fï½îIw\x001b\x000cèwûc¿×z¶Áÿ¨ïyÅ>Ñ{[Ý+\x00108¶¸~ËË*aV</p><p>Û¿­mÐßê[E©\x001fJ¹/}¼ ê\x001dÕV$O°þ­Ü\x000f'èm`×zg9É+\x0019üBý¤yÆ·Åô\x0000È÷Åò}®÷úÆJ}»\x0017\x0008Æ9a¯j\x001bpòÞ\x0017\x001f°?:û{ÕgmËq¶÷Êï\x001cOtF\x001dø?Ïq?Ê=éSK.àùS-µø\x0005\x0005\x0005\x0005\x0005\x0005\x0005\x0005\x0005\x00056ðêÓZo\x0018_]yî1Ë1_cAFò\x001eØlã\x001b¥TE²æÐ¥F«N?\x0018Òh.^ã/¯zþÜqÎ§µçÛpa\x0003gÆb\x000bxþ6ÇàskUÿ\x0003\x0010J§Ý7ÌÞ¯G\x001dÉÛ)öÑ¯÷yuÜ7Ò?T×ònÕ\x0015yCßE\x0005\x001eÝ\x0002ôÁî»\x0002u2(¡Ów|Õ·'ºõuÝy~#à9 34\x0016QPkUâ)@R&¾íô@Ûy\x0014+?¹\x001dßJH\x0011o·Íß ó9«c¸AjRo<Ï\x0015ÏªDÅi¿Që··®\x0016àÙßxÖg¶Û\x001e+/ÇwÏÛ7O´ÕöµV<g»í¬v6ð<V<W\x001bÇ­9õJ¹Õö'¬xf]4myVc\x000buìéÿVÏzfÔÃ!=õêe£hÞ]N\x000fzZl[úþZ¨Á	\x0003X\x0001\x001dt\x0002É~Oô\x001bppØÛJ\x0016BK]©³Âá#½ùè6ht*Í\x0014	8Pz\x000eÙCü&\x0007Þue(U\x0011ú°µ-é_g\x0001ú\x000c YõÅ¨\x001a\x0010´CÃºw9=\x000c?ç@JÊß}ôèi	Spw©»Ó\x0003XA©7r \x0001\x0017Ù.8Ä|ÃÝÚá\x000fí²\x0008ûü #:Pçl/a¯æ4(ÊJaÇÃ2ÐxÚJØ´~·pÒ».è×Û×õï:&=i§|d\x0000Þþ\x0016½Û\x0015½ÓÎNQ\x0012\x00198dF>õ\x0001z«e\x0003Ð3¸¼¶ÚæXt\x001b x§±å¦õã\x001f>\x0000NøÓ¾ª[u%\x000eM:
¸ÛÓ¢74>rh7a./\x0004\x0000ÿüó¯Ê¿~ýzkW\x001fw\x001câ*C9ëa{0yq\x0000<­ªý\x001dgï¶\x0011½\x0000g_¾|¥cö²\x0000è\x0002kÇsÛÙ\x00064ÇfØÏ>Ïm±o¾·vX'µ\x0013Ýtÿ«¶©q\x0006Ù"[ç\x0014÷Â\x0002³ÂY ù¦«^*(ÐÜÇ¶ìÅr96P¾ã|©gD^\x0016È\x000b\x0003\x0000ÐäÙ\x001dÿ#ñ#$eB?ÂÎ½õÀå/\x000b,\x000b,\x000b,\x000b,\x000b,\x000b,\x000b,\x000b,\x000b,\x000b<+\x000bl\x0013óÖ*
=·P$Òx"ãÙ»)²á3­4d1øì±F^JfüUÄTc/V;\x0003>÷q[Ò?\x0018b\x0001ÏOç\x0010º\x001e\x0000Ï(s'Àr\x001aTìÕÙÕíGÙ-o¤\x0013¿3Oe\x001a[\x0015}°ºèQ\x0015®eÇ´\x0000çI÷½î\x000c&¼ã«ó$y¢9o¸ÿ\x0018xÖÄîDÇgu¹9ùÔ\x0015-y#>d×
+õl£LJº1fáÆÆ6 }ÏF®ßßb óøà\x0000\x0000@\x0000IDAThÕL«¨V%©X\x0019Ô\x0013Ü<YñÜgM²g«í\x0013&\x0017k«í_\jBöll³ÍvÛ¬x\x0006¤6ð|ám¶5Q|%yùÆ3«ÑÚõ\x0012B\x0007QÝ¡ÒúÈgçñ[[v\x0017ðüÞ¢âøá 	WÂ3øñ\x0011\x001e=íÑÚÓ\x001f\x0010«Ò2«\x001fýx°d\x0002þ½&Ïk\x0012]î\x0005D\x000fÐC\x0000§WrùSõc&ö+>LÙÁ_½YÍ¬:ÕG\x000fênéÊºí¢×¨³@\x0011vWPDõEöQ\x0019·¥~E</p><p></p><p>ÅUôQ,`Pk¾=ý$îXøXZø"§%\x0018¤r\x0002e'¸Å90ë#ñ;MøXýIë´Î5@7su¨sÕõ\x0005d\x000e
pø¤£Ù2xê6F¦)zºnïfÙÊØ\x0014À\x00190m\\x000fto´M(9m_WÍÈ&K Röªk2=Ø5øp§¯</p><p>ò»Ýz\x0018ð¶äí}/O\x0018ã\x0008Å¶Ô\x001d]bë¤ÃSùØYß</p><p>ö@]wêÖWöö$\x001eÀr\x001fN9Ûtê^A¬ËöÂõÛô®Ñ1:GÿÞ®\x00124~ö6Iký¹lÈq¯\x001ag\x0015ò¡}ê>Àý¤ú§íúèöé¾w8
"zéWég\x0000Ï\x0006I÷æC»Íó\x0011\x0019·,ôQÓ\x001fºdËì²\x0011éÔ)}Ot¼ôWÔ¶\x001aÇ\x0019°\x0008ä\x0001ÎcÏké:\x0000®­W^Â\x0000d\x000eàLßóË\x0003>WÒNUVå?ýçsù\x001dâ?½¦Å¹,°,°,°,°,°,°,°,°,°,ðÄ-°MÊz;jTc^ÆOe3¶b<êpÆ\x0019s2î¨a\x0018C,ªÜ¨Çc$ÔðLü\x0006<SO Ô3p¿\x0002<\x0013^îû·ú_õÁêw¨ÛòZpôv\x0019ÇónëÏ0â7ã$¨ÜÛ?­\x0016ü¼ºº\x001e·kX)Ë\x0002g\x0001:q÷½æqnä\x001c)´\x001d_ÝÓ'ºÝãtïùÍü7cÅ³_&MùÃA\x0001QK\x0007Â\x0015$Í¹Î2/'oTJ#Ã©¡.i	\x001bð\</p><p>\x0001iR\x001e\x0000ÉÆ
|æ\x000e(çë´OÂPçw\x0002&\x0017ð¬Õ,Y,à\x0019Ðo=½ßx®\x0015Ïgó\x001bÏ×\x0000Øgàù®\x0015ÏXB^º@?
x>\x0018é9¹íïcò|FãX=üñ*Ë\x001fúp|Õ­ê£\x0001\x000fñµÅè\x0000§*
Ãç¼Pßå¼)Ð9ç\x0006çþ& ÅÊ/ê¢ B\x0015\x0018qÊ:L§²u&Sg¯ßÙõk]Ö¡¤û=Û~x¿fú^¤¥\x001f£\x000fa÷?kw,|,mß\x0016äÜåöyû8å¥\x001d«7i{¤E^\x0007ö\x000c\x0005`\x0004 àX@?VBS\x0006]8Ç¥ÂHÃm\x0001GõúxéªÊ\x0006Ð¼\x0005´´\x0000Ï\x0000Îó~YRK¬ÏcëAx\x0007z¸þ©«ÁSVæÆÓ&¦Qöt°ÖäÜ¢zG<Þ:ºî\x001c#¨m4ÐÔ½×/ñð§¬u£ïÉ\x001akBS'vÇhçÇ@O\x0002C¯\x0003:^\x0016B¿Ø	\x001a}¢_×?yPäÇïu@©W²³¥wtSÜ(54u@£G­ô>è\x0006àsì±Oêfõrï?ÉetÇf¯lÀ³û'máØr_}òìâ1õäÜàØJ§²÷MñðMî·J\x0017%/-¬~Þ@sdù\x001c*\x001bÒ\x0016ÕYí(à9[£§\x000f\x0006p\x001ev\x0014`ÅVä³~\þãE°\x0007\x000ep%¬eeeeeeeeee§fmýá\x0014g2=c7êbÌ\x0013qdâPÜn¼¡!\x000b£\x0016\x000f}æ<\x0000¤á\x0001Ëë³GÏ\x000fx=ÖVÛ\x001cî'àª§.L\x0018×ûsÒsÿy½.êèõõ¼\x000eß§æÁ»Ü²À·´\x0000}·û®Kúq§	ïø\x000eð4ñl÷DÝî\x0002-j\x0008\x001c\x0005tËÙÀgWAÜ<º\x0005Ö¹Ut;\x0019}ò[c¶\x0012Ëg<ø\x0003t.\x0010MI\x0014ÐË!ÇD7>OdfÅó1à\x0019\x0000\x001aÀ\x0019àùò§rÂVÛ§?òç±âY\x0013¶×\x0003|.Ày\x000f<W[e ôÖÚð1àY­\x0011;¿\x0000ØZUÍÛTÏÆq\x00000Æ Ï¦]4Ä}ðð\x0006ñ0
\x000f<ÄåápRj%\x001d	ð^&iÅ \x001fÈ	\x0008\x0001Åeb\x001fð\x0001\x0017¹\x00159\x0012Oú¾Ä÷\x0014þ¤Evhd=\x000c¥\x001f\x0002¦Ó\x0017ûÞ->\x0012ºï#ï)íJÚ¾u,~Oþ1.ïX´¤ßE£ë1\x0018s-t\x0002~\x0006 ÇÇåoëÙuH]¤åü\x0006$\x001c`2$+9Iàóù¼6è¾Y/¢È.½þè­phx ÙÂ\x001aôÞÐ®\x0013zõï8U§9~Ôµ÷ÈìÔ\x00050xx \Âè\x0012g\x00012ë\x0019âÜ`s·iì¶§±}d!7uv]\x0012&\x000f½üÝa3¹IÙÐè\x0007Í1ÍqÄn±\x001fáø²¯VµC¥NÕõv|96âß¾}»\x001d7ãÚé®××PlvgUðemK}¹\x001dKtÂ±\x00057r]ó\x0001ç¬bWÛÍç0mí6¨ÊuN\x001c\x001eOx&ÎwoTÏ\x001b}Ëùl¼ô¼à\x0017«TSégÐÛ/3ôv¥}ÝÆ9þèº¡\x000fïÒ/C\x001f¾ÆUÃ²À²À²À²À²À²À²À²À²À²À=[``¿g¹wëcO÷¢IÛa¨ãáÎ\x001cSy\x001cdNò\x000c<>kàyÃö}ãûÓ!\x0019ãsÌBæI\x000b½+t\(ü½Ì§ä?ôsêB~Ê\x0011^nYà[Z }7´ë~ÚiÂ;¾º\x000f&Ot»/j~½\x0003Ï\x0017ÊSJókº×iÉä\ÂðÀ&Wyú½©\x000bÂL!Ç%C)2¸¥Èûò|\x000fQÀ\x0002³ê¹\x0000gMTú;ÏðK#\x0017«ÜDÙb²V<+\x001dðùpÅ³&kÙj»ç_5àùgoµ]À3àó¹V:Ëk\x0014\x0000-¶Ë£¥Â®\x0013Ý­7À3°²©ÂÄ\x0005³\x0002: ô\x00029þOÍ=\x001eð	x\x001eîèÇ{åúC¢\x001f\x0002óPhÚ­[çÂäßS:ãºì¤uJîzü®pø?&;|_O¥ã\x0002¿Þ,!ýgßOz<áÐc*F\x000ey=8iÇú|dÞE?VWäo\x0002\x0006S/uÏ<I\x001cø».\x0003\x0005¸#­§ß\x0015\x000er¡Ñ5uFPôL\x0018NÑ=y¤u\x001f¾ÈN;¢\x001b4Àiô* T iâi'2öõ#/iÑ!:\x0005T%?yÑ-ú¤í¦¾±Z\À3zÆ'?mH\x001c#\x001d\x0017Ý {\x0012ßÓ½½JÐúC©\x000f\x001bv°´7ýôÜÂ*a@ç\x0000Ï±]l\x0014}îãÍªc\x001cÍÂ#o/àøm¨µ-õ\x0006X¯ç%x-º³"\x001a ß:AmWÿên²\x001dO×Mù«\x0006:#++\x0003.ÛÎ\x0002¥\x0007ð|%jçã\x0010ÝCy\x0011Ñ/%NÀ96ìÔ:'6\x000fE\x0016õ>K;B\x001f§ÖUË²À²À²À²À²À²À²À²À²À²À=Z``¿G!±\x000c.t\x001f®ÌúÉØ1S³\x0015c Û\x0018ÁI~
:#÷±ÆGSÓ\x000ba+ùZñ¼Æa\x000fgçû¬þW}0ýpÜNwåíÓáM¹}^Ò?$ïCy{ywÕu\x000fÞå\x0005\x001eÓ\x0002ô÷î{Ýé£&¼ã«û`òD·û¢æ\x0006'ð|rr¡Ô\x0008¡¼ºõ\x0014\x0018\x000bÎa\x0000çq«RV?Q«T¥\x0019pv\x001eaÁ·\x001bðR5©ÉÃ´Ô¤²f6\x001bðÌµÆu±¥°'</p><p>wÀ³&Eo.ØfûEm¹\x001dÐ¹¶ÚÖç³\x001f½Ýv}ã\x0019ÀùÈçú6³nÜèæÖ\x0019\x000b¸\x001d\x0001jâ¶Ö4ë&]ù¢\x0000Ðü^\x0003O¯\x0015Ï³|÷¡Ç\x0001ëNý$@D&¼C1S\x000fÇl½\Oëü)\x0007er\x001dú¹è{þ\x001eïáèðí¨®#\x000bxþvæÿéÝ},Þy	÷~x,LZ|ÊRG÷¤'pxSö.</p><p>_ò²¢Ô«HÙºxÛ\x001düËùri3´\x0003a\x0001e\x0003<ö¼</p><p>\x0003®
P¯ËH[ÖÛÒõE\x000f\x0013\x0004O¼ëN»²Z2]þ^§½®û8e)ÓiôF§è\x0011[%=||çèK>®×\x0011;NÐ4[*ûÛÄµ"W@i\x001c²ö.:&=<Ô\x0017ßu^I':"\x0003yñ{\x001b\x0012ïv/<	C#§\x0002ã§\x0014ê,Ðù­VWëØQoôM8ñþ|fÙØÎõE²Àç\x000b\x0001àçcõrxPÃ²xÖÑ³âÈ1µR©§ì¤ç$¾ß\x001c»°=v¥gÀçØ36Î\x0005H¿û¥V<\x0003<û\x0018Óüh\x001bMÝù®¹¿åL¾WaïífÖ×ö$\x001e\x0017\x001b'þ°4õ>lmKú²À²À²À²À²À²À²À²À²À²À\x0003X``\x0000Ù\x001f\x0010ÙÇ.wgqFnÃ)àá¯Ç5öÒ\x000c8\x000c}X¼ç\x0018lÑok\x0001uÌ\x0003à\x0019m2ÞzuSñ®¼¤Ãº/¼}:¼_2\x001fª«Ë&¼Ü²À·°\x0000}¾û®Cúq§	ïøê><Ñí¾¨¹B\x0003Ï\x0006e\x00123\x0016CA\x0017\x0006^ev±h¯Cá,¶~¢:\x000c\x000b\x0007%í\x001cöjgrk½ðXí¼\x0003Y3lp\x000bxÖdm¾ñüN<^ñ\x000cèlðùR`sm·­ÏlµmàÙ+¯4)Y«\x00015Égèõh\x001f«Ñ²µ¼ôg³Ági-ÝXý\x000cå:UÏµâ¹d­­¶Ç\x0001\x0002äñç>É	ðc´\x001b-\x0013ñ¡É#²¤%¼§L¾ÃÛÝçÄ;/²¹Îs,ÿ~ÓÔ\x0005<ß¯I\x001fXZúM(Õõp¯>éû>Õã	Rp|ä!ëc>¼ÕÏÑaI'i\x0006gßÖVÆi©»ó$-uD\x0000b|\x0001H¡Ý\x0017\x00008V¿?åüÄ£gtìqt$\x001eÚÃ]\x000eízóæMyx¢\x0007º±íó16À®Ñ3íîò\x0013Ný\x0001ð»^ð\x0010ßû\x0000¼\x0001¥¾Ô\x001b\x001d³EuâP\x0000gVñ^\x0002¦ê²è\x0010J¸ÇSGÒGÇè\x0015Ý£\x0017éá
 Ñ\x0011=­Ë<ÖÝ¾)\x0003ÿþø¢GêïºRß[@çÚjûj;¯º¬è\x0010|Àäó¶R96¬¼Zá\x000c\x000f¾Ý[\x0014.\x0010ZÏ8ú\x001f¾s/öÔ±\x000bÈ|ÍÖÞ\x001cKoñmÛÍ0oÚ»=]\x000eï\x001efÅ³Àg\x0001ÏÖo®¯ãÉ1­c-Á/¥Agøc\x0003h\x001cÇ\x0006ãxxBÃÿ04ú>L-Kê²À²À²À²À²À²À²À²À²À²À\x0003Z``À:èýX¥Ç{x\x0016a¶\x001eç_È\x0018\x000ejìÆ\x001f	þ7(Þn1íôôC4F~­x~BR\x001dó\x0016ðüÔ¿SÕX¡w2®e\x0007´Î/.þïU¥ovðïsgM%ªt\x0000W-ÎaÝv|.¾T¨É\x0005Á¡J¨\x001f7À 3¥Ó ñK±kù¬.fëlOhJ¶ô6Ûº*#¾\x0012­ßÚRQ\x0013¦Ìzîg¯v6ølÐÙàs}ãùµÀgùW?ÎÕÎ\x0000ÐÈÑÌªgàï%\x001em]gµz\x0000Î</p><p>K\x0000Î\x0013|6\x000fÀtÁÑ	\x0010Nøù¸qìåE_ÇéàDy£î\x0006<\x0018Þå»\x0006½\x001cé(æá²Ó.\x0013à yòôrN¯¸YWRö²\x000e=V¾çß_XJ/àùþÌù\x0008öýf\x001f</p><p>ûô}J|O)OZ/0´áM0²¡\x001dàëáäÃKz¾uËêÌ:ÆÏ+_\x001e¬s\x001d°¯À<îwf¬*\x0015\x00089¾×k0
p
/\x001egðKáq?®è;¾w;A»wè%/}Þ\x0007h\x0006PUZ®;E\x0019d\x000c¥£¬<m#\x0008@øîAx\x0003\x0002ä\x0005Ð
%/ßk6HI»ü¢åÙ®±WtM¡ÝS&Ç#¶\x000eMYhx Ônøè\x0013p<ºCÍc°ã{\x001d¢cÒS_Ú\x0011=B\x001fý\x0013F¯n\x0013êßëÚÓÈÃ¥oÞUÏ^?×ïãÎq¦m<O\x0015\x001d lê=¤\x0006Ä½Ùá+se}u½Ò\x001fTDF¶Öööl9oüb·Î\x001e@s\x001d_¾ã\x001cðÙéá©ófô=¶Ù¦w. J\x001f~'ÿV}õêÔ1¬öÌcíóGÇ¼:\x0000én´çÔÙe»\x000eìëúÜçÌ;¯\x0015[¡\x0007	D©Ð\x0007©d	]\x0016X\x0016X\x0016X\x0016X\x0016X\x0016X\x0016X\x0016X\x0016X\x0016xH\x000bÔ<âCV°=\x000fÛìâNÚ2v\x0005ñ\x000eã.¸+Ê¸i\x0015Ê°HÚb\x001bÙ5ÿ[¹Ïà\x0007\x001bÑ~ÆÝûî-°á\x000f­s~÷Jª£?~*ûâ[\x0016¸w\x000bp^uß+È5²Ów|\x0007xx¶û¢îT¿ùÿúæB³rç*s.</p><p>ð\x001biz\x00050¢ëFä;_\ÿÎsæÐÁa>µíZ\x0017ü	<3Q(¯	SÍ\x000fàYLº\x0019VuR¼¨&\x0015ó=¿Ûßxî+õg­v¾ÔwÏ\x0007è<g¶Úßx¾ÌÃ\x0015Ïn'õYwM¶\x001eÒE4Àó¹&ïkÅ³¬r&Uá%·d±\x00117my6ntÆíÂÿl\x001a¦è8\x001d(\x000f×6@zÀ£?\x0001&
O	Cã<9Îià\x0007ÂPò\x0017ÞërOzøR.4éÐci=?²Br¡I\x0018ÊÉæ\x0014\x001eFþú\x0018\x0016Ø÷¡ÕÙûVÂ¡)L\x0003O·û=<á&Ü\x0001CÂ\x0001\x0012\x0003ðuJðsµ\x0007xÓO]ù¿Ý?9ëããÞfÐN@©î?g\x0002
\x000e MàYOK; ÄïU×V÷^ú\x0016Ð|¨{ÏjO\x0011 6=¤ù\x001bQ5©ÚD{Ð1Àm\Ý®;a\iô-³"8üØ5¼èEùî»Ìª`ü¤\x001e¢ÝNÑ5zv\x001d\x000bL­öÊ\x0016ú£þè³§]·Ô~¸^wÒ\x000el:Ú\x0011¡CoÓ±päbÈ]B£SèäµNõ\x0004§g\x000eìaÐ9ý+Ôý|tó(?î;n\x001f\x0016ÂñK?7¥O§\x001c|óÅ\x0007@ç¼D\x0000Ð,Û</p><p>l\x0006p&<u6uwß¬ZmcOÒ¨·\x0010O¯U­µ\x0006è\x0015ÍÛ¹¢öæ~`[SÚí 4Ý¡üN(ü¡¹Åq;éSr\x000fýbA«à²À²À²À²À²À²À²À²À²À²À·²À6ÁþÐ</p><p>xtvPKÆo$öð\x0001\x00139²«,E²óàjU ®æÂÕpÆ\x000cÿhÇ­,¾~¾Ä\x0002\x001bö@ÇlóKd}weZ_üît[</p><p>ýã±@Î­ÐÞò\ü;MxÇw§g»¾j~×À³@g]|;ð(&ë¢\ç·n9­´#§|åQq.\x0006¦u£ª4ÃËpØi\x0012]²XñÌ"Ógº³×ä¼iòUÏÜùjÅ³</p><p>¡MiÅJ\x001e\x0000]M6^-«ooµmÐ\x0019ðùüõ¯jµ³ç\x001fjÅó\x0004\x0005\x0014K\x0016å½Õ¶ª.´:©¿¨RH
ð\x001cÐ\x0019êtóÞH·\x0005<s¬{<à\x0007»L~g\x001bÚ}·\xS®Sø2I<LO#=eBIÛ»äõ²	\x001e+rû¼ûëì\Àóýô\x0001¥¥OîûÏ>~*)Oþ]á\x0000~\x000bïÞ\x0007Ì\x000b
8\x0016\x001a 2ñ	Mð7\x0000\x001c\x0000\x0018uu_ç\x001ei\x0005\x0019\x000c¬Î\x0001\x000bx\x0006\x00084h\x0016svG®î)w|\x0017W¾Â\x0001\x000bÀU¶2Î7sgX«°Ã§ûÌ°¹ºÎ:Dõ;ô×ó@\x0001|¬\x0010Î*áÃº±q\x0000UtEFlMÑ\x0011]ãóÍhhò ý8"#íïu\x0004¤O^·sÊÂCÙNSN½F+Á¯´Vö\x0012H\x001aÝ èÕiÚ\x0000E6.õF^§É\x000b\x001f:Ð\x0007³\x001aô´5v</p><p>¥\x000eÂUg{x¥ÉN&=e\x0000]//´Õ´>3\x0002-\x0010~6lÁwke°têv¥ÿÒ4±\x001d8ë¥ºë¼A7ëQ/Y³Ê²\x0001¡ØÏ+mK÷S÷Wt>û`ë\x0007ZÐ\x0017ô\x0019\x0018½Ïp¡íÀeJ·KÏiÓîî/ÛêìzR£19ßcs×Aÿ\x001fR<n{ï÷3í@âuûÁ>÷Ëâ\x0015úeRV©eeeeeeeeeeohmý\x001eu¸c±Çó}ü¤1
ÕnC\x0011ïª\x001ce90E\x0016ã§Qö<Í}or»À§\x001e¦QÏ²aOýÀÜ¡?\x001d³û;ØTrú`èR~)û¬,ÐÏ­Ü\x0004ÒÀ\';M8<P¥Õ}0y;ïô¯þä_Ý\x00008\x001f\x0002Ï\x0014ó\x0005\x000cA"È2\x000cKOô»ÝÐ¢¬\x001b`\x00087¥\x000egéPÀó \x0001\x000bVÑ¦¾n~Ô$ñ\x0001ßS+ï;Ç{µó?9¹Ì7µêÏµÕ¶x\x0001\x000b|fR_á¹âù\x0003À³îÆ´U8\x0007Às¥K-QV9_£¶ÚVøù¸q\x000c··OËtäv'ÊÃ¶}\À\x000el$=<Ä
\x0004¸LÂ¡äã:?ñÈÎ$}ÏO8\x0014þ\x000f¹cú?yÈOÞÃQ.</p><p>:é·\x0007å«iIþz\x000b¤_¤¿¥ÏDò>ôc42ÈëáÄ³Ò5À3<\x0006½L\x0013\x0006\x0014#\àÂ¡\x0006Ï\x001cO8|)\x001b</p><p>X\[c_\x001aÐ£\x001doÐ=øyW<çgÊÒ\x000eÂñ\x0007\x0014
@\x000eñÑ34mööGVdG×Ðèp!ð­´_\¾,ð4ù\x0012Þ;ô¡N(ºDçÐÏ]¿®\x00132\x0003Ø\x0006¸åx\x0016;F´å\x0018Ýó\x0018\x001cÕ·¯ÞJ7£Çô$-¶Æ.Ðè°§ÔÕë\x000bè\x001cýÃ±À§ý¤%|\x0017\x001eý8FN(ÛL¿xùêäåW:n/\x000flT 3vcK÷¼ô0ì¨æ¨mö\K#/u½g«kéÝ&hÌµw<\x0005N½
:¿Ã®Ú¦½V:\x0017®s©Êsÿ¢\x000e®Û©sOý¤NÊ=OÕ\x0007ÏÔ&yc<óõüV+ºÑ]<ðS\x00152ïÐu÷Õ.î\x0015úç\x0018âõ¤\x0017Ã­VÏ­¼/I\x0018:G÷/\x0011±Ê,\x000b,\x000b,\x000b,\x000b,\x000b,\x000b,\x000b,\x000b,\x000b,\x000b|[\x000b<*ðì1[opÆ7¤e\x001cÕók\x0010´åy¼´\x0018 \x000båer§XVÒ\x0007Û³ k\x001cö´\x000ecæ}[_¤\x001f2§þø´ÊÒö¹XóªûÞ®ôÍN\x0013Þñ}\x0008xþÍüW\x0003xÖª\x0012ÝY\x000eÿ\x0010$¡ÛÔ\x0010r%µÃ§ÿ¸\x0008dBòà\x0006f°67¼Pç+É®M\x0014Uw­¸\x001e´îvðÜ\x0000hñ¦y\x0000Ï¬"Û\x0003ÏsÅóË\x0013M³Å¶¿ó­¶ªUÏ§õgÎ\x0003|.Àù\x0013çl·o;\x0007|Îªè\x0005<÷Î÷Â\x000b<c\x0019&Ã3ùM<\x000f¡¤ÅÁ«	ô#áðíi¿Ïë2w¬nò¾§=/ºEnd>\x000c=\x0016ðü0¦}\x0000©é\x001bÇD§O%o\x001fOú¾_Ý\x0015§|<eá\x000bè\x0017\x0010/\x0014Ð,aè>NZtï4r·ïË\x000eP/À#4\x0000ih\x0001f;p´¸´çX=ð [@Òè	o×¿÷r\x0011»ìuI|Â¬t\x00060½¼xQínÈèrSß^èüc4rºN;Àí'-zBáÝ»®gÏ\x000bï\+àyl\x0001nÑ7´È¦^äØ>}Õí\x0000CÇ±§óåøw\x001bPÏ1\x001f\x001eê$Ü]ä\x001e£¶\x0013«_ÈV[ýÖÃ:óMæè\x0015ûÙÜ\x000eï/Ô_@s­Ï9\x0000õË\x000e¬\x001a·þ\x0000ônuí"­á#¶äA£\x001b;ð*¿\x000e+±z¿P«ÏÔ.úÛQå\x0004@\x001bx\x0016_gtV\x0019Û.çÒêX:\x001d\x001dpÈz|\x001e.f9òF¥Ü¼/I¬Ð/±Ê,\x000b,\x000b,\x000b,\x000b,\x000b,\x000b,\x000b,\x000b,\x000b,\x000b|S\x000blóå÷¨Å\x0018usp\x001e_9¼\x001f¿Ôxª\x0017RøvÚ±ñ\x0007òîJß	|òÑ´3ôÉ7è7`\x0001ÏÏü\x0000¯æ}S\x000bÔ,4\x0008íÊä\x001aÙiÂ;¾O\x0001µa\x0001¿`Ê/%J\x0002ø\x001b·¶
Ræ\x000eæ4¸ºó0Ý*:\x001fÀùJ%ÙÞ\x001a\x0010ÚÀ3¸âbÒ­¶E«L\x0015A\x000bn+Ùnûò
<¿<¹ÑäkgV;{«í\x0005:ß/ð\ 3ß\x001dÔäê\x0002é\x0003OÙ=>ð\x001ckåa1ôóp\x0019^hÒö´ó|J8åñ¦þä%¾§ä'
yñ)÷pT'ü\x0002\x001fÎ¼÷,9}-4âÓw÷pòÑ½cñ=G\x001c>h\x0007\x0017Ã|xâ©p×+áÐla|qa ôw\x0001)¶E\x0007ên\x0001%IK>4é£_ô&­\x0002ãúRç1\x0002vÝk«m\x0000ßsÑ!õw\x00000é}pt:¦Gôé\x0014½R?úD§CÃ\x0003Å¥ÍèGø\x0018
\x001fù¥çuV;¿Ûdt}	G>4uöãÚõEHøJàøI\x001a\x0014nÔ\x000fí6MßouâLoÁ~{%x¥m\x0005\x0010></æ:'Ô1y4×C¶ãL9\x0017d×_´lxuòæí·Ã£w\x0000éP\x0003Îî£\x000f¸Ë¹Ñí9Ï\x0015ÔE/È¥Býð(¨î -ÃíKFÎ£¿´2¨ãËë»æÞ.\:J\x001cÛª²å
<\x001fÚeê0C\x001cG\x001fËö5¡È</p><p>ý\x001aY«ì²À²À²À²À²À²À²À²À²À²À7±À#\x0002Ï\x0019ï\x001ck§6·ÜLcì³Ï	É\x001bÃÁÆèñaKx\x0006Á´;ô\x00194éY7yÌY<§Òÿx\x0001~õÃçtT^[rnö\x0016¤ovðïãÀ³V;«³kAº½nHÕñýËIàùJ\x0007hvE¡·\x000boLp;\x0013¡I¿Ä+Ýá®Ä	¼Ì¤â9[)r×ÓÄ¡W;×l¡r6nèÇV<³åö\x0006<kµó|V;\x0003>_hí³×¯ïeÅ3«Ùj;«\x0017ðÜ;ÜS
{à\x0019Ë}|òÛö500m½''é¡I\x000fíé½î\x001e7ñ=íyÈü£:á\x0017ðüpæ½gÉég¡O_ÚÅIÃõò=ì\ÿ\x0002êe;ê\x0000}\x0005B©¾\x001fÀ\x001fé\x000f@Õe\x0011\x000e°ø\x000e:&\x000eõ6Æ\x0002\x0005ÛçÎ\x001b\x00005ò ¸Ô
E\x000eDFw(úM`Ò`\x001aeð{>8h×q¯O@Üè\x0016Úù\x001c\x0016\x0000,0S\x0012K¿èõöí[oOÞ¼ySv&\yÚ^Ùv6\x0008\:dkäZ¹l@9«£Çíz
²&½ë¶ÑÎØ!Ç0v</p><p>í\x000f?«¯Æ6ÛðY\x001eÒ&ø¸¯·×O8:@ãr<:~¡Ñ\x000bÊñ¶÷</p><p>aVå\x000e`{\x0006°*Ùèq^«½õýfVË×öçl.-¼±' 3ÇÉÏHÖkêâãQ 0@òè?Î7h¬­>UyõàG?ãZ[ÿú¹©cýûßÿîäw¿ûÝÉïÿ{L\x000f\x0008«gÒ?)#\x001f°ÙÛ|óbáÜò»Ú(Tyã\x0003in®ÒUçÙð±K§9\x000eiW÷{Î×\x0005@ûR=Jú¥\x0002ÊÄG¿ÈiÕïèv¨ßá3£\x0015úÅ\x0017û²À²À²À²À²À²À²À²À²À²À··À7\x0000=;l:c§\x001a»éw?¶éñ\x001e¦Ä>N\x001aÎS\x000e5ºsÂ³ùÍø+ôÙ4ì6Äó\x000céÛÏ§ô¿\x0005<?ãùT[Â5¾ûÞ\#;MxÇ÷%À³Eirn»\x0012ÈØ¹u\x000bòÝm§¨oNá\x0012PÑÀ³ÀgÉ}/9\x0000ÎLºBYAlðÙB¸U\x0016]È\x0013Æj»låå;Ï\x001dx®\x0015Ïcµs}ã¹¾ï¬\x0015Ï?ý|rúêmíí¶%\x0013=ðT¯V+@</p><p>¾@gé¶\x0001ÏL\x0014\x0003WøDIA\x0017¶ðæ»ÓÏÇa\x0011\x001dmBú¹´Ì}Ûö\x0006\x001e®eØP}Ëd«F]n¸-Pñ~,ÿ¸¬pÒ]OèÌqh§Dõv\x001dÞM\x0005\x0007zÜaÎÁÈÚ\x0002J\x0018\x0013ü{±a½7J\x0005òÕ\x000fy\x0008Yî)X`?8ºkÓÛÒË$|\x0017M9@Ð¡\x0005æ	|¢\x000c\x001eP*\x0014þ¤\x0013Fî?\x0004@Âç|\x0011X\x0006ÜËÎ|Ä»\x000b8Fý\x0001\x000f\x0001I\x0003ðõ6ìå$\x000eÞÄ\x0013þ\x0018íe	×*V­dµý;¾\x001d4ÍvËsµ3íÁAjuª\x000cº\x0001m\x0003:÷4Âä\x0005à.P\hEÆOah·SìÕmLØ¼¬8\x0016Ø«­¢\x0001L©\x001bùÑ'4ºg¯\x000b2£C§=ÜõØó'N³\x0008ã¢\x00034vÝ 	'Ïü\x0002ÄõÜQÏFã:^ÂôSupßFWýÅ\x0016®Û+°o¶o9Ï\x001bø¾3xQ®·UÞýÑ«õ­ìwo©aTeZMÎ6s¿¬</p><p>\x00050»M¡Óî}Ûl\x001fö/Ô«}q¤\x000bKýgd#\x0003ÙçWl6ª¨ßcT\x001bF¯*©\x000b=s\CGvÑkõIÑce¥}°Å´,°,°,°,°,°,°,°,°,°,ð=X`3¿Gej®ëPÇo\x001eÎ1Ø!OÒk<ÎñOÊ90ãI7½y¶\x001dVñb\x0001¾Qý«ÚO·\x0000s¾Ì5ÄzÉïþ\x0017ÿÐ\x0018Ä÷k¥Ù÷`W¡]§\';MxÇW÷än÷\x000eÝoüçÛ+a7èÜ</p><p>êÄ@>ùi¼	FZY2w.\x0010³´Òõ-¦wºÃ½\x0013õgM´*\x000eø¬ÙÑáUCMÈZ¢TVõþÆ3ôZrÞ\x0015Íª\x000b¯v®\x0015ÏúÆ3 óåë±âù§NÎ\x0005@ðg½\x0012?ôZ\x0013¼Ä\x000btV\x0015i©[\x000ew\x0001Ïl¹]|Ò\x0005</p><p>,]rKÞsº¨jÝó[iJßâ s¬\x0008?¬Ëäxèamý!°ç\x001cK®\x001cã.uëX¹ãòû\x0003èþáu\x001fO\x001d¡Ç5º¯Tð\x000bx¾/c~\x00139é?ûþx§û0ñF\x0003\x0012Ï\( äx£\x0003´\x0003~\x001dô\x000bÀ\x0017\x0010²óÕõ°®ùêÍE.I£[t	\x0018~\x001fòáv\x001d	wN=?:ö´{¹\x001enê\iõò7ZÕ,\x001b\x0012Þðl`Þ8\x0006i[ÊwÑ£Sì\x0018\x001eÒw05ò ©+vHZâö<Â'\x000cÍñÊóJê\x000fÍ±îú\x0012F_\x001ct¯\x0013ñ=Ø\x001d½rl\x0001ò\x0011ÑÛ½¯c\x001fO£LtHyhôVÙS¯|öêçÊn?<¸ýÝ.þ>3+ÕçvéÖY/>Ô7°I'_ÇbÓ^á9Ü/Ý¶Ñ>^ÄP_ÈÈyÕ©ÂÚ^Çí\x0015\x0005<.\x0010Ù/+HJÙ</p><p></p><p>Ø|}­ÿÃwÀÙ/6X\x0001hëó¢\x001fs}}¨> 3Ô\x001d³~(½³ë.·ä\x001f¦}JÌÇê8çòX©Ë\x0002Ë\x0002Ë\x0002Ë\x0002Ë\x0002Ë\x0002Ë\x0002Ë\x0002Ë\x0002Ë\x0002ß\x0005¶	ö{Ôé\x0008ðÌ(&ã\x001cjª±Í®Ê1Ù¥&Êt?\x001c¼;N©ç	<Ï6Ç2~Ï\x0016`®M÷Úñò{Öó3uÛðç\x0019}¦
\x0016ûw`\x0001&Æºï*åZÙiÂ;¾/\x00029¯ø+@Qg¦õ0\x0005öÊF\x0000Èº1°9Î6ÛÎÏ·V<k¢S³*\x001f¢\x000e§\x0008\x0006tÞgåóçmÅ³Àç\x0017/
:³êYÀó¹V:×7¥\x0015Ï\x0002\x0007è|%Y\x0006
>\x001f¬x^èzþCçýçúÎs\x0007Åw£Tt1ý\x001cW<\x000b?ÿY¸ÑÏëÂÿÐ\x0017}\x001e\x0016Õ¥é'\x0004\x000e\âè3]\x001e\x0008\x000f)ù|³Ä\x000c¹\x000e×ÔÈqü°Nçs(û°L$Ý¦·ÛtçëSÐY¾\x001e<èË=\x0005\x000bôA\x000eÈ\x0012=¬÷\x0017Â'ü9\x0014\x001bÀ\x000fàÌ6Ðx@´c\x000e]ð\x0001ô \x0001\x001dCûêÒ\x000e\x0016¯øÏ\x0004\x0006¸»Ö*ZÂ¸»Ú\x00100ü\x0000\x00134xÙÓ;ÀÉ¥\x0002 m¯GÚ`\x0010Ï+IÓ¤õ¶¢\x001fñc®ëýËï9ùßþöä·ÿð»\x0002 -Ã\x0000gê\x000cM=wÑðYmÞõÀÞÙJp\x0007r±G¶¥N¸Û,6­hC|ÚØÛEÓ
z¢¶JW}ñ±-tß.³\x001f£¬V\x000fíy×lõÌ\x0005ã\x001bØ%wÔw¡­ÙÓæPò	S7:A±\x0019.mèíM¡\x0000¯|ûüü¢|ÊúÙ¬$mö¡\x001c 2À®mÌ</p><p>æxoþîJyZÕl>µÕÇr\x0017Ò6°\x00158uL\x0010ØÇ÷ì`u³û
<pÀé</p><p>\x0013/ï>Jsêê¶t×÷¤¡¤Å.>F\x001c¿¤¹ÿGVlV­ný¢\x001e)·ø´m5L?)ø¤\x001cãçÎäÙÂ\x001fºÏ_ñeeeeeeeeee'mG\x00065Ñ.\x0016Û\x0002I8B\x000fy4¤\x001añWÂÐ\x001ewç\x0003¦^`\x0005\x001eØ\x0002ô]ùg7÷Ë9%ÿ(\x0018Ä\x0003\x001f¢%þ[`cgå{sríï4á\x001dßg\x0003Ï*¨üZS\x0008\x0003\x001bO0\x0017(</p><p>ÅNÐy\x0000Ð°*ïJE½â¹\x0003ÏDÔ$ªf\x001cU\\x0013ª\x0000ÐuW6iHMÈ</p><p>Ð\x0005<V6 s­x\x0006\x001eßw>øÆ3+\x0005<	x>W8Àó;ÀaÉ`µ³W<{«í\x001bÝ}Ë«\x0005\x000c<KG,\x00010ý~\x0003/*%ãxÊØÏn¥i\x001d9õ³A\x001fø`u\x0010c?9¾¯Ið¸ýxÏ\x000bÏF>tÏ¿ïË&þi|ýá7%\x001fÒ\x000fåéË=	\x000b¤\x001fAÓ/Q<ah÷\x001dX#=ñcáÈ!\x000f\x0010-\x0000A9CÔÛ½+U\x0001ú\x0002BB\x0003Dö´^0sÀ;êê:\x0006L:´§õð¾MÄñq£Sô¢-{}÷ô´\x00179#÷\x0018íºÿòËúïï~û\x0000¿wL^úò·z'`ÛíC\x0018\x001d Ñ#:@£G\x0005Æ\x000fü´	O¸ÀÚ±\x0012¼¾\x001d½ûfw@^Ú\x0010ÛF\x001ei¸cu\x0007 þ\x0017\x0015úFo(¾Ëè¶éúå\x0018&-úD7Àç*«c\x000fH\x001bÛ\x00010ç;Í\x0001¡9¶Ñ¶ +¾×º èz~&û\x0001<ÞvZ¡Ìß°Yhúnç;³Ý; 4ß\x001a\x0017@]+ù.¶\x001e³.¤«ô½¼ô1\x000bøk\x001bÊ~²/mu;úyÇ±±çÉá}~ä	<_	x~7gÚ\x001a\x001f;\x00117øí:%¹xº\x001dh3.ÛÈÛ¦ö\èmGÚ±ôÛ3%ü¡3g\x0005\x0005\x0005\x0005\x0005\x0005\x0005\x0005\x0005\x0005\x0005j\x001eñÛqtÅ3u0¦ñ¸&ãÔ¼'=ü¡û±Î]ñ	:¯±Ì´å</p><p>=®\x0005Fs¿Â½\x0016ðü¸ÝiÕvÄ\x0002¹§v\û;MxÇ\x0017¼¶Å³Ý\x001757wt«m1 ªÿ\x0012\x000bà\x001cêjR©<\x0002<;7
 ¤Â°êçSçña¾¦$\x0002L\x000b4>Ý\x0003Ïß­¶\x000f¾ñÜV<\x0007x~GÙ\x0005<÷ò	aã\x0002?ÁP\x001feÉCa(\x0005öác\x000f=­?V!²÷üûøÇd$¿ë´Ç§\x000bx~|]½¿õ>D8>`\x001añÑ²¡Ñ2õAã\x000fª\x0000c\x001f¦¥\dR\x000fÛ\x000e³*3Û\x0010\x0007\x0018DgÂ\x0001I\x0003LFWø\x0017×ëÚ×I< ï±¼è\x0015LÂ±Uhì\x0019]£SÒC¯õF\x0017À)åR_×¡ëÒÃðÄG\x0007ôH¸\x0002»ä\x001c} \x001d\x0008Mzô\x0017Ýpis§Ñ9ùPÀI¯Ô5\x0000¼^?iÈO}¡¤\x0013\x000e\x001fG\x001c×eíõ]b¯c2]÷\x0012ª®OÂ¡<Sñ\¤\x00046^ò­w¾mío:cËîm¶«\x001f«]n\x001bõ),\x000få¾\x000fp­Ôj_ÙP/\x0017\x0018H·¾Ø¶Àæ\x0001î»
*ÂÓ[\x001d~ÛtÊ"oÚ,+¢Ý~Ê0\x0010þµÍ¶W]Sâ;´sÎ÷ùò\x0000eà±½J¬ÞkÇ8vìrn×C#æ¹z;ÿXJøCñ¬´eeeeeeeeee'kmý\x001e[ð\x0001ày\x000c­klÓkdL³w3-ã®=ã\x000e\x001dñî\x000fsWlYàq,à9ç¹èh\x0001ÏÓV-\x001f¶À8ÇÆ|ß!oî\x000b&Ü9ö5À³¦ðÆÜ Â5qWQÂq	KÙ\x001dðÌjár-]\x0012J\x001eôç*&Ö¡&$\x0005\x001c\x0002\x001cK\x001c«¡µÕö\x000exæ\x001bÏ}«ícÀóU­Pöªgãv¦kÅs\x000esQç\x0002\x000fLò<\x0008"®»øL'mÿpø]å)\x0017}82÷ô¬¤ö2]~O¿ÿð\x0002ïß¦'1}\x0007\x001ao ÌÀWÂ{°q\x0002f|]FV²¢\x0014`>\x0019 xÀ¿Náé|Xâ®¾\x001cÝá©ïÝÖ
ÚúDß¬\x0018ÍÝÄ\x000f7Ïó¾R\x0013ý²ú7+é\x001c}³\x000fwÙè\x001aíuN¡\x00052\x000fÀü\÷WVè^hekê}\x0012öp·gì\x001dý w9õ^Çcº¦OÐ&ÂÑ':£O×|\x001c´Rm\x0011}qaà9ýfo'äcèÑõËcMÚ³?~©\x001b]r,	G\x0007ôø\x0014\x001fþÔÓ)úvG\x0014|ø½\x0002Ð®/á«±6+{»ªÿ\x000ep\x0019]/sÛ</p><p>»áqÝ¬lTùµÚYÏP¥¦uÍ\x000b\x001a7²m\x0000m·c_¯\x0001c÷!µR+­ñZÿ<@qÿ¼n c¯{tô·§½±Yé½ä9Î)¿Ñíë°?o§(%ÏÇ¡\x001fâ]yË\x0002Ë\x0002Ë\x0002Ë\x0002Ë\x0002Ë\x0002Ë\x0002Ë\x0002Ë\x0002Ë\x0002OÎ\x0002\x0008<3´ÅÇ1K84é\x001aù(8ùfúa1Ôt»9+´,ðx\x0016\x0018}w­x~<¯þY ÷ÐÞüÜ\x0013:MxÇ÷Aàùßþ«\x001b¦D/TVSôc½&êTÈâ\x0008sË1\x0010k@¶W0L]QM&\x0012å\x0006·¥W¢¦×*Ê7ùÖóµü\x0019\x001e\x001dj¥\x000b³¨\x00144?\x001aP~\x00058×ê\x001eV-K\x0014Àó;Ñ÷JgmV=gÅ³g¾ïÌwÙjûçÚjûØg¶ÛfìëPê®ZjåhyMiÂ6><¬7Ò¸ÚsQ@8òã¸ÉØu<Eãèñ¶Ñ \x000fÜ.jÙ\x0016Õ°j\x001e\x000eMH?T"\x000f\x001bí2J\Iu¡!3\x0012R¦ÔÏäíyáFJëòvúr~G×È</p><p>íòî?L?¤\x000f>§~xÿVú®$¶~Dÿ/ð§À(V7jëj\x000b8ká\x0000iÉ§L÷Õ\x0007W¯^üðã'?üðÃöÍ\º·\x0000¨\x0002U¹l\x001dmûÏ\x000bht\x00062¥Þ©;ý?\x001e0- \x001e4Û}\x0017øüN\x001fíQ:rp©¯¾Ë+ \x0014²æÙzïéæ[ºI¹º\x001fÎS¹Ôfî±\x000fuR7:u½®¤Ó;Òø®¯¶SÆÆñ/_È?¼>ùñÇ\x001fN^¾|Uur®­¶±\x0019:\x0015¸8|lJ~tÕX~¶ã#U\x0001tã»Ü\x0001é£\x0003úGwÒ\x0000,}­tÙs­°E\x000f_@Þ:¶-­\x001f[ô1ðÌVÛ*§í {m6ZöáÇ>fÅ+=p[\x001bU·Áå	2_°Ýõø3v|ñòE\x001dWú\x0012î(U\x0016ÇnÚ¨XëÙCU¤ê$EÂ¢ô=V¨_]q\x000cC
W?¼}Ù:[«Õ\x000eÚI­ö\x0000ù\x0006ã}lÕ\x001em£}I¿\x0014µÝrÌÓéülíË}\x001c88.ÒN:öó¨¶õfËnßÐ\x0006 ÕjO<&Å¦ÈÙ¼déyãìL^4[\x0017}­8ç<;\x000e #jÉ\x001e[ytÙõÉ:\x000c6uéçógÍè`ê#ß\x0008\x000fMúÇhøC?Æ¿ò\x0005\x0005\x0005\x0005\x0005\x0005\x0005\x0005\x0005\x0005\x0005ô¬Ï°ê>]Í¹\x001e</p><p>ôxq\x0016ã\x0015çÍ±%qÏ\x0005¤Q\x000cp8öÔ²J\x0005ÝïyW|Yà±,¹ßOéÃ¥Ó×Ö3Î­µÕö×\x001arÿj\x000bä¼</p><p>í\x0002Çf»\x0017´\x001d_ái¹g(¯âæ?ýÿÝ{s¡»\x0016_\x0005\x0004|®û\x001bw(ù*¢ ©&\x0011\x0015pª\x000bó;+­iSGÑwpV(79\x0004\x0004`l\x001c¦n&Sj3a9\x000b0¡íIí\x001b\x0000æ\x0002tÏN:ÝV<\x000bT\x0000p¶×d¯@æK}×\x0019zñ£@g\x0001Ïg\x0003x¾Öd$@õµÊ\x0018p\x0006,ö7³ê\x0019\x0000¹»²\x0003ZXbxMúÓÏ\x0007Ä\x0004`WKÓ%=åp\x001aô¹8\x001fYwÐÇ8^®_[Q¿õ\x001f]3-Ì!7~,aÆ·,\x0005\2åÍ9ËNÎC\x0019¤\x000f7FB$ZGxx mÌ	K`i¹	\x000eÏCP*íþ!êøG 3#cM\x0007¹rso±\x001eðU'¸ÍRàÐ\x0000t½\x0004l\x0002,\x000b8ZT\x0019ßL~\x001f</p><p>Ð(ÙáÝ\x000bM_\x001bgÆ87òýY¸\x0000\x0013\x0012°\x0006¨ÕÓ¸§\x0008\x0002ô*7\x001aYúD¿è\x0013^è/o<\x001bü\x001aúJçZÑ)\x001eô¯îp]\x0003CUÅËU\x0005´©nV\x0017\x0017x\x0017P\x0015¹]Oé\x001d×e}>ì\x0019½öúG×|é\x0015=KGôãO:\x0003z¿zù²@g¾ç\x001b\x001b¡3º\x0017-\x0015ïyÖÑ¶,Ý8~ñU\x001fºÚ\x001eI\x000fÐûî­@QR9ÿ0ºõ
\x0014¡|^"\x0007ÞÒp\x0004 ®\x0012uß\x0016­¶nvãXÊ\x001e\x0002d
nf+jú(\x0005á¶³
h·ë­Õáðíx¡\x0013/\x000b`»¼@\x0010="g\x0013\x0018ÙØ*Ê^£Æ+O¹õÏOx«@õC¿@ðV2ßd¶Þ¬hÎ9å4µ²£Ýe*DÈ\x001e^Å<ì9¶Ë.À¹Ú¶ú|¡\x0008ÊP>À®Ï3÷:N±ñhCÍõhtË¹bZç©Hõ§\x001fèTÏYÔ£«jCé/\x0019\x0007T6A\x0019ÊãõSÇ'çY%g\x001e\x0015Ýl~XÆ§\x001c<C\x0016ò\x000eË\x001f¦},ö%e>&så/\x000b,\x000b,\x000b,\x000b,\x000b,\x000b,\x000b,\x000b,\x000b,\x000b|\x001f\x0016Ðó>ãûrÛðáPh%krk¨Â¸(u\x001fILNh\x0018Ð­Þ\x0004 	\x001fá_IË\x0002b\x0001ú®|-<z</p><p>\x001f¡\x0012W{ î\x0011j]U,\x000bÜ¶À8¿¶{Å#÷=í|Gús\x0007ÿÿõ¿\x0013ð\x000cè,ð\x00199¨Ôì½nZ\x00065éGVÉÝU6Efç¡lÅÑáÈ
«V\x0013S&AkUsÕG!ß8kB:¹¹jY3E\x0001ke²´*àYEXùü^<§\x0000ÏÚbõT+.|}r©U[\x0017¢\x0000Ïgµâù§S­«ÕÑDÎ{É-Zr-\x0015Ø\x0005@×$¤õ¯¶¤\x001dÕ&§¸¶\x000b¿´ûL\x00069{/\x001fÃíú\x001aVÍL»z{vú×±òqÜåÜot_E³?,ÞQÝ(g²\x0013²n×}ºD\x001f-Gôí[G{¯o+ûy²[ÁÏ\x000eJ	N´åîÅ\x0002½Ü²ê¸\x001e×un¹.]V\x0003P¼f»ßú^«À½\x0002Æ\x000c@e+\x0014à\x000fp|[6\x0012t-\x0005Ì/K W·fp9@àV¿\x0002¼¬d@l\x0002g.¯x@©\x0002·\x0004oU;ÕßÕ¨¬n-`¹VzhéZº£ëûZ¥ûöW¢wÉºw\x0018ÄKÝY)</p><p>X®3N¸Àµ*3Àh#Ç \x0018ç¬õ3X¶]\x0001xº\x001a\x0000÷å\x0002ç6\ÙÚÅ]Ø²¹§N\x0010×¶ÝêTWñ</p><p>4\x0015xÊl\x0015³N£|x+};ê\x0000îèf_z`+éBØ\x0000¨}­v\x001dàggV`\x0003ú=ê8³B9ÇyÒZ\x0001.¼³¿TCI÷\x0017Õ²\x0011º´p\x001d×z¹aè¡ün\x001fën\x0019È¬vJèÖgÒÿ~-ëå\x0005õR\x0006Ûå{ÈCj\x0011ó×éèÁ¿mg`\x0018Ýe»v¬\x0001ÁcWëjàóêÝÛ_NÞ¾ûE«×±Èc¿´?)\x000eE¥»û\x0002ýÕa3â\x0019Ç!Ç{{É@²Ý¬&·ÅhSµMíØtN;_
/¬ðV\x0017\x0002ü¯ºü\x0004Yå·²ÃVÈà87NZEze£tÕ9\x0008ýLÊÇÑoÑ»sn±ÞJø²·­eeeeeeeeeel\x0016Ð¢*æ(F¡\x0019\x0019Áð\x0019vò\x0013</p><p>ý\x000c!uYà^,>\x000cMø^\x0004\x0007B8¯rn~\x0007j-\x0015þY`[¯ìÎ±\x0003<óCýUy·ð´Ñ§~úÿoÿæF»)\x0016è\x000cø¬YbMvÊ³òH¬Û- UÔS\x001c\x0003WhÜÇÂÈ³Nµ>¥®	LßUºJ°E·Ý¤ç¿`²Yúð^\x0011%à·ÊéG§À=Õ$´fµ2Ù[s³Îø</p><p>/Û°ÕöòO\x000bt~qr&zñÃ'¯~,zþúµW<\x0003@ÿðJú¨ÑÃ¿×d+q\x0003Ú^ùlà9i¦´%`4m­°¨\x000fSk\x0012.µ#ç&/hÄrË\x0002Ë\x0002Ë\x0002ß£\x0005tÙ:\x0006³\x0014\x001cÃM.áP§Îß-}\\x0002É{wõF ­=@cV²</p><p>2[P\x001eP|À ¯ZDÝ\x0003\x0000A/´\x0012·h­$ÕR]ç\x000b\x001c%\x000fR´¶g,¶FA´À"³)Yÿºï\x001fðÔ2ÐÍÛS{5©ÀJÀQVmÖÊØë_Þ¼9ùå÷¿?ùå_ªM¬V\x0006¸å\x001bÓñÒóÅåÉ\x000bô/@uèLÝ9</p><p>ØÒ@©¨ôÀ\x0007Ì5h</p><p>kÙ6\x0014 [ñ±6¶\x0005¼'
U÷ ÄÓN¿Û<uä\x001bÎl¥\@sÙ\x000fW .£Ê@«¬Â\x0014ü?tt\x001f1ì\x00066\x001d¥ïÐ\x0019{\x000eýr¬\x0003<{Këë:ÆèÃqåø¾ä\x0018c?l'\x001b\x0016U^m	ò¸Í^ê;¶ë¶.\x0006¾k{q½(ðVÛsL\x000f\x001cm¢z\x0016¨\x0015Ë²\x0007zP\x000f+ëØb+ì­j«q×\x001d9Ñc¬Þ÷l³Øzì·²<Iè?v)À\x0017\x00088Ãû\x0005\x000eÅµ­vø\x0000Ø¯®ß¼yû\x000fêÿ ~ÿ»jëFèjZ}¯Òô¼T/>äpÛó"DéupÜRêGwâ</p><p>§\x0001	¹[ê¸p¶4\x0002ôõc®KÜòL8,W1~¦"=¸p 1UÂ¡¬\x001dóè¾ü\x0011´,°,°,°,°,°,°,°,°,°,°,ðÍ-ð¹c½Âkì³·È+\x000b|m_þVz¬Þu}ÌB+ÿ¡- së\x0018èjëÔK?ÝÓ0)}\x0003Ã3óNÿBÀ³>Ç·mµ­YoÍ|</p><p>5Å+Ì´êöãÛ\x0004`¡cz{L%6\x0000è¢æ3OÂªS³ªçR«\x0000ÐL¤Þ(\\x0000DÐ>À]Í\x000eàY+¯4á{-|\x001f\x001aÊç+é\x0003½Ñ$ê©&¦\x0001\x0001 \x000bt~õgy­zÎgçÎP@qÎ\x0002\x0005BgËí
|\x0015?gÎ\x0001Çi+Îí>§]2ßå\x0002Ë*ëgY`Yàû´@\x001fQ-`\x001alÇÂ¤qí¾+ô«ë·\x0002ËÆç\x0002DYý8Á³\x0002K¹þKV<å:p\x0007\x0008\x0008(ê­\x0005\x0006\x000e\x0010×é\x0006	\x0001ÕUà¶@Î\x0002^\x0001Ç¸ÈVdü¤¾ºÿ¶\x0004è3õ·\x0001É£g@¿	¾+½».Ño\x0003Mùf®t.0S÷4tí )êt\x001dz\x0018\x001dS·é\ù\x001a½¬+`³í\x0018\x001aº¨ú­ç\x0000\x0001Ë·4ÀIÝGÍ¢\x001fº¡\x0003.[\x001cw»Q\x0017~¯câèØó)\x001bý:E¾u³\x001e¶mvYß\x001aÇ9:B#\x000fY©ºý2Ã´]·\x0015|ÝuyØÀÞ6¢nôBä¥oÆ.Ý\x001eI'rS\x0017q\x\x0012îå{;z{X\x0011^6UÛ\x0000nÉ£\x001cç×»«ß\x0016è|uýË8o\x000c|{+÷´GtÎ´£Ú0\x0000tÊÄç\x0008à¯v©Ú~Hå|ª_[Þ</p><p>.\x000b,\x000b,\x000b,\x000b,\x000b,\x000b,\x000b,\x000b,\x000b,\x000b,\x000b,\x000b,\x000b,\x000b,\x000b,\x000b,\x000b,\x000b|ÿ\x0016`Oþ(ø¬ù¾mb0s¡i\x0019qø\x0006MòF5ø\x001fþÿ¡çsUÂw\x000b.\x0006pÖd&°*uW\x001ay[Hð\x0019¦DËdüÍ[\x001eYÅgàù&¤_P\x001f\x0013¨TÍ+U¡w}=É[Mú²ê¹V<«¼pÝZùÌjç\x0002ágõçS­:ÓVÛ\x0017Î¯^	þáä\À3ßx¾Ð7\x000fgÀäÏ\x0006'ð\x001cÀyPôÖDkÐ\x0015æ\x0018fvK§KÍi_^ß\x0008P?0´\nY`Y`YàÛ[ \x0000X(\x001aõp4\x000c \x0016\x001a°+×jè\x0004\x0018Û5\÷\x0010ÊÏ\x0015òF+y]H)%:ò$Üë'\x000cHæí~
²Ê4Àdh\x0000´ÐÔ\x0019v\x0013>Ô}.çötÑ·\x001a1~Ð\x0015\x000f\x001eµjv¬Mzt\x000c?´ëz¢[â¡þþ°uªª±qÙv]/ÂÑË4\x0000¤W¹Æ\x0005@¢»<«y{\x0019Â]\x001fì\x0015%l:=\x0000ï¾]èBZ§c\x001bo;n½\¿í\x0019]à#\x001c\x001fùÈ@¿èÄË\x0006Ñ+wô¬¬¤§lt\ÕP}cþâs\x000c£OÊC©'\x0014Ù©0¼½ïe¢g§ý÷5\x000eåè%·z)àzÃ[o#_Ûfs<9®\x0003d&\x000eà¬g\x001f¶ÏÞ¶}Õ|9~t¬Æã\x000b}lï°ÓrË\x0002Ë\x0002Ë\x0002Ë\x0002Ë\x0002Ë\x0002Ë\x0002Ë\x0002Ë\x0002Ë\x0002Ë\x0002Ë\x0002Ë\x0002Ë\x0002Ë\x0002Ë\x0002Ë\x0002Ë\x0002OÌ\x0002\x001bàÌß~Þo?çG¼§)\EÞó°ã§ÿþßý÷\x0002µ\x001d©¸YÝ|.Ê</p><p>hÂµÍv±</p><p>^°\x0003\x0011\x0007ÂÅ¤\ÌÞzÒáÆä:,Å\x0013zzr)À\x0019Ðù\x0000¬xÎö¡\x0001s\x000b4×d©f\x001bðìÕÎYñ\x000cq¥\x001ajÅ³V$é;ÏÏ\x0001¡õg¾ñüÓÏ'ç¯ô\x001dhM¸jV¸èü¾3\x0000ó\x0004kÅ³tinW;c_åÑ¦2Ìl#À3Ûl\x0003>/àã½Ü²À²À÷f\x0001@1Ü]\x0014`+.à\x0018i\x0001ø\x0002îyu±ÁH¯0í  ÁHa\x0002\x0018åu)\x001fÕnõ\x0016§ë(\x0019\x0001ó õ½YÑ\x000eôõ°y:Py\x0008LÒ®èÛuEÇx¶w¶ÎÖ?më Þ1û÷ªf¶ÔöJØ¤Æ¦½\x0000¤%l:Ê:\x0006\x00026Ù\x0019>ê«ú°!NéÝäÅcC§Oû\x000cå÷täàb\x0017è´V°ëû×e?Òkù\x0004»\x001d½R\x0007í¾_¾ÔÚ/_=©²¡»ïö±^³OfEsxÈ§lÙNíØ_¨\x0017z1c×ëÔ½°Slu\x0017èLèF¹Ô´.3i\x0015\x000eç\x0000\x0000\x0006cIDATáv»:>í\x0017ð>ü)\x001fJ}q§§z\x00129¿ÞúøÈÂÉê\x000fùÆy^ÞçLúH?gJRÉ«®Ý\x00196ËÈHdÑeeeeeeeeeeeeeeeeee'a\x0001fúä\x000fW\x001aß¡yæ Ek°Å3\x001f½QDïôÿüÿÍAg\x0001Ï¬<V:ßz\x000eø\x0018 Õ\x0012W]¿uªÔkÎpoÀ³d\x0012C\x0012ú9­¶_j\x0005Ü\x000bÁ·çª»¶d;SV
Q«ØWß\x0007ßxV^­\x0013Aç±Õ<L>½Ðç\x0001<_¼\x0014èÌªg­x¾øùçK­x>g«mt\x0018à³e\x0001Îª\x0007 y\x00035uÛ·Øv­A:î@Ï¡sg¾ï¼ç2ÓúY\x0016X\x0016øÎ,\x0000(\x0016×ÃI\x0006ä\x0006\x0000ë`Y@HÒðÄ\x0013\x000e\x001fåÎ/\x0000\x0018Y­<\x0001eêôË	.ç»¹\x0001ü\x0000Ê\x0012\x000e\x001704qôìú\î\x0019Þ]¯wú®ïôÎ§\x0001'\x0010ØeN°Î -ñÔ\x0001ùJ/2½âå&­í. `·a\x000fc\x0017â±«©AÖ¤\x000cñÔ\x001ftøèWºè¾s\x0008,\x001aTìvë:£;>2ºÎ	rÔé\x0017Â|±\x001f6\x000bh-À9Ç¼ëÝe\x0010F©Ó´% =öÃ\x0007\x000cFNÕ;ú\x0015ñÔ1i×á6Þ)\x001bZ6TÃ ÈÿAÞx©ç\x0002ÀnÒßí\x0011}i?></p>
  
### Reference
* http://blogs.wsj.com/cio/2013/10/08/adobe-source-code-leak-is-bad-news-for-u-s-government/

  
#### CWE Id : 540
  
#### WASC Id : 13
  
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
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr](https://france-chaleur-urbaine.beta.gouv.fr)
  
  
  * Method: `GET`
  
  
  * Parameter: `X-Frame-Options`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/ressources](https://france-chaleur-urbaine.beta.gouv.fr/ressources)
  
  
  * Method: `GET`
  
  
  * Parameter: `X-Frame-Options`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/](https://france-chaleur-urbaine.beta.gouv.fr/)
  
  
  * Method: `GET`
  
  
  * Parameter: `X-Frame-Options`
  
  
  
  
Instances: 6
  
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
  
  
  
  
Instances: 6
  
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
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/_next/static/chunks/framework-c93ed74a065331c4bd75.js](https://france-chaleur-urbaine.beta.gouv.fr/_next/static/chunks/framework-c93ed74a065331c4bd75.js)
  
  
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
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/_next/static/chunks/pages/_error-ef6fb2a85018fcbd5e37.js](https://france-chaleur-urbaine.beta.gouv.fr/_next/static/chunks/pages/_error-ef6fb2a85018fcbd5e37.js)
  
  
  * Method: `GET`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/robots.txt](https://france-chaleur-urbaine.beta.gouv.fr/robots.txt)
  
  
  * Method: `GET`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/_next/static/chunks/pages/_app-b1559682e86a1ccb6406.js](https://france-chaleur-urbaine.beta.gouv.fr/_next/static/chunks/pages/_app-b1559682e86a1ccb6406.js)
  
  
  * Method: `GET`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/sitemap.xml](https://france-chaleur-urbaine.beta.gouv.fr/sitemap.xml)
  
  
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
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/partenaires](https://france-chaleur-urbaine.beta.gouv.fr/partenaires)
  
  
  * Method: `GET`
  
  
  * Evidence: `X-Powered-By: Next.js`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr](https://france-chaleur-urbaine.beta.gouv.fr)
  
  
  * Method: `GET`
  
  
  * Evidence: `X-Powered-By: Next.js`
  
  
  
  
Instances: 8
  
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
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/_next/static/chunks/pages/_error-ef6fb2a85018fcbd5e37.js](https://france-chaleur-urbaine.beta.gouv.fr/_next/static/chunks/pages/_error-ef6fb2a85018fcbd5e37.js)
  
  
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
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/_next/static/chunks/pages/_app-b1559682e86a1ccb6406.js](https://france-chaleur-urbaine.beta.gouv.fr/_next/static/chunks/pages/_app-b1559682e86a1ccb6406.js)
  
  
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
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/](https://france-chaleur-urbaine.beta.gouv.fr/)
  
  
  * Method: `GET`
  
  
  * Evidence: `353b-RNVtJ+4D5UX5VqrGGhXfknEj1Gs`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/mentions-legales](https://france-chaleur-urbaine.beta.gouv.fr/mentions-legales)
  
  
  * Method: `GET`
  
  
  * Evidence: `335a-08mVynkYp5ISdmuSY4WneCgTQ3A`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/robots.txt](https://france-chaleur-urbaine.beta.gouv.fr/robots.txt)
  
  
  * Method: `GET`
  
  
  * Evidence: `da7-AV3eVYFIshHzRzVy3oHJnrCgllI`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/sitemap.xml](https://france-chaleur-urbaine.beta.gouv.fr/sitemap.xml)
  
  
  * Method: `GET`
  
  
  * Evidence: `da7-AV3eVYFIshHzRzVy3oHJnrCgllI`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/Enqu%C3%AAte-classement-reseaux.png](https://france-chaleur-urbaine.beta.gouv.fr/Enqu%C3%AAte-classement-reseaux.png)
  
  
  * Method: `GET`
  
  
  * Evidence: `qkX5P5P5P5P5P5P5P5P5P5P5P5P5P5P5P5P5P5P5`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/_next/static/css/00104bcde2c4b2198fa2.css](https://france-chaleur-urbaine.beta.gouv.fr/_next/static/css/00104bcde2c4b2198fa2.css)
  
  
  * Method: `GET`
  
  
  * Evidence: `d09GRgABAAAAABnQAAsAAAAANhAAAQAAAAAAAAAAAAAAAAAAAAAAAAAAAABHU1VCAAABCAAAAFsAAACEI00oO09TLzIAAAFkAAAAQgAAAFZZDkN/Y21hcAAAAagAAAIWAAAGch5gS9hnbHlmAAADwAAAEToAACPAlpW6CWhlYWQAABT8AAAAMQAAADYdwQw/aGhlYQAAFTAAAAAeAAAAJAiYBEJobXR4AAAVUAAAABYAAAFkdpwAAGxvY2EAABVoAAAAsAAAALSFg48KbWF4cAAAFhgAAAAdAAAAIAFtAGBuYW1lAAAWOAAAATEAAAIuRB1J2XBvc3QAABdsAAACYwAABX8p96PdeJxjYGRgYOBiMGCwY2BycfMJYeDLSSzJY5BiYGGAAJA8MpsxJzM9kYEDxgPKsYBpDiA2YmACmiUBFjUD4iCGYIYQMM8FKB7EEMYQDiQj4DQjUH0gQygAoDUKywB4nGNgZDFjnMDAysDA9JPZg4GBYQWEZnJgsGI0BdIMrMwMWEFAmmsKgwOD7wN/5hf/LRhymF8wnAAKM4LkANBODB8AAHiczdRJU1NhFITh90JARFDEEcVZwZlBEQQUxXlkEmRPUcWKBVX83/4n2Cf0KuXOjZd6UuQLCTm3TjfQA3TbY2tB1zKNf6NZ9GnTPu+mv33eaob8/DxDPmnxg3V22GWPfQ441MrRkV/tPKV92nk1/pTOH1hjky2//zcbbPPLf9XV/k899HKCPk76e5xigEFOc8bf4izDnPM7L3CRS1xmhCtcZZRrXOcGN7nFbe5wl3uMMc59HvCQR57nCU+ZYJIppnnGc2Z4wSxzvGSeBRZ5xWuWeMNblnnHez7wkU985gtf+cZ3z/iTFVY9Ru9fZvuXa60eNjtP6574ptS1Ydv43vw/10A9tCbzzF/O9+dYTbMeNdRObNlu1Gt7USPuRw16EPWZh+HJxbHaToU3BUVts6I2WlGbrvBGofBuofCWofC+oagEKLyDKGp6hfcShTcUhXcVhbcWhfcXhTcZhXcaReVC4T1H4Y1H4d1H4RSgcB5QOBkonBEUTgsK5waFE4TCWULhVKFwvlA4aSicORROHwrnEIUTicLZROGUonBeUTi5KJxhFNVaCucahROOwllH4dSjcP5RuAlQuBNQuB1QuCdQuDFQuDtQuEVQuE9QuFlQuGNQuG1QuHdQuIFQuItQuJVQuJ9QuKlQuLNQuL1QuMdQuNFQuNtQuOVQuO9QuPlQuANRuA1RVOYVbkgU7koUrP4Bmz3bVwAAeJy1WQ1wU9eVfvc9+cm/EkJ6ehhbQj9Iz47/9Yv/ZDPYTyYYDIaAlxgHmBcHQpKFBkgJJGynNmUJZp2m1e5saNLFm03I7NCw7ZDuhmkZZ2arTpp0M+MwWya7w3am2exMNttJ3eCq1suec9+TLBk5MbOzGD1dXd17/u453znniuEY5ouLhn5unLExLqaBYUhAtIv2FUbeyLskv+RfEY1EIxxMBWDQSDx8NBAjIRiYiM1J2KGzR49s6OnZcOSo+tvMaKp1y7Zr2wbWdb309y99UttbU9M7iA9uLH8ZWYGj9L4dTc0tTdvburqm9IXwYIry5IowG5h+hinyZCVyZaX0wYCKZiJGKcbaRfhWaiSS3wgTPCzzeRpJKEYCTmIzESkQCfk9vM2eI7kmCBXu9Mbh3X8y3Bccf/6bLb2xV9+83N1eXu5Z+1f7947s/45rjdncSboiw5HI8GP4iNS2tw+2tyuLiFAN32q3We32WHAd2xHu27CR6+0eVPYNj5yx2ysrz+0d3qds/alOBR4KkhlsZxhm4TzKQO8wnEc4KAQFr+ANe8PWQvpLeDCREH7jwc82/Ib1K8mkkkwV0PHs43t2h6PR8O49tzIDMo2Lk0r6ViFNlLy1dABiMSjsNfZTkJMhlqDFLbgtXos7DJxJvTqjqDNkOjOoV6he7xlGuUOMhRGYSoYpIXY4Dq8bDydK4HjsnBAM44sdIx/yJrFivq9iVYWRfGgUq1YNKYrCDc7/rKzabjLZq8u41jKTKX1IUchIKoWiGHLo25hVTHUhDsRNOLClBV6FmKg7uHL16YBSiNf8B+xU+ncKmU5ldP83zsUUM4yPiCUkChZgz5HyuHpSPRkn5cpPcXyKjMvq79m9uFzbk2A3o2eTKO5hh+Z61bfVaZnsvBNXp0ksnl33MScgbQJGJcYSIpKz7N709yl9oEmmFXU2TsbJeJxh6foT7HWwcAmeBJyBaBSNhEwqLB+fmwPK7PX0GHsqfmdOJjFcru25yr4PsuDpicjCLYFIEvtmSlZvkG5ZndHeU2QyJZNuGMFn9YacysoosO9RXehu1qmrQCbvyKSTxOTFugD1EiIRd5irVWdlMo52qki/DE6yYLWsbGML+oBngToi4VxKOoX6kFhhff6BfUfXR0JOPvokf0DpQW7Wrw/I5O+pJptS+ntGTpeuD93HvoCM1GnQZ05Wp2GQ1Qdlo/qgMuDznEsdjJMr6jh4PrtS3QZjCKSFM9f9BE+GgI2N7Lns6bH70i+z+9TfxdEcctZHhqgcRrp4SDcneUcXSNMXfH0zdw0sVMUwVrfFxoOb+8MkGLA7QKpQpB1hwx0OKtzHDmH+lOBgP00KjvlVDiEJ4QlurMYEh0PgBh1CKiU4wON17HkPsOcaIzJeRgIZgJ6QIW5ZoGp0IxzBCGBJdFvc3GASqSEfnQFEvZLgXAklNX+bcyGb+duUoYsySyoUntTDms4Gnv0J6qzH0iz5hZz+FALjM/KLePq/aWCgzi+CzpgPVi+RCTg4EslYENj/ieyPq7+ZiBeEalJP9svqby7EdRtk+NQyTUtwKoi5USkqQiQUYl8Ac9tn4hOkqrBABRA3ORO/QKrkPDu4lrKDhBETFUEgqbA4E/GJzP+CArDtOSuY3BqhFnLxPdjEGkUwkowSGme5pnn8gjxxQf6LCfn8hHxhuQYiNy/IF2ALbITteiz9JcR0GcXbrBSIup/PyX+4I38OoXVzTp6DEXyek/Wz7+fGMjmKYLLIuL83HAy7EY/wjxtMKQ4h3QPenCKz6mFMGQBQK9HH2U/B/S+ph8kkvvTclEvXgVndLeQTFy1uS1HQ4rXCi4yQ2Sz9JDukxmjIAAclh0e6h72e0NhkMGE18OCYcoaJQuYoyWSmBDc2fwqiqllWh9RdfaRJCSjkLGmS1V3ksqy+zzZq+y/C/m8ypYwJItEbJpHAGsigRpqEHp1hO8y1pgtm8/xvkZqCn80TMJV+SGGydQvuNzBmxoqxLBFBXERmPfljXC06jJtrzFliSZw1yEjTZAKa5vTeLM2Mr9OMXtjbsWyAIykc95jMC8b8CNQOk1ibZM4nE/MNTMs9RT0tKCzeZce9spRIBZw6pYBzzTDMwvkOMisR84mAtVYwB5uDPnAisDk8ZlOQisB7jmsQr6hPy+TMR+x1SEspdYa6zznBAa7zEf1GWaifjlP6tbTexk7ASUQsol1YT8dINGKlFoj6syYw2qkN8ivsvP5g/NiRF0XxxSPH1Tv66Nj4gT0Pdq0XxfVdD+75l4XhgdgjHR2PnMJHzNPq8bT24IMb7Gh79/Tpd9s6Mu/ztxvqB7Y9/PC2gfqGhdEz+lZ4KPpWeNA+4hnQa4qpYJyMDzTrAN/kDZpCUhTSLDYOTjYSlUykEd5EiXey0SIJWgrOKEWcrMgbCbwZuWePqv/zx9crV+xcfzHO/Xv8lfTrwV6zePbtD/aM1o/uvd9dVv3JJZM5vNFDzvcFrcLjL7+5e8vXPv/XSbt9i9ra/GCPh/NuFJ64+a1dFzsvxuc98VfYnU1PbTjwys6y0Gh1mfv+vaP1n1zybgybTUfifTt3J0ZWVQ40rHjq5yeeOUh+xnp6HmymNcUXl6iv1sEHegaCDc+J4hO4AUSb4IV5BwkavRY8tDD1WN0/10VvPHX69Oguz31ru+qElc/Zjz11I7oOnVBrz86efOzAeSsZmXxiz2hR0clVNs/IpHrJev7AYyfp/owvvmioAhkqIGKgAsx1Q0KLgijnSmVyPpSriWSSG0shnIFDjgkOtTwJ/3JxY4zhAbfQs4NGKRgORqGssHh9QNAN5I0affYcEEoAupaz15Pp18CPh1LmCjuyIZNIcf42zAgO4GQzmx0Cs4BrY+DXAtZKgUjY4s6WNRIIHRUSpB4ozNIa5ra9wgzxA2LXaxWN2SSw12mTkdF7DPQGhLMSd055RCPSApRYv0YHKI6k2OvsUIYQxmIqfQvKwSy2raY2FJk1d1lRC6I6YrFCDWbj60iuQSdpCxqBlAANaK2SZ9p0D+0oIS/UY0dpyJ5VCWQfESIAsN0S1EIVoBPbYa81z9i6rYeSScrmrymTRK7NNUGSKAewIvVJ4ETqc4zvpLbPrRu+BL8BPSVs++4Jv1k/YneS1q2GvPrkHvHbis31/xd+Q62vaPitybgZfKeZ6WRkZjvFV0BYTrQLkB5tRhMHXs57JI/UyIFb+kPRUDTGRSPBiKhhqeYSPu36IhAp0s5Qg152aP9a533y6GaJYwlhOWnzqFzn8E8Xmtzb8+SGDU+exQchvqAP/qtv5V7TwNKa/qX350ymdDrwqKhEQr5dOXc4Wk6p4rbD2fvgZNppXUHtryEUduJBOJIgvXMSfB5/KILeboUviNvDQ3DZgzRiwUlbuO+Oc0WmFa4mq2n8z8gK59qGbp/bVJ7+uauhobux0XvmDBtNM1WSVMV+US1J1dvf96ysNls9qwMfkCvtjpX2qlUtNd3zjd24XF1FrpBt/qp5tcrvr+LYKn8mJjFWHND91BXsf0LoQpq4xrCW5hxExBLkWiAT9w4h0Nw4MPiTwYHGZoUaB3qiWYegltPoBZwJPITf4aKHAgF6HD0BDRANOTK4wWpNXyVFEa0bBS/JSrOEJFguYqFK6qlISwpES0oFgjsjmF579ENtYNYxNE+eEryikBIIPjrQkVvqjfXkG+TU+vzOT91CVvSrPyZ9/XqvuRl8wwxRK95NtaiEWNwlbC5Z7hH1qPoY55pPkRPkaD7pGfV7REn/EFT8IdmsYQ8YczWALccYsQewQv2Z+aMFMTuUfg3foapOwd+y9mRfuXuWUaNm2obCl46/XhLkziHI0SL1/1SjcnpfsVyMq6XtxrJBzq9JqedaDYc9S6G9n0a1aO8iIGVBgd4tFXhDWelsSUlho7zGl5Wrb/GlLM9P8QLPLOpP2+4J/UW7zUx4qG/R56KRZfeoNSDebGlpEY+iLttSPVNGoWiK59kSnvRSDZic/IW9mwg1EOZo8Dgf9IhevR7IBAdBpHFnbnmwT4S8PJTuUTLpH2MiEcCQhlydACdNaQGuBTuZxa7HISQSAjShRVm+XvCnMNMKmQkQegFlKF9HBn/qiKCFZyeb/QbAxyq4ofiBF4JQfQJZJTSemfECzCjzt5NaW5y+lUgEtEl6d5TUllE9khS/ArgQKr5E+ngiAe3a4nqieel+sJPE2EYOynoxRpxQ3ns9WA4vUWDUdFaXNfU9sClUvL+opc1vqHPiFdVSPeNgeduWHT21nHd9rc3hKW7oqHEImwrUIPK99pBRwUvL9xhpJDz+kOFEBe6pKnEIzjqDv62laH9xaNMDfU1l1R21y+80r7k2CY6ajoZij8NWu34tV9u7Y0trObOojvMywSU0i4LknFGETknwWiW+kQ0HoaNyctGCOhyMRYWHXni1v6X12Uc7Ei0tbfg2oU8WFPrztpdemRjg1+6qLJP/tEt9e2g1fddnM33JecMu7gV6BgzBeIbOyA7SccFQIwd9HJ4A/jYEolu9NicXiRLLyIljx078+L77zOb49xMdT3z7ey+0ssMjJ44f+/o/1tWazX2ZSa5sW1WVY83fHTvy9ZMPE+fA80dibOu69OhgdbXT+SrMnhpVf731+cNdpDWa06/jnQ+DWTobyyINJrw3HUu/pmj9OPh/EuOCer2W0pLYwOP9BJelVczY8fbTB9SgaHZbOHdu10CjECBBmUi/H6AkaX4kZlIfQIBmmybSPZwrqV8MuBAjsOjAnnLCMAznuwpoi0YJIwZPOKfMsPHcmZvyzc7JzU8fHO3o7OwYPTiLg+BlmG0OZj/j4On+5/Wz0Gg2fQlVY4yEF0UD9CRRYBa/2XEXs+80B7P1DC1Wek63XIaVTYsE2DwptpzuydY0dH2weeFO/hqZRqtifocWLd0DLSpMl4LM63QcxvyP91iIx2uYECIj0X86wttEfFlBJ4IviFy8EPctqLAQ5FicBy1QpCP0QjPw5/JBmQ3Dowhe6X+GB/fLBEA2698m99TU1tb0yJcyA/U/tT6PG8MVHGzdlH4HdwziXhxBoQb/Unm76ECdiWAPGBnWdf7iM8MDXCtWDQRNHuWN+HupCKHAC5CN/ZIADYbIS/TCB55B7aInEg6FI4YdrV3upvJYvHnimbYVz/7H1upAXbC+rr+lqVk4tGH932zvm3rguWOHBu6v9cfYdyuLbR1rfaaQuOEbvfzX9resiwxXk0quZWdHaXlJ91YSaihtbI4Edu84dODRcnNDJm4vch9z1+hvnoyY4yBkkcfY0MTJLGqphwd7NbV7/zYzULLo+DiZzvuGDjJ4RvmJTD1kvTyO3gVvLMw9735rQRQla3tSf7dQgws/GufIlz3ybYUkVRZ+H9Zs9F/QF0QBAXy5WdqHKQ7Ss4n4JV+RhOHkl6IwBcKS69MY6dOkhDdVFBdXmHh1jnwW99UG6/rauh3VSbzlEBy/MrB8efH8R8XlPGv4lbOventTeHdVX93pvp7ONt1eGu8iqHCxLzJCyyxKy5KBPff6j370+ntfLgh7+rnkc9JypNHscIXawbOUHRpI9jeHqEj8d/Nmb16NX70qv/GGfPVqvKAVkplv4T+TtcEV3QY1X26DfP6zSxggT4ilLZAviSbHad0PQsv1BN8ixyhkk6l438CuLfHh0eYmNfUVTvLLePcbex9+szu+5cMTTx06oNzlM4asnJrPtN2b1yyWd0kbLiH00ub8Csnpb8mQA1xQX0KlQyDq1xB6022ib15EBFpCSP4wxUi8Yo1GgogPUG2QBmIIl/IGvDAx8KUlobXhyzvu37onvt+/NlRi4rkC0+kkzc5TUl+wMxTqDMZrfJFSs7a0rDTiW/dkaxNM90l502rlD37A/C93fqv3AAB4nGNgZGBgAOLrq24eiue3+crAzbIBKMJw5+fjSwj6vwXLOuZtQC4HAxNIFAC4FA89AAAAeJxjYGRgYH7x34KBgWUDAxCwrGNgZEAFkQBgNQPkAAB4nGNgYGBg2TCKMbAP8WoJAQBQDjfdAAB4nGNgAAIfhhOMMowmjCmMsxi3MJ5gfMD4i0mKSY/JgymJqYlpGtM6pmNMt5jZmB2YQ5g7mG+wCLHksLSxbGJ5wsrCqsLqx9rEeoWNha2A7Qa7FLsDewH7NPY97B849DiSOLZw6nG2cZ7gEuKy4crhauNawHWFW407ifsQ9z+eMJ4lvEK8abxreC/xMfHp8FXwtfF94nfir+K/IiAkECEwReCGoI5gh+ADdAgAM0MwdHicY2BkYGCIZAhh4GIAASYg5gKz/4P5DAAaxwHOAAAAeJxtkT1OwzAYht/0D9FKCARiYfECC2r6M3ZkaPcO3dPESVMlceS4Fb0DJ+AQHIKBM3AIDsFb80mVUG3Jfr7H7xcrCYBrfCHAcQTo+/U4Wrhg9cdt0o1wh/wg3MUAj8I9+rFwH8+YCQ9wC80nBJ1Lmju8CrdwhTfhNv27cIf8IdzFPT6Fe/Tfwn2s8CM8wFPwkjSpHeaxqZqlznZFZE/iRCttm9xUahKOT3KhK20jpxO1Pqhmn02dS1VqTanmpnK6KIyqrdnq2IUb5+rZaJSKD2NTIkGDFBZD5IhhULFe8n0z7FAg4sm5xDm3YpflnvtaYYKQ3/NccsFk5dMRHPeE6TUOXBvsefOU1rFL+U6DkjT3vcd0wWloan+2pYnpQ2x8V83/NuJM/+VDf3v5C7A1ZCwAAAB4nG1UV1vbQBD0kEYxAQwJkN67Ukjvvfce8naWTlgfpzvnJGH497nblWwZ0IO/mbndvd1ZS42RBj/NxvbPMkawAzuxC7uxB6MYwzgm0MQk9mIK05hBC7OYwz7sxzwWsIgDOIhDOIwjOIpjOI4TOIlTOI0zOItzOI8LuIhLCHAZV3AV17CE67iBm7iF27iDu7iH+3iAh3iEx3iCp3iG53iBl3iF13iDt3iH9/iAj/iEz/iCr/iG7/iBn/iF3/iDZfxtNEUYmkLnQZwo1Scq0XJKRFEQJjZUkvio5x6MCyUtJ5SQw601vSAyPU18psazeoSSMWfM13jmytmM9YUh3SuuStFWVcnawTQrNlnpDNVkwcWIsubiJn1QtLX1ZLYuFV3SJlkr2VSfccZk6IzQkbDkyoCRXWFHhqsE5wi2zXrlq4/eIpJ7oTKZrIcNK1yYFA8nIqlkzoEVpr68/coIXtyYjBLeGyOvtaSbxAY9YXWiV+hwk8RR67m0WijPeJZRucF3ND0wccwTxiKUbWNW66233I8M+q1sI1F3JFF3hKh/Qt0oZl/7jHaf6NjYVOSJ0XQ8JPiIvYnOcrFiRcoO+t7d4DrwZtNFyrjNDBC1kYpEsUaI7E2lLoKlUvWY6nVFsWlHQwpV6yqxwXmEyLCuTbSzk1+5itC4/wqZ9ecZMMqyMrYy63BWReiOTKyVxhGijjMpbMjBFaYbsqKdWxHy8sfzjkw5tZn3krxqasxNUUdk95pRRco7Y7vrQj0iLcp/4pBACykF99748xqlCTdMkRdtznUfLQmNwn2yQnRgG43/Nx/DWwA=`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/ressources](https://france-chaleur-urbaine.beta.gouv.fr/ressources)
  
  
  * Method: `GET`
  
  
  * Evidence: `4513-ciOQq/E2v1d4JRbgvIEuOorjKFk`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr](https://france-chaleur-urbaine.beta.gouv.fr)
  
  
  * Method: `GET`
  
  
  * Evidence: `353b-RNVtJ+4D5UX5VqrGGhXfknEj1Gs`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/partenaires](https://france-chaleur-urbaine.beta.gouv.fr/partenaires)
  
  
  * Method: `GET`
  
  
  * Evidence: `3507-TTPv+SHV+DlzKTh0dMhQsoWSFAQ`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/Comparaison-AMORCE.png](https://france-chaleur-urbaine.beta.gouv.fr/Comparaison-AMORCE.png)
  
  
  * Method: `GET`
  
  
  * Evidence: `E5_-P-P-P-P-P-P-P-P-P-P-P-P-P-P-P-p`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/politique-de-confidentialite](https://france-chaleur-urbaine.beta.gouv.fr/politique-de-confidentialite)
  
  
  * Method: `GET`
  
  
  * Evidence: `3a80-JmVNfiSHrCUiYpp634n+Kf2qWro`
  
  
  
  
Instances: 11
  
### Solution
<p>Manually confirm that the Base64 data does not leak sensitive information, and that the data cannot be aggregated/used to exploit other vulnerabilities.</p>
  
### Other information
<p>ߝ��\x0013U���\x000f�\x0017�Z�\x0018hW~IďQ�</p>
  
### Reference
* http://projects.webappsec.org/w/page/13246936/Information%20Leakage

  
#### CWE Id : 200
  
#### WASC Id : 13
  
#### Source ID : 3

  
  
  
  
### Information Disclosure - Suspicious Comments
##### Informational (Low)
  
  
  
  
#### Description
<p>The response appears to contain suspicious comments which may help an attacker. Note: Matches made within script blocks or files are against the entire content not only comments.</p>
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/mentions-legales](https://france-chaleur-urbaine.beta.gouv.fr/mentions-legales)
  
  
  * Method: `GET`
  
  
  * Evidence: `query`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/_next/static/chunks/framework-c93ed74a065331c4bd75.js](https://france-chaleur-urbaine.beta.gouv.fr/_next/static/chunks/framework-c93ed74a065331c4bd75.js)
  
  
  * Method: `GET`
  
  
  * Evidence: `select`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr](https://france-chaleur-urbaine.beta.gouv.fr)
  
  
  * Method: `GET`
  
  
  * Evidence: `query`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/_next/static/chunks/pages/_error-ef6fb2a85018fcbd5e37.js](https://france-chaleur-urbaine.beta.gouv.fr/_next/static/chunks/pages/_error-ef6fb2a85018fcbd5e37.js)
  
  
  * Method: `GET`
  
  
  * Evidence: `from`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/_next/static/chunks/main-cdc763525a8ea4696302.js](https://france-chaleur-urbaine.beta.gouv.fr/_next/static/chunks/main-cdc763525a8ea4696302.js)
  
  
  * Method: `GET`
  
  
  * Evidence: `query`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/_next/static/chunks/pages/_app-b1559682e86a1ccb6406.js](https://france-chaleur-urbaine.beta.gouv.fr/_next/static/chunks/pages/_app-b1559682e86a1ccb6406.js)
  
  
  * Method: `GET`
  
  
  * Evidence: `from`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/robots.txt](https://france-chaleur-urbaine.beta.gouv.fr/robots.txt)
  
  
  * Method: `GET`
  
  
  * Evidence: `query`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/ressources](https://france-chaleur-urbaine.beta.gouv.fr/ressources)
  
  
  * Method: `GET`
  
  
  * Evidence: `query`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/partenaires](https://france-chaleur-urbaine.beta.gouv.fr/partenaires)
  
  
  * Method: `GET`
  
  
  * Evidence: `query`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/](https://france-chaleur-urbaine.beta.gouv.fr/)
  
  
  * Method: `GET`
  
  
  * Evidence: `query`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/sitemap.xml](https://france-chaleur-urbaine.beta.gouv.fr/sitemap.xml)
  
  
  * Method: `GET`
  
  
  * Evidence: `query`
  
  
  
  
Instances: 11
  
### Solution
<p>Remove all comments that return information that may help an attacker and fix any underlying problems they refer to.</p>
  
### Other information
<p>The following pattern was used: \bQUERY\b and was detected in the element starting with: "<script id="__NEXT_DATA__" type="application/json">{"props":{"pageProps":{}},"page":"/mentions-legales","query":{},"buildId":"1X", see evidence field for the suspicious comment/snippet.</p>
  
### Reference
* 

  
#### CWE Id : 200
  
#### WASC Id : 13
  
#### Source ID : 3

  
  
  
  
### Modern Web Application
##### Informational (Medium)
  
  
  
  
#### Description
<p>The application appears to be a modern web application. If you need to explore it automatically then the Ajax Spider may well be more effective than the standard one.</p>
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/APC.pdf](https://france-chaleur-urbaine.beta.gouv.fr/APC.pdf)
  
  
  * Method: `GET`
  
  
  * Evidence: `<A>`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/ressources](https://france-chaleur-urbaine.beta.gouv.fr/ressources)
  
  
  * Method: `GET`
  
  
  * Evidence: `<a class="fr-footer__bottom-link">Accessibilité: non conforme</a>`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/mentions-legales](https://france-chaleur-urbaine.beta.gouv.fr/mentions-legales)
  
  
  * Method: `GET`
  
  
  * Evidence: `<a class="fr-footer__bottom-link">Accessibilité: non conforme</a>`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/partenaires](https://france-chaleur-urbaine.beta.gouv.fr/partenaires)
  
  
  * Method: `GET`
  
  
  * Evidence: `<a class="fr-footer__bottom-link">Accessibilité: non conforme</a>`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/politique-de-confidentialite](https://france-chaleur-urbaine.beta.gouv.fr/politique-de-confidentialite)
  
  
  * Method: `GET`
  
  
  * Evidence: `<a class="fr-footer__bottom-link">Accessibilité: non conforme</a>`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/](https://france-chaleur-urbaine.beta.gouv.fr/)
  
  
  * Method: `GET`
  
  
  * Evidence: `<a class="fr-footer__bottom-link">Accessibilité: non conforme</a>`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/_next/static/chunks/framework-c93ed74a065331c4bd75.js](https://france-chaleur-urbaine.beta.gouv.fr/_next/static/chunks/framework-c93ed74a065331c4bd75.js)
  
  
  * Method: `GET`
  
  
  * Evidence: `<script>`
  
  
  
  
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
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr](https://france-chaleur-urbaine.beta.gouv.fr)
  
  
  * Method: `GET`
  
  
  * Evidence: `<a class="fr-footer__bottom-link">Accessibilité: non conforme</a>`
  
  
  
  
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
  
  
  
  
Instances: 11
  
### Solution
<p>This is an informational alert and so no changes are required.</p>
  
### Other information
<p>Links have been found that do not have traditional href attributes, which is an indication that this is a modern web application.</p>
  
### Reference
* 

  
#### Source ID : 3

  
  
  
  
### Storable and Cacheable Content
##### Informational (Medium)
  
  
  
  
#### Description
<p>The response contents are storable by caching components such as proxy servers, and may be retrieved directly from the cache, rather than from the origin server by the caching servers, in response to similar requests from other users.  If the response data is sensitive, personal or user-specific, this may result in sensitive information being leaked. In some cases, this may even result in a user gaining complete control of the session of another user, depending on the configuration of the caching components in use in their environment. This is primarily an issue where "shared" caching servers such as "proxy" caches are configured on the local network. This configuration is typically found in corporate or educational environments, for instance.</p>
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/robots.txt](https://france-chaleur-urbaine.beta.gouv.fr/robots.txt)
  
  
  * Method: `GET`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/ressources](https://france-chaleur-urbaine.beta.gouv.fr/ressources)
  
  
  * Method: `GET`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/_next/static/chunks/pages/_app-b1559682e86a1ccb6406.js](https://france-chaleur-urbaine.beta.gouv.fr/_next/static/chunks/pages/_app-b1559682e86a1ccb6406.js)
  
  
  * Method: `GET`
  
  
  * Evidence: `max-age=31536000`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/_next/static/chunks/main-cdc763525a8ea4696302.js](https://france-chaleur-urbaine.beta.gouv.fr/_next/static/chunks/main-cdc763525a8ea4696302.js)
  
  
  * Method: `GET`
  
  
  * Evidence: `max-age=31536000`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/sitemap.xml](https://france-chaleur-urbaine.beta.gouv.fr/sitemap.xml)
  
  
  * Method: `GET`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/_next/static/chunks/framework-c93ed74a065331c4bd75.js](https://france-chaleur-urbaine.beta.gouv.fr/_next/static/chunks/framework-c93ed74a065331c4bd75.js)
  
  
  * Method: `GET`
  
  
  * Evidence: `max-age=31536000`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/_next/static/chunks/pages/_error-ef6fb2a85018fcbd5e37.js](https://france-chaleur-urbaine.beta.gouv.fr/_next/static/chunks/pages/_error-ef6fb2a85018fcbd5e37.js)
  
  
  * Method: `GET`
  
  
  * Evidence: `max-age=31536000`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/_next/static/chunks/webpack-9e447151ce92b4aa8322.js](https://france-chaleur-urbaine.beta.gouv.fr/_next/static/chunks/webpack-9e447151ce92b4aa8322.js)
  
  
  * Method: `GET`
  
  
  * Evidence: `max-age=31536000`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/_next/static/css/00104bcde2c4b2198fa2.css](https://france-chaleur-urbaine.beta.gouv.fr/_next/static/css/00104bcde2c4b2198fa2.css)
  
  
  * Method: `GET`
  
  
  * Evidence: `max-age=31536000`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/](https://france-chaleur-urbaine.beta.gouv.fr/)
  
  
  * Method: `GET`
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr](https://france-chaleur-urbaine.beta.gouv.fr)
  
  
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
  
  
  
  
* URL: [https://france-chaleur-urbaine.beta.gouv.fr/_next/static/chunks/webpack-9e447151ce92b4aa8322.js](https://france-chaleur-urbaine.beta.gouv.fr/_next/static/chunks/webpack-9e447151ce92b4aa8322.js)
  
  
  * Method: `GET`
  
  
  * Evidence: `39789197`
  
  
  
  
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
  
  
  
  
Instances: 12
  
### Solution
<p>Manually confirm that the timestamp data is not sensitive, and that the data cannot be aggregated to disclose exploitable patterns.</p>
  
### Other information
<p>23000091, which evaluates to: 1970-09-24 04:54:51</p>
  
### Reference
* http://projects.webappsec.org/w/page/13246936/Information%20Leakage

  
#### CWE Id : 200
  
#### WASC Id : 13
  
#### Source ID : 3
