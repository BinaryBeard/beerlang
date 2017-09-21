<h1 align="center">
  <a href="http://brewboy.wbit.io"><img src="docs/img/beerlang-file@3x.png" alt="beerlang" width="200"></a>
  <br>
</h1>

<h4 align="center">The open source file specification for brewing software</h4>

<p align="center">
  <img src="https://img.shields.io/badge/version-0.0.1--alpha-F5BD56.svg" alt="version">
</p>
<br>

# <center>EVERYTHING BELOW THIS POINT IS A WORK IN PROGRESS</center>

## Purpose

Currently, there are no standards for automated and semi-automated beer making software. This industry is filled with proprietary software and few open standards. **beerlang** is only one solution to this closed industry.

## Compliance 

An application, program, or service can hold three types of compliance when it comes to following the **beerlang** specification.

### Interpretation

This type of compliance is earned when the application, program, or service can receive a **beerlang** file as input and completely understand what **beerlang** is asking the application, program, or service to do. 

### Composition

This type of compliance is earned when the application, program, or service can create a **beerlang** file to the **beerlang** specification. 

### Both?[NEED NAME]

This type of compliance is earned when the application, program, or service can both *Interpret* and *Compose* **beerlang** files to its specification. 

## General Specification

|tag|description|
|---|-----------|
|[`hops`](#hops-specification)|the flowers of the Humulus Iupulus plant that act as a flavoring and stability agen in beer||

## Specification Reference

### hops specification

**Attributes**

|attribute|required|type|primitive|description|accepted values|example|
|:--------|:------:|:---|:--------|:----------|:-------------:|:------|
|`name`|true|string||the human readable name|`^[\w,\ ,.]{1,255}$`|`cascade`, `mt. hood`, `saaz`|
|`type`|false|string||the human readable type of use for these hops|`bittering`, `aroma`, `bittering and aroma`|`bittering`, `aroma`, `bittering and aroma`|
|`form`|false|string||the form of the hops|`pellet`, `plug`, `leaf`|`pellet`, `plug`, `leaf`|
|`alpha`|true|number|float|the percentage of alpha acid|`^(\d*\.\d+)$`|`0.082` => `8.2%`, `0.12` => `12%`, `0.045` => `4.5%`|
|`quantity`|true|number|float|the quantity of required for the recipe|`^(\d*\.\d+)$`|`1.2`, `0.8`, `5.7`
|`qty_unit`|true|string||refer to the *symbol* on the [mass table](#mass-table) in the [Appendix](#appendix)|[mass table](#mass-table)|`kg`, `g`, `lb`|
|`usage`|true|string||refer to the *name* on the [hop usage table](#hop-usage-table) in the [Appendix](#appendix)|`boil`, `dry hop`, `mash`|`boil`, `dry hop`, `mash`|
|`duration`|true|number|float|the duration of the usage|`^(\d*\.\d+)$`|`60.0`, `3600.0`, `1.0`|
|`dur_unit`|true|string||refer to the *symbol* on the [duration table](#duration-table) in the [Appendix](#appendix)|[duration table](#duration-table)|`sec`, `min`, `hr`|

## Appendix

### mass table

|symbol|name|default|equivalence|
|------|----|-------|:----------|
|`g`|gram|true|`1.0 g` = `1.0g`|
|`kg`|kilogram||`1.0 kg` = `1000.0 g`|
|`oz`|ounce||`1.0 oz` = `28.3495 g`|
|`lb`|pound||`1.0 lb` = `453.592 g`|

### volume table

|symbol|name|default|equivalence|
|------|----|-------|:----------|
|`mL`|milliliter|true|`1.0 mL` = `1.0 mL`|
|`tsp`|teaspoon||`1.0  tsp` = `4.92892 mL`|
|`tbsp`|tablespoon||`1.0  tbsp` = `14.7868 mL`|
|`fl oz`|fluid ounce||`1.0  fl oz` = `29.5735 mL`|
|`cup`|cup||`1.0  cup` = `240 mL`|
|`pt`|pint||`1.0  pt` = `473.176 mL`|
|`qt`|quart||`1.0  qt` = `946.353 mL`|
|`l`|liter||`1.0  L` = `1000 mL`|
|`gal`|gallon||`1.0  gal` = `3785.41 mL`|

### temperature table

|symbol|name|default|equivalence|
|------|----|-------|:----------|
|`C`|celsius|true|`20.0 C` = `20.0 C`|
|`F`|fahrenheit||`68.0 F` = `20.0 C`|
|`K`|kelvin||`293.15 K` = `20.0 C`|

### duration table

|symbol|name|default|equivalence|
|------|----|-------|:----------|
|`sec`|second|true|`1.0 sec` = `1.0 sec`|
|`min`|minute||`1.0 min` = `60.0 sec`|
|`hr`|hour||`1.0 hr` = `3600.0 sec`|
|`day`|day||`1.0 day` = `86400.0 sec`|
|`wk`|week||`1.0 wk` = `604800.0 sec`|

### color table

|symbol|name|default|equivalence|
|------|----|-------|:----------|
|`srm`|Standard Reference Method|true|`25.0 srm` = `25.0 srm`|
|`ebc`|European Brewing Convention||`49.3 ebc` = `25.0 srm`|
|`L`|Lovibond||`19.0 L` = `25.0 srm`|

### specific gravity table

|symbol|name|default|
|------|----|-------|
|`sg`|Specific Gravity|true|
|`plato`|Plato||
