# Bibliography

- Overview

  https://en.wikipedia.org/wiki/PDF : 

    -> PDF documents can support JavaScript
    -> PDF uses a subset of the PostScript page description programming language : runs in an interpreter to generate images  
    -> attacks : modifying content without invalidating the signature, extract encrypted content, DoS, arbitrary code execution 

  https://malwarecheese.com/posts/pdf-malware-analysis.html : 

    -> explique la structure d'un fichier PDF 
    -> possible de mettre un objet contenant des instructions à exécuter dès l'ouverture du document 
    -> possibilité d'évaluer la dangerosité d'un PDf avant de l'ouvrir -> cf. **Tools** : `pdfid`  

  https://0xdf.gitlab.io/2018/09/12/malware-analysis-yourexploitpdf.html : 
  
    -> décorticage d'une attaque par PDF exécutant un code arbitraire 
    -> existance d'entrées du dictionnaire d'action permettant de discréditer la plateforme sur laquelle le fichier est ouvert 
    -> foinctionnement de l'attaque : ouverture d'un shell, connexion à un site malveillant, téléchargement d'un malware hébergé sur le site, exécution du malware 
    -> le fait que le PDF soit frauduleux est détecté par un minorité d'agent de sécurité, mais le malware qu'il essaye d'exécuter l'est part une grande majorité -> attaque pas si efficace 

  https://0xdf.gitlab.io/2018/08/06/malware-analysis-inovoice-019338pdf.html : 
  
    -> même type d'attaque que la précédente, un peu plus élaborée mais demande à l'utilisateur son autorisation pour ouvrir un second document lors de l'attaque -> si vigilant, peut être empêchée    

  https://www.sans.org/blog/pdf-malware-analysis/

    -> décorticage d'une attaque par injection de code arbitraire via PDF 

  https://www.sans.org/posters/cheat-sheet-for-analyzing-malicious-documents/

  https://www.sans.org/white-papers/33443/

  https://www.sentinelone.com/blog/malicious-pdfs-revealing-techniques-behind-attacks/

- Different kinds of attacks:

  https://en.wikipedia.org/wiki/PDF#Security

  - On the digital signatures authentifying the pdf

  https://dl.acm.org/doi/10.1145/3319535.3339812

  - On the password encrypting the pdf

  https://superuser.com/questions/56132/how-good-is-pdf-password-protection

  - Exploiting the PDF format:

    PDf can contain

      - Javascript
      - OpenAction (automatic code)
      - AcroForm and XFA: in-pdf forms

    that can lead to remote code-execution, or can drop a malicious program (e.g. a virus)

    https://security.stackexchange.com/questions/64052/can-a-pdf-file-contain-a-virus

    exemple de malware: pidief

  - Exploiting flaws in the pdf viewers

    https://nvd.nist.gov/vuln/detail/CVE-2018-4901

  - Misc:

  https://blog.didierstevens.com/2010/03/29/escape-from-pdf/

- Best practices:

  https://security.stackexchange.com/questions/87534/why-is-pdf-still-safe

  https://security.stackexchange.com/questions/153308/is-there-a-best-practice-regarding-pdf-files-on-website

- Tools:

  https://blog.didierstevens.com/programs/pdf-tools/