# Attaques sur les fichiers PDFs

## Introduction

Les fichiers PDFs sont un vecteur d'attaque intéressant.

Ils sont tout d'abord très utilisés, par des millions de personnes, et sont disponibles sur les trois systèmes d'exploitation utilisateurs majeurs: Windows, MacOS, et (GNU/)Linux.

En lui-même, le PDF est un fichier de présentation. Il vise à transmettre des informations données sous une forme visuelle donnée. Ainsi, son format est complexe, car il décrit précisément l'organisation visuelle des différents éléments: texte, police, encadrés, couleurs, ...
Il peut usuellement inclure des images, et pour les versions les plus riches[^multimedia], des vidéos, des pistes sonores, ou des modèles 3D[^3D]. Enfin, un fichier PDF peut contenir des formulaires (basés notamment HTML ou XML)[^formulaire], et même, pour encore plus d'interactivités, peut exécuter du code en Javascript.

Cette richesse accroît la surface d'attaque sur le format en lui-même, et permet à l'attaquant de faire preuve de sa créativité.

Pour analyser et faire un rendu de ce format complexe, les fichiers PDFs sont lus et affichés par des lecteurs appropriés. Le lecteur est ainsi un vecteur d'attaque supplémentaire. Les lecteurs de PDFs doivent être capable de comprendre un format complexe, ce qui accroît les possibilités d'erreur d'implémentation.

Enfin, les PDFs, de part leur universalité d'utilisation, proposent d'encrypter un document, ou de le signer numériquement (avec une signature digitale). Ces services de sécurité présentes sont également sujets à des attaques.

Ce document se concentre ainsi sur les:

+ Attaques sur le format PDF
+ Attaques sur les lecteurs de PDF
+ Attaques sur les services de sécurité associés à un fichier PDF

[^multimedia]: https://helpx.adobe.com/fr/acrobat/using/rich-media.html
[^3D]: https://fr.wikipedia.org/wiki/Portable_Document_Format#3D
[^formulaire]: https://en.wikipedia.org/wiki/PDF#Forms



## Attaques sur le format PDF

### Les possibilités du format

Utilisation de Javascript:

Problème implémentation de l'API javascript du lecteur de PDF de chrome, autorisant un attaqueur à faire des requêtes HTTP depuis la machine de l'utilisateur

	https://blog.edgespot.io/2019/02/edgespot-detects-pdf-zero-day-samples.html

Plus et autres:

	https://www.pdf-insecurity.org/pdf-dangerous-paths/attacks.html


### Implémentation du format dans les lecteurs

L'implémentation d'un parser pour le format PDF est délicate, et donc est sujette à des erreurs d'implémentations engendrant des vulnérabilités.

Parser de PDF pouvant causer un DOS du fait d'une mauvaise regex dans une libraire python:

	https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2021-25292
	https://pillow.readthedocs.io/en/stable/releasenotes/8.1.1.html

Vulnerability of ClamAV: denial of service via the PDF parser due to stack buffer overflow read. 

	https://vigilance.fr/vulnerability/ClamAV-denial-of-service-via-the-PDF-parser-32252

En cherchant des CVEs sur MITRE, on peut en trouver beaucoup d'autres:

	https://cve.mitre.org/cgi-bin/cvekey.cgi?keyword=pdf

quelques exemples:

	CVE-2022-24954 	Foxit PDF Reader before 11.2.1 and Foxit PDF Editor before 11.2.1 have a Stack-Based Buffer Overflow related to XFA, for the 'subform colSpan="-2"' and 'draw colSpan="1"' substrings. 

	CVE-2022-24197 	iText v7.1.17 was discovered to contain a stack-based buffer overflow via the component ByteBuffer.append, which allows attackers to cause a Denial of Service (DoS) via a crafted PDF file.

	CVE-2022-24196 	iText v7.1.17 was discovered to contain an out-of-memory error via the component readStreamBytesRaw, which allows attackers to cause a Denial of Service (DoS) via a crafted PDF file. 


## Attaques sur les services de sécurité associés à un fichier PDF

### Signatures

https://www.pdf-insecurity.org/signature/certification.html

https://dl.acm.org/doi/10.1145/3319535.3339812


### Attaque sur la protection par mot de passe d'un fichier PDF

Owner vs User

https://www.lifewire.com/what-is-a-pdf-owner-password-2619254
http://www.verypdf.com/wordpress/201204/whats-the-difference-user-password-and-owner-password-24678.html

Owner: easy, just discard it

https://hashcat.net/forum/thread-6233-page-2.html

User:

démo en fin de document









## Protection et contre-mesures

Pour se protéger d'un fichier PDF potentiellement malveillant, les recommendations usuelles adaptables à n'importe quel fichier potentiellement malveillant s'appliquent:

+ Ne pas ouvrir ce fichier.
+ N'ouvrir ce fichier que dans des environnements sûrs, par exemple:
	+ un ordinateur dédié à cela,
	+ une VM
	+ utiliser les lecteurs de PDF inclut dans les navigateurs internet (e.g. `pdf.js`) plutôt qu'une application de bureau. En effet, on peut espérer que même s'il y a une faille de sécurité, la sandbox du navigateur offrira plus de protection qu'une application, qui elle est directement en contact avec le système.
+ Toujours utiliser des logiciels (dans le cas des PDFs, les lecteurs de PDFs notamment[^éditeurs]) à jour.
+ Faire une analyse du fichier, par exemple avec VirusTotal[^VT]

Pour ce qui est des recommendations propres aux PDFs:,





- Best practices:

  https://security.stackexchange.com/questions/87534/why-is-pdf-still-safe

  https://security.stackexchange.com/questions/153308/is-there-a-best-practice-regarding-pdf-files-on-website





[^éditeurs]: On pourrait également penser aux logiciels qui génèrent ou éditent des PDFs, par exemple *LibreOffice* ou *Microsoft Word*.
[^VT]: https://support.virustotal.com/hc/en-us/articles/115002075969-What-kind-of-files-will-VirusTotal-scan-



## Analyses de fichiers

https://malwarecheese.com/posts/pdf-malware-analysis.html


  https://www.sans.org/posters/cheat-sheet-for-analyzing-malicious-documents/



















## Exemples d'attaques



### Phishing + écrit un fichier 
https://github.com/edwisdom/googlespoof/blob/master/Security%20Final%20Project.pdf



### Password Cracking

Avec john

	pdf2john to_crack.pdf > /tmp/hash &&
	john --wordlist=`locate -e rockyou.txt` /tmp/hash

Par exemple, le hash

	"$pdf$4*4*128*-1028*1*16*51cacf728db0cc489bd42a56dd58d87c*32*fa9ce7f2daef91b171ec19e04edc00ba00000000000000000000000000000000*32*c431fab9cc5ef7b59c244b61b745f71ac5ba427b1b9102da468e77127f1e69d6"

correspond au mdp "123456".

https://blog.pentesteracademy.com/cracking-password-of-a-protected-pdf-file-using-hashcat-and-john-the-ripper-1b50074eeabd
https://hackntricks.fr/cracker-un-pdf-avec-john-the-ripper-sur-kali/

HashCat peut égalemnt être utilisé. Il supporte les versions 1.1 à 1.7 du format PDF.[^hashcat]

[^hashcat]: https://hashcat.net/wiki/doku.php?id=example_hashes


Plus et autres

	https://www.pdf-insecurity.org/encryption/encryption.html



### Exemple: pidief trojan

http://www.secuser.com/alertes/2007/pidief.htm

https://www.f-secure.com/v-descs/exploit_js_pidief.shtml

