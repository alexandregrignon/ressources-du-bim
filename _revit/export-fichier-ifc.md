---
layout: methode-revit
group: bonnes-pratiques
title: Exporter un fichier IFC
comments: true
---

Prérequis à prend en compte sans exception :

1. Avoir installé le dernier [Service Pack](https://knowledge.autodesk.com/support/revit-products/downloads) pour Revit
2.	Avoir installé le module "[IFC for Revit](https://sourceforge.net/projects/ifcexporter/files/)" (disponible pour les versions 2012 à 2018 de Revit)
3.	Avoir installé le module "[ARCHICAD Connection for Revit](http://www.graphisoft.com/downloads/interoperability.html)". Les versions précédentes sont disponibles en [archive](http://www.graphisoft.com/downloads/addons/interoperability/Archive.html).

> Il est recommandé d'utiliser systématiquement l'Add-In "ARCHICAD Connection for Revit" pour toutes les opération d'import/export avec ARCHICAD.
> ![capture]({{ site.url }}/assets/img/bp_revit_acfr_ruban.png)

---

## Conseils préalables

**Vérifications de modèle**

* **Important** - Valider au préalable les étapes de la page "Autocontrôle".
* Les utilisateurs Revit doivent vérifier que le **mapping** des éléments dans la table de correspondances est correct pour assurer la fiabilité de l'échange.
* Les modèles envoyés doivent être exportés depuis Revit avec uniquement les niveaux architecturaux. Par exemple, les niveaux additionnels créés pour des besoins structurels doivent être désactivés en décochant la case "Etage de bâtiment" dans les coupes et élévations. (réglage disponible pour Revit 2013 et ultérieur).
* Si une classification d'éléments à été choisie pour le projet, la méthode suivante doit être utilisée : [http://www.evolve-consultancy.com/resource/guides/ifc-classification-revit](http://www.evolve-consultancy.com/resource/guides/ifc-classification-revit).

**Contrôle visuel**

Il est recommandé d'effectuer un contrôle systématique des fichiers IFC à réception ou avant envoi à un tiers. Cela permet de prévenir toute erreur avant import dans le logiciel-métier. Il est possible d'utiliser un viewer IFC gratuit parmi ceux proposés dans la liste suivante :

* **Solibri Model Viewer** (PC ou Mac) : [http://www.solibri.com/products/solibri-model-viewer/](http://www.solibri.com/products/solibri-model-viewer/)
* **Tekla BIMsight** (PC) : [http://www.teklabimsight.com/](http://www.teklabimsight.com/)
* **BIM Vision** (PC) : [http://bimvision.eu/en/download/](http://bimvision.eu/en/download/)

## Méthode

### Export IFC vers ARCHICAD

Utiliser le bouton "Export to ARCHICAD" dans l'onglet "Compléments" du ruban.

![capture]({{ site.url }}/assets/img/bp_revit_acfr_export_to_archicad.png)

## Options d'export IFC

**Géolocalisation** : 

**Exporter un extrait de maquette** :

**Exporter les propriétés IFC** :

## Options d'export pour les modèles Fluides (Revit MEP)



## Sources

* **IFC ARCHICAD & REVIT - Bonnes pratiques** [PDF en ligne - mis à jour en mai 2017]. Abvent, 2017. Disponible sur : [https://archicad.fr/download/guide-ifc-abvent/?wpdmdl=14005](https://archicad.fr/download/guide-ifc-abvent/?wpdmdl=14005)
* **Les bonnes pratiques BIM IFC dans Revit** [PDF en ligne]. Autodesk, 2016. Disponible sur : [http://abcdblog.typepad.com/abcd/2016/05/Livre_blanc_Autodesk-Bonnes_Pratiques_BIM-Revit-IFC.pdf](http://abcdblog.typepad.com/abcd/2016/05/Livre_blanc_Autodesk-Bonnes_Pratiques_BIM-Revit-IFC.pdf)
* **Guidance notes for Autodesk Revit users exchanging models with Graphisoft ARCHICAD** [Article en ligne]. BIM Blog, Bond Bryan Digital. Disponible sur : [http://bimblog.bondbryan.com/guidance-notes-for-autodesk-revit-users-exchanging-models-with-graphisoft-archicad/](http://bimblog.bondbryan.com/guidance-notes-for-autodesk-revit-users-exchanging-models-with-graphisoft-archicad/)
* **Protocol IFC export met Revit** [Article en ligne]. Open Bimmers. Disponible sur : [http://openbimmers.nl/protocol-ifc-export-met-revit/](http://openbimmers.nl/protocol-ifc-export-met-revit/)
* **A tool to build Revit's IFC mapping tables - feedback and revision** [Article en ligne]. Ik Leer BIM. Disponible sur : [http://ikleerbim.blogspot.fr/2017/02/a-tool-to-build-revits-ifc-mapping.html?m=1](http://ikleerbim.blogspot.fr/2017/02/a-tool-to-build-revits-ifc-mapping.html?m=1)
