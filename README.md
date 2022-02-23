# Projet-SR2I203 :  Etude et mise en œuvre des attaques sur les documents PDF

## Rapport du projet 

Le rapport du projet est dans le fichier rapport.pdf


## `examples` 

On trouvera dans ce répertoire des exemples de PDF lançant un code arbitraire (innoffensif). Ces exemples sont issus du travail de Didier Stevens (https://blog.didierstevens.com/2008/04/29/pdf-let-me-count-the-ways/). 

Ils ont été testés sous Linux avec plusieurs lecteurs de PDF (evince et adobe acrobat reader), sans succés car les lecteurs ont beaucoup de fonctionnalités désactivées. 
Sous Windows, les "attaques" fonctionnent avec Adobe Acrobat Reader (version 2021.011.20039), en demandant d'autoriser la connexion au site distant. 


## `pdf_tools`

Ce répertoire contient plusieurs des outils développés par Didier Stevens (https://blog.didierstevens.com/programs/pdf-tools/). On y retrouve : 
    - `pdfid` : cet outil permet de scanner un PDF à la recherche de certains mots clés, comme du JavaScript, ou les balises d'exécution automatique 
    - `parser` : un simple parser de PDF, permettant de compter les différentes types d'objet du PDF donné en entrée 
    - `maker` : permet d'insérer du code JavaScript qui sera exécuté à l'ouverture du PDF 



## `src`

Essai de PDF exécutant un code arbitraire à l'ouverture 