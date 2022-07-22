![logo](BR_Black.jpg)

# WORKSHOP - Sharing data with the eMOTIONAL Cities SDI :open_hands:
This workshop introduces the tools that compose the
eMOTIONAL Cities GIS infrastructure. We will see how to share and
consume data through the classic W * OGC services and the latest OGC
Open API. During the workshop, we will see how to use client
applications, such as QGIS, to consume data from various endpoints.
Please read the [FAQ](#faq) section for more information.

This workshop was created by [ByteRoad](https://byteroad.net/), in the context of the [eMOTIONAL Cities](https://emotionalcities-h2020.eu/) project.

## Architecture and Technology Stack :desktop_computer:
An SDI is a set of tools and methodologies for storing and facilitating the use of geospatial data. The SDI of eMOTIONAL Cities favours using open source tools and open standards for data and service formats.

When we talk about standards, it's helpful to distinguish between two different categories:

* **Data formats**: the formats by which data is stored in a computer: they can indicate a file with a particular format or a database.
* **Service standards**: the standards by which data is shared and made accessible (which is not the same as giving access to raw data).

For *geospatial data*, the most popular formats are:

* Geographic database
* Vector files
* Raster files

The most widely used open standards for *services* are those defined by the Open Geospatial Consortium (OGC).
The most commonly used standards to date are those of OGC Web Services (OWS).
Still, in recent years new standards have emerged that are more adherent to modern technological trends, oriented to the web and ease of use, known under the name of OGC OpenAPI.
Our SDI uses a hybrid architecture with a mix of OWS standards, which we will call ["Legacy Stack"](#the-legacy-stack) and the latest OGC OpenAPI OGC, the ["Modern Stack"](#the-modern-stack).
The idea is to create an SDI that is easy to use, aligned with emerging technological trends, and compatible with most existing tools.

> **Note**
> It is possible to use the Legacy or Modern stack services... or both, as long as it suits users who have to consume your data. However, from a harmonization point of view, the ideal would be to have uniformity between the different datasets.

### Data formats

From the perspective of the data lifecycle in the eMOTIONAL Cities SDI, the data format is the first aspect we need to consider. Geospatial data is significantly associated with a location on the Earth's surface. An example:

| Temperature | Humidity  | Time                | Geometry                                  |
|-------------|-----------|---------------------|-------------------------------------------|
| 37.5        | 30 %      | 15:30:00 21/07/2022 |POINT (1016908.55777364 4680222.7018746)   |
| 37          | 35 %      | 15:30:00 21/07/2022 |POINT (1016721.55777364 4680232.7018746)   |
| 37          | 31.5 %    | 15:35:00 21/07/2022 |POINT (1016908.55777364 4680222.7018746)   |
| 37          | 34 %      | 15:35:00 21/07/2022 |POINT (1016721.55777364 4680232.7018746)   |

In GIS data, this association must be explicit, and the geographic information must be associated 1:1 with the relevant feature. This is quite straightforward in the data produced with GIS software such as QGIS. For data produced with other softwares this is not always true, and therefore an extra processing step is required before producing the dataset to be ingested into the SDI.

### The Modern Stack

![Modern Stack](img/modern_stack.png)

These are the standards that we identified as relevant for publishing the eMOTIONAL Cities datasets:
- [OGC API Features](https://www.ogc.org/standards/ogcapi-features) - for serving feature data over the web;
- [OGC API Tiles](https://ogcapi.ogc.org/tiles/) - (draft) for serving vector tiles over the web;
- [OGC API Records](https://ogcapi.ogc.org/records/) - (draft) for exposing a catalogue of geospatial metadata;
- [OGC API DGGS](https://ogcapi.ogc.org/dggs/) - (draft) for serving data organised according to a Discrete Global Grid System (for instance, indexes);

### The Legacy Stack

![Legacy Stack](img/legacy_stack.png)

The legacy stack rests on the solid foundation of GeoServer, which allows geospatial datasets to be exposed in the following standards:
- [WFS](https://www.ogc.org/standards/wfs) 1.0.0, 1.1.0, 2.0.0
- [WMS](https://www.ogc.org/standards/wms) 1.1.1, 1.3.0
- [WMS-C](https://www.ogc.org/standards/wms) 1.1.1
- [WMTS](https://www.ogc.org/standards/wmts) 1.0.0


## Where is the SDI? :eyes:
You can access the ```modern``` services at this endpoint:

https://emotional.byteroad.net/

It features a HTML interface, which you can use to explore it.

View the list of available collections, by clicking on ```View the collections in this service```, or by accessing this endpoint:

https://emotional.byteroad.net/collections?f=html

You can click in any collection, to learn about the available services and access the data.

An alternative way to browse the catalogue using this client:

https://luoghi-indomiti.github.io/a-gis-full-of-records/

You can access the ```legacy``` services at this endpoint:

https://emotional.byteroad.net/geoserver/

The UI is protected with username and password, so ask for the credentials first.

These are the endpoints for the different services:
- [WMS 1.3.0](https://emotional.byteroad.net/geoserver/ows?service=wms&version=1.3.0&request=GetCapabilities)
- [WMTS 1.0.0](https://emotional.byteroad.net/geoserver/gwc/service/wmts?REQUEST=GetCapabilities)
- [WFS 2.0.0](https://emotional.byteroad.net/geoserver/ows?service=wfs&version=2.0.0&request=GetCapabilities)


## Connecting to the SDI using a Client :electric_plug:
Using the endpoints above, you can access data from the SDI using a client, provided that the client supports the standards in the [legacy](#the-legacy-stack) or [newer](#the-modern-stack). In this section of the workshop, we will demonstrate how-to do that, using different clients: QGIS, python/OWSLib, Mapstore and JavaScript/LeafLet. If you are using a different GIS client, you can ask us if it has support for any of these standards.

### QGIS
[QGIS](https://www.qgis.org/en/site/) could be considered one of the eMOTIONAL Cities SDI tools, with the only difference that it must be installed locally, on your machine.

QGIS is a desktop software to edit GIS data. It's the main open source solution in the category and is compatible with most of the data formats and standards available, and is continuously updated to support new standards.

QGIS supports OGC API Vector Tiles via the [Vector Tiles Layer](https://docs.qgis.org/3.22/en/docs/user_manual/working_with_vector_tiles/vector_tiles_properties.html). Although OGC API Tiles are not natively supported, you can customize the `generic connection` in order to access them in QGIS.

Before entering QGIS, access your pygeoapi installation page on the browser and follow these steps.

- Access the collection page of the tiles dataset: https://emotional.byteroad.net/collections/masked
- From there, navigate to the tiles page by clicking on `tiles`: https://emotional.byteroad.net/collections/masked/tiles
- Click in `Tiles metadata in tilejson format`: https://emotional.byteroad.net/collections/masked/tiles/WorldCRS84Quad/metadata
- Take note of the url in `tiles`: `https://emotional.byteroad.net/collections/masked/tiles/WorldCRS84Quad/{tileMatrix}/{tileRow}/{tileCol}?f=mvt` and of the values of minZoom and maxZoom.

Follow these steps to connect to a service and access vector tiles:

- Locate the vector tiles service, on the left hand side browser panel. In alternative, you can also go to the top menu and navigate to Layer->Add Layer->Vector Tile Layer.

![](vtiles1.png)

- Right-click to bring up the context menu and choose `New Generic connection`.  
- Fill the required values. For URL, use the one you noted from the previous step, replacing the`{tileMatrix}/{tileRow}/{tileCol}` by {x}/{x}/{y}. 
- Press `Ok` to add the service. At this point, if you are using the browser you should see the collection appearing in the menu, bellow "Vector Tiles".
- Double-click in the collection to add it to the map. 
- Don't forget to set the CRS of the map to `EPSG:4326`, by clicking in the button on the lower right corner. 
- Zoom in to Florence, to see your dataset.

![](vtiles2.png)
![](vtiles3.png)
![](vtiles4.png)

> **Note**
> OGC API Features, OGC API Vector Tiles, OGC API Records, OGC WFS, WMTS & WMTS.

### Mapstore

[Mapstore](https://mapstore.readthedocs.io/en/latest/) is a component of our SDI and offers some interesting [Web mapping](https://en.wikipedia.org/wiki/Web_mapping) capabilities for the legacy stack. In fact, it is possible to use Mapstore to view the data stored in GeoServer.

To access Mapstore you can go [here](https://emotional.byteroad.net/mapstore/#/) and log in with credentials:

**User**: *workshop*

**Password**: *WSTartu22!*

![Mapstore Login](img/mapstore1.png)

To create a new map, click on this button:

![Mapstore New Map](img/mapstore2.png)

The new map will be empty, so we need to configure our Geoserver WMS enpoint to pick some layers to load (or WFS and WMTS if you prefer).

![Mapstore Menu](img/mapstore3.png)

The eMOTIONAL Cities Geoserver WMS endpoint is *https://emotional.byteroad.net/geoserver/wms*

![Mapstore Catalog Configuration](img/mapstore4.png)

After save we will be able to load our layers

![Mapstore Catalog Layers](img/mapstore5.png)

And add them to the map

![Mapstore Map with layers](img/mapstore6.png)

We can add more layers to a single map. There are [many options](https://mapstore.readthedocs.io/en/latest/user-guide/layer-settings/) to play with.

To persist our map we can save it from the top right menu

![Mapstore Menu](img/mapstore3.png)

Then we can choose the name and description of the map and who has access to it

![Mapstore Menu](img/mapstore7.png)

The official documentation of Mapstore is available [here](https://mapstore.readthedocs.io/en/latest/user-guide/home-page/)

### Python
> **Note**
> OGC API Features, OGC API Records, OGC WFS, WMTS & WMTS.

## Authoring Metadata :open_book:
> **Warning**
> Use QGIS & PygeoMeta?

## Ingesting Data into the SDI :rocket:

Upload your own dataset, using [these](https://github.com/emotional-cities/data-share) instructions. We recommend that you use the ```GeoJSON``` format.

We are going to ingest the dataset into the SDI, and you can access it using one of the clients you saw in the previous section.

> **Note**
> Configure geoserver to [read data from an S3 bucket](https://github.com/emotional-cities/byteroad-workshop/issues/2)

## FAQ

**Q: How can I register for the workshop?**

**A:** Please register using [this](https://docs.google.com/forms/d/e/1FAIpQLSffKGPfxnrFIAVHXUDnkUDzrWAn7a-YNTHgkWuwVnGTCWbQ6Q/viewform) link.

**Q: Do I need to install anything ahead of the workshop?**

**A:** Yes. If you want to be *hands-on*, please install (*at least, some of*) this software:
- [QGIS](https://github.com/doublebyte1/bts_geospatial/blob/master/INSTALL_QGIS.md)
- [Jupyter](https://jupyter.org/install#jupyter-notebook)
- [Visual Studio Code](https://visualstudio.microsoft.com/downloads/) or another text editor

**Q: Is this workshop for me?**

**A:** If you produce/collect or access any data from the eMOTIONAL Cities project, this workshop is for you.

**Q: Do I need to know how-to code, in order to attend this workshop?**

**A:** No. Although some of the client applications which interface with the SDI use some coding, we will also show *no-coding* alternatives.

**Q: What will I learn during this workshop?**

**A:** At the end of this workshop you should be able to consume data from the SDI using a client and ingest data to the SDI, through the data lake.




