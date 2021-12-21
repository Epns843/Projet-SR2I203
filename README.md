# Projet-SR2I203 :  Etude et mise œuvre des attaques sur les documents PDF

## Roadmap

- Documentation : 
  - Format PDF
  - Lecteurs de PDF
  - Différents types d'attaques
- Choix et implémentation d'une attaque
- Analyse de l'attaque et proposition de mécanismes de défense
- Réalisation d'une liste de bonnes pratiques pour se prémunir de ce type d'attaque 


## Bibliography

- Overview

  https://en.wikipedia.org/wiki/PDF

  https://malwarecheese.com/posts/pdf-malware-analysis.html

  https://0xdf.gitlab.io/2018/09/12/malware-analysis-yourexploitpdf.html

  https://0xdf.gitlab.io/2018/08/06/malware-analysis-inovoice-019338pdf.html

  https://www.sans.org/blog/pdf-malware-analysis/

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