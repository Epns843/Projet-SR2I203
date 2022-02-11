# Attaques sur les fichiers PDFs

## Introduction

Les fichiers PDFs sont un vecteur d'attaque intéressant.

Ils sont tout d'abord très utilisés, par des millions de personnes, et sont disponibles sur les trois systèmes d'exploitation utilisateurs majeurs: Windows, MacOS, et (GNU/)Linux.

En lui-même, le PDF est un fichier de présentation. Il vise à transmettre des informations données sous une forme visuelle donnée. Ainsi, son format est complexe, car il décrit précisément l'organisation visuelle des différents éléments: texte, police, encadrés, couleurs, ...
Il peut usuellement inclure des images, et pour les versions les plus riches[^multimedia], des vidéos, des pistes sonores, ou des modèles 3D[^3D]. Enfin, un fichier PDF peut contenir des formulaires (basés notamment HTML ou XML)[^formulaire], et même, pour encore plus d'interactivités, peut exécuter du code en Javascript.

Cette richesse accroît la surface d'attaque sur le format en lui-même.
Cela permet également, comme il sera illustré par la suite (!!!), une certaine créativité pour l'attaquant.

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

Idée: lire un fichier

## Attaques sur les lecteurs de PDF


## Attaques sur les services de sécurité associés à un fichier PDF

attaque DRM

### Cracker un mot de passe

Owner vs User

https://www.lifewire.com/what-is-a-pdf-owner-password-2619254
http://www.verypdf.com/wordpress/201204/whats-the-difference-user-password-and-owner-password-24678.html

Owner: easy, just discard it

https://hashcat.net/forum/thread-6233-page-2.html

User:



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



## Conclusion

Pour se protéger d'un fichier PDF potentiellement malveillant, les recommendations usuelles adaptables à n'importe quel fichier potentiellement malveillant s'appliquent:

+ Ne pas ouvrir ce fichier.
+ N'ouvrir ce fichier que dans des environnements sûrs, par exemple:
	+ un ordinateur dédié à cela,
	+ une VM
	+ utiliser les lecteurs de PDF inclut dans les navigateurs internet (e.g. `pdf.js`) plutôt qu'une application de bureau. En effet, on peut espérer que même s'il y a une faille de sécurité, la sandbox du navigateur offrira plus de protection qu'une application, qui elle est directement en contact avec le système.
+ Toujours utiliser des logiciels (dans le cas des PDFs, les lecteurs de PDFs notamment[^éditeurs]) à jour.
+ Faire une analyse du fichier, par exemple avec VirusTotal[^VT]

Pour ce qui est des recommendations propres aux PDFs:,

[^éditeurs]: On pourrait également penser aux logiciels qui génèrent ou éditent des PDFs, par exemple *LibreOffice* ou *Microsoft Word*.
[^VT]: https://support.virustotal.com/hc/en-us/articles/115002075969-What-kind-of-files-will-VirusTotal-scan-

## TODO
variante du format: https://en.wikipedia.org/wiki/PDF/A
(qui ne supporte pas l'encryption)


