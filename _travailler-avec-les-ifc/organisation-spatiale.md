---
layout: default-toc
group: travailler-avec-les-ifc
title: Organisation spatiale
description: Méthode d'organisation hiérarchique des objets IFC (site, bâtiment, niveau, espace), géoréférencement.
comments: true
icon: cubes
ordre: 3
status: publish
redirect_from:
  - /bonnes-pratiques/regles-base/organisation-spatiale/
---

# Organisation spatiale

## Arborescence IFC

Tout projet doit être organisé avec l'arborescence spatiale `Projet > Site > Bâtiment > Niveau > Local > Ouvrage` dont la représentation IFC est la suivante :

~~~
IfcProject                  (Projet)
  > IfcSite                 (Site)
    > IfcBuilding           (Bâtiment)
      > IfcBuildingStorey   (Niveau)
        > IfcProduct        (Produit, Equipement)
        > IfcSpace          (Local)
          > IfcProduct      (Produit, Equipement)
~~~

Le système relationnel est un des fondements de l'IFC ; les objets sont reliés entre eux par la classe `IfcRelContainedInSpatialStructure`. Par exemple, une fenêtre est attachée à un mur, et ce même mur dépend d'un étage. Ces relations sont généralement gérées automatiquement par les logiciels-métier.

Un fichier IFC ne doit contenir qu'un seul bâtiment. Pour gérer plusieurs bâtiments appartenant au même site, il faut créer autant de fichiers natifs que de bâtiments en leur attribuant un même nom de projet (`IfcProject`) et de site (`IfcSite`).

Les éléments `IfcProduct` peuvent être contenues dans un niveau (`IfcBuildingStorey`) ou dans un local (`IfcSpace`), lui-même contenu dans un niveau.

Pour une bonne structure de fichier IFC, il est conseillé de renseigner à minima les attributs `IfcProject.Name`, `IfcSite.Name` et `IfcBuilding.Name`.

### Projet

La classe `IfcProject` est le plus haut niveau de l'arborescence d'un fichier IFC.

Tous les fichiers d'un projet doivent adopter le même `GUID` et le même attribut `Name` sous la classe `IfcProject`. Il est conseillé d'utiliser le `GUID` du fichier de l'architecte. Si le logiciel-métier ne permet pas de préserver le `GUID`, on peut se contenter de l'attribut `Name`.

### Site

La classe `IfcSite` définit le terrain sur lequel peuvent être placés un ou plusieurs bâtiments (`IfcBuilding`). Un seul objet `IfcSite` peut être contenu dans le projet (`IfcProject`).

Le nom du terrain est indiqué dans l'attribut `IfcSite.Name`, et le numéro de parcelle cadastrale dans le champ `IfcSite.LandTitleNumber`.

Tout comme pour l'`IfcProject`, l'objet `IfcSite` doit posséder un `GUID` et `Name` identiques dans tous les fichiers IFC.

