---
layout: methode-archicad
group: bonnes-pratiques
title: Attribution des classifications
comments: true
---

...

## Uniformat CSI 2010

~~~
<?xml version="1.0" encoding="utf-8"?>
<Rules Name="UNIFORMAT CSI 2010">
	<Rule>
		<Name>UNIFORMAT CSI 2010</Name>
		<Description>Description</Description>
		<ApplicableTo>
			<ClassName>IfcObject</ClassName>
			<ClassName>IfcTypeObject</ClassName>
		</ApplicableTo>
		<Data>
			<DataDescriptors>
				<DataDescriptor Variable="number" Title="Code" />
				<DataDescriptor Variable="title" Title="Ouvrage" />
			</DataDescriptors>
			<DataEntries>{% for classification in site.data.uniformat-csi-2010 %}
			<DataEntry number="{{ classification.code }}" title="{{ classification.title_FR }}"/>{% endfor %}
			</DataEntries>
		</Data>
		<Script>
			<CreateClassificationReference>
				<IfcRelAssociatesClassification Name="UNIFORMAT CSI 2010">
					<IfcClassificationReference Name="$title" ItemReference="$number" Location="www.csiresources.org/practice/standards/uniformat">
						<IfcClassification Source="www.csiresources.org" Name="UNIFORMAT CSI 2010" Edition="2010">
							<IfcCalendarDate DayComponent="01" MonthComponent="01" YearComponent="2010"/> <!-- EditionDate -->
						</IfcClassification>
					</IfcClassificationReference>
				</IfcRelAssociatesClassification>
			</CreateClassificationReference>
		</Script>
	</Rule>
</Rules>
~~~

## Uniformat II 2015

~~~
<?xml version="1.0" encoding="utf-8"?>
<Rules Name="UNIFORMAT II 2015">
	<Rule>
		<Name>UNIFORMAT II 2015</Name>
		<Description>Description</Description>
		<ApplicableTo>
			<ClassName>IfcObject</ClassName>
			<ClassName>IfcTypeObject</ClassName>
		</ApplicableTo>
		<Data>
			<DataDescriptors>
				<DataDescriptor Variable="number" Title="Code" />
				<DataDescriptor Variable="title" Title="Ouvrage" />
			</DataDescriptors>
			<DataEntries>{% for classification in site.data.uniformat-ii-2015 %}
			<DataEntry number="{{ classification.code }}" title="{{ classification.title_FR }}"/>{% endfor %}
			</DataEntries>
		</Data>
		<Script>
			<CreateClassificationReference>
				<IfcRelAssociatesClassification Name="UNIFORMAT II 2015">
					<IfcClassificationReference Name="$title" ItemReference="$number" Location="www.astm.org/Standards/E1557.htm">
						<IfcClassification Source="www.astm.org" Name="UNIFORMAT II 2015" Edition="ASTM E1557 - 09(2015)">
							<IfcCalendarDate DayComponent="01" MonthComponent="10" YearComponent="2015"/> <!-- EditionDate -->
						</IfcClassification>
					</IfcClassificationReference>
				</IfcRelAssociatesClassification>
			</CreateClassificationReference>
		</Script>
	</Rule>
</Rules>
~~~
