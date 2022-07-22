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
The SDI uses an hybrid architecture, with a mix of [legacy](#the-legacy-stack) and [newer](#the-modern-stack) OGC standards. On one hand we will leverage the OGC API family of standards, which are web native and present a number of advantages for modern web applications. On the other hand, we aknoweledge the fact that a certain degree of compatibility with legacy OGC Web Services (OWS) may be required for some use cases, and will publish data also using those standards.

### The Modern Stack
These are the standards that we identified as relevant for publishing the eMOTIONAL Cities datasets:
- OGC API Features - for serving feature data over the web;
- OGC API Tiles - for serving vector tiles over the web;
- OGC API Records - for exposing a catalogue of geospatial metadata;
- OGC API DGGS - for serving data organised according to a Discrete Global Grid System (for instance, indexes);

> **Note**
> Add hyperlinks to the standards above

### The Legacy Stack
The legacy stack rests on the solid foundation of GeoServer, which allows geospatial datasets to be exposed in the following standards:
- WFS 1.0.0, 1.1.0, 2.0.0
- WMS 1.1.1, 1.3.0
- WMS-C 1.1.1
- WMTS 1.0.0

> **Note**
> Add hyperlinks to the standards above

## Where is the SDI? :eyes:
You can access the ```newer``` SDI at this endpoint:

https://emotional.byteroad.net/

It features a HTML interface, which you can use to explore it.

View the list of available collections, by clicking on ```View the collections in this service```, or by accessing this endpoint:

https://emotional.byteroad.net/collections?f=html

You can click in any collection, to learn about the available services and access the data.

You can access the ```legacy``` SDI at this endpoint:

https://emotional.byteroad.net/geoserver/

The UI is protected with username and password, so ask for the credentials first.

These are the endpoints for the different services:
- [WMS 1.3.0](https://emotional.byteroad.net/geoserver/ows?service=wms&version=1.3.0&request=GetCapabilities)
- [WMTS 1.0.0](https://emotional.byteroad.net/geoserver/gwc/service/wmts?REQUEST=GetCapabilities)
- [WFS 2.0.0](https://emotional.byteroad.net/geoserver/ows?service=wfs&version=2.0.0&request=GetCapabilities)


Browse the catalogue using this client:

https://github.com/Luoghi-indomiti/bootstrap-ogc-api-react

> **Note**
> Enable GitHub pages for this endpoint and replace the link.

## Connecting to the SDI using a Client :electric_plug:
Using the endpoints above, you can access data from the SDI using a client, provided that the client supports the standards in the [legacy](#the-legacy-stack) or [newer](#the-modern-stack). In this section of the workshop, we will demonstrate how-to do that, using different clients: QGIS, python/OWSLib, Mapstore and JavaScript/LeafLet. If you are using a different GIS client, you can ask us if it has support for any of these standards.

### QGIS

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
> **Note**
> OGC WFS, WMTS & WMTS.

### Python
> **Note**
> OGC API Features, OGC API Records, OGC WFS, WMTS & WMTS.

### JavaScript
> **Note**
> OGC API Features, OGC API Vector Tiles

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




