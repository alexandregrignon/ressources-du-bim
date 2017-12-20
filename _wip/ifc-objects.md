---
layout: default
group: standards
lang: english
ref: objets-ifc
title: IFC objects
description: Decoding IFC objects classes
comments: true
ordre: 3
status: publish
---

# IFC objects

{% assign langs = site.standards | where: 'ref','objets-ifc' %}
This page is also available in the following languages : {% for page in langs %}<a class="btn btn-outline-dark btn-sm" href="{{ page.url }}" role="button"><i class="fa fa-globe" aria-hidden="true"></i> {{ page.lang }}</a> {% endfor %}

## Introduction

...

## Lists by specialties

<ul class="nav nav-tabs" id="myTab" role="tablist">
  <li class="nav-item">
    <a class="nav-link active" data-toggle="tab" href="#domaine_architectural" role="tab" aria-controls="domaine_architectural" rel="nofollow">Architecture (IFC2x3-TC1)</a>
  </li>
  <li class="nav-item">
    <a class="nav-link" data-toggle="tab" href="#domaine_structurel" role="tab" aria-controls="domaine_structurel" rel="nofollow">Structure (IFC2x3-TC1)</a>
  </li>
  <li class="nav-item">
    <a class="nav-link" data-toggle="tab" href="#domaine_fluides" role="tab" aria-controls="domaine_fluides" rel="nofollow">MEP (IFC2x3-TC1)</a>
  </li>
</ul>

