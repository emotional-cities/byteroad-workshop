# GIS data formats

Below we cover the GIS file types that plays well with both Modern and Legacy stacks of our SDI:

## GeoJSON :sunny:

It's a JSON format designed to represent simple geographical features and their non-spatial attributes. It's the preferred format for the Modern Stack but can be easily converted to a convenient form for the Legacy stack.

## GeoPackage :inbox_tray:

GeoPackage is an open, standards-based, platform-independent, portable, self-describing, compact format for transferring geospatial information. GeoServer supports it natively. For OGC API Feature, a GeoJSON conversion pipeline is already set up in our SDI

## ShapeFile :see_no_evil:

It's not an open format (ESRI regulates it), but many open source tools like QGIS support it. Both modern and legacy stacks of our SDI can load data from this format.

## CSV :floppy_disk:

It's the most convenient output to produce with many software (Excel & similar, Database exports, custom software etc.). It's ok to use it, according to [RFC4180](https://datatracker.ietf.org/doc/html/rfc4180), but you have to take care of spatial coordinates yourself (format, projection etc.).
If you adopt the CSV format, we can upload the file to the PostGIS database in eMOTIONAL Cities SDI, making it available on GeoServer and with some extra conversion on OGC API Features.

  **Whichever format you choose, please make sure you have a colum with a unique identifier for your records. The ID could be an incrementing integer, or an alphanumeric string, as long each row as an unique ID value. You can read more about unique identifiers [here](https://veeevek.medium.com/possible-ways-to-generate-unique-ids-for-your-application-bfdcf4e6bef4)**


## General Guidelines 🧑‍🏫
In the nomenclature that you give to your datasets, there are a couple of general naming conventions to follow, in order for the datasets to be correctly usable through the various services of the SDI. 

Rules for file names:
1. All letters must be lowercase.
2. They cannot begin with _ (underscore) or - (hyphen).
3. They cannot contain spaces, commas, or the following characters: ```:, ", *, +, /, \, |, ?, #, >, or <```

- Ideal names are: london_pop_23, exp0823
- Acceptable names are: myexperiment_in_london, lisbon-walk-001
- Bad names are: my.File, _myexperiment0823, londonWalk
   
Rules for field names (e.g.: attributes, properties, column headers etc.):

1. [lower camel case](https://en.wikipedia.org/wiki/Camel_case)
2. [Alphanumeric](https://en.wikipedia.org/wiki/Alphanumericals) (therefore, they cannot contain spaces)
3. They cannot have a number as the first character
4. They cannot contain any dots, e.g.: ```.```
5. If you want your data to be exportable as a shapefile, make sure the names are at most 10 characters long (or at least that by truncating them after 10 characters they are still understandable!)

- Ideal names are: _myVariable, a001VariableVeryLong, theVar002_
- Acceptable names are: _my_variable_name, a_001_variable, the_variable_002_
- Bad names are: _my.Variable, my-Variable, Variable_Very_Very_Loooooooong_001, 123Variable_

> **Warning**
> Your data is not in a [geo format](https://github.com/emotional-cities/byteroad-workshop#data-formats)? No problem. Read [this](./tabular.md) guide to transform tabular data into one of the supported formats.
