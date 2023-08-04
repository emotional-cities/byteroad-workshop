# GIS data formats

Below we cover the GIS file types that plays well with both Modern and Legacy stacks of our SDI:

## GeoJSON :sunny:

It's a JSON format designed to represent simple geographical features and their non-spatial attributes. It's the preferred format for the Modern Stack but can be easily converted to a convenient form for the Legacy stack.

## GeoPackage :inbox_tray:

GeoPackage is an open, standards-based, platform-independent, portable, self-describing, compact format for transferring geospatial information. GeoServer supports it natively. For OGC API Feature, a GeoJSON conversion pipeline is already set up in our SDI

## ShapeFile :see_no_evil:

It's not an open format (ESRI regulates it), but many open source tools like QGIS support it. Both modern and legacy stacks of our SDI can load data from this format.

## CSV :floppy_disk:

It's the most convenient output to produce with many software (Excel & similar, Database exports, custom software etc.). It's ok to use it, but you have to take care of spatial coordinates yourself (format, projection etc.).
If you adopt the CSV format, we can upload the file to the PostGIS database in eMOTIONAL Cities SDI, making it available on GeoServer and with some extra conversion on OGC API Features.

## General recommendations 🧑‍🏫
In the nomenclature that you give to your datasets, there are a couple of general naming conventions that it would be better to follow if you want your datasets to be correctly usable through the various services of the SDI. Write the names (filenames, variables, attributes, column headers etc.) to be:

1. [Camel case](https://en.wikipedia.org/wiki/Camel_case)
2. [Alphanumeric](https://en.wikipedia.org/wiki/Alphanumericals) (therefore, they cannot contain spaces)
3. They cannot have a number as the first character

> **Warning**
> Your data is not in a [geo format](https://github.com/emotional-cities/byteroad-workshop#data-formats)? No problem. Read [this](./tabular.md) guide to transform tabular data into one of the supported formats.