<div class="tab-content">
  <div class="tab-pane active" id="domaine_architectural" role="tabpanel">
    <div id="table-domaine-architectural">
      <table class="table table-responsive table-sm table-hover">
        <div class="form-group">
          <div class="input-group">
            <div class="input-group-addon"><i class="fa fa-search"></i></div>
            <input class="search fuzzy-search form-control" id="test" placeholder="Search in list..." />
          </div>
        </div>
        <thead>
          <tr>
            <th>Terme anglais</th>
            <th>IfcProduct + PredefinedType</th>
            <th>IfcTypeProduct + PredefinedType</th>
          </tr>
        </thead>
        <tbody class="list">
          {% for object in site.data.ifc-objets %}
            {% if object.domaine_architecture == true %}
            <tr>
              <td class="en_gb">
                {% if object.nom_en_gb != null %}
                  <a href="https://www.google.fr/search?q={{ object.nom_en_gb | downcase }}" target="_blank" data-proofer-ignore><i class="fa fa-search"></i></a>
                  <a href="https://translate.google.com/#en/fr/{{ object.nom_en_gb | downcase }}" target="_blank" data-proofer-ignore><i class="fa fa-globe"></i></a>
                {% endif %}
                {{ object.nom_en_gb }}
              </td>
              <td class="ifcproduct">
                {% if object.ifcproduct_ifc2x3tc1 != null %}
                  <a href="https://www.google.fr/search?q={{ object.ifcproduct_ifc2x3tc1 | downcase }}" target="_blank"><i class="fa fa-search" data-proofer-ignore></i></a>
                {% endif %}
                {{ object.ifcproduct_ifc2x3tc1 }}
              </td>
              <td class="ifctypeproduct">
                {% if object.ifctypeproduct_ifc2x3tc1 != null %}
                  <a href="https://www.google.fr/search?q={{ object.ifctypeproduct_ifc2x3tc1 | downcase }}" target="_blank" data-proofer-ignore><i class="fa fa-search"></i></a>
                {% endif %}
                {{ object.ifctypeproduct_ifc2x3tc1 }}
              </td>
            </tr>
            {% endif %}
          {% endfor %}
        </tbody>
      </table>
    </div>
  </div>
  <div class="tab-pane" id="domaine_structurel" role="tabpanel">
    <div id="table-domaine-structurel">
      <table class="table table-responsive table-sm table-hover">
        <div class="form-group">
          <div class="input-group">
            <div class="input-group-addon"><i class="fa fa-search"></i></div>
            <input class="search fuzzy-search form-control" id="test" placeholder="Search in list..." />
          </div>
        </div>
        <thead>
          <tr>
            <th>Terme anglais</th>
            <th>IfcProduct + PredefinedType</th>
            <th>IfcTypeProduct + PredefinedType</th>
          </tr>
        </thead>
        <tbody class="list">
          {% for object in site.data.ifc-objets %}
            {% if object.domaine_structure == true %}
            <tr>
              <td class="en_gb">
                {% if object.nom_en_gb != null %}
                  <a href="https://www.google.fr/search?q={{ object.nom_en_gb | downcase }}" target="_blank" data-proofer-ignore><i class="fa fa-search"></i></a>
                  <a href="https://translate.google.com/#en/fr/{{ object.nom_en_gb | downcase }}" target="_blank" data-proofer-ignore><i class="fa fa-globe"></i></a>
                {% endif %}
                {{ object.nom_en_gb }}
              </td>
              <td class="ifcproduct">
                {% if object.ifcproduct_ifc2x3tc1 != null %}
                  <a href="https://www.google.fr/search?q={{ object.ifcproduct_ifc2x3tc1 | downcase }}" target="_blank" data-proofer-ignore><i class="fa fa-search"></i></a>
                {% endif %}
                {{ object.ifcproduct_ifc2x3tc1 }}
              </td>
              <td class="ifctypeproduct">
                {% if object.ifctypeproduct_ifc2x3tc1 != null %}
                  <a href="https://www.google.fr/search?q={{ object.ifctypeproduct_ifc2x3tc1 | downcase }}" target="_blank" data-proofer-ignore><i class="fa fa-search"></i></a>
                {% endif %}
                {{ object.ifctypeproduct_ifc2x3tc1 }}
              </td>
            </tr>
            {% endif %}
          {% endfor %}
        </tbody>
      </table>
    </div>
  </div>
  <div class="tab-pane" id="domaine_fluides" role="tabpanel">
    <div id="table-domaine-fluides">
      <table class="table table-responsive table-sm table-hover">
        <div class="form-group">
          <div class="input-group">
            <div class="input-group-addon"><i class="fa fa-search"></i></div>
            <input class="search fuzzy-search form-control" id="test" placeholder="Search in list..." />
          </div>
        </div>
        <thead>
          <tr>
            <th>Terme anglais</th>
            <th>IfcProduct + PredefinedType</th>
            <th>IfcTypeProduct + PredefinedType</th>
          </tr>
        </thead>
        <tbody class="list">
          {% for object in site.data.ifc-objets %}
            {% if object.domaine_fluides == true %}
            <tr>
              <td class="en_gb">
                {% if object.nom_en_gb != null %}
                  <a href="https://www.google.fr/search?q={{ object.nom_en_gb | downcase }}" target="_blank" data-proofer-ignore><i class="fa fa-search"></i></a>
                  <a href="https://translate.google.com/#en/fr/{{ object.nom_en_gb | downcase }}" target="_blank" data-proofer-ignore><i class="fa fa-globe"></i></a>
                {% endif %}
                {{ object.nom_en_gb }}
              </td>
              <td class="ifcproduct">
                {% if object.ifcproduct_ifc2x3tc1 != null %}
                  <a href="https://www.google.fr/search?q={{ object.ifcproduct_ifc2x3tc1 | downcase }}" target="_blank" data-proofer-ignore><i class="fa fa-search"></i></a>
                {% endif %}
                {{ object.ifcproduct_ifc2x3tc1 }}
              </td>
              <td class="ifctypeproduct">
                {% if object.ifctypeproduct_ifc2x3tc1 != null %}
                  <a href="https://www.google.fr/search?q={{ object.ifctypeproduct_ifc2x3tc1 | downcase }}" target="_blank" data-proofer-ignore><i class="fa fa-search"></i></a>
                {% endif %}
                {{ object.ifctypeproduct_ifc2x3tc1 }}
              </td>
            </tr>
            {% endif %}
          {% endfor %}
        </tbody>
      </table>
    </div>
  </div>
</div>

## Sources

* **IFC2x Edition 3 - Technical Corrigendum 1**. Disponible sur : [http://www.buildingsmart-tech.org/ifc/IFC2x3/TC1/html/index.htm](http://www.buildingsmart-tech.org/ifc/IFC2x3/TC1/html/index.htm)
* **IFC 2×3 element and type classification – The plain language A-Z list** [Article en ligne]. BIM Blog, Bond Bryan Digital. Disponible sur : [http://bimblog.bondbryan.com/ifc-2x3-element-and-type-classification-the-plain-language-a-z-list/](http://bimblog.bondbryan.com/ifc-2x3-element-and-type-classification-the-plain-language-a-z-list/)