Cette classe défini notamment le [géoréférencement](#géoréférencement) du projet.

### Bâtiment

La classe `IfcBuilding` regroupe l'ensemble des objets formant le bâtiment.

Un numéro de bâtiment peut être indiqué dans le champ `Pset_BuildingCommon.BuildingID`, tandis que le nom du bâtiment est inclus dans le champ `IfcBuilding.Name`.

### Niveaux

Les niveaux, définis par la classe `IfcBuildingStorey`, doivent respecter la logique spatiale de l'édifice, en incluant les mezzanines ou demi-niveaux.

Il est déconseillé d'utiliser des niveaux fictifs pour régler de façon simultanée les hauteurs de certains éléments. Tout niveau fictif d'aide au dessin (ex: plan masse) devra être exclu de l'export IFC.

La codification des niveaux est établie par des codes à 2 caractères dans le champ `IfcBuildingStorey.Name` + une description plus complète du niveau dans le champ `IfcBuildingStorey.LongName`.

<table class="table table-responsive table-bordered table-hover">
  <thead>
    <tr>
      <th>`IfcBuildingStorey.Name`</th>
      <th>`IfcBuildingStorey.LongName`</th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>00</th>
      <th>Rez-de-chaussée</th>
      <td>Correspond au niveau d'accès au bâtiment depuis l'espace public</td>
    </tr>
    <tr>
      <th>01, 02, 03, ...</th>
      <th>Etages</th>
      <td>Niveaux en élévation au-dessus du sol</td>
    </tr>
    <tr>
      <th>S1, S2, S3, ...</th>
      <th>Sous-sol</th>
      <td>Niveaux enterrés</td>
    </tr>
    <tr>
      <th>TT</th>
      <th>Toiture</th>
      <td>Au-dessus du dernier niveau d'étage</td>
    </tr>
  </tbody>
</table>

Il est également possible d'indiquer le niveau d'entrée dans le bâtiment avec l'attribut `Pset_BuildingStoreyCommon.EntranceLevel=TRUE` sur le niveau concerné. On pourra également définir les niveaux situés au-dessus du sol avec l'attribut `Pset_BuildingStoreyCommon.AboveGround=TRUE`.

### Locaux

Chaque local est représenté par un objet `IfcSpace` correspondant aux limites spatiales de cette pièce, dans les trois dimensions.

Le code (numéro) du local est inséré dans le champ `IfcSpace.Name`, tandis que son nom (ex: chambre, bureau) est renseigné dans le champ `IfcSpace.LongName`. Le code est généralement basé sur une nomenclature propre au maître d'ouvrage, par exemple sous la forme "SITE_BATIMENT_ETAGE_NUMERO-PIECE".

**Exemple de nomenclature de locaux**

<table class="table table-responsive table-bordered table-hover">
  <thead>
    <tr>
      <th>`IfcSpace.Name`</th>
      <th>`IfcSpace.LongName`</th>
      <td>Commentaire</td>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>CE_A_00_001</th>
      <th>Hall d'entrée</th>
      <td>Local "Hall d'entrée" n°001 situé au RDC du bâtiment A, sur le site "Campus Erdre" (CE)</td>
    </tr>
    <tr>
      <th>CE_A_00_012</th>
      <th>Bureau</th>
      <td>Local "Bureau" n°012 situé au RDC du bâtiment A, sur le site "Campus Erdre" (CE)</td>
    </tr>
    <tr>
      <th>CE_A_01_027</th>
      <th>Ménage</th>
      <td>Local "ménage" n°027 situé au niveau 1 du bâtiment A, sur le site "Campus Erdre" (CE)</td>
    </tr>
    <tr>
      <th>CL_D_03_005</th>
      <th>Salle de réunion</th>
      <td>Local "Salle de réunion" n°005 situé au niveau 3 du bâtiment D, sur le site "Campus Loire" (CL)</td>
    </tr>
  </tbody>
</table>

Il est possible de définir des relations entre plusieurs locaux à l'aide de la classe `IfcZone` (ex: zones thermiques, de recoupement au feu, zones fonctionnelles, acoustiques, ou plusieurs locaux appartenant à un même logement). Un même local peut appartenir à plusieurs zones.

## Géoréférencement

Chaque maquette est située dans l'espace par rapport à un point zéro projet qui doit être commun à toutes les disciplines pour garantir une parfaite superposition des différentes maquettes numériques.

Idéalement, le point zéro du projet se trouvera à l'intersection de deux axes, ce qui permettra de le situer facilement. Ou bien à une coordonnée géographique "ronde". Un volume 3D identifiable pourra être placé sur le point zéro afin de permettre un recollage facile des modèles numériques.

Sur l'illustration ci-dessous : montrer un bâtiment non orienté perpendiculairement au Nord, avec flèche vers le nord géographique.

![capture]({{ site.url }}/assets/img/bp_archicad_point_zero.png)

{% include callout-open.html param="danger" %}
**Attention !:**
La modélisation doit projet doit se situer à proximité du point zéro pour éviter des abberations géométriques.
{% include callout-close.html %}

La correspondance de ce zéro projet avec les coordonnées géographiques réelles se fait via les attributs `IfcSite.RefLatitude` et `IfcSite.RefLongitude` exprimés en degrés, minutes, secondes ; ainsi que la valeur d'altitude via l'attribut `IfcSite.RefElevation`.

Le projet doit toujours être modélisé en orientation réelle (nord géographique en haut, sur la coordonnée Y) ; les vues orientées au besoin sont gérées par le logiciel-métier.

## Axes du projet

Il est important de définir au plus tôt les axes du projet (`IfcGridAxis`), correspondant aux files porteuses.

Les axes et le point zéro commun seront communiqués en début de projet par fichier IFC ou référence DWG.

## Méthode de modélisation

Points de vigilance :

* Chaque objet est attribué à un étage
* Les murs sont recoupés entre deux niveaux
* En cas de doute, modéliser comme on construit.

![capture]({{ site.url }}/assets/img/bp_assemblages.png)
