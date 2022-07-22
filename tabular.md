# Export Tabular Data in a Geo Format

In this section we will import tabular data (e.g.: CSV file) with lat, long coordinates into a geo format, using GDAL/OGR.

First of all, install GDAL. These are the instructions for Ubuntu:

https://mothergeo-py.readthedocs.io/en/latest/development/how-to/gdal-ubuntu-pkg.html

Here are instructions for other platforms:

https://gdal.org/download.html

A the end of the installation, you shoud be able to open a terminal in your OS, and type:

```
ogrinfo --version
```

> **Warning**
> Ensure that the file you want to convert is in [OCSV](https://en.wikipedia.org/wiki/Comma-separated_values) format and that it has two separate fields for storing the latitude and longitude coordinates, in decimals. Also take note of the [CRS](https://en.wikipedia.org/wiki/Spatial_reference_system) of the data.


Create a [virtual data source](https://gdal.org/drivers/vector/vrt.html) text file, with a content that describes your data (see the example bellow). Save it with a ".vrt" extension.

```
<OGRVRTDataSource>
  <OGRVRTLayer name="masked">
    <SrcDataSource>masked.csv</SrcDataSource>
    <GeometryType>wkbPoint</GeometryType>
    <LayerSRS>EPSG:4326</LayerSRS>
    <GeometryField encoding="PointFromColumns" x="X" y="Y"/>
  </OGRVRTLayer>
</OGRVRTDataSource>
```

> **Warning**
> Ensure that the x and y field names match the names of your latitude and longitude fields.

Run ogrinfo, to ensure it recognizes the data source:

```
ogrinfo masked.vrt masked -fid 1
```

Export the data source into a GeoJSON:

```
ogr2ogr -f GeoJSON masked.geojson masked.vrt
```

Export the data source into a GeoPackage:

```
 ogr2ogr -f GPKG masked.gpkg masked.vrt
```